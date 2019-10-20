---
title: 'Microsoft Fakes: & derleme kodu oluşturma; adlandırma kuralları'
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: e29b0b05b836dd4072b704bfd48cfb85cde50927
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665244"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları

Bu makalede, Fakes kod oluşturma ve derleme içindeki seçenekler ve sorunlar ele alınmaktadır ve Fakes üretilen türler, Üyeler ve parametreler için adlandırma kuralları açıklanmaktadır.

**Requirements**

- Visual Studio Enterprise
- Bir .NET Framework projesi

> [!NOTE]
> .NET Standard projeler desteklenmez.

## <a name="code-generation-and-compilation"></a>Kod oluşturma ve derleme

### <a name="configure-code-generation-of-stubs"></a>Saplamalar için kod oluşturmayı yapılandırma

Saplama türlerinin üretimi *. Fakes* dosya uzantısına sahıp bir XML dosyasında yapılandırılır. Fakes çerçevesi, derleme sürecinde özel MSBuild görevleri aracılığıyla tümleştirilir ve derleme zamanında bu dosyaları algılar. Fakes kod Oluşturucusu, saplama türlerini bir derlemede derler ve başvuruyu projeye ekler.

Aşağıdaki örnek, *FileSystem. dll*dosyasında tanımlanan saplama türlerini gösterir:

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

- Filtrenin sonuna `!` eklemek, büyük/küçük harfe duyarlı eşleşme yapar:

     `el!` "Hello" ile eşleşmiyor

     `hello!` "Hello" ile eşleşir

- Filtrenin sonuna `*` eklemek, dizenin önekiyle aynı olur:

     `el*` "Hello" ile eşleşmiyor

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

Fakes kod Oluşturucusu, oluşturulan Fakes derlemesine görünür olan türler için dolgu türleri ve saplama türleri oluşturur. Shimmed derlemesinin iç türlerini Fakes ve test derlemelerinizi görünür hale getirmek için, oluşturulan Fakes derlemesine ve test derlemesine görünürlük sağlayan shimmed derleme koduna <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelikleri ekleyin. Örnek buradadır:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

**Kesin adlandırılmış derlemelerde iç türler**

Shimmed derlemesi kesin olarak adlandırılmışsa ve derlemenin iç türlerine erişmek istiyorsanız:

- Hem test derlemeniz hem de Fakes derlemesi kesin adlandırılmış olmalıdır.

- Test ve Fakes derlemesinin ortak anahtarlarını shimmed derlemelerindeki **InternalsVisibleToAttribute** özniteliklerine ekleyin. Shimmed derleme kodundaki örnek özniteliklerin, shimmed derlemesi kesin olarak adlandırılmışsa şöyle görünür:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Shimmed derlemesi kesin olarak adlandırılmışsa, Fakes çerçevesi oluşturulan Fakes derlemesini otomatik olarak kesin olarak imzalar. Test derlemesini güçlü bir şekilde imzalamanız gerekir. Bkz. [tanımlayıcı adlandırılmış derlemeler](/dotnet/framework/app-domains/strong-named-assemblies).

Fakes çerçevesi, tüm oluşturulan derlemeleri imzalamak için aynı anahtarı kullanır; bu nedenle, Fakes derlemesinin **InternalsVisibleTo** özniteliğini shimmed derleme kodunuza eklemek için bu kod parçacığını bir başlangıç noktası olarak kullanabilirsiniz.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

@No__t_2 \\ `KeyFile` özniteliği değeri olarak alternatif anahtarı içeren *. snk* dosyasının tam yolunu belirterek, Fakes derlemesi için shimmed derlemesi için oluşturduğunuz anahtar gibi farklı bir ortak anahtar belirtebilirsiniz @no__t_ *. Fakes* dosyasının 4 öğesi. Örneğin:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Daha sonra, shimmed derleme kodundaki Fakes derlemesi için ınternalvisibleto özniteliğinin ikinci parametresi olarak alternatif *. snk* dosyasının ortak anahtarını kullanmanız gerekir:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

Yukarıdaki örnekte, değerler `Alternate_public_key` ve `Test_assembly_public_key` aynı olabilir.

### <a name="optimize-build-times"></a>Derleme sürelerini iyileştirme

Fakes derlemelerinin derlenmesi, derleme zamandan önemli ölçüde artabilir. Ayrı bir merkezi projede .NET sistem derlemeleri ve üçüncü taraf derlemeler için Fakes derlemelerini oluşturarak derleme süresini en aza indirmiş olabilirsiniz. Bu tür derlemeler makinenizde nadiren değiştiğinden, oluşturulan Fakes derlemelerini diğer projelerde yeniden kullanabilirsiniz.

Birim testi projelerinizden, proje klasöründe FakesAssemblies altına yerleştirilmiş derlenmiş Fakes derlemelerine bir başvuru ekleyin.

1. Test projelerinizle eşleşen .NET çalışma zamanı sürümü ile yeni bir sınıf kitaplığı oluşturun. Daha sonra Fakes. prebuild ' i arayalım. *Class1.cs* dosyasını projeden kaldırın, gerekli değildir.

