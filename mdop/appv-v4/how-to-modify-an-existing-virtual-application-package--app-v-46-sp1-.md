---
title: 既存の仮想アプリケーション パッケージを変更する方法 (App-V 4.6 SP1)
description: 既存の仮想アプリケーション パッケージを変更する方法 (App-V 4.6 SP1)
author: dansimp
ms.assetid: f43a9927-4325-4b2d-829f-3068e4e84349
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: f0e9d45a32afa240ce7f6fb2ee5dfbc51889c1fa
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10817037"
---
# 既存の仮想アプリケーション パッケージを変更する方法 (App-V 4.6 SP1)


既存の仮想アプリケーションパッケージを変更するには、次の手順を使用します。 以下の手順を使用して、次の操作を行うことができます。

-   既存の仮想アプリケーションパッケージの一部であるアプリケーションを更新します。 この処理を実行するには、このドキュメントの **「既存のアプリケーションパッケージのアプリケーションを更新するに**は」の手順を使用します。

-   既存の仮想アプリケーションパッケージに関連付けられているプロパティを変更します。 この処理を実行するには、このドキュメントの **「既存の仮想アプリケーションパッケージに関連するプロパティを変更するに**は」の手順を使用します。

-   既存の仮想アプリケーションパッケージに新しいアプリケーションを追加します。 この処理を実行するには、このドキュメントの **「既存の仮想アプリケーションパッケージに新しいアプリケーションを追加するに**は」の手順を使用します。

仮想アプリケーションパッケージを変更するには、App-v Sequencer をインストールしておく必要があります。 App-v Sequencer のインストールの詳細については、「 [Sequencer のインストール方法 (app-v 4.6 SP1)](how-to-install-the-sequencer---app-v-46-sp1-.md)」を参照してください。

**既存の仮想アプリケーションパッケージのアプリケーションを更新するには**

1.  App-v sequencer を実行しているコンピューターで app-v sequencer を起動するには、[すべてのプログラムを**起動**する] をクリックし  /  **All Programs**  /  ます。**microsoft**application virtualization  /  **microsoft application virtualization Sequencer**。

2.  App-v Sequencer で、[**既存の仮想アプリケーションパッケージの変更**] をクリックし、[**次へ**] をクリックします。

3.  [**タスクの選択**] ページで、[**既存のパッケージのアプリケーションの更新**] をクリックし、[**次へ**] をクリックします。

4.  [**パッケージの選択**] ページで [**参照**] をクリックして、更新するアプリケーションが含まれている仮想アプリケーションパッケージを見つけ、[**次へ**] をクリックします。

5.  [**コンピューターの準備**] ページで、アプリケーションの更新に失敗する原因となる可能性のある問題を確認します。または、アプリケーションの更新に不要なデータが含まれている可能性があります。 続行する前に、発生する可能性があるすべての問題を解決することを強くお勧めします。 競合を修正した後、表示される情報を更新するには、[**更新**] をクリックします。 すべての潜在的な問題を解決したら、[**次へ**] をクリックします。

    **重要** ウイルススキャンソフトウェアを無効にする必要がある場合は、sequencer を実行しているコンピューターをスキャンして、不要なファイルや悪意のあるファイルがパッケージに追加されないようにします。

     

6.  [**インストーラーの選択**] ページで [**参照**] をクリックし、アプリケーションの更新インストールファイルを指定します。 更新プログラムに関連するインストーラーファイルがなく、すべてのインストール手順を手動で実行する予定の場合は、[**このオプションを選択してカスタムインストールを実行**する] チェックボックスをオンにし、[**次へ**] をクリックします。

7.  **インストール**ページで、sequencer とアプリケーションインストーラーの準備ができたら、アプリの更新プログラムをインストールして、sequencer がインストールプロセスを監視できるようにします。 インストールの一部として追加のインストールファイルを実行する必要がある場合は、[**実行**] をクリックして、追加のインストールファイルを見つけて実行します。 インストールが完了したら、[インストールを**完了**しました] を選択します。 **[次へ]** をクリックします。

    **注** Sequencer は、sequencer を実行しているコンピューターに対するすべての変更とインストールを監視します。これには、シーケンスウィザードの外部で実行される変更とインストールが含まれます。

     

8.  [**インストールレポート**] ページで、更新した仮想アプリケーションに関する情報を確認できます。 [**追加情報**] に表示される情報について詳しくは、イベントをダブルクリックしてください。 情報を確認したら、[**次へ**] をクリックします。

9.  [**ストリーミング**] ページで、各プログラムを実行して、ターゲットコンピューターで最適化し、より効率的に実行できるようにします。 すべてのアプリケーションが実行されるまでに数分かかることがあります。 すべてのアプリケーションが実行されたら、各アプリケーションを閉じて、[**次へ**] をクリックします。

    **注** この手順の実行中にアプリケーションの読み込みを中止する場合は、 **[アプリケーションの起動**] ダイアログボックスで [**停止**] をクリックし、次のいずれかのオプションをクリックします。 [すべての**アプリケーションを停止**] または [**このアプリケーションを停止**する] は、必要に応じて設定します。

     

