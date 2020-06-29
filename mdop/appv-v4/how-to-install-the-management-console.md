---
title: Management Console をインストールする方法
description: Management Console をインストールする方法
author: dansimp
ms.assetid: 586d99c8-bca6-42e2-a39c-a696053142f1
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 48f4f69753794cf8099df36828e0502e98414b31
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10817304"
---
# Management Console をインストールする方法


次の手順を使用して、ネットワーク上のターゲットコンピューターに Application Virtualization 管理コンソールをインストールすることができます。 ターゲットコンピューターの管理者権限を持つネットワークアカウントを使用する必要があります。 コンソールを使って、Application Virtualization System Platform の構成と管理を行うことができます。

この手順を完了する前に、Application Virtualization Management Web Service をこのコンピューターまたは別のコンピューターにインストールする必要があります。 管理 Web サービスを使うと、データストアとドメインコントローラーにアクセスできます。 Web サービスのインストールの詳細については、「[管理 Web サービスをインストールする方法](how-to-install-the-management-web-service.md)」を参照してください。

**管理コンソールをインストールするには**

1.  ターゲットコンピューターに以前のバージョンの管理コンソールがインストールされていないことを確認します。

2.  ネットワーク上でアプリケーションの仮想化システムセットアッププログラムが保存されている場所に移動します。ネットワークからこのプログラムを実行するか、またはターゲットコンピューターにディレクトリをコピーして、[ **Setup.exe**] をダブルクリックします。

3.  [**ようこそ] ページ**で、[**次へ**] をクリックします。

4.  [**使用許諾契約**書] ページで、使用許諾契約に同意する場合は、[**ライセンス条項に同意**する] を選択し、[**次へ**] をクリックします。

5.  [**登録情報**] ページで、**ユーザー名**と**組織**の情報を指定し、[**次へ**] をクリックします。

6.  [**セットアップの種類**] ページで、[**ユーザー設定**] をクリックし、[**次へ**] をクリックします。

7.  [**カスタムセットアップ**] ページで、[**管理コンソール**を除くすべての Application Virtualization システムコンポーネント] の選択を解除し、[**次へ**] をクリックします。

    **注** コンポーネントがコンピューターに既にインストールされている場合は、[カスタムセットアップ] 画面でそのコンポーネントをオフにすると、自動的にアンインストールされます。

     

8.  [**プログラムを変更する準備ができ**ました] 画面で、[**インストール**] をクリックします。

    **注** 初めてインストールする場合は、[**プログラムをインストールする準備ができ**ました] ページが表示されます。 インストールを開始するには、[**インストール**] をクリックします。

     

9.  **インストールウィザード**の [完了] 画面で、[**完了**] をクリックします。 [ **Ok** ] をクリックしてコンピューターを再起動し、インストールを完了します。

10. Windows のコントロールパネルで、[**管理ツール**] をダブルクリックし、[**アプリケーション仮想化管理コンソール**] をクリックして、管理コンソールを表示します。

11. [**接続**] アイコンをクリックするか、[ **application virtualization Systems** ] コンテナーを右クリックして、[**アプリケーション仮想化システムに接続する**] をクリックします。

12. [ **Application Virtualization System への接続**] 画面で、管理 Web サービスコンピューターのホスト名とポートを入力し、必要に応じてセキュリティ情報とログイン資格情報を変更して、[ **OK]** をクリックします。

13. 管理 Web サービスコンピューターに接続した後、[**コンソール**] メニューの [**ファイル**] をクリックし、[**終了**] をクリックします。 [**はい]** をクリックしてコンソールの設定を保存します。

## 関連トピック


[サーバーおよびシステム コンポーネントをインストールする方法](how-to-install-the-servers-and-system-components.md)

 

 




