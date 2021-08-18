---
title: 'Microsoft Fakes: & derleme kodu oluşturma; adlandırma kuralları'
description: Fakes üretilen türler, üyeler ve parametreler için adlandırma kuralları da dahil olmak üzere Fakes kod oluşturma ve derleme konularında seçenekler ve sorunlar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e683d40d93dca29445491b1e3fccdcd9c863b8f6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123105"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları

bu makalede Fakes kod oluşturma ve derleme içindeki seçenekler ve sorunlar ele alınmaktadır ve Fakes oluşturulan türler, üyeler ve parametreler için adlandırma kuralları açıklanmaktadır.

**Gereksinimler**

- Visual Studio Enterprise
- bir .NET Framework projesi
::: moniker range=">=vs-2019"
- Visual Studio 2019 güncelleştirme 6 ' da önizlenen .net Core, .net 5,0 ve SDK stili proje desteği ve güncelleştirme 8 ' de varsayılan olarak etkinleştirilmiştir. daha fazla bilgi için bkz. [.net Core ve SDK stilindeki projeler için Microsoft Fakes](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

## <a name="code-generation-and-compilation"></a>Kod oluşturma ve derleme

### <a name="configure-code-generation-of-stubs"></a>Saplamalar için kod oluşturmayı yapılandırma

Saplama türlerinin üretimi *. Fakes* dosya uzantısına sahıp bir XML dosyasında yapılandırılır. Fakes framework, derleme sürecinde özel MSBuild görevleri aracılığıyla tümleştirilir ve derleme zamanında bu dosyaları algılar. Fakes kod üreticisi, saplama türlerini bir derlemede derler ve başvuruyu projeye ekler.

Aşağıdaki örnek, *FileSystem.dll* tanımlı saplama türlerini gösterir:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Tür filtreleme

Filtreler, hangi türlerin saplaması olması gerektiğini kısıtlamak için *. Fakes* dosyasında ayarlanabilir. Seçili türlerin listesini oluşturmak için StubGeneration öğesinin altına sınırsız sayıda Clear, Add, remove öğesi ekleyebilirsiniz.

Örneğin, aşağıdaki *. Fakes* dosyası sistem ve System.IO ad alanları kapsamındaki türler için saplamalar üretir, ancak sistemde "tanıtıcı" içeren herhangi bir türü dışlar:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Clear />
    <Add Namespace="System!" />
    <Add Namespace="System.IO!"/>
    <Remove TypeName="Handle" />
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

Filtre dizeleri, eşleştirmesinin nasıl yapılacağını tanımlamak için basit bir dilbilgisi kullanır:

- Filtreler varsayılan olarak büyük/küçük harfe duyarlıdır; filtreler bir alt dize eşleştirmesi gerçekleştirir:

     `el` "Hello" ile eşleşir

- `!`Filtrenin sonuna eklemek, büyük/küçük harfe duyarlı eşleşme yapar:

     `el!` "Hello" ile eşleşmez

     `hello!` "Hello" ile eşleşir

- `*`Filtrenin sonuna eklemek, dizenin önekiyle aynı olur:

     `el*` "Hello" ile eşleşmez

     `he*` "Hello" ile eşleşir

- Noktalı virgülle ayrılmış bir listede birden çok filtre ayırıcı olarak birleştirilir:

     `el;wo` "Hello" ve "World" ile eşleşir

### <a name="stub-concrete-classes-and-virtual-methods"></a>Saplama somut sınıfları ve sanal yöntemler

Varsayılan olarak, saplama türleri tüm korumalı olmayan sınıflar için oluşturulur. Saplama türlerini, *. Fakes* yapılandırma dosyası aracılığıyla soyut sınıflarla kısıtlamak mümkündür:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Types>
      <Clear />
      <Add AbstractClasses="true"/>
    </Types>
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

### <a name="internal-types"></a>İç türler

Fakes kod oluşturucu, oluşturulan Fakes derlemesine görünür olan türler için dolgu türleri ve saplama türleri oluşturur. shimmed derlemesinin iç türlerini Fakes ve test derlemenizin görünür hale getirmek için, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> oluşturulan Fakes derlemesine ve test derlemesine görünürlük sağlayan shimmed derleme koduna öznitelikler ekleyin. Aşağıda bir örnek verilmiştir:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

**Kesin adlandırılmış derlemelerde iç türler**

Shimmed derlemesi kesin olarak adlandırılmışsa ve derlemenin iç türlerine erişmek istiyorsanız:

- hem test derlemeniz hem de Fakes derlemesi kesin adlandırılmış olmalıdır.

- test ve Fakes derlemesinin ortak anahtarlarını shimmed derlemelerindeki **ınternalsvisibletoattribute** özniteliklerine ekleyin. Shimmed derleme kodundaki örnek özniteliklerin, shimmed derlemesi kesin olarak adlandırılmışsa şöyle görünür:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

shimmed derlemesi kesin olarak adlandırılmışsa, Fakes framework oluşturulan Fakes derlemesini otomatik olarak kesin olarak imzalar. Test derlemesini güçlü bir şekilde imzalamanız gerekir. Bkz. [tanımlayıcı adlandırılmış derlemeler](/dotnet/framework/app-domains/strong-named-assemblies).

Fakes framework, tüm oluşturulan derlemeleri imzalamak için aynı anahtarı kullanır; bu nedenle, Fakes derlemesinin **ınternalsvisibleto** özniteliğini shimmed derleme kodunuza eklemek için bu kod parçacığını bir başlangıç noktası olarak kullanabilirsiniz.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

 `KeyFile` `Fakes` \\ `Compilation` *. fakes* dosyasının öğesinde öznitelik değeri olarak alternatif anahtarı içeren. snk dosyasının tam yolunu belirterek, Fakes derlemesi için shimmed derlemesi için oluşturduğunuz bir anahtar gibi farklı bir ortak anahtar belirtebilirsiniz. Örnek:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

daha sonra, shimmed derleme kodundaki Fakes derlemesi için ınternalvisibleto özniteliğinin ikinci parametresi olarak alternatif *. snk* dosyasının ortak anahtarını kullanmanız gerekir:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

Yukarıdaki örnekte, değerleri `Alternate_public_key` ve `Test_assembly_public_key` aynı olabilir.

### <a name="optimize-build-times"></a>Derleme sürelerini iyileştirme

Fakes derlemelerinin derlenmesi, derleme zamandan önemli ölçüde artabilir. ayrı bir merkezi projede .net sistem derlemeleri ve üçüncü taraf derlemeler için Fakes derlemeleri oluşturarak derleme süresini en aza indirmiş olabilirsiniz. bu tür derlemeler makinenizde nadiren değiştiğinden, oluşturulan Fakes derlemelerini diğer projelerde yeniden kullanabilirsiniz.

birim testi projelerinizden, proje klasöründe FakesAssemblies altına yerleştirilmiş derlenmiş Fakes derlemelerine bir başvuru ekleyin.

1. Test projelerinizle eşleşen .NET çalışma zamanı sürümü ile yeni bir sınıf kitaplığı oluşturun. Fakes arayalım. Prebuild. Bu gerekli değil, *Class1. cs* dosyasını projeden kaldırın.

2. için Fakes gereken tüm sistem ve üçüncü taraf derlemelere başvuru ekleyin.

3. Her derleme ve derleme için bir *. Fakes* dosyası ekleyin.

4. Test projenizden

    - Fakes çalışma zamanı DLL 'sine başvurunuz olduğundan emin olun:

         *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - Fakes oluşturduğunuz her derleme için, Fakes karşılık gelen DLL dosyasına bir başvuru ekleyin *. Projenizin Prebuild\FakesAssemblies* klasörü.

### <a name="avoid-assembly-name-clashing"></a>Derleme adının çakışmasını önleyin

Bir ekip derleme ortamında, tüm derleme çıkışları tek bir dizinde birleştirilir. birden çok proje Fakes kullanıyorsa, farklı sürümlerden Fakes derlemelerin birbirini geçersiz kılmasına kaynaklanabilir. örneğin, .NET Framework 4 için .NET Framework 2,0 ve TestProject2 fakes *mscorlib.dll* *mscorlib.dll* fakes, her ikisi de *mscorlib.Fakes.dll* Fakes derlemesine neden olur.

bu sorundan kaçınmak için, Fakes *. fakes* dosyalarını eklerken proje dışı başvurular için otomatik olarak sürüm Fakes derleme adları oluşturmalıdır. sürüm nitelikli Fakes bütünleştirilmiş kod adı, Fakes bütünleştirilmiş kod adı oluştururken bir sürüm numarası katıştırır:

bir derleme myassembly ve bir sürüm 1.2.3.4 verildiğinde Fakes bütünleştirilmiş kod adı myassembly. 1.2.3.4 olur. Fakes.

*. Fakes* içindeki derleme öğesinin sürüm özniteliğini düzenleyerek bu sürümü değiştirebilir veya kaldırabilirsiniz:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Fakes adlandırma kuralları

### <a name="shim-type-and-stub-type-naming-conventions"></a>Dolgu türü ve saplama türü adlandırma kuralları

**Ad alanları**

- . Fakes soneki ad alanına eklenir.

   Örneğin, `System.Fakes` ad alanı sistem ad alanının dolgu türlerini içerir.

- Genel. Fakes boş ad alanının dolgu türünü içerir.

  **Tür adları**

- Dolgu türü adı oluşturmak için tür adına dolgu ön eki eklenir.

   Örneğin, Shimex, örnek türünün dolgu türüdür.

- Saplama türü adı derlemek için, tür adına saplama ön eki eklenir.

   Örneğin, StubIExample, IExample türünün saplama türüdür.

  **Tür bağımsız değişkenleri ve Iç Içe tür yapıları**

- Genel tür bağımsız değişkenleri kopyalanır.

- İç içe tür yapısı dolgu türleri için kopyalanır.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Dolgu temsilcisi özelliği veya saplama temsilcisi alan adlandırma kuralları

Boş bir adından başlayarak alan adlandırmayla ilgili **temel kurallar** :

- Yöntem adı eklenir.

- Yöntem adı açık arabirim bir uygulama ise, noktalar kaldırılır.

- Yöntem geneldir ise n, `Of`  genel yöntem bağımsız değişkenlerinin sayısıdır  .

  Özellik alıcısı veya ayarlayıcılar gibi **özel yöntem adları** aşağıdaki tabloda açıklandığı gibi değerlendirilir:

|If yöntemi...|Örnek|Yöntem adı eklendi|
|-|-|-|
|Bir **Oluşturucu**|`.ctor`|`Constructor`|
|Statik **Oluşturucu**|`.cctor`|`StaticConstructor`|
|"_" (Özellik alıcıları gibi) ile ayrılmış iki bölümden oluşan Yöntem adına sahip bir **erişimci**|*kind_name* (yaygın durum, ancak ECMA tarafından zorlanmaz)|*NameKind*, her iki parça da büyük harfli ve değiştirilmiş|
||Özelliğin alıcısı `Prop`|`PropGet`|
||Özelliğin ayarlayıcısı `Prop`|`PropSet`|
||Olay Ekleyici|`Add`|
||Olay çıkarıcı|`Remove`|
|İki bölümden oluşan bir **operatör**|`op_name`|`NameOp`|
|Örneğin: + işleci|`op_Add`|`AddOp`|
|Bir **dönüştürme işleci** için, dönüş türü eklenir.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Dizin oluşturucularının alıcıları ve ayarlayıcıları** özelliğe benzer şekilde işlenir. Bir dizin oluşturucunun varsayılan adı `Item` .
> - **Parametre türü** adları dönüştürülür ve bitiştirilir.
> - Aşırı yükleme belirsizliğe neden olmadıkça **dönüş türü** yok sayılır. Bir aşırı yükleme varsa, dönüş türü adın sonuna eklenir.

### <a name="parameter-type-naming-conventions"></a>Parametre türü adlandırma kuralları

|İşlemlerindeki|Eklenen dize...|
|-|-|
|Bir **tür**`T`|T<br /><br /> Ad alanı, iç içe yapı ve genel olarak bırakılır.|
|**Out parametresi**`out T`|`TOut`|
|Bir **ref parametresi**`ref T`|`TRef`|
|Bir **dizi türü**`T[]`|`TArray`|
|**Çok boyutlu dizi** türü`T[ , , ]`|`T3`|
|Bir **işaretçi** türü `T*`|`TPtr`|
|**Genel tür**`T<R1, ...>`|`TOfR1`|
|Türünde **genel bir tür bağımsız değişkeni** `!i``C<TType>`|`Ti`|
|Metodun **genel metot bağımsız değişkeni** `!!i``M<MMethod>`|`Mi`|
|**İç içe bir tür**`N.T`|`N` eklendiğinde, `T`|

### <a name="recursive-rules"></a>Özyinelemeli kurallar

Aşağıdaki kurallar yinelemeli olarak uygulanır:

- Fakes, Fakes derlemeleri oluşturmak için C# kullandığından, geçersiz bir C# belirteci üreten herhangi bir karakter "_" (alt çizgi) öğesine atlanmalıdır.

- Elde edilen bir ad, bildirim türünün herhangi bir üyesiyle çakışıyor, bir numaralandırma düzeni, 01 ' den başlayarak iki basamaklı bir sayaç eklenerek kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Fakes test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