10. [**パッケージの作成**] ページでパッケージを保存せずに変更するには、[**パッケージエディターを使用してパッケージを保存せずにパッケージを変更**します] チェックボックスをオンにします。 このオプションを選択すると、Sequencer コンソールのパッケージが開き、保存する前にパッケージを変更することができます。 **[次へ]** をクリックします。

    パッケージを直ちに保存するには、[既定で**パッケージを保存**する] を選択します。 パッケージに関連付けられる**コメント**(省略可能) を追加します。 コメントは、パッケージについてのバージョンとその他の情報を特定するのに役立ちます。 既定の**保存場所**も表示されます。 既定の場所を変更するには、[**参照**] をクリックし、新しい場所を指定します。 圧縮されていないパッケージサイズが表示されます。 パッケージサイズが 4 GB (非圧縮) を超えていて、パッケージをターゲットコンピューターにストリーミングする予定の場合は、[**パッケージの圧縮**] を選択し、[**作成**] をクリックする必要があります。

11. [**完了**] ページで、[**閉じる**] をクリックしてウィザードを閉じます。 このパッケージは、sequencer で利用できるようになりました。

**既存の仮想アプリケーションパッケージに関連付けられているプロパティを変更するには**

1.  App-v sequencer を実行しているコンピューターで app-v sequencer を起動するには、[すべてのプログラムを**起動**する] をクリックし  /  **All Programs**  /  ます。**microsoft**application virtualization  /  **microsoft application virtualization Sequencer**。

2.  App-v Sequencer で、[**既存の仮想アプリケーションパッケージの変更**] をクリックし、[**次へ**] をクリックします。

3.  [**タスクの選択**] ページで [**パッケージの編集**] をクリックし、[**次へ**] をクリックします。

4.  [**パッケージの選択**] ページで [**参照**] をクリックして、変更するアプリケーションのプロパティが含まれている仮想アプリケーションパッケージを見つけ、[**編集**] をクリックします。

5.  Sequencer コンソールでは、次のいずれかのタスクを実行できます。

    -   パッケージのプロパティを表示します。

    -   パッケージの変更履歴を表示します。

    -   関連付けられたパッケージファイルを表示します。

    -   レジストリ設定を編集します。

    -   追加のパッケージ設定を確認します (オペレーティングシステムのファイルプロパティを除く)。

    -   関連付けられた Windows インストーラー (MSI) を作成します。

    -   OSD ファイルを変更します。

    -   パッケージの圧縮と圧縮解除を行います。

    -   ファイルの種類の関連付けを追加します。

    -   仮想化されたレジストリキーの状態 (上書きまたはマージ) を設定します。

    -   仮想化されたフォルダーの状態を設定します。

    -   仮想ファイルシステムのマッピングを編集します。

6.  パッケージプロパティの変更が完了したら、[**ファイル**の  /  **保存**] をクリックしてパッケージを保存します。

**既存の仮想アプリケーションパッケージに新しいアプリケーションを追加するには**

1.  App-v sequencer を実行しているコンピューターで app-v sequencer を起動するには、[すべてのプログラムを**起動**する] をクリックし  /  **All Programs**  /  ます。**microsoft**application virtualization  /  **microsoft application virtualization Sequencer**。

2.  App-v Sequencer で、[**既存の仮想アプリケーションパッケージの変更**] をクリックし、[**次へ**] をクリックします。

3.  [**タスクの選択**] ページで、[**新しいアプリケーションの追加**] をクリックし、[**次へ**] をクリックします。

4.  [**パッケージの選択**] ページで [**参照**] をクリックして、アプリケーションを追加する仮想アプリケーションパッケージを指定し、[**次へ**] をクリックします。

5.  [**コンピューターの準備**] ページで、パッケージの作成に失敗する可能性のある問題を確認します。または、更新に不要なデータが含まれている可能性があります。 続行する前に、発生する可能性があるすべての問題を解決することを強くお勧めします。 競合を修正した後、表示される情報を更新するには、[**更新**] をクリックします。 すべての潜在的な問題を解決したら、[**次へ**] をクリックします。

    **重要** ウイルススキャンソフトウェアを無効にする必要がある場合は、sequencer を実行しているコンピューターをスキャンして、不要なファイルや悪意のあるファイルがパッケージに追加されないようにします。

     

6.  [**インストーラーの選択**] ページで [**参照**] をクリックして、アプリケーションのインストールファイルを指定します。 アプリケーションに関連付けられたインストーラーファイルがなく、インストール手順を手動で実行する場合は、[**このオプションを選択してカスタムインストールを実行**する] チェックボックスをオンにし、[**次へ**] をクリックします。

