---
title: Kod parçacıkları şema başvurusu
ms.date: 02/25/2019
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22f84fbe5188e74acbf24256444ad11dd9c64347
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410130"
---
# <a name="code-snippets-schema-reference"></a>Kod parçacıkları şema başvurusu

IntelliSense kod parçacıkları, Visual Studio ile uygulamanıza eklenmeye hazırlanan önceden yazılmış kod parçalarıdır. Yinelenen kodları yazmak veya örnekleri aramak için harcanan süreyi kısaltan kod parçacıkları sağlayarak üretkenliği artırabilirsiniz. Kendi kod parçacıklarını oluşturmak ve bunları Visual Studio 'Nun zaten içerdiği kod parçacıklarına eklemek için IntelliSense kod parçacığı XML şemasını kullanabilirsiniz.

## <a name="assembly-element"></a>Assembly öğesi

Kod parçacığının başvurduğu derlemenin adını belirtir.

**Derleme** öğesinin metin değeri, `System.dll`veya `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`gibi tanımlayıcı adı gibi derlemenin kolay metin adıdır.

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Reference öğesi](../ide/code-snippets-schema-reference.md#reference-element)|Kod parçacığının gerek duyduğu derleme başvuruları hakkındaki bilgileri içerir.|

Bir metin değeri gereklidir. Bu metin, kod parçacığının başvurduğu derlemeyi belirtir.

## <a name="author-element"></a>Author öğesi

Kod parçacığı yazarının adını belirtir. **Kod parçacıkları Yöneticisi** , kod parçacığının `Author` öğesinde depolanan adı görüntüler.

```xml
<Author>
   Code Snippet Author
</Author>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler içerir.|

Bir metin değeri gereklidir. Bu metin kod parçacığının yazarını belirtir.

## <a name="code-element"></a>Kod öğesi

Kısa kod blokları için bir kapsayıcı sağlar.

### <a name="keywords"></a>Anahtar sözcükler

`Code` öğenin metninde kullanılabilecek iki ayrılmış sözcük vardır: `$end$` ve `$selected$`. `$end$`, kod parçacığı eklendikten sonra imlecin yerleştirileceği konumu işaretler. `$selected$`, çağrıldığında, çağrıldığında kod parçacığına eklenecek metni temsil eder. Örneğin, şunları içeren bir kod parçacığı verilmiştir:

```
$selected$ is a great color.
```

Kullanıcı şablonu çağırdığında "mavi" sözcüğü seçilirse sonuç şu olur:

```
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

`$selected$` ile `is`arasında boşluk olduğundan, başlangıç alanı görüntülenir.

Diğer tüm `$` anahtar sözcükleri `<Literal>` ve `<Object>` etiketlerinde dinamik olarak tanımlanmıştır.

Kod öğesinin yapısı aşağıda verilmiştir:

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

Bir metin değeri gereklidir. Bu metin, kod parçacığı kod dosyasına eklendiğinde kullanabileceğiniz değişmez değerler ve nesnelerle birlikte kodu belirtir.

### <a name="attributes"></a>Öznitelikler

Kod öğesi için kullanılabilen üç öznitelik vardır:

- **Dil** - , kod parçacığının dilini belirten _gerekli_ öznitelik. Değer aşağıdakilerden biri olabilir:

   |Değer|Açıklama|
   |-----|-----------|
   |`VB`|Bir Visual Basic kod parçacığını tanımlar.|
   |`CSharp`|Bir C# kod parçacığını tanımlar.|
   |`CPP`|Bir C++ kod parçacığını tanımlar.|
   |`XML`|Bir XML kod parçacığını tanımlar.|
   |`JavaScript`|Bir JavaScript kod parçacığını tanımlar.|
   |`TypeScript`|TypeScript kod parçacığını tanımlar.|
   |`SQL`|Bir SQL kod parçacığını tanımlar.|
   |`HTML`|Bir HTML kod parçacığını tanımlar.|

- **Tür** , kod parçacığının içerdiği kodun türünü belirten _isteğe bağlı_ - özniteliği. Değer aşağıdakilerden biri olabilir:

   |Değer|Açıklama|
   |-----|-----------|
   |`method body`|Kod parçacığının bir yöntem gövdesi olduğunu ve bu nedenle, bir yöntem bildiriminin içine eklenmesi gerektiğini belirtir.|
   |`method decl`|Kod parçacığının bir yöntem olduğunu ve bu nedenle, bir sınıf veya modül içine eklenmesi gerektiğini belirtir.|
   |`type decl`|Kod parçacığının bir tür olduğunu ve bu nedenle, bir sınıf, modül veya ad alanı içine eklenmesi gerektiğini belirtir.|
   |`file`|Kod parçacığının eksiksiz bir kod dosyası olduğunu belirtir. Bu kod parçacıkları tek başına bir kod dosyasının içine veya bir ad alanının içine eklenebilir.|
   |`any`|Kod parçacığının istenen yere eklenebileceğini belirtir. Bu etiket, açıklamalar gibi içeriğe bağımlı kod parçacıkları için kullanılır.|

- **Sınırlayıcı** - , koddaki değişmez değerleri ve nesneleri tanımlamakta kullanılan sınırlayıcıyı belirten _isteğe bağlı_ öznitelik. Varsayılan olarak, sınırlayıcı `$`.

### <a name="parent-element"></a>Üst öğe

|Üst öğe|Açıklama|
| - |-----------------|
|[Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#snippet-element)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

## <a name="codesnippet-element"></a>Codeparçacığının öğesi

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

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header-element)|Gerekli öğe. Kod parçacığı hakkında genel bilgiler içerir. Kod parçacığında tam olarak bir `Header` öğesi olmalıdır.|
|[Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#snippet-element)|Gerekli öğe. Visual Studio tarafından eklenecek kodu içerir. Kod parçacığında tam olarak bir `Snippet` öğesi olmalıdır.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Codeparçacıklar öğesi](../ide/code-snippets-schema-reference.md#codesnippets-element)|Kod parçacığı XML şemasının kök öğesi.|

## <a name="codesnippets-element"></a>Codeparçacıklar öğesi

[Kod parçacığı](../ide/code-snippets-schema-reference.md#codesnippet-element) öğelerini gruplandırır. `CodeSnippets` öğesi, kod parçacığı XML şemasının kök öğesidir.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Codeparçacığının öğesi](../ide/code-snippets-schema-reference.md#codesnippet-element)|İsteğe bağlı öğe. Tüm kod parçacığı verisi için üst öğe. Bir `CodeSnippets` öğesinde sıfır veya daha fazla `CodeSnippet` öğe olabilir.|

## <a name="declarations-element"></a>Bildirimleri öğesi

Bir kod parçacığının düzenleyebileceğiniz bölümlerini oluşturan değişmez değerleri ve nesneleri belirtir.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal-element)|İsteğe bağlı öğe. Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini tanımlar. Bir `Declarations` öğesinde sıfır veya daha fazla `Literal` öğe olabilir.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object-element)|İsteğe bağlı öğe. Kod parçacığının düzenleme yapabileceğiniz nesnelerini tanımlar. Bir `Declarations` öğesinde sıfır veya daha fazla `Object` öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#snippet-element)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

## <a name="default-element"></a>Varsayılan öğe

Bir IntelliSense Kod Parçacığı için değişmez değerin veya nesnenin varsayılan değerini belirtir.

```xml
<Default>
    Default value
</Default>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object-element)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

Bir metin değeri gereklidir. Bu metin, düzenleyebileceğiniz kod parçacığı alanlarını dolduran değişmez değerin veya nesnenin varsayılan değerini belirtir.

## <a name="description-element"></a>Description öğesi

Bir IntelliSense Kod Parçacığı'nın içeriği hakkında açıklayıcı bilgileri belirtir.

```xml
<Description>
    Code Snippet Description
</Description>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler içerir.|

Bir metin değeri gereklidir. Bu metin kod parçacığını tanımlar.

## <a name="function-element"></a>Function öğesi

Değişmez değer veya nesne Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir.

> [!NOTE]
> `Function` öğesi yalnızca kod parçacıkları içinde C# desteklenir.

```xml
<Function>
    FunctionName
</Function>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object-element)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

Bir metin değeri gereklidir. Bu metin, değişmez değer veya nesne alanı Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir.

## <a name="header-element"></a>Header öğesi

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

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Author öğesi](../ide/code-snippets-schema-reference.md#author-element)|İsteğe bağlı öğe. Kod parçacığını yazan kişinin veya şirketin adı. Bir `Header` öğesinde sıfır veya bir `Author` öğe olabilir.|
|[Description öğesi](../ide/code-snippets-schema-reference.md#description-element)|İsteğe bağlı öğe. Kod parçacığının açıklaması. Bir `Header` öğesinde sıfır veya bir `Description` öğe olabilir.|
|[HelpUrl öğesi](../ide/code-snippets-schema-reference.md#helpurl-element)|İsteğe bağlı öğe. Kod parçacığı hakkında daha fazla bilgi içeren URL. Üst bilgi öğesinde sıfır veya bir `HelpURL` öğe olabilir. **Note:**  Visual Studio `HelpUrl` öğesini kullanmaz. Öğe, IntelliSense Kod Parçacığı XML şemasının bir parçasıdır ve öğeyi içeren her kod parçacığı doğrulanacaktır, ancak öğenin değeri hiçbir zaman kullanılmaz.|
|[Keywords öğesi](../ide/code-snippets-schema-reference.md#keywords-element)|İsteğe bağlı öğe. Öğeleri `Keyword` gruplar. Bir `Header` öğesinde sıfır veya bir `Keywords` öğe olabilir.|
|[Shortcut öğesi](../ide/code-snippets-schema-reference.md#shortcut-element)|İsteğe bağlı öğe. Kod parçacığını eklemek için kullanılabilecek kısayol metnini belirtir. Bir `Header` öğesinde sıfır veya bir `Shortcut` öğe olabilir.|
|[SnippetTypes öğesi](../ide/code-snippets-schema-reference.md#snippettypes-element)|İsteğe bağlı öğe. Öğeleri `SnippetType` gruplar. Bir `Header` öğesinde sıfır veya bir `SnippetTypes` öğe olabilir. `SnippetTypes` öğe yoksa, kod parçacığı her zaman geçerlidir.|
|[Title öğesi](../ide/code-snippets-schema-reference.md#title-element)|Gerekli öğe. Kod parçacığının kolay adı. Bir `Header` öğesinde tam olarak bir `Title` öğesi olmalıdır.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Codeparçacığının öğesi](../ide/code-snippets-schema-reference.md#codesnippet-element)|Tüm kod parçacığı verisi için üst öğe.|

## <a name="helpurl-element"></a>HelpUrl öğesi

Bir kod parçacığı hakkında daha fazla bilgi sağlayan URL'yi belirtir.

> [!NOTE]
> Visual Studio `HelpUrl` öğesini kullanmaz. Öğe, IntelliSense Kod Parçacığı XML şemasının bir parçasıdır ve öğeyi içeren her kod parçacığı doğrulanacaktır, ancak öğenin değeri hiçbir zaman kullanılmaz.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler içerir.|

Metin değeri isteğe bağlıdır. Bu metin, kod parçacığı hakkında daha fazla bilgi için ziyaret edilmesi gereken URL'yi belirtir.

## <a name="id-element"></a>ID öğesi

Bir `Literal` veya `Object` öğesi için benzersiz bir tanımlayıcı belirtir. Aynı kod parçacığında iki değişmez değer veya nesne `ID` öğelerinde aynı metin değerine sahip olamaz. Değişmez değer ve nesneler `ID` öğesi bitiş değeri olan bir öğe içeremez. `$end$` değeri ayrılmıştır ve kod parçacığı eklendikten sonra imlecin yerleştirileceği konumu işaretlemek için kullanılır.

```xml
<ID>
    Unique Identifier
</ID>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object-element)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

