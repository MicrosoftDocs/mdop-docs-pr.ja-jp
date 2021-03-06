---
title: サーバーのセキュリティの計画
description: サーバーのセキュリティの計画
author: dansimp
ms.assetid: c7cd8227-b359-41e7-a8ae-d0d5718a76a2
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 08/30/2016
ms.openlocfilehash: 9bea1bd8287a15385200bbfb425ed8e00fbcdb02
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10815904"
---
# サーバーのセキュリティの計画


環境のセキュリティを強化するには、環境内の潜在的な脅威のリスクを確認する必要があります。 App-v インフラストラクチャのセキュリティを提供するには、特定の App-v セキュリティ機能と、基になるインフラストラクチャのセキュリティプラクティスと機能を使用する必要があります。 インターネットインフォメーションサービス (IIS)、Active Directory ドメインサービス、SQL Server などのサービスの基になるインフラストラクチャをセキュリティで保護すると、アプリの全体的なセキュリティが向上します。

サーバーインストールの既定の設定では、最高レベルのセキュリティが提供されます。 ただし、一部のコンポーネントは、インストールの一部として構成されていない基礎インフラストラクチャに依存しています。 インストール後に次の手順を実行すると、App-v インフラストラクチャのセキュリティが強化されます。

Content ディレクトリには、クライアントにストリーミングされるすべてのパッケージが含まれています。 これらのリソースは、考えられるさまざまなセキュリティの脅威を排除するため、可能な限りセキュリティで保護されている必要があります。 次の一覧では、追加のガイダンスをいくつか紹介します。

-   UNC ベースのパブリッシングまたはストリーミング: このアイテムに対する権限は、環境で最も制限されている必要があります。 NTFS アクセス許可を使用して、コンテンツディレクトリ (ユーザー = 読み取り、管理者 = 読み取りおよび書き込み) に最も制限の厳しいアクセス制御リスト (Acl) を実装します。

-   公開/ストリーミング用に使用される IIS — Windows 統合認証のみをサポートするように IIS を構成します。 IIS サーバーへの匿名アクセスを削除し、NTFS アクセス許可を使用してディレクトリへのアクセスを制限します。

-   RTSP/RTSPS をストリーミングするアプリケーションパッケージ: 認証を要求し、アクセス許可を適用し、必要なグループのみにプロバイダーポリシーへのアクセスを許可するように、アプリ-V プロバイダーポリシーを構成します。 データベースの適切なアクセス許可を使用してアプリケーションを構成します。

管理者権限を持つユーザーの数を最小限に抑えて、データストア内のデータに対する脅威を軽減し、悪意のあるアプリケーションをインフラストラクチャに公開しないようにします。

## Application Virtualization のセキュリティ


App-v では、インフラストラクチャのさまざまな構成要素間でいくつかの通信方法を使用します。 App-v インフラストラクチャを計画する場合は、サーバー間の通信をセキュリティで保護することで、既存のネットワークに既に存在する可能性があるセキュリティリスクを軽減することができます。

### データストア

Application Virtualization Management Server と Application Virtualization 管理サービスは、TCP ポート1433経由の SQL 接続を使用して、データストアと通信します。 管理サーバーは、データストアを使ってアプリケーションデータと構成データを取得し、データベースに使用状況情報を書き込みます。 管理サービスは、App-v インフラストラクチャを構成している管理者の代わりに、データストアと通信します。 データストアには重要な情報が含まれているため、このデータに対する脅威を最小限に抑えることが重要です。

App-v Management Server、管理サービス、データストア間の通信は、インターネットプロトコルセキュリティ (IPsec) を使ってセキュリティで保護することをお勧めします。 具体的には、データストア (SQL) と管理サーバー間、およびデータストアと管理サービス間の通信チャネルをセキュリティで保護するためのポリシーを作成します。 また、IPsec を使用してサーバーとドメインの分離を展開し、すべての App-v インフラストラクチャコンポーネントがセキュリティで保護されたチャネルのみで通信できることを確認することもできます。 IPsec の実装については、次のドキュメントを参照してください。

-   Windows Server2003 の場合は、() を参照してください <https://go.microsoft.com/fwlink/?LinkId=133226> https://go.microsoft.com/fwlink/?LinkId=133226) 。

-   Windows Server2008 の場合は、() を参照してください <https://go.microsoft.com/fwlink/?LinkId=133227> https://go.microsoft.com/fwlink/?LinkId=133227) 。

### コンテンツディレクトリ

App-v Management Server をインストールすると、コンテンツディレクトリの場所が構成されます。 このディレクトリは、仮想化されたアプリケーションパッケージの保存場所です。 この場所は、サーバーに対してローカルにすることも、リモートネットワーク共有に配置することもできます。 したがって、コンテンツディレクトリのリモートの場所との通信をセキュリティで保護するために IPsec を実装します。

また、IIS サーバー上の仮想ディレクトリを使って、クライアントへのパッケージのストリーミングを行うこともできます。 コンテンツ用に作成された仮想ディレクトリがリモートソースにある場合は、IPsec を使って、IIS サーバーとリモート記憶域の場所の間の通信をセキュリティで保護します。

