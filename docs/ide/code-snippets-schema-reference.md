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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301841"
---
# <a name="code-snippets-schema-reference"></a>Kod parçacıkları şema başvurusu

IntelliSense Code Snippets Visual Studio ile uygulamanıza eklenmeye hazır önceden yazılmış kod parçalarıdır. Yinelenen kodları yazmak veya örnekleri aramak için harcanan süreyi kısaltan kod parçacıkları sağlayarak üretkenliği artırabilirsiniz. Kendi kod parçacıklarınızı oluşturmak ve Bunları Visual Studio'nun zaten içerdiği kod parçacıklarına eklemek için IntelliSense Code Snippet XML şemasını kullanabilirsiniz.

## <a name="assembly-element"></a>Montaj öğesi

Kod parçacığının başvurduğu derlemenin adını belirtir.

**Derleme** öğesinin metin değeri, derlemenin dost metin adıdır( `System.dll`örneğin, `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`') gibi.

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Referans öğesi](../ide/code-snippets-schema-reference.md#reference-element)|Kod parçacığının gerek duyduğu derleme başvuruları hakkındaki bilgileri içerir.|

Bir metin değeri gereklidir. Bu metin, kod parçacığının başvurduğu derlemeyi belirtir.

## <a name="author-element"></a>Yazar öğesi

Kod parçacığı yazarının adını belirtir. **Kod Parçacıkları Yöneticisi,** kod parçacığının `Author` öğesinde depolanan adı görüntüler.

```xml
<Author>
   Code Snippet Author
</Author>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Üstbilgi öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler içerir.|

Bir metin değeri gereklidir. Bu metin kod parçacığının yazarını belirtir.

## <a name="code-element"></a>Kod öğesi

Kısa kod blokları için bir kapsayıcı sağlar.

### <a name="keywords"></a>Anahtar sözcükler

`Code` Öğenin metninde kullanılmak üzere iki ayrılmış `$end$` sözcük kullanılabilir: ve `$selected$`. `$end$`kod parçacığı takıldıktan sonra imleci yerleştirmek için konumu işaretler. `$selected$`çağrıldığı zaman snippet'e eklenecek belgede seçilen metni temsil eder. Örneğin, içeren bir parçacık verilir:

```
$selected$ is a great color.
```

Kullanıcı şablonu çağırdığında "Mavi" sözcüğü seçilirse, sonuç şudur:

```
Blue is a great color.
```

Bir kod parçacığında birden `$end$` fazla veya `$selected$` birden fazla kullanamazsınız. Bunu yaparsanız, yalnızca ikinci örnek tanınır. Içeren bir parçacık göz önüne alındığında:

```
$selected$ is a great color. I love $selected$.
```

"Mavi" sözcüğü seçilirse, sonuç:

```
 is a great color. I love Blue.
```

İlk boşluk görüntülenir, çünkü . `$selected$` `is`

Diğer `$` tüm anahtar kelimeler dinamik `<Literal>` `<Object>` olarak tanımlanır ve etiketler.

Kod öğesinin yapısı aşağıdadır:

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

Bir metin değeri gereklidir. Bu metin, bu kod parçacığı bir kod dosyasına eklendiğinde kullanabileceğiniz gerçek ve nesnelerle birlikte kodu belirtir.

### <a name="attributes"></a>Öznitelikler

Kod öğesi için üç öznitelik vardır:

- **Kod** - parçacığının dilini belirten Dil_Gerekli_ öznitelik. Değer aşağıdakilerden biri olabilir:

   |Değer|Açıklama|
   |-----|-----------|
   |`VB`|Bir Visual Basic kod parçacığını tanımlar.|
   |`CSharp`|Bir C# kod parçacığını tanımlar.|
   |`CPP`|Bir C++ kod parçacığını tanımlar.|
   |`XML`|Bir XML kod parçacığını tanımlar.|
   |`JavaScript`|Bir JavaScript kod parçacığını tanımlar.|
   |`TypeScript`|Bir TypeScript kod parçacığı tanımlar.|
   |`SQL`|Bir SQL kod parçacığını tanımlar.|
   |`HTML`|Bir HTML kod parçacığını tanımlar.|

- **Tür** - Snippet içerdiği kod türünü belirten_İsteğe Bağlı_ öznitelik. Değer aşağıdakilerden biri olabilir:

   |Değer|Açıklama|
   |-----|-----------|
   |`method body`|Kod parçacığının bir yöntem gövdesi olduğunu ve bu nedenle, bir yöntem bildiriminin içine eklenmesi gerektiğini belirtir.|
   |`method decl`|Kod parçacığının bir yöntem olduğunu ve bu nedenle, bir sınıf veya modül içine eklenmesi gerektiğini belirtir.|
   |`type decl`|Kod parçacığının bir tür olduğunu ve bu nedenle, bir sınıf, modül veya ad alanı içine eklenmesi gerektiğini belirtir.|
   |`file`|Kod parçacığının eksiksiz bir kod dosyası olduğunu belirtir. Bu kod parçacıkları tek başına bir kod dosyasının içine veya bir ad alanının içine eklenebilir.|
   |`any`|Kod parçacığının istenen yere eklenebileceğini belirtir. Bu etiket, açıklamalar gibi içeriğe bağımlı kod parçacıkları için kullanılır.|

- **Delimiter** - Koddaki gerçek ve nesneleri tanımlamak için kullanılan sınır çözücünün belirttiği_Isteğe bağlı_ öznitelik. Varsayılan olarak, sınır `$`layıcı.

### <a name="parent-element"></a>Üst öğe

|Üst öğe|Açıklama|
| - |-----------------|
|[Parçacık öğesi](../ide/code-snippets-schema-reference.md#snippet-element)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

## <a name="codesnippet-element"></a>CodeSnippet öğesi

Visual Studio kod dosyalarına ekleyebileceğiniz bir başlık ve birden fazla IntelliSense Kod Parçacığı belirtmenizi sağlar.

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>
```

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Format`|Gerekli öznitelik. Kod parçacığının şema sürümünü belirtir. Format özniteliği, her "x"in sürüm numarasına ait sayısal bir değeri temsil ettiği x.x.x sözdiziminde bir dize olmalıdır. Visual Studio, anlamadığı özniteliklere sahip `Format` kod parçacıklarını yok sayar.|

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Üstbilgi öğesi](../ide/code-snippets-schema-reference.md#header-element)|Gerekli öğe. Kod parçacığı hakkında genel bilgiler içerir. Kod parçacığında `Header` tam olarak bir öğe olmalıdır.|
|[Parçacık öğesi](../ide/code-snippets-schema-reference.md#snippet-element)|Gerekli öğe. Visual Studio tarafından eklenecek kodu içerir. Kod parçacığında `Snippet` tam olarak bir öğe olmalıdır.|

|Üst öğe|Açıklama|
| - |-----------------|
|[CodeSnippets öğesi](../ide/code-snippets-schema-reference.md#codesnippets-element)|Kod parçacığı XML şemasının kök öğesi.|

## <a name="codesnippets-element"></a>CodeSnippets öğesi

Gruplar [CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element) elemanları. Öğe, `CodeSnippets` kod snippet XML şemasının kök öğesidir.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[CodeSnippet öğesi](../ide/code-snippets-schema-reference.md#codesnippet-element)|İsteğe bağlı öğe. Tüm kod parçacığı verisi için üst öğe. Bir `CodeSnippets` öğede sıfır `CodeSnippet` veya daha fazla öğe olabilir.|

## <a name="declarations-element"></a>Bildirimler öğesi

Bir kod parçacığının düzenleyebileceğiniz bölümlerini oluşturan değişmez değerleri ve nesneleri belirtir.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Edebi eleman](../ide/code-snippets-schema-reference.md#literal-element)|İsteğe bağlı öğe. Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini tanımlar. Bir `Declarations` öğede sıfır `Literal` veya daha fazla öğe olabilir.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object-element)|İsteğe bağlı öğe. Kod parçacığının düzenleme yapabileceğiniz nesnelerini tanımlar. Bir `Declarations` öğede sıfır `Object` veya daha fazla öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Parçacık öğesi](../ide/code-snippets-schema-reference.md#snippet-element)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

## <a name="default-element"></a>Varsayılan öğe

Bir IntelliSense Kod Parçacığı için değişmez değerin veya nesnenin varsayılan değerini belirtir.

```xml
<Default>
    Default value
</Default>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Edebi eleman](../ide/code-snippets-schema-reference.md#literal-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object-element)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

Bir metin değeri gereklidir. Bu metin, düzenleyebileceğiniz kod parçacığı alanlarını dolduran değişmez değerin veya nesnenin varsayılan değerini belirtir.

## <a name="description-element"></a>Açıklama öğesi

Bir IntelliSense Kod Parçacığı'nın içeriği hakkında açıklayıcı bilgileri belirtir.

```xml
<Description>
    Code Snippet Description
</Description>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Üstbilgi öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler içerir.|

Bir metin değeri gereklidir. Bu metin kod parçacığını tanımlar.

## <a name="function-element"></a>Fonksiyon öğesi

Değişmez değer veya nesne Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir.

> [!NOTE]
> Öğe `Function` yalnızca C# kod parçacıklarında desteklenir.

```xml
<Function>
    FunctionName
</Function>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Edebi eleman](../ide/code-snippets-schema-reference.md#literal-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object-element)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

Bir metin değeri gereklidir. Bu metin, değişmez değer veya nesne alanı Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir.

## <a name="header-element"></a>Üstbilgi öğesi

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
|[Yazar öğesi](../ide/code-snippets-schema-reference.md#author-element)|İsteğe bağlı öğe. Kod parçacığını yazan kişinin veya şirketin adı. Bir `Header` öğede sıfır `Author` veya bir öğe olabilir.|
|[Açıklama öğesi](../ide/code-snippets-schema-reference.md#description-element)|İsteğe bağlı öğe. Kod parçacığının açıklaması. Bir `Header` öğede sıfır `Description` veya bir öğe olabilir.|
|[HelpUrl öğesi](../ide/code-snippets-schema-reference.md#helpurl-element)|İsteğe bağlı öğe. Kod parçacığı hakkında daha fazla bilgi içeren URL. Üstbilgi öğesinde `HelpURL` sıfır veya bir öğe olabilir. **Not:**  Visual Studio öğeyi `HelpUrl` kullanmaz. Öğe, IntelliSense Kod Parçacığı XML şemasının bir parçasıdır ve öğeyi içeren her kod parçacığı doğrulanacaktır, ancak öğenin değeri hiçbir zaman kullanılmaz.|
|[Anahtar kelimeler öğesi](../ide/code-snippets-schema-reference.md#keywords-element)|İsteğe bağlı öğe. Öğeleri `Keyword` grupla. Bir `Header` öğede sıfır `Keywords` veya bir öğe olabilir.|
|[Kısayol öğesi](../ide/code-snippets-schema-reference.md#shortcut-element)|İsteğe bağlı öğe. Kod parçacığını eklemek için kullanılabilecek kısayol metnini belirtir. Bir `Header` öğede sıfır `Shortcut` veya bir öğe olabilir.|
|[SnippetTypes öğesi](../ide/code-snippets-schema-reference.md#snippettypes-element)|İsteğe bağlı öğe. Öğeleri `SnippetType` grupla. Bir `Header` öğede sıfır `SnippetTypes` veya bir öğe olabilir. Öğe yoksa, `SnippetTypes` kod parçacığı her zaman geçerlidir.|
|[Başlık öğesi](../ide/code-snippets-schema-reference.md#title-element)|Gerekli öğe. Kod parçacığının kolay adı. Bir `Header` elementte `Title` tam olarak bir öğe olmalıdır.|

|Üst öğe|Açıklama|
| - |-----------------|
|[CodeSnippet öğesi](../ide/code-snippets-schema-reference.md#codesnippet-element)|Tüm kod parçacığı verisi için üst öğe.|

## <a name="helpurl-element"></a>HelpUrl öğesi

Bir kod parçacığı hakkında daha fazla bilgi sağlayan URL'yi belirtir.

> [!NOTE]
> Visual Studio öğeyi `HelpUrl` kullanmaz. Öğe, IntelliSense Kod Parçacığı XML şemasının bir parçasıdır ve öğeyi içeren her kod parçacığı doğrulanacaktır, ancak öğenin değeri hiçbir zaman kullanılmaz.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Üstbilgi öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler içerir.|

Metin değeri isteğe bağlıdır. Bu metin, kod parçacığı hakkında daha fazla bilgi için ziyaret edilmesi gereken URL'yi belirtir.

## <a name="id-element"></a>KIMLIK öğesi

Bir `Literal` veya `Object` öğe için benzersiz bir tanımlayıcı belirtir. Aynı kod snippet'indeki iki gerçek veya nesne, `ID` öğelerinde aynı metin değerine sahip olamaz. Literals ve nesneler sonu `ID` değeri olan bir öğe içeremez. Değer `$end$` ayrılmıştır ve kod parçacığı takıldıktan sonra imleci yerleştirmek için konumu işaretlemek için kullanılır.

```xml
<ID>
    Unique Identifier
</ID>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Edebi eleman](../ide/code-snippets-schema-reference.md#literal-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object-element)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

Bir metin değeri gereklidir. Bu metin, nesne veya değişmez değer için benzersiz tanımlayıcıyı belirtir.

## <a name="import-element"></a>Alma öğesi

IntelliSense kod parçacığı tarafından kullanılan içe aktarılan ad alanlarını belirtir.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Namespace öğesi](../ide/code-snippets-schema-reference.md#namespace-element)|Gerekli öğe. Kod parçacığı tarafından kullanılan ad alanını belirtir. Bir `Import` elementte `Namespace` tam olarak bir öğe olmalıdır.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Alma öğesi](../ide/code-snippets-schema-reference.md#imports-element)|**Alma** öğeleri için gruplandırma öğesi.|

## <a name="imports-element"></a>Alma öğesi

Tek `Import` tek öğeleri grupla.

```xml
<Imports>
    <Import>... </Import>
</Imports>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Alma öğesi](../ide/code-snippets-schema-reference.md#import-element)|İsteğe bağlı öğe. Kod parçacığı için içeri aktarılan ad alanlarını içerir. Bir `Imports` öğede sıfır veya daha fazla **Alma** öğesi olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Parçacık öğesi](../ide/code-snippets-schema-reference.md#snippet-element)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

## <a name="keyword-element"></a>Anahtar kelime öğesi

Kod parçacığı için özel bir anahtar sözcük belirtir. Kod parçacığı anahtar sözcükleri Visual Studio tarafından kullanılır ve çevrimiçi içerik sağlayıcılarının aramaya veya kategorilere ayırmaya yönelik özel anahtar sözcükler eklemek için kullandıkları standart bir yöntemi temsil eder.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Anahtar kelimeler öğesi](../ide/code-snippets-schema-reference.md#keywords-element)|Tek `Keyword` tek öğeleri grupla.|

Bir metin değeri gereklidir. Kod parçacığı için anahtar sözcük.

## <a name="keywords-element"></a>Anahtar kelimeler öğesi

Tek `Keyword` tek öğeleri grupla. Kod parçacığı anahtar sözcükleri Visual Studio tarafından kullanılır ve çevrimiçi içerik sağlayıcılarının aramaya veya kategorilere ayırmaya yönelik özel anahtar sözcükler eklemek için kullandıkları standart bir yöntemi temsil eder

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
</Keywords>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Anahtar kelime öğesi](../ide/code-snippets-schema-reference.md#keyword-element)|İsteğe bağlı öğe. Kod parçacığı için tek tek anahtar sözcükleri içerir. Bir `Keywords` öğede sıfır `Keyword` veya daha fazla öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Üstbilgi öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler içerir.|

## <a name="literal-element"></a>Edebi eleman

Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini tanımlar. Öğe, `Literal` tamamen parçacık içinde bulunan bir kod parçasının yerine birini tanımlamak için kullanılır, ancak büyük olasılıkla koda yerleştirildikten sonra özelleştirilmiş tir. Örneğin, değişmez değer dizeleri, sayısal değerler ve bazı değişken adları değişmez değer olarak bildirilmelidir.

Literals ve nesneler seçili veya sonu değeri olan bir **KIMLIK** öğesi içeremez. Değer, `$selected$` çağrıldığı zaman snippet'e eklenecek olan belgede seçili metni temsil eder. `$end$`kod parçacığı takıldıktan sonra imleci yerleştirmek için konumu işaretler.

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
|`Editable`|İsteğe bağlı `Boolean` öznitelik. Kod parçacığı eklendikten sonra değişmez değerde düzenleme yapıp yapamayacağınızı belirtir. Bu özniteliğin varsayılan `true`değeri .|

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Varsayılan öğe](../ide/code-snippets-schema-reference.md#default-element)|Gerekli öğe. Kod parçacığını eklediğinizde değişmez değerin alacağı varsayılan değeri belirtir. Bir `Literal` elementte `Default` tam olarak bir öğe olmalıdır.|
|[Fonksiyon öğesi](../ide/code-snippets-schema-reference.md#function-element)|İsteğe bağlı öğe. Değişmez değer Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir. Bir `Literal` öğede sıfır `Function` veya bir öğe olabilir.|
|[KIMLIK öğesi](../ide/code-snippets-schema-reference.md#id-element)|Gerekli öğe. Değişmez değer için benzersiz bir tanımlayıcı belirtir. Bir `Literal` elementte `ID` tam olarak bir öğe olmalıdır.|
|[ToolTip öğesi](../ide/code-snippets-schema-reference.md#tooltip-element)|İsteğe bağlı öğe. Değişmez değerin beklenen değerini ve kullanımını açıklar. Bir `Literal` öğede sıfır veya bir **Araç İpucu** öğesi olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Bildirimler öğesi](../ide/code-snippets-schema-reference.md#declarations-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini ve nesnelerini içerir.|

## <a name="namespace-element"></a>Namespace öğesi

Kod parçacığının derlenip çalışması için içeri aktarılması gereken ad alanını belirtir. `Namespace` Öğede belirtilen ad alanı, zaten yoksa, kodun başındaki bir `using` yönergeye veya `Imports` deyime otomatik olarak eklenir.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Alma öğesi](../ide/code-snippets-schema-reference.md#import-element)|Belirtilen ad alanını içeri aktarır.|

Bir metin değeri gereklidir. Bu metin, kod parçacığının içeri aktarıldığını varsaydığı bir ad alanını belirtir.

## <a name="object-element"></a>Nesne öğesi

Kod parçacığının düzenleme yapabileceğiniz nesnelerini tanımlar. Öğe, `Object` kod parçacığı tarafından gerekli olan ancak snippet'in dışında tanımlanması muhtemel bir öğeyi tanımlamak için kullanılır. Örneğin, Windows Forms denetimleri, ASP.NET denetimleri, nesne örnekleri ve tür örnekleri nesne olarak bildirilmelidir. Nesne bildirimleri, `Type` öğeyle yapılan bir tür belirtilmesi gerekir.

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
|`Editable`|İsteğe bağlı `Boolean` öznitelik. Kod parçacığı eklendikten sonra değişmez değerde düzenleme yapıp yapamayacağınızı belirtir. Bu özniteliğin varsayılan `true`değeri .|

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Varsayılan öğe](../ide/code-snippets-schema-reference.md#default-element)|Gerekli öğe. Kod parçacığını eklediğinizde değişmez değerin alacağı varsayılan değeri belirtir. Bir `Literal` elementte `Default` tam olarak bir öğe olmalıdır.|
|[Fonksiyon öğesi](../ide/code-snippets-schema-reference.md#function-element)|İsteğe bağlı öğe. Değişmez değer Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir. Bir `Literal` öğede sıfır `Function` veya bir öğe olabilir.|
|[KIMLIK öğesi](../ide/code-snippets-schema-reference.md#id-element)|Gerekli öğe. Değişmez değer için benzersiz bir tanımlayıcı belirtir. Bir `Literal` elementte `ID` tam olarak bir öğe olmalıdır.|
|[ToolTip öğesi](../ide/code-snippets-schema-reference.md#tooltip-element)|İsteğe bağlı öğe. Değişmez değerin beklenen değerini ve kullanımını açıklar. Bir `Literal` öğede sıfır veya bir **Araç İpucu** öğesi olabilir.|
|[Tür öğesi](../ide/code-snippets-schema-reference.md#type-element)|Gerekli öğe. Nesnenin türünü belirtir. Bir `Object` elementte `Type` tam olarak bir öğe olmalıdır.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Bildirimler öğesi](../ide/code-snippets-schema-reference.md#declarations-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini ve nesnelerini içerir.|

## <a name="reference-element"></a>Referans öğesi

Kod parçacığının gerek duyduğu derleme başvuruları hakkındaki bilgileri belirtir.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Montaj öğesi](../ide/code-snippets-schema-reference.md#assembly-element)|Gerekli öğe. Kod parçacığının başvurduğu derlemenin adını içerir. Bir `Reference` elementte `Assembly` tam olarak bir öğe olmalıdır.|
|[Url öğesi](../ide/code-snippets-schema-reference.md#url-element)|İsteğe bağlı öğe. Başvurulan derleme hakkında daha fazla bilgi sağlayan bir URL içerir. Bir `Reference` öğede sıfır `Url` veya bir öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Referanslar öğesi](../ide/code-snippets-schema-reference.md#references-element)|Öğeler için `Reference` gruplandırma öğesi.|

## <a name="references-element"></a>Referanslar öğesi

Tek `Reference` tek öğeleri grupla.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[Referans öğesi](../ide/code-snippets-schema-reference.md#reference-element)|İsteğe bağlı öğe. Kod parçacığı için derleme başvuruları hakkındaki bilgileri içerir. Bir `References` öğede sıfır `Reference` veya daha fazla öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Parçacık öğesi](../ide/code-snippets-schema-reference.md#snippet-element)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|

## <a name="shortcut-element"></a>Kısayol öğesi

Kod parçacığını eklemek için kullanılan kısayol metnini belirtir. Bir `Shortcut` öğenin metin değeri yalnızca alfasayısal karakterler içerebilir ve alt çizgi (_ ) çizilebilir.

> [!CAUTION]
> Alt puan (_) C++ snippet kısayollarında desteklenmez.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Üstbilgi öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler içerir.|

Metin değeri isteğe bağlıdır. Bu metin, kod parçacığını eklemek için bir kısayol olarak kullanılır.

## <a name="snippet-element"></a>Parçacık öğesi

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
|[Kod öğesi](../ide/code-snippets-schema-reference.md#code-element)|Gerekli öğe. Bir belge dosyasına eklemek istediğiniz kodu belirtir. Bir `Snippet` elementte `Code` tam olarak bir öğe olmalıdır.|
|[Bildirimler öğesi](../ide/code-snippets-schema-reference.md#declarations-element)|İsteğe bağlı öğe. Bir kod parçacığının düzenleyebileceğiniz bölümlerini oluşturan değişmez değerleri ve nesneleri belirtir. Bir `Snippet` öğede sıfır `Declarations` veya bir öğe olabilir.|
|[Alma öğesi](../ide/code-snippets-schema-reference.md#imports-element)|İsteğe bağlı öğe. Tek `Import` tek öğeleri grupla. Bir `Snippet` öğede sıfır `Imports` veya bir öğe olabilir.|
|[Referanslar öğesi](../ide/code-snippets-schema-reference.md#references-element)|İsteğe bağlı öğe. Tek `Reference` tek öğeleri grupla. Bir `Snippet` öğede sıfır `References` veya bir öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[CodeSnippet öğesi](../ide/code-snippets-schema-reference.md#codesnippet-element)|Visual Studio kod dosyalarına ekleyebileceğiniz bir başlık ve birden fazla IntelliSense Kod Parçacığı belirtmenizi sağlar.|

## <a name="snippettype-element"></a>SnippetType öğesi

Visual Studio'nun kod parçacığını nasıl eklediğini belirtir.

```xml
<SnippetType>
    SurroundsWith/Expansion
</SnippetType>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[SnippetTypes öğesi](../ide/code-snippets-schema-reference.md#snippettypes-element)|Öğeleri `SnippetType` grupla.|

Metin değeri şu değerlerden biri olmalıdır:

- `SurroundsWith`: kod parçacığının seçili bir kod parçasının etrafına yerleştirilmesini sağlar.

- `Expansion`: kod parçacığının imlecin arasına eklenmesini sağlar.

- `Refactoring`: c# refactoring sırasında kod parçacığının kullanıldığını belirtir. `Refactoring`özel kod parçacıkları kullanılamaz.

## <a name="snippettypes-element"></a>SnippetTypes öğesi

Tek `SnippetType` tek öğeleri grupla. `SnippetTypes` Öğe yoksa, kod parçacığı kodun herhangi bir yerine eklenebilir.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
</SnippetTypes>
```

|Alt öğe|Açıklama|
|-------------------|-----------------|
|[SnippetType öğesi](../ide/code-snippets-schema-reference.md#snippettype-element)|İsteğe bağlı öğe. Visual Studio'nun kod parçacığını kodun içine nasıl eklediğini belirtir. Bir `SnippetTypes` öğede sıfır `SnippetType` veya daha fazla öğe olabilir.|

|Üst öğe|Açıklama|
| - |-----------------|
|[Üstbilgi öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler belirtir.|

## <a name="title-element"></a>Başlık öğesi

Kod parçacığı için başlığı belirtir. Kod parçacığı nın `Title` öğesinde depolanan **başlık, Kod Snippet Seçici'de** ve **Kod Parçacıkları Yöneticisi'ndeki**kod snippet açıklamasında görünür.

```xml
<Title>
    Code Snippet Title
</Title>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Üstbilgi öğesi](../ide/code-snippets-schema-reference.md#header-element)|Kod parçacığı hakkında genel bilgiler belirtir.|

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
|[Edebi eleman](../ide/code-snippets-schema-reference.md#literal-element)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|
|[Nesne öğesi](../ide/code-snippets-schema-reference.md#object-element)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|

Bir metin değeri gereklidir. Bu metin, kod parçacığındaki nesne veya değişmez değer ile ilişkilendirilecek ToolTip açıklamasını belirtir.

## <a name="type-element"></a>Tür öğesi

Nesnenin türünü belirtir. Öğe, `Object` kod parçacığı tarafından gerekli olan ancak snippet'in dışında tanımlanması muhtemel bir öğeyi tanımlamak için kullanılır. Örneğin, Windows Forms denetimleri, ASP.NET denetimleri, nesne örnekleri ve tür örnekleri nesne olarak bildirilmelidir. Nesne bildirimleri, `Type` öğeyle yapılan bir tür belirtilmesi gerekir.

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

## <a name="url-element"></a>Url öğesi

Başvurulan derleme hakkında daha fazla bilgi sağlayan bir URL'yi belirtir.

> [!NOTE]
> Öğe `Url` yalnızca Visual Basic projeleri için desteklenir.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Üst öğe|Açıklama|
| - |-----------------|
|[Referans öğesi](../ide/code-snippets-schema-reference.md#reference-element)|Kod parçacığının gerek duyduğu derleme başvurularını belirtir.|

Bir metin değeri gereklidir. Bu metin, başvurulan derleme hakkında daha fazla bilgi içeren bir URL'yi belirtir. Bu URL, başvuru projeye eklenemediğinde görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)
- [İzlenecek Yol: Kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
