---
title: DaRT の回復イメージ ウィザードを使用して回復イメージを作成する方法
description: DaRT の回復イメージ ウィザードを使用して回復イメージを作成する方法
author: dansimp
ms.assetid: 1b8ef983-fff9-4d75-a2f6-53120c5c00c9
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: support
ms.sitesec: library
ms.prod: w10
ms.date: 08/30/2016
ms.openlocfilehash: 49253a8c0bf9c9073b57712acc773e4a57e31d72
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10822924"
---
# DaRT の回復イメージ ウィザードを使用して回復イメージを作成する方法


Microsoft 診断/回復ツールセット (DaRT) 7 には、Windows で使用される**Dart Recovery イメージウィザード**が含まれており、これを使って、起動可能な国際標準化機関 (ISO) 画像を作成します。 ISO 画像は、CD の生のコンテンツを表すファイルです。

**DaRT の回復イメージウィザード**には、次の情報が必要です。

-   [**ブートイメージ**の度] DaRT 回復イメージを作成するために必要な WINDOWS 7 DVD または windows 7 のソースファイルのパスを指定する必要があります。

-   **ツール選択**度度 DaRT リカバリ画像に含めるツールを選択できます。

-   [**リモート接続**]: DaRT 回復イメージに、ヘルプデスクとエンドユーザーコンピューター間のリモート接続を確立する機能を含めるかどうかを選ぶことができます。

-   **Windows 用デバッグツール**の場合は、windows 用のデバッグツールの場所を指定するように求められます。

-   **単体システム Sweeper 度の定義**。回復イメージを作成するときに最新の定義をダウンロードするか、後で定義をダウンロードするかを決めることができます。

-   **ドライバ**度 * また、ISO 画像にドライバを追加するかどうかを尋ねるメッセージが表示されます。

-   **追加ファイル**の角度問題の診断に役立つファイルを、ISO イメージに追加することができます。

-   **Iso イメージの場所**を確認する必要がある場合は、iso 画像を配置する場所を指定するように求められます。

-   **Cd または Dvd ドライブ**の * * cd または dvd ドライブを使って cd または dvd を焼き付けるかどうかを指定するように求められます。

**注** ISO イメージのサイズは、 **DaRT リカバリ画像ウィザード**で選択されたツールによって異なる場合があります。

 

## DaRT 回復イメージウィザードを使用して回復イメージを作成するには


**Dart リカバリ画像ウィザード**を使用して dart リカバリ画像を作成するには、次の手順を実行します。

### DaRT リカバリ画像に含めるツールを選択するには

**DaRT の回復イメージウィザード**には、**ツールの選択**ダイアログボックスが表示されます。 ツールを強調表示し、[**有効**] または [**無効**] ボタンをクリックして、DaRT リカバリ画像に含めるツールのリストからツールを選択または削除することができます。

回復イメージに含めるすべてのツールを選んだら、[**次へ**] をクリックします。

### リモート接続を許可するオプションを追加するには

[**リモート接続を許可**する] チェックボックスをオンにすると、**診断/回復ツールセット**ウィンドウに、ヘルプデスクエージェントとエンドユーザーコンピューター間のリモート接続を確立するオプションが提供されます。 ヘルプデスクエージェントは、リモート接続を確立した後、エンドユーザーのコンピューター上の DaRT ツールをリモートの場所から実行することができます。

[**ポート番号の指定**] チェックボックスをオンにして、リモート接続を確立するときに使用される特定のポート番号を入力できます。 1 ~ 65535 の範囲のポート番号を指定できます。 競合の可能性を最小限に抑えるため、ポート番号を1024以上にすることをお勧めします。

エンドユーザーがリモート接続を確立するときに受け取るカスタマイズされたメッセージを作成することもできます。 メッセージの最大文字数は2048です。

DaRT ツールのリモート実行の詳細については、「 [Dart リカバリ画像を使ってリモートコンピューターを回復する方法](how-to-recover-remote-computers-using-the-dart-recovery-image-dart-7.md)」を参照してください。

### Windows 用デバッグツールを DaRT 回復イメージに追加するには

