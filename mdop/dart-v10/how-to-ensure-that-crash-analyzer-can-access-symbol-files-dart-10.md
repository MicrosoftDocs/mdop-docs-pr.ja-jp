---
title: クラッシュ アナライザーがシンボル ファイルにアクセスできるようにする方法
description: クラッシュ アナライザーがシンボル ファイルにアクセスできるようにする方法
author: dansimp
ms.assetid: 39e307bd-5d21-4e44-bed6-bf532f580775
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: support
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 8e0ba2fa777039e1c6ffb91dd997438d8ea50616
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10822607"
---
# クラッシュ アナライザーがシンボル ファイルにアクセスできるようにする方法


通常、デバッグ情報は、プログラムとは別のシンボルファイルに格納されます。 応答を停止したアプリケーションをデバッグするときに、シンボル情報へのアクセス権を持っている必要があります。

**クラッシュアナライザー**を実行すると、シンボルファイルが自動的にダウンロードされます。 コンピューターがインターネットに接続されていない場合、またはネットワークでコンピューターが HTTP プロキシサーバーにアクセスする必要がある場合、シンボルファイルをダウンロードすることはできません。

**クラッシュアナライザーがシンボルファイルにアクセスできることを確認するには**

1.  **ダンプファイルを別のコンピューターにコピーします。** インターネットに接続していないためにシンボルをダウンロードできない場合は、インターネットに接続されているコンピューターにメモリダンプファイルをコピーし、そのコンピューターでスタンドアロンの**Crash Analyzer ウィザード**を実行します。

2.  **別のコンピューターからシンボルファイルにアクセスします。** インターネットに接続していないためにシンボルをダウンロードできない場合は、インターネット接続されているコンピューターからシンボルをダウンロードして、インターネットに接続していないコンピューターにファイルをコピーするか、ネットワークドライブをローカルネットワーク上のシンボルが使用可能な場所にマップすることができます。 Windows 回復環境 (WindowsRE) で**クラッシュアナライザー**を実行した場合、Microsoft Diagnostics And Recovery ツールセット (DaRT) 10 の回復イメージにシンボルファイルを含めることができます。

3.  **HTTP プロキシサーバー経由でのシンボルファイルへのアクセス。** HTTP プロキシサーバーにアクセスする必要があるため、シンボルをダウンロードできない場合は、次の手順を使用して HTTP プロキシサーバーにアクセスします。 DaRT 10 では、[ **Crash Analyzer] ウィザード**では、ラベルプロキシサーバーでマークされた [**シンボルファイルの場所の指定**] ダイアログページで設定を行うことができます **("server: port" の形式を使用します)**。 このテキストボックスを使用して、プロキシサーバーを指定できます。 [ ** &lt; Hostname &gt; : &lt; port &gt; **] の形式でプロキシアドレスを入力します。ここで、 &lt; **hostname** &gt; は DNS 名または IP アドレスで、 &lt; **ポート** &gt; は TCP ポート番号です。 **クラッシュアナライザー**を実行するには、2つのモードがあります。 次に、これらの各モードでプロキシ設定を使用する方法について説明します。

    -   **オンラインモード:** このモードでは、[プロキシサーバー] フィールドが空白になっている場合、ウィザードでは、コントロールパネルの [インターネットオプション] のプロキシ設定が使用されます。 提供されているテキストボックスにプロキシアドレスを入力すると、そのアドレスが使用され、[インターネットオプション] の設定が上書きされます。

    -   Windows 回復環境 (WindowsRE): [**診断/回復ツールセット**] ウィンドウから**クラッシュアナライザー**を実行すると、既定のプロキシアドレスは表示されません。 コンピューターがインターネットに直接接続されている場合は、プロキシアドレスは必要ありません。 このため、ウィザードの設定でこのフィールドを空白のままにすることができます。 コンピューターがインターネットに直接接続されておらず、プロキシサーバーがあるネットワーク環境内にある場合は、ウィザードのプロキシフィールドを設定して、シンボルストアにアクセスする必要があります。 プロキシアドレスは、ネットワーク管理者から取得できます。 プロキシサーバーを設定することが重要なのは、パブリックシンボルストアがインターネットに接続されている場合のみです。 シンボルがすでに DaRT リカバリ画像に登録されている場合、またはローカルで利用可能な場合は、プロキシサーバーを設定する必要はありません。

## 関連トピック


[クラッシュ アナライザーを使用したシステム障害の診断](diagnosing-system-failures-with-crash-analyzer-dart-10.md)

[DaRT 10 の操作](operations-for-dart-10.md)

 

 





