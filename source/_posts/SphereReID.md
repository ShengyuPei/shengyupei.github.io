---
title: SphereReID
date: 2020-04-30 19:58:19
tags:
  - Person ReID
categories:
  - Person ReID
---
# SphereReID网络
文章Arxiv下载地址
[SphereReID: Deep Hypersphere Manifold
Embedding for Person Re-Identification](https://arxiv.org/abs/1807.00537 "下载")
它的网络基础是ResNet50，在后面增加了几个环节进行降维。
```python
self.bn2 = nn.BatchNorm1d(2048)
self.dp = nn.Dropout(0.5)
self.fc = nn.Linear(in_features=2048, out_features=1024, bias=True)
self.bn3 = nn.BatchNorm1d(1024)
```
网络输出的特征维度是1024，
文章最重要的贡献是损失函数。
<!--more-->
![网络结构](network.png "网络结构")
# 球损失函数
```python
class SphereLoss(nn.Module):
    def __init__(self, in_feats, n_classes, scale = 14, *args, **kwargs):
        super(SphereLoss, self).__init__(*args, **kwargs)
        self.scale = scale
        self.cross_entropy = nn.CrossEntropyLoss()
        self.W = torch.nn.Parameter(torch.randn(in_feats, n_classes),
                requires_grad = True)
        nn.init.xavier_normal_(self.W, gain=1)

    def forward(self, x, label):
        x_norm = torch.norm(x, 2, 1, True).clamp(min = 1e-12).expand_as(x)
        x_norm = x / x_norm
        w_norm = torch.norm(self.W, 2, 0, True).clamp(min=1e-12).expand_as(self.W)
        w_norm = self.W / w_norm
        cos_th = torch.mm(x_norm, w_norm)
        s_cos_th = self.scale * cos_th
        loss = self.cross_entropy(s_cos_th, label)
        return loss
```

```python
class OhemSphereLoss(nn.Module):
    def __init__(self, in_feats, n_classes, thresh=0.7, scale=14, *args, **kwargs):
        super(OhemSphereLoss, self).__init__(*args, **kwargs)
        self.thresh = thresh
        self.scale = scale
        self.cross_entropy = nn.CrossEntropyLoss(reduction='none')
        self.W = torch.nn.Parameter(torch.randn(in_feats, n_classes),
                requires_grad = True)
        nn.init.xavier_normal_(self.W, gain=1)

    def forward(self, x, label):
        n_examples = x.size()[0]
        n_pick = int(n_examples*self.thresh)
        x_norm = torch.norm(x, 2, 1, True).clamp(min = 1e-12).expand_as(x)
        x_norm = x / x_norm
        w_norm = torch.norm(self.W, 2, 0, True).clamp(min = 1e-12).expand_as(self.W)
        w_norm = self.W / w_norm
        cos_th = torch.mm(x_norm, w_norm)
        s_cos_th = self.scale * cos_th
        loss = self.cross_entropy(s_cos_th, label)
        loss, _ = torch.sort(loss, descending=True)
        loss = torch.mean(loss[:n_pick])
        return loss
```
![损失函数](sphere_loss.png "损失函数")
![损失函数](loss.png "损失函数")

