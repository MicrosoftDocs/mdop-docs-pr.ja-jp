---
title: スタンドアロン コンピューターにレポート サーバーをインストールしてデータベースに接続する方法
description: スタンドアロン コンピューターにレポート サーバーをインストールしてデータベースに接続する方法
author: dansimp
ms.assetid: 11f07750-4045-4c8d-a583-7d70c9e9aa7b
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 67866714ff6ae60097d9b368fd0eaf361b08eec6
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10813971"
---
# スタンドアロン コンピューターにレポート サーバーをインストールしてデータベースに接続する方法

次の手順を使用して、スタンドアロンコンピューターにレポートサーバーをインストールし、データベースに接続します。

**重要**次の手順を実行する前に、「 [app-v 5.1 レポート](about-app-v-51-reporting.md)」を参照して理解しておく必要があります。

## スタンドアロンコンピューターにレポートサーバーをインストールしてデータベースに接続するには

1. アプリをインストールするコンピューターに、App-v 5.1 サーバーのインストールファイルをコピーします。 App-v 5.1 server のインストールを開始するには、右クリックして、管理者として**appv\_server\_setup.exe**を実行します。 **[インストール]** をクリックします。

2. [はじめ**に] ページで**、ライセンス条項を確認して同意し、[**次へ**] をクリックします。

3. [ **Microsoft update を使用してコンピューターをセキュリティで保護し**、最新の状態に維持する] ページで、microsoft update を有効にするには、[**更新プログラムをチェックするときに Microsoft update を使用する (推奨)** ] を選択します。 Microsoft 更新プログラムを無効にするには、[ **Microsoft Update を使用しない**] を選択します。 **[次へ]** をクリックします。

4. [**機能の選択**] ページで、[**レポートサーバー** ] チェックボックスをオンにし、[**次へ**] をクリックします。

5. [**インストール場所**] ページで、既定の場所をそのまま使用し、[**次へ**] をクリックします。

6. [**既存のレポートデータベースの構成**] ページで、[**リモート SQL server を使用**する] を選び、Microsoft sql server を実行しているコンピューターのコンピューター名 ( **SqlServerMachine**など) を入力します。

    > [!NOTE]
    > Microsoft SQL Server が同じサーバーに展開されている場合は、[**ローカル Sql server を使用する**] を選びます。

    SQL Server インスタンスの場合は、[**既定のインスタンスの使用**] を選択します。 Microsoft SQL Server のカスタムインスタンスを使用している場合は、[**カスタムインスタンスの使用**] を選択し、インスタンスの名前を入力する必要があります。

    このレポートサーバーで使用する**SQL Server データベース名**を指定します (例**AppvReporting**)。

7. [**レポートサーバー構成の構成**] ページで、

   - レポートサービスに使用する Web サイト名を指定します。 カスタム名を指定しない場合は、既定のままにしておきます。

   - **ポートバインディング**には、 **55555**などの app-v 5.1 で使用される一意のポート番号を指定します。 指定したポートが別の web サイトで使用されていないことも確認する必要があります。

8. **[インストール]** をクリックします。

**App-v の問題が発生しましたか?** App-v の[TechNet フォーラム](https://social.technet.microsoft.com/Forums/home?forum=mdopappv)を使用します。

## 関連トピック

[App-V 5.1 のレポート機能について](about-app-v-51-reporting.md)

[APP-V 5.1 の展開](deploying-app-v-51.md)

[PowerShell を使用して App-V 5.1 Client のレポート機能を有効にする方法](how-to-enable-reporting-on-the-app-v-51-client-by-using-powershell.md)
