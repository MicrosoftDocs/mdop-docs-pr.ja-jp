---
title: 旧バージョンの MBAM からのアップグレード
description: 旧バージョンの MBAM からのアップグレード
author: dansimp
ms.assetid: 73b425cf-9cd9-4ebc-a35e-1b3bf18596ce
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, security
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: af45d193a5e8001288e70389ff220cb5d8269918
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10823807"
---
# 旧バージョンの MBAM からのアップグレード


Microsoft BitLocker の管理と監視 (MBAM) を MBAM 2.0 にアップグレードするには、次の操作を実行します。

-   **インプレースサーバーの置き換え**– Mbam サーバーをアップグレードするには、インストーラまたはコントロールパネルのいずれかを使用して mbam を手動でアンインストールしてから、mbam 2.0 インフラストラクチャをインストールします。 データベースを削除する必要はありません。 MBAM 1.0 サーバーをアンインストールすると、MBAM データベースはそのまま残ります。 MBAM 1.0 で使用されていたものと同じデータベースを指定した場合、MBAM 2.0 のインストールでは、データベース内の MBAM 1.0 データは保持され、MBAM 2.0 で動作するようにデータベースが変換されます。

-   **分散クライアントアップグレード**-スタンドアロンの mbam トポロジを使用している場合は、mbam 2.0 サーバーインフラストラクチャをインストールした後に、Mbam クライアントを段階的にアップグレードできます。 MBAM 2.0 サーバーによって、既存のクライアントのバージョンが検出され、2.0 クライアントにアップグレードするために必要な手順が実行されます。

    Mbam 2.0 サーバーインフラストラクチャをアップグレードした後、MBAM 1.0 クライアントは、escrowing の回復データを正常に2.0 報告し続けますが、コンプライアンスは MBAM 1.0 のポリシーに基づいています。 クライアントコンピューターで MBAM 2.0 ポリシーに準拠したコンプライアンスを正確に報告するには、クライアントを MBAM 2.0 にアップグレードする必要があります。 クライアントは、以前のクライアントをアンインストールせずに MBAM 2.0 クライアントにアップグレードできます。クライアントは、MBAM 2.0 ポリシーの適用と報告を開始します。

    MBAM を Configuration Manager で使用している場合は、MBAM 1.0 クライアントを MBAM 2.0 にアップグレードする必要があります。

## 2 Server アーキテクチャから MBAM をアップグレードする


次の手順を使用して、以前のバージョンの MBAM からアップグレードします。これは、1つのサーバーが Microsoft SQL Server コンポーネントをホストしていて、もう一方のサーバーが web サイトとサービスをホストしている場合です。

**2 server アーキテクチャから MBAM をアップグレードするには**

1.  SQL Server 機能があるサーバーで、[コントロールパネル] の [**プログラムと機能**] を選択し、[ **Microsoft BitLocker の管理と監視**] をアンインストールします。 回復データベースとコンプライアンスおよび監査データベースは変更されません。

2.  バージョン MBAM 2.0 の**MBAMSetup.exe**を実行します。必要に応じて、**カスタマーエクスペリエンス向上プログラム**を選択し、[**開始**] をクリックします。

3.  Microsoft ソフトウェアライセンス条項を読んで同意し、[**次へ**] をクリックしてインストールを続行します。

4.  [**トポロジの選択**] ページで、**スタンドアロン**または**System Center Configuration Manager 統合**トポロジを選択し、[**次へ**] をクリックします。

5.  [**インストールする機能の選択**] ページで、[**セルフサービスサーバー** ] および [**管理と監視**] のサーバー機能をオフにし、[**次へ**] をクリックします。

6.  前提条件チェックが終了するまで待ち、[**次へ**] をクリックします。 見つからない前提条件が検出された場合は、不足している前提条件を解決し、[**前提条件の確認] をもう一度**クリックします。

7.  [ **MBAM データベースへのアクセスに使用するアカウントを指定**してください] ページで、サイトとサービスをホストするサーバーのコンピューター名を入力し、[**次へ**] をクリックします。

8.  [**回復データベースの構成**] ページで、SQL Server インスタンス名と、回復データを格納するデータベースの名前を指定します。 また、データベースファイルとログ情報を配置する場所も指定する必要があります。

9.  **[Next]** をクリックして続行します。

10. [**コンプライアンスと監査データベースの構成**] ページで、SQL Server インスタンスの名前と、コンプライアンスおよび監査データを格納するデータベースの名前を指定します。

11. **[Next]** をクリックして続行します。

12. [**コンプライアンスおよび監査レポートの構成**] ページで、コンプライアンスと監査レポートをインストールする SQL Server Reporting Services インスタンスを指定し、ドメインユーザーアカウントとパスワードを入力して、コンプライアンスと監査データベースにアクセスします。 有効期限が切れないように、このアカウントのパスワードを設定します。 ユーザーアカウントは、MBAM Reports Users グループで利用可能なすべてのデータにアクセスできます。

