---
title: ドメイン レベルのアクセスを委任する
description: ドメイン レベルのアクセスを委任する
author: dansimp
ms.assetid: 64c8e773-38cc-4991-9ed2-5a801094d06e
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 7eb4c33e60b0d995e45fca6c9e91a26c30dd4a7f
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10820997"
---
# ドメイン レベルのアクセスを委任する


グループポリシー管理者が適切なアクセス権を持ち、グループポリシーオブジェクト (Gpo) を制御できるように、環境の委任を設定します。 高度なグループポリシー管理 (AGPM) の操作をより効率的にするために、適用できるベースラインのアクセス許可があります。 組織のニーズに合った任意の方法でアクセス許可を付与することができます。

この手順を完了するには、AGPM 管理者 (フルコントロール) の役割または高度なグループポリシー管理の必要なアクセス許可を持つユーザーアカウントが必要です。 詳細については、このトピックの「その他の考慮事項」を参照してください。

**ユーザーやグループがドメイン全体のすべての Gpo に対する適切な権限を持つように、アクセスを委任するには**

1.  [**グループポリシー管理コンソール**] ツリーで、gpo を管理するフォレストとドメインの [ **Change Control** ] をクリックします。

2.  [ **Domain Delegation** ] タブをクリックし、[**詳細設定**] ボタンをクリックします。

3.  [**アクセス許可**] ダイアログボックスで、個別に割り当てる役割のチェックボックスをオンにして、[**詳細設定**] ボタンをクリックします。

    **注** 編集者には、レビュー担当者の権限が含まれています。

     

4.  [**詳細なセキュリティ設定**] ダイアログボックスで、グループポリシーの管理者を選択し、[**編集**] をクリックします。

5.  [**適用先**] で、**このオブジェクトと入れ子になったオブジェクト**を選び、標準の AGPM ロールを超える特殊なアクセス許可を構成し、[**アクセス許可****エントリ**] ダイアログボックスで [ **OK** ] をクリックします。

6.  [**詳細なセキュリティ設定**] ダイアログボックスで、[ **OK**] をクリックします。

7.  [**アクセス許可**] ダイアログボックスで、[ **OK]** をクリックします。

### その他の考慮事項

-   既定では、この手順を実行するには AGPM 管理者 (フルコントロール) である必要があります。 具体的には、ドメインの [**セキュリティの変更**] アクセス許可を持っている必要があります。

-   AGPM を使用するグループポリシー管理者に読み取りアクセスを委任するには、**リストの内容**と**読み取り設定**のアクセス許可を付与する必要があります。 こうすることで、ユーザーは AGPM の [**コンテンツ**] タブで gpo を表示できます。 **このオブジェクトと入れ子になったオブジェクト**に適用するアクセス許可を設定します。 その他の権限は、明示的に委任する必要があります。

-   グループポリシーソフトウェアインストールを最大限に活用するために、編集者には、展開された GPO のコピーに対する**読み取り**アクセス許可が付与されている必要があります。

-   グループポリシー Creator Owners グループのメンバーシップは、Gpo へのアクセスの AGPM 管理を回避するために使用されないように制限されている必要があります。 (**グループポリシー管理コンソール**で、gpo を管理するフォレストとドメインの [**グループポリシーオブジェクト**] をクリックし、[**委任**] をクリックして、組織のニーズに合わせて設定を構成します)。

### その他の参照情報

-   [AGPM 管理者タスクの実行](performing-agpm-administrator-tasks.md)

 

 





