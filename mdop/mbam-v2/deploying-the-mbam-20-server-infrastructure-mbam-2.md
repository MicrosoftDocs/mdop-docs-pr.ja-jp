---
title: MBAM 2.0 サーバー インフラストラクチャの展開
description: MBAM 2.0 サーバー インフラストラクチャの展開
author: dansimp
ms.assetid: 52e68d94-e2b4-4b06-ae55-f900ea6cc59f
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, security
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 22a69fe8f6853c02a818bb026b36771cd09632f0
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10824757"
---
# MBAM 2.0 サーバー インフラストラクチャの展開


スタンドアロントポロジ用の Microsoft BitLocker 管理と監視 (MBAM) サーバー機能は、実稼働環境の2台以上のサーバー上のさまざまな構成でインストールできます。 推奨される構成は、スケーラビリティ要件に応じて、運用環境の2つのサーバーです。 MBAM インストールでは、テスト環境でのみ単一のサーバーを使用します。 MBAM Server 機能の展開の計画について詳しくは、「 [mbam 2.0 サーバー展開の計画](planning-for-mbam-20-server-deployment-mbam-2.md)」をご覧ください。

次の図は、推奨される 2 server MBAM 展開を構成する方法の例を示しています。 この構成では、運用環境で最大 20万 MBAM クライアントをサポートしています。 アーキテクチャイメージのサーバー機能とデータベースについては、次のセクションで説明しています。また、これらの機能をインストールすることをお勧めするコンピューターまたはサーバーの下に表示されています。

![mbam 2 2-サーバー展開トポロジ](images/mbam2-3-servers.gif)

## 管理と監視サーバー


このサーバーには、次の機能がインストールされています。

-   **管理と監視サーバー**。 管理と監視のサーバー機能は Windows サーバーにインストールされ、ヘルプデスクの web サイトと監視 web サービスで構成されます。

-   **セルフサービスポータル**。 セルフサービスポータルは Windows サーバーにインストールされます。 セルフサービスポータルを使用すると、クライアントコンピューターのエンドユーザーが、ロックされた BitLocker ボリュームを回復するための回復キーを取得できる web サイトに個別にログオンできます。

## データベースサーバー


このサーバーには、次の機能がインストールされています。

-   **回復データベース**。 回復データベースは、Windows server とサポートされている Microsoft SQLServer のインスタンスにインストールされています。 このデータベースには、MBAM クライアントコンピューターから収集された回復データが格納されます。

-   **コンプライアンスと監査データベース**。 コンプライアンスと監査データベースは、Windows server とサポートされている SQLServer のインスタンスにインストールされています。 このデータベースには、MBAM クライアントコンピューターのコンプライアンスデータが格納されます。 このデータは、主に SQL Server Reporting Services (SSRS) ホストであるレポートに使用されます。

-   **コンプライアンスおよび監査レポート**。 コンプライアンスと監査レポートは、Windows server と、SQL Server Reporting Services (SSRS) 機能がインストールされている SQLServer のサポートされているインスタンスにインストールされています。 これらのレポートには、ヘルプデスクの web サイトから、または SSRS サーバーから直接アクセスできる MBAM レポートが用意されています。

## 管理ワークステーション


以下の機能は管理ワークステーションにインストールされます。これは、Windows server またはクライアントコンピューターとして使用できます。

-   **ポリシーテンプレート**。 ポリシーテンプレートは、BitLocker ドライブ暗号化の MBAM 実装設定を定義するグループポリシーで構成されています。 ポリシーテンプレートは、任意のサーバーまたはワークステーションにインストールできますが、一般的には、サポートされている Windows サーバーまたはクライアントコンピューターである管理ワークステーションにインストールされます。 ワークステーションは専用のコンピュータである必要はありません。

## <a href="" id="---------mbam-client"></a> MBAM クライアント


MBAM クライアントは Windows コンピューターにインストールされ、次のような特徴があります。

-   グループポリシーを使用して、企業内のクライアントコンピューターの BitLocker ドライブ暗号化を適用します。

-   オペレーティングシステムドライブ、固定データドライブ、およびリムーバブルデータ (USB) ドライブの3つの BitLocker データドライブの種類の回復キーを収集します。

-   コンピューターのコンプライアンスデータを収集し、データをレポートシステムに渡します。

## MBAM 2.0 サーバー機能の展開に関するその他のリソース


[MBAM 2.0 の展開](deploying-mbam-20-mbam-2.md)

 

 