13. **[Next]** をクリックして続行します。

14. コンピューターのセキュリティを維持するために Microsoft Update を使用するかどうかを指定し、[**次へ**] をクリックします。 これにより、Windows で自動更新が有効になりません。 この製品または別の製品の Microsoft Update を以前に使用することを選択した場合、Microsoft Update ページは表示されません。

15. [**インストールの概要**] ページで、インストールされる機能を確認してから、[**インストール**] をクリックしてインストールを開始します。

**管理と監視のサーバー機能をアンインストールして、アップグレードを完了するには**

1.  管理と監視のサーバー機能をホストしているコンピューターで、[コントロールパネル] の [**プログラムと機能**] を選択し、mbam をアンインストールして、以前にインストールされた web サイトとサービスを削除します。

2.  バージョン2.0 の**MBAMSetup.exe**を実行します。必要に応じて、**カスタマーエクスペリエンス向上プログラム**を選択し、[**開始**] をクリックします。

3.  Microsoft ソフトウェアライセンス条項を読んで同意し、[**次へ**] をクリックしてインストールを続行します。

4.  [**トポロジの選択**] ページで、**スタンドアロン**または**System Center Configuration Manager 統合**トポロジを選択し、[**次へ**] をクリックします。

5.  [**インストールする機能の選択**] ページで、[**回復データベース**] と [**コンプライアンスと監査のデータベース**および監査**レポート**の機能] をオフにし、[**次へ**] をクリックします。

6.  前提条件チェックが終了するまで待ち、[**次へ**] をクリックします。 見つからない前提条件が検出された場合は、最初に不足している前提条件を解決し、[**前提条件の確認] をもう一度**クリックします。

7.  [**ネットワーク通信セキュリティの構成**] ページで、web サイトとサービスに Secure Socket LAYER (SSL) 暗号化を使用するかどうかを選択します。 通信を暗号化することにした場合は、暗号化に使用する証明機関 (CA) 証明書を選択します。

    **注** この手順を実行する前に証明書を作成して、このページで選択できるようにする必要があります。

     

8.  [**コンプライアンスステータスデータベースの場所の構成**] ページで、SQL Server インスタンスの名前と、コンプライアンスおよび監査データを格納するデータベースの名前を指定します。 また、データベースファイルとログ情報を配置する場所も指定する必要があります。

9.  **[Next]** をクリックして続行します。

10. [**回復データベースの場所の構成**] ページで、SQL Server インスタンスの名前と回復データを格納するデータベースの名前を指定します。

11. **[Next]** をクリックして続行します。

12. [**コンプライアンスおよび監査レポートの構成**] ページで、別のサーバーに構成したレポートインスタンスの URL を入力します。 [**テスト**] ボタンを使用して、サイトに到達できることを確認します。

13. **[Next]** をクリックして続行します。

14. [**セルフサービスポータルの構成**] ページで、セルフサービスポータルのポート番号、ホスト名、仮想ディレクトリ名、インストールパスを入力します。

    **注** 一意のホストヘッダー名を指定しない限り、指定したポート番号は、管理および監視サーバーで未使用のポート番号である必要があります。

     

15. [**管理と監視サーバーの構成**] ページで、ヘルプデスクの web サイトに必要な仮想ディレクトリを指定します。

16. コンピューターのセキュリティを維持するために Microsoft Update を使用するかどうかを指定し、[**次へ**] をクリックします。 この手順では、Windows で自動更新が有効になっていません。 この製品または別の製品の Microsoft Update を以前に使用することを選択した場合、Microsoft Update ページは表示されません。

17. [**インストールの概要**] ページで、インストールされる機能を確認してから、[**インストール**] をクリックしてインストールを開始します。

18. アップグレードが成功したことを確認するには、ドメイン内の別のコンピューターから各サイトにアクセスできることを確認します。

## エンドユーザーのコンピューター上の MBAM クライアントのアップグレード


エンドユーザーコンピューターを MBAM 2.0 クライアントにアップグレードするには、各クライアントコンピューターで**MbamClientSetup.exe**を実行します。 インストーラーは、クライアントを MBAM 2.0 クライアントに自動的に更新します。 MBAM クライアントは、電子ソフトウェア配布システム (Active Directory Domain Services または System Center Configuration Manager などのツール) を使用してインストールできます。

クライアントのアップグレードを検証するには、次の操作を行います。

1.  構成済みのレポートサイクルが終了するまで待ち、SQL server コンピューターで**Sql Server Management Studio**を起動します。

2.  SQL Server コンピューターで、 **Sql Server Management Studio**を起動します。

3.  [ **Recoveryandmachines (マシン**名) テーブルに、エンドユーザーのコンピューター名を示す行が含まれていることを確認します。

## 関連トピック


[MBAM 2.0 の展開](deploying-mbam-20-mbam-2.md)

 

 





