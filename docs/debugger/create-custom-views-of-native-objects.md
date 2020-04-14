---
title: C++ nesnelerinin özel görünümlerini oluşturma
description: Visual Studio'nun hata ayıklamada yerel türleri görüntüleme şeklini özelleştirmek için Natvis çerçevesini kullanın
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8bdd8d26ba450b1aedd790d644c183607c44af
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224517"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Natvis çerçevesini kullanarak hata ayıklamada C++ nesnelerinin özel görünümlerini oluşturma

Visual Studio *Natvis* çerçevesi, **Yerel Aygıtlar** ve **İzle** pencereleri gibi yerel türlerin hata ayıklama değişken pencerelerinde ve **DataTips'te**görünme biçimini özelleştirir. Natvis görselleştirmeleri hata ayıklama sırasında oluşturduğunuz türleri daha görünür hale getirmeye yardımcı olabilir.

Natvis, Visual Studio'nun önceki sürümlerindeki *autoexp.dat* dosyasını XML sözdizimi, daha iyi tanılama, sürüm leme ve birden çok dosya desteğiyle değiştirir.

> [!NOTE]
> Natvis özelleştirmeler sınıflar ve structs ile çalışır, ancak typedefs değil.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Natvis görselleştirmeleri

Oluşturduğunuz türler için görselleştirme kuralları oluşturmak için Natvis çerçevesini kullanırsınız, böylece geliştiriciler hata ayıklama sırasında bunları daha kolay görebilir.

Örneğin, aşağıdaki resimde windows türünde bir değişken [gösterilmektedir::UI::Xaml::Denetimler::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) hata ayıklayıcı penceresinde herhangi bir özel görselleştirme uygulanmadan.

![TextBox varsayılan görselleştirme](../debugger/media/dbg_natvis_textbox_default.png "TextBox varsayılan görselleştirme")

Vurgulanan satır sınıfın `Text` özelliğini `TextBox` gösterir. Karmaşık sınıf hiyerarşisi bu özelliği bulmayı zorlaştırır. Hata ayıklayıcı özel dize türünü nasıl yorumlanacağı nızı bilmediğinden, metin kutusunun içinde tutulan dizeyi göremezsiniz.

Natvis özel görselleştirici kuralları uygulandığında aynı `TextBox` değişken penceresinde çok daha basit görünüyor. Sınıfın önemli üyeleri birlikte görünür ve hata ayıklama özel dize türünün alttaki dize değerini gösterir.

![Visualizer kullanarak TextBox verileri](../debugger/media/dbg_natvis_textbox_visualizer.png "Visualizer kullanarak TextBox verileri")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>C++ projelerinde .natvis dosyalarını kullanma

Natvis görselleştirme kurallarını belirtmek için *.natvis* dosyalarını kullanır. *.natvis* dosyası *,natvis* uzantılı bir XML dosyasıdır. Natvis şeması *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*olarak tanımlanır.

*.natvis* dosyasının temel yapısı, görselleştirme girişlerini temsil eden bir veya daha fazla `Type` öğedir. Her `Type` öğenin tam nitelikli adı `Name` özniteliği belirtilir.

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

Visual Studio *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* klasöründe bazı *.natvis* dosyaları sağlar. Bu dosyaların birçok yaygın türü için görselleştirme kuralları vardır ve yeni türler için görselleştirme yazmak için örnek teşkil edebilir.

### <a name="add-a-natvis-file-to-a-c-project"></a>C++ projesine .natvis dosyası ekleme

Herhangi bir C++ projesine *.natvis* dosyası ekleyebilirsiniz.

**Yeni bir *.natvis* dosyası eklemek için:**

1. **Çözüm Gezgini'nde**C++ proje düğümünü seçin ve **Project** > **Add new öğeyi**seçin veya projeyi sağ tıklatın ve**Yeni öğe ekle'yi** **Add** > seçin.

1. Yeni **Öğe Ekle** iletişim kutusunda **Visual C++** > **Yardımcı Program** > **Hata Ayıklama görselleştirme dosyası (.natvis)** öğesini seçin.

1. Dosyayı adlandırın ve **Ekle'yi**seçin.

   Yeni dosya Solution **Explorer'a**eklenir ve Visual Studio belge bölmesinde açılır.

Visual Studio hata ayıklama c++ projelerinde *.natvis* dosyaları otomatik olarak yükler ve varsayılan olarak, proje inşa edildiğinde *de .pdb* dosyasında içerir. Yerleşik uygulamayı hata ayıklama ederseniz, hata ayıklama *.pdb* dosyasından *.natvis* dosyasını yükler, proje açık olmasa bile. *.natvis* dosyasının *.pdb'de*bulunmasını istemiyorsanız, yerleşik *.pdb* dosyasından hariç tutabilirsiniz.

