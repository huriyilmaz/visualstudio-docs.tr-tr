---
title: 'Microsoft Fakes: Derleme & oluşturma; adlandırma kuralları'
description: Yeni oluşturulan türler, Fakes ve parametreler için adlandırma kuralları da dahil olmak üzere kod oluşturma ve derleme Fakes seçenekleri ve sorunları öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 10469a19000000720d2a11dc9b48e4f849e30f81f8952429d39beefbfb74f396
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395414"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları

Bu makalede kod oluşturma ve derleme Fakes seçenekleri ve sorunları açıklanmıştır ve oluşturulan türler, üyeler ve parametreler Fakes adlandırma kuralları açıklanmıştır.

**Gereksinimler**

- Visual Studio Enterprise
- .NET Framework projesi
::: moniker range=">=vs-2019"
- .NET Core, .NET 5.0 ve SDK stili proje desteği Visual Studio 2019 Güncelleştirme 6'da önizlemeye alındı ve Güncelleştirme 8'de varsayılan olarak etkindir. Daha fazla bilgi için [bkz. .NET Core Microsoft Fakes SDK stili projeleri](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects)için bkz. .
::: moniker-end

## <a name="code-generation-and-compilation"></a>Kod oluşturma ve derleme

### <a name="configure-code-generation-of-stubs"></a>Saplamaların kod oluşturma ayarlarını yapılandırma

Saplama türleri oluşturma, *.fakes* dosya uzantısına sahip bir XML dosyasında yapılandırılır. Fakes çerçevesi, özel derleme görevleri aracılığıyla derleme MSBuild ve derleme zamanında bu dosyaları algılar. Kod Fakes oluşturucu, saplama türlerini bir derlemede derler ve projeye başvuru ekler.

Aşağıdaki örnek, içinde tanımlanan saplama türlerini *FileSystem.dll:*

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Tür filtreleme

Hangi türlerin saplamaları gerektiğini kısıtlamak için *.fakes* dosyasında filtreler ayarlandırabilirsiniz. Seçilen türlerin listesini oluşturmak için StubGeneration öğesinin altına sınırsız sayıda Clear, Add, Remove öğesi ekleyebilirsiniz.

Örneğin, aşağıdaki *.fakes* dosyası Sistem ve System.IO altındaki türler için saplamalar üretir, ancak Sistem'de "Tanıtıcı" içeren türleri dışlar:

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

Filtre dizeleri, eşleştirmenin nasıl yapılması gerektiğini tanımlamak için basit bir dil bilgisi kullanır:

- Filtreler varsayılan olarak büyük/büyük/büyük harfe duyarlı değildir; filtreleri bir alt dize eşleştirmesi gerçekleştirin:

     `el` "hello" ile eşler

- Filtrenin `!` sonuna eklemek, büyük/küçük harfe duyarlı bir eşleşme yapar:

     `el!` "hello" ile eşle

     `hello!` "hello" ile eşler

- Filtrenin `*` sonuna eklemek, dizenin ön eki ile eşleşmesini sağlar:

     `el*` "hello" ile eşle

     `he*` "hello" ile eşler

- Noktalı virgülle ayrılmış bir listede yer alan birden çok filtre, ayrık olarak bir araya gelir:

     `el;wo` "hello" ve "world" ile eşler

### <a name="stub-concrete-classes-and-virtual-methods"></a>Somut sınıfları ve sanal yöntemleri saplama

Varsayılan olarak, saplama türleri tüm korumalı olmayan sınıflar için oluşturulur. Saplama türlerini *.fakes* yapılandırma dosyası aracılığıyla sınıfları soyutlamaları için kısıtlamak mümkündür:

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

Kod Fakes oluşturucu, oluşturulan derlemede görünen türler için dolgu türleri ve saplama Fakes üretir. Dolgulu derlemenin iç türlerini Fakes ve test derlemenize görünür yapmak için Fakes, oluşturulan derleme derlemesi ve test derlemesi için görünürlük sağlayan dolgulu derleme koduna <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelikler ekleyin. Aşağıda bir örnek verilmiştir:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

**Kesin adlandırılmış derlemelerde iç türler**

Dolgulı derleme kesin olarak adlandırılmışsa ve derlemenin iç türlerine erişmek istiyorsanız:

- Hem test derlemenizin hem de Fakes derlemenin kesin olarak adlandırılmış olması gerekir.

- Testin ve derlemenin ortak anahtarlarını dolgulu derlemelerde **InternalsVisibleToAttribute** özniteliklerine Fakes derlemeye ekleyin. Dolgulu derleme kodundaki örnek öznitelikler, dolgulu derleme kesin olarak adlandırılmış olduğunda şöyle olur:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Dolgulı derleme kesin olarak adlandırılmışsa, Fakes çerçeve oluşturulan derlemeyi otomatik olarak Fakes imzalar. Test derlemeyi güçlü bir şekilde imzalamanız gerekiyor. Bkz. [Güçlü Adlandırılmış derlemeler.](/dotnet/framework/app-domains/strong-named-assemblies)

Fakes çerçevesi, oluşturulan tüm derlemeleri imzalamak için aynı anahtarı kullanır, bu nedenle bu kod parçacığını başlangıç noktası olarak kullanarak fakes derlemesi **için InternalsVisibleTo** özniteliğini dolgulu derleme kodunuza ekleyebilirsiniz.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

