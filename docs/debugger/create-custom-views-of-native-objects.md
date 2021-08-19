---
title: C++ nesnelerinin özel görünümlerini oluşturma
description: Visual Studio hata ayıklayıcıda yerel türleri görüntüleme biçimini özelleştirmek için Natvis çerçevesini kullanın
ms.date: 03/02/2020
ms.topic: how-to
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 484d29f0c1976181007afee4d3da2f2e2e659d23
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121792"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Natvis çerçevesini kullanarak hata ayıklayıcıda C++ nesnelerinin özel görünümlerini oluşturma

Visual Studio *Natvis* çerçevesi, yerel türlerin hata ayıklayıcı değişken pencerelerinde görünme şeklini özelleştirir, örneğin **yereller** ve **izle** pencereleri ve **veri ipuçları**. Natvis görselleştirmeleri, oluşturduğunuz türlerin hata ayıklama sırasında daha görünür olmasına yardımcı olabilir.

Natvis, XML sözdizimi, daha iyi tanılama, sürüm oluşturma ve birden çok dosya desteğiyle daha önceki Visual Studio sürümlerindeki *oto exp. dat* dosyasını değiştirir.

> [!NOTE]
> Natvis özelleştirmeleri sınıflar ve yapılar ile çalışır, ancak Typedefs 'lar değildir.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Natvis görselleştirmeleri

Geliştiricilerin hata ayıklama sırasında daha kolay görebilmesi için, oluşturduğunuz türler için görselleştirme kuralları oluşturmak üzere Natvis çerçevesini kullanın.

örneğin, aşağıdaki çizimde özel görselleştirmeler uygulanmamış bir hata ayıklayıcı penceresinde [Windows:: uı:: Xaml:: Controls:: TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) türünde bir değişken gösterilmektedir.

![TextBox varsayılan görselleştirmesi](../debugger/media/dbg_natvis_textbox_default.png "TextBox varsayılan görselleştirmesi")

Vurgulanan satır `Text` sınıfının özelliğini gösterir `TextBox` . Karmaşık sınıf hiyerarşisi bu özelliği bulmayı zorlaştırır. Hata ayıklayıcı özel dize türünü nasıl yorumlayacağını bilmez, bu nedenle TextBox içinde tutulan dizeyi göremezsiniz.

`TextBox`Natvis özel görselleştiricisi kuralları uygulandığında değişken penceresinde aynı daha basit bir şekilde görünür. Sınıfının önemli üyeleri birlikte görünür ve hata ayıklayıcı özel dize türünün temel alınan dize değerini gösterir.

![Görselleştirici kullanarak metin kutusu verileri](../debugger/media/dbg_natvis_textbox_visualizer.png "Görselleştirici kullanarak TextBox verileri")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>C++ projelerinde. Natvis dosyalarını kullanma

Natvis, görselleştirme kurallarını belirtmek için *. natvis* dosyalarını kullanır. *. Natvis* dosyası. *NATVIS* uzantılı bir XML dosyasıdır. Natvis şeması, *%VSInstallDir%\Xml\Schemas\natvis. xsd*' de tanımlanmıştır.

Bir *. natvis* dosyasının temel yapısı, `Type` görselleştirme girdilerini temsil eden bir veya daha fazla öğe. Her öğenin tam adı `Type` `Name` özniteliğinde belirtilir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio, *%vsınstalldir%\common7\packages\debugger\visualıcılar* klasöründe bazı *. natvis* dosyaları sağlar. Bu dosyalar birçok ortak tür için görselleştirme kurallarına sahiptir ve yeni türler için görselleştirmeler yazmak üzere örnek olarak işlev görebilir.

### <a name="add-a-natvis-file-to-a-c-project"></a>C++ projesine bir. natvis dosyası ekleme

Herhangi bir C++ projesine bir *. natvis* dosyası ekleyebilirsiniz.

**Yeni bir *. natvis* dosyası eklemek için:**

1. **Çözüm Gezgini**' de C++ proje düğümünü seçin ve **Project**  >  **yeni öğe ekle**' yi seçin veya projeye sağ tıklayıp   >  **yeni öğe** ekle ' yi seçin.

1. **Yeni öğe Ekle** iletişim kutusunda **Visual C++**  >  **yardımcı program**  >  **ayıklayıcısı görselleştirme dosyası (. natvis)** öğesini seçin.

1. Dosyayı adlandırın ve **Ekle**' yi seçin.

   yeni dosya **Çözüm Gezgini** eklenir ve Visual Studio belge bölmesinde açılır.

