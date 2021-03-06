---
title: AGPM サーバー接続を構成する
description: AGPM サーバー接続を構成する
author: dansimp
ms.assetid: bbbb15e8-35e7-403c-b695-7a6ebeb87839
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 9b6b065b9855c6edf44456026baa32e8d9a4674f
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10819074"
---
# AGPM サーバー接続を構成する


グループポリシー管理者は、各グループポリシーオブジェクト (GPO) のすべてのバージョンを中央のアーカイブに保存して、展開されたバージョンの各 GPO にすぐに影響を与えることなく、Gpo をオフラインで表示したり、変更したりすることができます。

AGPM 管理者 (フルコントロール) の役割を持つユーザーアカウント、これらの手順で使用された GPO を作成した承認者のユーザーアカウント、または高度なグループポリシー管理 (AGPM) で必要なアクセス許可を持つユーザーアカウントは、すべてのグループポリシー管理者のアーカイブ場所を一元的に構成するために必要な手順です。 詳細については、このトピックの「その他の考慮事項」を参照してください。

## AGPM サーバー接続を構成する


AGPM 管理者は、関連付けられた設定を一元的に構成することで、すべてのグループポリシー管理者が同じ AGPM サーバーに接続することを確認できます。 環境で、一部またはすべてのドメインに別個の AGPM サーバーが必要な場合は、これらの追加の AGPM サーバーを既定の例外として構成します。 AGPM サーバー接続を一元的に構成しない場合、各グループポリシー管理者は、各ドメインに対して表示される AGPM サーバーを手動で構成する必要があります。

-   [すべてのグループポリシー管理者に対して AGPM サーバー接続を構成する](#bkmk-defaultarchiveloc)

-   [すべてのグループポリシー管理者に対して、追加の AGPM サーバー接続を構成する](#bkmk-additionalarchiveloc)

-   [アカウントの AGPM サーバー接続を手動で構成する](#bkmk-manuallyconfigurearchiveloc)

### <a href="" id="bkmk-defaultarchiveloc"></a>

**すべてのグループポリシー管理者に対して AGPM サーバー接続を構成するには**

1.  [**グループポリシー管理コンソール**] ツリーで、すべてのグループポリシー管理者に適用される GPO を編集します。 詳細については、「 [GPO を編集する](editing-a-gpo-agpm40.md)」を参照してください。

2.  [**グループポリシー管理エディター** ] ウィンドウで、[**ユーザーの構成**]、[**ポリシー**]、[**管理用テンプレート**]、[Windows コンポーネント]、[ **AGPM**] の**各項目**をクリックします。

3.  詳細ウィンドウで、[ **agpm: 既定の AGPM サーバーを指定してください (すべてのドメイン)**] をダブルクリックします。

4.  [**プロパティ**] ウィンドウで、[**有効**] チェックボックスをオンにし、完全修飾コンピューター名とポート (たとえば、server.contoso.com:4600) を入力します。

5.  **[OK]** をクリックします。 追加の AGPM サーバー接続を構成する場合以外は、[**グループポリシー管理エディター** ] ウィンドウを閉じて、GPO を展開します。 (詳細については、「 [GPO の展開](deploy-a-gpo-agpm40.md)」を参照してください)。グループポリシーが更新されると、すべてのグループポリシーの管理者に対して AGPM サーバー接続が構成されます。

### <a href="" id="bkmk-additionalarchiveloc"></a>

**すべてのグループポリシー管理者に対して、追加の AGPM サーバー接続を構成するには**

1.  AGPM サーバー接続が構成されていない場合は、上記の手順に従って、すべてのドメインに対して既定の AGPM サーバーを構成します。

2.  一部またはすべてのドメイン (既定の AGPM サーバーを上書きします) に対して別個の AGPM サーバーを構成するには、[**グループポリシー管理コンソール**] ツリーで、すべてのグループポリシー管理者に適用される GPO を編集します。 詳細については、「 [GPO を編集する](editing-a-gpo-agpm40.md)」を参照してください。

3.  [**グループポリシー管理エディター** ] ウィンドウで、[**ユーザーの構成**]、[**ポリシー**]、[**管理用テンプレート**]、[ **Windows コンポーネント**]、[ **AGPM**] の順にクリックします。

4.  詳細ウィンドウで、 **agpm: Agpm サーバーを指定**します。

5.  [**プロパティ**] ウィンドウで、[**有効**] チェックボックスをオンにし、[**表示**] をクリックします。

6.  [**コンテンツの表示**] ウィンドウで、次の操作を行います。

    1.  **[追加]** をクリックします。

    2.  [**値の名前**] には、ドメイン名 (server1.contoso.com など) を入力します。

    3.  **値**には、このドメインに使用する AGPM サーバー名とポート (たとえば、server2.contoso.com:4600) を入力して、[ **OK]** をクリックします。 (既定では、AGPM サービスはポート4600をリッスンします。 別のポートを使用する場合は、「 [AGPM サービスを変更](modify-the-agpm-service-agpm40.md)する」を参照してください。

    4.  既定の AGPM サーバーを使用しないドメインごとに、この手順を繰り返します。

7.  [ **OK** ] をクリックして、[コンテンツと**プロパティ**の**表示**] ウィンドウを閉じます。

8.  [**グループポリシー管理エディター** ] ウィンドウを閉じます。 (詳細については、「 [GPO の展開](deploy-a-gpo-agpm40.md)」を参照してください)。グループポリシーが更新されると、すべてのグループポリシーの管理者に対して新しい AGPM サーバー接続が構成されます。

### <a href="" id="bkmk-manuallyconfigurearchiveloc"></a>

AGPM サーバー接続を一元的に構成している場合、すべてのグループポリシー管理者は手動で構成するオプションは利用できません。

**アカウントに表示する AGPM サーバーを手動で構成するには**

1.  [**グループポリシー管理コンソール**] ツリーで、gpo を管理するフォレストとドメインの [ **Change Control** ] をクリックします。

2.  詳細ウィンドウで、[ **AGPM サーバー** ] タブをクリックします。

3.  このドメイン (たとえば、server.contoso.com) で使用されているアーカイブと、AGPM サービスがリッスンするポート (既定では、ポート 4600) を管理する AGPM サーバーの完全修飾コンピューター名を入力します。

4.  [**適用**] をクリックし、[**はい**] をクリックして確認します。

### その他の考慮事項

-   すべてのグループポリシーの管理者に対して、AGPM サーバー接続を一元的に構成するための手順を実行するには、GPO の編集と展開が可能である必要があります。 詳細については、「 [gpo を編集](editing-a-gpo-agpm40.md)する」と「 [gpo を展開](deploy-a-gpo-agpm40.md)する」を参照してください。

-   選択した AGPM サーバーによって、[**コンテンツ**] タブに表示される gpo と、[**ドメイン委任**] タブの設定が適用される場所が決定されます。 管理用テンプレートで一元管理されていない場合は、各グループポリシー管理者がこの設定を構成して、ドメインの AGPM サーバーを指すようにする必要があります。

-   グループポリシー Creator Owners グループのメンバーシップは制限されている必要があります。 soit は、Gpo へのアクセスの AGPM 管理を回避するために使用されることはありません。 (**グループポリシー管理コンソール**で、gpo を管理するフォレストとドメインの [**グループポリシーオブジェクト**] をクリックし、[**委任**] をクリックして、組織のニーズに合わせて設定を構成します)。

### その他の参照情報

-   [高度なグループ ポリシーの管理の構成](configuring-advanced-group-policy-management-agpm40.md)

 

 





