---
title: C++ nesnelerinin özel görünümlerini oluşturma
description: Natvis çerçevesini kullanarak hata ayıklayıcıda yerel Visual Studio görüntüleme yolunu özelleştirin
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630848"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Natvis çerçevesini kullanarak hata ayıklayıcıda C++ nesnelerinin özel görünümlerini oluşturma

Natvis Visual Studio, yerel türlerin YerelLer ve İzleme pencereleri gibi hata  ayıklayıcı  değişken pencerelerinde ve **DataTips'te görünme yolunu özeller.**  Natvis görselleştirmeleri, hata ayıklama sırasında daha görünür hale gelir.

Natvis, Visual Studio'nin önceki *sürümlerindeki autoexp.dat* dosyasını XML söz dizimi, daha iyi tanılama, sürüm ve birden çok dosya desteğiyle değiştirir.

> [!NOTE]
> Natvis özelleştirmeleri sınıflarla ve yapılarla çalışır, ancak typedef'lerle çalışmaz.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Natvis görselleştirmeleri

Natvis çerçevesini kullanarak, geliştiricilerin hata ayıklama sırasında bunları daha kolay bir şekilde görene kadar, kendi oluşturdukları türler için görselleştirme kuralları oluşturabilirsiniz.

Örneğin, aşağıdaki çizimde özel görselleştirme uygulanmamış bir hata ayıklayıcısı penceresinde [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) türünde bir değişken gösterilir.

![TextBox varsayılan görselleştirmesi](../debugger/media/dbg_natvis_textbox_default.png "TextBox varsayılan görselleştirmesi")

Vurgulanan satır, `Text` sınıfının özelliğini `TextBox` gösterir. Karmaşık sınıf hiyerarşisi bu özelliğin bulunamaz hale gelir. Hata ayıklayıcısı özel dize türünün nasıl yorumlanmasına yardımcı olduğunu bilmiyor, bu nedenle metin kutusunun içinde yer alan dizeyi göreyebilirsiniz.

Natvis `TextBox` özel görselleştirici kuralları uygulandığında da aynı durum değişken penceresinde çok daha basit görünür. Sınıfın önemli üyeleri birlikte görünür ve hata ayıklayıcı özel dize türünün temel dize değerini gösterir.

![Görselleştirici kullanarak TextBox verileri](../debugger/media/dbg_natvis_textbox_visualizer.png "Görselleştirici kullanarak TextBox verileri")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>C++ projelerinde .natvis dosyalarını kullanma

Natvis görselleştirme *kurallarını belirtmek için .natvis* dosyalarını kullanır. *.natvis dosyası,* *.natvis* uzantısına sahip bir XML dosyasıdır. Natvis *şeması% VSINSTALLDIR%\Xml\Schemas\natvis.xsd içinde tanımlanır.*

*.natvis* dosyasının temel yapısı görselleştirme girişlerini temsil eden `Type` bir veya daha fazla öğedir. Her öğenin tam `Type` adı özniteliğinde `Name` belirtilir.

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

Visual Studio *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* klasöründe bazı *.natvis* dosyaları sağlar. Bu dosyalar birçok yaygın tür için görselleştirme kurallarına sahip olur ve yeni türler için görselleştirme yazmak için örnek olarak görev kullanılabilir.

### <a name="add-a-natvis-file-to-a-c-project"></a>C++ projesine .natvis dosyası ekleme

Herhangi bir C++ *projesine .natvis* dosyası ekleme.

**Yeni bir *.natvis dosyası eklemek* için:**

1. öğesinde C++ proje **düğümünü Çözüm Gezgini** yeni öğe **ekle'Project** seçin veya projeye sağ tıklar ve Yeni öğe  >   **Ekle'yi**  >  **seçin.**

1. Yeni Öğe **Ekle iletişim kutusunda,** Visual C++ Yardımcı **Visual C++** görselleştirme dosyası  >    >  **(.natvis) öğesini seçin.**

1. Dosyaya bir ad girin ve Ekle'yi **seçin.**

   Yeni dosya Çözüm Gezgini **dosyasına** eklenir ve belge bölmesinde Visual Studio açılır.

