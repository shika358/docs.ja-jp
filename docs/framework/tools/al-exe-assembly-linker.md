---
title: "Al.exe (アセンブリ リンカー) | Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Al.exe
- Assembly Linker
- modules, Assembly Linker
- assembly manifest, Assembly Linker
ms.assetid: b5382965-0053-47cf-b92f-862860275a01
caps.latest.revision: 37
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2bbb13d5a885cca264ebb29edd5f97799630601e
ms.contentlocale: ja-jp
ms.lasthandoff: 06/02/2017

---
# <a name="alexe-assembly-linker"></a>Al.exe (アセンブリ リンカー)
アセンブリ リンカーは、モジュールまたはリソース ファイルのいずれかである 1 つ以上のファイルから、アセンブリのマニフェストを含むファイルを生成します。 モジュールとは、アセンブリ マニフェストを含まない中間言語 (IL: Intermediate Language) ファイルのことです。  
  
> [!NOTE]
>  Windows Vista コンピューターで仮想化されることを回避するには、要求実行レベルを指定した Win32 マニフェストがアセンブリに含まれていることが必要です。 コマンド ラインから al.exe を直接使用するときには、Win32 リソース ファイルにマニフェストを埋め込むことができます。または、ビルド プロセスの後の段階で mt.exe を使用してマニフェストを追加することも可能です。 [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)] 以降では、C# と Visual Basic のどちらのコンパイラを使用しても、Win32 マニフェストはアセンブリに自動的に埋め込まれます。 詳細については、「[/win32manifest (C# コンパイラ オプション)](~/docs/csharp/language-reference/compiler-options/win32manifest-compiler-option.md)」を参照してください。  
  
 このツールは、Visual Studio と共に自動的にインストールされます。 このツールを実行するには、開発者コマンド プロンプト (または、Windows 7 の Visual Studio コマンド プロンプト) を使用します。 詳細については、「[コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。  
  
 コマンド プロンプトに次のように入力します。  
  
## <a name="syntax"></a>構文  
  
```  
al sources options  
```  
  
#### <a name="parameters"></a>パラメーター  
 次の `sources` を 1 つ以上組み合わせて指定できます。  
  
|ソース|説明|  
|------------|-----------------|  
|`file`[,`target`]|`file` (モジュール) の内容を `target` で名前が指定されたファイルにコピーします。 コピーが完了すると、Al.exe は `target` をコンパイルしてアセンブリを生成します。|  
|**/embed**[`resource`]`:``file`[,`name`[,`private`]]|`file` で指定したリソースをアセンブリ マニフェストを含むイメージに埋め込みます。Al.exe は、`file` の内容をポータブル実行可能 (PE) イメージにコピーします。<br /><br /> `name` パラメーターは、リソースの内部識別子です。 既定では、リソースはアセンブリでパブリックに指定されており、他のアセンブリから参照できます。 `private` を指定すると、そのリソースを他のアセンブリから参照できなくなります。<br /><br /> `file` が[リソース ファイル ジェネレーター (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) や開発環境などで作成された .NET Framework リソース ファイルである場合は、<xref:System.Resources> のメンバーを使用してそのファイルにアクセスできます。 詳細については、「<xref:System.Resources.ResourceManager>」を参照してください。 それ以外のすべてのリソースに対しては、`GetManifestResource` の <xref:System.Reflection.Assembly>* メソッドを使用して、実行時にリソースにアクセスします。<br /><br /> リソース ファイルだけが Al.exe に渡された場合は、出力ファイルはサテライト リソース アセンブリになります。|  
|**/link**[`resource`]:`file`[,`name`[,`target`[,`private`]]]|リソース ファイルをアセンブリにリンクします。 `file` によって指定されたリソースがアセンブリの一部になります。ファイルはコピーされません。 `file` パラメーターには、任意のファイル形式を指定できます。 たとえば、`file` パラメーターとしてネイティブ DLL を指定できます。 このようにすると、ネイティブ DLL はアセンブリの一部になるので、グローバル アセンブリ キャッシュにインストールして、アセンブリ内のマネージ コードからアクセスできます。 **/linkresource** コンパイラ オプションを使用して、これを実行することもできます。 詳しくは、「[/linkresource (C# コンパイラ オプション)](~/docs/csharp/language-reference/compiler-options/linkresource-compiler-option.md)」をご覧ください。<br /><br /> `name` パラメーターは、リソースの内部識別子です。 `target` パラメーターは、Al.exe が `file` *をコピーする対象のパスおよびファイル名を指定します。* コピーが完了すると、Al.exe は `target` をコンパイルしてアセンブリを生成します。 既定では、リソースはアセンブリでパブリックに指定されており、他のアセンブリから参照できます。 `private` を指定すると、そのリソースを他のアセンブリから参照できなくなります。<br /><br /> `file` がリソース ファイル ジェネレーター (Resgen.exe) や開発環境などで作成された .NET Framework リソース ファイルである場合は、<xref:System.Resources> 名前空間のメンバーを使用してそのファイルにアクセスできます。 詳細については、「<xref:System.Resources.ResourceManager>」を参照してください。 それ以外のすべてのリソースに対しては、`GetManifestResource` クラスの <xref:System.Reflection.Assembly>* メソッドを使用して、実行時にリソースにアクセスします。<br /><br /> リソース ファイルだけが Al.exe に渡された場合は、出力ファイルはサテライト リソース アセンブリになります。|  
  
 指定できる `options` を次に示します。**/out** オプションは必ず指定する必要があります。  
  
|オプション|説明|  
|------------|-----------------|  
|**/algid**:`id`|アセンブリ マニフェストを含むファイルを除き、マルチファイル アセンブリ内の全ファイルをハッシュするためのアルゴリズムを指定します。 既定のアルゴリズムは CALG_SHA1 です。 その他のアルゴリズムについては、プラットフォーム SDK の ALG_ID のトピックを参照してください。 .NET Framework の最初のリリースでは、CALG_SHA1 および CALG_MD5 だけがサポートされています。<br /><br /> ハッシュ値は、アセンブリ マニフェストのファイル テーブルに格納されます。 インストール時や読み込み時に、アセンブリのファイルがそのハッシュと突き合わせされてチェックされます。<br /><br /> このオプションは、任意のモジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyAlgorithmIdAttribute>) として指定することもできます。|  
|**/base**[`address`]:`addr`|実行時にユーザーのコンピューターに DLL を読み込む先のアドレスを指定します。 オペレーティング システムにプロセス空間内で DLL を再配置させる代わりに DLL のベース アドレスを指定しておくと、アプリケーションの読み込み速度が速くなります。|  
|**/bugreport**:`filename`|バグ レポート用の情報を含むファイル (`filename`) を作成します。|  
|**/comp**[`any`]:`text`|アセンブリの Company フィールドに文字列を指定します。 `text` に空白が含まれている場合は、文字列を二重引用符 (" ") で囲みます。 この文字列はアセンブリのカスタム属性であり、リフレクションを使用して表示するために使用できます。<br /><br /> **/win32res** を指定しないと、`text` がそのファイルの `Company` プロパティとしてエクスプローラーに表示されます。 **/win32res** を指定すると、指定したリソース ファイル内の企業情報が `Company` プロパティとしてエクスプローラーに表示されます。<br /><br /> テキストが空の文字列 ("") の場合、Win32 `Company` リソースは単一の空白として表示されます。<br /><br /> **/win32res** を指定した場合は、Win32 リソース情報に対して **/company** は無効になります。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyCompanyAttribute>) として指定することもできます。|  
|**/config**[`uration`]:`text`|アセンブリの Configuration フィールドに文字列を指定します。 `text` に空白が含まれている場合は、文字列を二重引用符 (" ") で囲みます。 この文字列はアセンブリのカスタム属性であり、リフレクションを使用して表示するために使用できます。<br /><br /> テキストが空の文字列の場合、Win32 Configuration リソースは単一の空白として表示されます。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyConfigurationAttribute>) として指定することもできます。|  
|**/copy**[`right`]:`text`|アセンブリの Copyright フィールドに文字列を指定します。 `text` に空白が含まれている場合は、文字列を二重引用符 (" ") で囲みます。 この文字列はアセンブリのカスタム属性であり、リフレクションを使用して表示するために使用できます。<br /><br /> **/win32res** を指定しないと、**/copyright** が Win32 Copyright リソースとしてエクスプローラーに表示されます。<br /><br /> テキストが空の文字列の場合、Win32 Copyright リソースは単一の空白として表示されます。<br /><br /> **/win32res** を指定した場合は、Win32 リソース情報に対して **/copyright** は無効になります。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyCopyrightAttribute>) として指定することもできます。|  
|**/c**[**ulture**]:`text`|アセンブリに関連付けるカルチャ文字列を指定します。 カルチャとして有効な値は、RFC (Internet Requests for Comments) ドキュメント 1766 『Tags for the Identification of Languages』で定義されている値です。<br /><br /> `text` に空白が含まれている場合は、文字列を二重引用符 (" ") で囲みます。 既定のカルチャ文字列はありません。 この文字列は、リフレクションを使用して表示するために使用できます。<br /><br /> 有効な `text` 文字列の詳細については、「<xref:System.Globalization.CultureInfo>」を参照してください。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyCultureAttribute>) として指定することもできます。|  
|**/delay**[`sign`][`+&#124;-`]|アセンブリに完全に署名するか、部分的に署名するかを指定します。 完全署名されたアセンブリを作成する場合は、**/delaysign-** を使用します。 アセンブリに公開キーだけを含める場合は、**/delaysign+** を使用します。<br /><br /> アセンブリに完全に署名するように指定すると、Al.exe はマニフェスト (アセンブリ メタデータ) を含むファイルをハッシュし、秘密キーでそのハッシュに署名します。 結果として得られるデジタル署名は、マニフェストを含むファイルに格納されます。 アセンブリに遅延署名した場合は、署名は算出および格納されず、後で署名を追加できるようにファイル内の空間が予約されます。<br /><br /> 既定値は **/delaysign-** です。<br /><br /> **/delaysign** オプションは、**/keyfile** または **/keyname** と共に使用しない場合、無効になります。<br /><br /> たとえば、**/delaysign+** を指定すると、テスト時にはアセンブリをグローバル キャッシュに格納できます。 テスト後に、アセンブリに秘密キーを含めることにより、そのアセンブリに完全署名できます。<br /><br /> メモ: [Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用して遅延署名アセンブリをグローバル キャッシュに格納する前に、[Sn.exe (厳密名ツール)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を使用してアセンブリを登録して検証をスキップします。 たとえば、`Sn.exe –Vr delaySignedAssembly` のようにします。 これは、開発にのみ使用してください。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyDelaySignAttribute>) として指定することもできます。|  
|**/descr**[**iption**]**:**`text`|アセンブリの <xref:System.Reflection.AssemblyDescriptionAttribute.Description%2A> フィールドに文字列を指定します。 `text` に空白が含まれている場合は、文字列を二重引用符 (" ") で囲みます。 この文字列はアセンブリのカスタム属性であり、リフレクションを使用して表示するために使用できます。<br /><br /> **/win32res** を指定しないと、**/description** が Win32 **Comments** リソースとしてエクスプローラーに表示されます。<br /><br /> テキストが空の文字列の場合、Win32 **Comments** リソースは単一の空白として表示されます。<br /><br /> **/win32res** を指定した場合は、Win32 リソース情報に対して **/description** は無効になります。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyDescriptionAttribute.Description%2A>) として指定することもできます。|  
|**/e[vidence]:** `file`|Security.Evidence のリソース名を持つアセンブリに `file` を埋め込みます。<br /><br /> 通常のリソースに対して Security.Evidence を使用することはできません。|  
|**/fileversion:** `version`|アセンブリの **File Version** フィールドに文字列を指定します。 この文字列はアセンブリのカスタム属性であり、リフレクションを使用して表示するために使用できます。<br /><br /> **/win32res** を指定しないと、**/fileversion** が Win32 **File Version** リソースとして使用されます。 **/fileversion** を指定しないと、Win32 **Assembly Version** リソースによって Win32 **File Version** リソースが設定されます。<br /><br /> **/win32res** を指定した場合は、Win32 リソースに対して **/fileversion** は無効になります。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (AssemblyFileVersionAttribute) として指定することもできます。|  
|**/flags:** `flags`|アセンブリの `Flags` フィールドに値を指定します。 `flags` に指定できる値は次のとおりです。<br /><br /> 0x0000<br /> アセンブリは side-by-side 実行をサポートしています。<br /><br /> 0x0010<br /> アセンブリは別のバージョンが同じアプリケーション ドメインで実行されている場合には実行できません。<br /><br /> 0x0020<br /> アセンブリは別のバージョンが同じプロセスで実行されている場合には実行できません。<br /><br /> 0x0030<br /> アセンブリは別のバージョンが同じコンピューターで実行されている場合には実行できません。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyFlagsAttribute>) として指定することもできます。|  
|**/fullpaths**|エラー メッセージで報告されるすべてのファイルについて、Al.exe が絶対パスを使用するように指定します。|  
|**/help**|このツールのコマンド構文とオプションを表示します。|  
|**/keyf[ile]:** `filename`|アセンブリに署名するためのキー ペアまたは公開キーだけを含むファイル (`filename`) を指定します。 コンパイラは、アセンブリ マニフェストに公開キーを挿入し、最終的なアセンブリに秘密キーで署名します。 キー ファイルの生成、およびキー コンテナーへのキー ペアのインストールについては、「[厳密名ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)」を参照してください。<br /><br /> 遅延署名を使用する場合は、通常、このファイルには公開キーだけが含まれ、秘密キーは含まれません。<br /><br /> キー ペアの公開キー情報は、アセンブリの .publickey フィールドに表示されます。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyKeyFileAttribute>) として指定することもできます。<br /><br /> 同じコンパイルで、コマンド ライン オプションまたはカスタム属性によって **/keyfile** と **/keyname** の両方が指定された場合、Al.exe はまず、**/keyname** で指定されたコンテナーを検索します。 成功すると、キー コンテナー内の情報を使用して、アセンブリが署名されます。 キー コンテナーを検出できなかった場合、Al.exe は **/keyfile** で指定されたファイルを検索します。 ファイルが検出された場合、アセンブリはキー ファイルの情報で署名され、キー情報はキー コンテナーにインストールされるため ([Sn.exe](../../../docs/framework/tools/sn-exe-strong-name-tool.md) の -i オプションと同様)、次のコンパイル時には **/keyname** オプションが有効となります。|  
|**/keyn[ame]:** `text`|キー ペアを保持するコンテナーを指定します。 これにより、公開キーがアセンブリ マニフェストに挿入され、アセンブリに署名 (厳密な名前が指定) されます。 次に、Al.exe は最終的なアセンブリに秘密キーで署名します。<br /><br /> Sn.exe を使用して、キー ペアを生成します。<br /><br /> キー情報は、アセンブリの .publickey フィールドに表示されます。<br /><br /> 空白が埋め込まれている場合は、`text` を二重引用符 (" ") で囲みます。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyKeyNameAttribute>) として指定することもできます。|  
|**/main:** `method`|モジュールを実行可能ファイルに変換するときに、エントリ ポイントとして使用するメソッドの完全修飾名 (`class`.`method`) を指定します。|  
|**/nologo**|Al.exe の起動時に、著作権情報またはロゴをコマンド ラインに表示しないようにします。|  
|**/out:** `filename`|Al.exe で作成されるファイルの名前を指定します。 これは必須オプションです。|  
|**/platform**:`text`|コードを実行できるプラットフォームを制限します。x86、Itanium、x64、anycpu (既定値)、anycpu32bitpreferred のいずれかである必要があります。|  
|**/prod[uct]:** `text`|アセンブリの **Product** フィールドに文字列を指定します。 `text` に空白が含まれている場合は、文字列を二重引用符 (" ") で囲みます。 この文字列はアセンブリのカスタム属性であり、リフレクションを使用して表示するために使用できます。<br /><br /> **/win32res** を指定しないと、**/product** が Win32 **Product Name** リソースとしてエクスプローラーに表示されます。<br /><br /> テキストが空の文字列の場合、Win32 **Product Name** リソースは単一の空白として表示されます。<br /><br /> **/win32res** を指定した場合は、Win32 リソース情報に対して **/product** は無効になります。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyProductAttribute>) として指定することもできます。|  
|**/productv[ersion]:** `text`|アセンブリの **Product Version** フィールドに文字列を指定します。 `text` に空白が含まれている場合は、文字列を二重引用符 (" ") で囲みます。 この文字列はアセンブリのカスタム属性であり、リフレクションを使用して表示するために使用できます。<br /><br /> **/win32res** を指定しないと、**/productversion** が Win32 **Product Version** リソースとして使用されます。 **/productversion** を指定しないと、Win32 **File Version** リソースによって Win32 **Product Version** リソースが設定されます。<br /><br /> **/win32res** を指定した場合は、Win32 リソース情報に対して **/productversion** は無効になります。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyInformationalVersionAttribute>) として指定することもできます。|  
|**/t[arget]:lib[rary] &#124; exe &#124; win[exe]**|出力ファイルのファイル形式として、`lib`rary (コード ライブラリ)、`exe` (コンソール アプリケーション)、または `win`exe (Windows ベースのアプリケーション) を指定します。 既定値は lib[rary] です。|  
|**/template:** `filename`|カルチャ フィールドを除く、すべてのアセンブリ メタデータの継承元であるアセンブリ (`filename`) を指定します。<br /><br /> **/template** を指定して作成したアセンブリは、サテライト アセンブリになります。|  
|**/title:** `text`|アセンブリの **Title** フィールドに文字列を指定します。 `text` に空白が含まれている場合は、文字列を二重引用符 (" ") で囲みます。 この文字列はアセンブリのカスタム属性であり、リフレクションを使用して表示するために使用できます。<br /><br /> **/win32res** を指定しないと、**/title** が Win32 **Description** リソースとしてエクスプローラーに表示され、アプリケーションのフレンドリ名としてシェルによって使用されます。 この文字列は、複数のアプリケーションでサポートされる種類のファイルに対するショートカット メニューの **[ファイルを開くアプリケーションの選択]** サブメニューにも表示されます。<br /><br /> テキストが空の文字列の場合、Win32 **Description** リソースは単一の空白として表示されます。<br /><br /> **/win32res** を指定した場合は、Win32 リソース情報に対して **/title** は無効になります。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyTitleAttribute>) として指定することもできます。|  
|**/trade[mark]:** `text`|アセンブリの **Trademark** フィールドに文字列を指定します。 `text` に空白が含まれている場合は、文字列を二重引用符 (" ") で囲みます。 この文字列はアセンブリのカスタム属性であり、リフレクションを使用して表示するために使用できます。<br /><br /> **/win32res** を指定しないと、**/trademark** が Win32 **Trademark** リソースとしてエクスプローラーに表示されます。<br /><br /> テキストが空の文字列の場合、Win32 **Trademark** リソースは単一の空白として表示されます。<br /><br /> **/win32res** を指定した場合は、Win32 リソース情報に対して **/trademark** は無効になります。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyTrademarkAttribute>) として指定することもできます。|  
|**/v[ersion]:** `version`|アセンブリのバージョン情報を指定します。 バージョン文字列の形式は `major`.`minor`.`build`.`revision` です。 既定値は 0 です。<br /><br /> **/version** を指定する場合、`major` も指定する必要があります。 `major` と `minor` を指定する場合、`build` に対してアスタリスク (\*) を指定できます。 その場合、`build` は現地時間の 2000 年 1 月 1 日以降の経過日数と等しい値になり、`revision` は現地時間の当日の午前 0 時以降の経過秒数を 2 で割った値と等しくなります。<br /><br /> `major`、`minor`、および `build` を指定する場合、`revision` に対してアスタリスクを指定できます。 その場合、`revision` は現地時間の当日の午前 0 時以降の経過秒数を 2 で割った値と等しくなります。<br /><br /> まとめると、有効なバージョン文字列は次のようになります。<br /><br /> X<br /><br /> X.X<br /><br /> X.X.\*<br /><br /> X.X.X<br /><br /> X.X.X.\*<br /><br /> X.X.X.X<br /><br /> X は 65535 を除く unsigned short 定数 (0 ～ 65534) です。<br /><br /> **/win32res** を指定しないと、**/version** が Win32 **Assembly Version** リソースとして使用されます。<br /><br /> **/win32res**、**/productversion**、および **/fileversion** を指定しない場合、**/version** が **Assembly Version**、File Version、および **Product Version** Win32 リソースに対して使用されます。<br /><br /> **/win32res** を指定した場合は、Win32 リソース情報に対して **/version** は無効になります。<br /><br /> このオプションは、任意の MSIL モジュールのソース コードでカスタム属性 (<xref:System.Reflection.AssemblyVersionAttribute>) として指定することもできます。|  
|**/win32icon:** `filename`|.ico ファイルをアセンブリに挿入します。 この .ico ファイルは、エクスプローラーにおける出力ファイルの視覚的な表現を提供します。|  
|**/win32res:** `filename`|Win32 リソース (.res ファイル) を出力ファイルに挿入します。 Win32 リソース ファイルは、リソース コンパイラを使用して作成できます。 リソース コンパイラは、Visual C++ プログラムをコンパイルするときに呼び出されます。.res ファイルは .rc ファイルから作成されます。|  
|`@filename`|Al.exe コマンドが格納されている応答ファイルを指定します。<br /><br /> 応答ファイルでは、コマンドは各行に 1 つずつ指定されるか、複数のコマンドが 1 行に空白で区切られて指定されます。|  
|**/?**|このツールのコマンド構文とオプションを表示します。|  
  
