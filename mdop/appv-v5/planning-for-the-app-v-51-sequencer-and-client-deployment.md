---
title: App-V 5.1 Sequencer および Client の展開計画
description: App-V 5.1 Sequencer および Client の展開計画
author: dansimp
ms.assetid: d92f8773-fa7d-4926-978a-433978f91202
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/21/2016
ms.openlocfilehash: 31a0296814b16ba1c776dca522423fc7b6b6ed96
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10813459"
---
# App-V 5.1 Sequencer および Client の展開計画


Microsoft Application Virtualization (App-v) 5.1 の使用を開始する前に、アプリ-V 5.1 sequencer、App-v 5.1 クライアントをインストールし、必要に応じて app-v 5.1 shared content store をインストールする必要があります。 以下のセクションでは、これらのインストールの計画について説明します。

## App-v 5.1 sequencer の展開を計画する


App-v 5.1 は、シーケンスと呼ばれるプロセスを使って、仮想化されたアプリケーションとアプリケーションパッケージを作成します。 シーケンスには、App-v 5.1 sequencer を実行するコンピューターを使用する必要があります。

**注** App-v 5.1 sequencer の新機能の詳細については、「[アプリ-v 5.1 について](about-app-v-51.md)」の「sequencer の機能**強化**」を参照してください。

 

App-v 5.1 sequencer を実行するコンピューターは、システムの最小要件を満たしている必要があります。 これらの要件の一覧については、「 [app-v 5.1 でサポートされている構成](app-v-51-supported-configurations.md)」を参照してください。

理想的には、仮想マシンとして実行されているコンピューターに sequencer をインストールすることをお勧めします。 これにより、sequencer を実行しているコンピューターをより簡単に "クリーン" 状態に戻すことができます。これにより、別のアプリケーションを順序付けることができます。 仮想マシンを使用して sequencer をインストールする場合は、次の手順を実行する必要があります。

1.  関連するすべての sequencer の前提条件をインストールします。

2.  Sequencer をインストールします。

3.  環境の "スナップショット" を取る。

**重要** 会社のセキュリティチームが、シーケンス処理プランをレビューおよび承認する必要があります。 セキュリティ上の理由から、sequencer 操作は運用環境とは別のラボで保持する必要があります。 分離の配置は、ビジネス要件に基づいて、必要に応じてシンプルに、または包括的にすることができます。 シーケンスコンピューターでは、完了したパッケージを運用サーバーにコピーするために、会社のネットワークに接続できる必要があります。 ただし、優先順位のコンピューターは通常、ウイルス対策による保護なしで運営されているため、企業ネットワーク上では保護されていない必要があります。 たとえば、ファイアウォールまたは分離されたネットワークセグメントの背後で操作できる場合があります。 分離された仮想ネットワークを共有するように構成されている仮想マシンを使用できる場合もあります。 企業のセキュリティポリシーに従って、これらの懸念事項に安全に対応してください。

 

## App-v 5.1 クライアントの展開を計画する


ターゲットコンピューターで仮想化されたパッケージを実行するには、ターゲットコンピューターに App-v 5.1 クライアントをインストールする必要があります。 App-v 5.1 クライアントは、ターゲットコンピューターで仮想化されたアプリケーションを実行するコンポーネントです。 クライアントでは、ユーザーがアイコンや特定のファイルの種類を操作して、仮想化されたアプリケーションを開始できるようにします。 クライアントでは、管理サーバーからアプリケーションコンテンツを取得し、クライアントがアプリケーションを起動する前にコンテンツをキャッシュすることもできます。 2種類のクライアントがあります。リモートデスクトップサービスのクライアントであり、リモートデスクトップセッションホスト (RD セッションホスト) サーバーシステムと、他のすべてのコンピューターで使用される App-v 5.1 クライアントが使用されます。

App-v 5.1 クライアントは、インストーラコマンドラインを使用するか、インストールが完了した後で PowerShell スクリプトを使用して構成する必要があります。

App-v 5.1 クライアントソフトウェアを展開するには、事前に設定を慎重に定義しておく必要があります。 これは、さまざまな場所にあるコンピューターを使用していて、別の場所を使用するようにクライアントを構成する必要がある場合に特に重要です。

