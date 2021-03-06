---
title: 回復モードでドライブを回復する方法
description: 回復モードでドライブを回復する方法
author: dansimp
ms.assetid: 09d27e4b-57fa-47c7-a004-8b876a49f27e
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, security
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: c1151ffe7453eb8d07d2aa6dcb4c41f6b3efe6de
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10812954"
---
# 回復モードでドライブを回復する方法


Microsoft BitLocker の管理と監視 (MBAM) には、暗号化されたドライブの回復機能が含まれています。 これらの機能により、BitLocker によってそのボリュームが回復モードになったときに、BitLocker で保護されたボリュームへのアクセスに必要なツールのキャプチャと保存が可能になります。 BitLocker で保護されたボリュームは、PIN またはパスワードを紛失または忘れた場合、または信頼されているモジュールプラットフォーム (TPM) チップがコンピューターの BIOS またはスタートアップファイルへの変更を検出した場合に回復モードになります。

回復パスワード ID と関連付けられたユーザー識別子が指定されているときに回復パスワードを提供できる中央キー回復データシステムにアクセスするには、次の手順を使用します。

**重要** MBAM は、単一使用の回復キーを生成します。 この制限の下では、回復キーは1回だけ使用でき、その後は無効になります。 回復パスワードの1回の使用は、オペレーティングシステムドライブと固定ドライブに自動的に適用されます。 リムーバブルドライブでは、ドライブが取り外されたときに単一の使用が適用され、グループポリシーの設定がアクティブになっているコンピューターで、リムーバブルドライブを管理します。

 

**回復モードでドライブを回復するには**

1.  MBAM web サイトを開きます。

2.  ナビゲーションウィンドウで、[**ドライブの回復**] をクリックします。 [**暗号化されたドライブへのアクセスを回復する**web ページが開きます。

3.  ユーザーの Windows ログオンドメインとユーザー名、および回復キー ID の最初の8桁を入力して、一致する回復キーの候補の一覧を受け取ります。 または、完全な回復キーを受け取るには、回復キーの ID 全体を入力します。 [**ドライブロック解除の理由**] ドロップダウンリストから定義済みのオプションのいずれかを選択し、[**送信**] をクリックします。

    **注** MBAM Advanced ヘルプデスクユーザーの場合、ユーザードメインとユーザー ID のエントリは必要ありません。

     

4.  MBAM は、次の値を返します。

    1.  一致する回復パスワードが見つからなかった場合のエラーメッセージ

    2.  ユーザーが複数の一致する回復パスワードを持っている場合、一致する可能性がある複数の一致

    3.  送信されたユーザーの回復パスワードと回復パッケージ

        **注** 破損したドライブを回復する場合、回復パッケージオプションは、回復を試みるために必要な重要な情報を BitLocker に提供します。

         

5.  回復パスワードと回復パッケージを取得した後、回復パスワードが表示されます。 パスワードをコピーするには、[**キーのコピー**] をクリックして、回復パスワードをメールまたはその他の一時記憶域のテキストファイルに貼り付けます。 または、回復パスワードをファイルに保存するには、[**保存**] をクリックします。

6.  ユーザーが回復パスワードをシステムに入力するか、回復パッケージを使用すると、ドライブのロックが解除されます。

## 関連トピック


[MBAM での BitLocker 管理の実行](performing-bitlocker-management-with-mbam.md)

 

 





