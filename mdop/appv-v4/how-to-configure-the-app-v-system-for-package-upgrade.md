---
title: App-V システムをパッケージのアップグレード用に構成する方法
description: App-V システムをパッケージのアップグレード用に構成する方法
author: dansimp
ms.assetid: de133898-f887-46c1-9bc9-fbb03feac66a
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 5e5056f923c61aff39d9bd6e1d26f071177f7c12
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10817847"
---
# App-V システムをパッケージのアップグレード用に構成する方法


App-v Sequencer でアップグレードされた既存のアプリケーションパッケージの新しいバージョンを展開すると、アプリの V クライアントが自動的に新しいバージョンをローカルキャッシュにストリーミングできるように、アプリを展開することができます。 使用しているストリーミングソリューションに応じて、パッケージのアップグレードを構成するためのさまざまな手順があります。 以下のセクションでは、発行とストリーミングの最も一般的なシナリオについて説明し、各シナリオでパッケージのアップグレードを構成するために必要な手順を示します。

## パブリッシングとストリーミングの両方で管理サーバーを使用する


このシナリオでは、パッケージとアプリケーションの発行とストリーミングの両方に1つの App-v 管理サーバーが使用され、RTSP (S) プロトコルが必要です。 元のパッケージが App-v 管理サーバーにインポートされると、管理者は、sequencer によって作成されたファイルを含むパッケージフォルダーをコンテンツフォルダー (たとえば、\\\\server\\CONTENT\\packagename.) にコピーします。 また、管理者は、パッケージフォルダーの SFT ファイルをポイントするように OSD ファイルの HREF エントリを編集し、そのパッケージをサーバーにインポートします。

ユーザーが管理サーバーによって認証されると、サーバーはクライアントに applist.xml ファイルを送信してユーザーのアプリケーションを公開します。 次に、クライアントは、管理サーバーからアプリケーションの OSD ファイルとアイコンを取得します。 ユーザーがアプリケーションアイコンをダブルクリックすると、アプリケーションコンテンツは、OSD ファイルで指定されたパスからクライアントキャッシュにストリーミングされ、アプリケーションが開始されます。

### パッケージをアップグレードするには

App-v Sequencer でアップグレードされたアプリケーションの新しいバージョンを追加するには、管理者は、新しい SFT ファイルとその他の変更されたファイルを元のバージョンのアプリケーションと同じフォルダーにコピーする必要があります。 次に、管理者は、サーバー管理コンソールで [**バージョンの追加**] を使用して、新しいバージョンのパッケージを追加します。

ユーザーが次にアプリケーションを起動すると、サーバーはクライアントに対して自動的に新しいバージョンをストリームします。 このパッケージのアップグレードの具体的な方法は、以前はアクティブなアップグレードと呼ばれていました。

## 管理サーバーを公開用に使用し、ストリーミングをストリーミングサーバーで行う


このシナリオでは、App-v Management Server を使ってパッケージを公開し、ストリーミングサーバーをストリーミングパッケージとアプリケーションに使用します。 RTSP (S) プロトコルが必要です。 管理サーバーに元のパッケージがインポートされると、管理者は、sequencer によって作成されたファイルを含むパッケージフォルダーをコンテンツフォルダー (たとえば、\\\\server\\CONTENT\\packagename.) にコピーします。 管理者が、ストリーミングサーバー上の SFT ファイルをポイントするように OSD ファイル内の HREF エントリを編集し、そのパッケージを管理サーバーにインポートします。

ストリーミングサーバーをセットアップするには、管理サーバーからストリーミングサーバー上のコンテンツフォルダーにパッケージフォルダーをコピーします。 このフォルダーの名前と相対パスは、管理サーバー上のストリーミングサーバーのコンテンツフォルダーの下にある必要があります。たとえば、\\\\streamingserver\\CONTENT\\packagename.

クライアントのアプリケーションソースルート (ASR) 設定がストリーミングサーバーを指すように構成されている場合、クライアントは OSD ファイルの HREF エントリで、サーバー名の代わりにこの設定を使います。 クライアント上の ISR フィールドと OSR フィールドは、必要に応じて、使用されている特定のシステムアーキテクチャに応じて、管理サーバーまたはストリーミングサーバーのいずれかを指すように構成することができます。

ユーザーが管理サーバーによって認証されると、サーバーはクライアントに applist.xml ファイルを送信してユーザーのアプリケーションを公開します。 クライアントは、OSR と ISR のフィールドの設定に応じて、ストリーミングサーバーまたは管理サーバーからアプリケーションの OSD ファイルとアイコンを取得します。

ユーザーがアプリケーションアイコンをダブルクリックすると、クライアントは OSD ファイル HREF 要素に含まれているパッケージコンテンツファイル (SFT) へのパスを使用します。 ASR が使われている場合、クライアントは、ASR に指定されているストリーミングサーバーへのパスを含む HREF 要素のサーバー名 (および使用されている場合は、ポートとプロトコル) を置き換えます。 その後、アプリケーションはストリーミングサーバーからクライアントキャッシュにストリーミングされ、開始されます。