クライアントソフトウェアの展開方法も決定する必要があります。 各コンピューターにクライアントを手動で展開することもできますが、ほとんどの組織では、自動化されたプロセスを通じてクライアントを展開することをお勧めします。 大規模な組織には、業務用の電子ソフトウェア配布 (ESD) システムがあります。これは、理想的なクライアント展開システムです。 ESD システムが存在しない場合は、組織の標準的なソフトウェアインストール方法を使用できます。 可能な方法には、グループポリシーやさまざまなスクリプト手法があります。 クライアントコンピューターの数と場所によっては、この展開プロセスが複雑になることがあります。 すべてのコンピューターが正しい構成でクライアントをインストールできるように、構造化された手法を使用する必要があります。

クライアントの最小要件の一覧については、「 [app-v 5.1 の前提条件](app-v-51-prerequisites.md)」を参照してください。

## <a href="" id="bkmk-client-coexist"></a>App-v クライアントの共存の計画


App-v 5.1 クライアントは、app-v 4.6 クライアントと並行して展開できます。 クライアントの共存を使用するには、展開構成ファイルまたはユーザー構成ファイルを使用して、仮想化されたアプリケーションを追加または公開する必要があります。これらの構成ファイルには、アプリ-v 4.6 クライアントで動作するように構成する必要がある特定の設定が5.1 あります。 クライアントまたはサーバーのいずれかを使用してパッケージをアップグレードする場合、パッケージで構成ファイルを再送信する必要があります。 これは、対応する構成ファイルを持つすべてのパッケージに当てはまるため、クライアントの共存に固有ではありません。 ただし、パッケージのアップグレード中に構成ファイルを送信しない場合、パッケージの状態は、共存シナリオでは予期したとおりに機能しません。

App-v 5.1 動的構成ファイル特定のユーザーに対してパッケージをカスタマイズします。 使用する前に、動的ユーザー構成 (.xml) ファイルまたは動的展開構成ファイルを作成する必要があります。 ファイルを作成するには、高度な手動操作が必要です。

動的ユーザー構成ファイルを使用している場合、マニフェストファイルの拡張子について、App-v 5.1 情報は使用されません。 つまり、動的ユーザー構成ファイルには、マニフェストファイルの App-v 5.1 に固有の拡張子と、削除や更新などの必要な変更を含める必要があることを意味します。 カスタム構成ファイルの作成方法の詳細については、「 [app-v 5.1 管理コンソールを使用してカスタム構成ファイルを作成する方法](how-to-create-a-custom-configuration-file-by-using-the-app-v-51-management-console.md)」を参照してください。

## <a href="" id="bkmk-plan-for-scs"></a>App-v 5.1 Shared Content Store (SCS) の計画


App-v 5.1 shared content store モードでは、App-v 5.1 クライアントを実行しているコンピューターで仮想アプリケーションを実行できます。パッケージコンテンツは、App-v 5.1 クライアントを実行しているコンピューターに保存されません。 仮想アプリケーションは、クライアントから要求された場合にのみ、ターゲットコンピューターにストリーミングされます。

次の一覧は、App-v 5.1 shared content store を使用する場合のいくつかの利点を示しています。

-   アプリ間およびマルチユーザーアプリケーションの競合を減らし、回帰テストの必要性を減らしました

-   展開リスクを軽減してアプリケーションの展開を迅速化する

-   簡素化されたプロファイル管理






## <a href="" id="other-resources-for-the-app-v-5-1-deployment-"></a>App-v 5.1 の展開に関するその他のリソース


[App-V の展開計画](planning-to-deploy-app-v51.md)

## 関連トピック


[Sequencer をインストールする方法](how-to-install-the-sequencer-51beta-gb18030.md)

[APP-V Client を展開する方法](how-to-deploy-the-app-v-client-51gb18030.md)

[同じコンピューター上に App-v 4.6 と App-v 5.1 クライアントを展開する方法](how-to-deploy-the-app-v-46-and-the-app-v--51-client-on-the-same-computer.md)

[共有コンテンツ ストア モードの App-V 5.1 Client のインストール方法](how-to-install-the-app-v-51-client-for-shared-content-store-mode.md)

 

 