Content ディレクトリには、クライアントにストリーミングされるすべてのパッケージが含まれています。 これらのリソースは、考えられるさまざまなセキュリティの脅威を排除するため、可能な限りセキュリティで保護されている必要があります。

### セキュリティプロトコル

セキュリティで保護された通信を強化するには、RTSPS または HTTPS を使用できます。 RTSPS は、App-v サーバーによって使用されるプロトコルであり、HTTPS は IIS サーバーによって使用されるプロトコルです。 これらのプロトコルは、サーバーからアプリケーションの仮想化デスクトップクライアントにアプリケーションを公開するときに使われます。 目的のプロトコルを決定したら、そのプロトコルを使用する発行サーバーを追加します。

### <a href="" id="configuring-app-v-servers-for-rtsps-"></a>RTSPS の App-v サーバーを構成する

強化されたセキュリティ (TLS など) を使用するようにアプリをインストールまたは構成するには、x.509 V3 証明書を App-v Server にプロビジョニングする必要があります。 サーバーのセキュリティをインストールまたは構成する準備を行う際には、特定の要件を満たす必要があります。 セキュリティで保護されたアプリで証明書を展開して構成するための技術的要件には、次のようなものがあります。

-   証明書が有効である必要があります。 それ以外の場合、クライアントは接続を終了します。

-   証明書には、適切な拡張キー使用法 (EKU)-サーバー認証 (OID 1.3.6.1.5.5.7.3.1) が含まれている必要があります。 それ以外の場合、クライアントは接続を終了します。

-   証明書の完全修飾ドメイン名 (FQDN) は、それがインストールされているサーバーと一致している必要があります。 たとえば、クライアントが通話を発信していても、[ `RTSPS://Myserver.mycompany.com/content/MyApp.sft` **発行先**] フィールドが含まれている場合、 `Myserver1.mycompany.com` クライアントはサーバーに接続せず、 `Myserver.mycompany.com` `Myserver1.mycompany.com` 同じ IP アドレスに解決された場合でも、セッションは終了します。

    **注** ネットワーク負荷分散クラスターで App-v を使用している場合、RTSPS をサポートするために、証明書は*サブジェクト代替名*(san) で構成されている必要があります。 証明機関 (CA) を構成し、San で証明書を作成する方法については、() を参照してください <https://go.microsoft.com/fwlink/?LinkId=133228> https://go.microsoft.com/fwlink/?LinkId=133228) 。

     

-   証明書を App-v server に発行する CA は、サーバーに接続しているクライアントによって信頼されている必要があります。 それ以外の場合、クライアントは接続を終了します。

-   サーバー App-v サービスによるアクセスを有効にするには、*証明書の秘密キー*のアクセス許可を変更する必要があります。 既定では、App-v Management Server サービスと Streaming Server サービスは Network Service アカウントで実行されます。 サーバー上で PKCS \ #10 が生成されると、秘密キーが作成されます。 ローカルシステムグループと管理者グループのみがこのキーにアクセスできます。 これらの既定の Acl は、App-v サーバーがセキュリティで保護された接続を受け入れないようにします。

    **注** 公開キー基盤 (PKI) の構成の詳細については、() を参照してください <https://go.microsoft.com/fwlink/?LinkId=133229> https://go.microsoft.com/fwlink/?LinkId=133229) 。

     

### HTTPS で IIS サーバーを構成する

App-v では、特定のインフラストラクチャ構成で IIS サーバーを使用する場合があります。 IIS サーバーの構成の詳細については、() を参照してください <https://go.microsoft.com/fwlink/?LinkId=133230> https://go.microsoft.com/fwlink/?LinkId=133230) 。

**注** IIS を使って ICO ファイルと OSD ファイルを公開する場合は、OSD = TXT の MIME タイプを構成します。そうしないと、IIS は、ICO ファイルと OSD ファイルをクライアントに提供することを拒否します。

 

### アプリケーションレベルのセキュリティ

特定のアプリケーションをユーザーのデスクトップにストリーミングするようにサーバーを構成することができます。 ただし、アクセス許可は、実際にはアプリケーションレベルではなく、パッケージレベルで許可されています。 特定のアプリケーションはユーザーのデスクトップに公開されないことがありますが、ユーザーにアプリケーションを追加するアクセス許可が与えられているか、クライアントコンピューターの管理者である場合、ユーザーはクライアント上のショートカットを作成して使用して、パッケージ内のすべてのアプリケーションを実行することができます。

## 分散環境への App-V 管理の構成


特定の組織のインフラストラクチャを設計する場合は、app-v management Server をインストールするコンピューター以外のコンピューターに、App-v 管理 Web サービスをインストールできます。 これらの App-v コンポーネントを分離する一般的な理由には、次のようなものがあります。

-   パフォーマンス

-   信頼性

-   対象

-   スケーラビリティ

インフラストラクチャが正常に動作するためには、App-v 管理コンソール、管理サーバー、および管理 Web サービスを分離するには追加の構成が必要です。 サーバーの構成方法の詳細については、「[委任に対して信頼されるようにサーバーを構成する方法](how-to-configure-the-server-to-be-trusted-for-delegation.md)」を参照してください。

## 関連トピック


[セキュリティと保護の計画](planning-for-security-and-protection.md)

 

 





