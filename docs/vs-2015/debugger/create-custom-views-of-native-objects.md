---
title: Yerel nesnelerin özel görünümlerini oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a510c522723cf991c7a3fff21542a069a3de000a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299491"
---
# <a name="create-custom-views-of-native-objects"></a>Yerel Nesnelerin Özel Görünümlerini Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Natvis çerçevesi, Visual Studio 'Nun hata ayıklayıcı değişken pencerelerinde yerel türleri görüntüleme şeklini özelleştirmenizi sağlar (örneğin, **Watch**, **Yereller**ve **veri ipuçları** pencereleri).  

 Natvis, Visual Studio 'nun önceki sürümlerinde kullanılan ve XML sözdizimi, daha iyi tanılama, sürüm oluşturma ve birden çok dosya desteği sunan bir **oto exp. dat** dosyasının yerini alır.  

> [!NOTE]
> Şu durumlarda Natvis çerçevesini görselleştirmeler için kullanamazsınız:  
> 
> - Hata ayıklayıcı türü C++ **karma**olarak ayarlanmış bir Windows Masaüstü projesinde hata ayıklaması yapıyorsanız.  
>   - Yönetilen Uyumluluk modundaki bir Windows masaüstü uygulamasında karışık modda hata ayıklama yapıyorsunuz (**Araçlar/Seçenekler/hata ayıklama/genel/yönetilen uyumluluk modunu kullan**).  
>   - Yerel uyumluluk modundaki bir Windows masaüstü uygulamasında hata ayıklaması yapıyorsanız (**Araçlar/Seçenekler/hata ayıklama/genel/yerel uyumluluk modunu kullan**).  

