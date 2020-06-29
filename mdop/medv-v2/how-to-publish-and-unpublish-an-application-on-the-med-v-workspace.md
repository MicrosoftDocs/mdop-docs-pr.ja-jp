---
title: MED-V ワークスペースでアプリケーションを公開および公開を取り消す方法
description: MED-V ワークスペースでアプリケーションを公開および公開を取り消す方法
author: dansimp
ms.assetid: fd5a62e9-0577-44d2-ae17-61c0aef78ce8
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: cc8f9579d800aa0e5da0d67e0cd71bcae5e912a0
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10826924"
---
# MED-V ワークスペースでアプリケーションを公開および公開を取り消す方法


アプリケーションが MED-V ワークスペースにインストールされている場合でも、エンドユーザーがアプリを利用できるようになるには、アプリケーションを公開することが必要になる場合もあります。 既定では、ほとんどのアプリケーションはインストール時に公開され、ショートカットが作成されて有効になります。

場合によっては、アプリケーションをエンドユーザー (ウイルススキャンソフトウェアなど) で利用できるようにすることなく、MED-V ワークスペースにアプリケーションをインストールすることができます。 同様に、以前はエンドユーザーが利用できなかった MED-V ワークスペースにインストールされているアプリケーションを公開することが必要になる場合もあります。 たとえば、インストールによって [**スタート**] メニューにショートカットが自動的に作成されない場合は、インストールされているアプリケーションを公開しなければならない場合があります。

**重要** UNC パスをサポートしていないアプリケーションを公開する場合は、そのアプリケーションをドライブにマップすることをお勧めします。

 

次のいずれかのタスクを実行することによって、展開された MED-V ワークスペースにアプリケーションを公開または非公開にすることができます。

**インストールされているアプリケーションを公開する、または発行を取り消すには**

1.  展開された MED-V ワークスペースでアプリケーションを公開するには、そのアプリケーションのショートカットを仮想マシン上の次のフォルダーにコピーします。

    C:\\Documents と Settings\\All Users\\Start メニュー

    必要に応じて、グループポリシーまたは ESD システムを使って、そのアプリケーションのショートカットを [すべての Users\\Start] メニューフォルダーにコピーするスクリプトを展開します。

2.  展開された MED-V ワークスペースでアプリケーションの発行を取り消すには、仮想マシン上の次のフォルダーからそのアプリケーションのショートカットを削除します。

    C:\\Documents と Settings\\All Users\\Start メニュー

    必要な場合は、グループポリシーまたは ESD システムを使用して、[すべての Users\\Start] メニューフォルダーからそのアプリケーションのショートカットを削除するスクリプトを展開します。

    **注** 多くの場合、アプリケーションをアンインストールすると、ホストコンピューターの [**スタート**] メニューからショートカットが自動的に削除されます。 ただし、共有コンピューターのすべてのユーザーに対して構成されている MED-V ワークスペースなど、場合によっては、アプリケーションをアンインストールした後に、**スタート**メニューのショートカットを手動で削除する必要がある場合があります。 エンドユーザーは、ショートカットを右クリックして [**削除**] を選ぶことで、これを行うことができます。

     

アプリケーションが公開されていること、または未公開であることをテストするには、MED-V ワークスペースで対応するショートカットが使用可能かどうかを確認します。

**注** Windows XP SP3 に含まれていて、仮想マシンの [スタート] メニューフォルダーに配置されているアプリケーションは、ホストに自動的には公開されません。 自動発行をブロックするレジストリ設定によって制御されます。 詳細については、「 [Windows 仮想 PC アプリケーションの除外リスト](windows-virtual-pc-application-exclude-list.md)」を参照してください。

 

**コントロールパネルの項目を公開するには**

1.  ターゲットが、C:\\WINDOWS\\system32\\appwiz.cpl などの項目の名前である仮想マシンにショートカットを作成します。

    ショートカットは、"%ALLUSERSPROFILE%\\Start Menu\\" フォルダーまたはそのサブフォルダーのいずれかに作成または移動する必要があります。

    ホストコンピューターには、ホストのスタートメニューフォルダー内の対応する場所にアイテムが公開されます。

2.  ホストのアイテムのショートカットを開始します。

**注意** ショートカットを作成する場合は、% SystemRoot% \\control.exe を指定しないでください。 このアプリケーションは、自動発行をブロックするレジストリ設定に含まれているため、公開されません。

 

**MED-V でアプリケーションの自動発行を処理する方法**

1.  アプリケーションの発行中、MED-V はゲスト仮想マシンからホストコンピューターにショートカットをコピーします。ゲストのフォルダー階層と一致させます。 これにより、MED-V は次の手順に従ってゲストからホストへのショートカットをコピーします。

    1.  MED-V は、ショートカットが存在するゲストのフォルダーと同じ名前のホストコンピューターで、[スタートメニュー] の下にあるフォルダーを見つけようとします。

    2.  一致するフォルダーがない場合、MED-V は、ショートカットが存在するゲストのフォルダーと同じ名前の、ホストのスタートメニューフォルダー内のフォルダーを見つけようとします。

    3.  一致するフォルダーがない場合、MED-V は、ホスト上の既定のフォルダーのショートカットをコピーします。 [スタートメニュー] \\ [プログラム] フォルダーを選びます。

2.  アプリケーション公開プロセスの例:

    1.  アプリケーションのショートカットがゲストの Start Menu\\Programs\\AppShortcuts フォルダーに公開されている場合、MED-V はホストコンピューターで Start Menu\\Programs\\ AppShortcuts フォルダーを探し、見つかった場合は、そのフォルダーへのショートカットをコピーします。

    2.  フォルダーが見つからない場合、MED-V はホストコンピューターで [スタートメニュー] ¥ [appshortcut] フォルダーを探し、見つかった場合はそのフォルダーへのショートカットをコピーします。

    3.  フォルダーが見つからない場合は、MED によって [スタートメニュー] ¥ [プログラム] フォルダーにショートカットがコピーされます。

**注** ショートカットをコピーするには、MED-V のホストコンピューターのスタートメニューフォルダーにフォルダーが既に存在している必要があります。 MED-V はまだ存在しない場合はフォルダーを作成しません。

 

## 関連トピック


[MED-V ワークスペースでのアプリケーションのインストールと削除](installing-and-removing-an-application-on-the-med-v-workspace.md)

[MED-V ワークスペースのソフトウェア更新プログラムの管理](managing-software-updates-for-med-v-workspaces.md)

[Windows Virtual PC アプリケーションの除外一覧](windows-virtual-pc-application-exclude-list.md)

 

 




