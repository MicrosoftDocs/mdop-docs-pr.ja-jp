---
title: 運用環境から GPO をインポートする
description: 運用環境から GPO をインポートする
author: dansimp
ms.assetid: 35c2a682-ece8-4577-a083-7e3e9facfd13
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 3d739a46d5ca078ec9d218c1cc1e5bd258c55601
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10820714"
---
# 運用環境から GPO をインポートする


高度なグループポリシー管理 (AGPM) の外部でコントロールされたグループポリシーオブジェクト (GPO) に変更が加えられた場合、その GPO のコピーを運用環境からインポートし、アーカイブに保存して、アーカイブと運用環境を一貫した状態にすることができます。 (制御されていない GPO をインポートするには、GPO を制御します。 「[非管理 GPO の制御を要求する](request-control-of-an-uncontrolled-gpo-agpm30ops.md)」を参照してください。)

この手順を完了するには、エディター、承認者、または AGPM 管理者 (フルコントロール) ロールまたは、必要なアクセス許可を持つユーザーアカウントが必要です。 詳細については、このトピックの「その他の考慮事項」を参照してください。

**運用環境から GPO をインポートするには**

1.  [**グループポリシー管理コンソール**] ツリーで、gpo を管理するフォレストとドメインの [ **Change Control** ] をクリックします。

2.  [**コンテンツ**] タブで、[**コントロール**] タブをクリックして、管理された gpo を表示します。

3.  GPO を右クリックし、[**生産からのインポート**] をクリックします。

4.  GPO の監査記録に関するコメントを入力し、[ **OK]** をクリックします。

### その他の考慮事項

-   既定では、この手順を実行するには、編集者、承認者、または AGPM 管理者 (フルコントロール) である必要があります。 具体的には、GPO**の [** 設定の**編集**]、[ **gpo の展開**]、または [gpo の**削除**] のアクセス許可を設定する必要があります。

### その他の参照情報

-   [GPO の作成、制御、インポート](creating-controlling-or-importing-a-gpo-agpm30ops.md)

 

 





