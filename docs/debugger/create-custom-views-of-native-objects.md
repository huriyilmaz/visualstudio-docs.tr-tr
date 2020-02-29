---
title: C++ nesnelerinin özel görünümlerini oluşturma
description: Visual Studio 'Nun hata ayıklayıcıda yerel türleri görüntüleme biçimini özelleştirmek için Natvis çerçevesini kullanın
ms.date: 10/31/2018
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
ms.openlocfilehash: 9c26c35c09353d740f6db9745222bb66db40e7ba
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167760"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Natvis çerçevesini kullanarak hata C++ ayıklayıcıda nesnelerin özel görünümlerini oluşturma

Visual Studio *Natvis* çerçevesi yerel türlerin hata ayıklayıcı değişken pencerelerinde görünme şeklini özelleştirir, örneğin **Yereller** ve **İzle** pencereleri ve **veri ipuçları**. Natvis görselleştirmeleri, oluşturduğunuz türlerin hata ayıklama sırasında daha görünür olmasına yardımcı olabilir.

Natvis, Visual Studio 'nun önceki sürümlerinde bulunan, XML sözdizimi, daha iyi tanılama, sürüm oluşturma ve birden çok dosya desteğiyle birlikte bulunan *oto. dat* dosyasını değiştirir.

> [!NOTE]
> Natvis özelleştirmeleri sınıflar ve yapılar ile çalışır, ancak Typedefs 'lar değildir.

## <a name="BKMK_Why_create_visualizations_"></a>Natvis görselleştirmeleri

Geliştiricilerin hata ayıklama sırasında daha kolay görebilmesi için, oluşturduğunuz türler için görselleştirme kuralları oluşturmak üzere Natvis çerçevesini kullanın.

Örneğin, aşağıdaki çizimde özel görselleştirmeler uygulanmamış bir hata ayıklayıcı penceresinde [Windows:: UI:: XAML:: Controls:: TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) türünde bir değişken gösterilmektedir.

![TextBox varsayılan görselleştirmesi](../debugger/media/dbg_natvis_textbox_default.png "TextBox varsayılan görselleştirmesi")

Vurgulanan satır, `TextBox` sınıfının `Text` özelliğini gösterir. Karmaşık sınıf hiyerarşisi bu özelliği bulmayı zorlaştırır. Hata ayıklayıcı özel dize türünü nasıl yorumlayacağını bilmez, bu nedenle TextBox içinde tutulan dizeyi göremezsiniz.

Aynı `TextBox` Natvis özel görselleştiricisi kuralları uygulandığında değişken penceresinde çok daha basit bir şekilde görünür. Sınıfının önemli üyeleri birlikte görünür ve hata ayıklayıcı özel dize türünün temel alınan dize değerini gösterir.

![Görselleştirici kullanarak metin kutusu verileri](../debugger/media/dbg_natvis_textbox_visualizer.png "Görselleştirici kullanarak metin kutusu verileri")

## <a name="BKMK_Using_Natvis_files"></a>C++ Projelerde. Natvis dosyalarını kullanma

Natvis, görselleştirme kurallarını belirtmek için *. natvis* dosyalarını kullanır. *. Natvis* dosyası. *NATVIS* uzantılı bir XML dosyasıdır. Natvis şeması *%VSInstallDir%\Xml\Schemas\natvis.exe*içinde tanımlanmıştır.

Bir *. natvis* dosyasının temel yapısı, görselleştirme girdilerini temsil eden bir veya daha fazla `Type` öğesi. Her bir `Type` öğesinin tam adı `Name` özniteliğinde belirtilir.

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

### <a name="add-a-natvis-file-to-a-c-project"></a>C++ Projeye bir. natvis dosyası ekleyin

Herhangi C++ bir projeye bir *. natvis* dosyası ekleyebilirsiniz.

**Yeni bir *. natvis* dosyası eklemek için:**

1. Çözüm Gezgini ' C++ de proje düğümünüseçin ve **Proje** > **Yeni öğe Ekle**' yi seçin veya projeye sağ tıklayıp > **Yeni öğe** **Ekle** ' yi seçin.

1. **Yeni öğe Ekle** iletişim kutusunda, **hata ayıklayıcı görselleştirme dosyası (. natvis)**  > **Visual C++**  > **yardımcı programı** ' nı seçin.

1. Dosyayı adlandırın ve **Ekle**' yi seçin.

   Yeni dosya **Çözüm Gezgini**eklenir ve Visual Studio belge bölmesinde açılır.

