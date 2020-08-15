---
title: C++ nesnelerinin özel görünümlerini oluşturma
description: Visual Studio 'Nun hata ayıklayıcıda yerel türleri görüntüleme biçimini özelleştirmek için Natvis çerçevesini kullanın
ms.date: 03/02/2020
ms.topic: how-to
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
ms.openlocfilehash: 37bfd1ab57fd0e37f32a55d5bfc3787cb0c0cbd2
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248052"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Natvis çerçevesini kullanarak hata ayıklayıcıda C++ nesnelerinin özel görünümlerini oluşturma

Visual Studio *Natvis* çerçevesi yerel türlerin hata ayıklayıcı değişken pencerelerinde görünme şeklini özelleştirir, örneğin **Yereller** ve **İzle** pencereleri ve **veri ipuçları**. Natvis görselleştirmeleri, oluşturduğunuz türlerin hata ayıklama sırasında daha görünür olmasına yardımcı olabilir.

Natvis, Visual Studio 'nun önceki sürümlerinde bulunan, XML sözdizimi, daha iyi tanılama, sürüm oluşturma ve birden çok dosya desteğiyle birlikte bulunan *oto. dat* dosyasını değiştirir.

> [!NOTE]
> Natvis özelleştirmeleri sınıflar ve yapılar ile çalışır, ancak Typedefs 'lar değildir.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Natvis görselleştirmeleri

Geliştiricilerin hata ayıklama sırasında daha kolay görebilmesi için, oluşturduğunuz türler için görselleştirme kuralları oluşturmak üzere Natvis çerçevesini kullanın.

Örneğin, aşağıdaki çizimde özel görselleştirmeler uygulanmamış bir hata ayıklayıcı penceresinde [Windows:: UI:: XAML:: Controls:: TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) türünde bir değişken gösterilmektedir.

![TextBox varsayılan görselleştirmesi](../debugger/media/dbg_natvis_textbox_default.png "TextBox varsayılan görselleştirmesi")

Vurgulanan satır `Text` sınıfının özelliğini gösterir `TextBox` . Karmaşık sınıf hiyerarşisi bu özelliği bulmayı zorlaştırır. Hata ayıklayıcı özel dize türünü nasıl yorumlayacağını bilmez, bu nedenle TextBox içinde tutulan dizeyi göremezsiniz.

`TextBox`Natvis özel görselleştiricisi kuralları uygulandığında değişken penceresinde aynı daha basit bir şekilde görünür. Sınıfının önemli üyeleri birlikte görünür ve hata ayıklayıcı özel dize türünün temel alınan dize değerini gösterir.

![Görselleştirici kullanarak metin kutusu verileri](../debugger/media/dbg_natvis_textbox_visualizer.png "Görselleştirici kullanarak metin kutusu verileri")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>C++ projelerinde. Natvis dosyalarını kullanma

Natvis, görselleştirme kurallarını belirtmek için *. natvis* dosyalarını kullanır. *. Natvis* dosyası. *NATVIS* uzantılı bir XML dosyasıdır. Natvis şeması *%VSInstallDir%\Xml\Schemas\natvis.exe*içinde tanımlanmıştır.

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

Visual Studio, *%VSInstallDir%\common7\packages\debugger\visualıcılar* klasöründe bazı *. natvis* dosyaları sağlar. Bu dosyalar birçok ortak tür için görselleştirme kurallarına sahiptir ve yeni türler için görselleştirmeler yazmak üzere örnek olarak işlev görebilir.

### <a name="add-a-natvis-file-to-a-c-project"></a>C++ projesine bir. natvis dosyası ekleme

Herhangi bir C++ projesine bir *. natvis* dosyası ekleyebilirsiniz.

**Yeni bir *. natvis* dosyası eklemek için:**

1. **Çözüm Gezgini**' de C++ proje düğümünü seçin ve **Proje**  >  **Yeni öğe Ekle**' yi seçin veya projeye sağ tıklayıp **Add**  >  **Yeni öğe**Ekle ' yi seçin.

1. **Yeni öğe Ekle** iletişim kutusunda **Visual C++**  >  **yardımcı program**  >  **ayıklayıcısı görselleştirme dosyası (. natvis)** öğesini seçin.

1. Dosyayı adlandırın ve **Ekle**' yi seçin.

   Yeni dosya **Çözüm Gezgini**eklenir ve Visual Studio belge bölmesinde açılır.

