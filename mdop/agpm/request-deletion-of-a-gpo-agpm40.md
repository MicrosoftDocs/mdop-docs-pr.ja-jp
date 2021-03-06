---
title: GPO の削除を要求する
description: GPO の削除を要求する
author: dansimp
ms.assetid: 2410f7a1-ccca-44cf-ab26-76ad474409e7
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: cfdb50fba872b76c82152b469f787f2e1a6fb539
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10818427"
---
# GPO の削除を要求する


承認者または AGPM 管理者 (フルコントロール) でない場合は、グループポリシーオブジェクト (GPO) の削除を要求する必要があります。

この手順を完了するには、編集者の役割を持つユーザーアカウント、または高度なグループポリシー管理 (AGPM) で必要な権限を持っている必要があります。 詳細については、このトピックの「その他の考慮事項」を参照してください。

**コントロールされた GPO の削除を要求するには**

1.  [**グループポリシー管理コンソール**] ツリーで、gpo を管理するフォレストとドメインの [ **Change Control** ] をクリックします。

2.  [**コンテンツ**] タブで、[**コントロール**] タブをクリックして、管理された gpo を表示します。

3.  削除する GPO を右クリックし、[**削除**] をクリックします。

    -   展開されているバージョンの GPO を運用環境でそのまま残して、アーカイブから GPO を削除するには、[ **gpo の削除**] をクリックします。

    -   ドメインのアーカイブ環境と運用環境の両方から GPO を削除するには、[**アーカイブと運用] から [gpo の削除**] をクリックします。

4.  Gpo を削除するための特別なアクセス許可を持っていない場合は、展開された GPO の削除の要求を送信する必要があります。 要求のコピーを受信するには、[ **Cc** ] フィールドにメールアドレスを入力します。 GPO の監査トレールに表示されるコメントを入力し、[**送信**] をクリックします。

5.  **進行**状況ウィンドウで全体の進行状況が完了したことが示されたら、[**閉じる**] をクリックします。 GPO は、[**保留中**] タブの gpo の一覧に表示されます。承認者が要求を承認した場合、GPO は [**保留中**] タブから [**ごみ箱**] タブに移動され、そこで復元または破棄することができます。

### その他の考慮事項

-   既定では、この手順を実行するには、エディターが必要です。 具体的には、GPO の [**リストコンテンツ]** と [**編集設定**] のアクセス許可が必要です。

-   承認される前に要求を取り消すには、[**保留中**] タブをクリックします。 GPO を右クリックし、[**取り消し] をクリックし**ます。 GPO は [**コントロール**] タブに戻ります。

-   制御されていない GPO を運用環境から削除するには、まず**グループポリシー管理コンソール**で、[**フォレスト**] をクリックし、[**ドメイン**] をクリックして、[ ** &lt; MyDomain &gt; **] をクリックし、[**グループポリシーオブジェクト**] をクリックします。 非制御 GPO を右クリックし、[**削除**] をクリックします。

### その他の参照情報

-   [GPO の削除または復元](deleting-or-restoring-a-gpo-agpm40.md)

 

 





