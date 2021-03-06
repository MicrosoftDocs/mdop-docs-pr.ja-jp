---
title: スタンドアロン構成での MBAM 2.5 の展開
description: スタンドアロン構成で MBAM 2.5 を展開する方法について説明します。
author: Deland-Han
ms.reviewer: dcscontentpm
manager: dansimp
ms.author: delhan
ms.sitesec: library
ms.prod: w10
ms.date: 09/16/2019
ms.openlocfilehash: 905eb7a40483a7a7b499d6dced8472331c87b838
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10826434"
---
# スタンドアロン構成で MBAM 2.5 を展開する

この記事では、スタンドアロン構成で Microsoft BitLocker 管理と監視 (MBAM) 2.5 をインストールするための詳しい手順について説明します。 このガイドでは、2サーバー構成を使用します。 2つのサーバーのいずれかが、Microsoft SQL Server 2012 を実行しているデータベースサーバーになります。 このサーバーは、MBAM データベースとレポートをホストします。 追加のサーバーは、"管理および監視サーバー" と "セルフサービスポータル" をホストしている Windows Server 2012 web サーバーになります。

## MBAM 2.5 サーバーソフトウェアをインストールする前の準備手順

### 手順 1: サーバーのインストールと構成

MBAM 2.5 の構成を開始する前に、両方のサーバーが MBAM システム要件として構成されていることを確認する必要があります。 [Mbam 最小システム要件](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/mbam-25-supported-configurations#-mbam-server-system-requirements)を確認し、これらの要件を満たす構成を選択します。 

#### 手順 1.1: データベースおよびレポートサーバーの前提条件の展開

1. Windows Server 2008 R2 (以降) オペレーティングシステムを実行しているサーバーをインストールして構成します。

2. Windows PowerShell 3.0 をインストールします。

3. 最新の service pack が含まれている Microsoft SQL Server 2008 R2 またはそれ以降のバージョンをインストールします。 MBAM の SQL Server の新しいインスタンスをインストールする場合は、インストールする SQL Server に SQL_Latin1_General_CP1_CI_AS の照合順序が含まれていることを確認してください。 次の SQL Server 機能をインストールする必要があります。

    * データベースエンジン
    * Reporting Services
    * クライアントツールの接続
    * 管理ツール–完了

    > [!Note]
    > 必要に応じて、 [SQL Server で透過データ暗号化 (TDE) 機能](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/mbam-25-security-considerations)をインストールすることもできます。

    SQL Server Reporting Services は、未構成または "SharePoint" モードではなく、"ネイティブ" モードでインストールして構成する必要があります。

    ![必須の SQL Server 機能](images/deploying-MBAM-1.png)

4. 管理と監視の web サイトに SSL を使用する予定がある場合は、管理と監視の web サイトを構成する前に、Secure Sockets Layer (SSL) プロトコルを使用するように SQL Server Reporting Services (SSRS) を構成していることを確認してください。 そうしないと、レポート機能では暗号化された (HTTPS) のではなく、暗号化されていない (HTTP) データトランスポートが使用されます。

    ネイティブモードのレポートサーバーで[Ssl 接続を構成](https://docs.microsoft.com/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server?view=sql-server-2017)し、レポートサーバーで ssl を構成することができます。
    
    > [!Note]
    > 各バージョンの SQL Server 用の SQL Server インストールガイドに従って、SQL Server をインストールできます。 リンクは次のとおりです。
        > * [SQL Server 2014](https://docs.microsoft.com/sql/sql-server/install/planning-a-sql-server-installation?view=sql-server-2014)
        > * [SQL Server 2012](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/bb500442(v=sql.110))
        > * [SQL Server 2008 R2](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/bb500442(v=sql.110))

5. SQL Server のインストール後に、SQL Server でユーザーアカウントをプロビジョニングして、MBAM データベースの構成とデータベースサーバー上のレポートロールのユーザーに対して、次のアクセス許可を割り当てます。

    SQL Server のインスタンスのロール:
        
    * dbcreator
    * processadmin

    SQL Server Reporting Services インスタンスの権限:
    
    * フォルダーを作成する
    * レポートを発行する

データベースサーバーで MBAM 2.5 の役割を構成する準備ができました。 次のサーバーに移動しましょう。

#### 手順 1.2: 管理および監視サーバーの前提条件の展開

[Mbam システム要件ドキュメント](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/mbam-25-supported-configurations#-mbam-server-system-requirements)で説明されているように、ハードウェア構成を満たすサーバーを選びます。 最新の service pack と更新プログラムがインストールされている Windows Server 2008 R2 以降のオペレーティングシステムを実行している必要があります。 サーバーの準備ができたら、次の役割と機能をインストールします。

##### ロール

* Web サーバー (IIS) 管理ツール ([IIS 管理スクリプトとツール] を選びます。)

* Web サーバーの役割サービス

    * 一般的な HTTP 機能<br />
      静的なコンテンツ<br />
      既定のドキュメント

    * アプリケーションの開発<br />
      ASP.NET<br />
      .NET の拡張性<br />
      ISAPI 拡張機能<br />
      ISAPI フィルター<br />
      セキュリティ<br />
      Windows 認証<br />
      フィルターを要求する

    * Web サービス IIS 管理ツール

##### 機能

* .NET Framework 4.5 の機能
  
  * Microsoft .NET Framework 4.5
  
    Windows Server 2012 または Windows Server 2012 R2 の場合、これらのバージョンの Windows Server 用の .NET Framework 4.5 は既にインストールされています。 ただし、有効にする必要があります。
  
    Windows Server 2008 R2 の場合、Windows Server 2008 R2 には .NET Framework 4.5 が含まれていません。 したがって、.NET Framework 4.5 をダウンロードして、個別にインストールする必要があります。
  
  * WCF のアクティブ化<br />
    HTTP アクティベーション<br />
    HTTP 以外のアクティベーション
  
  * TCP ライセンス認証
  
  * Windows プロセスアクティブ化サービス:<br />
    プロセスモデル<br />
    .NET Framework 環境<br />
    構成 Api

セルフサービスポータルを使用するには、 [ASP.NET MVC 4.0 もダウンロードしてインストール](https://go.microsoft.com/fwlink/?linkid=392271)する必要があります。

次の手順では、必須の MBAM ユーザーと Active Directory 内のグループを作成します。

### 手順 2: Active Directory ドメインサービスでユーザーとグループを作成する
 
前提条件の一部として、MBAM で使用される特定の役割とアカウントを定義し、SQL Server のインスタンスで実行されているデータベースや、管理/監視サーバー上で実行されている web アプリケーションなどの特定のサーバーや機能に対するセキュリティとアクセス権を提供する必要があります。

Active Directory に次のグループとユーザーを作成します。 (グループとユーザーには任意の名前を使用できます。)ユーザーは、より多くのユーザー権限を持っている必要はありません。 ドメインユーザーアカウントで十分です。 MBAM 2.5 の構成時にこれらのグループの名前を指定する必要があります。

* **MBAMAppPool**  

  **種類**: ドメインユーザー

  **説明**: コンプライアンスと監査データベースへの読み取り/書き込みアクセス許可を持つドメインユーザー、および回復データベースは、web アプリケーションがこれらのデータベースのデータやレポートにアクセスできるようにします。 これは、web アプリケーションのアプリケーションプールでも使われます。

  **アカウントの役割 (MBAM の構成中)**:

  1. Web サービスアプリケーションプールドメインアカウント

  2. レポートの [コンプライアンスと監査データベース] と [復元データベース] の読み取り/書き込みユーザー

* **Mbamルーティング・ Ser**

  **種類**: ドメインユーザー

  **説明**: コンプライアンスと監査データベースへの読み取り専用アクセス権を持つドメインユーザーは、このデータベースのコンプライアンスおよび監査データにアクセスできるようにレポートを有効にします。 また、ローカル SQL Server Reporting Services インスタンスがコンプライアンスおよび監査データベースにアクセスするために使用するドメインユーザーアカウントでもあります。

  **アカウントの役割 (MBAM の構成中)**:

  1. レポートの読み取り専用ユーザー (コンプライアンスおよび監査データベース)

  2. コンプライアンスと監査データベースドメインのユーザーアカウント

* **MBAMAdvHelpDsk**

  **種類**: ドメイングループ

  **説明**: Mbam Advanced ヘルプデスクユーザーアクセスグループ: メンバーが管理および監視 web サイトのすべての領域にアクセスできるドメインユーザーグループ。 この役割を持つユーザーは、ユーザーのドライブの回復を支援するときに、回復キーのみを入力する必要があります。ユーザーのドメインとユーザー名は入力する必要はありません。 Mbam ヘルプデスクユーザーグループと MBAM Advanced ヘルプデスクユーザーグループの両方のメンバーである場合、MBAM Advanced ヘルプデスクのユーザーグループの権限は、MBAM ヘルプデスクのグループ権限よりも優先されます。

  **アカウントの役割 (mbam の構成中)**: Mbam Advanced ヘルプデスクユーザー

* **MBAMHelpDsk**

  **種類**: ドメイングループ

  **説明**: Mbam ヘルプデスクユーザーアクセスグループ: mbam 管理と監視 web サイトの TPM とドライブの回復領域にアクセスできるメンバーのドメインユーザーグループ。 この役割を持つユーザーは、いずれかのオプションを使用する場合にすべてのフィールドに入力する必要があります。 これには、ユーザーのドメインとアカウント名が含まれます。

  **アカウントの役割 (mbam の構成中)**: Mbam ヘルプデスクユーザー

* **Mbamgrp**

  **種類**: ドメイングループ

  **説明**: 管理と監視の web サイトの [レポート] 領域にあるレポートへの読み取り専用アクセス権を持つメンバーのドメインユーザーグループ。

  **アカウントの役割 (MBAM の構成中)**:

  1. レポート読み取り専用ドメインアクセスグループ

  2. MBAM レポートユーザーアクセスグループ

### 手順 3 (オプション): 管理および監視サーバーで SSL 証明書を構成してインストールする

必須ではありませんが、MBAM クライアントと、管理/監視 Web サイトとセルフサービスポータル web サイト間の通信をセキュリティで保護するために、証明書を使用することを強くお勧めします。 セキュリティ上の明白な理由から、自己署名の証明書を使用することはお勧めしません。 信頼できる証明機関から提供された Web サーバーの種類の証明書を使用することをお勧めします。 これを行うには、 [KB 2754259](https://support.microsoft.com/help/2754259)から、「証明機関によって承認された証明書を使用する」セクションを参照してください。

証明書が発行されたら、管理/監視サーバーの個人ストアに証明書を追加する必要があります。 証明書を追加するには、ローカルコンピューターの証明書ストアを開きます。 これを行うためには、次の手順を実行します。

1. [スタート] を右クリックし、[実行] を選択します。

   ![選択する ](images/deploying-MBAM-2.png)

2. "MMC.EXE" (引用符は不要) と入力して、[ **OK]** を選択します。

   ![[実行] ボックス](images/deploying-MBAM-3.png) 

3. 開いた新しい MMC で [**ファイル**] を選択し、[**スナップインの追加と削除**] を選択します。
   
   ![選択する](images/deploying-MBAM-4.png)

4. [**証明書**] スナップインを強調表示し、[**追加**] を選択します。

   ![[スナップインの追加または削除] ウィンドウ](images/deploying-MBAM-5.png)

5. [**コンピューターアカウント**] オプションを選択し、[**次へ**] を選択します。
   
   ![[証明書] スナップインウィンドウ](images/deploying-MBAM-6.png)

6. 次の画面で [**ローカルコンピューター** ] を選択し、[**完了**] を選択します。
   
   ![[コンピューター] ウィンドウを選ぶ](images/deploying-MBAM-7.png)

7. これで、[証明書] スナップインが追加されました。 これにより、コンピューターの証明書ストア内のすべての証明書を操作できるようになります。

   ![[スナップインの追加または削除] ウィンドウ](images/deploying-MBAM-8.png)

8. Web サーバー証明書をコンピューターの証明書ストアにインポートします。

   証明書スナップインにアクセスできるようになったので、コンピューターの証明書ストアに web サーバー証明書をインポートします。 そのためには、次の手順に従います。

9. [証明書 (ローカルコンピューター)] スナップインを開き、[**個人用**]、[**証明書**] の順に参照します。
   
   ![証明書 (ローカルコンピューター) スナップインウィンドウ](images/deploying-MBAM-9.png)

   > [!Note]
   > 証明書スナップインが表示されない場合があります。 見つからない場合は、証明書はインストールされません。

10. [**証明書**] を右クリックし、[**すべてのタスク**] を選択して、[**インポート**] を選択します。

    ![証明書 (ローカルコンピューター) スナップインウィンドウ](images/deploying-MBAM-10.png)

11. ウィザードが起動したら、[**次へ**] を選びます。 サーバー証明書と秘密キーを含む、作成したファイルを参照し、[**次へ**] を選択します。

    ![証明書のインポートウィザードウィンドウ](images/deploying-MBAM-11.png)

12. ファイルを作成したときに指定したパスワードを入力します。

   ![パスワードウィンドウを入力する](images/deploying-MBAM-12.png)

   > [!Note]
   > このコンピューターからもう一度キーペアをエクスポートできるようにするには、[エクスポート可能な**キーとしてマーク**する] オプションがオンになっていることを確認します。 追加されたセキュリティ対策として、秘密キーのバックアップを作成できないように、このオプションをオフのままにしておくこともできます。
 
13. [**次へ**] を選択し、証明書を保存する**証明書ストア**を選択します。

    ![証明書のインポートウィザードウィンドウ](images/deploying-MBAM-13.png)

    > [!Note]
    > Web サーバーの証明書であるため、[**個人用**] を選択する必要があります。 証明書階層に証明書が含まれている場合は、このストアにも追加されます。
 
14. [**次へ**] を選択し、[**完了**] を選択します。

    ![証明書のインポートウィザードウィンドウ](images/deploying-MBAM-14.png)

Web サーバーのサーバー証明書が個人証明書の一覧に表示されるようになります。 サーバーの共通名で示されます。 (この情報は、証明書の [件名] セクションで確認できます)。

詳細については、以下をご覧ください。

[MBAM 2.5 のセキュリティに関する考慮事項](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/mbam-25-security-considerations)

[MBAM Web サイトをセキュリティで保護する方法の計画](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/planning-how-to-secure-the-mbam-websites)

次の手順では、アプリケーションプールアカウントのサービスプリンシパル名を登録します。

### 手順 4: MBAM Web サーバーの SSL 証明書を構成する

クライアントとサーバーの間で SSL 通信を使用している場合は、証明書に拡張キー使用 Oid (1.3.6.1.5.5.7.3.1) と (1.3.6.1.5.5.7.3.2) が含まれていることを確認する必要があります。 つまり、サーバー認証とクライアント認証が追加されていることを確認する必要があります。

サービスの Url を参照しようとしたときに証明書エラーが表示される場合は、別の名前に発行された証明書を使用しているか、正しくない URL を使用して参照していることを確認します。

ブラウザーでは証明書のエラーメッセージが表示されますが、続行することはできますが、MBAM web サービスは証明書エラーを無視せず、接続をブロックします。 MBAM クライアントの MBAM 管理イベントログでは、証明書に関連するエラーが発生します。 エイリアスを使って管理および監視サーバーに接続している場合は、エイリアス名に証明書を発行する必要があります。 つまり、証明書のサブジェクト名はエイリアス名であり、ローカルサーバーの DNS 名は証明書の**サブジェクトの別名**フィールドに追加される必要があります。

例:

仮想名が "bitlocker.contoso.com" で、MBAM 管理および監視サーバー名が "adminserver.contoso.com" である場合、証明書は bitlocker.contoso.com (サブジェクト名) に発行され、adminserver.contoso.com は証明書のサブジェクトの [**代替名**] フィールドに追加される必要があります。

同様に、ロードバランサーを使用して負荷を分散するために、複数の管理サーバーと監視サーバーがインストールされている場合は、仮想名に SSL 証明書を発行する必要があります。 つまり、証明書の subject name フィールドには仮想名を指定し、すべてのローカルサーバーの名前を証明書の**サブジェクトの別名**フィールドに追加する必要があります。

例:

仮想名が "bitlocker.contoso.com" で、サーバーが "adminserver1.contoso.com" および "adminiserver2.contoso.com" である場合、証明書は bitlocker.contoso.com (サブジェクト名) と adminserver1.contoso.com に発行され、adminiserver2.contoso.com は証明書の**サブジェクトの別名**フィールドに追加される必要があります。

MBAM を使用して SSL 通信を構成する手順については、次のサポート技術情報の記事「 [KB 2754259](https://support.microsoft.com/help/2754259)」を参照してください。

### 手順 5: アプリケーションプールアカウントの SPN を登録し、制約付き委任を構成する

> [!Note]
> 制約付き委任は、2.5 に対してのみ必須であり、2.5 Service Pack 1 以降では必須ではありません。

MBAM サーバーが管理および監視 Web サイトとセルフサービスポータルからの通信を認証できるようにするには、web アプリケーションプールに使用しているドメインアカウントの下で、ホスト名にサービスプリンシパル名 (SPN) を登録する必要があります。 次の記事では、Spn を登録するための詳しい手順について説明します。 [MBAM Web サイトをセキュリティで保護する方法を計画](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/planning-how-to-secure-the-mbam-websites)する

SPN を構成したら、SPN の制約付き委任を設定する必要があります。 これを行うためには、次の手順を実行します。

1. Active Directory に移動して、前の手順で MBAM web サイト用に構成したアプリプールの資格情報を見つけます。

2. 資格情報を右クリックし、[**プロパティ**] を選択します。

3. [**委任**] タブを選択します。

4. [Kerberos 認証] のオプションを選択します。

5. [**参照**] を選択し、アプリプールの資格情報をもう一度参照します。 その後、アプリプールの資格アカウントに設定されているすべての Spn を確認する必要があります。 (SPN は "http/bitlocker. .com" と似ている必要があります)。 MBAM インストール時に指定したホスト名と同じ SPN を強調表示します。

6. **[OK]** を選択します。

前提条件については、こちらをお勧めします。 次の手順では、MBAM ソフトウェアをサーバーにインストールして構成します。

## MBAM 2.5 サーバーソフトウェアのインストールと構成

### 手順 6: MBAM 2.5 サーバーソフトウェアをインストールする 

Microsoft BitLocker の管理と監視のセットアップウィザードを使って、データベースサーバーと管理および監視サーバーの両方で MBAM サーバーソフトウェアをインストールするには、次の手順を実行します。

1. MBAM をインストールするサーバーで MBAMserversetup.exe を実行して、Microsoft BitLocker の管理と監視のセットアップウィザードを開始します。

2. [ようこそ] ページで、[**次へ**] を選びます。

3. Microsoft ソフトウェアライセンス条項を読んで同意し、[**次へ**] を選択してインストールを続行します。

4. 更新プログラムを確認するときに Microsoft Update を使用するかどうかを決定し、[**次へ**] を選択します。

5. カスタマーエクスペリエンス向上プログラムに参加するかどうかを決定し、[**次へ**] を選択します。

6. インストールを開始するには、[**インストール**] を選択します。

7. MBAM サーバーソフトウェアのインストールが完了した後でサーバーの機能を構成するには、[**ウィザードを終了した後に MBAM サーバーの構成を実行**する] チェックボックスをオンにします。 または、[**スタート**] メニューで作成した**Mbam server 構成**ショートカットを使用して、mbam を後で構成することもできます。

8. [**完了**] を選びます。

詳細については、「 [MBAM 2.5 サーバーソフトウェアをインストールする](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/installing-the-mbam-25-server-software)」を参照してください。

### 手順 7: MBAM 2.5 データベースとレポートの役割を構成する

この手順では、MBAM ウィザードを使用して、MBAM 2.5 データベースとレポートコンポーネントを構成します。

1. ウィザードを使用して、コンプライアンスデータベースおよび監査データベースと回復データベースを構成します。
   
   1. データベースを構成するサーバーで、 **Mbam サーバー構成ウィザード**を起動します。 [**スタート**] メニューで [ **Mbam Server 構成**] を選択してウィザードを開くことができます。

   2. [**新機能の追加**] を選択し、[**コンプライアンスと監査データベース**]、[**回復データベースとレポート**] の順に選択して、[**次へ**] を選択します。 ウィザードは、データベースのすべての前提条件が満たされていることを確認します。

   3. 前提条件の確認が正常に完了したら、[**次へ**] を選択して続行します。 それ以外の場合は、不足している前提条件を解決し、[**前提条件の確認] をもう一度**選びます。
   
   4. 次の説明を使用して、ウィザードにフィールド値を入力します。

2. コンプライアンスと監査データベース

   |フィールド   |説明|
   |-------|-------|
   |SQL Server 名 |コンプライアンスと監査データベースを構成しているサーバーの名前。 <br /> SQL Server ポートで着信受信トラフィックを有効にするには、コンプライアンスおよび監査データベースコンピューターで例外を追加する必要があります。 既定のポート番号は1433です。|
   |SQL Server データベースインスタンス    |コンプライアンスと監査データが保存されるデータベースインスタンスの名前です。 既定のインスタンスを使用している場合は、このフィールドを空白のままにしておく必要があります。 データベース情報を配置する場所も指定する必要があります。|
   |データベース名   |コンプライアンスデータを格納するデータベースの名前。 この情報は、後の手順で指定する必要があるため、ここで指定したデータベースの名前をメモしておく必要があります。|
   |読み取り/書き込み権限のドメインユーザーまたはグループ  |手順2で構成した MBAMAppPool ユーザーの名前を指定します。|
   |読み取り専用アクセスドメインのユーザーまたはグループ   |手順2で構成した Mbamルーブル Ser ユーザーの名前を指定します。|

3. 回復データベース。

   |フィールド   |説明|
   |-----|-----|
   |SQL Server 名 |回復用データベースを構成しているサーバーの名前。 SQL Server ポートで受信トラフィックの着信を有効にするには、回復データベースコンピューターで例外を追加する必要があります。 既定のポート番号は1433です。|
   |SQL Server データベースインスタンス    |回復データが保存されるデータベースインスタンスの名前。 既定のインスタンスを使用している場合は、このフィールドを空白のままにしておく必要があります。 データベース情報を配置する場所も指定する必要があります。|
   |データベース名   |回復データを格納するデータベースの名前。|
   |読み取り/書き込み権限のドメインユーザーまたはグループ  |このデータベースの読み取り/書き込みアクセス許可を持つドメインユーザーまたはグループ。このデータベースのデータとレポートにアクセスできるように、web アプリケーションを有効にします。 <br />このフィールドにユーザーを入力する場合は、[ **Web アプリケーションの構成**] ページの [ **web サービスアプリケーションプールドメインアカウント**] フィールドの値と同じ値である必要があります。 <br />このフィールドにグループを入力した場合、[ **Web アプリケーションの構成**] ページの [ **web サービスアプリケーションプールのドメインアカウント**] フィールドの値は、このフィールドに入力するグループのメンバーである必要があります。|
   
   入力が完了したら、[**次へ**] を選択します。 ウィザードは、データベースのすべての前提条件が満たされていることを確認します。
   
   前提条件の確認が正常に完了したら、[**次へ**] を選択して続行します。 それ以外の場合は、不足している前提条件を解決して、[**次へ**] をもう一度選びます。

4. いう.

   |フィールド   |説明|
   |----|----|
   |SQL Server Reporting Services インスタンス  |レポートが構成される SQL Server Reporting Services のインスタンス。 既定のインスタンスを使用している場合は、このフィールドを空白のままにしておく必要があります。|
   |レポート役割のドメイングループ |手順2で説明したように、Mbamgrp Grp の名前を指定します。|
   |SQL Server 名 |コンプライアンスおよび監査データベースが構成されているサーバーの名前。|
   |SQL Server データベースインスタンス    |コンプライアンスと監査データが構成されているデータベースインスタンスの名前。 既定のインスタンスを使用している場合は、このフィールドを空白のままにしておく必要があります。 <br />レポートサーバーのポートで受信トラフィックを有効にするには、レポートコンピューターで例外を追加する必要があります。 (既定のポートは80です)。|
   |データベース名|  コンプライアンスおよび監査データベースの名前。 既定では、データベース名は MBAM コンプライアンスの状態です。|
   |コンプライアンスと監査データベースのドメインアカウント    |手順2で構成した Mbamルーブル Ser ユーザーの名前を指定します。|
   
   入力が完了したら、[**次へ**] を選択します。 ウィザードは、レポート機能のすべての前提条件が満たされていることを確認します。 続行するには、[次へ] を選択します。 [**概要**] ページで、追加される機能を確認します。
   
   詳細については、「 [MBAM 2.5 データベースを構成する方法](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/how-to-configure-the-mbam-25-databases)」を参照してください。

### 手順 8: MBAM 2.5 Web アプリケーションの役割を構成する

1. Web アプリケーションを構成するサーバーで、MBAM サーバー構成ウィザードを起動します。 [**スタート**] メニューで [ **Mbam Server 構成**] を選択してウィザードを開くことができます。

2. [**新しい機能の追加**] を選択し、[**管理と監視の Web サイト**と**セルフサービスポータル**] を選択して、[**次へ**] を選択します。 ウィザードは、データベースのすべての前提条件が満たされていることを確認します。

3. 前提条件の確認が正常に完了したら、[**次へ**] を選択して続行します。 それ以外の場合は、不足している前提条件を解決し、[**前提条件の確認] をもう一度**選びます。

4. ウィザードでフィールドの値を入力するには、次の説明を使用します。

   |フィールド   |説明|
   |-----|-----|
   |セキュリティ証明書    |手順3で以前に作成した証明書を選択して、web サービスと、管理および監視 Web サイトを構成しているサーバー間の通信を暗号化することができます。 [証明書を使用しない] を選択した場合、web 通信がセキュリティで保護されない場合があります。|
   |ホスト名   |管理と監視の Web サイトを構成しているホストコンピューターの名前。 <br />コンピュータのホスト名にする必要はありません。何でもかまいません。 ただし、ホスト名がコンピューターの netbios 名と異なる場合は、A レコードを作成し、SPN が netbios 名ではなくカスタムホスト名を使用していることを確認する必要があります。 これは、ロードバランシングシナリオで一般的です。|
   |インストールパス   |管理と監視の Web サイトをインストールするパス。|
   |Port    |Web サイトの通信に使用するポート番号。 <br /> 指定したポートを介した通信を有効にするには、ファイアウォールの例外を設定する必要があります。|
   |Web サービスアプリケーションプールのドメインアカウントとパスワード    |手順2で構成した MBAMAppPool ユーザーのユーザーアカウントとパスワードを指定します。 <br /> セキュリティを向上させるには、資格情報で指定されているアカウントに、制限付きのユーザー権限を設定します。 また、アカウントのパスワードを無期限に設定します。|

5. 組み込みの IIS_IUSRS アカウントまたはアプリケーションプールアカウントが、[**認証後にクライアントを偽装**する] および **[バッチジョブ**のローカルセキュリティ設定] に追加されていることを確認します。

   ローカルセキュリティ設定にアカウントが追加されたかどうかを確認するには、**ローカルセキュリティポリシーエディター**を開き、[**ローカルポリシー** ] ノードを展開し、[**ユーザー権利の割り当て**] ノードを選択して、右側のウィンドウで [**認証後にクライアントを偽装**し、**バッチジョブとしてログオン**します] ポリシーをダブル選択します。

6. 次のフィールドの説明を使用して、コンプライアンスと監査データベース用にウィザードの接続情報を構成します。
   |フィールド   |説明|
   |------|------|
   |SQL Server 名 |コンプライアンスおよび監査データベースが構成されているサーバーの名前。|
   |SQL Server データベースインスタンス    |SQL Server のインスタンスの名前 (など \<Server Name\> ) と、コンプライアンスおよび監査データベースが構成されていること。 既定のインスタンスを使用している場合は、空白のままにします。|
   |データベース名   |コンプライアンスおよび監査データベースの名前。 既定では、"MBAM コンプライアンスステータス" となります。|

7. 次のフィールドの説明を使用して、回復データベースのウィザードで接続情報を構成します。
   |フィールド   |説明|
   |----|----|
   |SQL Server 名 |回復データベースが構成されているサーバーの名前。|
   |SQL Server データベースインスタンス    |回復データベースが構成されている SQL Server (など) のインスタンスの名前 \<Server Name\> 。 既定のインスタンスを使用している場合は、空白のままにします。|
   |データベース名   |回復データベースの名前。 既定では、"MBAM Recovery and Hardware" というメッセージがあります。|

8. 次の説明を使用して、管理と監視の Web サイトを構成するためのウィザードのフィールド値を入力します。
   |フィールド   |説明|
   |----|----|
   |高度なヘルプデスクの役割ドメイングループ |手順2で構成した MBAMAdvHelpDsk グループの名前を指定します。|
   |ヘルプデスクの役割ドメイングループ  |手順2で構成した MBAMHelpDsk グループの名前を指定します。|
   |System Center Configuration Manager の統合を使用する |このチェックボックスをオフにします。     |
   |レポート役割のドメイングループ |手順2で構成した Mbamgrp グループの名前を指定します。    |
   |SQL Server Reporting Services の URL   |MBAM レポートが構成されている SSRS サーバーの Web サービス URL を指定します。 この情報は、データベースサーバーの Reporting Services 構成マネージャーにログインすることで確認できます。 <br /> 完全修飾ドメイン名の例:https://MyReportServer.Contoso.com/ReportServer <br />カスタムホスト名の例:https://MyReportServer/ReportServer|
   |仮想ディレクトリ   |管理と監視の Web サイトの仮想ディレクトリ。 この名前は、サーバー上の web サイトの物理ディレクトリに対応し、web サイトのホスト名に追加されます。 以下に例を示します。 <br />http (s)// *\<host name\>* :/ *\<port\>* ヘルプデスク/ <br />仮想ディレクトリを指定しない場合は、値のヘルプデスクが使用されます。     |

9. 次の説明を使用して、セルフサービスポータルを構成するためのウィザードのフィールド値を入力します。

   |フィールド   |説明|
   |----|----|
   |仮想ディレクトリ   |Web アプリケーションの仮想ディレクトリ。 この名前は、サーバー上の web サイトの物理ディレクトリに対応し、web サイトのホスト名に追加されます。 以下に例を示します。<br />http (s)// *\<host name\>* :/ *\<port\>* Selfservice/<br /> 仮想ディレクトリを指定しない場合は、"SelfService" という値が使用されます。|

10. 入力が完了したら、[**次へ**] を選択します。 ウィザードは、web アプリケーションのすべての前提条件が満たされていることを確認します。

11. [**次へ**] を選択して続行します。

12. [**概要**] ページで、追加される機能を確認します。

13. [**追加**] を選択して web アプリケーションをサーバーに追加し、[**閉じる**] を選択します。

## MBAM 2.5 サーバーソフトウェアをインストールした後の手順のカスタマイズと検証

### 手順 9: 組織用のセルフサーバーポータルをカスタマイズする

ユーザー設定の通知テキスト、会社名、詳細情報へのポインターなどを追加してセルフサービスポータルをカスタマイズする方法については、「[組織のためのセルフサービスポータルのカスタマイズ](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/customizing-the-self-service-portal-for-your-organization)」を参照してください。
 
### 手順 10: クライアントコンピューターが CDN にアクセスできない場合に、セルフサーバーポータルを構成する 

クライアントコンピューターが Microsoft AJAX コンテンツ配信ネットワーク (CDN) にアクセスできるかどうかを確認します。 CDN は、特定の JavaScript ファイルに必要なアクセス権をセルフサービスポータルに提供します。 クライアントコンピューターが CDN にアクセスできないときにセルフサービスポータルを構成しないと、ユーザーがサインインしたときの会社名とアカウントのみが表示されます。 エラーメッセージは表示されません。

次のいずれかの操作を行います。

* クライアントコンピューターで CDN にアクセスできる場合は、何も行いません。 セルフサービスポータルの構成が完了しました。

* クライアントコンピューターが CDN にアクセスできない場合は、[クライアントコンピューターが Microsoft コンテンツ配信ネットワークにアクセスできない場合に、「セルフサービスポータルを構成する方法](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/how-to-configure-the-self-service-portal-when-client-computers-cannot-access-the-microsoft-content-delivery-network)」の手順に従います。

### 手順 11: MBAM 2.5 サーバー機能の構成を確認する 

スタンドアロントポロジを使用するために MBAM サーバー展開を検証するには、次の手順を実行します。

1. Mbam 機能が展開されている各サーバーで、[**コントロールパネル**プログラム] の [  >  **Programs**  >  **プログラムと機能**] を選択します。 **Microsoft BitLocker の管理と監視**が [**プログラムと機能**] の一覧に表示されることを確認します。
   > [!Note]
   > 検証を実行するには、各サーバーのローカルコンピューターの管理者資格情報を持つドメインアカウントを使用する必要があります。

2. 回復データベースが構成されているサーバーで、SQL Server Management Studio を開き、 **Mbam 回復とハードウェア**データベースが構成されていることを確認します。

3. コンプライアンスと監査データベースが構成されているサーバー om で SQL Server Management Studio を開き、MBAM コンプライアンスステータスデータベースが構成されていることを確認します。

4. レポート機能が構成されているサーバーの onm で、管理者の資格情報を使用して web ブラウザーを開き、SQL Server Reporting Services サイトのホームページを参照します。
   
   SQL Server Reporting Services サイトインスタンスの既定のホームページの場所は、次のようになります。 http (s)// *\<MBAM Reports Server Name\>* :/:/ *\<port\>* レポート .aspx
   
   実際の URL を確認するには、Reporting Services 構成マネージャーツールを使用し、セットアップ時に指定したインスタンスを選択します。
   
5. Microsoft BitLocker の管理と監視という名前のレポートフォルダーに、MaltaDataSource という名前のデータソースが含まれていることを確認します。 このデータソースには、言語ロケール (たとえば、en-us) を表す名前を持つフォルダーが含まれます。 レポートは、言語フォルダーにあります。

   > [!Note]
   > SQL Server Reporting Services (SSRS) が名前付きインスタンスとして構成されている場合、URL は次のようになります。 http (s):// \<MBAM Reports Server Name\> : \<port\> /Reports_\<SSRS Instance Name\>
   >
   > SSRS が Secure Socket Layer (SSL) を使用するように構成されていない場合、MBAM サーバーをインストールするときに、レポートの URL は "HTTPS" ではなく "HTTP" に設定されます。 その後、管理と監視の Web サイト (ヘルプデスクとも呼ばれます) に移動し、レポートを選択すると、"セキュリティ保護されたコンテンツのみが表示されます" というメッセージが表示されます。 レポートを表示するには、[**すべてのコンテンツを表示**] を選択します。

6. [Web サイトの管理と監視] 機能が構成されているサーバーで、サーバーマネージャーを実行し、[**役割**] を参照して、[ **Web サーバー (iis)**]  >  **インターネットインフォメーションサービス (iis** ) マネージャーを選択します。

7. [**接続**] で、[サイト] を参照 \<computer name\> し、[ **Sites**  >  **Microsoft BitLocker の管理と監視**] を選びます。 次の内容が表示されていることを確認します。

   * Mbam管理サービス
   * MBAMComplianceStatusService
   * Mbamrecoveryandハードウェアサービス

8. 管理と監視の Web サイトとセルフサービスポータルが構成されているサーバーで、管理者の資格情報を使用して web ブラウザーを開きます。

9. 次の web サイトを参照して、正常に読み込まれていることを確認します。
   * https (s)// \<MBAM Administration Server Name\> :/ \<port\> helpデスク/(ナビゲーションとレポートの各リンクを確認する)
   * http (s)// \<MBAM Administration Server Name\> :/ \<port\> Selfservice/

   > [!Note]
   > ネットワーク暗号化されていない既定のポートでサーバー機能を構成していることを前提としています。 異なるポートまたは仮想ディレクトリにサーバー機能を構成した場合は、適切なポートを含めるように Url を変更します。 たとえば、次のようにします。 http (s)// \<host name\> :/ \<port\> helpデスク/http (s)://://///////////////// \<host name\> \<port\> / \<virtualdirectory\> サーバー機能がネットワーク暗号化を使用するように構成されている場合は、http://
   
10. 次の web サービスを参照して、正しく読み込まれていることを確認します。 サービスが実行されていることを示すページが開きます。 ただし、このページにはメタデータは表示されません。

    * http (s):// \<MBAM Administration Server Name> :/ \<port> mbam管理サービス/管理サービス
    * http (s):// \<MBAM Administration Server Name> : \<port> /MBAMUserSupportService/UserSupportService.svc
    * http (s):// \<MBAM Administration Server Name> : \<port> /MBAMComplianceStatusService/StatusReportingService.svc
    * http (s):// \<MBAM Administration Server Name> : \<port> /MBAMRecoveryAndHardwareService/CoreService.svc

### 手順 12: MBAM グループポリシーテンプレートを構成する

MBAM を展開するには、BitLocker ドライブ暗号化の MBAM 実装設定を定義するグループポリシー設定を設定する必要があります。 このタスクを完了するには、MBAM グループポリシーテンプレートを、グループポリシー管理コンソール (GPMC) または Advanced グループポリシー管理 (AGPM) を実行できるサーバーまたはワークステーションにコピーして、設定を編集する必要があります。

> [!Important]
> **BitLocker ドライブ暗号化**ノードのグループポリシー設定を変更しないと、mbam が正常に動作しません。 [ **MDOP mbam (BitLocker Management)** ] ノードでグループポリシー設定を構成すると、mbam が自動的に**bitlocker ドライブ暗号化**設定を構成します。
 
#### MBAM 2.5 グループポリシーテンプレートをコピーする

MBAM クライアントをインストールする前に、MBAM 固有のグループポリシーオブジェクト (Gpo) を管理ワークステーションにコピーする必要があります。 これらの Gpo は、BitLocker の MBAM 実装設定を定義します。 グループポリシーテンプレートは、サポートされている Windows ベースのサーバーまたはクライアントコンピューターであり、グループポリシー管理コンソール (GPMC) または高度なグループポリシー管理 (AGPM) を実行できる任意のサーバーまたはワークステーションにコピーできます。

詳細については、「 [MBAM 2.5 グループポリシーテンプレートをコピーする](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/copying-the-mbam-25-group-policy-templates)」を参照してください。
 
#### MBAM 2.5 GPO 設定の編集

必要な Gpo を作成したら、MBAM グループポリシー設定を組織のクライアントコンピューターに展開する必要があります。 Gpo を表示および作成するには、グループポリシー管理コンソール (GPMC) または Advanced グループポリシー管理 (AGPM) がインストールされている必要があります。

詳細については、「 [mbam 2.5 グループポリシーの設定を編集する](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/editing-the-mbam-25-group-policy-settings)」と「 [Mbam 2.5 グループポリシーの要件を計画](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/planning-for-mbam-25-group-policy-requirements)する」を参照してください。
 
### 手順 13: MBAM 2.5 クライアントを展開する

Microsoft BitLocker の管理と監視クライアントソフトウェアを展開するときには、組織内のコンピューターで BitLocker を有効にするには、ユーザーがコンピューターを受け取る前に、またはグループポリシーを構成し、エンタープライズソフトウェア展開システムを使用して MBAM クライアントソフトウェアを展開することができます。
 
#### デスクトップまたはポータブルコンピューターに MBAM クライアントを展開する

グループポリシー設定を構成した後は、Microsoft System Center 2012 構成マネージャーや Active Directory ドメインサービス (AD DS) などのエンタープライズソフトウェア展開システム製品を使用して、MBAM クライアントインストールの Windows インストーラーファイルをターゲットコンピューターに展開することができます。 32ビットまたは64ビットの MbamClientSetup.exe ファイルまたは32ビットまたは64ビットの MBAMClient.msi ファイルを使用できます。 これらは、MBAM クライアントソフトウェアと共に提供されます。

詳細については、「 [MBAM クライアントをデスクトップコンピューターまたはノート pc に展開する方法](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/how-to-deploy-the-mbam-client-to-desktop-or-laptop-computers-mbam-25)」を参照してください。
 
#### Windows 展開の一部として MBAM クライアントを展開する

コンピューターが送受信され、中央で構成されている組織では、ユーザーデータが書き込まれる前に、各コンピューター上の BitLocker ドライブ暗号化を管理するために MBAM クライアントをインストールできます。 このプロセスの利点は、すべてのコンピューターが BitLocker に準拠していることです。 この方法では、管理者がコンピューターを既に暗号化しているため、ユーザー操作に依存することはありません。 このシナリオの主な前提となるのは、組織のポリシーによって、コンピューターがユーザーに配信される前に企業の Windows イメージをインストールすることです。 グループポリシー設定が PIN を要求するように構成されている場合、ユーザーはポリシーを受信した後に PIN を設定するように求められます。

詳細については、「 [Windows 展開の一部として MBAM クライアントを展開する方法](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/how-to-enable-bitlocker-by-using-mbam-as-part-of-a-windows-deploymentmbam-25)」を参照してください。
 
#### コマンドラインを使用して MBAM クライアントを展開する方法

詳細については、[コマンドラインを使用して MBAM クライアントを展開する方法](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/how-to-deploy-the-mbam-client-by-using-a-command-line)に関する記事を参照してください。

#### クライアントの展開後

展開アクティビティが完了したら、次のログを確認して、クライアントが MBAM データベースに正常に報告しているかどうかを確認する必要があります。

## FAQ

### 負荷分散される IIS サーバーを作成する方法

* SPN はフレンドリ名 (例: bitlocker.corp.net) にのみ登録する必要があります。また、個々の IIS サーバーに登録することはできません。

* 証明書が使用されている場合、証明書には、[読み込みバランス] グループのすべての IIS サーバーの [**サブジェクトの代替名**] フィールドに入力されている FQDN と NetBIOS 名と、フレンドリ名 (例: bitlocker.corp.net) が含まれている必要があります。 そうしないと、負荷分散されたアドレスを参照したときに、証明書がブラウザーによって信頼されていないと報告されます。

詳細については、「 [IIS ネットワーク負荷分散](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/planning-for-mbam-25-high-availability#a-href-idbkmk-load-balanceaiis-network-load-balancing)と[アプリケーションプールアカウントの spn の登録](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/planning-how-to-secure-the-mbam-websites#registering-spns-for-the-application-pool-account)」を参照してください。

### 証明書を構成する方法

* 2つの証明書を持っている必要があります。 SQL server には1つの証明書が使用され、もう1つは IIS 用に使用されます。 MBAM インストールを開始する前に、これらのユーザーをインストールする必要があります。

* インストーラーを使用して、手動で web.config ファイルを編集するのではなく、IIS 構成に証明書を追加することをお勧めします。

* 証明書の "発行先" フィールドがサーバーの名前と一致しない場合、その証明書は MBAM コンフィギュレーターによって承認されません。 この場合は、一時的に IIS コンソールから自己署名証明書を作成し、それをコンフィギュレーターで使用します。 この操作を行うと、Web アプリが SSL と HTTPS 用にインストールされていることが確認されます。 その後、MBAM Web サイトの [IIS バインド] から証明書を1つに変更できます。

### インストールに必要な SQL の権限

MBAM アプリプールのアカウントを作成して、SecurityAdmin、Public、および DBCreator のアクセス許可のみを付与します。

詳細については、「 [Mbam データベースの構成–最低限の権限](https://blogs.technet.microsoft.com/dubaisec/2016/02/02/mbam-database-configuration-minimum-permissions/)」を参照してください。

> [!Note]
> * 場合によっては、最初のインストールとアップグレードの操作で、より多くの権限が必要になります。
> * インストールの一時 SA を持つアカウントを使用します。
> * SQL Server を変更するための十分な権限がないため、ユーザーアカウントのコンテキストでコンフィギュレーターを開始しないでください。これにより、インストールエラーが発生します。
> * SQL Server に対する権限を持つアカウントを使用してログオンする必要があります。 SQL Server データベースのみを作成または更新するには、MBAM コンフィギュレーターをリモートで実行します。 SSRS サーバーの場合、mbam SSRS レポートをインストールまたは更新するには、MBAM をインストールして、ローカルコンフィギュレーターを実行する必要があります。

### SPN の登録に必要なアクセス許可

IIS ポータルをインストールするために使用されるアカウントには、"ServicePrincipalName の書き込み" と "検証された SPN" アクセス許可を設定する必要があります。 これらのアクセス許可がない場合、インストールによって、SPN を登録できないことを示す警告メッセージが返されます。

> [!Note]
> この警告メッセージは2回表示されます。 これは、SPN に2つのオブジェクトが登録されている必要があるというわけではありません。

詳細については、「 [Mbam セットアップは "SPN の登録を延期する" エラーメッセージで失敗](https://support.microsoft.com/help/2754138/)する」を参照してください。

### ADMX テンプレートを最新バージョンに更新する必要はありましたか?

ADMX テンプレートを最新バージョンに更新した後、GPO の MBAM root ノードに複数の OS オプションが表示されます。 たとえば、Windows 7、Windows 8.1、Windows 10 バージョン1511以降。

ADMX テンプレートの更新方法の詳細については、次の記事を参照してください。
* [MDOP グループ ポリシー (.admx) テンプレートをダウンロードして展開する方法](https://docs.microsoft.com/microsoft-desktop-optimization-pack/solutions/how-to-download-and-deploy-mdop-group-policy--admx--templates)
* [MBAM 2.5 グループ ポリシー要件の計画](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/planning-for-mbam-25-group-policy-requirements)
* [Microsoft デスクトップ最適化パックのグループポリシー管理用テンプレート](https://www.microsoft.com/en-us/download/details.aspx?id=55531)
