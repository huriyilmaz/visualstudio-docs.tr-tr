---
title: Kod parçacıkları şema başvurusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9f105406888a9bf17899a4d47305cc1ed20d763f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620106"
---
# <a name="code-snippets-schema-reference"></a>Kod Parçacıkları Şema Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense kod parçacıkları, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Uygulamanıza eklenmeye hazırlanan önceden yazılmış kod parçalarıdır. Yinelenen kodları yazmak veya örnekleri aramak için harcanan süreyi kısaltan kod parçacıkları sağlayarak üretkenliği artırabilirsiniz. Kendi kod parçacıklarını oluşturmak için IntelliSense kod parçacığı XML şemasını kullanabilir ve bunları [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zaten içerdiği kod parçacıklarına ekleyebilirsiniz.

## <a name="intellisense-code-snippets-schema-elements"></a>IntelliSense Kod Parçacıkları Şeması Öğeleri

||||
|-|-|-|
|[Assembly öğesi](../ide/code-snippets-schema-reference.md#assembly)|[HelpUrl öğesi](../ide/code-snippets-schema-reference.md#helpurl)|[References öğesi](../ide/code-snippets-schema-reference.md#references)|
|[Author öğesi](../ide/code-snippets-schema-reference.md#author)|[ID öğesi](../ide/code-snippets-schema-reference.md#id)|[Shortcut öğesi](../ide/code-snippets-schema-reference.md#shortcut)|
|[Kod öğesi](../ide/code-snippets-schema-reference.md#code)|[İçeri aktarma öğesi](../ide/code-snippets-schema-reference.md#import)|[Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#snippet)|
|[Codeparçacığının öğesi](../ide/code-snippets-schema-reference.md#codesnippet)|[Imports öğesi](../ide/code-snippets-schema-reference.md#imports)|[SnippetType Öğesi](../ide/code-snippets-schema-reference.md#snippettype)|
|[Codeparçacıklar öğesi](../ide/code-snippets-schema-reference.md#codesnippets)|[Anahtar sözcük öğesi](../ide/code-snippets-schema-reference.md#keyword)|[SnippetTypes öğesi](../ide/code-snippets-schema-reference.md#snippettypes)|
|[Bildirimleri öğesi](../ide/code-snippets-schema-reference.md#declarations)|[Keywords öğesi](../ide/code-snippets-schema-reference.md#keywords)|[Title öğesi](../ide/code-snippets-schema-reference.md#title)|
|[Varsayılan öğe](../ide/code-snippets-schema-reference.md#default)|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|[ToolTip öğesi](../ide/code-snippets-schema-reference.md#tooltip)|
|[Description öğesi](../ide/code-snippets-schema-reference.md#description)|[Namespace öğesi](../ide/code-snippets-schema-reference.md#namespace)|[Type öğesi](../ide/code-snippets-schema-reference.md#type)|
|[Function öğesi](../ide/code-snippets-schema-reference.md#function)|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object)|[URL öğesi](../ide/code-snippets-schema-reference.md#url)|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|[Reference öğesi](../ide/code-snippets-schema-reference.md#reference)||

## <a name="assembly"></a>Assembly öğesi
 Kod parçacığının başvurduğu derlemenin adını belirtir.

> [!NOTE]
> @No__t_0 öğesi yalnızca Visual Basic kod parçacıkları tarafından desteklenir.

 **Derleme** öğesinin metin değeri, `System.dll` veya `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1` gibi tanımlayıcı adı gibi derlemenin kolay metin adıdır.

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Reference öğesi](../ide/code-snippets-schema-reference.md#reference)|Kod parçacığının gerek duyduğu derleme başvuruları hakkındaki bilgileri içerir.|

 Bir metin değeri gereklidir. Bu metin, kod parçacığının başvurduğu derlemeyi belirtir.

## <a name="author"></a>Author öğesi
 Kod parçacığı yazarının adını belirtir. **Kod parçacıkları Yöneticisi** , kod parçacığının `Author` öğesinde depolanan adı görüntüler.

```xml
<Author>
   Code Snippet Author
</Author>

```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler içerir.|

 Bir metin değeri gereklidir. Bu metin kod parçacığının yazarını belirtir.

## <a name="code"></a>Kod öğesi
 Kısa kod blokları için bir kapsayıcı sağlar.

 @No__t_0 öğenin metninde kullanılabilecek iki ayrılmış sözcük vardır: `$end$` ve `$selected$`. `$end$`, kod parçacığı eklendikten sonra imlecin yerleştirileceği konumu işaretler. `$selected$`, çağrıldığında, çağrıldığında kod parçacığına eklenecek metni temsil eder. Örneğin, şunları içeren bir kod parçacığı verilmiştir:

```xml
$selected$ is a great color.
```

 Kullanıcı şablonu çağırdığında "mavi" sözcüğü seçilirse sonuç şu olur:

```xml
Blue is a great color.
```

 Kod parçacığında `$end$` ya da `$selected$` birden çok kez kullanamazsınız. Bunu yaparsanız yalnızca ikinci örnek tanınır. Şunu içeren bir kod parçacığı verildi:

```
$selected$ is a great color. I love $selected$.
```

 "Mavi" sözcüğü seçilirse sonuç şu olur:

```
is a great color. I love Blue.
```

 @No__t_0 ile `is` arasında boşluk olduğundan, başlangıç alanı görüntülenir.

 Diğer tüm `$` anahtar sözcükleri `<Literal>` ve `<Object>` etiketlerinde dinamik olarak tanımlanmıştır.

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Delimiter`|İsteğe bağlı öznitelik. Kod içindeki değişmez değerleri ve nesneleri açıklamak için kullanılan sınırlayıcıyı belirtir. Varsayılan olarak, sınırlayıcı `$`.|
|`Kind`|İsteğe bağlı öznitelik. Kod parçacığının içerdiği kod türünü ve kod parçacığının derlenmesi için bir kod parçacığının araya eklenmesi gereken konumu belirtir. Kullanılabilir değerler `method body`, `method decl`, `type decl`, `file` ve `any`.|
|`Language`|Gerekli öznitelik. Kod parçacığının dilini belirtir.|

|Tür Öznitelik Değeri|Açıklama|
|--------------------------|-----------------|
|`method body`|Kod parçacığının bir yöntem gövdesi olduğunu ve bu nedenle, bir yöntem bildiriminin içine eklenmesi gerektiğini belirtir.|
|`method decl`|Kod parçacığının bir yöntem olduğunu ve bu nedenle, bir sınıf veya modül içine eklenmesi gerektiğini belirtir.|
|`type decl`|Kod parçacığının bir tür olduğunu ve bu nedenle, bir sınıf, modül veya ad alanı içine eklenmesi gerektiğini belirtir.|
|`file`|Kod parçacığının eksiksiz bir kod dosyası olduğunu belirtir. Bu kod parçacıkları tek başına bir kod dosyasının içine veya bir ad alanının içine eklenebilir.|
|`any`|Kod parçacığının istenen yere eklenebileceğini belirtir. Bu etiket, açıklamalar gibi içeriğe bağımlı kod parçacıkları için kullanılır.|

|Dil Özniteliği Değeri|Açıklama|
|------------------------------|-----------------|
|`VB`|Bir Visual Basic kod parçacığını tanımlar.|
|`CSharp`|Bir C# kod parçacığını tanımlar.|
|`CPP`|Bir C++ kod parçacığını tanımlar.|
|`XML`|Bir XML kod parçacığını tanımlar.|
|`JavaScript`|Bir JavaScript kod parçacığını tanımlar.|
|`SQL`|Bir SQL kod parçacığını tanımlar.|
|`HTML`|Bir HTML kod parçacığını tanımlar.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#snippet)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

 Bir metin değeri gereklidir. Bu metin, bu kod parçacığı bir projeye eklendiğinde kullanabileceğiniz değişmez değerler ve nesnelerle birlikte kodu belirtir.

## <a name="codesnippet"></a>Codeparçacığının öğesi
 Visual Studio kod dosyalarına ekleyebileceğiniz bir başlık ve birden fazla IntelliSense Kod Parçacığı belirtmenizi sağlar.

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>

```

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Format`|Gerekli öznitelik. Kod parçacığının şema sürümünü belirtir. Format özniteliği, her "x"in sürüm numarasına ait sayısal bir değeri temsil ettiği x.x.x sözdiziminde bir dize olmalıdır. Visual Studio, anlamadığını `Format` öznitelikleri olan kod parçacıklarını yok sayar.|

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Gerekli öğe. Kod parçacığı hakkında genel bilgiler içerir. Kod parçacığında tam olarak bir `Header` öğesi olmalıdır.|
|[Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#snippet)|Gerekli öğe. Visual Studio tarafından eklenecek kodu içerir. Kod parçacığında tam olarak bir `Snippet` öğesi olmalıdır.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Codeparçacıklar öğesi](../ide/code-snippets-schema-reference.md#codesnippets)|Kod parçacığı XML şemasının kök öğesi.|

## <a name="codesnippets"></a>Codeparçacıklar öğesi
 [Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#codesnippet)öğelerini gruplandırır. @No__t_0 öğesi, kod parçacığı XML şemasının kök öğesidir.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>

```

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[Codeparçacığının öğesi](../ide/code-snippets-schema-reference.md#codesnippet)|İsteğe bağlı öğe. Tüm kod parçacığı verisi için üst öğe. Bir `CodeSnippets` öğesinde sıfır veya daha fazla `CodeSnippet` öğe olabilir.|

## <a name="declarations"></a>Bildirimleri öğesi
 Bir kod parçacığının düzenleyebileceğiniz bölümlerini oluşturan değişmez değerleri ve nesneleri belirtir.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>

```

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|İsteğe bağlı öğe. Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini tanımlar. Bir `Declarations` öğesinde sıfır veya daha fazla `Literal` öğe olabilir.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object)|İsteğe bağlı öğe. Kod parçacığının düzenleme yapabileceğiniz nesnelerini tanımlar. Bir `Declarations` öğesinde sıfır veya daha fazla `Object` öğe olabilir.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#snippet)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

## <a name="default"></a>Varsayılan öğe
 Bir IntelliSense Kod Parçacığı için değişmez değerin veya nesnenin varsayılan değerini belirtir.

```xml
<Default>
    Default value
</Default>

```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

 Bir metin değeri gereklidir. Bu metin, düzenleyebileceğiniz kod parçacığı alanlarını dolduran değişmez değerin veya nesnenin varsayılan değerini belirtir.

## <a name="description"></a>Description öğesi
 Bir IntelliSense Kod Parçacığı'nın içeriği hakkında açıklayıcı bilgileri belirtir.

```xml
<Description>
    Code Snippet Description
</Description>
```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler içerir.|

 Bir metin değeri gereklidir. Bu metin kod parçacığını tanımlar.

## <a name="function"></a>Function öğesi
 Değişmez değer veya nesne Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir.

> [!NOTE]
> @No__t_0 öğesi yalnızca görsel C# kod parçacıkları tarafından desteklenir.

```xml
<Function>
    FunctionName
</Function>
```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

 Bir metin değeri gereklidir. Bu metin, değişmez değer veya nesne alanı Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir.

## <a name="header"></a>Header öğesi
 IntelliSense Kod Parçacığı hakkında genel bilgileri belirtir.

```xml
<Header>
    <Title>... </Title>
    <Author>... </Author>
    <Description>... </Description>
    <HelpUrl>... </HelpUrl>
    <SnippetTypes>... </SnippetTypes>
    <Keywords>... </Keywords>
    <Shortcut>... </Shortcut>
</Header>

```

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[Author öğesi](../ide/code-snippets-schema-reference.md#author)|İsteğe bağlı öğe. Kod parçacığını yazan kişinin veya şirketin adı. Bir `Header` öğesinde sıfır veya bir `Author` öğe olabilir.|
|[Description öğesi](../ide/code-snippets-schema-reference.md#description)|İsteğe bağlı öğe. Kod parçacığının açıklaması. Bir `Header` öğesinde sıfır veya bir `Description` öğe olabilir.|
|[HelpUrl öğesi](../ide/code-snippets-schema-reference.md#helpurl)|İsteğe bağlı öğe. Kod parçacığı hakkında daha fazla bilgi içeren URL. Üst bilgi öğesinde sıfır veya bir `HelpURL` öğe olabilir. **Note:**  Visual Studio `HelpUrl` öğesini kullanmaz. Öğe, IntelliSense Kod Parçacığı XML şemasının bir parçasıdır ve öğeyi içeren her kod parçacığı doğrulanacaktır, ancak öğenin değeri hiçbir zaman kullanılmaz.|
|[Keywords öğesi](../ide/code-snippets-schema-reference.md#keywords)|İsteğe bağlı öğe. Öğeleri `Keyword` gruplar. Bir `Header` öğesinde sıfır veya bir `Keywords` öğe olabilir.|
|[Shortcut öğesi](../ide/code-snippets-schema-reference.md#shortcut)|İsteğe bağlı öğe. Kod parçacığını eklemek için kullanılabilecek kısayol metnini belirtir. Bir `Header` öğesinde sıfır veya bir `Shortcut` öğe olabilir.|
|[SnippetTypes öğesi](../ide/code-snippets-schema-reference.md#snippettypes)|İsteğe bağlı öğe. Öğeleri `SnippetType` gruplar. Bir `Header` öğesinde sıfır veya bir `SnippetTypes` öğe olabilir. @No__t_0 öğe yoksa, kod parçacığı her zaman geçerlidir.|
|[Title öğesi](../ide/code-snippets-schema-reference.md#title)|Gerekli öğe. Kod parçacığının kolay adı. Bir `Header` öğesinde tam olarak bir `Title` öğesi olmalıdır.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Codeparçacığının öğesi](../ide/code-snippets-schema-reference.md#codesnippet)|Tüm kod parçacığı verisi için üst öğe.|

## <a name="helpurl"></a>HelpUrl öğesi
 Bir kod parçacığı hakkında daha fazla bilgi sağlayan URL'yi belirtir.

> [!NOTE]
> Visual Studio `HelpUrl` öğesini kullanmaz. Öğe, IntelliSense Kod Parçacığı XML şemasının bir parçasıdır ve öğeyi içeren her kod parçacığı doğrulanacaktır, ancak öğenin değeri hiçbir zaman kullanılmaz.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>

```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler içerir.|

 Metin değeri isteğe bağlıdır. Bu metin, kod parçacığı hakkında daha fazla bilgi için ziyaret edilmesi gereken URL'yi belirtir.

## <a name="id"></a>ID öğesi
 Bir `Literal` veya `Object` öğesi için benzersiz bir tanımlayıcı belirtir. Aynı kod parçacığında iki değişmez değer veya nesne `ID` öğelerinde aynı metin değerine sahip olamaz. Değişmez değer ve nesneler `ID` öğesi bitiş değeri olan bir öğe içeremez. @No__t_0 değeri ayrılmıştır ve kod parçacığı eklendikten sonra imlecin yerleştirileceği konumu işaretlemek için kullanılır.

```xml
<ID>
    Unique Identifier
</ID>

```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

 Bir metin değeri gereklidir. Bu metin, nesne veya değişmez değer için benzersiz tanımlayıcıyı belirtir.

## <a name="import"></a>İçeri aktarma öğesi
 Bir IntelliSense Kod Parçacığı tarafından kullanılan içeri aktarılan ad alanlarını belirtir.

> [!NOTE]
> @No__t_0 öğesi yalnızca Visual Basic projeleri için desteklenir.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>

```

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[Namespace öğesi](../ide/code-snippets-schema-reference.md#namespace)|Gerekli öğe. Kod parçacığı tarafından kullanılan ad alanını belirtir. Bir `Import` öğesinde tam olarak bir `Namespace` öğesi olmalıdır.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Imports öğesi](../ide/code-snippets-schema-reference.md#imports)|Öğe **Içeri aktarma** öğeleri için gruplandırma öğesi.|

## <a name="imports"></a>Imports öğesi
 Tek tek `Import` öğeleri gruplandırır.

> [!NOTE]
> @No__t_0 öğesi yalnızca Visual Basic projeleri için desteklenir.

```xml
<Imports>
    <Import>... </Import>
<Imports>
```

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[İçeri aktarma öğesi](../ide/code-snippets-schema-reference.md#import)|İsteğe bağlı öğe. Kod parçacığı için içeri aktarılan ad alanlarını içerir. Bir `Imports` öğesinde sıfır veya daha fazla **Içeri aktarma** öğesi olabilir.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#snippet)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

## <a name="keyword"></a>Anahtar sözcük öğesi
 Kod parçacığı için özel bir anahtar sözcük belirtir. Kod parçacığı anahtar sözcükleri Visual Studio tarafından kullanılır ve çevrimiçi içerik sağlayıcılarının aramaya veya kategorilere ayırmaya yönelik özel anahtar sözcükler eklemek için kullandıkları standart bir yöntemi temsil eder.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Keywords öğesi](../ide/code-snippets-schema-reference.md#keywords)|Tek tek `Keyword` öğeleri gruplandırır.|

 Bir metin değeri gereklidir. Kod parçacığı için anahtar sözcük.

## <a name="keywords"></a>Keywords öğesi
 Tek tek `Keyword` öğeleri gruplandırır. Kod parçacığı anahtar sözcükleri Visual Studio tarafından kullanılır ve çevrimiçi içerik sağlayıcılarının aramaya veya kategorilere ayırmaya yönelik özel anahtar sözcükler eklemek için kullandıkları standart bir yöntemi temsil eder

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
<Keywords>
```

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[Anahtar sözcük öğesi](../ide/code-snippets-schema-reference.md#keyword)|İsteğe bağlı öğe. Kod parçacığı için tek tek anahtar sözcükleri içerir. Bir `Keywords` öğesinde sıfır veya daha fazla `Keyword` öğe olabilir.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler içerir.|

## <a name="literal"></a>Literal öğesi
 Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini tanımlar. @No__t_0 öğesi, tamamen kod parçacığında yer alan kod parçasının yerini belirlemek için kullanılır, ancak büyük olasılıkla koda eklendikten sonra özelleştirilmeyecektir. Örneğin, değişmez değer dizeleri, sayısal değerler ve bazı değişken adları değişmez değer olarak bildirilmelidir.

 Sabit değerler ve nesneler, seçili veya son değeri olan bir **ID** öğesi içeremez. Değer `$selected$`, çağrıldığında, çağrıldığında kod parçacığına eklenecek metni temsil eder. `$end$`, kod parçacığı eklendikten sonra imlecin yerleştirileceği konumu işaretler.

```xml
<Literal Editable="true/false">
   <ID>... </ID>
   <ToolTip>... </ToolTip>
   <Default>... </Default>
   <Function>... </Function>
</Literal>
```

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Editable`|İsteğe bağlı `Boolean` özniteliği. Kod parçacığı eklendikten sonra değişmez değerde düzenleme yapıp yapamayacağınızı belirtir. Bu özniteliğin varsayılan değeri `true`.|

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[Varsayılan öğe](../ide/code-snippets-schema-reference.md#default)|Gerekli öğe. Kod parçacığını eklediğinizde değişmez değerin alacağı varsayılan değeri belirtir. Bir `Literal` öğesinde tam olarak bir `Default` öğesi olmalıdır.|
|[Function öğesi](../ide/code-snippets-schema-reference.md#function)|İsteğe bağlı öğe. Değişmez değer Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir. Bir `Literal` öğesinde sıfır veya bir `Function` öğe olabilir.|
|[ID öğesi](../ide/code-snippets-schema-reference.md#id)|Gerekli öğe. Değişmez değer için benzersiz bir tanımlayıcı belirtir. Bir `Literal` öğesinde tam olarak bir `ID` öğesi olmalıdır.|
|[ToolTip öğesi](../ide/code-snippets-schema-reference.md#tooltip)|İsteğe bağlı öğe. Değişmez değerin beklenen değerini ve kullanımını açıklar. @No__t_1 öğesinde sıfır veya bir **araç ipucu** öğesi olabilir.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Bildirimleri öğesi](../ide/code-snippets-schema-reference.md#declarations)|Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini ve nesnelerini içerir.|

## <a name="namespace"></a>Namespace öğesi
 Kod parçacığının derlenip çalışması için içeri aktarılması gereken ad alanını belirtir. @No__t_0 öğesinde belirtilen ad alanı, zaten mevcut değilse kodun başındaki bir `Imports` ifadesine otomatik olarak eklenir.

> [!NOTE]
> @No__t_0 öğesi yalnızca Visual Basic projeleri için desteklenir.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[İçeri aktarma öğesi](../ide/code-snippets-schema-reference.md#import)|Belirtilen ad alanını içeri aktarır.|

 Bir metin değeri gereklidir. Bu metin, kod parçacığının içeri aktarıldığını varsaydığı bir ad alanını belirtir.

## <a name="object"></a>Nesne öğesi
 Kod parçacığının düzenleme yapabileceğiniz nesnelerini tanımlar. @No__t_0 öğesi, kod parçacığı için gereken ancak büyük olasılıkla kod parçacığı dışında tanımlanmış bir öğeyi tanımlamak için kullanılır. Örneğin, Windows Forms denetimleri, ASP.NET denetimleri, nesne örnekleri ve tür örnekleri nesne olarak bildirilmelidir. Nesne bildirimleri, `Type` öğesiyle gerçekleştirilen bir türün belirtilmesini gerektirir.

```xml
<Object Editable="true/false">
    <ID>... </ID>
    <Type>... </Type>
    <ToolTip>... </ToolTip>
    <Default>... </Default>
    <Function>... </Function>
</Object>
```

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Editable`|İsteğe bağlı `Boolean` özniteliği. Kod parçacığı eklendikten sonra değişmez değerde düzenleme yapıp yapamayacağınızı belirtir. Bu özniteliğin varsayılan değeri `true`.|

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[Varsayılan öğe](../ide/code-snippets-schema-reference.md#default)|Gerekli öğe. Kod parçacığını eklediğinizde değişmez değerin alacağı varsayılan değeri belirtir. Bir `Literal` öğesinde tam olarak bir `Default` öğesi olmalıdır.|
|[Function öğesi](../ide/code-snippets-schema-reference.md#function)|İsteğe bağlı öğe. Değişmez değer Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir. Bir `Literal` öğesinde sıfır veya bir `Function` öğe olabilir.|
|[ID öğesi](../ide/code-snippets-schema-reference.md#id)|Gerekli öğe. Değişmez değer için benzersiz bir tanımlayıcı belirtir. Bir `Literal` öğesinde tam olarak bir `ID` öğesi olmalıdır.|
|[ToolTip öğesi](../ide/code-snippets-schema-reference.md#tooltip)|İsteğe bağlı öğe. Değişmez değerin beklenen değerini ve kullanımını açıklar. @No__t_1 öğesinde sıfır veya bir **araç ipucu** öğesi olabilir.|
|[Type öğesi](../ide/code-snippets-schema-reference.md#type)|Gerekli öğe. Nesnenin türünü belirtir. Bir `Object` öğesinde tam olarak bir `Type` öğesi olmalıdır.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Bildirimleri öğesi](../ide/code-snippets-schema-reference.md#declarations)|Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini ve nesnelerini içerir.|

## <a name="reference"></a>Reference öğesi
 Kod parçacığının gerek duyduğu derleme başvuruları hakkındaki bilgileri belirtir.

> [!NOTE]
> @No__t_0 öğesi yalnızca Visual Basic projeleri için desteklenir.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[Assembly öğesi](../ide/code-snippets-schema-reference.md#assembly)|Gerekli öğe. Kod parçacığının başvurduğu derlemenin adını içerir. Bir `Reference` öğesinde tam olarak bir `Assembly` öğesi olmalıdır.|
|[URL öğesi](../ide/code-snippets-schema-reference.md#url)|İsteğe bağlı öğe. Başvurulan derleme hakkında daha fazla bilgi sağlayan bir URL içerir. Bir `Reference` öğesinde sıfır veya bir `Url` öğe olabilir.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[References öğesi](../ide/code-snippets-schema-reference.md#references)|@No__t_0 öğeleri için gruplandırma öğesi.|

## <a name="references"></a>References öğesi
 Tek tek `Reference` öğeleri gruplandırır.

> [!NOTE]
> @No__t_0 öğesi yalnızca Visual Basic projeleri için desteklenir.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[Reference öğesi](../ide/code-snippets-schema-reference.md#reference)|İsteğe bağlı öğe. Kod parçacığı için derleme başvuruları hakkındaki bilgileri içerir. Bir `References` öğesinde sıfır veya daha fazla `Reference` öğe olabilir.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#snippet)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

## <a name="shortcut"></a>Shortcut öğesi
 Kod parçacığını eklemek için kullanılan kısayol metnini belirtir. Bir `Shortcut` öğesinin metin değeri yalnızca alfasayısal karakter, kısa çizgi (-) ve alt çizgi (_) içerebilir.

> [!CAUTION]
> _ ve – C++ kod parçacığı kısayollarında desteklenmeyen karakterlerdir.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler içerir.|

 Metin değeri isteğe bağlıdır. Bu metin, kod parçacığını eklemek için bir kısayol olarak kullanılır.

## <a name="snippet"></a>Kod parçacığı öğesi
 Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu belirtir.

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>

```

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[Kod öğesi](../ide/code-snippets-schema-reference.md#code)|Gerekli öğe. Bir belge dosyasına eklemek istediğiniz kodu belirtir. Bir `Snippet` öğesinde tam olarak bir `Code` öğesi olmalıdır.|
|[Bildirimleri öğesi](../ide/code-snippets-schema-reference.md#declarations)|İsteğe bağlı öğe. Bir kod parçacığının düzenleyebileceğiniz bölümlerini oluşturan değişmez değerleri ve nesneleri belirtir. Bir `Snippet` öğesinde sıfır veya bir `Declarations` öğe olabilir.|
|[Imports öğesi](../ide/code-snippets-schema-reference.md#imports)|İsteğe bağlı öğe. Tek tek `Import` öğeleri gruplandırır. Bir `Snippet` öğesinde sıfır veya bir `Imports` öğe olabilir.|
||İsteğe bağlı öğe. Tek tek `Reference` öğeleri gruplandırır. Bir `Snippet` öğesinde sıfır veya bir `References` öğe olabilir.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Codeparçacığının öğesi](../ide/code-snippets-schema-reference.md#codesnippet)|Visual Studio kod dosyalarına ekleyebileceğiniz bir başlık ve birden fazla IntelliSense Kod Parçacığı belirtmenizi sağlar.|

## <a name="snippettype"></a>SnippetType Öğesi
 Visual Studio'nun kod parçacığını nasıl eklediğini belirtir.

```xml
<SnippetType>
    SurroundsWith/Expansion
<SnippetType>
```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[SnippetTypes öğesi](../ide/code-snippets-schema-reference.md#snippettypes)|Öğeleri `SnippetType` gruplar.|

 Metin değeri şu değerlerden biri olmalıdır:

- `SurroundsWith`: kod parçacığının seçili kod parçası çevresinde yerleştirilmesine izin verir.

- `Expansion`: kod parçacığının imlece eklenmesine izin verir.

- `Refactoring`: görsel C# yeniden düzenleme sırasında kod parçacığının kullanıldığını belirtir. `Refactoring` özel kod parçacıkları içinde kullanılamaz.

## <a name="snippettypes"></a>SnippetTypes öğesi
 Tek tek `SnippetType` öğeleri gruplandırır. @No__t_0 öğesi yoksa, kod parçacığı kodda herhangi bir yere eklenebilir.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
<SnippetTypes>
```

|Alt Öğe|Açıklama|
|-------------------|-----------------|
|[SnippetType Öğesi](../ide/code-snippets-schema-reference.md#snippettype)|İsteğe bağlı öğe. Visual Studio'nun kod parçacığını kodun içine nasıl eklediğini belirtir. Bir `SnippetTypes` öğesinde sıfır veya daha fazla `SnippetType` öğe olabilir.|

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler belirtir.|

## <a name="title"></a>Title öğesi
 Kod parçacığı için başlığı belirtir. Kod parçacığının `Title` öğesinde depolanan başlık kod **parçacığı seçicisinde** ve kod parçacığı içindeki açıklama kod **parçacıkları yöneticisinde**görüntülenir.

```xml
<Title>
    Code Snippet Title
<Title>
```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler belirtir.|

 Bir metin değeri gereklidir. Bu metin kod parçacığının başlığını belirtir.

## <a name="tooltip"></a>ToolTip öğesi
 Kod parçacığındaki bir değişmez değerin veya nesnenin beklenen değerini ve kullanımını açıklar; Visual Studio, kod parçacığını bir projeye eklerken ToolTip öğesinde bunu görüntüler. ToolTip metni, kod parçacığı eklendikten sonra değişmez değerin veya nesnenin üzerine fare geldiğinde görüntülenir.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

 Bir metin değeri gereklidir. Bu metin, kod parçacığındaki nesne veya değişmez değer ile ilişkilendirilecek ToolTip açıklamasını belirtir.

## <a name="type"></a>Type öğesi
 Nesnenin türünü belirtir. @No__t_0 öğesi, kod parçacığı için gereken ancak büyük olasılıkla kod parçacığı dışında tanımlanmış bir öğeyi tanımlamak için kullanılır. Örneğin, Windows Forms denetimleri, ASP.NET denetimleri, nesne örnekleri ve tür örnekleri nesne olarak bildirilmelidir. Nesne bildirimleri, `Type` öğesiyle gerçekleştirilen bir türün belirtilmesini gerektirir.

```xml
<Type>
    Type
</Type>
```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

 Bir metin değeri gereklidir. Bu metin nesnenin türünü belirtir.

## <a name="url"></a>URL öğesi
 Başvurulan derleme hakkında daha fazla bilgi sağlayan bir URL'yi belirtir.

> [!NOTE]
> @No__t_0 öğesi yalnızca Visual Basic projeleri için desteklenir.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Üst Öğe|Açıklama|
|--------------------|-----------------|
|[Reference öğesi](../ide/code-snippets-schema-reference.md#reference)|Kod parçacığının gerek duyduğu derleme başvurularını belirtir.|

 Bir metin değeri gereklidir. Bu metin, başvurulan derleme hakkında daha fazla bilgi içeren bir URL'yi belirtir. Bu URL, başvuru projeye eklenemediğinde görüntülenir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod parçacıkları](../ide/code-snippets.md) [Izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