7.  **インストール**ページで、sequencer とアプリケーションインストーラーの準備ができたら、アプリをインストールして、sequencer がインストールプロセスを監視できるようにします。 インストールの一部として追加のインストールファイルを実行する必要がある場合は、[**実行**] をクリックして、追加のインストールファイルを見つけて実行します。 インストールが完了したら、[インストールを**完了**しました] を選択します。 **[次へ]** をクリックします。 [**フォルダーの参照**] ダイアログボックスで、アプリケーションをインストールするプライマリディレクトリを指定します。 これは新しい場所であり、仮想アプリケーションパッケージの既存のバージョンを上書きしないようにする必要があります。

    **注** Sequencer を実行しているコンピューターへのすべての変更とインストールは、sequencer によって監視されます。これには、シーケンスウィザードの外部で実行される変更とインストールが含まれます。

     

8.  [**ソフトウェアの構成**] ページで、必要に応じてパッケージに含まれるプログラムを実行します。 この手順では、ターゲットコンピューターにパッケージを展開して実行する前に、アプリの実行に必要な関連付けられたすべてのライセンスまたは構成タスクを完了することができます。 すべてのプログラムを同時に実行するには、1つ以上のプログラムを選択し、[**すべて実行**] をクリックします。 特定のプログラムを実行するには、実行するプログラムを選択し、[**実行**] をクリックします。 必要な構成タスクを完了して、アプリケーションを閉じます。 すべてのプログラムが実行されるまでに数分かかることがあります。 **[次へ]** をクリックします。

9.  [**インストールレポート**] ページで、更新した仮想アプリケーションに関する情報を確認できます。 [**追加情報**] に表示される情報について詳しくは、イベントをダブルクリックしてください。 情報を確認したら、[**次へ**] をクリックします。

10. 仮想アプリケーションのインストールと構成が完了したら、[**カスタマイズ**] ページで [**今すぐ停止**] を選択し、この手順の手順14に進みます。 次の一覧の項目をカスタマイズする場合は、[**ユーザー設定**] をクリックします。

    -   アプリケーションに関連付けられているファイルの種類の関連付けを編集します。

    -   ストリーミング用の仮想パッケージを準備します。 ストリーミングにより、仮想アプリケーションパッケージがターゲットコンピューターで実行されるときのエクスペリエンスが向上しました。

    **[次へ]** をクリックします。

11. [**ショートカットの編集**] ページでは、パッケージ内のさまざまなアプリケーションに関連付けられるファイルの種類の関連付け (FTA) をオプションで構成できます。 新しい FTA を作成するには、左側のウィンドウでカスタマイズするアプリケーションを選択して展開し、[**追加**] をクリックします。 [**ファイルの種類の関連付けの追加**] ダイアログボックスで、新しい FTA に必要な情報を入力します。 アプリケーションに関連付けられているショートカット情報を確認するには、アプリケーションの下にある [**ショートカット**] チェックボックスをオンにし、[**場所**] ウィンドウでアイコンファイル情報を確認します。 既存の FTA を編集するには、[**編集**] をクリックします。 FTA を削除するには、FTA を選択し、[**削除**] をクリックします。 **[次へ]** をクリックします。

12. [**ストリーミング**] ページで、各プログラムを実行して、ターゲットコンピューターで最適化し、より効率的に実行できるようにします。 すべてのアプリケーションが実行されるまでに数分かかることがあります。 すべてのアプリケーションが実行されたら、各アプリケーションを閉じて、[**次へ**] をクリックします。

    **注** この手順の実行中にアプリケーションの読み込みを中止する場合は、 **[アプリケーションの起動**] ダイアログボックスで [**停止**] をクリックし、必要に応じて、[すべての**アプリケーションを停止**する] または [**このアプリケーションのみ**を停止する] チェックボックスをオンにします。

     

13. [**パッケージの作成**] ページで、[パッケージ**エディターを使ってパッケージを保存せずにパッケージを変更**します] チェックボックスをオンにして、パッケージを保存せずに変更します。 このオプションを選択すると、sequencer コンソールのパッケージが開き、保存する前にパッケージを変更することができます。 **[次へ]** をクリックします。

    [**今すぐパッケージを保存**する] を選択して、パッケージを直ちに保存します。 パッケージに関連付けられる**コメント**(省略可能) を追加します。 コメントは、パッケージについてのバージョンとその他の情報を特定するのに役立ちます。 既定の**保存場所**も表示されます。 既定の場所を変更するには、[**参照**] をクリックし、新しい場所を指定します。 圧縮されていないパッケージサイズが表示されます。 パッケージサイズが 4 GB (非圧縮) を超えていて、パッケージをターゲットコンピューターにストリーミングする予定の場合は、[**パッケージの圧縮**] を選択する必要があります。 **[作成]** をクリックします。

14. **[完了]** ページで、**[閉じる]** をクリックします。 このパッケージは、sequencer で利用できるようになりました。

## 関連トピック


[Application Virtualization Sequencer のタスク (APP-V 4.6 SP1)](tasks-for-the-application-virtualization-sequencer--app-v-46-sp1-.md)

 

 