Visual Studio hata ayıklayıcı, C++ projelerindeki *. natvis* dosyalarını otomatik olarak yükler ve varsayılan olarak, proje oluştururken *. pdb* dosyasında da içerir. Oluşturulan uygulamada hata ayıklaması yaparsanız, proje açık olmasa bile, hata ayıklayıcı. *pdb* dosyasından *. natvis* dosyasını yükler. .,. *Natvis* dosyasını *. pdb* dosyasına dahil etmek istemiyorsanız, bunu yerleşik *. pdb* dosyasından hariç bırakabilirsiniz.

**. *Natvis* dosyasını bir *. pdb* dosyasından dışlamak için:**

1. **Çözüm Gezgini** *. natvis* dosyasını seçin ve **Özellikler** simgesini seçin ya da dosyaya sağ tıklayıp **Özellikler**' i seçin.

1. **Derlemeden çıkarılan** ' ın yanındaki oku ve **Evet**' i seçin ve ardından **Tamam**' ı seçin.

>[!NOTE]
>Yürütülebilir projelerde hata ayıklama için, kullanılabilir bir C++ projesi bulunmadığından, *. pdb* içinde olmayan *. natvis* dosyalarını eklemek için çözüm öğelerini kullanın.

>[!NOTE]
>Bir *. pdb* 'den yüklenen Natvis kuralları yalnızca *. pdb* 'nin başvurduğu modüllerde bulunan türlere uygulanır. Örneğin, *Module1. pdb* adlı bir tür için Natvis girişi varsa `Test` , bu yalnızca `Test` *Module1.dll* sınıfı için geçerlidir. Başka bir modül adlı bir sınıfı da tanımlıyorsa `Test` , *Module1. pdb* Natvis girdisi buna uygulanmaz.

**Bir *. natvis* dosyasını bir VSIX paketi aracılığıyla yüklemek ve kaydetmek için:**

Bir VSıX paketi, *. natvis* dosyalarını yükleyebilir ve kaydedebilir. Nerede yüklendiğine bakılmaksızın, tüm kayıtlı *. natvis* dosyaları hata ayıklama sırasında otomatik olarak alınır.

1. *. Natvis* dosyasını VSIX paketine dahil edin. Örneğin, aşağıdaki proje dosyası için:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. *. Natvis* dosyasını *Source. Extension. valtmanifest* dosyasına kaydedin:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a> Natvis dosya konumları

Birden çok projeye uygulanmasını istiyorsanız, *. natvis* dosyalarını Kullanıcı dizininize veya bir sistem dizinine ekleyebilirsiniz.

*. Natvis* dosyaları aşağıdaki sırayla değerlendirilir:

1. Yüklü projede aynı ada sahip bir dosya mevcut değilse, bir *. pdb* dosyasına gömülü tüm *. natvis* dosyaları hata ayıklaması yapılır.

2. Yüklü bir C++ projesinde veya en üst düzey çözümde bulunan *. natvis* dosyaları. Bu grup, sınıf kitaplıkları da dahil olmak üzere tüm yüklenen C++ projelerini içerir, ancak diğer dillerdeki projeler değildir.

3. Herhangi bir *. natvis* dosyası, bir VSIX paketi aracılığıyla yüklenir ve kaydedilir.

::: moniker range="vs-2017"

4. kullanıcıya özgü Natvis dizini (örneğin, *%userprofile%\documents\ Visual Studio 2017 \ görselleştiriciler*).

::: moniker-end

::: moniker range=">= vs-2019"

4. kullanıcıya özgü Natvis dizini (örneğin, *%userprofile%\documents\ Visual Studio 2019 \ görselleştiriciler*).

::: moniker-end

5. Sistem genelindeki Natvis dizini (*%VSInstallDir%\common7\packages\debugger\görselleştiriciler*). Bu dizin, Visual Studio yüklü *. natvis* dosyalarına sahiptir. Yönetici izinleriniz varsa, bu dizine dosyalar ekleyebilirsiniz.

## <a name="modify-natvis-files-while-debugging"></a>Hata ayıklarken. Natvis dosyalarını değiştirme

Projesinde hata ayıklarken IDE 'deki bir *. natvis* dosyasını değiştirebilirsiniz. dosyayı hata ayıkladığınızı Visual Studio aynı örneğinde açın, değiştirin ve kaydedin. Dosya kaydedildiği anda, değişikliği yansıtmak için **Watch** ve **Locals** Windows Update.

ayrıca, hata ayıklaması yaptığınız bir çözüme *. natvis* dosyaları ekleyebilir veya silebilirsiniz ve Visual Studio ilgili görselleştirmeleri ekler veya kaldırır.

Hata ayıklarken *. pdb* dosyalarına katıştırılmış *. natvis* dosyalarını güncelleştiremezsiniz.

