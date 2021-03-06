---
title: MBAM 1.0 サーバー インフラストラクチャの展開
description: MBAM 1.0 サーバー インフラストラクチャの展開
author: dansimp
ms.assetid: 90529379-b70e-4c92-b188-3d7aaf1844af
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, security
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 08/30/2016
ms.openlocfilehash: de136db557233a097d95f47ef0a1bba5996798c5
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10825177"
---
# MBAM 1.0 サーバー インフラストラクチャの展開


Microsoft BitLocker 管理と監視 (MBAM) サーバー機能は、1 ~ 5 台のサーバーを使用して、さまざまな構成でインストールできます。 通常、運用環境では、スケーラビリティのニーズに応じて、3 ~ 5 台のサーバーの構成を使用する必要があります。 MBAM と推奨される展開トポロジのパフォーマンスのスケーラビリティの詳細については、「 [Mbam スケーラビリティと高可用性ガイドホワイトペーパー](https://go.microsoft.com/fwlink/p/?LinkId=258314)」を参照してください。

## すべての MBAM 1.0 を1台のサーバーに展開する


この構成では、すべての MBAM 機能が1台のサーバーにインストールされます。 MBAM サーバーインフラストラクチャ向けのこの展開トポロジは、最大 21000 MBAM クライアントコンピューターをサポートします。

**重要** この構成はサポートされていますが、テストのみに使用することをお勧めします。

 

このセクションの手順では、1つのサーバーに MBAM 機能を完全にインストールする方法について説明します。

[単一サーバーに MBAM をインストールして構成する方法](how-to-install-and-configure-mbam-on-a-single-server-mbam-1.md)

## 分散サーバーに MBAM 1.0 を展開する


MBAM 機能は、スケーラビリティのニーズに応じて、さまざまな構成でインストールできます。 MBAM サーバー機能の展開を計画する方法の詳細については、「 [mbam 1.0 サーバー展開の計画](planning-for-mbam-10-server-deployment.md)」を参照してください。

このセクションの手順では、分散サーバー上の MBAM 機能の完全なインストールについて説明します。

### 3台のコンピューター構成

次の図は、MBAM 向けの3台のコンピューターの展開トポロジを示しています。 最大 55000 MBAM クライアントをサポートする運用環境では、このトポロジをお勧めします。

![mbam 3 台のコンピューターの展開トポロジ](images/mbam-3-server.jpg)

この構成では、MBAM 機能は次の構成でインストールされます。

1.  回復とハードウェアデータベース、コンプライアンスおよび監査データベース、コンプライアンスおよび監査レポートはサーバーにインストールされます。

2.  サーバーには、管理と監視のサーバー機能がインストールされています。

3.  MBAM グループポリシーテンプレートは、グループポリシーオブジェクト (GPO) を変更できるコンピューターにインストールされています。

### 4台のコンピューターによる構成

次の図は、MBAM 向けの4台のコンピューターの展開トポロジを示しています。 最大 11万 MBAM クライアントをサポートしている運用環境では、このトポロジをお勧めします。

![mbam 4 台のコンピューターの展開トポロジ。](images/mbam-4-computer.jpg)

この構成では、MBAM 機能は次の構成でインストールされます。

1.  回復とハードウェアデータベース、コンプライアンスおよび監査データベース、コンプライアンスおよび監査レポートはサーバーにインストールされます。

2.  管理と監視サーバー機能は、ネットワーク負荷分散 (NLB) サーバークラスターで構成されているサーバーにインストールされます。

3.  MBAM グループポリシーテンプレートは、グループポリシーオブジェクトを変更できるコンピューターにインストールされています。

### 5台のコンピューター構成

次の図は、MBAM の5台のコンピューターの展開トポロジを示しています。 最大 135000 MBAM クライアントをサポートする運用環境では、このトポロジをお勧めします。

![mbam 5 台のコンピューターの展開トポロジ。](images/mbam-5-computer.jpg)

この構成では、MBAM 機能は次の構成でインストールされます。

1.  回復とハードウェアデータベースはサーバーにインストールされています。

2.  コンプライアンスと監査データベース、コンプライアンスおよび監査レポートは、サーバーにインストールされます。

3.  管理と監視サーバー機能は、ネットワーク負荷分散 (NLB) サーバークラスターで構成されているサーバーにインストールされます。

4.  MBAM グループポリシーテンプレートは、グループポリシーオブジェクトを変更できるコンピューターにインストールされています。

[分散サーバーに MBAM をインストールして構成する方法](how-to-install-and-configure-mbam-on-distributed-servers-mbam-1.md)

[MBAM のネットワーク負荷分散を構成する方法](how-to-configure-network-load-balancing-for-mbam.md)

## MBAM 1.0 Server 機能の展開に関するその他のリソース


[MBAM 1.0 の展開](deploying-mbam-10.md)

 

 