### パッケージをアップグレードするには

App-v Sequencer でアップグレードされたアプリケーションの新しいバージョンを追加するには、管理者は、新しいバージョンの SFT ファイルとその他の変更されたファイルを、ストリーミングサーバー上の元のバージョンのアプリケーションと同じフォルダーにコピーする必要があります。

一貫性を保つため、管理サーバー上のフォルダーにも新しいファイルをコピーすることをお勧めします。 特に、クライアントの OSR または ISR のフィールドを使用する場合は、更新された OSD ファイルとアイコンを OSR と ISR の各フィールドに指定されているサーバーにコピーします。

ストリーミングサーバーによって新しいバージョンが検出されると、次回ユーザーがアプリケーションを起動したときに、サーバーはクライアントに自動的に新しいバージョンをストリームします。

## 管理サーバーを公開用に使用し、ストリーミング用に IIS サーバーを使用する


このシナリオでは、App-v Management Server を使ってパッケージを公開し、IIS サーバーを使ってストリーミングパッケージとアプリケーションを使用します。 管理サーバーに元のパッケージがインポートされると、管理者は、sequencer によって作成されたファイルを含むパッケージフォルダーをコンテンツフォルダー (たとえば、\\\\server\\CONTENT\\packagename.) にコピーします。 管理者が、IIS サーバー上の SFT ファイルをポイントするように OSD ファイル内の HREF エントリを編集し、そのパッケージを管理サーバーにインポートします。

ストリーミング用に IIS サーバーを設定するために、管理者は、パッケージフォルダーを管理サーバーから IIS サーバーのコンテンツフォルダーにコピーします。 このフォルダーの名前と相対パスは、管理サーバー上の IIS サーバーの Web コンテンツフォルダーと同じである必要があります。たとえば、IIS サーバーの URL には、またはを使用してアクセスでき http://IISserver/CONTENT/packagename https://IISserver/CONTENT/packagename ます。

クライアントのアプリケーションソースルート (ASR) 設定が、IIS サーバーを指すように構成されている場合、クライアントは OSD ファイルの HREF エントリでサーバー名の代わりに ASR を使用します。 必要に応じて、使用している特定のシステムアーキテクチャに応じて、管理サーバーまたは IIS サーバーを指すようにクライアントの ISR フィールドと OSR フィールドを構成することができます。

管理サーバーがユーザーを認証すると、サーバーは applist.xml ファイルをクライアントに送信して、ユーザーのアプリケーションを公開します。 クライアントは、ISR フィールドと OSR フィールドの設定に応じて、IIS サーバーまたは管理サーバーからアプリケーションの OSD ファイルとアイコンを取得します。

ユーザーがアプリケーションアイコンをダブルクリックすると、クライアントは OSD ファイル HREF 要素に含まれているパッケージコンテンツファイル (SFT) へのパスを使用します。 ASR が使われている場合、クライアントは、ASR に指定されている IIS サーバーへのパスを使用して、HREF 要素にサーバー名 (および使用されている場合は、ポートとプロトコル) を置き換えます。 次に、アプリケーションは、HTTP (S) プロトコルを使って、IIS サーバーからクライアントキャッシュにストリーミングされ、開始されます。

### パッケージをアップグレードするには

パッケージをアップグレードする手順は次のとおりです。

-   新しいバージョンの OSD ファイルを、管理サーバーのコンテンツフォルダーの下にある元のバージョンのフォルダー (\\\\server\\CONTENT\\packagename など) にコピーして、既存の OSD ファイルを置き換えます。 整合性を保つには、他の変更されたファイルもコピーします。 クライアントの OSR または ISR のフィールドが使用されている場合は、更新された OSD ファイルとアイコンを、OSR フィールドと ISR フィールドで指定されているサーバーにコピーすることもできます。

-   新しいバージョンの SFT ファイルを、IIS サーバー上の Web コンテンツフォルダーの下にあるパッケージフォルダーにコピーします。たとえば、IIS サーバーの URL には、またはを使用してアクセスでき http://IISserver/CONTENT/packagename https://IISserver/CONTENT/packagename ます。

次の公開の更新時に、クライアントは新しいバージョンの OSD ファイルで更新されます。 これで、このファイルは新しいバージョンの SFT ファイルを指します。そのため、ユーザーが次にアプリケーションアイコンをダブルクリックすると、新しいバージョンが開始されます。

## 管理サーバーを公開用に使用し、ストリーミング用にファイル共有を使用する


