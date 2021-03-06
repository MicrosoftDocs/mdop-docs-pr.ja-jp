---
title: ファイルから GPO をインポートする
description: ファイルから GPO をインポートする
author: dansimp
ms.assetid: 6e901a52-1101-4fed-9f90-3819b573b378
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: e15704806f089bb0d8530cd84df64b0889413426
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10820724"
---
# ファイルから GPO をインポートする


高度なグループポリシー管理 (AGPM) で、グループポリシーオブジェクト (GPO) を CAB ファイルにエクスポートした場合、その GPO から別のフォレストのドメイン内の既存の GPO にポリシー設定をインポートできます。 既存の GPO にポリシー設定をインポートすると、その GPO 内のすべてのポリシー設定が置き換えられます。 CAB ファイルに GPO 設定をエクスポートする方法について詳しくは、「 [gpo をファイルにエクスポート](export-a-gpo-to-a-file.md)する」をご覧ください。

この手順を完了するには、Editor または AGPM 管理者 (フルコントロール) の役割を持つ、または高度なグループポリシー管理 (AGPM) に必要なアクセス許可を持つユーザーアカウントが必要です。詳細については、このトピックの「その他の考慮事項」を参照してください。

## <a href="" id="bkmk-existing"></a>


**既存の GPO にポリシー設定をインポートするには**

1.  [**グループポリシー管理コンソール**] ツリーで、ポリシー設定をインポートするドメインの [ **Change Control** ] をクリックします。

2.  [**コンテンツ**] タブで、[**コントロール**] タブをクリックして、管理された gpo を表示します。

3.  ポリシー設定をインポートする宛先 GPO を確認します。

4.  送信先 GPO を右クリックし、[**インポート元**] をポイントして、[**ファイル**] をクリックします。

5.  **設定のインポートウィザード**の指示に従って、GPO のバックアップを選び、宛先 gpo のポリシー設定をインポートして、移行先 gpo の監査証跡に関するコメントを入力します。 既定では、ウィザードが終了すると、送信先 GPO がチェックインされます。

### その他の考慮事項

-   既定では、この手順を実行するには、Editor または AGPM 管理者 (フルコントロール) である必要があります。 具体的には、ドメインの [**コンテンツの一覧表示**]、[**設定の編集**]、[ **gpo のインポート**] のアクセス許可が必要であり、gpo をチェックアウトする必要があります。

-   エディターは、作成中に新しい GPO にポリシー設定をインポートすることはできませんが、新しい GPO の作成を要求し、それを作成した後でポリシー設定をインポートすることができます。

### その他の参照情報

-   [テスト環境の使用](using-a-test-environment.md)

 

 