***.natvis* dosyasını bir *.pdb'den*çıkarmak için :**

1. **Solution Explorer'da** *.natvis* dosyasını seçin ve **Özellikler** simgesini seçin veya dosyayı sağ tıklatın ve **Özellikler'i**seçin.

1. **Dışlanmış Yapı'nın** yanındaki oku bırakın ve **Evet'i**seçin ve ardından **Tamam'ı**seçin.

>[!NOTE]
>Yürütülebilir projelerin hata ayıklanması için, *.pdb'de*olmayan *.natvis* dosyaları eklemek için çözüm öğelerini kullanın, çünkü C++ projesi yok.

>[!NOTE]
>*.pdb'den* yüklenen Natvis kuralları yalnızca *.pdb'nin* ifade ettiği modüllerde bulunan türler için geçerlidir. Örneğin, *Module1.pdb* adlı `Test`bir tür için bir Natvis girişi varsa, yalnızca `Test` *Module1.dll'deki*sınıf için geçerlidir. Başka bir modül de adlı `Test`bir sınıf tanımlarsa, *Module1.pdb* Natvis giriş için geçerli değildir.

**Bir VSIX paketi üzerinden *bir .natvis* dosyasını yüklemek ve kaydetmek için:**

Bir VSIX paketi *.natvis* dosyalarını yükleyebilir ve kaydedebilir. Nerede yüklenirlerse yüklensinler, tüm kayıtlı *.natvis* dosyaları hata ayıklama sırasında otomatik olarak alınır.

1. *.natvis* dosyasını VSIX paketine ekleyin. Örneğin, aşağıdaki proje dosyası için:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. *.natvis* dosyasını *source.extension.vsixmanifest* dosyasına kaydedin:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>Natvis dosya konumları

Birden çok projeye başvurmalarını istiyorsanız *,natvis* dosyalarını kullanıcı dizininize veya sistem dizininize ekleyebilirsiniz.

*.natvis* dosyaları aşağıdaki sırada değerlendirilir:

1. Yüklenen projede aynı adı taşıyan bir dosya yoksa, *.pdb'ye* katıştırılmış herhangi bir *.natvis* dosyası hata ayıklama yapıyorsunuz.

2. Yüklü bir C++ projesinde veya üst düzey çözümde bulunan *.natvis* dosyaları. Bu grup, sınıf kitaplıkları da dahil olmak üzere tüm yüklü C++ projelerini içerir, ancak diğer dillerdeki projeleri içermez.

3. VSIX paketi ile yüklenen ve kaydedilmiş *.natvis* dosyaları.

::: moniker range="vs-2017"

4. Kullanıcıya özel Natvis dizini (örneğin, *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers).*

::: moniker-end

::: moniker range=">= vs-2019"

4. Kullanıcıya özel Natvis dizini (örneğin, *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers).*

::: moniker-end