*. natvis* dosyasını Visual Studio dışında değiştirirseniz değişiklikler otomatik olarak geçerli olmaz. Hata ayıklayıcı pencerelerini güncelleştirmek için, **hemen** penceresinde **. natvisreload komutunu yeniden** değerlendirmeye alabilirsiniz. Ardından, değişiklikler hata ayıklama oturumunu yeniden başlatmadan geçerli olur.

. *Natvis* dosyasını daha yeni bir sürüme yükseltmek için **. natvisreload** komutunu da kullanabilirsiniz. Örneğin, *. natvis* dosyası kaynak denetimine iade edilebilir ve başka birisinin yaptığı son değişiklikleri almak istiyorsunuz.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> İfadeler ve biçimlendirme
Natvis görselleştirmeleri, görüntülenecek veri öğelerini belirtmek için C++ ifadeleri kullanır. [Bağlam operatörü (C++)](../debugger/context-operator-cpp.md)içinde açıklanan hata ayıklayıcıdaki C++ ifadelerinin geliştirmelere ve kısıtlamalarına ek olarak, aşağıdakilerin farkında olun:

- Natvis ifadeleri, geçerli yığın çerçevesini değil görselleştirilen nesne bağlamında değerlendirilir. Örneğin, `x` Natvis ifadesinde, geçerli işlevde **x** adlı yerel bir değişkene değil, görselleştirilen nesnede **x** adlı alana başvurur. Küresel değişkenlere erişebilseniz de, Natvis ifadelerinde yerel değişkenlere erişemezsiniz.

- Natvis ifadeleri işlev değerlendirmesi veya yan etkilere izin vermez. İşlev çağrıları ve atama işleçleri yok sayılır. [Hata ayıklayıcı iç işlevleri](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) yan etkilerden farklı olduğundan, diğer işlev çağrılarına izin verilmese de, her bir natvis ifadesinden serbestçe çağrılabilir.

- Bir ifadenin nasıl görüntüleneceğini denetlemek için [C++ ' da biçim tanımlayıcıda](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)açıklanan biçim belirticilerini kullanabilirsiniz. Girdi, `Size` [ArrayItems genişletmesinin](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)ifadesi gibi Natvis tarafından dahili olarak kullanıldığında biçim belirticileri yoksayılır.

>[!NOTE]
> Natvis belgesi XML olduğundan deyimleriniz, ampersan, büyüktür, küçüktür veya SHIFT işleçlerini doğrudan kullanamaz. Bu karakterleri hem öğe gövdesinde hem de koşul deyimlerinde atlamanız gerekir. Örnek:<br>
> \<Item Name="HiByte"\>bayt (_flags \& gt; \& > 24), x\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) == 0"\>Seçim\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) != 0"\>Bölümünü\</Item\>

## <a name="natvis-views"></a>Natvis görünümleri

Farklı yollarla türleri göstermek için farklı Natvis görünümleri tanımlayabilirsiniz. Örneğin, aşağıda `std::vector` adlı Basitleştirilmiş görünümü tanımlayan bir görselleştirme verilmiştir `simple` . , Ve `DisplayString` `ArrayItems` `simple` `[size]` `[capacity]` öğeleri görünümde gösterilmezseniz, ve öğeleri varsayılan görünümde ve görünümünde gösterilir `simple` .

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

**İzleme** penceresinde, alternatif bir görünüm belirtmek için **, görünüm** biçim belirticisini kullanın. Basit görünüm VEC olarak görünür **, görünüm (basit)**:

![Basit görünümle izleme penceresi](../debugger/media/watch-simpleview.png "izleme penceresi görünümüyle görüntüleme")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis hataları

Hata ayıklayıcı bir görselleştirme girişinde hatalarla karşılaştığında onları yoksayar. Bu, türü ham biçiminde görüntüler ya da uygun bir görselleştirme seçer. Hata ayıklayıcının bir görselleştirme girişini neden yoksaydığını anlamak ve temeldeki sözdizimi ve ayrıştırma hatalarını görmek için Natvis tanılamayı kullanabilirsiniz.

**Natvis tanılamayı açmak için:**

- Araçlar **Seçenekleri**(veya Hata Ayıklama Seçenekleri) altında > Ayıklama Çıkış Penceresi, Natvis tanılama iletilerini  >     >     >   **(yalnızca C++) Hata** , Uyarı veya   Ayrıntılı olarak ayarlayın ve tamam'ı **seçin.**

Hatalar Çıkış **penceresinde** görüntülenir.

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Natvis söz dizimi başvurusu

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> AutoVisualizer öğesi
öğesi `AutoVisualizer`  , *.natvis* dosyasının kök düğümü ve ad alanı özniteliğini `xmlns:` içerir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