## <a name="BKMK_Why_create_visualizations_"></a>Neden Natvis görselleştirmeleri oluşturulsun?  
 , Geliştiricilerin hata ayıklama sırasında kolayca görebilmesi için oluşturduğunuz türler için görselleştirme kuralları oluşturmak üzere Natvis çerçevesini kullanabilirsiniz.  

 Örneğin, aşağıdaki görüntüde özel görselleştirmeler uygulanmadan hata ayıklayıcıda görüntülenen [Windows:: UI:: XAML:: Controls:: TextBox](https://go.microsoft.com/fwlink/?LinkId=258422) türünde bir değişken gösterilmektedir.  

 ![TextBox varsayılan görselleştirmesi](../debugger/media/dbg-natvis-textbox-default.png "DBG_NATVIS_TextBox_Default")  

 Vurgulanan satır, `TextBox` sınıfının `Text` özelliğini gösterir. Karmaşık sınıf hiyerarşisi bu değeri bulmayı zorlaştırır; Üstelik, hata ayıklayıcı nesne tarafından kullanılan özel dize türünü nasıl yorumlayabileceğinizi bilmez, bu nedenle TextBox içinde tutulan dizeyi göremezsiniz.  

 Aynı `TextBox` özel görselleştirme kuralları uygulandığında değişken penceresini çok daha basit bir şekilde inceler. Sınıfının önemli üyeleri birlikte görüntülenebilir ve hata ayıklayıcı özel dize türünün temel alınan dize değerini gösterir.  

 ![Görselleştirici kullanarak metin kutusu verileri](../debugger/media/dbg-natvis-textbox-visualizer.png "DBG_NATVIS_TextBox_Visualizer")  

## <a name="BKMK_Using_Natvis_files"></a>Natvis dosyalarını kullanma  
 . natvis dosyaları. natvis uzantılı XML dosyalarıdır. Şema **%VSInstallDir%\Xml\Schemas\natvis.exe**içinde tanımlanmıştır.  

 Bir. natvis dosyasının temel yapısı bir veya daha fazla `Type` öğesidir; burada her `Type` öğesi, `Name` özniteliğinde tam nitelikli adı belirtilen bir tür için bir görselleştirme girdisini temsil eder.  

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

 Visual Studio, **%VSInstallDir%\common7\packages\debugger\visualıcılar** klasöründe bazı. natvis dosyaları sağlar. Bu dosyalar birçok ortak türün görselleştirme kurallarını içerir ve yeni türler için görselleştirmeler yazarken örnek olarak işlev görebilir.  

## <a name="adding-natvis-files-to-your-projects"></a>. Natvis dosyalarını projelerinize ekleme  
 Herhangi bir C++ projeye. natvis dosyası ekleyebilirsiniz.  

 Açık C++ bir proje ile yeni bir. natvis dosyası eklemek için, **Çözüm Gezgini**proje düğümünü seçin ve **Ekle/yeni C++ öğe/görsel/yardımcı/hata ayıklayıcı görselleştirme dosyası (. natvis) öğesine**tıklayın. Hata ayıklayıcı, Natvis dosyalarını C++ projeden otomatik olarak yükler. Varsayılan olarak, projenizdeki Natvis dosyaları, proje tarafından oluşturulan. pdb dosyasına da eklenir. Yani bu proje tarafından oluşturulan ikilide hata ayıklaması yaparsanız, proje açık olmasa bile hata ayıklayıcı,. pdb dosyasından Natvis dosyasını yükler. . Natvis dosyasının. pdb dosyasına dahil edilmesini istemiyorsanız, **Çözüm Gezgini**. natvis dosyasına sağ tıklayın ve **yapılandırma özellikleri** penceresinde derleme dışında **Evet**olarak **dışarıda bırakılır** .  

 Visual Studio 'Yu kullanarak Natvis dosyalarını düzenlemeniz önerilir. hata ayıklama sırasında yaptığınız tüm değişiklikler, dosyayı kaydettiğinizde bu işlem otomatik olarak etkili olur. IntelliSense 'den geliştirilmiş bir düzen deneyimi de alırsınız.  

 Bir. pdb 'den yüklenen Natvis dosyaları yalnızca, pdb 'nin başvurduğu modüldeki türler için geçerlidir. Örneğin, Module1. pdb `Test`adlı bir tür için bir giriş tanımlıyorsa, bu giriş yalnızca Module1. dll içindeki **Test** sınıfına uygulanır. Başka bir modül **Test**adlı bir sınıfı da tanımlıyorsa, Module1. pdb 'nin Natvis girdisi kendisine uygulanmaz.  

## <a name="BKMK_natvis_location"></a>. Natvis dosyalarını dağıtma  
 . Natvis dosyanız yalnızca bir Visual Studio projesinde oluşturmakta olduğunuz türlere geçerliyse, herhangi bir şey yapmanız gerekmez; . natvis,. pdb içine dahil edilmiştir. Ancak,. Natvis dosyalarını Kullanıcı dizininize veya birden çok projeye uygulanmasını istiyorsanız bir sistem dizinine ekleyebilirsiniz.  

 . Natvis dosyalarının değerlendirilme sırası aşağıdaki gibidir:  

1. bir. pdb dosyasına katıştırılmış. natvis dosyaları, hata ayıklaması yaptığınız (yüklenen projede aynı ada sahip bir dosya mevcut değilse)  

2. yüklü C++ projelerin parçası olan. natvis dosyaları veya üst düzey bir çözüm öğesi. Bu, sınıf kitaplıkları C++ dahil olmak üzere tüm yüklü projeleri içerir, ancak diğer dillerin projelerini içermez (örn. bir C# projeden. natvis dosyası yüklenemez). Yürütülebilir projelerde, kullanılabilir proje bulunmadığından C++ , bir. pdb dosyasında bulunmayan. Natvis dosyalarını barındırmak için çözüm öğelerini kullanmanız gerekir.  

3. Kullanıcıya özgü Natvis dizini ( **%USERPROFILE%\My, Studio 2015 \ Görselleştiriciler**  

4. Sistem genelindeki Natvis dizini ( **%VSInstallDir%\common7\packages\debugger\görselleştiriciler**). Bu, Visual Studio ile yüklenen. natvis dosyalarının kopyalandığı yerdir. Yönetici izinleriniz varsa, bu dizine diğer dosyaları da ekleyebilirsiniz.  

## <a name="modifying-natvis-files-while-debugging"></a>Hata ayıklarken. Natvis dosyalarını değiştirme  
 İçindeki bir. natvis dosyasını, dahil olduğu projede hata ayıklarken IDE 'de değiştirebilirsiniz. Dosyayı IDE 'de açın (hata ayıklamada kullandığınız Visual Studio örneğini kullanarak), değiştirin ve kaydedin. Dosya kaydedildiği anda, **Watch** ve **Locals** pencerelerinin değişikliği yansıtacak şekilde güncelleştirilmeleri gerekir. . Natvis dosyasını IDE dışında değiştirirseniz, değişiklikler otomatik olarak etkili olmaz. Windows 'u güncelleştirmek için, **izleme** penceresindeki **. natvisreload** komutunu değerlendirebilirsiniz. Bu, değişikliklerin hata ayıklama oturumunu yeniden başlatmadan etkili olmasına neden olur.  

 Ayrıca, hata ayıklaması yaptığınız bir çözüme. natvis dosyaları ekleyebilir veya silebilirsiniz ve Visual Studio ilgili görselleştirmeleri ekler veya kaldırır.  

 Bir. pdb dosyasına katıştırılmışsa hata ayıklarken bir. natvis dosyasını değiştiremezsiniz.  

 Natvis dosyasını daha yeni bir sürüme yükseltirken **. natvisreload** komutunu kullanın (örneğin, kaynak denetimine işaretlenmişse ve dosyada başka birinin yaptığı en son değişiklikleri almak istiyorsanız). Visual Studio XML düzenleyicisini kullanarak Natvis dosyalarını düzenlemeniz önerilir.  

## <a name="BKMK_Expressions_and_formatting"></a>İfadeler ve biçimlendirme  
 Natvis görselleştirmeleri C++ görüntülenecek veri öğelerini belirtmek için ifadeleri kullanır. [Bağlam operatörü (C++)](../debugger/context-operator-cpp.md)içinde açıklanan hata ayıklayıcıdaki C++ deyimlerin ve sınırlamalara ek olarak, aşağıdaki farklılıklara dikkat etmeniz gerekir:  

- Natvis ifadeleri, geçerli yığın çerçevesini değil görselleştirilen nesne bağlamında değerlendirilir. Örneğin, bir Natvis ifadesinde `x` kullanırsanız, bu, şu anda yürütülmekte olan işlevde `x` adlı yerel bir değişkene değil, görselleştirilebilen nesnedeki `x` adlı alana başvurur. Küresel değişkenlere erişebilseniz de, Natvis ifadelerinde yerel değişkenlere erişemezsiniz.  

- Natvis ifadeleri işlev değerlendirmesi veya yan etkilere izin vermez. Bu, işlev çağrılarının ve atama işleçlerinin yoksayıldığı anlamına gelir. [Hata ayıklayıcı iç işlevleri](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) yan etkilerden farklı olduğundan, diğer işlev çağrılarına izin verilmese de, her bir natvis ifadesinden serbestçe çağrılabilir.  

  Bir ifadenin bir değişken penceresinde nasıl görüntülendiğini denetlemek için [, konusunun biçim C++ Belirticilerinin](../debugger/format-specifiers-in-cpp.md) [Biçim](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) belirticileri bölümünde açıklanan biçim belirticilerini kullanabilirsiniz. Dizi öğeleri genişletmesinde `Size` ifadesi gibi, sanallaştırma girişi Natvis tarafından dahili olarak kullanıldığında biçim Belirticilerinin yoksayıldığını unutmayın.  

## <a name="natvis-views"></a>Natvis görünümleri  
 Natvis görünümleri, herhangi bir türü birden fazla şekilde görmenizi sağlar. Örneğin, **basit** adlı bir görünümü tanımlayabilir ve bu sayede bir türün basitleştirilmiş bir görünümünü elde edebilirsiniz. Örneğin, `std::vector`görselleştirmesi aşağıda verilmiştir:  

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

 `DisplayString` ve `ArrayItems` öğeleri varsayılan görünümde ve basit görünümde kullanılır, ancak `[size]` ve `[capacity]` öğeleri basit görünümden hariç tutulur. Alternatif bir görünüm belirtmek için **, görünüm Biçim belirleyicisi ' ni** kullanabilirsiniz. **İzle** penceresinde, basit görünümü VEC olarak belirtirsiniz **, görüntüleme (basit)** :  

 ![Basit görünümle izleme penceresi](../debugger/media/watch-simpleview.png "İzleme-SimpleView")  

## <a name="BKMK_Diagnosing_Natvis_errors"></a>Natvis hatalarını tanılama  
 , Sözdizimi ve ayrıştırma hatalarını gidermek için Natvis tanılamayı kullanabilirsiniz. Hata ayıklayıcı bir görselleştirme girişinde hata ile karşılaştığında, hataları yoksayar ve türü ham biçiminde görüntüler ya da uygun bir görselleştirmeyi seçer. Belirli bir görselleştirme girişinin neden yoksayıldığını anlamak ve temeldeki hataların ne olduğunu görmek için, Natvis tanılama **araçları/seçenekler/hata ayıklama/çıkış penceresi/Natvis tanılama iletileri (C++ yalnızca)** seçeneğini etkinleştirebilirsiniz. Hatalar **Çıkış** penceresinde görüntülenir.  

## <a name="BKMK_Syntax_reference"></a>Natvis sözdizimi başvurusu  

### <a name="BKMK_AutoVisualizer"></a>Oto görselleştiricisi öğesi  
 `AutoVisualizer` öğesi,. natvis dosyasının kök düğümüdür ve ad alanı `xmlns:` özniteliğini içerir.  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

### <a name="BKMK_Type"></a>Type öğesi  
 Temel bir tür şöyle görünür:  

```xml  
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  

```  

 Şunları belirtir:  

1. Bu görselleştirmenin kullanılması gereken tür (`Type Name` özniteliği).  

2. Bu türdeki bir nesnenin değeri şöyle görünmelidir (`DisplayString` öğesi).  

3. Kullanıcı onu bir değişken penceresinde (`Expand` düğümü) genişlediğinde, türün üyeleri şöyle görünmelidir.  

   **Şablonlu sınıflar** `Type` öğesinin `Name` özniteliği, şablonlu sınıf adları için kullanılabilen bir joker karakter olarak bir yıldız işareti `*` kabul eder:  

```xml  
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  

```  

 Bu örnekte, nesnenin `CAtlArray<int>` mı yoksa `CAtlArray<float>`mi olduğunu aynı görselleştirme kullanılacaktır. Bir `CAtlArray<float>` için belirli bir görselleştirme girişi varsa, genel bir üzerinden önceliklidir.  

 Şablon parametrelerine, $T 1, $T 2 vb. makrolar kullanılarak görselleştirme girişinde başvurulabileceğini unutmayın. Bu makroların örneklerini bulmak için bkz. Visual Studio ile birlikte gelen. natvis dosyaları.  

#### <a name="BKMK_Visualizer_type_matching"></a>Görselleştiricisi türü eşleşiyor  
 Bir görselleştirme girdisi doğrulanamazsa, bir sonraki kullanılabilir görselleştirme kullanılır.  

#### <a name="inheritable-attribute"></a>Inheritable özniteliği  
 Bir görselleştirmenin yalnızca bir temel tür için mi yoksa temel türe ve tüm türetilmiş türlerin isteğe bağlı `Inheritable` özniteliğiyle mi geçerli olduğunu belirtebilirsiniz. Aşağıdaki, görselleştirme yalnızca `BaseClass` türü için geçerlidir:  

```xml  
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

 `Inheritable` varsayılan değeri `true`.  

#### <a name="priority-attribute"></a>Priority özniteliği  
 `Priority` özniteliği, bir tanım ayrıştıramazsa alternatif tanımlarının kullanılacağı sırayı belirtir. `Priority` olası değerleri şunlardır: `Low`, `MediumLow`,`Medium`, `MediumHigh`ve `High`, varsayılan değer `Medium`.  

 Priority özniteliği yalnızca aynı. natvis dosyasındaki önceliklerin ayırt edilmesini sağlamak için kullanılmalıdır, farklı dosyalar arasında değil.  

 Aşağıdaki örnekte, ilk olarak 2015 STL ile eşleşen girişi ayrıştıracağız ve bu, ayrıştıramazsa, STL 'nin 2013 sürümü için alternatif girişi kullanacağız:  

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

#### <a name="BKMK_Versioning"></a>Sürüm öğesi  
 Ad çakışmalarının en aza indirilebilmesi ve türlerin farklı sürümleri için farklı görselleştirmeler kullanılabilmesi için, görselleştirmeleri belirli modüller ve sürümleri için kapsamını atamak üzere `Version` öğesini kullanın. Örneğin:  

```xml  
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

 Bu örnekte, görselleştirme yalnızca 1,0 sürümünden 1,5 ' de bulunan `Windows.UI.Xaml.dll` bulunan `DirectUI::Border` türü için geçerlidir. Sürüm öğelerinin kapsamını, görselleştirme girişini belirli bir modüle ve sürüme ekleme ve yanlışlıkla uyuşmazlıkları azalttığını unutmayın, ancak bir tür farklı modüller tarafından kullanılan ortak bir üst bilgi dosyasında tanımlanmışsa, sürümlük görselleştirmesi şu durumlarda uygulanmaz tür, belirtilen modülde değil.  

#### <a name="optional-attribute"></a>İsteğe bağlı öznitelik  
 `Optional` özniteliği herhangi bir düğümde görünebilir. İsteğe bağlı bir düğümün içindeki herhangi bir alt ifade ayrıştırılamazsa bu düğüm yok sayılır, ancak Type öğesinin geri kalanı hala geçerlidir. Aşağıdaki türde `[State]` isteğe bağlı değildir, ancak `[Exception]` isteğe bağlıdır.  Bu, `MyNamespace::MyClass` _`M_exceptionHolder`adlı bir alan içeriyorsa, hala `[State]` düğüm ve `[Exception]` düğümüne sahip olacağını, ancak `_M_exceptionHolder` eksikse yalnızca `[State]` düğümünü görürsünüz.  

```xml  
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

### <a name="BKMK_Condition_attribute"></a>Condition özniteliği  
 İsteğe bağlı `Condition` özniteliği birçok görselleştirme öğesi için kullanılabilir ve bir görselleştirme kuralının ne zaman kullanılması gerektiğini belirtir. Koşul özniteliği içindeki ifade `false`olarak çözümlenirse, öğe tarafından belirtilen görselleştirme kuralı uygulanmaz. True olarak değerlendirilirse veya `Condition` özniteliği yoksa, görselleştirme kuralı türe uygulanır. Görselleştirme girişlerinde `if-else` mantığı için bu özniteliği kullanabilirsiniz. Örneğin, aşağıdaki görselleştirmede akıllı işaretçi türü için iki `DisplayString` öğesi vardır:  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 `_Myptr` üyesi `null`olduğunda, ilk `DisplayString` öğenin koşulu `true`olarak çözümlendiğinden form görüntülenir. `_Myptr` üyesi `null`olmadığında, koşul `false`olarak değerlendirilir ve ikinci `DisplayString` öğesi görüntülenir.  

### <a name="includeview-and-excludeview-attributes"></a>IncludeView ve ExcludeView öznitelikleri  
 Bu öznitelikler, farklı görünümlerde görüntülenecek veya görüntülenmeyen öğeleri belirtir. Örneğin, `std::vector`Natvis belirtimi verildiğinde:  

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

 Basit görünüm, [size] ve [Capacity] öğelerini basit görünümde görüntülemez. `ExcludeView`yerine `IncludeView="simple"` kullandığımızda, `[size]` ve `[capacity]` öğeleri varsayılan görünüm yerine basit görünümde gösterilir.  

 `IncludeView` ve `ExcludeView` özniteliklerini, türler üzerinde ve tek tek üyelere kullanabilirsiniz.  

### <a name="BKMK_DisplayString"></a>DisplayString  
 Bir `DisplayString` öğesi, değişkenin değeri olarak gösterilecek dizeyi belirtir. İfadelerle karışık rastgele dizeler kabul eder. Küme ayraçları içindeki her şey bir ifade olarak yorumlanır. Örneğin, şöyle bir `DisplayString` girişi:  

```xml  
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  

```  

 `CPoint` türü değişkenlerin şöyle görüntüleneceği anlamına gelir:  

 ![DisplayString öğesi kullanma](../debugger/media/dbg-natvis-cpoint-displaystring.png "DBG_NATVIS_CPoint_DisplayString")  

 `DisplayString` ifadesinde, `CPoint`üyeleri olan `x` ve `y`, küme ayraçları içinde ve değerleri değerlendirilir. İfade ayrıca çift küme ayraçları (`{{` veya `}}`) kullanarak bir küme ayracını nasıl atkullanabileceğinizi gösterir.  

> [!NOTE]
> `DisplayString` öğesi, rastgele dizeleri ve küme ayracı sözdizimini kabul eden tek öğedir. Diğer tüm Görselleştirme öğeleri yalnızca hata ayıklayıcı tarafından değerlendirilen ifadeleri kabul eder.  

### <a name="BKMK_StringView"></a>StringView  
 `StringView` öğesi, değeri yerleşik metin Görselleştirici öğesine gönderilecek olan ifadeyi tanımlar. Örneğin, `ATL::CStringT` türü için aşağıdaki görselleştirmeye sahip olduğunuzu varsayalım:  

```xml  
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>  

```  

 `CStringT` nesnesi şöyle görünür:  

 ![CStringT DisplayString öğesi](../debugger/media/dbg-natvis-displaystring-cstringt.png "DBG_NATVIS_DisplayString_CStringT")  

 Görselleştirme aşağıdaki gibi bir değişken penceresinde bir `CStringT` nesnesi görüntüler:  

 `StringView` bir öğesi eklemek, bu değerin bir metin görselleştirmesi tarafından görüntülenebileceğini hata ayıklayıcıya gösterir:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

 Büyüteç simgesinin aşağıdaki değerin yanında göründüğünü unutmayın. Simgenin seçilmesi, `m_pszData` işaret eden dizeyi görüntüleyen metin Görselleştirici başlatacaktır.  

 ![StringView görselleştiricisi ile CStringT verileri](../debugger/media/dbg-natvis-stringview-cstringt.png "DBG_NATVIS_StringView_CStringT")  

> [!NOTE]
> `{m_pszData,su}` ifade, değeri bir Unicode dize C++ olarak göstermek için `su` bir Biçim belirleyicisi içerir. Daha fazla bilgi için [içindeki C++ biçim belirticilerine](../debugger/format-specifiers-in-cpp.md) bakın.  

### <a name="BKMK_Expand"></a>Genişletin  
 `Expand` düğümü, Kullanıcı onu değişken Windows 'ta genişlettiğinde görselleştirilen türün alt öğelerini özelleştirmek için kullanılır. Alt öğeleri tanımlayan alt düğümlerin listesini kabul eder.  

 `Expand` düğümü isteğe bağlıdır.  

- Bir görselleştirme girişinde `Expand` düğümü belirtilmemişse, Visual Studio 'nun varsayılan genişletme kuralları kullanılır.  

- Bir `Expand` düğümü altında alt düğüm olmadan belirtilmişse, tür hata ayıklayıcı penceresinde Genişletilebilir olmayacaktır.  

#### <a name="BKMK_Item_expansion"></a>Öğe genişletmesi  
 `Item` öğesi, bir `Expand` düğümünde kullanılacak en temel ve en yaygın öğedir. `Item` tek bir alt öğe tanımlıyor. Örneğin, `top`, `left`, `right`ve `bottom` alanları ve aşağıdaki görselleştirme girişi ile bir `CRect` sınıfınız olduğunu varsayalım:  

```xml  
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  

```  

 `CRect` türü şöyle görünür:  

 ![Öğe öğesi genişlemesiyle CRect](../debugger/media/dbg-natvis-expand-item-crect1.png "DBG_NATVIS_Expand_Item_CRect1")  

 `Width` ve `Height` öğelerinde belirtilen ifadeler değerlendirilir ve değer sütununda gösterilir. `[Raw View]` düğümü, özel bir genişletme kullanıldığında hata ayıklayıcı tarafından otomatik olarak oluşturulur. Nesnenin ham görünümünün görselleştirmeden farklı olduğunu göstermek için yukarıdaki ekran görüntüsünde genişletilir. Visual Studio varsayılan genişletmesi, temel sınıf için bir alt ağaç oluşturur ve temel sınıfın tüm veri üyelerini alt öğe olarak listeler.  

> [!NOTE]
> Öğe öğesinin ifadesi karmaşık bir türe işaret ediyorsa, `Item` düğümünün kendisi Genişletilebilir olur.  

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

 ![std:: ArrayItems genişletmesi kullanan vektör](../debugger/media/dbg-natvis-expand-arrayitems-stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  

 En azından, `ArrayItems` düğümü şunları içermelidir:  

1. Hata ayıklayıcının dizi uzunluğunu anlaması için bir `Size` ifadesi (bir tamsayı olarak değerlendirilmesi gerekir)  

2. İlk öğeyi işaret etmesi gereken bir `ValuePointer` ifadesi (`void*`olmayan bir öğe türünün işaretçisi olması gerekir).  

   Dizi alt sınırının varsayılan değeri 0 ' dır. Değer bir `LowerBound` öğesi kullanılarak geçersiz kılınabilir (örnekler, Visual Studio ile birlikte gelen. natvis dosyalarında bulunabilir).  

   Artık `[]` işlecini `ArrayItems` genişlemesiyle kullanabilirsiniz, örneğin `vector[i]`. [] İşleci, türün kendisi bu işlece izin vermediği halde (örneğin, `CATLArray`) `ArrayItems` veya `IndexListItems`kullanan tek boyutlu bir dizinin herhangi bir görselleştirmesinde kullanılabilir.  

   Çok boyutlu diziler de belirtilebilir. Hata ayıklayıcı, bu durumda alt öğeleri düzgün şekilde göstermek için biraz daha daha fazla bilgiye ihtiyaç duyuyor:  

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

 `Direction`, dizinin satır başına mi yoksa birincil sütun mi olduğunu belirtir. `Rank` dizinin derecesini belirtir. `Size` öğesi, bu boyuttaki dizinin uzunluğunu bulmak için boyut diziniyle birlikte bulunan örtük `$i` parametresini kabul eder. Örneğin, önceki örnekte, ifadenin üzerindeki `_M_extent.M_base[0]` 0. boyutun uzunluğuna, 1 ' i `_M_extent._M_base[1]` ve bu şekilde devam eder.  

 İki boyutlu bir nesne hata ayıklayıcıda nasıl görünür `Concurrency::array` aşağıda verilmiştir:  

 ![ArrayItems genişletmesi olan iki boyutlu dizi](../debugger/media/dbg-natvis-expand-arrayitems-2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  

#### <a name="BKMK_IndexListItems_expansion"></a>IndexListItems genişletmesi  
 `ArrayItems` genişletmeyi, yalnızca dizi öğeleri bellekte bitişik olarak yerleştirilse kullanabilirsiniz. Hata ayıklayıcı, yalnızca işaretçisini geçerli öğe ile arttırarak bir sonraki öğeye alınır. Dizini değer düğümüne göre değiştirmeniz gereken durumları desteklemek için `IndexListItems` düğümler kullanılabilir. `IndexListItems` düğüm kullanan bir görselleştirme aşağıda verilmiştir:  

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

 Artık `[]` işlecini `IndexListItems` genişlemesiyle kullanabilirsiniz, örneğin `vector[i]`. `[]` işleci, türün kendisi bu işlece izin vermediği halde, `ArrayItems` veya `IndexListItems`kullanan tek boyutlu bir dizinin herhangi bir görselleştirmesinde kullanılabilir (örneğin, `CATLArray`).  

 `ArrayItems` ve `IndexListItems` arasındaki tek fark, `ValueNode` örtük `$i`<sup>parametresiyle i.</sup> öğesi için tam ifadeyi bekledir.  

#### <a name="BKMK_LinkedListItems_expansion"></a>LinkedListItems genişletmesi  
 Görselleştirilmiş tür bağlantılı bir listeyi temsil ediyorsa, hata ayıklayıcı alt öğelerini bir `LinkedListItems` düğümü kullanarak görüntüleyebilir. Bu özelliği kullanarak `CAtlList` türünün görselleştirmesi aşağıda verilmiştir:  

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

- `NextPointer` ve `ValueNode` ifadeleri, ana liste türü değil, bağlantılı liste düğümü öğesi bağlamında değerlendirilir. Yukarıdaki örnekte `CAtlList`, bağlantılı listenin bir düğümünü temsil eden bir `CNode` sınıfına (`atlcoll.h`içinde bulunur) sahiptir. `m_pNext` ve `m_element`, bu `CNode` sınıfının alanları `CAtlList` sınıfı değil.  

- `ValueNode` boş bırakılabilir veya bağlantılı liste düğümünün kendine başvurabileceği `this` olabilir.  

#### <a name="customlistitems-expansion"></a>CustomListItems genişletmesi  
 `CustomListItems` genişletmesi, Hashtable gibi bir veri yapısına geçiş yapmak için özel mantık yazmanızı sağlar. Değerlendirmek için ihtiyaç duyduğunuz her şeyin ifadeler aracılığıyla C++ ifade edilir olduğu, ancak `ArrayItems`, `TreeItems`veya `LinkedListItems.` için tam olarak uymadığı veri yapılarını görselleştirmek için `CustomListItems` kullanmanız gerekir  

 CAtlMap 'in görselleştiricisi, `CustomListItems` uygun olduğu durumlarda mükemmel bir örnektir.  

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

#### <a name="BKMK_TreeItems_expansion"></a>Ağaç öğeleri genişletmesi  
 Görselleştirilmiş tür bir ağacı temsil ediyorsa, hata ayıklayıcı ağaca yol açabilir ve bir `TreeItems` düğümü kullanarak alt öğelerini görüntüleyebilir. Bu özelliği kullanarak `std::map` türünün görselleştirmesi aşağıda verilmiştir:  

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

 Söz dizimi `LinkedListItems` düğümüne çok benzer. `LeftPointer`, `RightPointer`ve `ValueNode`, ağaç düğümü sınıfının bağlamı altında değerlendirilir ve `ValueNode` boş bırakılabilir veya ağaç düğümünün kendine başvurabileceği `this` olabilir.  

#### <a name="BKMK_ExpandedItem_expansion"></a>ExpandedItem genişletmesi  
 `ExpandedItem` öğesi, temel sınıfların veya veri üyelerinin özelliklerini görselleştirilen türün alt öğeleri gibi görüntüleyerek toplanmış bir alt görünüm oluşturmak için kullanılabilir. Belirtilen ifade değerlendirilir ve sonucun alt düğümleri görselleştirilen türün alt listesine eklenir. Örneğin, genellikle şu şekilde görüntülenecek akıllı bir işaretçi türü `auto_ptr<vector<int>>` olduğunu varsayalım:  

 ![Otomatik&#95;PTR&#60;vektör&#60;int&#62; &#62; varsayılan genişletmesi](../debugger/media/dbg-natvis-expand-expandeditem-default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  

 Vector öğesinin değerlerini görmek için, değişken penceresinde _Myptr üye aracılığıyla geçen iki düzeyin detayına gidebilirsiniz. `ExpandedItem` bir öğesi ekleyerek `_Myptr` değişkenini hiyerarşisinden ortadan kaldırabilir ve doğrudan vektör öğelerini görüntüleyebilirsiniz::  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 ![Otomatik&#95;PTR&#60;vektör&#60;int&#62; &#62; ExpandedItem genişletmesi](../debugger/media/dbg-natvis-expand-expandeditem-visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  

 Aşağıdaki örnekte, türetilmiş bir sınıftaki temel sınıftan özelliklerin nasıl toplanacağını gösterilmektedir. `CPanel` sınıfın `CFrameworkElement`türediğini varsayalım. Temel `CFrameworkElement` sınıfından gelen özellikleri yinelemek yerine `ExpandedItem` düğümü, bu özelliklerin `CPanel` sınıfının alt listesine eklenmesini sağlar. Türetilmiş sınıf için görselleştirme eşleştirmeyi kapatan **ND** Biçim belirleyicisi burada gereklidir. Aksi takdirde `*(CFrameworkElement*)this` ifade, varsayılan görselleştirme türü eşleştirme kuralları en uygun olanı düşüntiğinden, `CPanel` görselleştirmesinin yeniden uygulanmasını sağlar. **ND** Biçim belirticisinin kullanılması, hata ayıklayıcıya temel sınıf görselleştirmesini veya temel sınıfın görselleştirmesi yoksa temel sınıf varsayılan genişletmesini kullanmasını söyler.  

```xml  
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  

```  

#### <a name="BKMK_Synthetic_Item_expansion"></a>Yapay öğe genişletmesi  
 `ExpandedItem` öğesinin hiyerarşileri ortadan kaldırarak verilerin bir düzbir görünümünü sağladığından, `Synthetic` düğümü tersini yapar. Yapay bir alt öğe (yani, bir ifadenin sonucu olmayan bir alt öğe) oluşturmanızı sağlar. Bu alt öğe, kendi alt öğelerini içerebilir. Aşağıdaki örnekte, `Concurrency::array` türü için görselleştirme, kullanıcıya bir tanılama iletisi göstermek için bir `Synthetic` düğümü kullanır:  

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

 ![Concurrency:: Smtik element Expansio ile dizi](../debugger/media/dbg-natvis-expand-synthetic.png "DBG_NATVIS_Expand_Synthetic")  

### <a name="BKMK_HResult"></a>HResult  
 `HResult` öğesi, hata ayıklayıcı penceresinde bir HRESULT için görüntülenen bilgileri özelleştirmenize olanak sağlar. `HRValue` öğesi, özelleştirilecek olan HRESULT 'nin 32 bitlik değerini içermelidir. `HRDescription` öğesi, hata ayıklayıcıda görüntülenen bilgileri içerir.  

```  

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

### <a name="BKMK_UIVisualizer"></a>UIVisualizer  
 `UIVisualizer` öğesi bir grafik görselleştiricisi eklentisini hata ayıklayıcıyla kaydeder. Bir grafik görselleştiricisi eklentisi, bir değişken veya nesneyi veri türüne uygun şekilde göstermek için bir iletişim kutusu veya başka bir arabirim oluşturur. Görselleştiricisi eklentisi bir [VSPackage](../extensibility/internals/vspackages.md) olarak yazılmalıdır ve hata ayıklayıcı tarafından tüketilen bir hizmeti kullanıma sunmayı gerektirir. . Natvis dosyası, eklentinin adı, sunulan hizmetin GUID 'SI ve ayrıca görselleştirilecek türler gibi kayıt bilgilerini içerir.  

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

 Bir `UIVisualizer`, bir `ServiceId` - `Id` öznitelik çifti tarafından tanımlanır. `ServiceId`, görselleştiricisi paketi tarafından sunulan hizmetin GUID 'sidir, `Id` bir hizmet birden fazla Görselleştirici sağlıyorsa Görselleştiriciler için kullanılabilen benzersiz bir tanımlayıcıdır. Yukarıdaki örnekte, aynı görselleştiricisi hizmeti iki Görselleştiriciler sağlar.  

 `MenuName` özniteliği, kullanıcıların hata ayıklayıcı değişken pencerelerinin büyüteç simgesinin yanında açılan menüyü açtıklarında Görselleştirici adı olarak gördükleri şeydir, örneğin:  

 ![UIVisualizer menü kısayol menüsü](../debugger/media/dbg-natvis-vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  

 . Natvis dosyasında tanımlanan her tür, bunları görüntüleyebilen UI görselleştiricilerini açıkça listemelidir. Hata ayıklayıcı, türleri kayıtlı Görselleştiriciler ile eşleştirmek için tür girişlerindeki Görselleştirici başvurularıyla eşleşir. Örneğin, `std::vector` için aşağıdaki tür girdisi Yukarıdaki örneğimizde UIVisualizer 'a başvurur.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Bellek içi bit eşlemler görüntülemek için kullanılan görüntü Izleme uzantısında UIVisualizer örneğini görebilirsiniz: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  

### <a name="customvisualizer-element"></a>CustomVisualizer öğesi  
 `CustomVisualizer`, Visual Studio 'da çalışan kodda görselleştirmeyi denetlemek için yazabileceğiniz bir VSıX uzantısı belirten bir genişletilebilirlik noktasıdır. VSıX uzantıları yazma hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md). Özel görselleştiricisi yazmak, bir XML Natvis tanımı yazmadan çok daha fazla çalışmadır, ancak Natvis 'ın neleri desteklediğine veya desteklemediği kısıtlamalardan ücretsizdir. Özel Görselleştiriciler, hata ayıklanan işlemi sorgulamak ve değiştirmek ya da Visual Studio 'nun diğer bölümleriyle iletişim kurmak için kullanılabilecek hata ayıklayıcı genişletilebilirlik API 'Lerinin tamamına erişebilir.  

 CustomVisualizer öğelerinde `Condition`, `IncludeView`ve `ExcludeView` özniteliklerini kullanabilirsiniz.
