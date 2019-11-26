---
title: Microsoft Fakes 'te kod oluşturma, derleme ve adlandırma kuralları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 20221de4-2a9e-4787-b99a-b5855bb90872
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ff1d953dc853beba8ef836b1eab03140ee0b1e0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300391"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, Fakes kod oluşturma ve derleme konusundaki seçenekler ve sorunlar ele alınmaktadır ve Fakes üretilen türler, Üyeler ve parametreler için adlandırma kuralları açıklanmaktadır.

 **Requirements**

- Visual Studio Enterprise

## <a name="BKMK_In_this_topic"></a>Bu konuda
 [Kod oluşturma ve derleme](#BKMK_Code_generation_and_compilation)

- [Kod saplamalarını yapılandırma](#BKMK_Configuring_code_generation_of_stubs) • [tür filtreleme](#BKMK_Type_filtering) • [kalıntıları oluşturuluyor somut sınıflar ve sanal yöntemler](#BKMK_Stubbing_concrete_classes_and_virtual_methods) • [iç türler](#BKMK_Internal_types) • [derleme sürelerini iyileştirme](#BKMK_Optimizing_build_times) • [derleme adının çakışmasını önleme](#BKMK_Avoiding_assembly_name_clashing)

  [Fakes adlandırma kuralları](#BKMK_Fakes_naming_conventions)

- [Dolgu türü ve saplama türü adlandırma kuralları](#BKMK_Shim_type_and_stub_type_naming_conventions) • [Dolgu temsilcisi özelliği veya saplama temsilcisi alan adlandırma kuralları](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions) • [parametre türü adlandırma kuralları](#BKMK_Parameter_type_naming_conventions) • [Özyinelemeli kurallar](#BKMK_Recursive_rules)

  [Dış kaynaklar](#BKMK_External_resources)

- [Kılavuz](#BKMK_Guidance)

## <a name="BKMK_Code_generation_and_compilation"></a>Kod oluşturma ve derleme

### <a name="BKMK_Configuring_code_generation_of_stubs"></a>Saplamalar için kod oluşturmayı yapılandırma
 Saplama türlerinin üretimi. Fakes dosya uzantısına sahip bir XML dosyasında yapılandırılır. Fakes framework yapı işleminde özel MSBuild görevleri ile tümleştirir ve bu dosyaları derleme sırasında algılar. Fakes Kod Oluşturucusu bir derleme içine Koçan türleri derler ve projeye başvuruyu ekler.

 Aşağıdaki örnek, FileSystem. dll dosyasında tanımlanan saplama türlerini gösterir:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>

```

### <a name="BKMK_Type_filtering"></a>Tür filtreleme
 Filtreler, hangi türlerin saplaması olması gerektiğini kısıtlamak için. Fakes dosyasında ayarlanabilir. Temizle, Ekle, Kaldır öğelerini seçili türlerinin listesini oluşturmak için StubGeneration öğesinin altındaki sınırsız sayıda ekleyebilirsiniz.

 Örneğin, bu. Fakes dosyası sistem ve System.IO ad alanları kapsamındaki türler için saplamalar oluşturur, ancak sistemde "tanıtıcı" içeren herhangi bir türü dışlar:

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

 Filtre dizeleri nasıl yapılması gerektiğini tanımlamak için basit bir dil bilgisi kullanın:

- Filtreleri, varsayılan olarak büyük küçük harf duyarsız; eşleşen alt dizenin filtreleri uygulayın:

     `el` "Hello" ile eşleşir

- Filtrenin sonuna `!` eklemek, büyük/küçük harfe duyarlı eşleşme yapar:

     `el!` "Hello" ile eşleşmiyor

     `hello!` "Hello" ile eşleşir

- Filtrenin sonuna `*` eklemek, dizenin ön ekiyle eşleşir:

     `el*` "Hello" ile eşleşmiyor

     `he*` "Hello" ile eşleşir

- Noktalı virgülle ayrılmış bir liste içinde birden çok filtre ayırım yaparak birleştirilebilir.

     `el;wo` "Hello" ve "World" ile eşleşir

### <a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a>Kalıntıları oluşturuluyor somut sınıflar ve sanal yöntemler
 Varsayılan olarak, Koçan türleri korumalı olmayan tüm sınıflar için oluşturulur. Saplama türlerini,. Fakes yapılandırma dosyası aracılığıyla soyut sınıflarla kısıtlamak mümkündür:

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

### <a name="BKMK_Internal_types"></a>İç türler
 Fakes kod Oluşturucusu, oluşturulan Fakes derlemesine görünür olan türler için dolgu türleri ve saplama türleri oluşturacaktır. Shimmed derlemesinin iç türlerini Fakes ve test derlemelerinizi görünür hale getirmek için, oluşturulan Fakes derlemesine ve test derlemesine görünürlük sağlayan shimmed derleme koduna <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelikleri ekleyin. Örnek buradadır:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

 **Kesin adlandırılmış derlemelerde iç türler**

 Shimmed derlemesi kesin olarak adlandırılmışsa ve derlemenin iç türlerine erişim istiyorsanız:

- Hem test derlemeniz hem de Fakes derlemeniz kesin adlandırılmış olmalıdır.

- Test ve Fakes derlemesinin ortak anahtarlarını shimmed derlemelerindeki **InternalsVisibleToAttribute** özniteliklerine eklemeniz gerekir. Shimmed derlemesi kesin olarak adlandırılmışsa, shimmed derleme kodundaki örnek özniteliklerimiz şöyle görünür:

  ```csharp
  // FileSystem\AssemblyInfo.cs
  [assembly: InternalsVisibleTo("FileSystem.Fakes",
      PublicKey=<Fakes_assembly_public_key>)]
  [assembly: InternalsVisibleTo("FileSystem.Tests",
      PublicKey=<Test_assembly_public_key>)]
  ```

  Shimmed derlemesi kesin olarak adlandırılmışsa, Fakes çerçevesi oluşturulan Fakes derlemesini otomatik olarak kesin olarak imzalayacaktır. Test derlemesi strong oturum gerekir. Bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](https://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).

  Fakes çerçevesi, tüm oluşturulan derlemeleri imzalamak için aynı anahtarı kullanır; bu nedenle, Fakes derlemesinin **InternalsVisibleTo** özniteliğini shimmed derleme kodunuza eklemek için bu kod parçacığını bir başlangıç noktası olarak kullanabilirsiniz.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

 **. Fakes** dosyasının `Fakes`\\`Compilation` öğesindeki `KeyFile` özniteliği değeri olarak alternatif anahtarı içeren **. snk** dosyasının tam yolunu belirterek, Fakes derlemesi için, shimmed derlemesi için oluşturduğunuz bir anahtar gibi farklı bir ortak anahtar belirtebilirsiniz. Örneğin:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>

```

 Daha sonra, shimmed derleme kodundaki Fakes derlemesi için ınternalvisibleto özniteliğinin ikinci parametresi olarak alternatif **. snk** dosyasının ortak anahtarını kullanmanız gerekir:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

 Yukarıdaki örnekte, değerler `Alternate_public_key` ve `Test_assembly_public_key` aynı olabilir.

### <a name="BKMK_Optimizing_build_times"></a>Derleme sürelerini iyileştirme
 Fakes derlemelerinin derlemesi yapım sürenizi önemli ölçüde artırabilir. Ayrı merkezi bir proje içinde .NET System derlemeleri için Fakes derlemeleri ve üçüncü taraf derlemeler oluşturarak derleme zamanını en aza indirebilirsiniz. Bu tür derlemeler makinenizde nadiren değiştiğinden, oluşturulan Fakes derlemeleri diğer projelerde yeniden kullanabilirsiniz.

 Birim testi projelerinizden, proje klasöründeki FakesAssemblies altına yerleştirilmiş derlenmiş Fakes derlemelerine bir başvuru almanız yeterlidir.

1. Test projelerinizle eşleşen .NET çalışma zamanı sürümünü ile yeni bir sınıf kitaplığı oluşturun. Daha sonra Fakes. prebuild ' i arayalım. Class1.cs dosyasını projeden kaldırın, gerekli değildir.

2. Tüm sistem başvuru ekleyin ve üçüncü taraf derlemeler için Fakes gerekir.

3. Her derleme ve derleme için bir. Fakes dosyası ekleyin.

4. Test projenizden

    - Fakes çalışma zamanı DLL başvuru sahip olduğunuzdan emin olun:

         C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll

    - Fakes 'i oluşturduğunuz her derleme için, projenizin Fakes. Prebuild\FakesAssemblies klasöründe karşılık gelen DLL dosyasına bir başvuru ekleyin.

### <a name="BKMK_Avoiding_assembly_name_clashing"></a>Derleme adının çakışmasını önleme
 Bir ekip ortamında, tüm yapı çıkışları tek bir dizin içinde birleştirilir. Fakes kullanan birden fazla proje söz konusu olduğunda, farklı sürümdeki daha Fakes derlemelerinin birbirini geçersiz kılmasını sağlayabilir. Örneğin, TestProject1 Fakes mscorlib. dll .NET Framework 2,0 ve TestProject2 Fakes mscorlib. dll ' den .NET Framework 4 için her ikisi de mscorlib 'e neden olur. Fakes. dll Fakes derlemesi.

 Bu sorundan kaçınmak için, Fakes,. Fakes dosyalarını eklerken proje dışı başvurular için otomatik olarak sürüm nitelikli bir derleme adları oluşturmalıdır. Fakes derleme adı oluştururken bir sürüm nitelikli Fakes derleme adı bir sürüm numarası gömer:

 Bir derleme MyAssembly ve sürüm 1.2.3.4, Fakes derleme adı MyAssembly.1.2.3.4.fakes'dir.

 . Fakes içindeki derleme öğesinin sürüm özniteliğini düzenleyerek bu sürümü değiştirebilir veya kaldırabilirsiniz:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>

```

## <a name="BKMK_Fakes_naming_conventions"></a>Fakes adlandırma kuralları

### <a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a>Dolgu türü ve saplama türü adlandırma kuralları
 **Ad Alanları**

- . Fakes sonekini ad alanına eklenir.

   Örneğin, `System.Fakes` ad alanı sistem ad alanının dolgu türlerini içerir.

- Global.Fakes boş ad alanını dolgu türünü içerir.

  **Tür adları**

- Dolgu/Shim öneki Dolgu türü adı yapılandırmak için tür adına eklenir.

   Örneğin, ShimExample Example türünün shim türüdür.

- Stub öneki stub türü adı yapılandırmak için tür adına eklenir.

   Örneğin, Stubıexample IExample türünün stub türüdür.

  **Tür bağımsız değişkenleri ve Iç Içe tür yapıları**

- Genel tür argümanları kopyalanır.

- İç içe tür yapıları shim türleri için kopyalanır.

### <a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a>Dolgu temsilcisi özelliği veya saplama temsilcisi alan adlandırma kuralları
 Boş bir adından başlayarak alan adlandırmayla ilgili **temel kurallar** :

- Yöntem adı eklenir.

- Yöntem adı açık arabirim uygulaması ise noktalar kaldırılır.

- Yöntem geneldir ise, *n* , genel yöntem bağımsız değişkenlerinin sayısıdır `Of`*n* eklenir.

  Özellik alıcısı veya ayarlayıcılar gibi **özel yöntem adları** aşağıdaki tabloda açıklandığı gibi değerlendirilir.

|If yöntemi...|Örnek|Yöntem adı eklenmiş|
|-------------------|-------------|--------------------------|
|Bir **Oluşturucu**|`.ctor`|`Constructor`|
|Statik **Oluşturucu**|`.cctor`|`StaticConstructor`|
|"_" (Özellik alıcıları gibi) ile ayrılmış iki bölümden oluşan Yöntem adına sahip bir **erişimci**|*kind_name* (yaygın durum, ancak ECMA tarafından zorlanmaz)|*NameKind*, her iki parça da büyük harfli ve değiştirilmiş|
||Özellik `Prop` alıcısı|`PropGet`|
||Özellik `Prop` ayarlayıcısı|`PropSet`|
||Olay ekleyici|`Add`|
||Olay kaldırıcısı|`Remove`|
|İki bölümden oluşan bir **operatör**|`op_name`|`NameOp`|
|Örneğin: + işleci|`op_Add`|`AddOp`|
|Bir **dönüştürme işleci**için, dönüş türü eklenir.|`T op_Implicit`|`ImplicitOpT`|

 **Notlar**

- **Dizin oluşturucularının alıcıları ve ayarlayıcıları** özelliğe benzer şekilde işlenir. Bir dizin oluşturucunun varsayılan adı `Item`.

- **Parametre türü** adları dönüştürülür ve bitiştirilir.

- Aşırı yükleme belirsizliğe neden olmadıkça **dönüş türü** yok sayılır. Bu durumda, dönüş türü adın sonuna eklenir

### <a name="BKMK_Parameter_type_naming_conventions"></a>Parametre türü adlandırma kuralları

|Verilen|Eklenen dize...|
|-----------|-------------------------|
|Bir **tür**`T`|T<br /><br /> Ad alanı, iç içe yapı ve genel tikler iptal bırakılır.|
|**Out parametresi**`out T`|`TOut`|
|Bir **ref parametresi** `ref T`|`TRef`|
|Bir **dizi türü**`T[]`|`TArray`|
|**Çok boyutlu dizi** türü `T[ , , ]`|`T3`|
|Bir **işaretçi** türü `T*`|`TPtr`|
|**Genel tür**`T<R1, …>`|`TOfR1`|
|`C<TType>` türünde **genel tür bağımsız değişken**`!i`|`Ti`|
|Metodun **genel metot bağımsız değişkeni**`!!i` `M<MMethod>`|`Mi`|
|**İç içe bir tür**`N.T`|`N` eklendiğinde `T`|

### <a name="BKMK_Recursive_rules"></a>Özyinelemeli kurallar
 Aşağıdaki kurallar özyinelemeli olarak uygulanır şunlardır:

- Fakes kullandığından C# geçersiz oluşturur herhangi bir karakter Fakes derlemeleri oluşturmak için C# belirteci "_" (alt çizgi) kaçış.

- Bildirim türü herhangi bir üyesi ile elde edilen adı çakışıyor, 01 ile başlayan iki basamaklı sayaç ekleyerek bir numaralandırma şeması kullanılır.

## <a name="BKMK_External_resources"></a>Dış kaynaklar

### <a name="BKMK_Guidance"></a>Kılavuzu
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 2: birim testi: Içini test etme](https://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Ayrıca Bkz.
 [Microsoft Fakes ile Test Edilen Kodu Yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