Visual Studio hata ayıklayıcı, *. natvis* dosyalarını C++ projelerinde otomatik olarak yükler ve varsayılan olarak, proje oluştururken *. pdb* dosyasında da içerir. Oluşturulan uygulamada hata ayıklaması yaparsanız, proje açık olmasa bile, hata ayıklayıcı. *pdb* dosyasından *. natvis* dosyasını yükler. .,. *Natvis* dosyasını *. pdb*dosyasına dahil etmek istemiyorsanız, bunu yerleşik *. pdb* dosyasından hariç bırakabilirsiniz.

**. *Natvis* dosyasını bir *. pdb*dosyasından dışlamak için:**

1. **Çözüm Gezgini** *. natvis* dosyasını seçin ve **Özellikler** simgesini seçin ya da dosyaya sağ tıklayıp **Özellikler**' i seçin.

1. **Derlemeden çıkarılan** ' ın yanındaki oku ve **Evet**' i seçin ve ardından **Tamam**' ı seçin.

>[!NOTE]
>Yürütülebilir projelerde hata ayıklama için, kullanılabilir bir C++ projesi bulunmadığından, *. pdb*içinde olmayan *. natvis* dosyalarını eklemek için çözüm öğelerini kullanın.

>[!NOTE]
>Bir *. pdb* 'den yüklenen Natvis kuralları yalnızca *. pdb* 'nin başvurduğu modüllerde bulunan türlere uygulanır. Örneğin, *Module1. pdb* adlı bir tür için Natvis girişi varsa `Test` , bu yalnızca `Test` *Module1.dll*sınıfı için geçerlidir. Başka bir modül adlı bir sınıfı da tanımlıyorsa `Test` , *Module1. pdb* Natvis girdisi buna uygulanmaz.

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

