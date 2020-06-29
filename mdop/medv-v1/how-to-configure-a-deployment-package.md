---
title: 展開パッケージを構成する方法
description: 展開パッケージを構成する方法
author: dansimp
ms.assetid: 748272a1-6af2-476e-a3f1-87435b8e94b1
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: aba5e91a4da92f9e51a5ccc70502658ae724d76f
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10825947"
---
# 展開パッケージを構成する方法


パッケージウィザードでは、ローカルコンピューター上にフォルダーを作成し、必要なすべてのインストールファイルを1つのフォルダーに転送することによって、パッケージの作成方法を説明します。 このフォルダーの内容は、配布用に複数のリムーバブルメディアドライブに移動できます。

**注**  
1つのパッケージに、x86 システムと x64 システムの両方のインストールファイルを含めることはできません。



## 展開パッケージを作成する方法


**展開パッケージを作成するには**

1. 少なくとも1つのローカルパックイメージを作成した**Images**モジュールで確認します。

2. [**ツール**] メニューの [**パッケージウィザード**] をクリックします。

3. **パッケージウィザード**の [ようこそ] ページで、[**次へ**] をクリックします。

4. [**ワークスペースイメージ**] ページで、[**パッケージに画像を含める**] チェックボックスをオンにして、パッケージに画像を追加します。

   [**画像**] フィールドが有効になっています。

   **注**  
   イメージは、MED-V パッケージでは必要ありません。パッケージはイメージなしで作成することができます。 このような場合は、後でネットワーク経由でクライアントにダウンロードしたり、イメージの事前ステージフォルダーにプッシュしたりできるように、画像をサーバーにアップロードする必要があります。



5. **画像**リストをクリックして、利用可能なすべての画像を表示します。 パッケージにコピーする画像を選びます。 [**更新**] をクリックすると、使用可能な画像の一覧が更新されます。

6. **[次へ]** をクリックします。

7. [ **Med-v のインストール設定**] ページで、次のいずれかの操作を行って、med-v インストールファイルを選びます。

   -   [ **Med-v インストールファイル**] フィールドに、インストールファイルが保存されているディレクトリへのフルパスを入力します。

   -   [ **...** ] をクリックして、インストールファイルが配置されているディレクトリを参照します。

   **注**  
   このフィールドは必須であり、有効なファイル名がないとウィザードは続行されません。



8. [**サーバーアドレス**] フィールドに、サーバー名または IP アドレスを入力します。

9. [**サーバーポート**] フィールドにサーバーのポートを入力します。

10. サーバーへの接続に https 接続を要求するには、[**サーバーにアクセス**します] チェックボックスをオンにします。

11. 次のいずれかの操作を行います。

    -   [**既定のインストール設定**] をクリックして、[**次へ**] をクリックし、既定の設定のままにします。

    -   [**カスタムインストール設定**] をクリックし、[**次**へ] をクリックしてインストール設定をカスタマイズします。

        1.  [ **Med-v のインストールカスタム設定**] ページにある [**インストールフォルダー** ] フィールドに、ホストコンピューター上の med-v ファイルがインストールされるフォルダーのパスを入力します。

            **注**  
            定数ではなく、パスの変数を使うことをお勧めします。これは、コンピューターによって異なる可能性があります。

            たとえば、 *c:\\MED-V*の代わりに *%ProgramFiles%\\MED-V*を使います。



    ~~~
    2.  In the **Virtual machines images folder** field, type the path of the folder where the virtual images files will be installed on the host computer.

        **Note**  
        If you are using image pre-staging, this is the image pre-stage folder where the image is located.



    3.  In the **Minimal required RAM** field, enter the RAM required to install a MED-V package. If the user installing the MED-V package does not have the minimal required RAM, the installation will fail.

    4.  Select the **Install the MED-V management application** check box to include the MED-V management console application in the installation.

    5.  Select the **Create a shortcut to MED-V on the desktop** check box to create a shortcut to MED-V on the host's desktop.

    6.  Select the **Start automatically on computer startup** check box to start MED-V automatically on startup.

    7.  Click **Next**.
    ~~~

12. [**追加のインストール**] ページで、[仮想**化ソフトウェアのインストールを含める**] チェックボックスをオンにして、パッケージに仮想 PC のインストールを含めます。

    [**インストールファイル**] フィールドが有効になっています。 仮想化ソフトウェアのインストールファイルの完全なパスを入力するか、[ **...** ] をクリックしてディレクトリを参照します。

13. [ **VIRTUAL PC QFE のインストールを含める**] チェックボックスをオンにして、仮想 pc の更新プログラムのインストールをパッケージに含めます。

    [**インストールファイル**] フィールドが有効になっています。 仮想 PC 更新プログラムのインストールファイルの完全なパスを入力するか **、[...]** をクリックしてディレクトリを参照します。

14. [ **Microsoft .Net framework 2.0 のインストールを含める**] チェックボックスをオンにして、パッケージに Microsoft .net framework 2.0 インストールを含めます。

    [**インストールファイル**] フィールドが有効になっています。 Microsoft .NET Framework 2.0 インストールファイルの完全なパスを入力するか、[ **...** ] をクリックしてディレクトリを参照します。

15. **[次へ]** をクリックします。

16. [**完了**] ページで、次のいずれかの操作を行って、パッケージを保存する場所を選びます。

    -   [**パッケージの宛先**] フィールドに、パッケージを保存するディレクトリの完全なパスを入力します。

    -   [ **...** ] をクリックして、インストールファイルが保存されるディレクトリを参照します。

    **注**  
    パッケージをビルドすると、実際のパッケージサイズよりも多くの領域が消費される場合があります。 このため、ハードドライブにパッケージを作成することをお勧めします。 パッケージを作成したら、USB にコピーできます。



17. [**パッケージ名**] フィールドに、パッケージの名前を入力します。

18. [**完了**] をクリックして、パッケージを作成します。

    パッケージが作成されます。 数分かかる場合があります。

    パッケージが作成されると、正常に完了したことを通知するメッセージが表示されます。

**注**  
リムーバブルメディアに直接ではなく、すべてのファイルをローカルで保存した場合は、フォルダー自体ではなく、フォルダー自体をコピーして、リムーバブルメディアにコピーしてください。



**注**  
リムーバブルメディアは、パッケージのコンテンツが、リムーバブルメディアのメモリの3分の1しか消費しないように、十分な大きさである必要があります。



**注**  
パッケージを作成するときに、ビルドが完了したときに、実際のパッケージサイズの最大2倍のサイズが必要になることがあります。



## 関連トピック


[MED-V イメージの作成](creating-a-med-v-image.md)