alternatif anahtarı içeren *.snk* dosyasının tam yolunu `KeyFile` `Fakes` \\ `Compilation` *.fakes* dosyasının öğesinde öznitelik değeri olarak belirterek, Fakes derlemesi için dolgulu derleme için oluşturduğunuz bir anahtar gibi farklı bir ortak anahtar belirtebilirsiniz. Örnek:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Daha sonra alternatif *.snk* dosyasının ortak anahtarını, dolgulu derleme kodundaki derleme derlemesi için InternalVisibleTo özniteliğinin ikinci parametresi olarak Fakes gerekir:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

Yukarıdaki örnekte ve değerleri `Alternate_public_key` `Test_assembly_public_key` aynı olabilir.

### <a name="optimize-build-times"></a>Derleme zamanlarını iyileştirme

Derleme derlemeleri Fakes derleme sürenizi önemli ölçüde artırabilir. Ayrı bir merkezi projede .NET Sistem derlemeleri Fakes üçüncü taraf derlemeler için derleme derlemeleri oluşturarak derleme süresini en aza abilirsiniz. Bu tür derlemeler makineniz üzerinde nadiren değişe bile, oluşturulan derlemeleri Fakes projelerde yeniden kullanabilirsiniz.

Birim testi projelerinden, proje klasöründeki FakesAssemblies altına Fakes derlemeler için derlenmiş derlemelere bir başvuru ekleyin.

1. Test projelerinize eşleşen .NET çalışma zamanı sürümüyle yeni bir Sınıf Kitaplığı oluşturun. Bunu bir Fakes. Önceden geliştirme. *class1.cs dosyasını* projeden kaldırın, gerekli değildir.

2. Gereken tüm Sistem ve üçüncü taraf derlemelere başvuru Fakes ekleyin.

3. Derlemelerin ve derlemelerin her biri için *bir .fakes* dosyası ekleyin.

4. Test projenize

    - Fakes çalışma zamanı DLL'lerine başvuru Fakes olun:

         *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - Oluşturduğunuz her derleme için Fakes, dosyanın içinde karşılık gelen DLL dosyasına bir *Fakes. Projenizin Prebuild\FakesAssemblies* klasörü.

### <a name="avoid-assembly-name-clashing"></a>Derleme adı ile çatışmaktan kaçının

Takım Derlemesi ortamında, tüm derleme çıkışları tek bir dizinde birleştirilir. Birden çok proje Fakes farklı sürümlerden derlemeler Fakes birbirini geçersiz kılacak şekilde olabilir. Örneğin, .NET Framework 2.0'dan TestProject1 fakes *mscorlib.dll* ve .NET Framework 4 için TestProject2 fakes *mscorlib.dll* her ikisi de bir *mscorlib.Fakes.dllFakes* derlemeye neden olur.

Bu sorunu önlemek için Fakes *.fakes* dosyalarını eklerken proje dışı başvurular Fakes derleme adları için otomatik olarak sürüm nitelikli derleme adları oluşturması gerekir. Derleme adı için Fakes derleme adı oluşturma adımlarını 1.000.000 Fakes ekleme:

MyAssembly derlemesi ve 1.2.3.4 sürümü göz Fakes derleme adı MyAssembly.1.2.3.4'dür. Fakes.

.fakes içinde Derleme öğesinin Version özniteliğini düzenleyerek bu sürümü değiştirebilir veya *kaldırebilirsiniz:*

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

   Örneğin, `System.Fakes` ad alanı Sistem ad alanının dolgu türlerini içerir.

- Küresel. Fakes boş ad alanının dolgu türünü içerir.

  **Tür adları**

- Dolgu türü adını oluşturmak için tür adına dolgu ön eki eklenir.

   Örneğin, ShimExample, Örnek türünün dolgu t t'dır.

- Saplama türü adını oluşturmak için tür adına saplama ön eki eklenir.

   Örneğin StubIExample, IExample türünün saplama t t tür.

  **Tür Bağımsız Değişkenleri ve İç İçe Tür Yapıları**

- Genel tür bağımsız değişkenleri kopyalanır.

- Dolgu türleri için iç içe tür yapısı kopyalanır.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Dolgu temsilcisi özelliği veya saplama temsilcisi alan adlandırma kuralları

**Boş bir** addan başlayarak alan adlandırma için temel kurallar:

- Yöntem adı eklenir.

- Yöntem adı açık bir arabirim uygulaması ise noktalar kaldırılır.

- Yöntem genelse `Of` *n* eklenir; burada *n, genel* yöntem bağımsız değişkenlerinin sayısıdır.

  **Özellik alıcı** veya ayarıcı gibi özel yöntem adları aşağıdaki tabloda açıklandığı gibi kabul edilir:

|Yöntem...|Örnek|Yöntem adı ekli|
|-|-|-|
|Oluşturucu |`.ctor`|`Constructor`|
|Statik **oluşturucu**|`.cctor`|`StaticConstructor`|
|**"_"** ile ayrılmış iki parçadan oluşan yöntem adına sahip bir erişimci (özellik getter'ları gibi)|*kind_name* (genel durum, ancak ECMA tarafından zorlanmaz)|*NameKind*, burada her iki parça da büyük harfle ve değiştirildi|
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
