---
title: 'Microsoft Fakes: Kod derleme& oluşturun; adlandırma kuralları'
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 155caf50e82f56c1db0b0b0a65a640f252f44063
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589337"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları

Bu makalede, Sahte kod oluşturma ve derleme seçenekleri ve sorunları tartışır ve Sahte oluşturulan türleri, üyeleri ve parametreleri için adlandırma kuralları açıklanır.

**Gereksinimler**

- Visual Studio Enterprise
- A .NET Framework projesi

> [!NOTE]
> .NET Standart projeler desteklenmez.

## <a name="code-generation-and-compilation"></a>Kod oluşturma ve derleme

### <a name="configure-code-generation-of-stubs"></a>Saplamaların kod oluşturma yapılandırma

Saplama türlerinin *üretimi,.fakes* dosya uzantısına sahip bir XML dosyasında yapılandırılır. Fakes çerçevesi, özel MSBuild görevleri aracılığıyla yapı sürecine entegre eder ve bu dosyaları oluşturma zamanında algılar. Fakes kod jeneratörü saplama türlerini bir derlemeye toplar ve projeye başvuru ekler.

Aşağıdaki örnek, *FileSystem.dll'de*tanımlanan saplama türlerini göstermektedir:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Tür filtreleme

Filtreler, *.fakes* dosyasında hangi türlerin saplanması gerektiğini kısıtlamak için ayarlanabilir. Seçili türlerin listesini oluşturmak için StubGeneration öğesinin altına sınırsız sayıda Açıkla, Ekle, Kaldır öğeleri ekleyebilirsiniz.

Örneğin, aşağıdaki *.fakes* dosyası Sistem ve System.IO ad boşlukları altındaki türler için saplamalar oluşturur, ancak Sistemde "Tanıtıcı" içeren türleri hariç tutar:

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

Filtre dizeleri, eşleştirmenin nasıl yapılması gerektiğini tanımlamak için basit bir dilbilgisi kullanır:

- Filtreler varsayılan olarak büyük/küçük harf duyarsızdır; filtreler bir alt dize eşleştirme gerçekleştirin:

     `el`"merhaba" eşleşir

- Filtrenin sonuna eklenmesi, `!` filtreyi kesin bir büyük/küçük harf duyarlı eşleşme yapar:

     `el!`"merhaba" ile eşleşmiyor

     `hello!`"merhaba" eşleşir

- Filtrenin sonuna eklenmesi `*` dize öneki eşleşir yapar:

     `el*`"merhaba" ile eşleşmiyor

     `he*`"merhaba" eşleşir

- Yarı sütunayrılmış bir listedeki birden çok filtre ayırma olarak birleştirilir:

     `el;wo`"merhaba" ve "dünya" ile eşleşiyor

### <a name="stub-concrete-classes-and-virtual-methods"></a>Saplama beton sınıfları ve sanal yöntemler

Varsayılan olarak, mühürsüz tüm sınıflar için saplama türleri oluşturulur. *.fakes* yapılandırma dosyası aracılığıyla saplama türlerini soyut sınıflarla sınırlamak mümkündür:

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

### <a name="internal-types"></a>Dahili tipler

Fakes kod jeneratörü oluşturulan Fakes montaj görülebilir türleri için şim türleri ve saplama türleri oluşturur. Sahteler ve test derlemeniz için görünür olan bir şimmli derlemenin iç türlerini yapmak için, oluşturulan Sahte derlemeye ve test derlemesine görünürlük sağlayan şim'li montaj koduna öznitelikleri ekleyin. <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Bir örneği aşağıda verilmiştir:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

**Güçlü adlandırılmış derlemelerde dahili türleri**

Şimmed derleme güçlü adlandırılmış ve derleme iç türleri erişmek istiyorsanız:

- Hem test derlemeniz hem de Sahte montaj Güçlü bir şekilde adlandırılmalıdır.

- Sitmed derlemelerinde **InternalsVisibleToAttribute** özniteliklerine test ve Fakes derlemesinin ortak anahtarlarını ekleyin. Şimmed derleme kodundaki örnek öznitelikler, şimmed derleme güçlü bir şekilde adlandırıldığında şu şekilde görünür:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Şimmed derleme güçlü adlandırılmışsa, Fakes çerçevesi otomatik olarak oluşturulan Fakes derlemesini güçlü bir şekilde imzalar. Test toplantısını güçlü bir şekilde imzalaman gerekiyor. Bkz. [Güçlü Adlandırılmış derlemeler.](/dotnet/framework/app-domains/strong-named-assemblies)