4. Kullanıcıya özgü Natvis dizini (örneğin, *%userprofile%\, Visual Studio 2017 \ Görselleştiriciler*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Kullanıcıya özgü Natvis dizini (örneğin, *%userprofile%\, Studio 2019 \ Görselleştiriciler*).

::: moniker-end

5. Sistem genelindeki Natvis dizini (*%VSInstallDir%\common7\packages\debugger\görselleştiriciler*). Bu dizin, Visual Studio ile yüklenen *. natvis* dosyalarını içerir. Yönetici izinleriniz varsa, bu dizine dosyalar ekleyebilirsiniz.

## <a name="modify-natvis-files-while-debugging"></a>Hata ayıklarken. Natvis dosyalarını değiştirme

Projesinde hata ayıklarken IDE 'deki bir *. natvis* dosyasını değiştirebilirsiniz. Dosyayı hata ayıklaması yaptığınız aynı Visual Studio örneğinde açın, değiştirin ve kaydedin. Dosya kaydedildiği anda, değişikliği yansıtmak için **Watch** ve **Locals** Windows Update.

Ayrıca, hata ayıklaması yaptığınız bir çözüme *. natvis* dosyaları ekleyebilir veya silebilirsiniz ve Visual Studio ilgili görselleştirmeleri ekler veya kaldırır.

Hata ayıklarken *. pdb* dosyalarına katıştırılmış *. natvis* dosyalarını güncelleştiremezsiniz.

*. Natvis* dosyasını Visual Studio dışında değiştirirseniz, değişiklikler otomatik olarak geçerli olmaz. Hata ayıklayıcı pencerelerini güncelleştirmek için, **hemen** penceresinde **. natvisreload komutunu yeniden** değerlendirmeye alabilirsiniz. Ardından, değişiklikler hata ayıklama oturumunu yeniden başlatmadan geçerli olur.

. *Natvis* dosyasını daha yeni bir sürüme yükseltmek için **. natvisreload** komutunu da kullanabilirsiniz. Örneğin, *. natvis* dosyası kaynak denetimine iade edilebilir ve başka birisinin yaptığı son değişiklikleri almak istiyorsunuz.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> İfadeler ve biçimlendirme
Natvis görselleştirmeleri, görüntülenecek veri öğelerini belirtmek için C++ ifadeleri kullanır. [Bağlam operatörü (C++)](../debugger/context-operator-cpp.md)içinde açıklanan hata ayıklayıcıdaki C++ ifadelerinin geliştirmelere ve kısıtlamalarına ek olarak, aşağıdakilerin farkında olun:

- Natvis ifadeleri, geçerli yığın çerçevesini değil görselleştirilen nesne bağlamında değerlendirilir. Örneğin, `x` Natvis ifadesinde, geçerli işlevde **x** adlı yerel bir değişkene değil, görselleştirilen nesnede **x** adlı alana başvurur. Küresel değişkenlere erişebilseniz de, Natvis ifadelerinde yerel değişkenlere erişemezsiniz.

- Natvis ifadeleri işlev değerlendirmesi veya yan etkilere izin vermez. İşlev çağrıları ve atama işleçleri yok sayılır. [Hata ayıklayıcı iç işlevleri](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) yan etkilerden farklı olduğundan, diğer işlev çağrılarına izin verilmese de, her bir natvis ifadesinden serbestçe çağrılabilir.

- Bir ifadenin nasıl görüntüleneceğini denetlemek için [C++ ' da biçim tanımlayıcıda](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)açıklanan biçim belirticilerini kullanabilirsiniz. Girdi, `Size` [ArrayItems genişletmesinin](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)ifadesi gibi Natvis tarafından dahili olarak kullanıldığında biçim belirticileri yoksayılır.

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

![Basit görünümle izleme penceresi](../debugger/media/watch-simpleview.png "Basit görünümle izleme penceresi")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis hataları

Hata ayıklayıcı bir görselleştirme girişinde hatalarla karşılaştığında onları yoksayar. Bu, türü ham biçiminde görüntüler ya da uygun bir görselleştirme seçer. Hata ayıklayıcının bir görselleştirme girişini neden yoksaydığını anlamak ve temeldeki sözdizimi ve ayrıştırma hatalarını görmek için Natvis tanılamayı kullanabilirsiniz.

**Natvis tanılamayı açmak için:**

- **Araç**  >  **seçenekleri** (veya **hata ayıklama**  >  **seçenekleri**) altında > hata **ayıklama**  >  **Çıkış penceresi**, **Natvis tanılama iletileri (yalnızca C++)** **hata**, **Uyarı**veya **ayrıntılı**olarak ayarlayın ve ardından **Tamam**' ı seçin.

Hatalar **Çıkış** penceresinde görüntülenir.

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Natvis sözdizimi başvurusu

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> Oto görselleştiricisi öğesi
`AutoVisualizer`Öğesi, *. natvis* dosyasının kök düğümüdür ve ad alanı `xmlns:` özniteliğini içerir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

`AutoVisualizer`Öğesi [Type](#BKMK_Type), [HRESULT](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)ve [CustomVisualizer](#BKMK_CustomVisualizer) alt öğelerine sahip olabilir.

### <a name="type-element"></a><a name="BKMK_Type"></a> Type öğesi

Temel bir `Type` örnek şöyle görünür:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 `Type`Öğesi şunları belirtir:

1. Görselleştirmenin kullanılması gereken tür ( `Name` öznitelik).

2. Bu türdeki bir nesnenin değeri şöyle görünmelidir ( `DisplayString` öğe).

3. Kullanıcı türü bir değişken penceresinde (düğüm) genişlediğinde türün üyeleri şöyle görünmelidir `Expand` .

#### <a name="templated-classes"></a>Şablonlu sınıflar
`Name`Öğesinin özniteliği, `Type` `*` şablonlu sınıf adları için kullanılabilecek bir joker karakter olarak bir yıldız işareti kabul eder.

Aşağıdaki örnekte, nesnenin bir veya olarak olup olmadığı aynı görselleştirme kullanılır `CAtlArray<int>` `CAtlArray<float>` . Bir için belirli bir görselleştirme girişi varsa `CAtlArray<float>` , genel bir üzerinden önceliklidir.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

$T 1, $T 2 vb. makroları kullanarak görselleştirme girişinde şablon parametrelerine başvurabilirsiniz. Bu makroların örneklerini bulmak için bkz. Visual Studio ile birlikte gelen *. natvis* dosyaları.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Görselleştiricisi türü eşleşiyor
Bir görselleştirme girişi doğrulanamazsa, bir sonraki kullanılabilir görselleştirme kullanılır.

#### <a name="inheritable-attribute"></a>Inheritable özniteliği
İsteğe bağlı `Inheritable` öznitelik, bir görselleştirmenin yalnızca bir temel türe mi yoksa bir temel türe ve tüm türetilmiş türlere mi uygulanacağını belirtir. Varsayılan değeri `Inheritable` `true` .

Aşağıdaki örnekte, görselleştirme yalnızca tür için geçerlidir `BaseClass` :

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priority özniteliği

İsteğe bağlı `Priority` öznitelik, bir tanım ayrıştıramazsa alternatif tanımlarının kullanılacağı sırayı belirtir. Olası değerleri `Priority` şunlardır: `Low` ,,, `MediumLow` `Medium` `MediumHigh` ve `High` . Varsayılan değer: `Medium`. `Priority`Öznitelik yalnızca aynı *. natvis* dosyasındaki öncelikler arasında ayrım yapar.

Aşağıdaki örnek öncelikle 2015 STL ile eşleşen girişi ayrıştırır. Bu, ayrıştıramazsa, STL 'nin 2013 sürümü için alternatif girişi kullanır:

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
Herhangi bir düğüme bir `Optional` öznitelik yerleştirebilirsiniz. İsteğe bağlı bir düğümün içindeki bir alt ifade ayrıştıramazsa, hata ayıklayıcı bu düğümü yoksayar, ancak kuralların geri kalanını uygular `Type` . Aşağıdaki türde, `[State]` isteğe bağlı değildir, ancak `[Exception]` isteğe bağlıdır.  `MyNamespace::MyClass`_ Adlı bir alana sahipse, `M_exceptionHolder` hem `[State]` düğüm hem de `[Exception]` düğüm görünür, ancak `_M_exceptionHolder` alan yoksa yalnızca `[State]` düğüm görünür.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Condition özniteliği

İsteğe bağlı `Condition` öznitelik birçok görselleştirme öğesi için kullanılabilir ve bir görselleştirme kuralının ne zaman kullanılacağını belirtir. Koşul özniteliği içindeki ifade olarak çözümlenirse `false` görselleştirme kuralı uygulanmaz. Olarak değerlendirilirse veya bir `true` `Condition` öznitelik yoksa görselleştirme uygulanır. Görselleştirme girişlerinde If-Else mantığı için bu özniteliği kullanabilirsiniz.

Örneğin, aşağıdaki görselleştirmede `DisplayString` akıllı işaretçi türü için iki öğe vardır. `_Myptr`Üye boş olduğunda, ilk `DisplayString` öğenin koşulu olarak çözümlenir `true` , böylece form görüntülenir. `_Myptr`Üye boş olmadığında, koşul olarak değerlendirilir `false` ve ikinci `DisplayString` öğe görüntülenir.

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

`IncludeView`Ve `ExcludeView` öznitelikleri, belirli görünümlerde görüntülenecek veya görüntülenecek öğeleri belirtir. Örneğin, aşağıdaki Natvis belirtiminde, `std::vector` `simple` görünümü `[size]` ve `[capacity]` öğelerini görüntülemez.

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

`IncludeView`Ve `ExcludeView` özniteliklerini, türleri ve ayrı Üyeler üzerinde kullanabilirsiniz.

### <a name="version-element"></a><a name="BKMK_Versioning"></a> Sürüm öğesi
`Version`Öğesi, bir görselleştirme girişini belirli bir modüle ve sürüme kapsamlar. `Version`Öğesi ad çakışmalarını önlemeye yardımcı olur, yanlışlıkla uyuşmazlıkları azaltır ve farklı tür sürümleri için farklı görselleştirmelere izin verir.

Farklı modüller tarafından kullanılan ortak bir üst bilgi dosyası bir türü tanımlıyorsa, sürümlü görselleştirme yalnızca tür belirtilen modül sürümünde olduğunda görünür.

Aşağıdaki örnekte, görselleştirme yalnızca `DirectUI::Border` 1,0 sürümünden 1,5 ' de bulunan tür için geçerlidir `Windows.UI.Xaml.dll` .

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Ve öğelerinin her ikisine de ihtiyacınız yoktur `Min` `Max` . Bunlar isteğe bağlı özniteliklerdir. Joker karakter desteklenmez.

`Name`Özniteliği, *hello.exe* veya *some.dll*gibi *filename. ext*biçimindedir. Hiçbir yol adına izin verilmez.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a> DisplayString öğesi
`DisplayString`Öğesi, bir değişkenin değeri olarak göstermek için bir dize belirtir. İfadelerle karışık rastgele dizeler kabul eder. Küme ayraçları içindeki her şey bir ifade olarak yorumlanır. Örneğin, aşağıdaki `DisplayString` giriş:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Türündeki değişkenlerin `CPoint` Bu çizimde gösterildiği gibi gösterdiği anlamına gelir:

 ![Bir DisplayString öğesi kullanın](../debugger/media/dbg_natvis_cpoint_displaystring.png "Bir DisplayString öğesi kullanın")

İfadesinde, `DisplayString` üyesi olan `x` ve `y` `CPoint` küme ayraçları içinde olduğu için değerleri değerlendirilir. Örnek ayrıca çift küme ayraçları (veya) kullanarak bir küme ayracını nasıl atkullanabileceğinizi gösterir `{{` `}}` .

> [!NOTE]
> `DisplayString`Öğesi, rastgele dizeleri ve küme ayracı sözdizimini kabul eden tek öğedir. Diğer tüm Görselleştirme öğeleri yalnızca hata ayıklayıcının değerlendirebilmesi için ifadeleri kabul eder.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a> StringView öğesi

`StringView`Öğesi, hata ayıklayıcının yerleşik metin Görselleştirici öğesine gönderebileceğini bir değer tanımlar. Örneğin, türü için aşağıdaki görselleştirme verildiğinde `ATL::CStringT` :

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

`CStringT`Nesnesi aşağıdaki örnekteki gibi bir değişken penceresinde görüntülenir:

![CStringT DisplayString öğesi](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT DisplayString öğesi")

Bir `StringView` öğesi eklemek, hata ayıklayıcıya bir metin görselleştirmesi olarak değerini görüntülemesini söyler.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Hata ayıklama sırasında, değişkenin yanındaki büyüteç simgesini seçebilir ve ardından **m_pszData** işaret eden dizeyi göstermek Için **metin görselleştiricisi** ' ı seçebilirsiniz.

 ![StringView görselleştiricisi ile CStringT verileri](../debugger/media/dbg_natvis_stringview_cstringt.png "StringView görselleştiricisi ile CStringT verileri")

İfade, `{m_pszData,su}` değeri bir Unicode dize olarak göstermek için bir C++ Biçim belirleyicisi **su**içerir. Daha fazla bilgi için bkz. [C++ ' da biçim belirticileri](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a> Öğeyi Genişlet

İsteğe bağlı `Expand` düğüm, türü bir değişken penceresinde genişlettiğinizde görselleştirilen bir türün alt öğelerini özelleştirir. `Expand`Düğüm, alt öğeleri tanımlayan alt düğümlerin listesini kabul eder.

- Bir `Expand` görselleştirme girişinde bir düğüm belirtilmemişse, alt öğeler varsayılan genişletme kurallarını kullanır.

- `Expand`Düğüm altında alt düğüm olmayan bir düğüm belirtilmişse, tür hata ayıklayıcı penceresinde genişletilebilir değildir.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Öğe genişletmesi

 `Item`Öğesi, bir düğümdeki en temel ve ortak öğedir `Expand` . `Item` tek bir alt öğe tanımlar. Örneğin,,, `CRect` ve alanlarını içeren bir sınıf `top` `left` `right` `bottom` aşağıdaki görselleştirme girişine sahiptir:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Hata ayıklayıcı penceresinde, tür şöyle `CRect` görünür:

![Öğe öğesi genişlemesiyle CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "Öğe öğesi genişlemesiyle CRect")

Hata ayıklayıcı, ve öğelerinde belirtilen ifadeleri değerlendirir `Width` `Height` ve değişken penceresinin **değer** sütunundaki değerleri gösterir.

Hata ayıklayıcı her özel genişletme için **[ham Görünüm]** düğümünü otomatik olarak oluşturur. Önceki ekran görüntüsünde, nesnenin varsayılan ham görünümünün Natvis görselleştirmesinden nasıl farklı olduğunu göstermek için genişletilmiş **[ham Görünüm]** düğümü görüntülenir. Varsayılan genişletme, temel sınıf için bir alt ağaç oluşturur ve temel sınıfın tüm veri üyelerini alt öğe olarak listeler.

> [!NOTE]
> Öğe öğesinin ifadesi karmaşık bir türe işaret ediyorsa, **öğe** düğümünün kendisi Genişletilebilir olur.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> ArrayItems genişletmesi
`ArrayItems`Visual Studio hata ayıklayıcının türü bir dizi olarak yorumlamasını ve bireysel öğelerini görüntülemesini sağlamak için düğümünü kullanın. Görselleştirmesi `std::vector` iyi bir örnektir:

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

`std::vector`, Değişken penceresinde genişletildiğinde tek tek öğelerini gösterir:

![std:: ArrayItems genişletmesi kullanan vektör](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std:: ArrayItems genişletmesi kullanan vektör")

Düğüm şu olmalıdır `ArrayItems` :

- `Size`Hata ayıklayıcının dizi uzunluğunu anlaması için bir ifade (bir tamsayı olarak değerlendirilmesi gerekir).
- `ValuePointer`İlk öğeyi işaret eden bir ifade (olmayan bir öğe türünün işaretçisi olması gerekir `void*` ).

Dizi alt sınırının varsayılan değeri 0 ' dır. Değeri geçersiz kılmak için bir öğesi kullanın `LowerBound` . Visual Studio ile birlikte gelen *. natvis* dosyalarında örneklere sahip.

>[!NOTE]
>`[]`İşleci, örneğin `vector[i]` `ArrayItems` kendisi (örneğin `CATLArray` ) bu işlece izin vermediği halde, kullanan herhangi bir tek boyutlu dizi görselleştirmesi ile birlikte kullanabilirsiniz.

Çok boyutlu diziler de belirtebilirsiniz. Bu durumda, hata ayıklayıcının alt öğeleri düzgün şekilde görüntülemesi için biraz daha fazla bilgi gerekir:

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

- `Direction` dizinin satır içi mi yoksa sütun birincil sırada mı olduğunu belirtir.
- `Rank` dizinin derecesini belirtir.
- `Size`Öğesi, `$i` Bu boyuttaki dizinin uzunluğunu bulmak için boyut diziniyle birlikte bulunan örtük parametreyi kabul eder. Önceki örnekte, ifadesi `_M_extent.M_base[0]` 0TH boyutunun, `_M_extent._M_base[1]` 1 ' in uzunluğuna ve bu şekilde devam eder.

İki boyutlu bir `Concurrency::array` nesne hata ayıklayıcı penceresinde nasıl görünür:

![ArrayItems genişletmesi olan iki boyutlu dizi](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "ArrayItems genişletmesi olan iki boyutlu dizi")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> IndexListItems genişletmesi

`ArrayItems`Genişletmeyi yalnızca dizi öğeleri bellekte bitişik olarak halinde düzenlense kullanabilirsiniz. Hata ayıklayıcı, işaretçisini arttırarak bir sonraki öğeye alır. Dizini değer düğümüne göre değiştirmeniz gerekiyorsa, `IndexListItems` düğümleri kullanın. Düğüm içeren bir görselleştirme aşağıda verilmiştir `IndexListItems` :

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

Ve arasındaki tek fark `ArrayItems` , `IndexListItems` `ValueNode` örtük parametresi olan i. öğesi için tam ifadeyi bekleyen öğesidir<sup>th</sup> `$i` .

>[!NOTE]
>`[]`İşleci, örneğin `vector[i]` `IndexListItems` kendisi (örneğin `CATLArray` ) bu işlece izin vermediği halde, kullanan herhangi bir tek boyutlu dizi görselleştirmesi ile birlikte kullanabilirsiniz.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems genişletmesi

Görselleştirilmiş tür bağlantılı bir listeyi temsil ediyorsa, hata ayıklayıcı alt öğelerini bir düğüm kullanarak görüntüleyebilir `LinkedListItems` . Türü için aşağıdaki görselleştirme şunları `CAtlList` kullanır `LinkedListItems` :

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

`Size`Öğesi, listenin uzunluğunu ifade eder. `HeadPointer` ilk öğesini işaret eder, `NextPointer` Sonraki öğesine başvurur ve `ValueNode` öğenin değerine başvurur.

Hata ayıklayıcı, `NextPointer` ve `ValueNode` ifadelerini, `LinkedListItems` üst liste türü değil, Node öğesi bağlamında değerlendirir. Önceki örnekte, `CAtlList` `CNode` bağlantılı listenin bir düğümü olan bir sınıfı (içinde bulunur `atlcoll.h` ) vardır. `m_pNext` ve `m_element` `CNode` , sınıfının değil, bu sınıfın alanlarıdır `CAtlList` .

`ValueNode` boş bırakılabilir veya `this` düğümün kendisini ifade etmek için kullanabilirsiniz `LinkedListItems` .

#### <a name="customlistitems-expansion"></a>CustomListItems genişletmesi

`CustomListItems`Genişletme, Hashtable gibi bir veri yapısına geçiş için özel mantık yazmanızı sağlar. `CustomListItems`Değerlendirmek için gereken her şey Için C++ ifadelerini kullanılabilecek veri yapılarını görselleştirmek için kullanın, ancak, veya için Mold ' i tam olarak uydurmayın `ArrayItems` `IndexListItems` `LinkedListItems` .

`Exec` `CustomListItems` Genişletmeyle tanımlanan değişkenleri ve nesneleri kullanarak bir genişletmenin içindeki kodu yürütmek için ' yi kullanabilirsiniz. İle mantıksal işleçler, aritmetik işleçler ve atama işleçlerini kullanabilirsiniz `Exec` . `Exec`C++ ifade değerlendiricisi tarafından desteklenen [hata ayıklayıcı iç işlevleri](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) dışında işlevleri değerlendirmek için kullanamazsınız.

İçin aşağıdaki Görselleştirici, `CAtlMap` uygun olduğu durumlarda mükemmel bir örnektir `CustomListItems` .

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

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> Ağaç öğeleri genişletmesi
 Görselleştirilen tür bir ağacı temsil ediyorsa, hata ayıklayıcı ağaca yol açabilir ve bir düğüm kullanarak alt öğelerini görüntüleyebilir `TreeItems` . `std::map`Bir düğüm kullanarak türün görselleştirmesi aşağıda verilmiştir `TreeItems` :

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

Sözdizimi, `LinkedListItems` düğümüne benzer. `LeftPointer`, `RightPointer` ve, `ValueNode` ağaç düğümü sınıfının bağlamı altında değerlendirilir. `ValueNode` boş bırakılabilir veya `this` düğümün kendisini ifade etmek için kullanılabilir `TreeItems` .

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem genişletmesi
 `ExpandedItem`Öğesi, temel sınıfların veya veri üyelerinin özelliklerini görselleştirilen türün alt öğeleri gibi görüntüleyerek toplanmış bir alt görünüm oluşturur. Hata ayıklayıcı belirtilen ifadeyi değerlendirir ve sonucun alt düğümlerini görselleştirilen türün alt listesine ekler.

Örneğin, akıllı işaretçi türü `auto_ptr<vector<int>>` genellikle şöyle görüntülenir:

 ![Otomatik&#95;PTR&#60;vektör&#60;int&#62;&#62; varsayılan genişletme](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Varsayılan genişletme")

 Vector öğesinin değerlerini görmek için, değişken penceresinde üye aracılığıyla geçen iki düzeyin ayrıntılarına sahip olmanız gerekir `_Myptr` . Bir öğe ekleyerek `ExpandedItem` , `_Myptr` değişkeni hiyerarşisinden ortadan kaldırabilir ve vektör öğelerini doğrudan görüntüleyebilirsiniz:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![Otomatik&#95;PTR&#60;vektör&#60;int&#62;&#62; ExpandedItem genişletmesi](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem genişletmesi")

Aşağıdaki örnek, türetilmiş bir sınıftaki temel sınıftan özelliklerin nasıl toplanacağını gösterir. `CPanel`Sınıfın türetildiğini varsayalım `CFrameworkElement` . Temel sınıftan gelen özellikleri yinelemek yerine `CFrameworkElement` , `ExpandedItem` düğüm görselleştirmesi bu özellikleri sınıfının alt listesine ekler `CPanel` .

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Türetilmiş sınıf için görselleştirme eşleştirmeyi kapatan **ND** Biçim belirleyicisi burada gereklidir. Aksi takdirde, `*(CFrameworkElement*)this` `CPanel` varsayılan görselleştirme türü eşleştirme kuralları en uygun olanı düşüntiğinden, ifade görselleştirmenin yeniden uygulanmasına neden olur. Hata ayıklayıcıya temel sınıf görselleştirmesini kullanmasını söylemek için **ND** biçim belirticisini veya temel sınıfın görselleştirmesi yoksa varsayılan genişletmeyi kullanın.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Yapay öğe genişletmesi
 Öğe, `ExpandedItem` hiyerarşileri ortadan kaldırarak verilerin düzbir görünümünü sağlarken, `Synthetic` düğüm tersini yapar. Bir ifadenin sonucu olmayan yapay bir alt öğe oluşturmanıza olanak sağlar. Yapay öğe kendi alt öğelerine sahip olabilir. Aşağıdaki örnekte, türü için görselleştirme, kullanıcıya bir `Concurrency::array` `Synthetic` tanılama iletisi göstermek için bir düğüm kullanır:

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

 ![Concurrency:: yapay öğe genişletmesi olan dizi](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency:: yapay öğe genişletmesi olan dizi")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a> HResult öğesi
 `HResult`Öğesi, hata ayıklayıcı penceresinde bir **HRESULT** için gösterilen bilgileri özelleştirmenize olanak sağlar. `HRValue`Öğesi, özelleştirilecek olan **HRESULT** 'nin 32 bitlik değerini içermelidir. `HRDescription`Öğesi, hata ayıklayıcı penceresinde gösterilecek bilgileri içerir.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a> UIVisualizer öğesi
Bir `UIVisualizer` öğesi bir grafik görselleştiricisi eklentisini hata ayıklayıcıyla kaydeder. Grafik görselleştiricisi bir iletişim kutusu veya bir değişken ya da nesneyi veri türüyle tutarlı bir şekilde gösteren başka bir arabirim oluşturur. Görselleştiricisi eklentisi [VSPackage](../extensibility/internals/vspackages.md)olarak yazılmalıdır ve hata ayıklayıcının tüketebileceği bir hizmeti kullanıma sunmalıdır. *. Natvis* dosyası, eklentinin adı, GÖSTERILEN hizmetin GUID 'i ve görselleştirilecek türler gibi, eklenti için kayıt bilgilerini içerir.

UIVisualizer öğesine bir örnek aşağıda verilmiştir:

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

- Bir `ServiceId`  -  `Id` öznitelik çifti bir tanımlar `UIVisualizer` . , `ServiceId` Görselleştiricisi paketinin sunduğu hizmetin GUID 'sidir. `Id` , bir hizmet birden fazla sağlıyorsa görselleştiricilerin fark eden benzersiz bir tanımlayıcıdır. Yukarıdaki örnekte, aynı görselleştiricisi hizmeti iki Görselleştiriciler sağlar.

- `MenuName`Öznitelik, hata ayıklayıcıdaki büyüteç simgesinin yanında açılan kutuda görüntülenecek Görselleştirici adını tanımlar. Örnek:

  ![UIVisualizer menü kısayol menüsü](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer menü kısayol menüsü")

*. Natvis* dosyasında tanımlanan her tür, kendisini görüntüleyebilen HERHANGI bir UI görselleştiricilerini açıkça listemelidir. Hata ayıklayıcı, kayıtlı görselleştiricilerde tür girişlerinde Görselleştirici başvurularıyla eşleşir. Örneğin, önceki örnekteki öğesine başvuru için aşağıdaki tür girişi `std::vector` `UIVisualizer` .

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 `UIVisualizer`Bellek içi bit eşlemler görüntülemek için kullanılan [görüntü izleme](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) uzantısında bir örneğini görebilirsiniz.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>CustomVisualizer öğesi
 `CustomVisualizer` , Visual Studio Code 'da görselleştirmeleri denetlemek için yazdığınız bir VSıX uzantısını belirten bir genişletilebilirlik noktasıdır. VSıX uzantıları yazma hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

XML Natvis tanımından özel bir Görselleştirici yazmak çok daha fazla çalışmadır, ancak Natvis 'ın ne yaptığını veya desteklemediği hakkında kısıtlamalardan ücretsiz olursunuz. Özel Görselleştiriciler hata ayıklama genişletilebilirlik API 'Lerinin tamamına erişebilir, bu da hata ayıklanan işlemi sorgulayabilir ve değiştirebilir veya Visual Studio 'nun diğer bölümleriyle iletişim kurabilir.

 `Condition` `IncludeView` Öğelerinde, ve `ExcludeView` özniteliklerini kullanabilirsiniz `CustomVisualizer` .

## <a name="limitations"></a>Sınırlamalar

Natvis özelleştirmeleri sınıflar ve yapılar ile çalışır, ancak Typedefs 'lar değildir.

Natvis, ilkel türler (örneğin, `int` , `bool` ) veya ilkel türlere yönelik işaretçiler için Görselleştiriciler desteklemez. Bu senaryoda, bir seçenek, kullanım çalışmanıza uygun [Biçim belirleyicisi](../debugger/format-specifiers-in-cpp.md) kullanmaktır. Örneğin, `double* mydoublearray` kodunuzda kullanıyorsanız, hata ayıklayıcının **Gözcü** penceresinde, `mydoublearray, [100]` ilk 100 öğesini gösteren ifadesi gibi bir dizi Biçim belirleyicisi kullanabilirsiniz.
