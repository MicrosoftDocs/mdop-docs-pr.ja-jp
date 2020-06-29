---
title: GPO を削除する
description: GPO を削除する
author: dansimp
ms.assetid: 85fca371-5707-49c1-aa51-813fc3a58dfc
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 8a6419943604ee5a76d305228bb7418a8525bf33
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10820984"
---
# GPO を削除する


高度なグループポリシー管理 (AGPM) では、管理者がグループポリシーオブジェクト (GPO) を削除し、ごみ箱に移動できるようにします。

この手順を完了するには、承認者または AGPM 管理者 (フルコントロール) の役割、または高度なグループポリシーの管理に必要なアクセス許可を持つユーザーアカウントが必要です。 詳細については、このトピックの「その他の考慮事項」を参照してください。

**コントロールされた GPO を削除するには**

1.  [**グループポリシー管理コンソール**] ツリーで、gpo を管理するフォレストとドメインの [ **Change Control** ] をクリックします。

2.  [**コンテンツ**] タブで、[**コントロール**] タブをクリックして、管理された gpo を表示します。

3.  削除する GPO を右クリックし、[**削除**] をクリックします。

    -   展開されたバージョンの GPO を運用環境でそのまま残して、アーカイブから GPO を削除するには、[ **gpo の削除**] をクリックします。

    -   アーカイブと運用環境の両方から GPO を削除するには、[**アーカイブと運用] から [gpo の削除**] をクリックします。

4.  GPO の監査トレールに表示されるコメントを入力し、[ **OK]** をクリックします。

5.  **進行**状況ウィンドウで全体の進行状況が完了したことが示されたら、[**閉じる**] をクリックします。 GPO は [**コントロール**] タブから削除され、[**ごみ箱**] タブに表示され、そこで復元または破棄することができます。 GPO がアーカイブからのみ削除された場合は、[**非コントロール**] タブにも表示されます。

### その他の考慮事項

-   既定では、展開された GPO を削除するには、承認者または AGPM 管理者 (フルコントロール) である必要があります。 具体的には、GPO の [**コンテンツの一覧表示**] および [ **gpo の削除**] のアクセス許可を持っている必要があります。

-   既定では、アーカイブから GPO を削除するには、編集者、承認者、AGPM 管理者 (フルコントロール) である必要があります。 具体的には、GPO の [**コンテンツの一覧]** と [**設定の編集**] または [ **gpo の削除**] のアクセス許可を持っている必要があります。

-   制御されていない GPO を運用環境から削除するには、まず**グループポリシー管理コンソール**で、[**フォレスト**] をクリックし、[**ドメイン**] をクリックして、[ ** &lt; MyDomain &gt; **] をクリックし、[**グループポリシーオブジェクト**] をクリックします。 非制御 GPO を右クリックし、[**削除**] をクリックします。

### その他の参照情報

-   [GPO の削除、復元、破棄](deleting-restoring-or-destroying-a-gpo.md)

 

 




