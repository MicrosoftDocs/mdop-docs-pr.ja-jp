---
title: GPO またはテンプレートの名前を変更する
description: GPO またはテンプレートの名前を変更する
author: dansimp
ms.assetid: 84293f7a-4ff7-497e-bdbc-cabb70189a03
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 642622ae0242e614733e8f33ea5840c8b6758db8
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10818514"
---
# GPO またはテンプレートの名前を変更する


コントロールされたグループポリシーオブジェクト (GPO) またはテンプレートの名前を変更できます。

この手順を完了するには、Editor または AGPM 管理者 (フルコントロール) の役割を持つユーザーアカウント、または高度なグループポリシー管理 (AGPM) で必要なアクセス許可を持つユーザーアカウントを指定する必要があります。 詳細については、このトピックの「その他の考慮事項」を参照してください。

**GPO またはテンプレートの名前を変更するには**

1.  [**グループポリシー管理コンソール**] ツリーで、gpo を管理するフォレストとドメインの [ **Change Control** ] をクリックします。

2.  [**コンテンツ**] タブで、[**コントロール**] または [**テンプレート**] タブをクリックして、名前を変更するアイテムを表示します。

3.  名前を変更する GPO またはテンプレートを右クリックし、[**名前の変更**] をクリックします。

4.  GPO またはテンプレートの新しい名前とコメントを入力し、[ **OK]** をクリックします。

5.  **進行**状況ウィンドウで全体の進行状況が完了したことが示されたら、[**閉じる**] をクリックします。 GPO またはテンプレートが [**コンテンツ**] タブの新しい名前の下に表示されます。

### その他の考慮事項

-   既定では、この手順を実行するには、GPO、エディター、または AGPM 管理者 (フルコントロール) を作成または管理している承認者である必要があります。 具体的には、GPO の [**コンテンツの一覧]** と [**設定の編集**] のアクセス許可が必要です。

-   展開されている GPO の名前を変更すると、アーカイブ内でその名前がすぐに変更されます。 この名前は、GPO が再展開された場合にのみ、実稼働環境で変更されます。 GPO が再展開されるか (または、プロダクションコピーが削除されるまで)、古い名前はまだ実稼働環境で使用されているため、別の GPO に使用することはできません。 同様に、アーカイブ内の GPO は、GPO が配置される (運用コピーの名前を変更する) か、プロダクションコピーが削除されるまで、元の名前に戻すことはできません。

### その他の参照情報

-   [GPO の編集](editing-a-gpo-agpm40.md)

 

 





