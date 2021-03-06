---
title: GPO の現在のバージョンにラベルを付ける
description: GPO の現在のバージョンにラベルを付ける
author: dansimp
ms.assetid: cadc8769-21da-44b0-8122-6cafdb448913
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: b15a4d3ee006fb37db4ce7362a2f5c92d7c233e5
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10820664"
---
# GPO の現在のバージョンにラベルを付ける


グループポリシーオブジェクト (GPO) の現在のバージョンにラベルを付けて、履歴を簡単に識別することができます。 問題が発生した場合は、ラベルを使用して、ロールバックできる既知の適切なバージョンを特定できます。 また、同じラベルの複数の Gpo に一度にラベルを付けることで、ロールバックする必要がある場合は、同じポイントにロールバックする必要がある関連する Gpo にマークを付けることができます。

この手順を完了するには、エディター、承認者、または AGPM 管理者 (フルコントロール) の役割を持つ、または高度なグループポリシー管理 (AGPM) の必要なアクセス許可を持つユーザーアカウントが必要です。 詳細については、このトピックの「その他の考慮事項」を参照してください。

**履歴で現在のバージョンの Gpo にラベルを付けるには**

1.  [**グループポリシー管理コンソール**] ツリーで、gpo を管理するフォレストとドメインの [ **Change Control** ] をクリックします。

2.  [**コンテンツ**] タブで、[**コントロール**] タブをクリックして、管理された gpo を表示します。

3.  現在のバージョンのラベルを付ける GPO をクリックします。 複数の Gpo を選択するには、SHIFT キーを押しながら、Gpo の隣接するグループ内の最後の GPO をクリックするか、CTRL キーを押しながら個別の Gpo をクリックします。 選択した GPO を右クリックし、[**ラベル**] をクリックします。

4.  選択されている各 GPO の履歴に表示するラベルとコメントを入力し、[ **OK]** をクリックします。

5.  **進行**状況ウィンドウで全体の進行状況が完了したことが示されたら、[**閉じる**] をクリックします。

### その他の考慮事項

-   既定では、この手順を実行するには、編集者、承認者、AGPM 管理者 (フルコントロール) である必要があります。 具体的には、その GPO の [**コンテンツの一覧]** と [**設定の編集**] または [gpo のアクセス許可の**展開**] を行う必要があります。

### その他の参照情報

-   [GPO の編集](editing-a-gpo-agpm40.md)

 

 





