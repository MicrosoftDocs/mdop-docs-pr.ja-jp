---
title: プロジェクト テンプレートを作成して使用する方法
description: プロジェクト テンプレートを作成して使用する方法
author: dansimp
ms.assetid: 2063f0b3-47a1-4090-bf99-0f26b107331c
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: e7640b9dc1e7baec194315400ee5672dfa83f394
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10814259"
---
# プロジェクト テンプレートを作成して使用する方法


App-v 5.0 プロジェクトテンプレートを使用して、既存の仮想アプリケーションパッケージに関連付けられている一般的に適用される設定を保存することができます。 これらの設定は、環境に新しい仮想アプリケーションパッケージを作成するときに適用できます。 プロジェクトテンプレートを使うと、仮想アプリケーションパッケージの作成プロセスを効率化することができます。

**注** パッケージのアップグレード中に、場合によっては、App-v 5.0 プロジェクトテンプレートを適用することができます。 たとえば、カスタムの除外リストを使ってアプリケーションをシーケンスした場合、関連付けられたテンプレートを作成して保存してから、シーケンス処理されたアプリケーションのアップグレード中に使用できるようにすることをお勧めします。

App-v 5.0 のプロジェクトテンプレートは、app-v の5.0 アプリケーションアクセラレータがアプリケーション固有であり、App-v の5.0 プロジェクトテンプレートを複数のアプリケーションに適用できるため、app-v 5.0 アプリケーションアクセラレータとは異なります。

新しいテンプレートを作成して適用するには、次の手順を使用します。

**プロジェクトテンプレートを作成するには**

1.  Sequencer を実行しているコンピューターで app-v 5.0 sequencer を起動するには、[すべてのプログラムを**起動**する] をクリックし  /  **All Programs**  /  ます。**microsoft**application virtualization  /  **microsoft application virtualization sequencer**。

**注** 現在、仮想アプリケーションパッケージが App-v 5.0 Sequencer コンソールで開かれている場合は、手順3に進んでください。

2. App-v 5.0 プロジェクトテンプレートで保存する設定を含む既存の仮想アプリケーションパッケージを開くには、[**ファイル**を開く] をクリックし、[  /  **Open****パッケージの編集**] をクリックします。 [**パッケージの選択**] ページで [**参照**] をクリックし、開く仮想アプリケーションパッケージを探します。 **[編集]** をクリックします。

3. App-v 5.0 Sequencer コンソールでテンプレートファイルを保存するには、[ファイルを**File**  /  **テンプレートとして保存**] をクリックします。 新しいテンプレートと共に保存される設定を確認したら、[ **OK]** をクリックします。 新しい App-v 5.0 プロジェクトテンプレートに関連付ける名前を指定します。 [保存] をクリックします。
   新しい App-v 5.0 プロジェクトテンプレートは、この手順の手順3で指定したディレクトリに保存されます。

**プロジェクトテンプレートを適用するには**

**重要** プロジェクトテンプレートを使用して、パッケージアクセラレータと組み合わせて仮想アプリケーションパッケージを作成することはサポートされていません。

1.  Sequencer を実行しているコンピューターで app-v 5.0 sequencer を起動するには、[すべてのプログラムを**起動**する] をクリックし  /  **All Programs**  /  ます。**microsoft**application virtualization  /  **microsoft application virtualization sequencer**。

2.  App-v 5.0 プロジェクトテンプレートを使用して新しい仮想アプリケーションパッケージを作成またはアップグレードするには **、[**  /  **テンプレートから新規**作成] をクリックします。

3.  使用するプロジェクトテンプレートを選択するには、プロジェクトテンプレートが保存されているディレクトリを参照し、プロジェクトテンプレートを選択して、[**開く**] をクリックします。

    新しい仮想アプリケーションパッケージを作成します。 指定したテンプレートと共に保存された設定が、作成する新しい仮想アプリケーションパッケージに適用されます。

    App-v**の提案をお寄せ**ください。 [ここで](http://appv.uservoice.com/forums/280448-microsoft-application-virtualization)候補を追加または投票してください。 **App-v の問題が発生しましたか?** App-v の[TechNet フォーラム](https://social.technet.microsoft.com/Forums/home?forum=mdopappv)を使用します。

## 関連トピック


[APP-V 5.0 の操作](operations-for-app-v-50.md)