Visual Studio hata ayıklayıcı, *. natvis* dosyalarını C++ projelere otomatik olarak yükler ve varsayılan olarak, proje oluştururken *. pdb* dosyasında da içerir. Oluşturulan uygulamada hata ayıklaması yaparsanız, proje açık olmasa bile, hata ayıklayıcı. *pdb* dosyasından *. natvis* dosyasını yükler. .,. *Natvis* dosyasını *. pdb*dosyasına dahil etmek istemiyorsanız, bunu yerleşik *. pdb* dosyasından hariç bırakabilirsiniz.

**. *Natvis* dosyasını bir *. pdb*dosyasından dışlamak için:**

1. **Çözüm Gezgini** *. natvis* dosyasını seçin ve **Özellikler** simgesini seçin ya da dosyaya sağ tıklayıp **Özellikler**' i seçin.

1. **Derlemeden çıkarılan** ' ın yanındaki oku ve **Evet**' i seçin ve ardından **Tamam**' ı seçin.

>[!NOTE]
>Yürütülebilir projelerde hata ayıklama için, kullanılabilir proje bulunmadığından C++ , *. pdb*içinde olmayan *. natvis* dosyalarını eklemek için çözüm öğelerini kullanın.

>[!NOTE]
>Bir *. pdb* 'den yüklenen Natvis kuralları yalnızca *. pdb* 'nin başvurduğu modüllerde bulunan türlere uygulanır. Örneğin, *Module1. pdb* `Test`adlı bir tür için Natvis girişi varsa, bu yalnızca *Module1. dll*içindeki `Test` sınıfı için geçerlidir. Başka bir modül de `Test`adlı bir sınıfı tanımlıyorsa, *Module1. pdb* Natvis girdisi buna uygulanmaz.

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

### <a name="BKMK_natvis_location"></a>Natvis dosya konumları

Birden çok projeye uygulanmasını istiyorsanız, *. natvis* dosyalarını Kullanıcı dizininize veya bir sistem dizinine ekleyebilirsiniz.

*. Natvis* dosyaları aşağıdaki sırayla değerlendirilir:

1. Yüklü projede aynı ada sahip bir dosya mevcut değilse, bir *. pdb* dosyasına gömülü tüm *. natvis* dosyaları hata ayıklaması yapılır.

2. Yüklü C++ bir proje veya üst düzey çözümdeki *. natvis* dosyaları. Bu grup, sınıf kitaplıkları C++ da dahil olmak üzere tüm yüklü projeleri içerir, ancak diğer dillerdeki projeler içermez.

3. Herhangi bir *. natvis* dosyası, bir VSIX paketi aracılığıyla yüklenir ve kaydedilir.

::: moniker range="vs-2017"

