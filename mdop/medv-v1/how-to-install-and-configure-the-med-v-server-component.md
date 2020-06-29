---
title: MED-V サーバー コンポーネントをインストールして構成する方法
description: MED-V サーバー コンポーネントをインストールして構成する方法
author: dansimp
ms.assetid: 2d3c5b15-df2c-4ab6-bf78-f47ef8ae7418
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 08/30/2016
ms.openlocfilehash: 4fb0cc5c9ffe76e987e316d0285f172dd0b76578
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10826977"
---
# MED-V サーバー コンポーネントをインストールして構成する方法


このセクションでは、MED-V サーバーを[インストール](#bkmk-howtoinstallthemedvserver)して[構成](#bkmk-howtoconfigurethemedvserver)する方法について説明します。

## <a href="" id="bkmk-howtoinstallthemedvserver"></a>MED-V サーバーをインストールする方法


**MED-V サーバーをインストールするには**

1.  MED-V パッケージをインストールします。

    MED-V パッケージは*MED-V\_Server\_x.msi*と呼ばれます。ここで、x はバージョン番号です。

    たとえば、 *MED-V\_Server\_1.0.65.msi*とします。

2.  **InstallShield ウィザード**の [ようこそ] 画面が表示されたら、[**次へ**] をクリックします。

3.  [**使用**許諾契約書] 画面で、使用許諾契約書を読み、[使用許諾**契約書に同意**します] をクリックして、[**次へ**] をクリックします。

    [**インポート先のフォルダー** ] 画面が表示され、既定のインストールフォルダーが表示されます。

    既定のインストールフォルダーは、% *SystemVirtualization\\% ¥ Program filesmicrosoft Enterprise Desktop*です。

    -   MED-V をインストールする必要があるフォルダーを変更するには、[**変更**] をクリックし、既存のフォルダーを参照します。

4.  **[次へ]** をクリックします。

5.  [**プログラムをインストールする準備ができ**ました] 画面で、[**インストール**] をクリックします。

    MED-V サーバーのインストールが開始されます。 これには数分かかることがあり、画面にテキストが表示されないことがあります。 インストール中に、いくつかの進行状況画面が表示されます。 メッセージが表示されたら、表示される指示に従います。

6.  [ **InstallShield ウィザードの完了**] 画面が表示されたら、[**完了**] をクリックしてウィザードを完了します。

**注**  
Microsoft リモートデスクトップ経由で MED-V サーバーをインストールする場合は、次の構文を使用します。 **mstsc/admin**。RDP セッションが本体に送られていることを確認します。



## <a href="" id="bkmk-howtoconfigurethemedvserver"></a>MED-V サーバーを構成する方法


次のサーバー設定を構成できます。

-   [Connections](#bkmk-configuringconnections)

-   [画像](#bkmk-configuringimages)

-   [アクセス許可](#bkmk-configuringpermissions)

-   [レポート](#bkmk-configuringreports)

### <a href="" id="bkmk-configuringconnections"></a>接続を構成する

**接続を構成するには**

1.  Windows の [スタート] メニューで、[すべてのプログラム] を選びます** &gt; &gt; **。

    **注**  
    注: サーバーのインストール中に [ **Hyper-v Server 構成マネージャーを起動**する] チェックボックスをオンにした場合、サーバーのインストールが完了すると、med-v サーバー構成マネージャーが自動的に起動します。



~~~
The MED-V Server Configuration Manager appears.
~~~

2. [**接続**] タブで、次のクライアント接続設定を構成します。

   -   [暗号化されていない**接続 (http)、ポートを使用**する] —指定したポートを使って暗号化されていない接続を有効にするには、このチェックボックスをオン [ポート] ボックスに、暗号化されていない接続を受け付けるサーバーポート (http) を入力します。

   -   [**暗号化された接続 (https)、ポートを使用**する] —指定したポートを使って暗号化された接続を有効にするには、このチェックボックスをオンにします。 [ポート] ボックスに、暗号化された接続を受け付けるサーバーポート (https) を入力します。

       Https は、MED-V サーバーと MED-V クライアントの間でセキュリティで保護されたトランザクションを確保するために設定できるオプションの構成です。 Https を構成するには、次の手順を実行する必要があります。

       -   サーバー上で証明書を構成します。

       -   Netsh を使って指定したポートにサーバー証明書を関連付けます。 詳細については、以下を参照してください。

           -   [HTTP (ハイパーテキスト転送プロトコル) の Netsh コマンド](https://go.microsoft.com/fwlink/?LinkId=183314)

           -   [方法: SSL 証明書を使用してポートを構成する](https://go.microsoft.com/fwlink/?LinkID=183315)

           -   [方法: SSL 証明書を使用してポートを構成する](https://msdn.microsoft.com/library/ms733791.aspx)

3. **[OK]** をクリックします。

### <a href="" id="bkmk-configuringimages"></a>画像の構成

**画像を構成するには**

1.  [**画像**] タブをクリックします。

2.  次のイメージ管理設定を構成します。

    -   **VMs ディレクトリ**—仮想マシンディレクトリ (画像が保存されているディレクトリ)。 このフィールドには、MED-V サーバーからアクセスできるイメージ配布サーバー上の画像ディレクトリへの UNC パスが含まれています。

    -   [ **VM URL**の指定: イメージが保存されているサーバーの場所。

3.  **[OK]** をクリックします。

### <a href="" id="bkmk-configuringpermissions"></a>権限を構成する

**権限を構成するには**

1.  [**権限**] タブをクリックします。

2.  ログインできるすべてのユーザーの一覧が表示されます。 ユーザーに読み取りと書き込みのアクセス許可を適用するには、ユーザーの横にあるチェックボックスをオンにします。 ユーザーに読み取り専用のアクセス許可を適用するには、チェックボックスをオフにします。

3.  ドメインユーザーまたはグループを追加するには、[**追加**] をクリックします。

    [**ユーザーまたはグループ名の入力**] ダイアログボックスが表示されます。

    1.  次のいずれかの操作を行って、ドメインのユーザーまたはグループを選択します。

        -   [**ユーザーまたはグループ名の入力**] フィールドに、ドメイン内に存在するか、またはコンピューター上のローカルユーザーまたはグループとして存在するユーザーまたはグループを入力します。 次に、[**名前の確認**] をクリックして、存在する完全な名前に解決します。

        -   [**検索**] をクリックして、[標準の**ユーザーまたはグループの選択**] ダイアログボックスを開きます。 次に、[ドメインユーザーまたはグループ] を選択します。

    2.  **[OK]** をクリックします。

4.  ドメインユーザーまたはグループを削除するには、ユーザーまたはグループを選択し、[**削除**] をクリックします。

5.  **[OK]** をクリックします。

### <a href="" id="bkmk-configuringreports"></a>レポートを構成する

**レポートを構成するには**

1.  [**レポート**] タブをクリックします。

2.  レポートをサポートするには、[**レポートを有効**にする] を選択します。

3.  [**接続文字列**] ボックスに、MSSQL データベースの接続文字列を入力します。

    -   SQL Server がリモートサーバーにインストールされている場合は、次の接続文字列を使用します。

        `Data Source=<ServerName>;Initial Catalog=<DBName>;uid=sa;pwd=<Password>;`

        **注**  
        注: SQL Express に接続するには、次のように使用します。 `Data Source=<ServerName>\sqlexpress.`



4.  データベースを作成するには、[**データベースの作成**] をクリックします。

5.  接続をテストするには、[**接続テスト**] をクリックします。

6.  データベースの消去オプションを構成するには、[**オプションのクリア**] をクリックします。

    [**データベースオプションのクリア**] ダイアログボックスが表示されます。

    1.  次のいずれかのオプションを選びます。

        -   [以下の日付**より古いデータをクリア**する (指定の日数よりも古いデータをクリアする)。[数値] ボックスに日数を入力します。

        -   **データベースからすべてのデータを消去**—データベース内に存在するすべてのデータを消去します。

        -   [データベースの削除 **]**: データベースを削除します。

    2.  [ **OK** ] をクリックして変更を適用し、ダイアログボックスを閉じます。

7.  [ **OK** ] をクリックして変更を保存するか、[**キャンセル**] をクリックして、変更を保存せずにダイアログボックスを閉じます。

8.  メッセージが表示されたら、MED-V サーバーサービスを再起動して、ネットワーク設定に変更を適用します。

## 関連トピック


[サポートされる構成](supported-configurationsmedv-orientation.md)

[MED-V サーバー インフラストラクチャを設計する](design-the-med-v-server-infrastructure.md)








