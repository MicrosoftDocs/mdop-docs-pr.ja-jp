---
title: 未制御の GPO のコマンド
description: 未制御の GPO のコマンド
author: dansimp
ms.assetid: 05a8050f-adc3-465b-8524-bbe95745165c
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: d8efd1c1d3005fd97b92d392140b92bae6a38681
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10818244"
---
# 未制御の GPO のコマンド


[**非コントロール**] タブ:

-   高度なグループポリシー管理 (AGPM) で管理されていないグループポリシーオブジェクト (Gpo) の一覧が表示されます。

-   コントロールの Gpo を AGPM の管理下に表示したり、Gpo の履歴とレポートを表示したりするためのコマンドを含むショートカットメニューを提供します。

-   選択された GPO へのアクセス許可を持つグループとユーザーの一覧が表示されます。

このタブの [**グループポリシーオブジェクト**] リストを右クリックすると、次のいずれかのオプションを含むショートカットメニューが表示されます。

## コントロールと履歴


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">コマンド</th>
<th align="left">効果</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>履歴</strong></p></td>
<td align="left"><p>アーカイブに保存されている選択した GPO のすべてのバージョンを一覧表示するウィンドウを開きます。 履歴から、GPO 内の設定のレポートを取得したり、2つのバージョンの GPO を比較したり、GPO をテンプレートと比較したり、GPO の以前のバージョンにロールバックしたりすることができます。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>コントロール</strong></p></td>
<td align="left"><p>選択された非制御 GPO を、AGPM の変更コントロールの管理の下に移動します。 GPO を制御するためのアクセス許可が与えられていない場合は、要求を送信するように求められます。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>テンプレートとして保存</strong></p></td>
<td align="left"><p>選んだ GPO の設定に基づいて新しいテンプレートを作成します。</p></td>
</tr>
</tbody>
</table>

 

## レポート


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">コマンド</th>
<th align="left">効果</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>設定</strong></p></td>
<td align="left"><p>選択された GPO 内の設定を表示する HTML ベースまたは XML ベースのレポートを生成します。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>相違点</strong></p></td>
<td align="left"><p>選択した2つの Gpo、または選んだ GPO とテンプレート内の設定を比較して、HTML ベースまたは XML ベースのレポートを作成します。</p></td>
</tr>
</tbody>
</table>

 

## その他


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">コマンド</th>
<th align="left">効果</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Refresh</strong></p></td>
<td align="left"><p>グループポリシー管理コンソール (GPMC) の表示を更新して、変更を反映します。 表示が更新されるまで、一部の変更は表示されません。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>ヘルプ</strong></p></td>
<td align="left"><p>AGPM のヘルプを表示します。</p></td>
</tr>
</tbody>
</table>

 

### その他の参照情報

-   [[内容] タブ](contents-tab-agpm40.md)

-   [編集者タスクの実行](performing-editor-tasks-agpm40.md)

-   [承認者タスクの実行](performing-approver-tasks-agpm40.md)

-   [レビュー担当者タスクの実行](performing-reviewer-tasks-agpm40.md)

 

 