öğesi `AutoVisualizer` Type, [](#BKMK_Type) [HResult,](#BKMK_HResult) [UIVisualizer](#BKMK_UIVisualizer)ve [CustomVisualizer öğelerine](#BKMK_CustomVisualizer) sahip olabilir.

### <a name="type-element"></a><a name="BKMK_Type"></a> Type öğesi

Temel bir `Type` örnek şu şekildedir:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 `Type`öğesi şunları belirtir:

1. Görselleştirmenin hangi tür için (özniteliği) `Name` kullanılmalıdır?

2. Bu türdeki bir nesnenin değeri nasıl görünür `DisplayString` (öğesi).

3. Kullanıcı türü bir değişken penceresinde (düğüm) genişleten tür üyelerinin nasıl olması `Expand` gerekir?

#### <a name="templated-classes"></a>Şablon sınıfları
öğesinin özniteliği, şablonlu sınıf adları için kullanılan joker karakter olarak `Name` bir yıldız işareti kabul `Type` `*` eder.

Aşağıdaki örnekte, nesnenin veya olmasıyla aynı görselleştirme `CAtlArray<int>` `CAtlArray<float>` kullanılır. için belirli bir görselleştirme girişi `CAtlArray<float>` varsa, genel görselleştirmeye göre önceliklidir.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

$T 1, $T 2 vb. makroları kullanarak görselleştirme girdisinde şablon parametrelerine başvurabilirsiniz. Bu makroların örneklerini bulmak için, bu makrolarla birlikte gönderilen *.natvis* dosyalarına Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Görselleştirici türü eşleştirme
Bir görselleştirme girişi doğrulanamıyorsa, bir sonraki kullanılabilir görselleştirme kullanılır.

#### <a name="inheritable-attribute"></a>Devralınabilir öznitelik
İsteğe `Inheritable` bağlı öznitelik, görselleştirmenin yalnızca bir temel türe mi yoksa bir temel türe ve tüm türetilmiş türlere uygulanıp uygulana olmadığını belirtir. varsayılan `Inheritable` `true` değeridir.

Aşağıdaki örnekte görselleştirme yalnızca türü için `BaseClass` geçerlidir:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priority özniteliği

İsteğe `Priority` bağlı özniteliği, bir tanımın ayrıştırılamama durumunda alternatif tanımların hangi sırayla kullanılamayacaklarını belirtir. olası `Priority` değerleri: `Low` , `MediumLow` , , ve `Medium` `MediumHigh` `High` . `Medium` varsayılan değerdir. özniteliği `Priority` yalnızca aynı *.natvis* dosyasındaki öncelikleri birbirinden ayırt ediyor.

Aşağıdaki örnek ilk olarak 2015 STL ile eşleşen girdiyi ayrıştırıyor. Ayrıştıramazsa, STL'nin 2013 sürümü için alternatif girişi kullanır:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>İsteğe bağlı öznitelik
Herhangi bir `Optional` düğüme öznitelik koyarak. İsteğe bağlı bir düğümün içindeki bir alt ifade ayrıştıramazsa, hata ayıklayıcı bu düğümü yoksayır, ancak kuralların geri kalanını `Type` uygular. Aşağıdaki tür isteğe `[State]` bağlı değildir, ancak `[Exception]` isteğe bağlıdır.  _ adlı bir alanı varsa hem düğüm hem de düğüm görünür, ancak alan `MyNamespace::MyClass` `M_exceptionHolder` yoksa yalnızca düğüm `[State]` `[Exception]` `_M_exceptionHolder` `[State]` görünür.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Koşul özniteliği

İsteğe `Condition` bağlı özniteliği birçok görselleştirme öğe için kullanılabilir ve bir görselleştirme kuralının ne zaman kullanıcazı belirtir. Koşul özniteliğinin içindeki ifade olarak `false` çözümleyicisi olursa görselleştirme kuralı geçerli olmaz. değerlendirmesi olarak değerlendirilirse `true` veya özniteliği yoksa görselleştirme `Condition` uygulanır. Görselleştirme girişlerinde if-else mantığı için bu özniteliği kullanabilirsiniz.

Örneğin, aşağıdaki görselleştirmede akıllı `DisplayString` işaretçi türü için iki öğe vardır. Üye `_Myptr` boş olduğunda, ilk öğenin koşulu `DisplayString` olarak çözümleyicisi `true` olur, böylece form görüntülenir. Üye `_Myptr` boş değilken koşul olarak değerlendirilir ve `false` ikinci `DisplayString` öğe görüntülenir.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>IncludeView ve ExcludeView öznitelikleri

ve `IncludeView` `ExcludeView` öznitelikleri, belirli görünümlerde görüntülenmek veya görüntülenmek için öğeleri belirtir. Örneğin, aşağıdaki Natvis belirtimsinde, `std::vector` görünüm ve öğelerini `simple` `[size]` `[capacity]` görüntülemez.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

ve özniteliklerini `IncludeView` `ExcludeView` türlerde ve tek tek üyeler üzerinde kullanabilirsiniz.

### <a name="version-element"></a><a name="BKMK_Versioning"></a> Sürüm öğesi
öğesi, `Version` belirli bir modül ve sürüm için görselleştirme girişinin kapsamını gösterir. öğesi ad çakışmalarını önlemeye yardımcı olur, yanlışlıkla yapılan yanlışlıkları azaltır ve farklı tür sürümleri için `Version` farklı görselleştirmelere izin verir.

Farklı modüller tarafından kullanılan ortak bir üst bilgi dosyası bir tür tanımlarsa, sürümü belirtilmiş görselleştirme yalnızca tür belirtilen modül sürümünde olduğunda görünür.

Aşağıdaki örnekte görselleştirme yalnızca sürüm `DirectUI::Border` `Windows.UI.Xaml.dll` 1.0 ile 1.5 arasında bulunan tür için geçerlidir.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

hem hem de 'ye ihtiyacınız `Min` `Max` yok. Bunlar isteğe bağlı özniteliklerdir. Joker karakter desteği yoktur.

özniteliği `Name` *filename.ext biçimindedir;* örneğin, *hello.exe* veya *some.dll.* Yol adlarına izin verilmez.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a> DisplayString öğesi
`DisplayString`öğesi, bir değişkenin değeri olarak göstermek için bir dize belirtir. İfadelerle karışık rastgele dizeleri kabul eder. Küme ayraçları içindeki her şey bir ifade olarak yorumlanır. Örneğin, aşağıdaki `DisplayString` girdi:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Türüne sahip değişkenlerin `CPoint` bu çizimde gösterildiği gibi olduğu anlamına gelir:

 ![DisplayString öğesi kullanma](../debugger/media/dbg_natvis_cpoint_displaystring.png "DisplayString öğesi kullanma")

İfadede ve üyesi olan , küme ayraçlarının `DisplayString` `x` `y` `CPoint` içindedir, dolayısıyla değerleri değerlendirilir. Örnekte ayrıca çift küme ayraçları ( veya ) kullanarak küme ayracından nasıl kaçarak kaçış çıkarıcaz? `{{` `}}`

> [!NOTE]
> öğesi, `DisplayString` rastgele dizeleri ve küme ayracı söz dizimi kabul eden tek öğedir. Diğer tüm görselleştirme öğeleri yalnızca hata ayıklayıcı tarafından değerlendirilen ifadeleri kabul eder.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a> StringView öğesi

`StringView`öğesi, hata ayıklayıcının yerleşik metin görselleştiriciye göndere bir değer tanımlar. Örneğin, türü için aşağıdaki görselleştirmeyi `ATL::CStringT` kullanarak:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

nesnesi, `CStringT` aşağıdaki örnekte olduğu gibi bir değişken penceresinde görüntülenir:

![CStringT DisplayString öğesi](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT DisplayString öğesi")

Öğe `StringView` ekleniyor, hata ayıklayıcıya değeri metin görselleştirmesi olarak görüntüley olduğunu söyler.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Hata ayıklama sırasında değişkenin yanındaki büyüteç simgesini ve ardından **Metin** Görselleştirici'yi seçerek, m_pszData **görüntüebilirsiniz.**

 ![StringView görselleştiricisi ile CStringT verileri](../debugger/media/dbg_natvis_stringview_cstringt.png "StringView görselleştiricisi ile CStringT verileri")

İfade, `{m_pszData,su}` değeri Unicode dizesi olarak görüntülemek için bir C++ biçim belirtici **su** içerir. Daha fazla bilgi için [bkz. C++ içinde biçim belirleyicileri.](../debugger/format-specifiers-in-cpp.md)

### <a name="expand-element"></a><a name="BKMK_Expand"></a> Expand öğesi

İsteğe `Expand` bağlı düğüm, türü bir değişken penceresinde genişleten görselleştirilmiş bir türün alt ayarlarını özeller. Düğüm, `Expand` alt öğeleri tanımlayan alt düğümlerin listesini kabul eder.

- Bir görselleştirme `Expand` girdisinde düğüm belirtilmemişse alt öğeler varsayılan genişletme kurallarını kullanır.

- Altında `Expand` alt düğüm olmayan bir düğüm belirtilirse, tür hata ayıklayıcı pencerelerde genişletilemez.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Öğe genişletme

 öğesi, `Item` bir düğümdeki en temel ve en yaygın `Expand` öğedir. `Item` tek bir alt öğe tanımlar. Örneğin, , `CRect` , ve alanlarına sahip bir `top` sınıf aşağıdaki görselleştirme `left` `right` `bottom` girişe sahiptir:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Hata ayıklayıcısı penceresinde tür `CRect` şu örnekteki gibi görünür:

![Öğe öğesi genişletmesi ile CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "Öğe öğesi genişlemesiyle CRect")

Hata ayıklayıcısı, ve öğelerinde belirtilen ifadeleri değerlendirir ve değerleri `Width` `Height` değişken penceresinin **Değer** sütununda gösterir.

Hata ayıklayıcısı her özel genişletme **için [Ham Görünüm]** düğümünü otomatik olarak oluşturur. Önceki ekran görüntüsünde, nesnenin varsayılan ham görünümünün Natvis görselleştirmelerinden nasıl farklı olduğunu göstermek için **genişletilmiş [Ham Görünüm]** düğümü görüntülenir. Varsayılan genişletme, temel sınıf için bir alt ağaç oluşturur ve temel sınıfın tüm veri üyelerini alt sınıf olarak listeler.

> [!NOTE]
> Öğe öğesinin ifadesi karmaşık bir türü gösteriyorsa Öğe **düğümünün** kendisi genişletilebilir.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> ArrayItems genişletmesi
Hata ayıklayıcısının türü Visual Studio yorumlaması ve tek tek öğelerini görüntülemesi için `ArrayItems` düğümünü kullanın. için görselleştirme `std::vector` iyi bir örnektir:

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

, `std::vector` değişken penceresinde genişletilen öğelerini tek tek gösterir:

![ArrayItems genişletmesi kullanan std::vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std:: ArrayItems genişletmesi kullanan vektör")

Düğümde `ArrayItems` şunların olması gerekir:

- Hata ayıklayıcının dizinin uzunluğunu anlarken bir ifade `Size` (tamsayı olarak değerlendirilmesi gerekir).
- İlk `ValuePointer` öğeye işaret eden bir ifade (bu, değil bir öğe türünün işaretçisi olması `void*` gerekir).

Alt sınır dizisinin varsayılan değeri 0'dır. Değeri geçersiz kılmak için bir öğesi `LowerBound` kullanın. Bu dosyalarla birlikte gönderilen *.natvis* Visual Studio örnekler içerir.

>[!NOTE]
>Türün kendisi (örneğin) bu işleçe izin vermese bile, işleci, kullanan tek boyutlu dizi görselleştirmeleriyle birlikte `[]` `vector[i]` `ArrayItems` `CATLArray` kullanabilirsiniz.

Çok boyutlu diziler de belirtsiniz. Bu durumda, hata ayıklayıcı alt öğeleri düzgün şekilde görüntülemek için biraz daha fazla bilgi gerektirir:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction` dizinin satır-ana mı yoksa sütun-ana mı olduğunu belirtir.
- `Rank` dizinin derecesini belirtir.
- öğesi, bu boyuttaki dizinin uzunluğunu bulmak için boyut diziniyle `Size` `$i` değiştiren örtülü parametreyi kabul eder. Önceki örnekte ifade, `_M_extent.M_base[0]` 0. boyut, `_M_extent._M_base[1]` 1. boyut gibi uzunlukları ver ver önceki örnekte olmalıdır.

hata ayıklayıcısı penceresinde iki boyutlu `Concurrency::array` bir nesnenin nasıl göründüğünü görebilirsiniz:

![ArrayItems genişletmesi ile iki boyutlu dizi](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "ArrayItems genişletmesi olan iki boyutlu dizi")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> IndexListItems genişletmesi

Genişletmeyi `ArrayItems` yalnızca dizi öğelerinin belleğe bitişik olarak sıra olması gerekir. Hata ayıklayıcısı yalnızca işaretçisini artırarak bir sonraki öğeye gider. Dizini değer düğümüne göre işlemeniz gerekirse düğümleri `IndexListItems` kullanın. Bir düğüme sahip görselleştirme şu `IndexListItems` şekildedir:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

ve arasındaki tek `ArrayItems` `IndexListItems` fark, tam ifadeyi örtülü `ValueNode` parametresiyle i<sup>th öğesine</sup> bekler. `$i`

>[!NOTE]
>Türün kendisi (örneğin) bu işleçe izin vermese bile, işleci, kullanan tek boyutlu dizi görselleştirmeleriyle birlikte `[]` `vector[i]` `IndexListItems` `CATLArray` kullanabilirsiniz.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems genişletmesi

Görselleştirilmiş tür bağlantılı bir listeyi temsil ediyorsa, hata ayıklayıcı bir düğüm kullanarak altlarını `LinkedListItems` ekleyebilirsiniz. türü için aşağıdaki görselleştirme `CAtlList` şunları `LinkedListItems` kullanır:

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

`Size`öğesi listenin uzunluğuna başvurur. `HeadPointer` ilk öğeye, `NextPointer` sonraki öğeye ve `ValueNode` öğenin değerine başvurur.

Hata ayıklayıcısı, `NextPointer` ve `ValueNode` ifadelerini üst liste türü değil `LinkedListItems` düğüm öğesi bağlamında değerlendirir. Yukarıdaki örnekte, bağlı listenin bir düğümü olan bir `CAtlList` `CNode` sınıfı `atlcoll.h` (içinde bulunur) vardır. `m_pNext` ve `m_element` , sınıfının `CNode` değil, o sınıfın `CAtlList` alanlarıdır.

`ValueNode` boş bırakılanın veya `this` düğümün kendisine başvurmak `LinkedListItems` için kullanın.

#### <a name="customlistitems-expansion"></a>CustomListItems genişletmesi

Genişletme, `CustomListItems` karma tablosu gibi bir veri yapısında geçiş yapmak için özel mantık yazmanızı sağlar. Değerlendirmeniz gereken her şey için C++ ifadelerini kullana ama , veya kalıplarını tam olarak sığdırmayan veri `CustomListItems` yapılarını `ArrayItems` `IndexListItems` görselleştirmek için `LinkedListItems` kullanın.

Genişletmede `Exec` tanımlanan değişkenleri ve nesneleri kullanarak `CustomListItems` bir genişletmenin içindeki kodu yürütmek için kullanabilirsiniz. mantıksal işleçleri, aritmetik işleçleri ve atama işleçlerini ile `Exec` kullanabilirsiniz. C++ ifade değerlendiricisi tarafından desteklenen hata ayıklayıcı iç işlevleri dışında işlevleri değerlendirmek `Exec` için'yi [](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) kullanabilirsiniz.

için aşağıdaki `CAtlMap` görselleştirici, uygun olduğu mükemmel bir `CustomListItems` örnektir.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> TreeItems genişletmesi
 Görselleştirilmiş tür bir ağacı temsil ediyorsa, hata ayıklayıcı ağacı adım adım göstererek bir düğüm kullanarak altlarını `TreeItems` gösterir. Düğüm kullanan türün `std::map` görselleştirmesi şu `TreeItems` şekildedir:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

Söz dizimi düğüme `LinkedListItems` benzer. `LeftPointer`, `RightPointer` ve , ağaç düğümü sınıfının bağlamı altında `ValueNode` değerlendirilir. `ValueNode` boş bırakılanın veya `this` düğümün kendisine başvurmak `TreeItems` için kullanın.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem genişletmesi
 öğesi, temel sınıfların veya veri üyelerinin özelliklerini görselleştirilmiş türün alt öğesi gibi görüntüleyerek toplu `ExpandedItem` bir alt görünüm üretir. Hata ayıklayıcısı belirtilen ifadeyi değerlendirir ve sonucun alt düğümlerini görselleştirilmiş türün alt listesine ekler.

Örneğin, akıllı işaretçi türü genellikle `auto_ptr<vector<int>>` şu şekilde görüntülenir:

 ![otomatik&#95;ptr&#60;vektörü&#60;int&#62;&#62; genişletme](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Varsayılan genişletme")

 Vektör değerlerini görmek için, değişken penceresinde üyeyi geçerek iki düzey detaya `_Myptr` gitmelisiniz. Bir öğe `ExpandedItem` ekleyerek, hiyerarşideki değişkeni `_Myptr` ortadan kaldırabilirsiniz ve vektör öğelerini doğrudan görüntüebilirsiniz:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![int&#95;ExpandedItem&#60;otomatik&#60;ptr&#62;&#62; vektörü](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem genişletmesi")

Aşağıdaki örnek, türetilmiş bir sınıftaki temel sınıftan özellikleri toplamayı gösterir. sınıfının `CPanel` sınıfından türet olduğunu `CFrameworkElement` varsayalım. Temel sınıftan gelen özellikleri yinelemek yerine, düğüm görselleştirmesi bu özellikleri sınıfın `CFrameworkElement` `ExpandedItem` alt listesine `CPanel` ekler.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Türetilmiş sınıf için görselleştirme eşleştirmeyi kapatan **nd** biçim belirleyicisi burada gereklidir. Aksi takdirde, varsayılan görselleştirme türü eşleştirme kuralları bunu en uygun olan olarak kabul ettikçe ifade `*(CFrameworkElement*)this` `CPanel` görselleştirmenin yeniden uygulanmasına neden olur. Hata **ayıklayıcıya** temel sınıf görselleştirmesini kullanma talimatı veya temel sınıfın görselleştirmesi yoksa varsayılan genişletmeyi yapmak için nd biçim belirleyicisini kullanın.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Yapay öğe genişletme
 öğesi `ExpandedItem` hiyerarşileri ortadan kaldırarak verilerin düz bir görünümünü sağlarken, `Synthetic` düğüm tam tersini yapar. bir ifadenin sonucu olmayan yapay bir alt öğe oluşturmanıza olanak sağlar. Yapay öğenin kendi alt öğeleri olabilir. Aşağıdaki örnekte, türüne göre `Concurrency::array` görselleştirme, `Synthetic` kullanıcıya bir tanılama iletisi göstermek için bir düğüm kullanır:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![Concurrency::Array ve Yapay öğe genişletmesi](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency:: yapay öğe genişletmesi olan dizi")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a> HResult öğesi
 öğesi, `HResult` hata ayıklayıcı pencerelerde **HRESULT için gösterilen** bilgileri özelleştirmenize olanak sağlar. `HRValue`öğesi, özelleştirecek **HRESULT'un** 32 bit değerini içermesi gerekir. öğesi, `HRDescription` hata ayıklayıcısı penceresinde gösterilen bilgileri içerir.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a> UIVisualizer öğesi
Bir `UIVisualizer` öğe, bir grafik görselleştirici eklentiyi hata ayıklayıcıya kaydettirmektedir. Grafik görselleştirici, bir değişkeni veya nesneyi veri türüyle tutarlı bir şekilde gösteren bir iletişim kutusu veya başka bir arabirim oluşturur. Görselleştirici eklentisi [VSPackage](../extensibility/internals/vspackages.md)olarak yazmalı ve hata ayıklayıcının tükettiği bir hizmeti açığa çıkarmalı. *.natvis* dosyası eklentinin adı, açığa çıkarna hizmetin GUID'si ve görselleştirileyesi türleri gibi kayıt bilgilerini içerir.

UiVisualizer öğesinin bir örneği aşağıdaki gibidir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- Öznitelik `ServiceId`  -  `Id` çifti bir `UIVisualizer` tanımlar. `ServiceId`, görselleştirici paketinin ortaya çıkar olduğu hizmetin GUID'idir. `Id` , bir hizmet birden fazla hizmet sağlarsa görselleştiricileri ayırt etmek için benzersiz bir tanımlayıcıdır. Önceki örnekte, aynı görselleştirici hizmeti iki görselleştirici sağlar.

- özniteliği, hata ayıklayıcıda büyüteç simgesinin yanındaki açılan ekranda `MenuName` görüntülemek için bir görselleştirici adı tanımlar. Örnek:

  ![UIVisualizer menü kısayol menüsü](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer menü kısayol menüsü")

*.natvis* dosyasında tanımlanan her tür, onu görüntüleyiştiren kullanıcı arabirimi görselleştiricilerini açıkça listelelanmalıdır. Hata ayıklayıcısı, tür girişlerinde görselleştirici başvurularını kayıtlı görselleştiricilerle eşler. Örneğin, önceki örnekteki başvurusu `std::vector` için `UIVisualizer` aşağıdaki tür girdisi.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Bellek içinde bit eşlemleri `UIVisualizer` görüntülemek için kullanılan [Görüntü](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) İzleme uzantısında bir örneği yer almaktadır.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>CustomVisualizer öğesi
 `CustomVisualizer`, kodda görselleştirmeleri denetlemeye yazmak için yazacak bir VSIX uzantısını belirten bir Visual Studio noktasıdır. VSIX uzantıları yazma hakkında daha fazla bilgi için bkz. [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

Özel görselleştirici yazmak XML Natvis tanımından çok daha fazla iştir, ancak Natvis'in ne yaptığı veya desteklemesi konusunda kısıtlamalara sahip değilsiniz. Özel görselleştiriciler, hata ayıklama işlemini sorgulandırarak değiştirebilir veya hata ayıklayıcının diğer bölümleriyle iletişim kurarak hata ayıklayıcı genişletilebilirlik API'lerinin Visual Studio.

 Öğelerde `Condition` , `IncludeView` ve `ExcludeView` özniteliklerini `CustomVisualizer` kullanabilirsiniz.

## <a name="limitations"></a>Sınırlamalar

Natvis özelleştirmeleri sınıflarla ve yapılarla çalışır, ancak typedef'lerle çalışmaz.

Natvis, ilkel türler (örneğin, `int` , ) veya ilkel `bool` türlerin işaretçileri için görselleştiricileri desteklemez. Bu senaryoda bir seçenek, kullanım durumuna [uygun biçim belirleyiciyi](../debugger/format-specifiers-in-cpp.md) kullanmaktır. Örneğin, kodunda kullanıyorsanız, hata ayıklayıcının İzleme penceresinde ilk 100 öğeyi gösteren ifadesi gibi bir dizi biçimi belirleyicisi `double* mydoublearray`  `mydoublearray, [100]` kullanabilirsiniz.
