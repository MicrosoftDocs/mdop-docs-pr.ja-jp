---
title: MED-V イメージ リポジトリを設計する
description: MED-V イメージ リポジトリを設計する
author: dansimp
ms.assetid: e153154d-2751-4990-b94d-a2d76242c15f
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 08/30/2016
ms.openlocfilehash: e0c59a0dd2d1b3a78bd211c6a6353a86c77d8fc2
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10823614"
---
# MED-V イメージ リポジトリを設計する


MED-V イメージを作成してパックした後は、任意の場所にあるファイルサーバーに保存することができます。 ファイルは、1つ以上の IIS サーバーによって HTTP または HTTPS 経由で送信される場合があります。 イメージリポジトリは、複数の MED-V インスタンスで共有できます。

イメージリポジトリを設計するには、まず、各クライアントに画像を展開する方法と、クライアントにローカルイメージリポジトリが必要かどうかを決定する必要があります。 各リポジトリは、付随する IIS サーバーと共に設計および配置されます。

## 画像を配置する方法を決定する


各 MED-V ワークスペースに対して、MED-V イメージをクライアントに展開する計画を決定します。 これは、パックされた画像を保存するために必要なリポジトリの数と、それらのリポジトリが配置される場所を決定する際に重要となります。その後、リポジトリを設計します。

パックされた画像は、次の方法で展開できます。

-   ファイルサーバーと IIS サーバーで構成されるイメージ配布サーバーからネットワーク経由でダウンロードされます。

-   USB ドライブや DVD などのリムーバブルメディア。

-   Enterprise software distribution center を使用して、クライアントコンピューター上のイメージストアディレクトリに事前にステージングされている。

各クライアントに MED-V イメージを展開するために使用するメソッドと、その場所にイメージリポジトリが必要かどうかを決定します。

## 画像リポジトリの数を確認する


必要なリポジトリの最小数を決定したので、次のいずれかの条件が当てはまる場合は、さらに多くの情報を追加します。

-   MED-V の画像を分離する組織または規制上の理由: 一部の MED-V イメージは、同じリポジトリ内で共存できない場合があります。 たとえば、機密性の高い個人データの場合、データへのアクセスを必要とする従業員の限定されたユーザーのみが利用できるサーバー上のストレージが必要になることがあります。

-   分離ネットワークのクライアント—ネットワーク経由でイメージを展開する場合は、分離されたネットワークがあるかどうかを確認し、別のリポジトリが必要かどうかを確認します。 たとえば、多くの場合、組織は運用ネットワークからラボネットワークを分離します。

-   リモートネットワークのクライアント: 画像がネットワーク経由で展開される場合、クライアントが MED-V ワークスペースを読み込むときに適切なエクスペリエンスを提供するために十分な帯域幅のないネットワークリンクによって、一部のクライアントコンピューターがリポジトリから分離されることがあります。 必要に応じて、このニーズに対処するために追加の MED-V インスタンスを設計します。

これらのリポジトリをデザインに追加します。 各リポジトリの名前と設計の理由を決定します。 リポジトリに格納する MED-V イメージと、リポジトリからの画像を含む med-v のクライアントのどちらを読み込むかを決定します。

## イメージリポジトリを設計して配置する


クライアントが新しい画像を利用できるようになると、クライアントはイメージのダウンロードを開始します。 これにより、リポジトリで需要が高くなり、イメージリポジトリの設計時に考慮する必要があります。

各リポジトリについて、保存するデータの量を決定します。 リポジトリに格納される画像のサイズを合計します。 これは、ファイルサーバー上で必要なディスク領域の値です。

次に、リポジトリから MED-V イメージをダウンロードする可能性のあるクライアントの数を追加します。 これは、新しい MED-V イメージがリポジトリに読み込まれたときに発生する可能性がある同時ダウンロードの最大数です。 このファイルサーバーは、作成する IO 要求を満たすことができるディスクサブシステムで設計する必要があります。

イメージリポジトリは、MED-V サーバーと、SQL Server を実行しているサーバー、またはリモートファイル共有の同じシステム上に存在することができます。 また、Windows Server2008 Hyper-v VM で実行することもできます。 イメージリポジトリがサービスを実行しているクライアントのネットワーク上の場所を確認し、それらのクライアントのサービスレベルの期待値を満たす十分な帯域幅があるネットワーク上の場所にリポジトリを配置します。

### フォールトトレランス

イメージリポジトリが利用できない場合、クライアントは、新しいまたは更新された MED-V イメージをダウンロードできません。 ファイルサーバーとフォールトトレラントディスクのフォールトトレランスオプションを設計するには、「 [MICROSOFT SQL server 2008 ガイドのインフラストラクチャ計画と設計](https://go.microsoft.com/fwlink/?LinkId=163302)」を参照してください。

## IIS サーバーを設計して配置する


このセクションは、クライアントが HTTP または HTTPS を使ってネットワーク経由で画像ファイルをダウンロードする場合にのみ関連します。

IIS サーバーは、MED-V サーバーと SQL Server を実行しているサーバーと同じシステム上で共存させることができます。 また、Windows Server2008 Hyper-v VM で実行することもできます。 IIS サーバーインフラストラクチャには、組織のサービスレベルの期待値内でクライアントに画像を配信するための十分なスループットが必要です。 これによって作成される IO 要求を満たすことができるディスクサブシステムで設計する必要があります。

各イメージリポジトリについて、IIS を使用して、MED-V イメージをダウンロードできるクライアントの数を合計します。 これは、画像がリポジトリに読み込まれたときに発生する可能性がある同時ダウンロードの最大数です。 「[プロジェクトのスコープを定義](define-the-project-scope.md)して、IIS サーバーインフラストラクチャの設計を計画し、リポジトリに割り当てる適切な帯域幅を決定する」で決定されたスループットの合計とサービスレベルを使用します。

IIS インフラストラクチャを設計するには、『 [Microsoft インターネットインフォメーションサービス](https://go.microsoft.com/fwlink/?LinkId=160826)ガイド』を参照してください。

### フォールトトレランス

IIS サーバーインフラストラクチャを利用できない場合、クライアントは、新しいイメージや更新された画像をダウンロードできません。 フォールトトレランスを構成するために、Windows Server2008 ベースの IIS サーバーをフェールオーバークラスターに配置することができます。 IIS サーバーインフラストラクチャのフォールトトレランスを設計するには、『 [Microsoft インターネットインフォメーションサービス](https://go.microsoft.com/fwlink/?LinkId=160826)ガイド』を参照してください。

## 関連トピック


[エンタープライズ ソフトウェア配布システムを使用した MED-V ワークスペースの展開](deploying-a-med-v-workspace-using-an-enterprise-software-distribution-system.md)

[展開パッケージを使用した MED-V ワークスペースの展開](deploying-a-med-v-workspace-using-a-deployment-package.md)

 

 