Fakes çerçevesi, oluşturulan tüm derlemeleri imzalamak için aynı anahtarı kullanır, böylece bu snippet'i sahte derleme kodunuza sahte derleme özniteliğini eklemek için başlangıç noktası olarak kullanabilirsiniz. **InternalsVisibleTo**

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

*.fakes* dosyasının `Fakes` \\ `Compilation` öğesindeki öznitelik değeri olarak `KeyFile` alternatif anahtarı içeren *.snk* dosyasına tam yolu belirterek, sahte derleme için oluşturduğunuz anahtar gibi farklı bir ortak anahtar belirtebilirsiniz. Örnek:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Daha sonra, shimmed derleme kodundaki Fakes derlemesi için InternalVisibleTo özniteliğinin ikinci parametresi olarak alternatif *.snk* dosyasının ortak anahtarını kullanmanız gerekir:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

Yukarıdaki örnekte, değerler `Alternate_public_key` ve `Test_assembly_public_key` değerler aynı olabilir.

### <a name="optimize-build-times"></a>Yapı sürelerini optimize et

Fakes derlemeleri önemli ölçüde yapı süresini artırabilir. .NET System derlemeleri ve üçüncü taraf derlemeleri için ayrı bir merkezi projede Sahte derlemeler oluşturarak yapı süresini en aza indirebilirsiniz. Bu tür derlemeler makinenizde nadiren değiştiğinden, diğer projelerde oluşturulan Sahte derlemeleri yeniden kullanabilirsiniz.

Birim test projelerinizden, proje klasöründe FakesAssemblies'in altına yerleştirilen derlenmiş Fakes derlemelerine bir başvuru ekleyin.

1. .NET çalışma zamanı sürümü test projelerinizle eşleşen yeni bir Sınıf Kitaplığı oluşturun. Buna Fakes.Prebuild diyelim. *class1.cs* dosyasını projeden kaldırın, gerekmedi.

2. Sahtelere ihtiyacınız olan tüm Sisteme ve üçüncü taraf derlemelerine referans ekleyin.

3. Her derleme için bir *.fakes* dosyası ekleyin ve oluşturun.

4. Test projenizden

    - Fakes çalışma zamanı DLL'ye bir referansın olduğundan emin olun:

         *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - Sahteler oluşturduğunuz her derleme için, projenizin *Fakes.Prebuild\FakesAssemblies* klasöründeki ilgili DLL dosyasına bir başvuru ekleyin.

### <a name="avoid-assembly-name-clashing"></a>Montaj adının çakışmasını önle

Takım Yapısı ortamında, tüm yapı çıktıları tek bir dizin halinde birleştirilir. Birden çok proje Fakes kullanıyorsa, farklı sürümlerden Gelen Sahte derlemeler birbirini geçersiz kılar. Örneğin, TestProject1 .NET Framework 2.0 ve TestProject2 fakes *mscorlib.dll* 'den *mscorlib.dll'yi* taklit eder.NET Framework 4 için her ikisi de *bir mscorlib'e verir. Fakes.dll* Sahte montaj.

Bu sorunu önlemek için, Fakes otomatik olarak *.fakes* dosyaları eklerken proje dışı başvurular için sürüm nitelikli Fakes montaj adları oluşturmalıdır. Sürüm nitelikli Fakes derleme adı, Fakes derleme adını oluşturduğunuzda bir sürüm numarası yerlebir eder:

Bir derleme MyAssembly ve sürüm 1.2.3.4 göz önüne alındığında, Fakes montaj adı MyAssembly.1.2.3.4.Fakes olduğunu.

*.fakes'deki*Assembly öğesinin Sürüm özniteliğini düzenleyerek bu sürümü değiştirebilir veya kaldırabilirsiniz:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Sahte adlandırma kuralları

### <a name="shim-type-and-stub-type-naming-conventions"></a>Şim türü ve saplama türü adlandırma kuralları

**Ad Alanları**