Bu Visual Studio hata ayıklayıcısı C++ projelerine *.natvis* dosyalarını otomatik olarak yükler ve varsayılan olarak, proje derlemesi sırasında *bunları .pdb* dosyasına da dahil eder. Yerleşik uygulamada hata ayıklarsanız, projeniz açık olsa bile hata ayıklayıcı *.pdb* dosyasından *.natvis* dosyasını yükler. *.natvis* dosyasının  *.pdb* dosyasına dahil 1.

***Bir .natvis dosyasını bir* *.pdb'den dışlamak için:***

1. içinde *.natvis* dosyasını **Çözüm Gezgini,** Özellikler simgesini  seçin veya dosyaya sağ tıklar ve Özellikler'i **seçin.**

1. Derlemeden Hariç Tutul'un **yanındaki oku aşağı bırakın ve Evet** 'i **ve** ardından Tamam'ı **seçin.**

>[!NOTE]
>Yürütülebilir projelerde hata ayıklama için çözüm öğelerini kullanarak *.pdb* içinde yer alan *.natvis* dosyalarını ekleyin çünkü kullanılabilir C++ projesi yoktur.

>[!NOTE]
>*Bir .pdb'den yüklenen* Natvis kuralları yalnızca *modüllerde .pdb'nin başvurduğu türler* için geçerlidir. Örneğin, *Module1.pdb adlı* bir tür için Natvis girdisi varsa, yalnızca `Test` `Test`Module1.dll. ** Başka bir modül de adlı bir sınıf `Test` tanımlarsa *Module1.pdb* Natvis girdisi bu sınıf için geçerli değildir.

**VSIX paketi aracılığıyla *bir .natvis* dosyası yüklemek ve kaydetmek için:**

VSIX paketi *.natvis* dosyalarını yükleyebilir ve kaydedebilirsiniz. Nerede yüklendiklerine bak fark etmez, tüm kayıtlı *.natvis* dosyaları hata ayıklama sırasında otomatik olarak yüklenir.

1. *VSIX paketine .natvis* dosyasını dahil edin. Örneğin, aşağıdaki proje dosyası için:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. *.natvis dosyasını* *source.extension.vsixmanifest dosyasına* kaydedin:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a> Natvis dosya konumları

Birden çok proje için geçerli olacak şekilde kullanıcı dizininize veya bir sistem dizinine *.natvis* dosyaları eklemek için kullanabilirsiniz.

*.natvis* dosyaları aşağıdaki sırayla değerlendirilir:

1. Yüklenen projede aynı adı içeren bir dosya yoksa, hata ayıklamakta olduğunuz *bir .pdb'ye* eklenmiş tüm *.natvis* dosyaları.

2. Yüklü bir C++ projesinde veya üst düzey çözümde yer alan *.natvis* dosyaları. Bu grup, sınıf kitaplıkları dahil olmak üzere tüm yüklü C++ projelerini içerir, ancak diğer dillerdeki projeleri içerir.

3. VSIX paketi aracılığıyla yüklenmiş ve kaydedilmiş *.natvis* dosyaları.

::: moniker range="vs-2017"