2. Fakes için gereken tüm sistem ve üçüncü taraf derlemelere başvuru ekleyin.

3. Her derleme ve derleme için bir *. Fakes* dosyası ekleyin.

4. Test projenizden

    - Fakes çalışma zamanı DLL 'sine başvurunuz olduğundan emin olun:

         *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - Fakes 'i oluşturduğunuz her derleme için, projenizin *Fakes. Prebuild\FakesAssemblies* klasöründe KARŞıLıK gelen DLL dosyasına bir başvuru ekleyin.

### <a name="avoid-assembly-name-clashing"></a>Derleme adının çakışmasını önleyin

Bir ekip derleme ortamında, tüm derleme çıkışları tek bir dizinde birleştirilir. Birden çok proje Fakes kullanıyorsa, farklı sürümlerden gelen Fakes derlemelerinin birbirini geçersiz kılmasını sağlayabilir. Örneğin, TestProject1 Fakes *mscorlib. dll* .NET Framework 2,0 ve TestProject2 Fakes *mscorlib.* dll ' den .NET Framework 4 için her ikisi de mscorlib 'e neden olur *. Fakes. dll* Fakes derlemesi.

Bu sorundan kaçınmak için, Fakes, *. Fakes* dosyalarını eklerken proje dışı başvurular için otomatik olarak sürüm nitelikli bir derleme adları oluşturmalıdır. Sürüm nitelikli Fakes derleme adı, Fakes derleme adı oluştururken bir sürüm numarası katıştırır:

Bir derleme MyAssembly ve bir sürüm 1.2.3.4 verildiğinde, Fakes derleme adı MyAssembly. 1.2.3.4. Fakes ' dir.

*. Fakes*içindeki derleme öğesinin sürüm özniteliğini düzenleyerek bu sürümü değiştirebilir veya kaldırabilirsiniz:

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

- Global. Fakes boş ad alanının dolgu türünü içerir.

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

- Yöntem geneldir ise, *n* , genel yöntem bağımsız değişkenlerinin sayısıdır `Of`*n* eklenir.

  Özellik alıcısı veya ayarlayıcılar gibi **özel yöntem adları** aşağıdaki tabloda açıklandığı gibi değerlendirilir:

|If yöntemi...|Örnek|Yöntem adı eklendi|
|-|-|-|
|Bir **Oluşturucu**|`.ctor`|`Constructor`|
|Statik **Oluşturucu**|`.cctor`|`StaticConstructor`|
|"_" (Özellik alıcıları gibi) ile ayrılmış iki bölümden oluşan Yöntem adına sahip bir **erişimci**|*kind_name* (yaygın durum, ancak ECMA tarafından zorlanmaz)|*NameKind*, her iki parça da büyük harfli ve değiştirilmiş|
||Özellik `Prop` alıcısı|`PropGet`|
||Özellik `Prop` ayarlayıcısı|`PropSet`|
||Olay Ekleyici|`Add`|
||Olay çıkarıcı|`Remove`|
|İki bölümden oluşan bir **operatör**|`op_name`|`NameOp`|
|Örneğin: + işleci|`op_Add`|`AddOp`|
|Bir **dönüştürme işleci**için, dönüş türü eklenir.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Dizin oluşturucularının alıcıları ve ayarlayıcıları** özelliğe benzer şekilde işlenir. Bir dizin oluşturucunun varsayılan adı `Item`.
> - **Parametre türü** adları dönüştürülür ve bitiştirilir.
> - Aşırı yükleme belirsizliğe neden olmadıkça **dönüş türü** yok sayılır. Bir aşırı yükleme varsa, dönüş türü adın sonuna eklenir.

### <a name="parameter-type-naming-conventions"></a>Parametre türü adlandırma kuralları

|İşlemlerindeki|Eklenen dize...|
|-|-|
|Bir **tür** `T`|T<br /><br /> Ad alanı, iç içe yapı ve genel olarak bırakılır.|
|**Out parametresi** `out T`|`TOut`|
|Bir **ref parametresi** `ref T`|`TRef`|
|Bir **dizi türü** `T[]`|`TArray`|
|**Çok boyutlu dizi** türü `T[ , , ]`|`T3`|
|Bir **işaretçi** türü `T*`|`TPtr`|
|**Genel tür** `T<R1, ...>`|`TOfR1`|
|@No__t_2 türünde **genel tür bağımsız değişken** `!i`|`Ti`|
|Metodun **genel metot bağımsız değişkeni** `!!i` `M<MMethod>`|`Mi`|
|**İç içe bir tür** `N.T`|`N` eklendiğinde `T`|

### <a name="recursive-rules"></a>Özyinelemeli kurallar

Aşağıdaki kurallar yinelemeli olarak uygulanır:

- Fakes, Fakes derlemelerini oluşturmak için kullandığından C# , geçersiz C# bir belirteç üreten herhangi bir karakter "_" (alt çizgi) öğesine atlanmalıdır.

- Elde edilen bir ad, bildirim türünün herhangi bir üyesiyle çakışıyor, bir numaralandırma düzeni, 01 ' den başlayarak iki basamaklı bir sayaç eklenerek kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Fakes ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