## <a name="remarks"></a>コメント  
 すべての Visual Studio コンパイラは、アセンブリを生成します。 ただし、モジュール (マニフェストを含まないメタデータ) が 1 つ以上ある場合は、Al.exe を使用して、マニフェストを別個のファイルに含むアセンブリを作成できます。  
  
 アセンブリのキャッシュへのインストール、キャッシュからの削除、およびキャッシュの内容の一覧表示を実行するには、[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用します。  
  
## <a name="errors-and-warnings"></a>エラーと警告  
 Al.exe で発生するエラーの一覧を次の表に示します。  
  
|エラー|説明|  
|-----------|-----------------|  
|al1001|内部コンパイル エラー<br /><br /> エラーの発生原因が、予期しない構文を解析できなかったためかどうかを調べてください。 その後、マイクロソフト製品 サポート サービスにお問い合わせください。|  
|al1002|メモリが不足しています<br /><br /> Al.exe がメモリ不足のため、停止しました。 使用できるメモリの容量を増やしてください。|  
|al1003|コンパイラ オプション 'option' の後には引数が必要です。<br /><br /> コマンド ライン オプションに引数を渡す必要があります。 たとえば、**/algid:** を指定した場合は、アルゴリズム識別子を渡す必要があります。|  
|al1004|予期しない共通言語ランタイム初期化エラーです — '理由'<br /><br /> メッセージに示された原因により、Visual Studio または共通言語ランタイムのインストールに関するエラーが発生しました。|  
|al1005|ファイル 'file' のサイズが大きすぎて開けません<br /><br /> Al.exe で開くファイルは、4 ギガバイト (GB) 未満であることが必要です。|  
|al1006|応答ファイル 'file' は既に含まれています<br /><br /> 同じ応答ファイルが、コマンド ライン (`@file`) で複数回指定されました。 応答ファイルを指定できるのは 1 回だけです。|  
|al1007|応答ファイル 'file' を開いているときにエラーが発生しました -- '理由'<br /><br /> メッセージに示された原因により、指定された応答ファイルを開くことができません。|  
|al1008|'option' コマンド ライン オプションに対するファイル指定がありません。<br /><br /> コマンド ライン オプションにファイルを渡す必要があります。 たとえば、**/out** オプションを指定する場合は、ファイルを指定する必要があります。|  
|al1009|'file' を書き込むために開くことができません<br /><br /> 出力アセンブリ ファイルなどのファイルに書き込みできませんでした。 ディスクがいっぱいである、ファイルが読み取り専用である、ファイルに対するアクセス許可がないなどの理由が考えられます。|  
|al1010|コマンドライン構文エラー: 'option' オプションの ':text' がありません<br /><br /> コマンド ライン オプションに引数を渡す必要があります。 たとえば、**/title** オプションを指定する場合は、文字列を渡す必要があります。|  
|al1011|ファイル 'file' は実行可能ファイルです。テキスト ファイルとして開くことはできません<br /><br /> テキスト ファイルを指定する必要があるところにバイナリ ファイルが指定されました。 たとえば、コマンド ラインで応答ファイルとしてバイナリ ファイルが渡されると、このエラーが発生します。|  
|al1012|'value' はオプション 'option' に対する有効な設定ではありません<br /><br /> コマンド ライン オプションに予期しない値が渡されました。 たとえば、**/target** オプションに無効な値を指定すると、このエラーが発生します。|  
|al1013|認識できないコマンド ライン オプション : 'option'<br /><br /> 指定されたコマンド ライン オプションが無効です。|  
|al1014|予期しない初期化エラーです — '理由'<br /><br /> COM を初期化できなかったことが検出されました。 このエラーの原因としては、メモリ不足も考えられますが、システム DLL ファイルが原因であるケースが一般的です。 この場合、オートメーションや COM に対応したプログラム (Microsoft Visual Studio など) を実行する場合にも類似のエラーが発生するはずです。<br /><br /> オペレーティング システムを再インストールしてください。|  
|al1015|メッセージ ファイル 'alinkui.dll' が見つかりません<br /><br /> Al.exe には Alinkui.dll が必要です。 このファイルがパス上にあるかどうかを確認してください。 必要な場合は、製品 CD から Alinkui.dll をコピーしてください。|  
|al1016|有効な入力ファイルが指定されませんでした<br /><br /> アセンブリ情報を含んでいない 1 つ以上の入力ファイルを指定する必要があります。|  
|al1017|ターゲット ファイル名が指定されませんでした<br /><br /> ターゲット ファイル名の指定に必要な **/out** オプションが存在しませんでした。|  
|al1018|必要なファイル 'file' を読み込めませんでした<br /><br /> 特定の DLL ファイルを読み込めません。 Visual Studio または [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] を再インストールしてください。|  
|al1019|アセンブリを作成中にメタデータが失敗しました — 理由<br /><br /> メッセージに示された原因により、アセンブリの生成が中断されました。 たとえば、**/win32res** オプションで指定したファイルが見つからない場合に、このエラーが発生します。|  
|al1020|含まれているアセンブリ 'file' を無視します<br /><br /> 指定した入力ファイルにアセンブリが含まれています。 アセンブリを含むファイルを Al.exe 入力ファイルとして指定することはできません。|  
|al1021|'設定' : 今までの設定をオーバーライドしています<br /><br /> モジュールには、カスタム属性によって割り当てられた可能性のある特定の設定について値が指定されていましたが、Al.exe コマンド ライン オプションを使用して渡された値によって、この値がオーバーライドされました。|  
|al1022|埋め込みリソース 'file' の読み込みエラーです — 理由<br /><br /> メッセージに示された原因により、**/embedresource** オプションに渡されたファイルを読み取ることができません。|  
|al1023|リソース 'file' の埋め込みエラーです — 理由<br /><br /> メッセージに示された原因により、オペレーティング システムがアセンブリにリソース ファイルを埋め込めません。|  
|al1025|ComType レコード 'record' は無効なファイル レコード 'record' を指しています<br /><br /> 入力モジュール内のメタデータが無効です。 モジュールを作成したツールを修復する必要があります。|  
|al1026|指定されたバージョン 'version' は無効です<br /><br /> 有効な形式については、**/version** オプションの説明を参照してください。|  
|al1028|キー ファイル 'file' は署名に必要な秘密キーがありません<br /><br /> 公開キーだけを保持したキー ファイルが **/keyfile** オプションに渡されました。 [厳密名ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) で次のようなコマンドを使用して、公開キーと秘密キーの両方を含むファイルを生成してください。<br /><br /> `sn -k keypair.snk.`|  
|al1029|キーのコンテナー名 'container' は存在しません<br /><br /> **/keyname** オプションに渡された値が有効なコンテナーではありません。 [厳密名ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を使用してコンテナーを作成してください。|  
|al1030|適切な暗号サービスが正しくインストールされていないか、適切なキー プロバイダーがありません<br /><br /> 多くの場合は、オペレーティング システムを再インストールするか、キーの作成に使用した暗号ユーティリティをインストールする必要があります。|  
|al1031|アイコン 'file' を読み込み中にエラーが発生しました— 理由<br /><br /> メッセージに示された原因により、**/win32icon** オプションに渡されたファイルを読み取ることができません。|  
|al1032|'file' のリソースを生成中にエラーが発生しました — 理由<br /><br /> ディスク容量の不足またはその他のエラーが原因でファイルを作成できません。 .ico ファイルを生成する **/win32icon** オプションを指定した場合や、リソース情報を持つファイルを生成する **/win32res** オプションを指定しなかった場合に、このエラーが発生します。<br /><br /> ファイル生成に関するこの問題を解決できない場合は、**/win32res** を使用してください。/win32res は、バージョン情報やビットマップ (アイコン) 情報を含むファイルを指定します。|  
|al1033|アセンブリ カスタム属性 'attribute' が異なる値で複数回指定されました<br /><br /> Al.exe に対する入力ファイルとして指定されたソース モジュール内で、同じカスタム属性が 2 回使用されており、それぞれに異なる値が渡されています。|  
|al1034|アセンブリ 'file' のコピーおよび名前の変更はできません<br /><br /> 入力ファイルの指定やコピーを実行できる Al.exe 構文を使用しているときに、名前の競合が発生し、コンパイラが停止しました。 たとえば、`input.dll,somename.dll /out:somename.dll` と指定すると、このエラーが発生します。|  
|al1035|ライブラリはエントリ ポイントを持てません<br /><br /> **/target:lib** オプション (既定値) と **/main** オプションは同時には指定できません。|  
|al1036|実行可能アプリケーションにエントリ ポイントが必要です<br /><br /> **/target:exe** オプションまたは **/target:win** オプションを使用する場合は、**/main** オプションも指定する必要があります。|  
|al1037|エントリ ポイント メソッド 'main' が見つかりません<br /><br /> **/main** オプションで指定された位置に `Main` メソッドが見つかりません。|  
|al1039|グローバル アセンブリ キャッシュ マネージャーの初期化に失敗しました — 理由<br /><br /> Visual Studio または [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)] を再インストールしてください。|  
|al1040|キャッシュにアセンブリをインストールできませんでした — 理由<br /><br /> キャッシュにインストールできるのは署名されたアセンブリだけです。 詳細については、「[グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)」を参照してください。|  
|al1041|'method' : 署名または表示が正しくないか、ジェネリックであるため、エントリ ポイントになれません。<br /><br /> **/main** オプションで指定されたメソッドが、静的メソッドでないか、`int` または `void` を返さないか、ジェネリックであったか、無効な引数が含まれています。|  
|al1042|'exe': EXE を追加モジュールにすることはできません<br /><br /> アセンブリを含まない .exe ファイルが、Al.exe への入力ファイルとして指定されました。 Al.exe で入力ファイルとして指定できるのは、アセンブリを含まない .dll ファイルだけです。|  
|al1043|マニフェスト ファイル名 'name' をモジュール名と同じにすることはできません<br /><br /> **/out** オプションで指定する名前は、Al.exe に対する入力ファイルとして指定されるファイルと同じ名前にすることはできません。|  
|al1044|キー ファイル 'file' の読み込み中にエラーが発生しました -- 理由<br /><br /> **/keyfile** または <xref:System.Reflection.AssemblyKeyFileAttribute> で指定したファイルを開いているとき、または読み取っているときに、エラーが発生しました。|  
|al1045|ファイル名 'file' が長すぎるか無効です<br /><br /> 260 文字より長いファイル名が Al.exe に渡されました。 それよりも文字数の少ないファイル名または短いパスを選択するか、ファイルの名前を変更してください。|  
|al1046|リソース識別子 'ID' はアセンブリで既に使用されています<br /><br /> 埋め込まれたかリンクされた 2 つのリソースの ID または名前 (2 番目の引数) が同じです。 競合するリソースのうちのいずれか 1 つを削除するか、名前を変更してください。|  
|al1047|ファイル 'file' のインポート中にエラーが発生しました — 理由 <br /><br /> メッセージに示された原因により、モジュール ファイルを開くことができません。|  
|al1048|アセンブリ 'assembly' のモジュール 'module' のインポート中にエラーが発生しました -- 理由<br /><br /> マルチファイル アセンブリの非マニフェスト ファイルを開いているときにエラーが発生しました。 このエラーは、Al.exe によって直接は出力されませんが、プログラムによって、Al.exe を使用するプロセスに渡すことができます。|  
|al1049|2000 年 1 月 1 日以前のビルドとリビジョン バージョン番号は自動生成できません。<br /><br /> コンピューターのシステム時計が 2000 年 1 月 1 日よりも前の日付に設定されています。|  
|al1050|使用している機能 'old feature' は現在サポートされていません。'new feature' を代わりに使用してください。<br /><br /> Al.exe によって以前にサポートされていた機能がサポートされなくなっています。 代わりとして推奨されている機能を使用してください。|  
|al1051|'attribute' 属性を作成時にエラーが発生しました — 理由<br /><br /> メッセージに示された原因により、アセンブリのカスタム属性が処理されませんでした。|  
|al1052|ファイル 'filename' はアセンブリではありません<br /><br /> **/template** で指定したファイルには、アセンブリ メタデータが含まれている必要があります。 このエラーは、**/template** で指定したファイルにアセンブリが含まれていないことを示します。|  
|al1053|'option' に指定されたバージョン 'version' は正常な 'major.minor.build.revision' フォーマットではありません<br /><br /> **/fileversion** オプションまたは **/productversion** オプションで指定されたバージョン情報の形式が正しくないことが検出されました。|  
|al1054|'option' に指定されたバージョン 'version' は正常な 'major.minor.build.revision' フォーマットではありません<br /><br /> <xref:System.Resources.SatelliteContractVersionAttribute> で指定されたバージョン情報が不正であることが検出されました。|  
|al1055|参照されたアセンブリ 'filename' は厳密な名前を持っていません<br /><br /> このエラーは、厳密な名前を持つアセンブリを作成するときに、厳密な名前を持たないアセンブリを参照した場合に発生します。 これを解決するには、厳密な名前でアセンブリを再生成するか、sn.exe を使用してアセンブリに厳密な名前を追加する必要があります ([sn.exe](../../../docs/framework/tools/sn-exe-strong-name-tool.md) についてのドキュメントを参照してください)。<br /><br /> このエラーは、一般的には COM モジュールへの参照を Visual Studio IDE を介して C# プロジェクトに追加するときなど、ラッパー アセンブリを介して COM オブジェクトを使用しているときに発生します。 このエラーを回避するために、プロジェクト プロパティ "Wrapper Assembly Key File/Name" で COM ラッパー アセンブリに対して厳密な名前のキー ファイルを指定できます。<br /><br /> tlbimp を介してラッパー アセンブリを作成する場合、厳密な名前をラッパー アセンブリに割り当てる方法については [tlbimp](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) ドキュメントを参照してください。<br /><br /> アセンブリが厳密な名前を持つ場合、そのアセンブリはグローバル アセンブリ キャッシュにインストールできます。 したがって、参照されるアセンブリもグローバル アセンブリ キャッシュに格納する必要があります。 グローバル アセンブリ キャッシュには、厳密な名前を持つアセンブしか格納できません。|  
|al1056|参照されたアセンブリ 'filename' はローカライズされたサテライト アセンブリです<br /><br /> <xref:System.Reflection.AssemblyCultureAttribute> 属性を使用して作成されたアセンブリが、現在のアセンブリの作成時に参照されました。 <xref:System.Reflection.AssemblyCultureAttribute> 属性は、ファイルがローカライズされたサテライト アセンブリであることを示します。サテライト アセンブリを参照することは、適切ではありません。 多くの場合、代わりにメインの親アセンブリを参照する必要があります。|  
|al1057|実行可能ファイルはローカライズできません。カルチャは常に空でなければなりません<br /><br /> アセンブリが **/target:exe** で作成されているのに、**/culture** が指定されています。 .exe 内のアセンブリには、Culture フィールド内の情報を含むことができません。|  
|al1058|'file' はアセンブリです。モジュールとして追加することはできません<br /><br /> C++ のコンパイルで、**/assemblymodule** (リンカー オプション) がアセンブリを含むファイルに渡されました。|  
|al1059|不明なエラー (コード)<br /><br /> Al.exe が不明なエラー コード (`code`) を受け取りました。<br /><br /> 解決策として次の方法が挙げられます。<br /><br /> Visual Studio を再インストールしてください。<br /><br /> [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)] を再インストールします。<br /><br /> ファイルが不足していないかどうかを確認します。<br /><br /> 十分なディスク容量があるかどうかを確認します。<br /><br /> 十分なメモリがあるかどうかを確認します。<br /><br /> 同じファイルにアクセスしている可能性のある他のプロセスを停止します。<br /><br /> コンピューターを再起動します。|  
|al1060|ハッシュを作成中に暗号化に失敗しました — 理由<br /><br /> マルチファイルのアセンブリのファイル ハッシュを作成中にエラーが発生しました。|  
|al1061|'reason' のため、オプション 'option' を設定できません<br /><br /> メッセージに示された理由により、このオプションに指定された値は無効です。|  
|al1062|モジュール 'module' が複数回指定されました。指定できるのは 1 回だけです<br /><br /> この警告は、コマンド ラインで同じソース ファイル、入力ファイル、またはモジュール ファイルを複数回指定した場合に発生します。 ファイル名は 1 回だけ指定してください。|  
|al1063|パブリック型 'type' がこのアセンブリ内の複数の場所で定義されています: 'file1' および 'file2'<br /><br /> アセンブリ内の複数のモジュールで、同じ型が見つかりました。 それぞれの型では、1 つのバージョンのみがアセンブリに存在できます。|  
|al1064|複数の /bugreport オプションを指定することはできません<br /><br /> **/bugreport** オプションは 1 つしか指定できません。|  
|al1065|ファイル名 'File Name' が長すぎるか無効です<br /><br /> 指定されたファイル名が許可される最大値を超えています。|  
|al1066|文字 'character' は、コマンド ラインまたは応答ファイルに許可されていません<br /><br /> コマンド ラインまたはファイル内に、無効な文字が見つかりました。|  
|al1067|'filename' はテキスト ファイルではなく、バイナリ ファイルです<br /><br /> ファイルはテキストではなく、バイナリ形式です。|  
|al1068|モジュール 'ModuleName' はこのアセンブリ内で既に定義されています。 リンクされた各リソースおよびモジュールには一意のファイル名を指定しなければなりません。<br /><br /> モジュールが、このアセンブリに複数回現れています。|  
|al1069|同じ短いファイル名を使用している長いファイル名が既に存在するとき、短いファイル名 'filename' を作成することはできません<br /><br /> 現在のファイルには、既に存在するファイル名の短いバージョンの名前が付いています。 たとえば、LongFileName.cs をコンパイルしてから LongFi~1.cs という名前で再コンパイルすると、これに似たコンパイラ エラーが発生します。 名前が長いコンパイラ出力ファイルが削除されても、類似のリンカー ファイルが残っていると、このエラーが発生することがあります。|  
|al1070|agnostic なアセンブリにプロセッサ固有モジュール 'Module Name' を指定することはできません<br /><br /> **/platform:agnostic** を使用して (または、**/platform** を指定しないで) ビルドしている場合、**/addmodule** を使用して、agnostic ではないモジュールを追加しようとすると、エラーが発生します。 これは、i386 obj ファイルから ia64 obj ファイルにリンクを試みているのに似ています。<br /><br /> agnostic でないモジュールの主なソースは C++ です。 C++ モジュールで **/addmodule** を使用する場合、ビルド スクリプトを変更して適切な **/platform** 設定を指定する必要があります。|  
|al1072|アセンブリとモジュール 'Module Name' は、異なるプロセッサを対象にすることはできません<br /><br /> 異なるプロセッサを対象とするアセンブリとモジュールをリンクすることはできません。結果は 1 つのプロセッサで実行する必要があります。|  
|al1073|参照アセンブリ 'assembly' は異なるプロセッサを対象にしています<br /><br /> 異なるプロセッサを対象とする複数のアセンブリをリンクすることはできません。結果は 1 つのプロセッサで実行する必要があります。|  
|al1074|'File Name' に格納されているモジュール名 'Module Name' は、そのファイル名と一致していなければなりません<br /><br /> これは、リンカーで必要とされる条件です。 この問題を解決するには、2 つの名前が一致するようにします。|  
|al1075|遅延署名が要求されましたが、キーが指定されませんでした<br /><br /> アセンブリを遅延署名に設定すると、コンパイラは署名の計算も格納も行いませんが、後で署名を追加できるようにファイルに領域を確保します。<br /><br /> たとえば、**/delaysign+** を指定すると、テスト時にはアセンブリをグローバル キャッシュに格納できます。 テスト後に、アセンブリ リンカー ユーティリティを使用してアセンブリに秘密キーを追加することにより、そのアセンブリに完全署名できます。|  
|al1076|型 'type' は複数のアセンブリに転送されています: 'assembly' および 'assembly'<br /><br /> 型は 1 つのアセンブリにのみ転送できます。|  
|al1077|パブリック型 'type' は 'assembly' で定義され、'assembly' に転送されています。<br /><br /> 生成するアセンブリに重複するパブリック型があります。 1 つが有効な型定義で、その他は型フォワーダーです。|  
  
## <a name="example"></a>例  
 `t2a.exe` モジュールからアセンブリを含む実行可能ファイル `t2.netmodule` を作成するコマンドを次に示します。 エントリ ポイントは、`Main` 内の `MyClass` メソッドです。  
  
```  
al t2.netmodule /target:exe /out:t2a.exe /main:MyClass.Main  
```  
  
## <a name="see-also"></a>関連項目  
 [ツール](../../../docs/framework/tools/index.md)   
 [Sn.exe (厳密名ツール)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)   
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)