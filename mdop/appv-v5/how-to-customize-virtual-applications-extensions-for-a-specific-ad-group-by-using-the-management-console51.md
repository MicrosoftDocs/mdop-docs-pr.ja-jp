---
title: 管理コンソールを使用して特定の AD グループの仮想アプリケーションの拡張機能をカスタマイズする方法
description: 管理コンソールを使用して特定の AD グループの仮想アプリケーションの拡張機能をカスタマイズする方法
author: dansimp
ms.assetid: dd71df05-512f-4eb4-a55f-e5b93601323d
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 3bf086da3fbb6938a4fc602af5ab63adb1621532
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10814258"
---
# 管理コンソールを使用して特定の AD グループの仮想アプリケーションの拡張機能をカスタマイズする方法


Active Directory (AD) グループの仮想アプリケーション拡張機能をカスタマイズするには、次の手順を使用します。

**AD グループの仮想アプリケーションの拡張機能をカスタマイズするには**

1.  構成するパッケージを表示するには、App-v 5.1 管理コンソールを開きます。 特定のユーザーグループに割り当てられている構成を表示するには、パッケージを選択し、パッケージ名を右クリックして、[ **active directory アクセスの編集**] を選択します。 または、パッケージを選択し、**広告アクセス**ウィンドウで [**編集**] をクリックします。

2.  広告グループをカスタマイズするには、**アクセス権のある広告エンティティ**の一覧からグループを検索します。 次に、[**割り当てられた構成**] ウィンドウのドロップダウンボックスを使用して、[**カスタム**] を選択し、[**編集**] をクリックします。

3.  特定のアプリケーションのすべての拡張機能を無効にするには、[**有効に**する] をオフにします。

    選択したアプリケーションに新しいショートカットを追加するには、[**ショートカット**] ウィンドウでアプリケーションを右クリックし、[**新しいショートカットの追加**] を選択します。 ショートカットを削除するには、[**ショートカット**] ウィンドウでアプリケーションを右クリックし、[**ショートカットの削除**] を選択します。 既存のショートカットを編集するには、アプリケーションを右クリックし、[**ショートカットの編集**] を選択します。

4.  その他のアプリケーションの拡張子を表示するには、[**詳細設定**] をクリックし、[**構成のエクスポート**] をクリックします。 ファイル名を入力し、[**保存**] をクリックします。 パッケージに関連付けられているすべてのアプリケーション拡張機能は、構成ファイルを使って表示できます。

5.  その他のアプリケーションの拡張子を編集するには、構成ファイルを変更し、[インポート] をクリックして [**この構成を上書き**] をクリックします。 変更したファイルを選択し、[**開く**] をクリックします。 ダイアログボックスで、[**上書き**] をクリックして処理を完了します。

    App-v**の提案をお寄せ**ください。 [ここで](http://appv.uservoice.com/forums/280448-microsoft-application-virtualization)候補を追加または投票してください。 **App-v の問題が発生しましたか?** App-v の[TechNet フォーラム](https://social.technet.microsoft.com/Forums/home?forum=mdopappv)を使用します。

## 関連トピック


[APP-V 5.1 の操作](operations-for-app-v-51.md)

 

 