**DaRT 回復イメージウィザード**の [ **Crash Analyzer** ] ダイアログボックスで、Windows 用のデバッグツールの場所を指定するように求められます。 ツールのコピーを持っていない場合は、Microsoft からダウンロードできます。 ダウンロードページへの次のリンクは、ウィザードに用意されています。 [Windows 用のデバッグツールをダウンロードしてインストール](https://go.microsoft.com/fwlink/?LinkId=99934)します。

**DaRT Recovery イメージウィザード**を実行しているコンピューター上のデバッグツールの場所を指定するか、または移動先のコンピューターにあるツールを使用するかどうかを決定することができます。 別のコンピューターでコピーを使用する場合は、クラッシュを診断する各コンピューターにツールがインストールされていることを確認する必要があります。

**注** ISO イメージに**Crash Analyzer**を含める場合は、Windows 用のデバッグツールも含めることをお勧めします。

 

Windows 用のデバッグツールを追加するには、次の手順を実行します。

1.  省略ハイパーリンクをクリックして、Windows 用デバッグツールをダウンロードします。

2.  次のいずれかのオプションを選択します。

    -   **次の場所で、Windows 用デバッグツールを使用**します。 このオプションを選択すると、ツールの場所を参照できます。

    -   **修復するシステム上の Windows 用デバッグツールを見つけ**ます。 このオプションを選択すると、Windows 用デバッグツールが問題のコンピューターで見つからない場合に、**クラッシュアナライザー**が機能しなくなります。

3.  完了したら、[**次へ**] をクリックします。

### 単体システム Sweeper の定義を DaRT リカバリ画像に追加するには

定義は、既知のマルウェアやその他の望ましくない可能性のあるソフトウェアのリポジトリです。 マルウェアは絶えず開発されているため、**スタンドアロンのシステム Sweeper**は現在の定義に依存して、コンピューターの設定をインストール、実行、または変更しようとしているソフトウェアが望ましくない可能性のあるソフトウェアであるかどうかを判断します。

DaRT リカバリ画像に最新の定義を含めるには (推奨)、[**はい、最新の定義をダウンロードしてください**] をクリックします。 定義の更新プログラムが自動的に開始されます。 この処理を完了するには、インターネットに接続している必要があります。

定義の更新をスキップするには、[**いいえ、後で定義を手動でダウンロード**します] をクリックします。 定義は DaRT リカバリ画像には含まれません。

回復イメージに最新の定義を含めない場合、または**スタンドアロンシステム Sweeper**を使用する準備ができた時点で回復イメージに含まれている定義が最新ではない場合は、**スタンドアロンシステム Sweeper**で提供されている手順に従って、スキャンを開始する前に最新の定義を取得してください。

**重要** 定義が存在しない場合はスキャンできません。

 

完了したら、[**次へ**] をクリックします。

### DaRT リカバリ画像にドライバを追加するには

**注意** 既定では、ドライバーを DaRT 回復イメージに追加すると、そのフォルダーにあるすべての追加ファイルとサブフォルダーが回復イメージに追加されます。 詳細については、「 [DaRT 7.0 のトラブルシューティング](troubleshooting-dart-70-new-ia.md)」を参照してください。

 

コンピューターを修復するときに必要になる可能性のある、DaRT7 の回復イメージに追加のドライバーを含める必要があります。 通常、Windows DVD に含まれていないストレージまたはネットワークコントローラーが含まれていることがあります。

**重要** 含めるドライバーを選択するときは、ワイヤレス接続 (Bluetooth や 802.11 a/b/g/g など) が DaRT でサポートされていないことに注意してください。

 

**回復イメージに記憶域ドライバーまたはネットワークコントローラードライバーを追加するには**

1.  **DaRT 回復イメージウィザード**の [**追加ドライバー** ] ダイアログボックスで、[**デバイスの追加**] をクリックします。

2.  ドライバーに追加するファイルを参照し、[**開く**] をクリックします。

    **注** **ドライバー**ファイルは、記憶域またはネットワークコントローラーの製造元によって提供されます。

     

3.  追加するすべてのドライバーについて、手順1と2を繰り返します。

4.  完了したら、[**次へ**] をクリックします。

### DaRT リカバリ画像にファイルを追加するには

次の手順に従って、回復イメージにファイルを追加して、コンピューターの問題の診断に使用できるようにします。

1.  **DaRT 回復イメージウィザード**の [**追加ファイル**] ダイアログボックスで、[**ファイルの表示**] をクリックします。 これにより、共有ファイルを含むフォルダーが表示されたエクスプローラーウィンドウが開きます。

2.  このダイアログボックスに表示されているフォルダー内にサブフォルダーを作成します。

3.  目的のファイルを新しいサブフォルダーにコピーします。

4.  完了したら、[次へ] をクリックし**ます。**

### DaRT リカバリ画像が含まれる ISO の場所を選択するには

次の手順に従って、ISO イメージを作成する場所を指定します。

1.  **DaRT 回復イメージウィザード**の [**起動イメージの作成**] ダイアログボックスで、[**参照**] をクリックします。

2.  [**名前を付けて保存**] ウィンドウで目的の場所を参照し、[**保存**] をクリックします。

3.  完了したら、[**次へ**] をクリックします。

ISO イメージのサイズは、選んだツールとウィザードで追加したファイルによって異なります。

この機能を使うには、CD または DVD に書き込むほとんどのプログラムにこの拡張子が必要であるため、ISO イメージのファイル名拡張子は **.iso**である必要があります。 別の場所を指定しない場合は、 **DaRT70**名前の付いた iso 画像がデスクトップに作成されます。

### 回復イメージを CD または DVD に書き込むには

**DaRT Recovery イメージウィザード**で、コンピューター上に対応する cd-rw ドライブが検出された場合は、ISO イメージをディスクに書き込むことができます。 CD または DVD に書き込みを行うときに、ウィザードでドライブが認識されない場合は、ドライブに付属していたプログラムなどの別のプログラムを使用する必要があります。 Duplicator、複製サービス、または CD または DVD 書き込みソフトウェアを使用して、追加のコピーを作成することができます。

1.  **DaRT 回復イメージウィザード**の [**書き込み可能な CD/dvd に書き込み**] ダイアログボックスで、[**次の書き込み可能な cd/Dvd ドライブにイメージを書き込む**] を選びます。

2.  CD または DVD ドライブを選択します。

    **注** ドライブが認識されず、新しいドライブをインストールする場合は、[**ドライブの一覧の更新**] をクリックして、利用可能なドライブの一覧を自動的に更新することができます。

     

3.  **[次へ]** をクリックします。

## 関連トピック


[DaRT 7.0 の回復イメージの作成](creating-the-dart-70-recovery-image-dart-7.md)

 

 




