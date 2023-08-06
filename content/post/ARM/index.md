---
title: Azureリソース管理の全体像
date: 2023-08-05 00:00:00+0000
draft: true
# image: cover.jpg
# categories:
#     - Example Category
# tags:
#     - Example Tag
---

## Azureのリソース管理

業務でリソースアカウントを扱う必要があったんですが、権限やロールが内容でアクセスできなかった事がありました。

AzureADのロールでは該当するロールが見当たらず探してたところ、リソースグループに自分を追加する必要がありました。

このAzureのリソース管理の全体像があんまり理解できなかったので、調べてまとめてみました。

[公式ドキュメント](https://learn.microsoft.com/ja-jp/azure/cloud-adoption-framework/get-started/how-azure-resource-manager-works)

### Azureのリソース

Azureが管理できるすべての対象を指していて、例えば、ストレージアカウント、仮想マシン、仮想ネットワーク、Webアプリ、データベースなどはすべてリソースと呼ばれます。

ストレージアカウントはAzureのストレージサービスで、ファイルや各種データを管理できる場所のことです。

### 全体像

Azureのリソースを管理するための階層がいくつかあり、下記の図をベースにリソース管理をまとめていきます。

![scope-levels.png](scope-levels.png)