- . Ad alanına sahte sonek eklenir.

   Örneğin, `System.Fakes` ad alanı Sistem ad alanının şim türlerini içerir.

- Global.Fakes boş ad alanının şim türünü içerir.

  **Tür adları**

- Şim türü adını oluşturmak için tür adına Şim öneki eklenir.

   Örneğin, ŞimÖrnek Örnek türünün şim türüdür.

- Saplama önlemi, saplama türü adını oluşturmak için tür adına eklenir.

   Örneğin, StubIExample IExample türü saplama türüdür.

  **Tür Bağımsız Değişkenleri ve İç içe Yazı Yapıları**

- Genel tür bağımsız değişkenleri kopyalanır.

- İç içe yazı yapısı şim türleri için kopyalanır.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Şim temsilci özelliği veya saplama temsilci alanı adlandırma kuralları

Boş bir addan başlayarak alan adlandırma için **temel kurallar:**

- Yöntem adı eklenir.

- Yöntem adı açık bir arabirim uygulaması ysa, nokta kaldırılır.

- Yöntem genelse, `Of` *n* *n* genel yöntem bağımsız değişkenlerinin sayısı n'ye eklenir.

  Özellik getter veya ayarlayıcılar gibi **özel yöntem adları** aşağıdaki tabloda açıklandığı gibi kabul edilir:

|Yöntem ise...|Örnek|Eklenen yöntem adı|
|-|-|-|
|Bir **yapıcı**|`.ctor`|`Constructor`|
|Statik **bir yapıcı**|`.cctor`|`StaticConstructor`|
|"_" ile ayrılmış iki bölümden oluşan yöntem adı olan bir **erişimci** (özellik getters gibi)|*kind_name* (genel durum, ancak ECMA tarafından uygulanmaz)|*NameKind*, her iki parçanın büyük harfle büründüğü ve değiştirildiği|
||Mülkiyet getter`Prop`|`PropGet`|
||Özellik belirleyici`Prop`|`PropSet`|
||Olay toplayıcı|`Add`|
||Olay sökücü|`Remove`|
|İki bölümden oluşan bir **işleç**|`op_name`|`NameOp`|
|Örneğin: + işleç|`op_Add`|`AddOp`|
|Bir **dönüşüm işleci**için iade türü eklenir.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Dizinleyicilerin getters ve ayarlayıcıları** özelliğine benzer şekilde tedavi edilir. Bir dizinleyici için `Item`varsayılan adı .
> - **Parametre türü** adları dönüştürülür ve concatenated.
> - **Aşırı** yük belirsizliği olmadığı sürece iade türü yoksayılır. Aşırı yükleme amiguity varsa, dönüş türü adın sonuna eklenir.

### <a name="parameter-type-naming-conventions"></a>Parametre türü adlandırma kuralları

|Verilen|Eklenen dize...|
|-|-|
|A **türü**`T`|T<br /><br /> Ad alanı, iç içe yapı ve genel tikler bırakılır.|
|**Çıkış parametresi**`out T`|`TOut`|
|Ref **parametresi**`ref T`|`TRef`|
|Bir **dizi türü**`T[]`|`TArray`|
|**Çok boyutlu dizi** türü`T[ , , ]`|`T3`|
|**İşaretçi** türü`T*`|`TPtr`|
|**Genel bir tür**`T<R1, ...>`|`TOfR1`|
|**Genel bir tür bağımsız değişkeni** `!i``C<TType>`|`Ti`|
|Yöntemin **genel bir yöntem bağımsız değişkeni** `!!i``M<MMethod>`|`Mi`|
|İç **içe bir tür**`N.T`|`N`eklenir, sonra`T`|

### <a name="recursive-rules"></a>Özyinelemeli kurallar

Aşağıdaki kurallar özyinelemeli olarak uygulanır:

- Fakes, Fakes derlemelerini oluşturmak için C# kullandığından, geçersiz bir C# belirteci oluşturacak herhangi bir karakter "_" (alt puan) ile kaçar.

- Ortaya çıkan bir ad, beyan türünden herhangi bir üyeyle çakışıyorsa, 01'den başlayarak iki basamaklı bir sayaç ekleyerek bir numaralandırma şeması kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Fakes ile test altında kod yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