4. Kullanıcıya özgü Natvis dizini (örneğin, *%userprofile%\, Visual Studio 2017 \ Görselleştiriciler*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Kullanıcıya özgü Natvis dizini (örneğin, *%userprofile%\, Studio 2019 \ Görselleştiriciler*).

::: moniker-end

5. Sistem genelindeki Natvis dizini ( *%VSInstallDir%\common7\packages\debugger\görselleştiriciler*). Bu dizin, Visual Studio ile yüklenen *. natvis* dosyalarını içerir. Yönetici izinleriniz varsa, bu dizine dosyalar ekleyebilirsiniz.

## <a name="modify-natvis-files-while-debugging"></a>Hata ayıklarken. Natvis dosyalarını değiştirme

Projesinde hata ayıklarken IDE 'deki bir *. natvis* dosyasını değiştirebilirsiniz. Dosyayı hata ayıklaması yaptığınız aynı Visual Studio örneğinde açın, değiştirin ve kaydedin. Dosya kaydedildiği anda, değişikliği yansıtmak için **Watch** ve **Locals** Windows Update.

Ayrıca, hata ayıklaması yaptığınız bir çözüme *. natvis* dosyaları ekleyebilir veya silebilirsiniz ve Visual Studio ilgili görselleştirmeleri ekler veya kaldırır.

Hata ayıklarken *. pdb* dosyalarına katıştırılmış *. natvis* dosyalarını güncelleştiremezsiniz.

*. Natvis* dosyasını Visual Studio dışında değiştirirseniz, değişiklikler otomatik olarak geçerli olmaz. Hata ayıklayıcı pencerelerini güncelleştirmek için, **izleme** penceresindeki **. natvisreload komutunu yeniden** değerlendirmeye alabilirsiniz. Ardından, değişiklikler hata ayıklama oturumunu yeniden başlatmadan geçerli olur.

. *Natvis* dosyasını daha yeni bir sürüme yükseltmek için **. natvisreload** komutunu da kullanabilirsiniz. Örneğin, *. natvis* dosyası kaynak denetimine iade edilebilir ve başka birisinin yaptığı son değişiklikleri almak istiyorsunuz.

## <a name="BKMK_Expressions_and_formatting"></a>İfadeler ve biçimlendirme
Natvis görselleştirmeleri C++ görüntülenecek veri öğelerini belirtmek için ifadeleri kullanır. [Bağlam operatörü (C++)](../debugger/context-operator-cpp.md)bölümünde açıklanan, hata C++ Ayıklayıcıdaki ifadelerin geliştirmelere ve kısıtlamalarına ek olarak, aşağıdakilere dikkat edin:

- Natvis ifadeleri, geçerli yığın çerçevesini değil görselleştirilen nesne bağlamında değerlendirilir. Örneğin, bir Natvis ifadesindeki `x`, geçerli işlevde **x** adlı yerel bir değişkene değil, görselleştirilen nesnede **x** adlı alana başvurur. Küresel değişkenlere erişebilseniz de, Natvis ifadelerinde yerel değişkenlere erişemezsiniz.

- Natvis ifadeleri işlev değerlendirmesi veya yan etkilere izin vermez. İşlev çağrıları ve atama işleçleri yok sayılır. [Hata ayıklayıcı iç işlevleri](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) yan etkilerden farklı olduğundan, diğer işlev çağrılarına izin verilmese de, her bir natvis ifadesinden serbestçe çağrılabilir.

- Bir ifadenin nasıl görüntüleneceğini denetlemek için, [Içinde C++biçim tanımlayıcıda ](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)açıklanan biçim belirticilerini kullanabilirsiniz. Bir dizi [öğe genişletmesinde](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)`Size` ifadesi gibi, giriş Natvis tarafından dahili olarak kullanıldığında biçim belirticileri yok sayılır.

## <a name="natvis-views"></a>Natvis görünümleri

Farklı yollarla türleri göstermek için farklı Natvis görünümleri tanımlayabilirsiniz. Örneğin, `simple`adlı basitleştirilmiş bir görünümü tanımlayan `std::vector` görselleştirmesi aşağıda verilmiştir. `DisplayString` ve `ArrayItems` öğeleri varsayılan görünümde ve `simple` görünümünde gösterilir, ancak `[size]` ve `[capacity]` öğeleri `simple` görünümünde gösterilmez.

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

**İzleme** penceresinde, alternatif bir görünüm belirtmek için **, görünüm** biçim belirticisini kullanın. Basit görünüm VEC olarak görünür **, görünüm (basit)** :

![Basit görünümle izleme penceresi](../debugger/media/watch-simpleview.png "Basit görünümle izleme penceresi")

## <a name="BKMK_Diagnosing_Natvis_errors"></a>Natvis hataları

Hata ayıklayıcı bir görselleştirme girişinde hatalarla karşılaştığında onları yoksayar. Bu, türü ham biçiminde görüntüler ya da uygun bir görselleştirme seçer. Hata ayıklayıcının bir görselleştirme girişini neden yoksaydığını anlamak ve temeldeki sözdizimi ve ayrıştırma hatalarını görmek için Natvis tanılamayı kullanabilirsiniz.

**Natvis tanılamayı açmak için:**

- **Araçlar** > **Seçenekler** (ya da **hata ayıkla** > **Seçenekler**) > hata **ayıklama** > **Çıkış penceresi**, **Natvis tanılama IletileriC++ (yalnızca)** **hata**, **Uyarı**veya **ayrıntılı**olarak ayarlayın ve ardından **Tamam**' ı seçin.

Hatalar **Çıkış** penceresinde görüntülenir.

## <a name="BKMK_Syntax_reference"></a>Natvis sözdizimi başvurusu

### <a name="BKMK_AutoVisualizer"></a>Oto görselleştiricisi öğesi
`AutoVisualizer` öğesi *. natvis* dosyasının kök düğümüdür ve ad alanı `xmlns:` özniteliğini içerir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

`AutoVisualizer` öğesi [Type](#BKMK_Type), [HRESULT](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)ve [CustomVisualizer](#BKMK_CustomVisualizer) alt öğelerine sahip olabilir.

### <a name="BKMK_Type"></a>Type öğesi

Temel `Type` aşağıdaki örnekteki gibi görünür:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 `Type` öğesi şunları belirtir:

1. Görselleştirmenin kullanılması gereken tür (`Name` özniteliği).

2. Bu türdeki bir nesnenin değeri şöyle görünmelidir (`DisplayString` öğesi).

3. Kullanıcı türü bir değişken penceresinde (`Expand` düğümü) genişlediğinde, türün üyeleri şöyle görünmelidir.

#### <a name="templated-classes"></a>Şablonlu sınıflar
`Type` öğesinin `Name` özniteliği, şablonlu sınıf adları için kullanılabilen bir joker karakter olarak bir yıldız işareti `*` kabul eder.

Aşağıdaki örnekte, nesnenin `CAtlArray<int>` mı yoksa `CAtlArray<float>`mi olduğunu aynı görselleştirme kullanılır. Bir `CAtlArray<float>`için belirli bir görselleştirme girişi varsa, genel bir tane üzerinden önceliklidir.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

$T 1, $T 2 vb. makroları kullanarak görselleştirme girişinde şablon parametrelerine başvurabilirsiniz. Bu makroların örneklerini bulmak için bkz. Visual Studio ile birlikte gelen *. natvis* dosyaları.

#### <a name="BKMK_Visualizer_type_matching"></a>Görselleştiricisi türü eşleşiyor
Bir görselleştirme girişi doğrulanamazsa, bir sonraki kullanılabilir görselleştirme kullanılır.

#### <a name="inheritable-attribute"></a>Inheritable özniteliği
İsteğe bağlı `Inheritable` özniteliği, bir görselleştirmenin yalnızca bir temel türe mi yoksa bir temel türe ve tüm türetilmiş türlere mi uygulanacağını belirtir. `Inheritable` varsayılan değeri `true`.

Aşağıdaki örnekte, görselleştirme yalnızca `BaseClass` türü için geçerlidir:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priority özniteliği

İsteğe bağlı `Priority` özniteliği, tanım ayrıştıramazsa alternatif tanımların kullanılacağı sırayı belirtir. `Priority` olası değerleri şunlardır: `Low`, `MediumLow`,`Medium`, `MediumHigh`ve `High`. Varsayılan değer `Medium` şeklindedir. `Priority` özniteliği yalnızca aynı *. natvis* dosyasındaki öncelikler arasında ayrım yapar.

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
Herhangi bir düğüme bir `Optional` özniteliği yerleştirebilirsiniz. İsteğe bağlı bir düğümün içindeki bir alt ifade ayrıştıramazsa, hata ayıklayıcı bu düğümü yoksayar, ancak `Type` kuralların geri kalanını uygular. Aşağıdaki türde `[State]` isteğe bağlı değildir, ancak `[Exception]` isteğe bağlıdır.  `MyNamespace::MyClass` _`M_exceptionHolder`adlı bir alana sahipse, hem `[State]` düğümü hem de `[Exception]` düğümü görüntülenir, ancak `_M_exceptionHolder` alanı yoksa yalnızca `[State]` düğümü görüntülenir.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="BKMK_Condition_attribute"></a>Condition özniteliği

İsteğe bağlı `Condition` özniteliği birçok görselleştirme öğesi için kullanılabilir ve bir görselleştirme kuralının ne zaman kullanılacağını belirtir. Koşul özniteliği içindeki ifade `false`olarak çözümlenirse görselleştirme kuralı uygulanmaz. `true`olarak değerlendirilirse veya `Condition` özniteliği yoksa görselleştirme uygulanır. Görselleştirme girişlerinde If-Else mantığı için bu özniteliği kullanabilirsiniz.

Örneğin, aşağıdaki görselleştirmede akıllı işaretçi türü için iki `DisplayString` öğesi vardır. `_Myptr` üyesi boş olduğunda, ilk `DisplayString` öğenin koşulu `true`olarak çözümlenir, böylece form görüntülenir. `_Myptr` üyesi boş olmadığında, koşul `false`olarak değerlendirilir ve ikinci `DisplayString` öğesi görüntülenir.

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

`IncludeView` ve `ExcludeView` öznitelikleri, belirli görünümlerde görüntülenecek veya görüntülenecek öğeleri belirtir. Örneğin, aşağıdaki Natvis `std::vector`belirtiminde, `simple` görünümü `[size]` ve `[capacity]` öğelerini görüntülemez.

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

`IncludeView` ve `ExcludeView` özniteliklerini türler üzerinde ve ayrı Üyeler üzerinde kullanabilirsiniz.

### <a name="BKMK_Versioning"></a>Sürüm öğesi
`Version` öğesi, bir görselleştirme girişini belirli bir modüle ve sürüme kapsamlar. `Version` öğesi ad çakışmalarını önlemeye yardımcı olur, yanlışlıkla uyuşmazlıkları azaltır ve farklı tür sürümleri için farklı görselleştirmelere izin verir.

Farklı modüller tarafından kullanılan ortak bir üst bilgi dosyası bir türü tanımlıyorsa, sürümlü görselleştirme yalnızca tür belirtilen modül sürümünde olduğunda görünür.

Aşağıdaki örnekte, görselleştirme yalnızca 1,0 sürümünden 1,5 sürümüne `Windows.UI.Xaml.dll` bulunan `DirectUI::Border` türü için geçerlidir.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Hem `Min` hem de `Max`gerekmez. Bunlar isteğe bağlı özniteliklerdir. Joker karakter desteklenmez.

`Name` özniteliği, *Hello. exe* veya *bir. dll*gibi *filename. ext*biçimindedir. Hiçbir yol adına izin verilmez.

### <a name="BKMK_DisplayString"></a>DisplayString öğesi
`DisplayString` öğesi, bir değişkenin değeri olarak göstermek için bir dize belirtir. İfadelerle karışık rastgele dizeler kabul eder. Küme ayraçları içindeki her şey bir ifade olarak yorumlanır. Örneğin, aşağıdaki `DisplayString` girdisi:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Türündeki değişkenlerin Bu çizimde gösterildiği gibi `CPoint` gösterir:

 ![Bir DisplayString öğesi kullanın](../debugger/media/dbg_natvis_cpoint_displaystring.png "Bir DisplayString öğesi kullanın")

`DisplayString` ifadesinde, `CPoint`üyeleri olan `x` ve `y`küme ayraçları içindedir, bu nedenle değerleri değerlendirilir. Örnek ayrıca çift küme ayraçları (`{{` veya `}}`) kullanarak bir küme ayracını nasıl atkullanabileceğinizi gösterir.

> [!NOTE]
> `DisplayString` öğesi, rastgele dizeleri ve küme ayracı sözdizimini kabul eden tek öğedir. Diğer tüm Görselleştirme öğeleri yalnızca hata ayıklayıcının değerlendirebilmesi için ifadeleri kabul eder.

### <a name="BKMK_StringView"></a>StringView öğesi

`StringView` öğesi, hata ayıklayıcının yerleşik metin Görselleştirici öğesine gönderebileceğini bir değer tanımlar. Örneğin, `ATL::CStringT` türü için aşağıdaki görselleştirme verildiğinde:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

`CStringT` nesnesi aşağıdaki örnekteki gibi bir değişken penceresinde görüntülenir:

![CStringT DisplayString öğesi](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT DisplayString öğesi")

`StringView` bir öğesi eklemek, hata ayıklayıcıya bir metin görselleştirmesi olarak değeri göstermesini söyler.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Hata ayıklama sırasında, değişkenin yanındaki büyüteç simgesini seçebilir ve ardından **m_pszData** işaret eden dizeyi göstermek Için **metin görselleştiricisi** ' ı seçebilirsiniz.

 ![StringView görselleştiricisi ile CStringT verileri](../debugger/media/dbg_natvis_stringview_cstringt.png "StringView görselleştiricisi ile CStringT verileri")

`{m_pszData,su}` ifade, değeri bir C++ Unicode dize olarak göstermek için bir Biçim belirleyicisi **su**içerir. Daha fazla bilgi için bkz. [ C++içindeki biçim belirticileri ](../debugger/format-specifiers-in-cpp.md).

### <a name="BKMK_Expand"></a>Öğeyi Genişlet

İsteğe bağlı `Expand` düğümü, türü bir değişken penceresinde genişlettiğinizde görselleştirilen bir türün alt öğelerini özelleştirir. `Expand` düğümü, alt öğeleri tanımlayan alt düğümlerin listesini kabul eder.

- Bir görselleştirme girişinde `Expand` bir düğüm belirtilmemişse, alt öğeler varsayılan genişletme kurallarını kullanır.

- Bir `Expand` düğümü altında alt düğüm olmadan belirtilirse, tür hata ayıklayıcı penceresinde genişletilebilir değildir.

#### <a name="BKMK_Item_expansion"></a>Öğe genişletmesi

 `Item` öğesi, bir `Expand` düğümündeki en temel ve ortak öğedir. `Item` tek bir alt öğe tanımlıyor. Örneğin, `top`, `left`, `right`ve `bottom` alanları olan bir `CRect` sınıfı aşağıdaki görselleştirme girişine sahiptir:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Hata ayıklayıcı penceresinde `CRect` türü şu örneğe benzer şekilde görünür:

![Öğe öğesi genişlemesiyle CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "Öğe öğesi genişlemesiyle CRect")

Hata ayıklayıcı `Width` ve `Height` öğelerinde belirtilen ifadeleri değerlendirir ve değişken penceresinin **değer** sütunundaki değerleri gösterir.

Hata ayıklayıcı her özel genişletme için **[ham Görünüm]** düğümünü otomatik olarak oluşturur. Önceki ekran görüntüsünde, nesnenin varsayılan ham görünümünün Natvis görselleştirmesinden nasıl farklı olduğunu göstermek için genişletilmiş **[ham Görünüm]** düğümü görüntülenir. Varsayılan genişletme, temel sınıf için bir alt ağaç oluşturur ve temel sınıfın tüm veri üyelerini alt öğe olarak listeler.

> [!NOTE]
> Öğe öğesinin ifadesi karmaşık bir türe işaret ediyorsa, **öğe** düğümünün kendisi Genişletilebilir olur.

#### <a name="BKMK_ArrayItems_expansion"></a>ArrayItems genişletmesi
Visual Studio hata ayıklayıcının türü bir dizi olarak yorumlamasını ve bireysel öğelerini görüntülemesini sağlamak için `ArrayItems` düğümünü kullanın. `std::vector` görselleştirmesi iyi bir örnektir:

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

`std::vector`, bağımsız öğelerini değişken penceresinde genişletildiğinde gösterir:

![std:: ArrayItems genişletmesi kullanan vektör](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std:: ArrayItems genişletmesi kullanan vektör")

`ArrayItems` düğüm şunları içermelidir:

- Hata ayıklayıcının dizi uzunluğunu anlaması için bir `Size` ifadesi (bir tamsayı olarak değerlendirilmesi gerekir).
- İlk öğeyi işaret eden bir `ValuePointer` ifadesi (`void*`olmayan bir öğe türünün işaretçisi olması gerekir).

Dizi alt sınırının varsayılan değeri 0 ' dır. Değeri geçersiz kılmak için bir `LowerBound` öğesi kullanın. Visual Studio ile birlikte gelen *. natvis* dosyalarında örneklere sahip.

>[!NOTE]
>Türün kendisi (örneğin, `CATLArray`) bu işlece izin vermediği halde, `ArrayItems`kullanan tek boyutlu dizi görselleştirmelere sahip `vector[i]`gibi `[]` işlecini kullanabilirsiniz.

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
- `Size` öğesi, bu boyuttaki dizinin uzunluğunu bulmak için boyut diziniyle birlikte bulunan örtük `$i` parametresini kabul eder. Önceki örnekte, `_M_extent.M_base[0]` ifadesi 0. boyutun uzunluğuna, 1 ' i `_M_extent._M_base[1]` ve bu şekilde devam eder.

İki boyutlu bir `Concurrency::array` nesnesinin hata ayıklayıcı penceresinde nasıl göründüğünü aşağıda görebilirsiniz:

![ArrayItems genişletmesi olan iki boyutlu dizi](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "ArrayItems genişletmesi olan iki boyutlu dizi")

#### <a name="BKMK_IndexListItems_expansion"></a>IndexListItems genişletmesi

`ArrayItems` genişletmeyi yalnızca dizi öğeleri bellekte bitişik olarak olarak düzenlense kullanabilirsiniz. Hata ayıklayıcı, işaretçisini arttırarak bir sonraki öğeye alır. Dizini değer düğümüne göre değiştirmeniz gerekiyorsa `IndexListItems` düğümlerini kullanın. `IndexListItems` düğümü olan bir görselleştirme aşağıda verilmiştir:

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

`ArrayItems` ve `IndexListItems` arasındaki tek fark, örtük `$i` parametresiyle i<sup>. öğesi için</sup> tam ifadeyi bekleyen `ValueNode`.

>[!NOTE]
>Türün kendisi (örneğin, `CATLArray`) bu işlece izin vermediği halde, `IndexListItems`kullanan tek boyutlu dizi görselleştirmelere sahip `vector[i]`gibi `[]` işlecini kullanabilirsiniz.

#### <a name="BKMK_LinkedListItems_expansion"></a>LinkedListItems genişletmesi

Görselleştirilmiş tür bağlantılı bir listeyi temsil ediyorsa, hata ayıklayıcı alt öğelerini bir `LinkedListItems` düğümü kullanarak görüntüleyebilir. `CAtlList` türü için aşağıdaki görselleştirme `LinkedListItems`kullanır:

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

`Size` öğesi, listenin uzunluğunu ifade eder. `HeadPointer` ilk öğeye işaret eder, `NextPointer` bir sonraki öğeye başvurur ve `ValueNode` öğenin değerini gösterir.

Hata ayıklayıcı, `NextPointer` ve `ValueNode` ifadelerini, üst liste türü değil `LinkedListItems` node öğesi bağlamında değerlendirir. Yukarıdaki örnekte `CAtlList`, bağlantılı listenin bir düğümü olan `CNode` bir sınıfa (`atlcoll.h`bulunur) sahiptir. `m_pNext` ve `m_element`, `CAtlList` sınıfının değil, `CNode` sınıfının alanlarıdır.

`ValueNode` boş bırakılabilir veya `LinkedListItems` düğümüne başvurmak için `this` kullanabilirsiniz.

#### <a name="customlistitems-expansion"></a>CustomListItems genişletmesi
`CustomListItems` genişletmesi, Hashtable gibi bir veri yapısına geçiş yapmak için özel mantık yazmanızı sağlar. Değerlendirmek için gereken her şeye yönelik ifadeleri kullanan C++ veri yapılarını görselleştirmek için `CustomListItems` kullanın, ancak `ArrayItems`, `IndexListItems`veya `LinkedListItems`için Mold 'ı tam olarak uydurmayın.

`CAtlMap` için aşağıdaki Görselleştirici, `CustomListItems` uygun olan harika bir örnektir.

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

`Exec`, genişletmeyle tanımlanan değişkenleri ve nesneleri kullanarak `CustomListItems` genişletmenin içinde kod yürütmek için kullanabilirsiniz. `Exec`ile mantıksal işleçler, aritmetik işleçler ve atama işleçlerini kullanabilirsiniz. İşlevleri değerlendirmek için `Exec` kullanamazsınız.

`CustomListItems` aşağıdaki iç işlevleri destekler:

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

#### <a name="BKMK_TreeItems_expansion"></a>Ağaç öğeleri genişletmesi
 Görselleştirilmiş tür bir ağacı temsil ediyorsa, hata ayıklayıcı ağaca yol açabilir ve bir `TreeItems` düğümü kullanarak alt öğelerini görüntüleyebilir. Bir `TreeItems` düğümü kullanarak `std::map` türünün görselleştirmesi aşağıda verilmiştir:

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

Söz dizimi `LinkedListItems` düğümüne benzerdir. `LeftPointer`, `RightPointer`ve `ValueNode`, ağaç düğümü sınıfının bağlamı altında değerlendirilir. `ValueNode` boş bırakılabilir veya `TreeItems` düğümüne başvurmak için `this` kullanabilirsiniz.

#### <a name="BKMK_ExpandedItem_expansion"></a>ExpandedItem genişletmesi
 `ExpandedItem` öğesi, temel sınıfların veya veri üyelerinin özelliklerini görselleştirilen türün alt öğeleri gibi görüntüleyerek toplanmış bir alt görünüm oluşturur. Hata ayıklayıcı belirtilen ifadeyi değerlendirir ve sonucun alt düğümlerini görselleştirilen türün alt listesine ekler.

Örneğin, akıllı işaretçi türü `auto_ptr<vector<int>>` genellikle şöyle görünür:

 ![Otomatik&#95;PTR&#60;vektör&#60;int&#62; &#62; varsayılan genişletmesi](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Varsayılan genişletme")

 Vector öğesinin değerlerini görmek için, değişken penceresinde iki düzeyin detayına geçerek `_Myptr` üye aracılığıyla geçiş yapmanız gerekir. `ExpandedItem` bir öğesi ekleyerek `_Myptr` değişkenini hiyerarşisinden ortadan kaldırabilir ve vektör öğelerini doğrudan görüntüleyebilirsiniz:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![Otomatik&#95;PTR&#60;vektör&#60;int&#62; &#62; ExpandedItem genişletmesi](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem genişletmesi")

Aşağıdaki örnek, türetilmiş bir sınıftaki temel sınıftan özelliklerin nasıl toplanacağını gösterir. `CPanel` sınıfın `CFrameworkElement`türediğini varsayalım. Temel `CFrameworkElement` sınıfından gelen özellikleri yinelemek yerine, `ExpandedItem` düğümü görselleştirmesi bu özellikleri `CPanel` sınıfının alt listesine ekler.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Türetilmiş sınıf için görselleştirme eşleştirmeyi kapatan **ND** Biçim belirleyicisi burada gereklidir. Aksi takdirde `*(CFrameworkElement*)this` ifade, varsayılan görselleştirme türü eşleştirme kuralları en uygun olanı düşüntiğinden, `CPanel` görselleştirmesinin yeniden uygulanmasına neden olur. Hata ayıklayıcıya temel sınıf görselleştirmesini kullanmasını söylemek için **ND** biçim belirticisini veya temel sınıfın görselleştirmesi yoksa varsayılan genişletmeyi kullanın.

#### <a name="BKMK_Synthetic_Item_expansion"></a>Yapay öğe genişletmesi
 `ExpandedItem` öğesi hiyerarşileri ortadan kaldırarak verilerin düzbir görünümünü sağladığından, `Synthetic` düğümü tersini yapar. Bir ifadenin sonucu olmayan yapay bir alt öğe oluşturmanıza olanak sağlar. Yapay öğe kendi alt öğelerine sahip olabilir. Aşağıdaki örnekte, `Concurrency::array` türü için görselleştirme, kullanıcıya bir tanılama iletisi göstermek için bir `Synthetic` düğümü kullanır:

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

### <a name="BKMK_HResult"></a>HResult öğesi
 `HResult` öğesi, hata ayıklayıcı penceresinde bir **HRESULT** için gösterilen bilgileri özelleştirmenize olanak sağlar. `HRValue` öğesi, özelleştirilecek olan **HRESULT** 'nin 32 bitlik değerini içermelidir. `HRDescription` öğesi, hata ayıklayıcı penceresinde gösterilecek bilgileri içerir.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="BKMK_UIVisualizer"></a>UIVisualizer öğesi
`UIVisualizer` öğesi bir grafik görselleştiricisi eklentisini hata ayıklayıcıyla kaydeder. Grafik görselleştiricisi bir iletişim kutusu veya bir değişken ya da nesneyi veri türüyle tutarlı bir şekilde gösteren başka bir arabirim oluşturur. Görselleştiricisi eklentisi [VSPackage](../extensibility/internals/vspackages.md)olarak yazılmalıdır ve hata ayıklayıcının tüketebileceği bir hizmeti kullanıma sunmalıdır. *. Natvis* dosyası, eklentinin adı, GÖSTERILEN hizmetin GUID 'i ve görselleştirilecek türler gibi, eklenti için kayıt bilgilerini içerir.

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

- Bir `ServiceId` - `Id` öznitelik çifti bir `UIVisualizer`tanımlar. `ServiceId`, görselleştiricisi paketinin sunduğu hizmetin GUID 'sidir. `Id`, bir hizmet birden fazla sağlıyorsa görselleştiricilerin farklılaştırır. Yukarıdaki örnekte, aynı görselleştiricisi hizmeti iki Görselleştiriciler sağlar.

- `MenuName` özniteliği, hata ayıklayıcıdaki büyüteç simgesinin yanında açılan kutuda görüntülenecek Görselleştirici adını tanımlar. Örneğin:

  ![UIVisualizer menü kısayol menüsü](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer menü kısayol menüsü")

*. Natvis* dosyasında tanımlanan her tür, kendisini görüntüleyebilen HERHANGI bir UI görselleştiricilerini açıkça listemelidir. Hata ayıklayıcı, kayıtlı görselleştiricilerde tür girişlerinde Görselleştirici başvurularıyla eşleşir. Örneğin, `std::vector` için aşağıdaki tür girdisi, önceki örnekteki `UIVisualizer` başvurur.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Bellek içi bit eşlemler görüntülemek için kullanılan [görüntü izleme](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) uzantısında bir `UIVisualizer` örneğini görebilirsiniz.

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer öğesi
 `CustomVisualizer`, Visual Studio Code 'da görselleştirmeleri denetlemek için yazdığınız VSıX uzantısını belirten bir genişletilebilirlik noktasıdır. VSıX uzantıları yazma hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

XML Natvis tanımından özel bir Görselleştirici yazmak çok daha fazla çalışmadır, ancak Natvis 'ın ne yaptığını veya desteklemediği hakkında kısıtlamalardan ücretsiz olursunuz. Özel Görselleştiriciler hata ayıklama genişletilebilirlik API 'Lerinin tamamına erişebilir, bu da hata ayıklanan işlemi sorgulayabilir ve değiştirebilir veya Visual Studio 'nun diğer bölümleriyle iletişim kurabilir.

 `CustomVisualizer` öğelerinde `Condition`, `IncludeView`ve `ExcludeView` özniteliklerini kullanabilirsiniz.

 ## <a name="limitations"></a>Sınırlamalar

Natvis özelleştirmeleri sınıflar ve yapılar ile çalışır, ancak Typedefs 'lar değildir.

Natvis, temel türler (örneğin, `int`, `bool`) veya temel tür işaretçiler için Görselleştiriciler desteklemez. Bu senaryoda, bir seçenek, kullanım çalışmanıza uygun [Biçim belirleyicisi](../debugger/format-specifiers-in-cpp.md) kullanmaktır. Örneğin, kodunuzda `double* mydoublearray` kullanıyorsanız, hata ayıklayıcının **izleme** penceresinde, ilk 100 öğesini gösteren ifade `mydoublearray, [100]`gibi bir dizi Biçim belirleyicisi kullanabilirsiniz.