このシナリオでは、App-v Management Server を使ってパッケージを公開し、ファイルサーバーをストリーミングパッケージとアプリケーションに使用します。 管理サーバーに元のパッケージがインポートされると、管理者は、sequencer によって作成されたファイルを含むパッケージフォルダーをコンテンツフォルダー (たとえば、\\\\server\\CONTENT\\packagename.) にコピーします。 管理者は、ファイルサーバー上の SFT ファイルをポイントするように、OSD ファイルの HREF エントリを編集して、パッケージを管理サーバーにインポートします。

ストリーミング用にファイルサーバーをセットアップするには、管理者がパッケージフォルダーを管理サーバーからファイルサーバー上のコンテンツフォルダーにコピーします。 このフォルダーは、管理サーバー上のファイルサーバーのコンテンツフォルダーの下に、たとえば \\\\fileserver\\CONTENT\\packagename. のような名前と相対パスを持っている必要があります。

\\\\Fileserver\\content などの UNC パスを使用してファイルサーバーを指すようにクライアントのアプリケーションソースルート (ASR) 設定が構成されている場合、クライアントは、OSD ファイルの HREF エントリで、サーバー名の代わりにこの設定を使います。 必要に応じて、管理者は、使用されている特定のシステムアーキテクチャに応じて、管理サーバーまたはファイルサーバーのいずれかを指すようにクライアントの ISR フィールドと OSR フィールドを構成することができます。

管理サーバーがユーザーを認証すると、サーバーは applist.xml ファイルをクライアントに送信して、ユーザーのアプリケーションを公開します。 クライアントは、ISR フィールドと OSR フィールドの設定に応じて、ファイルサーバーまたは管理サーバーからアプリケーションの OSD ファイルとアイコンを取得します。

ユーザーがアプリケーションアイコンをダブルクリックすると、クライアントは OSD ファイル HREF 要素に含まれているパッケージコンテンツファイル (SFT) へのパスを使用します。 ASR が使われている場合、クライアントは、ASR 要素のサーバー名 (および使用されている場合は、ポートとプロトコル) を、ASR で指定されたファイルサーバーへのパスと置き換えます。 その後、アプリケーションはファイルサーバーからクライアントキャッシュにストリーミングされ、開始されます。

### パッケージをアップグレードするには

パッケージをアップグレードする手順は次のとおりです。

-   新しいバージョンの OSD ファイルを、管理サーバーのコンテンツフォルダーの下にある元のバージョンのフォルダー (\\\\server\\CONTENT\\packagename など) にコピーして、既存の OSD ファイルを置き換えます。 その他の変更されたファイルも、一貫性を維持するためにコピーする必要があります。 クライアントの OSR または ISR のフィールドが使用されている場合は、更新された OSD ファイルとアイコンを、OSR フィールドと ISR フィールドで指定されているサーバーにコピーすることもできます。

-   新しいバージョンの SFT ファイルを、ファイルサーバー上のコンテンツフォルダーの下にあるパッケージフォルダー (\\\\fileserver\\CONTENT\\packagename. など) にコピーします。 \\\\Fileserver\\CONTENT\\packagename\\V1. などのファイルサーバー上のコンテンツ共有の下のフォルダーに、"SFT" ファイルをコピーします。

次の公開時に、クライアントが新しいバージョンの OSD ファイルで更新されます。 このファイルは、新しいバージョンの SFT ファイルを指すようになりました。そのため、ユーザーが次にアプリケーションアイコンをダブルクリックすると、新しいバージョンが開始されます。

## MSI ストリーミングモードを使用したパッケージのアップグレード


パッケージのシーケンス処理中に Windows Installer (MSI) ファイルを生成すると、sequencer によってが作成されます。必要なすべての公開情報が含まれている MSI ファイル。 管理者は、をコピーする必要があります。MSI ファイルをクライアントとに保存します。クライアントコンピューターがアクセスできるネットワーク共有にパッケージコンテンツを含む SFT ファイル。

クライアントにアプリケーションを公開するには、クライアントコンピューターで次のコマンドを実行します。

   **Msiexec.exe/i \\\\PathToMsi\\packagename.msi モード = ストリーミング OVERRIDEURL = \\ ¥¥¥ (ドメイン \\ パッケージ)**

、.MSI ファイルは、クライアントにアプリケーションを発行して、をストリームします。SFT ファイルをクライアントキャッシュに保存します。

### パッケージをアップグレードするには

新しいバージョンを追加するには、管理者が新しいを展開する必要があります。MSI ファイルをクライアントに追加して、新しいを作成します。SFT ファイルをネットワーク共有に保存します。 次に、管理者は、パッケージの展開に使用したのと同じコマンドを実行しますが、新しいを使用する必要があります。MSI ファイルと新しいSFT ファイルの例:

   **Msiexec.exe/i \\\\PathToMsi\\packagename\_2.msi モード = ストリーミング OVERRIDEURL = ¥¥¥¥¥¥¥ (パッケージ)**

 

 





