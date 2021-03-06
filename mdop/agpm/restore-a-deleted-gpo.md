---
title: 削除された GPO を復元する
description: 削除された GPO を復元する
author: dansimp
ms.assetid: e6953296-7b7d-4d1e-ad82-d4a23044cdd7
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 2cba097ecd651a91f828901d8115a7020d6da819
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10818414"
---
# 削除された GPO を復元する


高度なグループポリシー管理 (AGPM) では、承認者が削除されたグループポリシーオブジェクト (GPO) をごみ箱から復元し、アーカイブに戻すことができるようにします。

この手順を完了するには、エディター、承認者、または AGPM 管理者 (フルコントロール) の役割を持つユーザーアカウント、または高度なグループポリシー管理の必要なアクセス許可が必要です。 詳細については、このトピックの「その他の考慮事項」を参照してください。

**削除された GPO を復元するには**

1.  [**グループポリシー管理コンソール**] ツリーで、gpo を管理するフォレストとドメインの [ **Change Control** ] をクリックします。

2.  [**コンテンツ**] タブで、[**ごみ箱**] タブをクリックして、削除された gpo を表示します。

3.  復元する GPO を右クリックし、[**復元**] をクリックします。

4.  GPO の履歴に表示するコメントを入力し、[ **OK]** をクリックします。

5.  **進行**状況ウィンドウで全体の進行状況が完了したことが示されたら、[**閉じる**] をクリックします。 GPO は [**ごみ箱**] タブから削除され、[**コントロール**] タブに表示されます。

**注** GPO が運用環境から削除された場合、アーカイブに復元しても、自動的に運用環境に再配置されることはありません。 GPO を運用環境に戻すには、GPO を展開します。 詳細については、「 [GPO の展開](deploy-a-gpo.md)」を参照してください。

 

### その他の考慮事項

-   既定では、この手順を実行するには、編集者、承認者、AGPM 管理者 (フルコントロール) である必要があります。 具体的には、GPO**の [** 設定の**編集**]、[ **gpo の展開**]、または [gpo の**削除**] のアクセス許可を設定する必要があります。

### その他の参照情報

-   [GPO の削除、復元、破棄](deleting-restoring-or-destroying-a-gpo.md)

 

 





