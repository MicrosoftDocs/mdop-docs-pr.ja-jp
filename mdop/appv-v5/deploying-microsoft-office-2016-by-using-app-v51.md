---
title: APP-V を使用した Microsoft Office 2016 の展開
description: APP-V を使用した Microsoft Office 2016 の展開
author: dansimp
ms.assetid: e0f4876-da99-4b89-977e-2fb6e89ea3d3
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 04/19/2017
ms.openlocfilehash: b47fd46c8dc368bbce819b24f18fa30328fbbaf0
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "10814610"
---
# APP-V を使用した Microsoft Office 2016 の展開


この記事の情報は、Microsoft Application Virtualization (App-v) 5.1 以降のバージョンを使用して、Microsoft Office 2016 を仮想化されたアプリケーションとして組織内のコンピューターに配信するために使用します。 Office 2013 を提供するために app-v を使用する方法については、「 [App-v を使用して Microsoft Office 2013 を展開](deploying-microsoft-office-2013-by-using-app-v51.md)する」を参照してください。 Office 2010 を提供するために app-v を使用する方法については、「 [App-v を使用して Microsoft Office 2010 を展開](deploying-microsoft-office-2010-by-using-app-v51.md)する」を参照してください。

ここでは、以下のトピックについて説明します。

-   [始める前に知っておくべきこと](#bkmk-before-you-start)

-   [Office 展開ツールを使用して、App-v 用の Office 2016 パッケージを作成する](#bkmk-create-office-pkg)

-   [Office パッケージを App-v で公開する-V 5.1](#bkmk-pub-pkg-office)

-   [Office App-v パッケージのカスタマイズと管理](#bkmk-custmz-manage-office-pkgs)

## <a href="" id="bkmk-before-you-start"></a>始める前に知っておくべきこと


App-v を使用して Office 2016 を展開する前に、次の計画情報を確認してください。

### <a href="" id="bkmk-supp-vers-coexist"></a>サポートされている Office のバージョンと Office の共存

次の表を使用して、サポートされているバージョンの Office と、共存バージョンの Office の実行に関する情報を取得します。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">レビューする情報</th>
<th align="left">説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="planning-for-using-app-v-with-office.md#bkmk-office-vers-supp-appv" data-raw-source="[Supported versions of Microsoft Office](planning-for-using-app-v-with-office.md#bkmk-office-vers-supp-appv)">サポートされている Microsoft Office のバージョン</a></p></td>
<td align="left"><ul>
<li><p>サポートされている Office のバージョン</p></li>
<li><p>サポートされている展開の種類 (デスクトップ、個人用仮想デスクトップインフラストラクチャ (VDI)、プールされた VDI)</p></li>
<li><p>Office のライセンスオプション</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p><a href="planning-for-using-app-v-with-office.md#bkmk-plan-coexisting" data-raw-source="[Planning for Using App-V with coexisting versions of Office](planning-for-using-app-v-with-office.md#bkmk-plan-coexisting)">共存バージョンの Office での App-v の使用を計画する</a></p></td>
<td align="left"><p>異なるバージョンの Office を同じコンピューターにインストールする場合の考慮事項</p></td>
</tr>
</tbody>
</table>



### <a href="" id="bkmk-pkg-pub-reqs"></a>パッケージ化、発行、展開の要件

App-v を使用して Office を展開する前に、次の要件を確認してください。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">タスク</th>
<th align="left">要件</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>パッケージ化</p></td>
<td align="left">
<ul>
<li><p>ユーザーに展開するすべての Office アプリケーションが1つのパッケージに含まれている必要があります。</p></li>
<li><p>App-v 5.1 以降では、Office 展開ツールを使用してパッケージを作成する必要があります。 Sequencer は使用できません。</p></li>
<li><p>Microsoft Visio 2016 と Microsoft Project 2016 を Office と共に展開する場合は、それらを Office と同じパッケージに含める必要があります。 詳細については、「 <a href="#bkmk-deploy-visio-project" data-raw-source="[Deploying Visio 2016 and Project 2016 with Office](#bkmk-deploy-visio-project)"> Visio 2016 および Project 2016 を Office と共に展開する」を参照してください </a> 。</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p>Publishing</p></td>
<td align="left"><ul>
<li><p>各クライアントコンピューターには、1つの Office パッケージのみを公開できます。</p></li>
<li><p>Office パッケージをグローバルに公開する必要があります。 ユーザーに公開することはできません。</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p>次の製品を共有コンピューターに展開する (たとえば、リモートデスクトップサービスを使用する)。</p>
<ul>
<li><p>エンタープライズ向けの Microsoft 365 アプリ</p></li>
<li><p>Visio Pro for Office 365</p></li>
<li><p>Project Pro for Office 365</p></li>
</ul></td>
<td align="left"><p>共有コンピューターのライセンス認証を有効にする必要があり <a href="https://technet.microsoft.com/library/dn782860.aspx" data-raw-source="[shared computer activation](https://technet.microsoft.com/library/dn782860.aspx)"> </a> ます。</p>
</td>
</tr>
</tbody>
</table>



### パッケージからの Office アプリケーションの除外

次の表では、特定の Office アプリケーションをパッケージから除外するための推奨される方法について説明します。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">タスク</th>
<th align="left">詳細</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong> </strong> Office 展開ツールを使用してパッケージを作成する場合は、excludeapp 設定を使います。</p></td>
<td align="left"><ul>
<li><p>Office 展開ツールがパッケージを作成するときに、特定の Office アプリケーションをパッケージから除外できるようにします。 たとえば、この設定を使って、Microsoft Word のみを含むパッケージを作成することができます。</p></li>
<li><p>詳細については、「excludeapp 要素」を参照してください <a href="https://technet.microsoft.com/library/jj219426.aspx#bkmk-excludeappelement" data-raw-source="[ExcludeApp element](https://technet.microsoft.com/library/jj219426.aspx#bkmk-excludeappelement)"> </a> 。</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p>DeploymentConfig.xml ファイルを変更する</p></td>
<td align="left"><ul>
<li><p>パッケージを作成した後で DeploymentConfig.xml ファイルを変更します。 このファイルには、App-v クライアントを実行しているコンピューター上のすべてのユーザーの既定のパッケージ設定が含まれています。</p></li>
<li><p>詳細については、「 <a href="#bkmk-disable-office-apps" data-raw-source="[Disabling Office 2016 applications](#bkmk-disable-office-apps)"> Office 2016 アプリケーションを無効にする」を参照してください </a> 。</p></li>
</ul></td>
</tr>
</tbody>
</table>



## <a href="" id="bkmk-create-office-pkg"></a>Office 展開ツールを使用して、App-v 用の Office 2016 パッケージを作成する


次の手順を実行して、App-v 5.1 以降の Office 2016 パッケージを作成します。

>**Important** &nbsp; 重要 &nbsp;App-v 5.1 以降では、Office 展開ツールを使用してパッケージを作成する必要があります。 Sequencer を使ってパッケージを作成することはできません。

### Office 展開ツールを使用するための前提条件を確認する

Office 展開ツールをインストールするコンピューターには、次のものが必要です。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">受講</th>
<th align="left">説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>必須ソフトウェア</p></td>
<td align="left"><p>.Net Framework 4</p></td>
</tr>
<tr class="even">
<td align="left"><p>サポートされているオペレーティング システム</p></td>
<td align="left"><ul>
<li><p>64ビット版の Windows 10</p></li>
<li><p>64ビット版の Windows 8 または8.1</p></li>
<li><p>64ビット版の Windows 7</p></li>
</ul></td>
</tr>
</tbody>
</table>


>**注** このトピックでは、"Office 2016 App-v パッケージ" という用語は、サブスクリプションライセンスを示しています。


### Office 展開ツールを使用して Office 2016 App-v パッケージを作成する

Office 2016 App-v パッケージを作成するには、Office 展開ツールを使用します。 次の手順では、サブスクリプションのライセンスを持つ Office 2016 App-v パッケージを作成する方法について説明します。

64ビットの Windows コンピューター上で Office 2016 App-v パッケージを作成します。 作成された Office 2016 App-v パッケージは、32ビットおよび64ビットの Windows 7、Windows 8.1、Windows 10 のコンピューターで実行されます。

### Office 展開ツールをダウンロードする

Office 2016 App-v パッケージは、office 展開ツールを使って作成されます。このパッケージは、office 2016 App-v パッケージを生成します。 App-v sequencer でパッケージを作成または変更することはできません。 パッケージの作成を開始するには:

1.  [クイック実行用に Office 2016 展開ツール](https://www.microsoft.com/download/details.aspx?id=49117)をダウンロードします。

> **重要**Office 2016 展開ツールを使用して、Office 2016 App-v パッケージを作成する必要があります。
> 2. .Exe ファイルを実行し、目的の場所にその機能を抽出します。 このプロセスをより簡単にするために、機能を保存する共有ネットワークフォルダーを作成することができます。

    Example: \\\\Server\\Office2016

3. setup.exe と configuration.xml ファイルが存在し、指定した場所にあることを確認します。

### Office 2016 アプリケーションをダウンロードする

Office 展開ツールをダウンロードしたら、それを使って最新の Office 2016 アプリケーションを入手できます。 Office アプリケーションを入手したら、Office 2016 App-v パッケージを作成します。

Office 展開ツールに含まれている XML ファイルでは、対象となる言語や Office アプリケーションなどの製品の詳細を指定します。

1. **サンプルの XML 構成ファイルをカスタマイズします。** Office 展開ツールと共にダウンロードしたサンプル XML 構成ファイルを使用して、Office アプリケーションをカスタマイズします。

   1. メモ帳またはお気に入りのテキストエディターでサンプル XML ファイルを開きます。

   2. サンプルの configuration.xml ファイルを開いて編集する準備ができたら、製品、言語、Office 2016 アプリケーションの保存先のパスを指定できます。 configuration.xml ファイルの基本的な例を次に示します。

      ```xml
      <Configuration>
         <Add SourcePath= ”\\Server\Office2016” OfficeClientEdition="32" >
          <Product ID="O365ProPlusRetail ">
            <Language ID="en-us" />
          </Product>
          <Product ID="VisioProRetail">
            <Language ID="en-us" />
          </Product>
        </Add>
      </Configuration>
      ```

      >**注** 構成 XML はサンプルの XML ファイルです。 ファイルには、コメントアウトされた行が含まれています。ファイルを使用して追加の設定をカスタマイズするには、これらの行のコメントを解除します。 これらの行のコメントを解除するには、「<」を削除します。 ------->--------------------------------------

      上の XML 構成ファイルを使用すると、Office 2016 ProPlus 32 ビット版 (Visio ProPlus を含む) が2016英語でダウンロードされます。これは、Office アプリケーションが保存される場所です。 アプリケーションの製品 ID は、Office の最終的なライセンスに影響を与えないことに注意してください。 さまざまなライセンスを持つ Office 2016 アプリ V パッケージは、後の段階でライセンスを指定することによって同じアプリケーションから作成できます。 次の表は、XML ファイルのカスタマイズ可能な属性と要素をまとめたものです。

      <table>
      <colgroup>
      <col width="33%" />
      <col width="33%" />
      <col width="33%" />
      </colgroup>
      <thead>
      <tr class="header">
      <th align="left">入力</th>
      <th align="left">説明</th>
      <th align="left">例</th>
      </tr>
      </thead>
      <tbody>
      <tr class="odd">
      <td align="left"><p>要素の追加</p></td>
      <td align="left"><p>パッケージに含める製品と言語を指定します。</p></td>
      <td align="left"><p>なし</p></td>
      </tr>
      <tr class="even">
      <td align="left"><p>OfficeClientEdition (Add 要素の属性)</p></td>
      <td align="left"><p>使用する Office 2016 製品のバージョン (32 ビットまたは64ビット) を指定します。 <strong>OfficeClientEdition </strong> が有効な値に設定されていない場合、操作は失敗します。</p></td>
      <td align="left"><p><strong>OfficeClientEdition </strong> = &quot; 32&quot;</p>
      <p><strong>OfficeClientEdition </strong> = &quot; 64&quot;</p></td>
      </tr>
      <tr class="odd">
      <td align="left"><p>Product 要素</p></td>
      <td align="left"><p>アプリケーションを指定します。 プロジェクト2016と Visio 2016 は、追加された製品としてアプリケーションに含める必要があります。

      製品 Id の詳細については、「 <a href="https://support.microsoft.com/kb/2842297" data-raw-source="[Product IDs that are supported by the Office Deployment Tool for Click-to-Run](https://support.microsoft.com/kb/2842297)"> クイック実行用に Office 展開ツールでサポートされている製品 id」を参照してください。</a>
      </p></td>
      <td align="left"><p><code>Product ID =&quot;O365ProPlusRetail &quot;</code></p>
      <p><code>Product ID =&quot;VisioProRetail&quot;</code></p>
      <p><code>Product ID =&quot;ProjectProRetail&quot;</code></p>
      </td>
      </tr>
      <tr class="even">
      <td align="left"><p>Language 要素</p></td>
      <td align="left"><p>アプリケーションでサポートされる言語を指定します</p></td>
      <td align="left"><p><code>Language ID=&quot;en-us&quot;</code></p></td>
      </tr>
      <tr class="odd">
      <td align="left"><p>Version (Add 要素の属性)</p></td>
      <td align="left"><p>省略可能。 パッケージに使用するビルドを指定します</p>
      <p>既定では、[最新のアドバタイズされたビルド] (Office ソースの v32.CAB で定義)</p></td>
      <td align="left"><p><code>16.1.2.3</code></p></td>
      </tr>
      <tr class="even">
      <td align="left"><p>SourcePath (Add 要素の属性)</p></td>
      <td align="left"><p>アプリケーションが保存される場所を指定します。</p></td>
      <td align="left"><p><code>Sourcepath = &quot;\Server\Office2016”</code></p></td>
      </tr>
      <tr class="even">
      <td align="left"><p>Branch (Add 要素の属性)</p></td>
      <td align="left"><p>省略可能。 ダウンロードまたはインストールする製品の更新ブランチを指定します。 </p><p>ブランチの更新の詳細については、「エンタープライズ向けの Microsoft 365 アプリの更新ブランチの概要」を参照してください。</p></td>
      <td align="left"><p><code>Branch = &quot;Business&quot;</code></p></td>
      </tr>
      </tbody>
      </table>

      configuration.xml ファイルを編集して、目的の製品、言語、および Office 2016 アプリケーションの保存場所を指定した後、Customconfig.xml として構成ファイルを保存できます。

2. **指定した場所にアプリケーションをダウンロードします。** 昇格したコマンドプロンプトと64ビットのオペレーティングシステムを使って、後で App-v パッケージに変換される Office 2016 アプリケーションをダウンロードします。 詳細については、次のコマンド例を参照してください。

   ``` syntax
   \\server\Office2016\setup.exe /download \\server\Office2016\Customconfig.xml
   ```

   次に例を示します。

   <table>
   <colgroup>
   <col width="50%" />
   <col width="50%" />
   </colgroup>
   <tbody>
   <tr class="odd">
   <td align="left"><p><strong>\ server office2016</strong></p></td>
   <td align="left"><p>は、Office 展開ツールとカスタム Configuration.xml ファイル (Customconfig.xml を含むネットワーク共有の場所です。</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p><strong>Setup.exe</strong></p></td>
   <td align="left"><p>は Office 展開ツールです。</p></td>
   </tr>
   <tr class="odd">
   <td align="left"><p><strong>/download</strong></p></td>
   <td align="left"><p>customConfig.xml ファイルで指定した Office 2016 アプリケーションをダウンロードします。 これらの bits は、ボリュームライセンスを持つ Office 2016 App-v パッケージで後で変換することができます。</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p><strong>\server\Office2016\Customconfig.xml</strong></p></td>
   <td align="left"><p>ダウンロードプロセスを完了するために必要な XML 構成ファイルを渡します。この例では、customconfig.xml を実行します。 [ダウンロード] コマンドを使用した後、Office アプリケーションは、構成 xml ファイルで指定されている場所 (この例では \ 2016office) にあります。</p></td>
   </tr>
   </tbody>
   </table>



### Office アプリケーションを App-v パッケージに変換する

Office 展開ツールを使用して Office 2016 アプリケーションをダウンロードした後、Office 展開ツールを使用して office 2016 App-v パッケージに変換します。 ライセンスモデルに対応する手順を実行します。

**必要な作業の概要:**

-   64ビットの Windows コンピューター上で Office 2016 App-v パッケージを作成します。 ただし、パッケージは、32ビットおよび64ビットの Windows 7、Windows 8、8.1、Windows 10 のコンピューターで実行されます。

-   Office 展開ツールを使用してサブスクリプションライセンスパッケージの Office App-v パッケージを作成し、CustomConfig.xml 構成ファイルを変更します。

    次の表は、使用しているライセンスモデルの CustomConfig.xml ファイルに入力する必要がある値をまとめたものです。 表に記載されているセクションの手順では、実行する必要がある正確なエントリを指定します。

>**Note** &nbsp; 注 &nbsp;Office 展開ツールを使用して、enterprise 用の Microsoft 365 アプリの App-v パッケージを作成することができます。 ボリュームライセンス版の Office Professional Plus または Office Standard のパッケージの作成はサポートされていません。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">製品 ID</th>
<th align="left">サブスクリプションのライセンス</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Office 2016</strong></p></td>
<td align="left"><p>O365ProPlusRetail</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Visio 2016 での Office 2016</strong></p></td>
<td align="left"><p>O365ProPlusRetail</p>
<p>VisioProRetail</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Office 2016 と Visio 2016、および Project 2016</strong></p></td>
<td align="left"><p>O365ProPlusRetail</p>
<p>VisioProRetail</p>
<p>ProjectProRetail</p></td>
</tr>
</tbody>
</table>



**Office アプリケーションを App-v パッケージに変換する方法**

1. メモ帳で CustomConfig.xml ファイルをもう一度開き、ファイルに次の変更を加えます。

   <table>
   <colgroup>
   <col width="50%" />
   <col width="50%" />
   </colgroup>
   <thead>
   <tr class="header">
   <th align="left">パラメーター</th>
   <th align="left">値を次のように変更する</th>
   </tr>
   </thead>
   <tbody>
   <tr class="odd">
   <td align="left"><p>SourcePath</p></td>
   <td align="left"><p>前にダウンロードした Office アプリケーションをポイントします。</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p>ProductID</p></td>
   <td align="left"><p>次の例に示すように、サブスクリプションのライセンスを指定します。</p>
   <pre class="syntax" space="preserve"><code>&lt;Configuration&gt;
      &lt;Add SourcePath= &quot;\server\Office 2016&quot; OfficeClientEdition=&quot;32&quot; &gt;
       &lt;Product ID=&quot;O365ProPlusRetail&quot;&gt;
         &lt;Language ID=&quot;en-us&quot; /&gt;
       &lt;/Product&gt;
       &lt;Product ID=&quot;VisioProRetail&quot;&gt;
         &lt;Language ID=&quot;en-us&quot; /&gt;
       &lt;/Product&gt;
     &lt;/Add&gt;
   &lt;/Configuration&gt; </code></pre>
   <p>この例では、サブスクリプションのライセンスを持つパッケージを作成するために、次の変更が加えられました。</p>
   <table>
   <colgroup>
   <col width="50%" />
   <col width="50%" />
   </colgroup>
   <tbody>
   <tr class="odd">
   <td align="left"><p><strong>SourcePath</strong></p></td>
   <td align="left"><p>は、以前にダウンロードした Office アプリケーションを指すように変更されたパスです。</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p><strong>製品 ID</strong></p></td>
   <td align="left"><p>Office のはに変更されました <code>O365ProPlusRetail</code> 。</p></td>
   </tr>
   <tr class="odd">
   <td align="left"><p><strong>製品 ID</strong></p></td>
   <td align="left"><p>がに変更されました <code>VisioProRetail</code> 。</p></td>
   </tr>
   </tbody>
   </table>
   <p></p>
   <tr class="odd">
   <td align="left"><p>ExcludeApp (省略可能)</p></td>
   <td align="left"><p>Office 展開ツールによって作成される App-v パッケージに含まれない Office プログラムを指定できます。 たとえば、Access や InfoPath を除外することができます。</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p>PACKAGEGUID (省略可能)</p></td>
   <td align="left"><p>既定では、Office 展開ツールによって作成されたすべての App-v パッケージは、同じアプリ-V パッケージ ID を共有します。 PACKAGEGUID を使用して、各パッケージに異なるパッケージ ID を指定することができます。これにより、Office 展開ツールによって作成された複数の App-v パッケージを公開して、アプリを管理することができます。</p>
   <p>このパラメーターを使用する場合の例として、さまざまなユーザーに対して異なるパッケージを作成する場合が挙げられます。 たとえば、一部のユーザーについては Office 2016 だけでパッケージを作成し、別のユーザーには Office 2016 と Visio 2016 を使用して別のパッケージを作成することができます。</p>

   &gt;<strong>注: </strong> 一意のパッケージ id を使用している場合でも、1つのデバイスに1つの app-v パッケージを展開することができます。
   </td>
   </tr>
   </tbody>
   </table>


2. Office アプリケーションを Office 2016 App-v パッケージに変換するには、/パッケージャーコマンドを使用します。

   以下に例を示します。

   ``` syntax
   \\server\Office2016\setup.exe /packager \\server\Office2016\Customconfig.xml  \\server\share\Office2016AppV
   ```

   次に例を示します。

   <table>
   <colgroup>
   <col width="50%" />
   <col width="50%" />
   </colgroup>
   <tbody>
   <tr class="odd">
   <td align="left"><p><strong>\ server office2016</strong></p></td>
   <td align="left"><p>は、Office 展開ツールとカスタム Configuration.xml ファイル (Customconfig.xml を含むネットワーク共有の場所です。</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p><strong>Setup.exe</strong></p></td>
   <td align="left"><p>は Office 展開ツールです。</p></td>
   </tr>
   <tr class="odd">
   <td align="left"><p><strong>/パッケージャー</strong></p></td>
   <td align="left"><p>customConfig.xml ファイルで指定されたライセンスの種類を使用して、Office 2016 App-v パッケージを作成します。</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p><strong>\server\Office2016\Customconfig.xml</strong></p></td>
   <td align="left"><p>パッケージステージの準備が整った構成 XML ファイル (この場合は、customConfig) を渡します。</p></td>
   </tr>
   <tr class="odd">
   <td align="left"><p><strong>\ \ sharepoint/Office 2016AppV</strong></p></td>
   <td align="left"><p>新しく作成された Office App-v パッケージの場所を指定します。</p></td>
   </tr>
   </tbody>
   </table>



~~~
After you run the **/packager** command, the following folders appear up in the directory where you specified the package should be saved:

-   **App-V Packages** – contains an Office 2016 App-V package and two deployment configuration files.

-   **WorkingDir**

**Note** To troubleshoot any issues, see the log files in the %temp% directory (default).
~~~



3. Office 2016 App-v パッケージが正しく動作することを確認します。

   1.  グローバルに作成した Office 2016 App-v パッケージをテストコンピューターに発行し、Office 2016 のショートカットが表示されることを確認します。

   2.  いくつかの Office 2016 アプリケーション (Excel や Word など) を起動して、パッケージが期待どおりに動作することを確認します。

## <a href="" id="bkmk-pub-pkg-office"></a>Office パッケージを App-v 用に発行する-V


Office パッケージを公開するには、次の情報を使用します。

### Office App-v パッケージを発行するためのメソッド

他のパッケージと同じ方法を使用して、Office 2016 用の App-v パッケージを展開します。

-   System Center Configuration Manager

-   App-v Server

-   PowerShell コマンドを使用したスタンドアロン

### 発行の前提条件と要件

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">前提条件または要件</th>
<th align="left">詳細</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>App-v クライアントで PowerShell スクリプトを有効にする</p></td>
<td align="left"><p>Office 2016 パッケージを発行するには、スクリプトを実行する必要があります。</p>
<p>App-v クライアントでは、パッケージスクリプトは既定で無効になっています。 スクリプトを有効にするには、次の PowerShell コマンドを実行します。</p>
<pre class="syntax" space="preserve"><code>Set-AppvClientConfiguration –EnablePackageScripts 1</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>Office 2016 パッケージをグローバルに公開する</p></td>
<td align="left"><p>Office App-v パッケージの拡張ポイントは、コンピューターレベルでインストールする必要があります。</p>
<p>コンピューターレベルで公開する場合、必要な操作または再配布は不要であり、Office 2016 パッケージでは、ネイティブにインストールされた Office と同じようにアプリをグローバルに使用できるため、管理者がパッケージをカスタマイズする必要はありません。</p></td>
</tr>
</tbody>
</table>



### Office パッケージを公開する方法

Office パッケージをグローバルに公開するには、次のコマンドを実行します。

-   `Add-AppvClientPackage <Path_to_AppV_Package> | Publish-AppvClientPackage –global`

-   App-v Server の Web 管理コンソールから、ユーザーグループではなく、コンピューターのグループにアクセス許可を追加して、パッケージを対応するグループ内のコンピューターにグローバルに公開することができます。

## <a href="" id="bkmk-custmz-manage-office-pkgs"></a>Office App-v パッケージのカスタマイズと管理


Office App-v パッケージを管理するには、他のパッケージと同じ操作を実行しますが、次のセクションで説明するように、いくつかの例外があります。

-   [接続グループを使用して Office プラグインを有効にする](#bkmk-enable-office-plugins)

-   [Office 2016 アプリケーションの無効化](#bkmk-disable-office-apps)

-   [Office 2016 ショートカットを無効にする](#bkmk-disable-shortcuts)

-   [Office 2016 パッケージのアップグレードの管理](#bkmk-manage-office-pkg-upgrd)

-   [Office で Visio 2016 と Project 2016 を展開する](#bkmk-deploy-visio-project)

### <a href="" id="bkmk-enable-office-plugins"></a>接続グループを使用して Office プラグインを有効にする

このセクションの手順を使用して、office パッケージで Office プラグインを有効にします。 Office プラグインを使うには、アプリ-V シーケンサーを使って、プラグインだけを含む個別のパッケージを作成する必要があります。Office 展開ツールを使用して、プラグインパッケージを作成することはできません。 次に、次の手順で説明するように、Office パッケージとプラグインパッケージを含む接続グループを作成します。

**Office App-v パッケージのプラグインを有効にするには**

1.  App-v Server、System Center Configuration Manager、または PowerShell コマンドレットを使用して、接続グループを追加します。

2.  App-v Sequencer を使ってプラグインの順序を作成します。 プラグインの順序を示すために使用されているコンピューターに Office 2016 がインストールされていることを確認します。 Office 2016 プラグインをシーケンス処理するときは、シーケンスコンピューターで Microsoft 365 アプリを使用することをお勧めします。

3.  目的のプラグインを含む App-v パッケージを作成します。

4.  App-v server、System Center Configuration Manager、または PowerShell コマンドレットを使用して、接続グループを追加します。

5.  作成した接続グループに並べた Office 2016 アプリとプラグインパッケージを追加します。

    >**重要**接続グループ内のパッケージの順序によって、パッケージコンテンツのマージ順序が決まります。 接続グループ記述子ファイルで、最初に Office 2016 App-V パッケージを追加してから、プラグインの App-v パッケージを追加します。



6.  両方のパッケージがターゲットコンピューターに公開されていること、およびプラグインパッケージがグローバルに公開された Office 2016 App-v パッケージのグローバル設定と一致するように公開されていることを確認します。

7.  プラグインパッケージの展開構成ファイルの設定が、Office 2016 App-v パッケージの設定と同じであることを確認します。

    Office 2016 App-v パッケージはオペレーティングシステムと統合されているため、プラグインパッケージの設定は一致する必要があります。 展開構成ファイルで "COM モード" を検索し、プラグインパッケージの値が "Integrated" として設定されていること、および "InProcessEnabled" と "OutOfProcessEnabled" の両方が、公開した Office 2016 App-v パッケージの設定と一致していることを確認することができます。

8.  展開構成ファイルを開き、**有効なオブジェクト**の値を**false**に設定します。

9.  シーケンス後に展開構成ファイルに変更を加えた場合は、プラグインパッケージがファイルと共に公開されていることを確認します。

10. 作成した接続グループが、目的のコンピューターに有効になっていることを確認します。 接続グループが有効になっている場合、作成された接続グループは、Office 2016 App-v パッケージを使用している場合、"保留" される可能性があります。 この問題が発生した場合は、再起動して接続グループを正常に有効にする必要があります。

11. 両方のパッケージを正常に公開し、接続グループを有効にした後、ターゲットの Office 2016 アプリケーションを起動して、接続グループに公開して追加したプラグインが正常に動作することを確認します。

### <a href="" id="bkmk-disable-office-apps"></a>Office 2016 アプリケーションの無効化

Office App-v パッケージで特定のアプリケーションを無効にすることができます。 たとえば、Access を無効にすることはできますが、その他のすべての Office アプリケーションはそのまま使用できます。 アプリケーションを無効にすると、エンドユーザーにそのアプリケーションのショートカットが表示されなくなります。 アプリケーションの順序を再設定する必要はありません。 Office 2016 App-v パッケージが公開された後に展開構成ファイルを変更した場合は、変更内容を保存して、Office 2016 App-v パッケージを追加し、新しい展開構成ファイルを使って Office 2016 App-v パッケージアプリケーションに新しい設定を適用します。

>**注**Office 展開ツールを使用して app-v パッケージを作成するときに、特定の Office アプリケーション (Access や InfoPath など) を除外するには、 **Excludeapp**設定を使用します。


**Office 2016 アプリケーションを無効にするには**

1.  **メモ帳**などのテキストエディターで展開構成ファイルを開き、"アプリケーション" を検索します。

2.  無効にする Office アプリケーション (Access 2016 など) を検索します。

3.  "有効" の値を "true" から "false" に変更します。

4.  展開構成ファイルを保存します。

5.  新しい展開構成ファイルを使用して、Office 2016 App-v パッケージを追加します。

    ```xml
    <Application Id="[{AppVPackageRoot}]\office16\lync.exe" Enabled="true">
      <VisualElements>
        <Name>Lync 2016</Name>
        <Icon />
        <Description />
      </VisualElements>
    </Application>
    <Application Id="[(AppVPackageRoot}]\office16\MSACCESS.EXE" Enabled="true">
      <VisualElements>
        <Name>Access 2016</Name>
        <Icon />
        <Description />
      </VisualElements>
    </Application>
    ```

6.  Office 2016 App-v パッケージを再度追加し、新しい展開構成ファイルを使用して再公開し、新しい設定を Office 2016 App-v パッケージアプリケーションに適用します。

### <a href="" id="bkmk-disable-shortcuts"></a>Office 2016 ショートカットを無効にする

特定の Office アプリケーションのショートカットを無効にすることもできます。その場合は、パッケージを非公開にするか、削除する必要があります。 次の例は、Microsoft Access のショートカットキーを無効にする方法を示しています。

**Office 2016 アプリケーションのショートカットを無効にするには**

1.  メモ帳で展開構成ファイルを開き、"ショートカット" を検索します。

2.  特定のショートカットを無効にするには、必要のない特定のショートカットを削除またはコメントアウトします。 サブシステムを常に表示して有効にする必要があります。 たとえば、次の例では、サブシステムのショートカットまたは &lt; &gt; &lt; ショートカットをそのままにして &gt; microsoft access ショートカットを無効にして、microsoft access のショートカットを削除します。

    ``` syntax
    Shortcuts

    -->
     <Shortcuts Enabled="true">
      <Extensions>
        <Extension Category="AppV.Shortcut">
          <Shortcut>
           <File>[{Common Programs}]\Microsoft Office 2016\Access 2016.lnk</File>
           <Target>[{AppvPackageRoot}])office16\MSACCESS.EXE</Target>
           <Icon>[{Windows}]\Installer\{90150000-000F-0000-0000-000000FF1CE)\accicons.exe.Ø.ico</Icon>
           <Arguments />
           <WorkingDirectory />
           <AppuserModelId>Microsoft.Office.MSACCESS.EXE.15</AppUserModelId>
           <AppUserModelExcludeFromShowInNewInstall>true</AppUserModelExcludeFromShowInNewInstall>
           <Description>Build a professional app quickly to manage data.</Description>
           <ShowCommand>l</ShowCommand>
           <ApplicationId>[{AppVPackageRoot}]\office16\MSACCESS.EXE</ApplicationId>
        </Shortcut>
    ```

3.  展開構成ファイルを保存します。

4.  新しい展開構成ファイルを使用して、Office 2016 App-v パッケージを再公開します。

他にも多くの設定を変更するには、たとえば、ファイルの種類の関連付け、仮想ファイルシステムなどの App-v パッケージの展開構成を変更します。 展開構成ファイルを使用して App-v パッケージの設定を変更する方法の詳細については、このドキュメントの最後にある「その他のリソース」セクションを参照してください。

### <a href="" id="bkmk-manage-office-pkg-upgrd"></a>Office 2016 パッケージのアップグレードの管理

Office 2016 パッケージをアップグレードするには、Office 展開ツールを使用します。 以前に展開された Office 2016 パッケージをアップグレードするには、次の手順を実行します。

**以前に展開された Office 2016 パッケージのアップグレード方法**

1. 最新の Office 2016 アプリケーションソフトウェアを使用している Office 展開ツールを使用して、新しい Office 2016 パッケージを作成します。 最新の Office 2016 bits は、Office 2016 App-v パッケージを作成するためのダウンロード段階でいつでも入手できます。 新しく作成された Office 2016 パッケージには、最新の更新プログラムと新しいバージョン ID が含まれています。 Office 展開ツールを使用して作成されたすべてのパッケージは、同じ系列になります。

   > **注**Office App-V パッケージには2つのバージョン Id があります。
   > <ul>
   > <li>Office 展開ツールを使用して作成されたすべてのパッケージ間で一意の Office 2016 App-v パッケージバージョン ID。</li>
   > <li>新しいバージョンの Office 自体がある場合にのみ変更される AppX マニフェストなどの、2つ目の App-v パッケージバージョン ID である x.x.x.x のバージョン。 たとえば、アップグレード機能付きの新しい Office 2016 リリースが用意されていて、Office 展開ツールを使用してこれらのアップグレードを組み込むパッケージを作成した場合、X.x.x.x のバージョン ID が変更され、Office バージョンの変更が反映されます。 App-v server は、x.x.x.x バージョン ID を使ってこのパッケージを区別し、以前に公開されたパッケージへの新しいアップグレードが含まれていることを認識し、その結果として、既存の Office 2016 パッケージへのアップグレードとして発行します。</li>
   > </ul>


2. 新しく作成された Office 2016 App-v パッケージを、新しい更新プログラムを適用するコンピューター上にグローバルに公開します。 新しいパッケージは、古い Office 2016 App-v パッケージの系列と同じであるため、更新プログラムを使用して新しいパッケージを公開しても、古いパッケージに新しい変更が適用されるため、高速になります。

3. アップグレードは、グローバルに公開された App-v パッケージと同じ方法で適用されます。 アプリケーションはおそらく使用されているため、コンピューターが再起動されるまで、アップグレードの遅延が発生する可能性があります。


### <a href="" id="bkmk-deploy-visio-project"></a>Office で Visio 2016 と Project 2016 を展開する

次の表では、Visio 2016 と Project 2016 を Office と共に展開するための要件とオプションについて説明します。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">タスク</th>
<th align="left">詳細</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Visio 2016 および Project 2016 を Office と共にパッケージ化して発行するにはどうすればよいですか?</p></td>
<td align="left"><p>Office と同じパッケージに Visio 2016 と Project 2016 を含める必要があります。</p>
<p>Office を展開していない場合は、このトピックで説明されているパッケージ化、発行、展開の要件に従う限り、Visio または Project を含むパッケージを作成することができます。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Visio 2016 と Project 2016 を特定のユーザーに展開するにはどうすればよいですか?</p></td>
<td align="left"><p>以下の方法のうちのいずれか 1 つを使用します。</p>
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">目的の処理</th>
<th align="left">...次に、この方法を使用します。</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>2つの異なるパッケージを作成し、それぞれを別のユーザーグループに展開する</p></td>
<td align="left"><p>次のパッケージを作成して展開します。</p>
<ul>
<li><p>Office のみを含むパッケージで、ユーザーが Office のみを必要とするコンピューターに展開されます。</p></li>
<li><p>Office、Visio、Project を含むパッケージ。ユーザーが3つのアプリケーションを必要とするコンピューターに展開します。</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p>組織全体に対してパッケージを1つだけ追加する場合、またはコンピューターを共有しているユーザーがいる場合は、次の操作を行います。</p></td>
<td align="left"><p>次の手順を実行します。</p>
<ol>
<li><p>Office、Visio、および Project を含むパッケージを作成します。</p></li>
<li><p>パッケージをすべてのユーザーに展開します。</p></li>
<li><p><a href="https://technet.microsoft.com/library/dd723678.aspx" data-raw-source="[Microsoft AppLocker](https://technet.microsoft.com/library/dd723678.aspx)">Microsoft AppLocker を使用し </a> て、特定のユーザーによる Visio と Project の使用を防止します。</p></li>
</ol></td>
</tr>
</tbody>
</table>
<p> </p></td>
</tr>
</tbody>
</table>


## その他の情報


[APP-V を使用した Microsoft Office 2013 の展開](deploying-microsoft-office-2013-by-using-app-v.md)

[APP-V を使用した Microsoft Office 2010 の展開](deploying-microsoft-office-2010-by-using-app-v.md)

[クイック実行用の Office 2016 展開ツール](https://www.microsoft.com/download/details.aspx?id=49117)

**接続グループ**

[Microsoft App での接続グループの展開-V v5](https://go.microsoft.com/fwlink/p/?LinkId=330683)

[接続グループの管理](managing-connection-groups.md)

**動的構成**

[App-V 5.1 の動的構成について](about-app-v-51-dynamic-configuration.md)





