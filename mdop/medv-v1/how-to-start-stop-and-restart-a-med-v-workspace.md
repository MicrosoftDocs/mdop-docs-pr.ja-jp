---
title: MED-V ワークスペースを開始、停止、再開する方法
description: MED-V ワークスペースを開始、停止、再開する方法
author: dansimp
ms.assetid: 54ce139c-8f32-499e-944b-72f123ebfd2d
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: c2739ace085a4d57d333daf7872e01a7712a7fbd
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10825724"
---
# MED-V ワークスペースを開始、停止、再開する方法


**MED-V ワークスペースを開始するには**

1.  通知領域で、MED-V アイコンを右クリックします。

2.  サブメニューで、[**ワークスペースの開始**] をクリックします。

    -   コンピューター上で実行されている複数の MED-V ワークスペースがある場合は、**ワークスペースの選択**ウィンドウが表示されます。

        1.  MED-V ワークスペースを選択します。

        2.  次回クライアントを起動し、選択した MED-V ワークスペースを自動的に開くには、[確認メッセージを表示**せずに、選択したワークスペース**をスキップする] チェックボックスをオンにします。

        3.  **[OK]** をクリックします。

    [**ワークスペースの認証の開始**] ウィンドウが表示されます。

    -   コンピューター上に複数の MED-V ワークスペースがあり、指定した MED-V ワークスペースを使うことを選んだ場合、次の図のようなウィンドウが表示されます。

        ![](images/medv-logon.gif)

    -   コンピューター上に MED-V ワークスペースが1つしかない場合、[最後に使用した作業を開始する] オプションは使用できません。

3.  ドメインユーザーの資格情報を入力します。

    **注** Med-v ワークスペースを初めて起動するときに、ユーザー名は次の形式になっている必要があります。 &lt; ドメイン名の &gt; \\ &lt; ユーザー名 &gt; 。

     

4.  [**パスワードを保存**してセッション間のパスワードを保存する] を選択します。

    **注** パスワードの保存機能を有効にするには、ClientSettings.xml ファイルで EnableSavePassword 属性が True に設定されている必要があります。 ファイルは*Servers\\Configuration \*フォルダーにあります。

     

5.  [最後に使用した**作業を開始**する] チェックボックスをオフにして、別の med-v ワークスペースを選びます。

6.  **[OK]** をクリックします。

    MED-V ワークスペースの構成に応じて、いくつかの状態画面が表示されます。

    [**ワークスペースの開始**] 画面が表示されます。

**MED-V ワークスペースを再起動するには**

1.  クライアントが実行されているときに、通知領域で MED-V アイコンを右クリックします。

2.  サブメニューで、[**ワークスペースの再起動**] をクリックします。

    MED-V ワークスペースが再起動されます。

    -   永続的な MED-V ワークスペースでは、仮想マシンはシャットダウンされ、再起動されます。

    -   Revertible MED ワークスペースでは、仮想マシンは実際にはシャットダウンされません。代わりに、元の状態に戻ります。

**MED-V ワークスペースを停止するには**

1.  通知領域で、MED-V アイコンを右クリックします。

2.  サブメニューで、[**ワークスペースの停止**] をクリックします。

    MED-V ワークスペースは停止されます。

## 関連トピック


[MED-V クライアントを開始および終了する方法](how-to-start-and-exit-the-med-v-client.md)

 

 