5. Sistem genelinde Natvis dizini (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Bu dizin Visual Studio ile yüklü *.natvis* dosyaları vardır. Yönetici izinlerin varsa, bu dizine dosya ekleyebilirsiniz.

## <a name="modify-natvis-files-while-debugging"></a>Hata ayıklama sırasında .natvis dosyalarını değiştirin

Projesini hata ayıklarken IDE'deki *bir .natvis* dosyasını değiştirebilirsiniz. Dosyayı hata ayıkladığınız Visual Studio ile aynı durumda açın, değiştirin ve kaydedin. Dosya kaydedilir kaydedilmez, **Saati ve** **Locals** pencereleri değişikliği yansıtacak şekilde güncellenir.

Ayrıca hata ayıkladığınız bir çözüme *.natvis* dosyalarını ekleyebilir veya silebilirsiniz ve Visual Studio ilgili görselleştirmeleri ekler veya kaldırır.

Hata ayıklama sırasında *.pdb* dosyalarına katıştırılmış *.natvis* dosyalarını güncelleştiremezsiniz.

*.natvis* dosyasını Visual Studio dışında değiştirirseniz, değişiklikler otomatik olarak etkili olmaz. Hata ayıklama pencerelerini güncelleştirmek **için, Immediate** **penceresindeki .natvisreload** komutunu yeniden değerlendirebilirsiniz. Ardından değişiklikler hata ayıklama oturumunu yeniden başlatmadan etkili olur.

Ayrıca *.natvis* dosyasını daha yeni bir sürüme yükseltmek için **.natvisreload** komutunu kullanın. Örneğin, *.natvis* dosyası kaynak denetiminde denetlenebilir ve başka birinin yaptığı son değişiklikleri almak istiyorsunuz.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a>İfadeler ve biçimlendirme
Natvis görselleştirmeleri, görüntülenecek veri öğelerini belirtmek için C++ ifadelerini kullanır. [Bağlam işlecinde (C++)](../debugger/context-operator-cpp.md)açıklanan hata ayıklamadaki C++ ifadelerinin geliştirmelerine ve sınırlamalarına ek olarak aşağıdakilere dikkat edin:

- Natvis ifadeleri, geçerli yığın çerçevesine değil, görselleştirilen nesne bağlamında değerlendirilir. Örneğin, `x` Bir Natvis ifadesinde, görselleştirilen nesnedeki **x** adlı alana başvurur, geçerli işlevdeki **x** adlı yerel bir değişkene değil. Natvis ifadelerinde yerel değişkenlere erişemezsiniz, ancak genel değişkenlere erişebilirsiniz.

- Natvis ifadeleri fonksiyon değerlendirmesine veya yan etkilere izin vermez. İşlev çağrıları ve atama işleçleri yoksayılır. [Hata ayıklama içsel işlevler](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) yan etkisiz olduğundan, diğer işlev çağrılarına izin verilmese bile, herhangi bir Natvis ifadesinden serbestçe çağrılabilirler.

- Bir ifadenin nasıl görüntülenebildiğini denetlemek için, [C++'da Biçim belirteçlerinde](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)açıklanan biçim belirteçlerinden herhangi birini kullanabilirsiniz. Giriş, `Size` [ArrayItems genişletmedeki](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)ifade gibi Natvis tarafından dahili olarak kullanıldığında biçim belirteci yoksayılır.

## <a name="natvis-views"></a>Natvis görünümleri

Türleri farklı şekillerde görüntülemek için farklı Natvis görünümleri tanımlayabilirsiniz. Örneğin, burada basitleştirilmiş bir `std::vector` görünüm adlı `simple`tanımlayan bir görselleştirme. Ve `DisplayString` `ArrayItems` öğeler varsayılan görünümde ve `simple` görünümde gösterirken, `[size]` ve `[capacity]` öğeler `simple` görünümde gösterilmez.

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

**İzleme** penceresinde, alternatif bir görünüm belirtmek için **,görünüm** biçimi belirticisini kullanın. Basit görünüm **vec,view(basit)** olarak görünür:

![Pencereyi basit görünümle izleme](../debugger/media/watch-simpleview.png "Pencereyi basit görünümle izleme")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>Natvis hataları

Hata ayıklama bir görselleştirme girişinde hatalarla karşılaştığında, bunları yok sayar. Türü ham formunda görüntüler veya başka bir uygun görselleştirme seçer. Hata ayıklamanın neden görselleştirme girişini göz ardı edildiğini anlamak ve altta yatan sözdizimi ve ayrıştırma hatalarını görmek için Natvis tanılamasını kullanabilirsiniz.

**Natvis tanısını açmak için:**

- **Tools** > **Options** (veya **Hata** >  **Ayıklama** > **Seçenekleri)** altında >**Hata Ayıklama Çıkış Penceresi,** Hata **,** **Uyarı**veya **Verbose**, **Natvis tanılama iletileri (Yalnızca C++)** ayarlayın ve sonra **Tamam'ı**seçin.

Hatalar **Çıktı** penceresinde görünür.

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a>Natvis sözdizimi başvurusu

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a>OtomatikGörselleştirici öğesi
Öğe `AutoVisualizer` *.natvis* dosyasının kök düğümüdür ve ad alanı `xmlns:` özniteliğini içerir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

Öğe `AutoVisualizer` [Türü,](#BKMK_Type) [HResult,](#BKMK_HResult) [UIVisualizer](#BKMK_UIVisualizer)ve [CustomVisualizer](#BKMK_CustomVisualizer) çocuklar olabilir.

### <a name="type-element"></a><a name="BKMK_Type"></a>Tür öğesi

Temel `Type` bir örnek şu örneğe benzer:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Öğe `Type` belirtir:

1. Görselleştirme nin hangi tür için `Name` kullanılması gerektiği (öznitelik).

2. Bu tür bir nesnenin değeri `DisplayString` (öğe) gibi görünmelidir.

3. Kullanıcı değişken penceresinde `Expand` (düğüm) türü genişletirken türün üyeleri nasıl görünmelidir.

#### <a name="templated-classes"></a>Şablonlanmış sınıflar
Öğenin `Name` `Type` özniteliği, şablonlu sınıf `*` adları için kullanılabilecek bir joker karakter olarak yıldız işaretini kabul eder.

Aşağıdaki örnekte, nesne bir veya bir `CAtlArray<int>` `CAtlArray<float>`. Bir için belirli bir görselleştirme `CAtlArray<float>`girişi varsa, o zaman genel bir öncelik alır.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

$T1, $T2 vb. makroları kullanarak görselleştirme girişinde şablon parametrelerine başvuru yapabilirsiniz. Bu makrolardan örnekler bulmak için Visual Studio ile gönderilen *.natvis* dosyalarına bakın.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a>Visualizer türü eşleştirme
Bir görselleştirme girişi doğrulamıyorsa, bir sonraki kullanılabilir görselleştirme kullanılır.

#### <a name="inheritable-attribute"></a>Devredilebilir öznitelik
İsteğe `Inheritable` bağlı öznitelik, görselleştirmenin yalnızca bir temel türe mi yoksa bir taban türüne ve türetilen tüm türlere mi uygulandığını belirtir. Varsayılan `Inheritable` değeri. `true`

Aşağıdaki örnekte, görselleştirme yalnızca `BaseClass` tür için geçerlidir:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Öncelik özniteliği

İsteğe `Priority` bağlı öznitelik, bir tanım ayrışdırmazsa, alternatif tanımların kullanılacağı sırayı belirtir. Olası değerler `Priority` `Low`şunlardır: `MediumLow``Medium`, `MediumHigh`, `High`, , ve . Varsayılan değer: `Medium`. Öznitelik yalnızca `Priority` aynı *.natvis* dosyasındaki öncelikler arasında ayrım eder.

Aşağıdaki örnek, ilk olarak 2015 STL ile eşleşen girişi ayrışdırır. Bu ayrıştırmak için başarısız olursa, STL 2013 sürümü için alternatif giriş kullanır:

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
Herhangi bir `Optional` düğüme bir öznitelik koyabilirsiniz. İsteğe bağlı bir düğüm içindeki bir alt ifade ayrıştırmazsa, hata ayıklayan bu düğümü `Type` yoksa, ancak kuralların geri kalanını uygular. Aşağıdaki türde, `[State]` isteğe bağlı `[Exception]` değildir, ancak isteğe bağlıdır.  _ `MyNamespace::MyClass` `M_exceptionHolder`adlı bir alanı varsa, hem `[State]` `[Exception]` düğüm hem de düğüm görünür, `_M_exceptionHolder` ancak alan `[State]` yoksa yalnızca düğüm görüntülenir.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a>Koşul özniteliği

İsteğe `Condition` bağlı öznitelik birçok görselleştirme öğesi için kullanılabilir ve bir görselleştirme kuralı kullanmak için ne zaman belirtir. Koşul özniteliği içindeki ifade giderirse, `false`görselleştirme kuralı uygulanmaz. 'yi `true`değerlendirirse veya öznitelik yoksa, `Condition` görselleştirme geçerlidir. Bu özniteliği görselleştirme girişlerinde if-else mantığı için kullanabilirsiniz.

Örneğin, aşağıdaki görselleştirme akıllı `DisplayString` işaretçi türü için iki öğe vardır. `_Myptr` Üye boşaldığında, ilk `DisplayString` öğenin durumu , `true`böylece form görüntüler giderir. `_Myptr` Üye boş olmadığında, koşul 'u `false`değerlendirir ve `DisplayString` ikinci öğe görüntülenir.

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

Ve `IncludeView` `ExcludeView` öznitelikleri belirli görünümlerde görüntülemek veya görüntülemek için öğeleri belirtir. Örneğin, aşağıdaki `std::vector`Natvis belirtiminde, `simple` görünüm `[size]` ve `[capacity]` öğeleri görüntülemez.

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

Türleri `IncludeView` ve tek `ExcludeView` tek üyeleri üzerinde ve öznitelikleri kullanabilirsiniz.

### <a name="version-element"></a><a name="BKMK_Versioning"></a>Sürüm öğesi
Öğe, `Version` belirli bir modüle ve sürüme görselleştirme girişini scopes. Öğe `Version` ad çakışmalarını önlemeye yardımcı olur, yanlışlıkla eşleşmeleri azaltır ve farklı tür sürümleri için farklı görselleştirmeler sağlar.

Farklı modüller tarafından kullanılan ortak bir üstbilgi dosyası bir tür tanımlıyorsa, sürümlü görselleştirme yalnızca tür belirtilen modül sürümünde olduğunda görüntülenir.

Aşağıdaki örnekte, görselleştirme yalnızca sürüm `DirectUI::Border` `Windows.UI.Xaml.dll` 1.0'dan 1.5'e kadar bulunan tür için geçerlidir.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

İkisine de `Min` ihtiyacın `Max`yok ve. Bunlar isteğe bağlı özniteliklerdir. Joker karakter desteklenmez.

Öznitelik `Name` biçimi *filename.ext*, *hello.exe* veya *some.dll*gibi . Yol adlarının izin verilmesine izin verilmez.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>DisplayString öğesi
Öğe, `DisplayString` bir değişkenin değeri olarak göstermek için bir dize belirtir. İfadelerle karışık rasgele dizeleri kabul eder. Kıvırcık parantez içindeki her şey bir ifade olarak yorumlanır. Örneğin, aşağıdaki `DisplayString` giriş:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Bu resimde olduğu `CPoint` gibi tür degisitlerinin görüntülenmesi anlamına gelir:

 ![DisplayString öğesi kullanma](../debugger/media/dbg_natvis_cpoint_displaystring.png "DisplayString öğesi kullanma")

İfadede, `DisplayString` `x` ve `y`, üyeleri `CPoint`olan , kıvırcık parantez içinde, bu yüzden değerleri değerlendirilir. Örnek ayrıca çift kıvırcık ayraç (veya) `{{` `}}` kullanarak kıvırcık bir ayraç nasıl kaçabilirsiniz gösterir.

> [!NOTE]
> Öğe, `DisplayString` rasgele dizeleri ve kıvırcık ayraç sözdizimini kabul eden tek öğedir. Diğer tüm görselleştirme öğeleri yalnızca hata ayıklamanın değerlendirebileceği ifadeleri kabul eder.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>StringView öğesi

Öğe, `StringView` hata ayıklayanın yerleşik metin görselleştiricisine gönderebileceği bir değer tanımlar. Örneğin, `ATL::CStringT` türü için aşağıdaki görselleştirme verilmiştir:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Nesne `CStringT` bu örnek gibi değişken bir pencerede görüntüler:

![CStringT DisplayString elemanı](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT DisplayString elemanı")

Öğe `StringView` ekleme, hata ayıklamanın değeri metin görselleştirmesi olarak görüntülenebebileceğini söyler.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Hata ayıklama sırasında, değişkenin yanındaki büyüteç simgesini seçebilir ve **ardından m_pszData** işaret eden dizeyi görüntülemek için **Metin Görselleştiricisini** seçebilirsiniz.

 ![StringView görselleştiricisi ile CStringT verileri](../debugger/media/dbg_natvis_stringview_cstringt.png "StringView görselleştiricisi ile CStringT verileri")

İfade, `{m_pszData,su}` değeri Unicode dizesi olarak görüntülemek için C++ biçimi belirtici **su**içerir. Daha fazla bilgi için [C++ format ında belirteçler](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a>Öğeyi genişlet

İsteğe `Expand` bağlı düğüm, değişken bir penceredeki türü genişletdiğinizde görselleştirilmiş bir türün çocuklarını özelleştirir. Düğüm, `Expand` alt öğeleri tanımlayan alt düğümlerin listesini kabul eder.

- Bir `Expand` düğüm görselleştirme girişinde belirtilmemişse, çocuklar varsayılan genişletme kurallarını kullanır.

- Altında `Expand` alt düğüm olmayan bir düğüm belirtilirse, hata ayıklama pencerelerinde tür genişletilemez.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a>Öğe genişletme

 Öğe, `Item` bir `Expand` düğümdeki en temel ve ortak öğedir. `Item`tek bir alt öğe tanımlar. Örneğin, alanları `CRect` `top`olan bir `left` `right`sınıf `bottom` , , , ve aşağıdaki görselleştirme girişi vardır:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Hata ayıklama penceresinde, `CRect` tür aşağıdaki örneğe benzer:

![Madde öğesi genişletme ile CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "Madde öğesi genişletme ile CRect")

Hata ayıklama, öğe `Width` ve `Height` öğelerde belirtilen ifadeleri değerlendirir ve değişken penceresinin **Değer** sütunundaki değerleri gösterir.

Hata ayıklama otomatik olarak her özel genişletme için **[Raw View]** düğüm oluşturur. Önceki ekran görüntüsü, nesnenin varsayılan ham görünümünün Natvis görselleştirmesinden nasıl farklı olduğunu göstermek için **[Ham Görünüm]** düğümünü genişletilmiş olarak görüntüler. Varsayılan genişletme, taban sınıf için bir alt ağaç oluşturur ve taban sınıfın tüm veri üyelerini alt sınıf olarak listeler.

> [!NOTE]
> Öğe öğesinin ifadesi karmaşık bir türü işaret ederse, **Öğe** düğümünün kendisi genişletilebilir.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a>ArrayItems genişletme
Visual `ArrayItems` Studio hata ayıklayıcısının türü bir dizi olarak yorumlamasını ve tek tek öğelerini görüntülemesini sağlamak için düğümü kullanın. Için görselleştirme `std::vector` iyi bir örnektir:

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

A, `std::vector` değişken penceresinde genişletildiğinde tek tek öğelerini gösterir:

![std::vector ArrayItems genişletme kullanarak](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector ArrayItems genişletme kullanarak")

Düğüm `ArrayItems` olmalıdır:

- Hata `Size` ayıklayanın dizinin uzunluğunu anlaması için bir ifade (tamsayıya değerlendirilmesi gereken) .
- İlk `ValuePointer` öğeyi işaret eden bir ifade (olmayan `void*`bir öğe türünün işaretçisi olmalıdır).

Dizinin varsayılan değeri alt sınır 0'dır. Değeri geçersiz kılmak için `LowerBound` bir öğe kullanın. Visual Studio ile gönderilen *.natvis* dosyaları örnekleri var.

>[!NOTE]
>İşleç'i, `[]` `vector[i]`örneğin, tür kendisi (örneğin) `ArrayItems` `CATLArray`bu işleç izin vermese bile, kullanan herhangi bir tek boyutlu dizi görselleştirmesi ile kullanabilirsiniz.

Çok boyutlu diziler de belirtebilirsiniz. Bu durumda, hata ayıklamanın alt öğeleri düzgün bir şekilde görüntülemek için biraz daha fazla bilgiye ihtiyacı vardır:

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

- `Direction`dizinin satır-büyük veya sütun-büyük sırada olup olmadığını belirtir.
- `Rank`dizinin sıralamasını belirtir.
- Öğe, `Size` bu boyuttaki dizinin uzunluğunu bulmak için boyut indeksi ile değiştirildiği örtük `$i` parametreyi kabul eder. Önceki örnekte, ifade `_M_extent.M_base[0]` 0. `_M_extent._M_base[1]`

İki boyutlu `Concurrency::array` bir nesne hata ayıklama penceresinde şu şekilde görünür:

![ArrayItems genişletme ile iki boyutlu dizi](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "ArrayItems genişletme ile iki boyutlu dizi")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a>IndexListItems genişletme

Genişletmeyi `ArrayItems` yalnızca dizi öğeleri bellekte bitişik olarak düzenlenirse kullanabilirsiniz. Hata ayıklama, işaretçisini yalnızca artımlayarak bir sonraki öğeye geçer. Dizin değeri düğümüne işlemek gerekiyorsa, düğümleri `IndexListItems` kullanın. Burada düğümlü bir `IndexListItems` görselleştirme:

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

Arasındaki `ArrayItems` `IndexListItems` tek `ValueNode`fark, örtük `$i` parametre ile i<sup>th</sup> öğesine tam ifade yi bekleyen dir.

>[!NOTE]
>İşleç'i, `[]` `vector[i]`örneğin, tür kendisi (örneğin) `IndexListItems` `CATLArray`bu işleç izin vermese bile, kullanan herhangi bir tek boyutlu dizi görselleştirmesi ile kullanabilirsiniz.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a>LinkedListItems genişletme

Görselleştirilmiş tür bağlantılı bir listeyi temsil ediyorsa, hata `LinkedListItems` ayıklama bir düğüm kullanarak çocuklarını görüntüleyebilir. `CAtlList` Türü için aşağıdaki görselleştirme `LinkedListItems`kullanır:

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

Öğe, `Size` listenin uzunluğunu ifade eder. `HeadPointer`ilk öğeye işaret `NextPointer` eder, bir sonraki `ValueNode` öğeyi ifade eder ve maddenin değerini ifade eder.

Hata ayıklama, üst `NextPointer` `ValueNode` liste türünde değil, `LinkedListItems` düğüm öğesi bağlamında ifadeleri değerlendirir. Önceki örnekte, `CAtlList` bağlı `CNode` listenin düğümü `atlcoll.h`olan bir sınıf (bulunan) vardır. `m_pNext`ve `m_element` bu `CNode` sınıfın alanlarıdır, `CAtlList` sınıfın değil.

`ValueNode`boş bırakılabilir veya `this` düğümün `LinkedListItems` kendisine başvurmak için kullanılabilir.

#### <a name="customlistitems-expansion"></a>CustomListItems genişletme

Genişletme, `CustomListItems` karma tablo gibi bir veri yapısında geçiş yapmak için özel mantık yazmanıza olanak tanır. Değerlendirmeniz gereken her şey için C++ ifadelerini kullanabilen, ancak kalıp için tam `ArrayItems` `IndexListItems`olarak uymayan veri yapılarını görselleştirmek için `LinkedListItems`kullanın. `CustomListItems`

Genişletmede `Exec` tanımlanan değişkenleri ve `CustomListItems` nesneleri kullanarak, genişletme içinde kodu yürütmek için kullanabilirsiniz. Mantıksal işleçler, aritmetik işleçler `Exec`ve atama işleçleri kullanabilirsiniz. C++ ifade `Exec` değerlendiricisi tarafından desteklenen [hata ayıklayıcı içsel işlevler](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) dışında işlevleri değerlendirmek için kullanamazsınız.

Aşağıdaki görselleştirici için `CAtlMap` uygun olduğu `CustomListItems` mükemmel bir örnektir.

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

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a>TreeItems genişletme
 Görselleştirilmiş tür bir ağacı temsil ediyorsa, hata ayıklama ağacı yürüyebilir ve bir `TreeItems` düğüm kullanarak çocuklarını görüntüleyebilir. Düğüm kullanarak `std::map` türü için görselleştirme `TreeItems` aşağıda veda edin:

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

Sözdizimi `LinkedListItems` düğüme benzer. `LeftPointer`, `RightPointer`ve `ValueNode` ağaç düğümü sınıfı bağlamında değerlendirilir. `ValueNode`boş bırakılabilir veya `this` düğümün `TreeItems` kendisine başvurmak için kullanılabilir.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a>Genişletilmiş Öğe genişletme
 Öğe, `ExpandedItem` temel sınıfların veya veri üyelerinin özelliklerini görselleştirilmiş türdeki çocuklar gibi göstererek toplu bir alt görünüm oluşturur. Hata ayıklama, belirtilen ifadeyi değerlendirir ve sonucun alt düğümlerini görselleştirilmiş türün alt listesine ekler.

Örneğin, akıllı işaretçi `auto_ptr<vector<int>>` türü genellikle aşağıdaki gibi görüntüler:

 ![otomatik&#95;ptr&#60;vektör&#60;int&#62;&#62; varsayılan genişleme](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Varsayılan genişletme")

 Vektörün değerlerini görmek için, üyenin içinden geçerek değişken penceresindeiki `_Myptr` seviyeyi delmeniz gerekir. Bir `ExpandedItem` öğe ekleyerek, değişkeni `_Myptr` hiyerarşiden ortadan kaldırabilir ve vektör öğelerini doğrudan görüntüleyebilirsiniz:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![oto&#95;ptr&#60;vektör&#60;int&#62;&#62; ExpandedItem genişletme](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Genişletilmiş Öğe genişletme")

Aşağıdaki örnek, türemiş bir sınıfta taban sınıftan özelliklerin nasıl toplanmış olduğunu gösterir. `CPanel` `CFrameworkElement`Sınıfın. Düğüm görselleştirme, taban `CFrameworkElement` sınıftan gelen özellikleri yinelemek yerine, bu özellikleri `CPanel` sınıfın alt listesine ekler. `ExpandedItem`

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Türemiş sınıf için görselleştirme eşleştirmesini kapatan **nd** biçimi belirtimi burada gereklidir. Aksi takdirde, `*(CFrameworkElement*)this` varsayılan `CPanel` görselleştirme türü eşleştirme kuralları en uygun olanı düşünün, çünkü ifade, görselleştirme yeniden uygulanmasına neden olur. Hata ayıklayıcıya temel sınıf görselleştirmesini kullanmasını veya taban sınıfın görselleştirmesi yoksa varsayılan genişletmeyi kullanmak için **nd** biçimini belirticisini kullanın.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a>Sentetik madde genişletme
 `ExpandedItem` Öğe hiyerarşileri ortadan kaldırarak verilerin daha düz `Synthetic` bir görünüm sağlarken, düğüm tam tersini yapar. Bir ifadenin sonucu olmayan yapay bir alt öğe oluşturmanıza olanak tanır. Yapay elementin kendi alt öğeleri olabilir. Aşağıdaki örnekte, `Concurrency::array` tür için görselleştirme `Synthetic` kullanıcıya bir tanılama iletisi göstermek için bir düğüm kullanır:

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

 ![Eşzamanlılık::Sentetik eleman genişletme li dizi](../debugger/media/dbg_natvis_expand_synthetic.png "Eşzamanlılık::Sentetik eleman genişletme li dizi")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>HResult öğesi
 Öğe, `HResult` hata ayıklama pencerelerinde Bir **HRESULT** için gösterilen bilgileri özelleştirmenize olanak tanır. Öğe, `HRValue` özelleştirilecek **Olan HRESULT'in** 32 bitlik değerini içermelidir. Öğe `HRDescription` hata ayıklama penceresinde gösterin bilgileri içerir.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>UIVisualizer öğesi
Bir `UIVisualizer` öğe hata ayıklayıcı ile bir grafik görselleştirici eklentisi kaydeder. Grafik görselleştirici, bir değişkeni veya nesneyi veri türüyle tutarlı bir şekilde gösteren bir iletişim kutusu veya başka bir arabirim oluşturur. Görselleştirici eklentisi [VSPackage](../extensibility/internals/vspackages.md)olarak yazılmalıdır ve hata ayıklayanın tüketebileceği bir hizmeti ortaya çıkarmalıdır. *.natvis* dosyası, eklentinin adı, açığa çıkarılan hizmetin GUID'i ve görselleştirebileceği türler gibi kayıt bilgilerini içerir.

Burada bir UIVisualizer öğesi nin bir örneği verilmiştir:

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

- `ServiceId`  -  `Id` Öznitelik çifti bir `UIVisualizer`. Görselleştirici `ServiceId` paketin açığa çıkardığı hizmetin GUID'idir. `Id`bir hizmet birden fazla hizmet sağlıyorsa, görüntüleyicileri farklılaştıran benzersiz bir tanımlayıcıdır. Önceki örnekte, aynı görselleştirici hizmeti iki görselleştirici sağlar.

- Öznitelik, `MenuName` hata ayıklamadaki büyüteç simgesinin yanındaki açılır da görüntülenecek bir görselleştirici adı tanımlar. Örneğin:

  ![UIVisualizer menü kısayol menüsü](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer menü kısayol menüsü")

*.natvis* dosyasında tanımlanan her tür, görüntülenebilen tüm UI görselleştiricilerini açıkça listelemelidir. Hata ayıklayıcı, tür girişlerinde bulunan görselleştirici başvurularını kayıtlı görselleştiricilerle eşleşir. Örneğin, önceki `std::vector` `UIVisualizer` örnekte başvurular için aşağıdaki tür girişi.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Bellekteki bit eşlemlerini görüntülemek için kullanılan Görüntü `UIVisualizer` [İzleme](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) uzantısında bir örnek görebilirsiniz.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>CustomVisualizer öğesi
 `CustomVisualizer`Visual Studio kodundaki görselleştirmeleri denetlemek için yazdığınız vsix uzantısını belirten bir genişletilebilirlik noktasıdır. VSIX uzantıları yazma hakkında daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.

Bir XML Natvis tanımı daha özel bir görselleştirici yazmak için çok daha fazla iş, ama Natvis ne yapar ya da desteklemez hakkında kısıtlamalar ücretsiz. Özel görselleştiriciler, hata ayıklama işlemini sorgulayabilen ve değiştirebilen veya Visual Studio'nun diğer bölümleriyle iletişim kurabilen tam hata ayıklayıcı genişletilebilirlik API'lerine erişebilir.

 Öğeler `Condition`üzerinde `IncludeView` `CustomVisualizer` , , `ExcludeView` ve öznitelikleri kullanabilirsiniz.

 ## <a name="limitations"></a>Sınırlamalar

Natvis özelleştirmeler sınıflar ve structs ile çalışır, ancak typedefs değil.

Natvis ilkel türleri (örneğin, `int`, ) `bool`veya ilkel türleri işaretçiler için görüntüleyicileri desteklemez. Bu senaryoda, bir seçenek kullanım örneği için uygun [biçim belirtici](../debugger/format-specifiers-in-cpp.md) kullanmaktır. Örneğin, kodunuzda `double* mydoublearray` kullanıyorsanız, hata ayıklayıcının **İzleme** penceresinde ilk 100 öğeyi gösteren ifade `mydoublearray, [100]`gibi bir dizi biçimi belirtimi kullanabilirsiniz.