Bir metin değeri gereklidir. Bu metin, nesne veya değişmez değer için benzersiz tanımlayıcıyı belirtir.

## <a name="import-element"></a>Import öğesi

Bir IntelliSense kod parçacığı tarafından kullanılan içeri aktarılan ad alanlarını belirtir.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Namespace öğesi](../ide/code-snippets-schema-reference.md#namespace-element)|Gerekli öğe. Kod parçacığı tarafından kullanılan ad alanını belirtir. Bir `Import` öğesinde tam olarak bir `Namespace` öğesi olmalıdır.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Imports öğesi](../ide/code-snippets-schema-reference.md#imports-element)|Öğe **Içeri aktarma** öğeleri için gruplandırma öğesi.|

## <a name="imports-element"></a>Imports öğesi

Tek tek `Import` öğeleri gruplandırır.

```xml
<Imports>
    <Import>... </Import>
</Imports>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[İçeri aktarma öğesi](../ide/code-snippets-schema-reference.md#import-element)|İsteğe bağlı öğe. Kod parçacığı için içeri aktarılan ad alanlarını içerir. Bir `Imports` öğesinde sıfır veya daha fazla **Içeri aktarma** öğesi olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#snippet-element)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

## <a name="keyword-element"></a>Anahtar sözcük öğesi

Kod parçacığı için özel bir anahtar sözcük belirtir. Kod parçacığı anahtar sözcükleri Visual Studio tarafından kullanılır ve çevrimiçi içerik sağlayıcılarının aramaya veya kategorilere ayırmaya yönelik özel anahtar sözcükler eklemek için kullandıkları standart bir yöntemi temsil eder.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Keywords öğesi](../ide/code-snippets-schema-reference.md#keywords-element)|Tek tek `Keyword` öğeleri gruplandırır.|

Bir metin değeri gereklidir. Kod parçacığı için anahtar sözcük.

## <a name="keywords-element"></a>Keywords öğesi

Tek tek `Keyword` öğeleri gruplandırır. Kod parçacığı anahtar sözcükleri Visual Studio tarafından kullanılır ve çevrimiçi içerik sağlayıcılarının aramaya veya kategorilere ayırmaya yönelik özel anahtar sözcükler eklemek için kullandıkları standart bir yöntemi temsil eder

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
</Keywords>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Anahtar sözcük öğesi](../ide/code-snippets-schema-reference.md#keyword-element)|İsteğe bağlı öğe. Kod parçacığı için tek tek anahtar sözcükleri içerir. Bir `Keywords` öğesinde sıfır veya daha fazla `Keyword` öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler içerir.|

## <a name="literal-element"></a>Literal öğesi

Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini tanımlar. `Literal` öğesi, tamamen kod parçacığında yer alan kod parçasının yerini belirlemek için kullanılır, ancak büyük olasılıkla koda eklendikten sonra özelleştirilmeyecektir. Örneğin, değişmez değer dizeleri, sayısal değerler ve bazı değişken adları değişmez değer olarak bildirilmelidir.

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

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Varsayılan öğe](../ide/code-snippets-schema-reference.md#default-element)|Gerekli öğe. Kod parçacığını eklediğinizde değişmez değerin alacağı varsayılan değeri belirtir. Bir `Literal` öğesinde tam olarak bir `Default` öğesi olmalıdır.|
|[Function öğesi](../ide/code-snippets-schema-reference.md#function-element)|İsteğe bağlı öğe. Değişmez değer Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir. Bir `Literal` öğesinde sıfır veya bir `Function` öğe olabilir.|
|[ID öğesi](../ide/code-snippets-schema-reference.md#id-element)|Gerekli öğe. Değişmez değer için benzersiz bir tanımlayıcı belirtir. Bir `Literal` öğesinde tam olarak bir `ID` öğesi olmalıdır.|
|[ToolTip öğesi](../ide/code-snippets-schema-reference.md#tooltip-element)|İsteğe bağlı öğe. Değişmez değerin beklenen değerini ve kullanımını açıklar. `Literal` öğesinde sıfır veya bir **araç ipucu** öğesi olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Bildirimleri öğesi](../ide/code-snippets-schema-reference.md#declarations-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini ve nesnelerini içerir.|

## <a name="namespace-element"></a>Namespace öğesi

Kod parçacığının derlenip çalışması için içeri aktarılması gereken ad alanını belirtir. `Namespace` öğesinde belirtilen ad alanı, zaten mevcut değilse kodun başındaki bir `using` yönergesine veya `Imports` bildirimine otomatik olarak eklenir.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[İçeri aktarma öğesi](../ide/code-snippets-schema-reference.md#import-element)|Belirtilen ad alanını içeri aktarır.|

Bir metin değeri gereklidir. Bu metin, kod parçacığının içeri aktarıldığını varsaydığı bir ad alanını belirtir.

## <a name="object-element"></a>Nesne öğesi

Kod parçacığının düzenleme yapabileceğiniz nesnelerini tanımlar. `Object` öğesi, kod parçacığı için gereken ancak büyük olasılıkla kod parçacığı dışında tanımlanmış bir öğeyi tanımlamak için kullanılır. Örneğin, Windows Forms denetimleri, ASP.NET denetimleri, nesne örnekleri ve tür örnekleri nesne olarak bildirilmelidir. Nesne bildirimleri, `Type` öğesiyle gerçekleştirilen bir türün belirtilmesini gerektirir.

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

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Varsayılan öğe](../ide/code-snippets-schema-reference.md#default-element)|Gerekli öğe. Kod parçacığını eklediğinizde değişmez değerin alacağı varsayılan değeri belirtir. Bir `Literal` öğesinde tam olarak bir `Default` öğesi olmalıdır.|
|[Function öğesi](../ide/code-snippets-schema-reference.md#function-element)|İsteğe bağlı öğe. Değişmez değer Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir. Bir `Literal` öğesinde sıfır veya bir `Function` öğe olabilir.|
|[ID öğesi](../ide/code-snippets-schema-reference.md#id-element)|Gerekli öğe. Değişmez değer için benzersiz bir tanımlayıcı belirtir. Bir `Literal` öğesinde tam olarak bir `ID` öğesi olmalıdır.|
|[ToolTip öğesi](../ide/code-snippets-schema-reference.md#tooltip-element)|İsteğe bağlı öğe. Değişmez değerin beklenen değerini ve kullanımını açıklar. `Literal` öğesinde sıfır veya bir **araç ipucu** öğesi olabilir.|
|[Type öğesi](../ide/code-snippets-schema-reference.md#type-element)|Gerekli öğe. Nesnenin türünü belirtir. Bir `Object` öğesinde tam olarak bir `Type` öğesi olmalıdır.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Bildirimleri öğesi](../ide/code-snippets-schema-reference.md#declarations-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini ve nesnelerini içerir.|

## <a name="reference-element"></a>Reference öğesi

Kod parçacığının gerek duyduğu derleme başvuruları hakkındaki bilgileri belirtir.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Assembly öğesi](../ide/code-snippets-schema-reference.md#assembly-element)|Gerekli öğe. Kod parçacığının başvurduğu derlemenin adını içerir. Bir `Reference` öğesinde tam olarak bir `Assembly` öğesi olmalıdır.|
|[URL öğesi](../ide/code-snippets-schema-reference.md#url-element)|İsteğe bağlı öğe. Başvurulan derleme hakkında daha fazla bilgi sağlayan bir URL içerir. Bir `Reference` öğesinde sıfır veya bir `Url` öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[References öğesi](../ide/code-snippets-schema-reference.md#references-element)|`Reference` öğeleri için gruplandırma öğesi.|

## <a name="references-element"></a>References öğesi

Tek tek `Reference` öğeleri gruplandırır.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Reference öğesi](../ide/code-snippets-schema-reference.md#reference-element)|İsteğe bağlı öğe. Kod parçacığı için derleme başvuruları hakkındaki bilgileri içerir. Bir `References` öğesinde sıfır veya daha fazla `Reference` öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Kod parçacığı öğesi](../ide/code-snippets-schema-reference.md#snippet-element)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

## <a name="shortcut-element"></a>Shortcut öğesi

Kod parçacığını eklemek için kullanılan kısayol metnini belirtir. Bir `Shortcut` öğesinin metin değeri yalnızca alfasayısal karakterler ve alt çizgi (_) içerebilir.

> [!CAUTION]
> Alt çizgi (_) C++ kod parçacığı kısayollarında desteklenmeyen karakterler değildir.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler içerir.|

Metin değeri isteğe bağlıdır. Bu metin, kod parçacığını eklemek için bir kısayol olarak kullanılır.

## <a name="snippet-element"></a>Kod parçacığı öğesi

Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu belirtir.

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Kod öğesi](../ide/code-snippets-schema-reference.md#code-element)|Gerekli öğe. Bir belge dosyasına eklemek istediğiniz kodu belirtir. Bir `Snippet` öğesinde tam olarak bir `Code` öğesi olmalıdır.|
|[Bildirimleri öğesi](../ide/code-snippets-schema-reference.md#declarations-element)|İsteğe bağlı öğe. Bir kod parçacığının düzenleyebileceğiniz bölümlerini oluşturan değişmez değerleri ve nesneleri belirtir. Bir `Snippet` öğesinde sıfır veya bir `Declarations` öğe olabilir.|
|[Imports öğesi](../ide/code-snippets-schema-reference.md#imports-element)|İsteğe bağlı öğe. Tek tek `Import` öğeleri gruplandırır. Bir `Snippet` öğesinde sıfır veya bir `Imports` öğe olabilir.|
|[References öğesi](../ide/code-snippets-schema-reference.md#references-element)|İsteğe bağlı öğe. Tek tek `Reference` öğeleri gruplandırır. Bir `Snippet` öğesinde sıfır veya bir `References` öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Codeparçacığının öğesi](../ide/code-snippets-schema-reference.md#codesnippet-element)|Visual Studio kod dosyalarına ekleyebileceğiniz bir başlık ve birden fazla IntelliSense Kod Parçacığı belirtmenizi sağlar.|

## <a name="snippettype-element"></a>SnippetType Öğesi

Visual Studio'nun kod parçacığını nasıl eklediğini belirtir.

```xml
<SnippetType>
    SurroundsWith/Expansion
</SnippetType>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[SnippetTypes öğesi](../ide/code-snippets-schema-reference.md#snippettypes-element)|Öğeleri `SnippetType` gruplar.|

Metin değeri şu değerlerden biri olmalıdır:

- `SurroundsWith`: kod parçacığının seçili kod parçası çevresinde yerleştirilmesine izin verir.

- `Expansion`: kod parçacığının imlece eklenmesine izin verir.

- `Refactoring`: yeniden düzenleme sırasında C# kod parçacığının kullanıldığını belirtir. `Refactoring` özel kod parçacıkları içinde kullanılamaz.

## <a name="snippettypes-element"></a>SnippetTypes öğesi

Tek tek `SnippetType` öğeleri gruplandırır. `SnippetTypes` öğesi yoksa, kod parçacığı kodda herhangi bir yere eklenebilir.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
</SnippetTypes>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[SnippetType Öğesi](../ide/code-snippets-schema-reference.md#snippettype-element)|İsteğe bağlı öğe. Visual Studio'nun kod parçacığını kodun içine nasıl eklediğini belirtir. Bir `SnippetTypes` öğesinde sıfır veya daha fazla `SnippetType` öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler belirtir.|

## <a name="title-element"></a>Title öğesi

Kod parçacığı için başlığı belirtir. Kod parçacığının `Title` öğesinde depolanan başlık kod **parçacığı seçicisinde** ve kod parçacığı içindeki açıklama kod **parçacıkları yöneticisinde**görüntülenir.

```xml
<Title>
    Code Snippet Title
</Title>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Header öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler belirtir.|

Bir metin değeri gereklidir. Bu metin kod parçacığının başlığını belirtir.

## <a name="tooltip-element"></a>ToolTip öğesi

Kod parçacığındaki bir değişmez değerin veya nesnenin beklenen değerini ve kullanımını açıklar; Visual Studio, kod parçacığını bir projeye eklerken ToolTip öğesinde bunu görüntüler. ToolTip metni, kod parçacığı eklendikten sonra değişmez değerin veya nesnenin üzerine fare geldiğinde görüntülenir.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object-element)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

Bir metin değeri gereklidir. Bu metin, kod parçacığındaki nesne veya değişmez değer ile ilişkilendirilecek ToolTip açıklamasını belirtir.

## <a name="type-element"></a>Type öğesi

Nesnenin türünü belirtir. `Object` öğesi, kod parçacığı için gereken ancak büyük olasılıkla kod parçacığı dışında tanımlanmış bir öğeyi tanımlamak için kullanılır. Örneğin, Windows Forms denetimleri, ASP.NET denetimleri, nesne örnekleri ve tür örnekleri nesne olarak bildirilmelidir. Nesne bildirimleri, `Type` öğesiyle gerçekleştirilen bir türün belirtilmesini gerektirir.

```xml
<Type>
    Type
</Type>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object-element)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

Bir metin değeri gereklidir. Bu metin nesnenin türünü belirtir. Örnek:

```xml
<Type>System.Data.SqlClient.SqlConnection</Type>
```

## <a name="url-element"></a>URL öğesi

Başvurulan derleme hakkında daha fazla bilgi sağlayan bir URL'yi belirtir.

> [!NOTE]
> `Url` öğesi yalnızca Visual Basic projeleri için desteklenir.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Reference öğesi](../ide/code-snippets-schema-reference.md#reference-element)|Kod parçacığının gerek duyduğu derleme başvurularını belirtir.|

Bir metin değeri gereklidir. Bu metin, başvurulan derleme hakkında daha fazla bilgi içeren bir URL'yi belirtir. Bu URL, başvuru projeye eklenemediğinde görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)
- [İzlenecek Yol: Kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
