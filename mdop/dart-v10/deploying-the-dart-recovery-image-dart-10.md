---
title: DaRT の回復イメージの展開
description: DaRT の回復イメージの展開
author: dansimp
ms.assetid: 2b859da6-e31a-4240-8868-93a754328cf2
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: support
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 7de3ed9c01a1808364158124c4f2dcab835823a7
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10813115"
---
# DaRT の回復イメージの展開


Microsoft Diagnostics and Recovery ツールセット (DaRT) 10 の回復イメージを含む国際標準化機構 (ISO) ファイルを作成した後、エンドユーザーやヘルプデスクの担当者が利用できるように、社内全体で DaRT 10 の回復イメージを展開できます。 DaRT リカバリイメージの展開に使用できる、4つのサポートされるメソッドが用意されています。 各方法の長所と短所を確認するには、「 [DaRT 10 の回復イメージを保存して展開する方法を計画](planning-how-to-save-and-deploy-the-dart-10-recovery-image.md)する」を参照してください。

DaRT 回復イメージウィザードを使用して、ISO イメージファイルを CD または DVD に書き込む

DaRT 回復イメージウィザードを使用して、ISO イメージファイルのコンテンツを USB フラッシュドライブ (UFD) に保存します。

ISO イメージから boot.ini ファイルを抽出し、エンドユーザーのコンピューターで使用できるリモートパーティションとして展開する

ISO イメージから boot.ini ファイルを抽出し、新しい Windows 10 インストールの回復パーティションに展開する

**重要** **Dart の回復イメージウィザード**では、画像を CD、DVD、または UFD に書き込むことができます。ただし、回復イメージを保存および展開するその他の方法には、DaRT に含まれていないツールに関連する追加の手順が必要です。 このセクションでは、これらの他の方法に関するガイダンスとリンクをいくつか紹介します。

 

## DaRT リカバリ画像を回復パーティションの一部として展開する


DaRT Recovery イメージウィザードの実行と回復イメージの作成が完了したら、ISO イメージファイルから boot.ini ファイルを抽出して、Windows 10 イメージの回復パーティションとして展開することができます。

[回復パーティションの一部として DaRT の回復イメージを展開する方法](how-to-deploy-the-dart-recovery-image-as-part-of-a-recovery-partition-dart-10.md)

## DaRT リカバリ画像をリモートのパーティションとして展開する


Windows 展開サービスなどの中央ネットワークブートサーバーで回復イメージをホストし、ユーザーまたはサポートスタッフがオンデマンドでコンピューターにイメージをストリーミングできるようにすることができます。

[リモート パーティションとして DaRT の回復イメージを展開する方法](how-to-deploy-the-dart-recovery-image-as-a-remote-partition-dart-10.md)

## DaRT リカバリイメージの展開に関するその他のリソース


[DaRT 10 の展開](deploying-dart-10.md)

 

 