4. Kullanıcıya özgü Natvis dizini (örneğin, *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Kullanıcıya özgü Natvis dizini (örneğin, *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

5. Sistem genelinde natvis dizini (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Bu dizinde, dosyalarla birlikte yüklenmiş *.natvis* Visual Studio. Yönetici izinlerine sahipseniz bu dizine dosya abilirsiniz.

## <a name="modify-natvis-files-while-debugging"></a>Hata ayıklama sırasında .natvis dosyalarını değiştirme

Projesinde hata ayıklarken IDE'de *bir .natvis* dosyasını değiştirebilirsiniz. Hata ayıklama sırasında dosyanın Visual Studio dosyasını açın, değiştirebilir ve kaydedin. Dosya kaydedildik hemen sonra, İzleme **ve** **YerelLer** pencereleri değişikliği yansıtacak şekilde güncelleştirmesi.

Ayrıca, hata ayıklamakta olduğunuz bir çözüme *.natvis* dosyaları ekleyebilir veya silebilir Visual Studio ilgili görselleştirmeleri ekleyebilir veya kaldırabilirsiniz.

Hata ayıklama sırasında *.pdb* dosyalarına eklenmiş *.natvis* dosyalarını güncelleştiresiniz.

*.natvis dosyasını dosyanın* dışında Visual Studio değişiklikler otomatik olarak etkili olmaz. Hata ayıklayıcı pencerelerini güncelleştirmek için, Hemen penceresinde **.natvisreload** komutunu yeniden **değerlendirebilirsiniz.** Ardından değişiklikler hata ayıklama oturumunu yeniden başlatmadan etkili olur.

.natvis dosyasını daha yeni bir sürüme yükseltmek *için .natvisreload* komutunu da kullanın.  Örneğin, *.natvis* dosyası kaynak denetimine iade olabilir ve başka birinin yaptığı son değişiklikleri almak istiyor olabilir.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> İfadeler ve biçimlendirme
Natvis görselleştirmeleri, görüntülemek üzere veri öğelerini belirtmek için C++ ifadelerini kullanır. Hata ayıklayıcısında Bağlam işleci [(C++)](../debugger/context-operator-cpp.md)içinde açıklanan C++ ifadelerinin iyileştirmelerine ve sınırlamalarına ek olarak, aşağıdakilere dikkat edin:

- Natvis ifadeleri, geçerli yığın çerçevesi değil, görselleştirildi nesnesi bağlamında değerlendirilir. Örneğin, bir Natvis ifadesinde, geçerli işlevde x adlı yerel bir değişken değil, görselleştirilen nesnede x adlı `x` alana başvurur.   Natvis ifadelerinde yerel değişkenlere erişesiniz, ancak genel değişkenlere erişebilirsiniz.

- Natvis ifadeleri işlev değerlendirmesine veya yan etkilere izin vermez. İşlev çağrıları ve atama işleçleri yoksayılır. Hata [ayıklayıcı iç](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) işlevleri yan etkisiz olduğundan, diğer işlev çağrılarını izin verilmiyor olsa bile herhangi bir Natvis ifadesinde serbestçe çağrılabilirsiniz.

- Bir ifadenin nasıl görüntüll olduğunu kontrol etmek için C++ içinde Biçim belirleyicileri konusunda açıklanan biçim [belirleyicilerini kullanabilirsiniz.](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) Giriş, ArrayItems genişletmesinde ifadesi gibi Natvis tarafından dahili olarak kullanılırken biçim `Size` belirleyicileri [yoksayılır.](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)

>[!NOTE]
> natvis belgesi XML olduğundan, ifadeleriniz ve /,büyüktür, küçük veya kaydırma işleçlerini doğrudan kullanamaz. Hem öğe gövdesinde hem de koşul deyimleri içinde bu karakterlerin kaçış karakteri olmalıdır. Örnek:<br>
> \<Item Name="HiByte"\>(byte) (_flags \& gt; \& gt; 24),x\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) == 0"\>"Hiçbiri"\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) != 0"\>"Bazıları"\</Item\>

## <a name="natvis-views"></a>Natvis görünümleri

Türleri farklı şekillerde görüntülemek için farklı Natvis görünümleri tanımlayabilirsiniz. Örneğin, adlı basitleştirilmiş bir görünümü `std::vector` tanımlayan görselleştirmeyi burada ve ardından ve ardından basitleştirilmiş bir şekilde oluşturabilirsiniz. `simple` ve `DisplayString` `ArrayItems` öğeleri varsayılan görünümde ve `simple` görünümde, ve öğeleri ise `[size]` `[capacity]` görünümde `simple` göstermez.

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

İzleme **penceresinde,** alternatif bir görünüm belirtmek için **,view** biçim belirteci kullanın. Basit görünüm **vec,view(simple) olarak görünür:**

![izleme penceresi görünümüyle birlikte](../debugger/media/watch-simpleview.png "izleme penceresi görünümüyle birlikte")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis hataları

Hata ayıklayıcı bir görselleştirme girdisinde hatalarla karşılaştığında bunları yoksayar. Türü ham formunda görüntüler veya başka bir uygun görselleştirme seçer. Natvis tanılamasını kullanarak hata ayıklayıcının bir görselleştirme girdisini neden yoksayarak yoksayarak temel söz dizimi ve ayrıştırma hatalarını görüntülebilirsiniz.

**Natvis tanılamasını açmak için:**

- Araçlar **Seçenekleri**(veya Hata Ayıklama Seçenekleri) altında > Hata Ayıklama Çıkış Penceresi, Natvis tanılama iletileri  >     >     >   **(yalnızca C++)**  değerini **Hata**, Uyarı veya Ayrıntılı olarak ayarlayın ve tamam'ı **seçin.**

Hatalar Çıkış **penceresinde** görüntülenir.

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Natvis söz dizimi başvurusu

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> AutoVisualizer öğesi
öğesi `AutoVisualizer`  . *natvis* dosyasının kök düğümü ve namespace özniteliğini `xmlns:` içerir.

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
`Name`öğesinin özniteliği, şablonlu sınıf adları için kullanılan joker karakter olarak `Type` bir yıldız işareti kabul `*` eder.

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

İsteğe `Condition` bağlı özniteliği birçok görselleştirme öğe için kullanılabilir ve bir görselleştirme kuralının ne zaman kullanılacazı belirtir. Koşul özniteliğinin içindeki ifade olarak `false` çözümleyicisi olursa görselleştirme kuralı geçerli olmaz. değerlendirmesi olarak değerlendirilirse `true` veya özniteliği yoksa görselleştirme `Condition` uygulanır. Görselleştirme girişlerinde if-else mantığı için bu özniteliği kullanabilirsiniz.

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

Farklı modüller tarafından kullanılan ortak bir üst bilgi dosyası bir tür tanımlarsa, sürüme sahip görselleştirme yalnızca tür belirtilen modül sürümünde olduğunda görünür.

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

özniteliği, `Name` *filename.ext biçimindedir;* örneğin, *hello.exe* veya *some.dll.* Yol adlarına izin verilmez.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a> DisplayString öğesi
`DisplayString`öğesi, bir değişkenin değeri olarak göstermek için bir dize belirtir. İfadelerle karışık rastgele dizeleri kabul eder. Küme ayraçları içindeki her şey bir ifade olarak yorumlanır. Örneğin, aşağıdaki `DisplayString` girdi:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Türüne sahip değişkenlerin `CPoint` şu çizimde gösterildiği gibi görüntüleniyor olduğu anlamına gelir:

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

Hata ayıklama sırasında değişkenin yanındaki büyüteç simgesini ve ardından **Metin** Görselleştirici'yi **seçerek** ilgili m_pszData görüntüebilirsiniz.

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

![Öğe öğesi genişletmesi ile CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "Öğe öğesi genişletmesi ile CRect")

Hata ayıklayıcısı, ve öğelerinde belirtilen ifadeleri değerlendirir ve değerleri `Width` `Height` değişken penceresinin **Değer** sütununda gösterir.

Hata ayıklayıcısı her özel genişletme **için [Ham Görünüm]** düğümünü otomatik olarak oluşturur. Önceki ekran görüntüsünde, nesnenin varsayılan ham görünümünün Natvis görselleştirmelerinden nasıl farklı olduğunu göstermek için **genişletilmiş [Ham Görünüm]** düğümü görüntülenir. Varsayılan genişletme, temel sınıf için bir alt ağaç oluşturur ve temel sınıfın tüm veri üyelerini alt sınıf olarak listeler.

> [!NOTE]
> Öğe öğesinin ifadesi karmaşık bir türü gösteriyorsa, **Öğe düğümünün** kendisi genişletilebilir.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> ArrayItems genişletmesi
Hata ayıklayıcısının türü Visual Studio yorumlaması ve tek tek öğelerini görüntülemesi `ArrayItems` için düğümünü kullanın. için görselleştirme `std::vector` iyi bir örnektir:

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

![ArrayItems genişletmesi kullanan std::vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "ArrayItems genişletmesi kullanan std::vector")

Düğümde `ArrayItems` şunların olması gerekir:

- Hata ayıklayıcının dizinin uzunluğunu anlarken bir ifade `Size` (tamsayı olarak değerlendirilmesi gerekir).
- İlk `ValuePointer` öğeye işaret eden bir ifade (bu, değil bir öğe türünün işaretçisi olması `void*` gerekir).

Alt sınır dizisinin varsayılan değeri 0'dır. Değeri geçersiz kılmak için bir öğesi `LowerBound` kullanın. Bu dosyalarla birlikte gönderilen *.natvis* Visual Studio örnekleri vardır.

>[!NOTE]
>Türün kendisi (örneğin) bu işleçe izin vermese bile, işleci, kullanan tek boyutlu dizi görselleştirmeleriyle birlikte `[]` `vector[i]` `ArrayItems` `CATLArray` kullanabilirsiniz.

Çok boyutlu diziler de belirtsiniz. Bu durumda, hata ayıklayıcısı alt öğeleri düzgün şekilde görüntülemek için biraz daha fazla bilgi gerektirir:

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

![ArrayItems genişletmesi ile iki boyutlu dizi](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "ArrayItems genişletmesi ile iki boyutlu dizi")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> IndexListItems genişletmesi

Genişletmeyi `ArrayItems` yalnızca dizi öğelerinin belleğe bitişik olarak sıra olması gerekir. Hata ayıklayıcısı yalnızca işaretçisini artırarak bir sonraki öğeye gider. Dizini değer düğümüne göre işlemeniz gerekirse düğümleri `IndexListItems` kullanın. Düğüme sahip görselleştirme şu `IndexListItems` şekildedir:

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

ve arasındaki tek fark, tam ifadeyi örtülü parametresiyle i th öğesine `ArrayItems` `IndexListItems` `ValueNode` bekler.<sup></sup> `$i`

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

 ![otomatik&#95;ptr&#60;vektör&#60;int&#62;&#62; genişletme](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Varsayılan genişletme")

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
 öğesi `ExpandedItem` hiyerarşileri ortadan kaldırarak verilerin düz bir görünümünü sağlarken, `Synthetic` düğüm tam tersini yapar. İfadenin sonucu olmayan bir yapay alt öğe oluşturmanıza olanak sağlar. Yapay öğenin kendi alt öğeleri olabilir. Aşağıdaki örnekte, türüne göre `Concurrency::array` görselleştirme, `Synthetic` kullanıcıya bir tanılama iletisi göstermek için bir düğüm kullanır:

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

 ![Concurrency::Array ve Yapay öğe genişletmesi](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency::Array ve Yapay öğe genişletmesi")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a> HResult öğesi
 öğesi, `HResult` hata ayıklayıcı pencerelerde **HRESULT için gösterilen** bilgileri özelleştirmenize olanak sağlar. `HRValue`öğesi, özelleştirecek **HRESULT'un** 32 bit değerini içermesi gerekir. öğesi, `HRDescription` hata ayıklayıcısı penceresinde gösterilen bilgileri içerir.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a> UIVisualizer öğesi
Bir `UIVisualizer` öğe, bir grafik görselleştirici eklentiyi hata ayıklayıcıya kaydettirmektedir. Grafik görselleştirici, veri türüyle tutarlı bir şekilde değişken veya nesne gösteren bir iletişim kutusu veya başka bir arabirim oluşturur. Görselleştirici eklentisi [VSPackage](../extensibility/internals/vspackages.md)olarak yazmalı ve hata ayıklayıcının tükettiği bir hizmeti açığa çıkarmalı. *.natvis* dosyası eklentinin adı, ortaya çıkarıla hizmetin GUID'si ve görselleştirileyenin türleri gibi kayıt bilgilerini içerir.

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

- özniteliği, hata ayıklayıcıda büyüteç simgesinin yanındaki açılan ekranda görüntülemek `MenuName` için bir görselleştirici adı tanımlar. Örnek:

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

Xml Natvis tanımı yerine özel görselleştirici yazmak çok daha fazla iştir, ancak Natvis'in ne yaptığı veya desteklemesi konusunda kısıtlamalara sahip değilsiniz. Özel görselleştiriciler, hata ayıklama işlemini sorgulandırarak değiştirebilir veya hata ayıklayıcının diğer bölümleriyle iletişim kurarak hata ayıklayıcı genişletilebilirlik API'lerinin Visual Studio.

 Öğelerde `Condition` , `IncludeView` ve `ExcludeView` özniteliklerini `CustomVisualizer` kullanabilirsiniz.

## <a name="limitations"></a>Sınırlamalar

Natvis özelleştirmeleri sınıflarla ve yapılarla çalışır, ancak typedef'lerle çalışmaz.

Natvis, ilkel türler (örneğin, `int` , ) veya ilkel `bool` türlerin işaretçileri için görselleştiricileri desteklemez. Bu senaryoda, bir seçenek kullanım durumuna [uygun biçim belirleyiciyi](../debugger/format-specifiers-in-cpp.md) kullanmaktır. Örneğin, kodunda kullanıyorsanız, hata ayıklayıcının İzleme penceresinde ilk 100 öğeyi gösteren ifadesi gibi bir dizi biçimi belirleyicisi `double* mydoublearray`  `mydoublearray, [100]` kullanabilirsiniz.
