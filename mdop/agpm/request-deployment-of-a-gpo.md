---
title: GPO の展開を要求する
description: GPO の展開を要求する
author: dansimp
ms.assetid: 9aa9af29-4754-4f72-b624-bb3e1087cbe1
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 2a9e5fdbbd352adb6d542932c7180c513cfac8b2
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10820377"
---
# GPO の展開を要求する


グループポリシーオブジェクト (GPO) を変更してチェックインした後、GPO を展開して、実稼働環境で有効にします。

この手順を完了するには、編集者の役割を持つユーザーアカウント、または高度なグループポリシーの管理に必要なアクセス許可が必要です。 詳細については、このトピックの「その他の考慮事項」を参照してください。

**GPO の展開を運用環境に要求するには**

1.  [**グループポリシー管理コンソール**] ツリーで、gpo を管理するフォレストとドメインの [ **Change Control** ] をクリックします。

2.  [詳細] ウィンドウの [**コンテンツ**] タブで、[**コントロール**] タブをクリックして、管理されている gpo を表示します。

3.  展開する GPO を右クリックし、[**展開**] をクリックします。

4.  承認者または AGPM 管理者であるか、Gpo を展開するための特別なアクセス許可を持っていない場合は、展開の要求を送信する必要があります。 要求のコピーを受信するには、[ **Cc** ] フィールドにメールアドレスを入力します。 GPO の**履歴**に表示するコメントを入力し、[**送信**] をクリックします。

5.  **進行**状況ウィンドウで全体の進行状況が完了したことが示されたら、[**閉じる**] をクリックします。 GPO は、[**保留中**] タブの gpo の一覧に表示されます。承認者が要求を承認した場合、GPO は [**保留中**] タブから [**コントロール**] タブに移動され、展開されます。

### その他の考慮事項

-   既定では、この手順を実行するには、エディターが必要です。 具体的には、GPO の [**リストコンテンツ]** と [**編集設定**] のアクセス許可が必要です。

-   承認される前に要求を取り消すには、[**保留中**] タブをクリックします。 GPO を右クリックし、[**取り消し] をクリックし**ます。 GPO は [**コントロール**] タブに戻ります。

### その他の参照情報

-   [GPO の編集](editing-a-gpo.md)

 

 





