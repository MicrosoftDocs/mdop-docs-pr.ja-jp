---
title: Application Virtualization Sequencer の実装計画
description: Application Virtualization Sequencer の実装計画
author: dansimp
ms.assetid: 052f32fe-ad13-4921-a8ce-4a657eb2b2bf
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: ac62991e290dcd2da1c42f025a19365bda239fb8
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10815894"
---
# Application Virtualization Sequencer の実装計画


シーケンスは、仮想アプリケーションとアプリケーションパッケージを作成するためにアプリケーションの仮想化によって使用されるプロセスであり、Application Virtualization Sequencer ソフトウェアがインストールされているコンピューターを使用する必要があります。

シーケンス処理の際には、Sequencer はモニターモードに配置され、シーケンス処理されるアプリケーションはシーケンスコンピューターにインストールされます。 次に、シーケンス処理されたアプリケーションが起動され、最も重要でよく使われる関数が実行されるため、監視プロセスでは、アプリケーションの実行に必要なアプリケーションパッケージの最小のコンテンツを含むプライマリ機能ブロックを構成できます。 これらの手順を完了すると、監視モードが停止し、シーケンス処理されたアプリケーションが保存されて、適切な操作が確認されます。

優先順位を付けるためにどのアプリケーションを選ぶかを決定するときは、特定のアプリケーションを順序指定できないことに注意してください。 これには、Internet Explorer、デバイスドライバー、起動時にサービスを起動するアプリケーションなど、Windows オペレーティングシステムの特定の部分が含まれます。

Sequencer のインストール方法の詳細については、「 [Application Virtualization sequencer をインストールする方法](how-to-install-the-application-virtualization-sequencer.md)」を参照してください。

**重要** すべてのシーケンス処理プランは、企業のセキュリティチームによってレビューおよび承認される必要があります。 一般的に、Sequencer 操作はラボの運用環境とは別に維持されます。 これは、ビジネス要件に基づいて、必要に応じて簡単に、または包括的にすることができます。 シーケンス処理のコンピューターでは、完了したパッケージを運用サーバーにコピーするために企業ネットワークへの接続が必要になります。 ただし、通常はウイルス対策を行わないで運営されているため、企業ネットワーク上にはないものとします。たとえば、ファイアウォールまたは分離されたネットワークセグメントで操作することができます。 分離仮想ネットワークを共有するように構成された仮想マシンを使用することも、受け入れられる方法です。 企業のセキュリティポリシーに従って、この状況に安全に対処してください。

 

シーケンス処理を計画するための主な手順は、次のとおりです。

-   毎月処理する必要があるアプリケーションの数、それらのアプリケーションのサイズ、今後の更新プログラムの順序を指定するための余裕を追加します。 パッケージは、最大 4 GB のサイズ、圧縮または非圧縮のいずれかにすることができます。

-   組織が各アプリケーションのシーケンスを実行するために、系統的で反復可能なプロセスを準備し、文書化します。 これには、各実行のチェックリストとバージョンコントロールのプロセスを使用する必要があります。 順序付けされた各アプリケーションの追跡ログを使用することも、パッケージに関する技術的な問題を調査する際に非常に役立ちます。

-   シーケンスアプリケーションの場合、処理スループットに最適化された高パフォーマンスのコンピューターを使用します。これには、最低 4 GB の RAM と高速な CPU (3 GHz 以上) が使用されます。 高速ハードディスクと別個のディスクボリュームを使用すると、パフォーマンスが向上することもあります。 仮想マシンは、簡単にリセットできるため、シーケンスには適しています。また、ローカルパーティション上のクリーンな画像を備えた物理コンピューターを使って、各パッケージの順序付け操作が完了した後ですばやく再イメージングを有効にすることもできます。

    **重要** セーフモードでの App-v sequencer の実行はサポートされていません。

     

-   Microsoft Office や Java ランタイム環境などの統合要素を含む、シーケンス処理されたアプリケーションのオペレーティング環境を理解していることを確認します。これは、アプリケーションを順序付けする前に、シーケンスコンピューターに何かをインストールする必要があるかどうかを判断することが多いためです。

-   新しいシーケンス処理の各操作は常に、クリーンな基本イメージで開始するようにしてください。 優先順位のコンピューターがリセットされたことを確認します。保存した画像を物理コンピューターに復元するか、すべての変更を破棄した後で仮想マシンを再起動します。 ベースイメージには、保存する前に Windows Update から適用された最新の更新プログラムが適用されている必要があります。

-   シーケンス処理中に、固定されたプラットフォームを使用することが重要であるため、ウイルス対策スキャナーや Windows Update などのインストール監視プロセスに干渉する可能性のある、シーケンスコンピューター上のすべての設定をオフにします。 この手順ではセキュリティのリスクが深刻であるため、コンピューターとネットワーク、およびシーケンス処理されたアプリケーションパッケージを保護するために、適切な措置が講じられていることを確認してください。 アプリパッケージの順序を付ける前に、ウイルス対策スキャンを実行することをお勧めします。

-   シーケンス後に各アプリケーションをテストするための詳細なプロセスを含めます。 シーケンス処理されたアプリケーションをテストすることによって、仮想化されたアプリケーションをエンドユーザーに展開する前に、正しく機能するかどうかを確認します。 エンドユーザーに大規模な展開を行う前にテストを行う最後の手順として、テストグループへの試験的展開を計画する必要があります。

-   連続したアプリケーションをテストする場合は、同じ種類のコンピューター機器を選択し、会社の運用環境で使用されている同じオペレーティングシステムを実行します。 適切に構成されていれば、仮想マシンと物理マシンのいずれかを使うことができます。

## 関連トピック


[Application Virtualization Sequencer のハードウェア要件とソフトウェア要件](application-virtualization-sequencer-hardware-and-software-requirements.md)

[Application Virtualization Sequencer をインストールする方法](how-to-install-the-application-virtualization-sequencer.md)

[Application Virtualization Sequencer をアップグレードする方法](how-to-upgrade-the-application-virtualization-sequencer.md)

[セキュリティと保護の概要](security-and-protection-overview.md)

 

 





