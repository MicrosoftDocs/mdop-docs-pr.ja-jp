---
title: 新しい制御された GPO の作成を要求する
description: 新しい制御された GPO の作成を要求する
author: dansimp
ms.assetid: 4194c2f3-8116-4a35-be1a-81c84072daec
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 4f9d7dd8a604bf2d2e3638142c070fed8b6d44e2
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10820327"
---
# 新しい制御された GPO の作成を要求する


承認者または AGPM 管理者 (フルコントロール) でない場合は、新しいグループポリシーオブジェクト (GPO) の作成を要求する必要があります。

この手順を完了するには、編集者の役割、または高度なグループポリシー管理 (AGPM) で必要なアクセス許可を持つユーザーアカウントが必要です。 詳細については、このトピックの「その他の考慮事項」を参照してください。

**AGPM によって管理される変更コントロールで新しい GPO を作成するには**

1.  [**グループポリシー管理コンソール**] ツリーで、gpo を管理するフォレストとドメインの [ **Change Control** ] をクリックします。

2.  [コントロールの**変更**] を右クリックし、[**新しい制御**された GPO] をクリックします。

3.  Gpo を作成するための特別なアクセス許可がない場合は、作成の要求を送信する必要があります。 [**新しいコントロール**された GPO] ダイアログボックスで、次の操作を行います。

    1.  要求のコピーを受信するには、[ **Cc** ] フィールドにメールアドレスを入力します。

    2.  新しい GPO の名前を入力します。

    3.  オプション: 新しい GPO にコメントを入力します。

    4.  承認されたときにすぐに新しい GPO を運用環境に展開するには、[**ライブの作成**] をクリックします。 承認されたときにすぐに新しい GPO をオフラインで作成するには、[**オフラインで作成**] をクリックします。

    5.  新しい GPO の開始点として使用する GPO テンプレートを選択します。

    6.  **[送信]** をクリックします。

4.  **進行**状況ウィンドウで全体の進行状況が完了したことが示されたら、[**閉じる**] をクリックします。 新しい GPO が、[**保留中**] タブの gpo の一覧に表示されます。承認者がリクエストを承認すると、その GPO は [**コントロール**] タブに移動されます。

### その他の考慮事項

-   既定では、この手順を実行するには、編集者またはレビュー担当者である必要があります。 具体的には、ドメインの**リストコンテンツ**のアクセス許可を持っている必要があります。

-   承認される前に要求を取り消すには、[**保留中**] タブをクリックします。 GPO を右クリックし、[**取り消し] をクリックし**ます。 GPO は破棄されます。

### その他の参照情報

-   [GPO の作成、制御、インポート](creating-controlling-or-importing-a-gpo-agpm30ops.md)

 

 





