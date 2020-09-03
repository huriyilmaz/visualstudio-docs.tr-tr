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
ms.openlocfilehash: 63390672b246add079806c68a23b69f0e0132c2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850202"
---
# <a name="create-custom-views-of-native-objects"></a>Yerel Nesnelerin Özel Görünümlerini Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Natvis çerçevesi, Visual Studio 'Nun hata ayıklayıcı değişken pencerelerinde yerel türleri görüntüleme şeklini özelleştirmenizi sağlar (örneğin, **Watch**, **Yereller**ve **veri ipuçları** pencereleri).  

 Natvis, Visual Studio 'nun önceki sürümlerinde kullanılan ve XML sözdizimi, daha iyi tanılama, sürüm oluşturma ve birden çok dosya desteği sunan bir **oto exp. dat** dosyasının yerini alır.  

> [!NOTE]
> Şu durumlarda Natvis çerçevesini görselleştirmeler için kullanamazsınız:  
> 
> - Hata ayıklayıcı türü **karma**olarak ayarlanmış bir C++ Windows Masaüstü projesinde hata ayıklaması yapıyorsanız.  
>   - Yönetilen Uyumluluk modundaki bir Windows masaüstü uygulamasında karışık modda hata ayıklama yapıyorsunuz (**Araçlar/Seçenekler/hata ayıklama/genel/yönetilen uyumluluk modunu kullan**).  
>   - Yerel uyumluluk modundaki bir Windows masaüstü uygulamasında hata ayıklaması yapıyorsanız (**Araçlar/Seçenekler/hata ayıklama/genel/yerel uyumluluk modunu kullan**).  

## <a name="why-create-natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a> Neden Natvis görselleştirmeleri oluşturulsun?  
 , Geliştiricilerin hata ayıklama sırasında kolayca görebilmesi için oluşturduğunuz türler için görselleştirme kuralları oluşturmak üzere Natvis çerçevesini kullanabilirsiniz.  

 Örneğin, aşağıdaki görüntüde özel görselleştirmeler uygulanmadan hata ayıklayıcıda görüntülenen [Windows:: UI:: XAML:: Controls:: TextBox](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textbox.aspx) türünde bir değişken gösterilmektedir.  

 ![TextBox varsayılan görselleştirmesi](../debugger/media/dbg-natvis-textbox-default.png "DBG_NATVIS_TextBox_Default")  

 Vurgulanan satır `Text` sınıfının özelliğini gösterir `TextBox` . Karmaşık sınıf hiyerarşisi bu değeri bulmayı zorlaştırır; Üstelik, hata ayıklayıcı nesne tarafından kullanılan özel dize türünü nasıl yorumlayabileceğinizi bilmez, bu nedenle TextBox içinde tutulan dizeyi göremezsiniz.  

 Aynı `TextBox` şey, özel görselleştirme kuralları uygulandığında değişken penceresini çok daha basit bir şekilde inceler. Sınıfının önemli üyeleri birlikte görüntülenebilir ve hata ayıklayıcı özel dize türünün temel alınan dize değerini gösterir.  

 ![Görselleştirici kullanarak metin kutusu verileri](../debugger/media/dbg-natvis-textbox-visualizer.png "DBG_NATVIS_TextBox_Visualizer")  

## <a name="using-natvis-files"></a><a name="BKMK_Using_Natvis_files"></a> Natvis dosyalarını kullanma  
 . natvis dosyaları. natvis uzantılı XML dosyalarıdır. Şema **%VSInstallDir%\Xml\Schemas\natvis.exe**içinde tanımlanmıştır.  

 Bir. natvis dosyasının temel yapısı bir veya daha fazla `Type` öğedir, burada her öğe, `Type` özniteliğinde tam adı belirtilen bir tür için bir görselleştirme girişini temsil eder `Name` .  

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
 . Natvis dosyalarını herhangi bir C++ projesine ekleyebilirsiniz.  

 Yeni bir. natvis dosyası eklemek için, açık bir C++ projesiyle, **Çözüm Gezgini**proje düğümünü seçin ve **Ekle/yeni öğe/Visual C++/yardımcı program/hata ayıklayıcı görselleştirme dosyası (. natvis) öğesine**tıklayın. Hata ayıklayıcı, Natvis dosyalarını C++ projelerinden otomatik olarak yükler. Varsayılan olarak, projenizdeki Natvis dosyaları, proje tarafından oluşturulan. pdb dosyasına da eklenir. Yani bu proje tarafından oluşturulan ikilide hata ayıklaması yaparsanız, proje açık olmasa bile hata ayıklayıcı,. pdb dosyasından Natvis dosyasını yükler. . Natvis dosyasının. pdb dosyasına dahil edilmesini istemiyorsanız, **Çözüm Gezgini**. natvis dosyasına sağ tıklayın ve **yapılandırma özellikleri** penceresinde derleme dışında **Evet**olarak **dışarıda bırakılır** .  

 Visual Studio 'Yu kullanarak Natvis dosyalarını düzenlemeniz önerilir. hata ayıklama sırasında yaptığınız tüm değişiklikler, dosyayı kaydettiğinizde bu işlem otomatik olarak etkili olur. IntelliSense 'den geliştirilmiş bir düzen deneyimi de alırsınız.  

 Bir. pdb 'den yüklenen Natvis dosyaları yalnızca, pdb 'nin başvurduğu modüldeki türler için geçerlidir. Örneğin, Module1. pdb adlı bir tür için bir giriş tanımlıyorsa `Test` , bu giriş yalnızca Module1.dll Içindeki **Test** sınıfına uygulanır. Başka bir modül **Test**adlı bir sınıfı da tanımlıyorsa, Module1. pdb 'nin Natvis girdisi kendisine uygulanmaz.  

## <a name="deploying-natvis-files"></a><a name="BKMK_natvis_location"></a> . Natvis dosyalarını dağıtma  
 . Natvis dosyanız yalnızca bir Visual Studio projesinde oluşturmakta olduğunuz türlere geçerliyse, herhangi bir şey yapmanız gerekmez; . natvis,. pdb içine dahil edilmiştir. Ancak,. Natvis dosyalarını Kullanıcı dizininize veya birden çok projeye uygulanmasını istiyorsanız bir sistem dizinine ekleyebilirsiniz.  

 . Natvis dosyalarının değerlendirilme sırası aşağıdaki gibidir:  

1. bir. pdb dosyasına katıştırılmış. natvis dosyaları, hata ayıklaması yaptığınız (yüklenen projede aynı ada sahip bir dosya mevcut değilse)  

2. yüklenen bir C++ projelerinin parçası olan. natvis dosyaları veya en üst düzey bir çözüm öğesi. Bu, sınıf kitaplıkları dahil olmak üzere tüm yüklenen C++ projelerini içerir, ancak diğer dillerin projelerini içermez (örn. bir C# projesinden bir. natvis dosyası yüklenemez). Yürütülebilir projelerde, kullanılabilir bir C++ projesi bulunmadığından, bir. pdb dosyasında bulunmayan. Natvis dosyalarını barındırmak için çözüm öğelerini kullanmanız gerekir.  

3. Kullanıcıya özgü Natvis dizini (**%USERPROFILE%\My, Studio 2015 \ Görselleştiriciler**  

4. Sistem genelindeki Natvis dizini (**%VSInstallDir%\common7\packages\debugger\görselleştiriciler**). Bu, Visual Studio ile yüklenen. natvis dosyalarının kopyalandığı yerdir. Yönetici izinleriniz varsa, bu dizine diğer dosyaları da ekleyebilirsiniz.  

## <a name="modifying-natvis-files-while-debugging"></a>Hata ayıklarken. Natvis dosyalarını değiştirme  
 İçindeki bir. natvis dosyasını, dahil olduğu projede hata ayıklarken IDE 'de değiştirebilirsiniz. Dosyayı IDE 'de açın (hata ayıklamada kullandığınız Visual Studio örneğini kullanarak), değiştirin ve kaydedin. Dosya kaydedildiği anda, **Watch** ve **Locals** pencerelerinin değişikliği yansıtacak şekilde güncelleştirilmeleri gerekir. . Natvis dosyasını IDE dışında değiştirirseniz, değişiklikler otomatik olarak etkili olmaz. Windows 'u güncelleştirmek için, **izleme** penceresindeki **. natvisreload** komutunu değerlendirebilirsiniz. Bu, değişikliklerin hata ayıklama oturumunu yeniden başlatmadan etkili olmasına neden olur.  

 Ayrıca, hata ayıklaması yaptığınız bir çözüme. natvis dosyaları ekleyebilir veya silebilirsiniz ve Visual Studio ilgili görselleştirmeleri ekler veya kaldırır.  

 Bir. pdb dosyasına katıştırılmışsa hata ayıklarken bir. natvis dosyasını değiştiremezsiniz.  

 Natvis dosyasını daha yeni bir sürüme yükseltirken **. natvisreload** komutunu kullanın (örneğin, kaynak denetimine işaretlenmişse ve dosyada başka birinin yaptığı en son değişiklikleri almak istiyorsanız). Visual Studio XML düzenleyicisini kullanarak Natvis dosyalarını düzenlemeniz önerilir.  

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> İfadeler ve biçimlendirme  
 Natvis görselleştirmeleri, görüntülenecek veri öğelerini belirtmek için C++ ifadeleri kullanır. [Bağlam operatörü (C++)](../debugger/context-operator-cpp.md)içinde açıklanan hata ayıklayıcıdaki C++ ifadelerinin geliştirmelere ve kısıtlamalarına ek olarak, aşağıdaki farklılıklara dikkat etmeniz gerekir:  

- Natvis ifadeleri, geçerli yığın çerçevesini değil görselleştirilen nesne bağlamında değerlendirilir. Örneğin, `x` bir Natvis ifadesinde kullanırsanız, bu, `x` `x` Şu anda yürütülmekte olan işlevde adlı yerel bir değişkene değil, görselleştirilen nesnede adlı alana başvurur. Küresel değişkenlere erişebilseniz de, Natvis ifadelerinde yerel değişkenlere erişemezsiniz.  

- Natvis ifadeleri işlev değerlendirmesi veya yan etkilere izin vermez. Bu, işlev çağrılarının ve atama işleçlerinin yoksayıldığı anlamına gelir. [Hata ayıklayıcı iç işlevleri](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) yan etkilerden farklı olduğundan, diğer işlev çağrılarına izin verilmese de, her bir natvis ifadesinden serbestçe çağrılabilir.  

  Bir ifadenin bir değişken penceresinde nasıl görüntülendiğini denetlemek için [C++](../debugger/format-specifiers-in-cpp.md) konusunun biçim Belirticilerinin [Biçim](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) belirticileri bölümünde açıklanan biçim belirticilerini kullanabilirsiniz. Sanallaştırma girişi `Size` bir ArrayItems genişletme ifadesi gibi Natvis tarafından dahili olarak kullanıldığında biçim Belirticilerinin yoksayıldığını unutmayın.  

## <a name="natvis-views"></a>Natvis görünümleri  
 Natvis görünümleri, herhangi bir türü birden fazla şekilde görmenizi sağlar. Örneğin, **basit** adlı bir görünümü tanımlayabilir ve bu sayede bir türün basitleştirilmiş bir görünümünü elde edebilirsiniz. Örneğin, şu şekilde görselleştirme `std::vector` :  

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

 Ve öğeleri, ve `DisplayString` `ArrayItems` `[size]` `[capacity]` öğeleri basit görünümden dışlarken varsayılan görünümde ve basit görünümde kullanılır. Alternatif bir görünüm belirtmek için **, görünüm Biçim belirleyicisi ' ni** kullanabilirsiniz. **İzle** penceresinde, basit görünümü VEC olarak belirtirsiniz **, görüntüleme (basit)**:  

 ![Basit görünümle izleme penceresi](../debugger/media/watch-simpleview.png "İzleme-SimpleView")  

## <a name="diagnosing-natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis hatalarını tanılama  
 , Sözdizimi ve ayrıştırma hatalarını gidermek için Natvis tanılamayı kullanabilirsiniz. Hata ayıklayıcı bir görselleştirme girişinde hata ile karşılaştığında, hataları yoksayar ve türü ham biçiminde görüntüler ya da uygun bir görselleştirmeyi seçer. Belirli bir görselleştirme girişinin neden yoksayıldığını anlamak ve temeldeki hataların ne olduğunu görmek için, Natvis tanılama **araçları/seçenekler/hata ayıklama/çıkış penceresi/Natvis tanılama iletileri (yalnızca C++)** seçeneğini etkinleştirebilirsiniz. Hatalar **Çıkış** penceresinde görüntülenir.  

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Natvis sözdizimi başvurusu  

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> Oto görselleştiricisi öğesi  
 `AutoVisualizer`Öğesi,. natvis dosyasının kök düğümüdür ve ad alanı `xmlns:` özniteliğini içerir.  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

### <a name="type-element"></a><a name="BKMK_Type"></a> Type öğesi  
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

1. Bu görselleştirmenin kullanılması gereken tür ( `Type Name` özniteliği).  

2. Bu türdeki bir nesnenin değeri şöyle görünmelidir ( `DisplayString` öğe).  

3. Kullanıcı onu bir değişken penceresinde (düğüm) genişlediğinde, türün üyeleri şöyle görünmelidir `Expand` .  

   **Şablonlu sınıflar** `Name` Öğesinin özniteliği, `Type` `*` şablonlu sınıf adları için kullanılabilecek bir joker karakter olarak bir yıldız işareti kabul eder:  

```xml  
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  

```  

 Bu örnekte, aynı görselleştirme, nesnenin a veya a olup olmadığı için kullanılacaktır `CAtlArray<int>` `CAtlArray<float>` . Bir için belirli bir görselleştirme girişi varsa, `CAtlArray<float>` Bu, genel bir üzerinden önceliklidir.  

 Şablon parametrelerine, $T 1, $T 2 vb. makrolar kullanılarak görselleştirme girişinde başvurulabileceğini unutmayın. Bu makroların örneklerini bulmak için bkz. Visual Studio ile birlikte gelen. natvis dosyaları.  

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Görselleştiricisi türü eşleşiyor  
 Bir görselleştirme girdisi doğrulanamazsa, bir sonraki kullanılabilir görselleştirme kullanılır.  

#### <a name="inheritable-attribute"></a>Inheritable özniteliği  
 Bir görselleştirmenin yalnızca bir temel tür için mi yoksa temel türe ve tüm türetilmiş türlerin isteğe bağlı özniteliğiyle mi geçerli olduğunu belirtebilirsiniz `Inheritable` . Aşağıdaki öğe, görselleştirme yalnızca tür için geçerlidir `BaseClass` :  

```xml  
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

 Varsayılan değeri `Inheritable` `true` .  

#### <a name="priority-attribute"></a>Priority özniteliği  
 `Priority`Öznitelik, bir tanım ayrıştıramazsa alternatif tanımlarının kullanılacağı sırayı belirtir. Olası değerleri `Priority` şunlardır: `Low` ,,, `MediumLow` `Medium` `MediumHigh` , ve `High` , varsayılan değerdir `Medium` .  

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

#### <a name="version-element"></a><a name="BKMK_Versioning"></a> Sürüm öğesi  
 Ad çakışmalarının `Version` en aza indirilebilmesi ve türlerin farklı sürümleri için farklı görselleştirmeler kullanılabilmesi için görselleştirmeleri belirli modüller ve sürümleri ile kapsamını atamak için öğesini kullanın. Örneğin:  

```xml  
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

 Bu örnekte, görselleştirme yalnızca `DirectUI::Border` 1,0 sürümünden 1,5 ' de bulunan tür için geçerlidir `Windows.UI.Xaml.dll` . Sürüm öğelerinin kapsamını, görselleştirme girişini belirli bir modüle ve sürüme ekleme ve yanlışlıkla uyuşmazlıkları azalttığını unutmayın, ancak bir tür farklı modüller tarafından kullanılan ortak bir üstbilgi dosyasında tanımlanmışsa, tür belirtilen modülde olmadığında sürümlü görselleştirme uygulanmaz.  

#### <a name="optional-attribute"></a>İsteğe bağlı öznitelik  
 `Optional`Özniteliği herhangi bir düğümde görünebilir. İsteğe bağlı bir düğümün içindeki herhangi bir alt ifade ayrıştırılamazsa bu düğüm yok sayılır, ancak Type öğesinin geri kalanı hala geçerlidir. Aşağıdaki türde, `[State]` isteğe bağlı değildir, ancak `[Exception]` isteğe bağlıdır.  Bu `MyNamespace::MyClass` , _ adlı bir alan içeriyorsa `M_exceptionHolder` , yine de node `[State]` ve `[Exception]` Node, ancak `_M_exceptionHolder` eksikse yalnızca `[State]` düğümü görürsünüz.  

```xml  
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Condition özniteliği  
 İsteğe bağlı `Condition` öznitelik birçok görselleştirme öğesi için kullanılabilir ve bir görselleştirme kuralının ne zaman kullanılması gerektiğini belirtir. Koşul özniteliği içindeki ifade olarak çözümlenirse `false` , öğesi tarafından belirtilen görselleştirme kuralı uygulanmaz. True olarak değerlendirilirse veya bir öznitelik yoksa, `Condition` görselleştirme kuralı türe uygulanır. Görselleştirme girişlerinde Logic için bu özniteliği kullanabilirsiniz `if-else` . Örneğin, aşağıdaki görselleştirmede `DisplayString` akıllı işaretçi türü için iki öğe vardır:  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 Üye olduğunda `_Myptr` `null` , ilk `DisplayString` öğenin koşulu olarak çözümlenir `true` , böylece form görüntülenir. `_Myptr`Üye olmadığında `null` , koşul olarak değerlendirilir `false` ve ikinci `DisplayString` öğe görüntülenir.  

### <a name="includeview-and-excludeview-attributes"></a>IncludeView ve ExcludeView öznitelikleri  
 Bu öznitelikler, farklı görünümlerde görüntülenecek veya görüntülenmeyen öğeleri belirtir. Örneğin, Natvis belirtimi aşağıda verilmiştir `std::vector` :  

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

 Basit görünüm, [size] ve [Capacity] öğelerini basit görünümde görüntülemez. `IncludeView="simple"`Yerine `ExcludeView` `[size]` `[capacity]` kullanılsaydı, ve öğeleri varsayılan görünüm yerine basit görünümde gösterilir.  

 `IncludeView`Ve `ExcludeView` özniteliklerini bağımsız üyelerde ve türlerinde kullanabilirsiniz.  

### <a name="displaystring"></a><a name="BKMK_DisplayString"></a> DisplayString  
 Bir `DisplayString` öğesi, değişkeninin değeri olarak gösterilecek dizeyi belirtir. İfadelerle karışık rastgele dizeler kabul eder. Küme ayraçları içindeki her şey bir ifade olarak yorumlanır. Örneğin, şöyle bir `DisplayString` giriş:  

```xml  
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  

```  

 , Türü değişkenlerinin şöyle gösterildiği anlamına gelir `CPoint` :  

 ![DisplayString öğesi kullanma](../debugger/media/dbg-natvis-cpoint-displaystring.png "DBG_NATVIS_CPoint_DisplayString")  

 `DisplayString`İfadesinde `x` ve `y` üyeleri olan, `CPoint` küme ayraçları içindedir ve bu nedenle değerleri değerlendirilir. İfade ayrıca çift küme ayraçları (veya) kullanarak bir küme ayracını nasıl kaçırkullanabileceğinizi gösterir `{{` `}}` .  

> [!NOTE]
> `DisplayString`Öğesi, rastgele dizeleri ve küme ayracı sözdizimini kabul eden tek öğedir. Diğer tüm Görselleştirme öğeleri yalnızca hata ayıklayıcı tarafından değerlendirilen ifadeleri kabul eder.  

### <a name="stringview"></a><a name="BKMK_StringView"></a> StringView  
 `StringView`Öğesi, değeri yerleşik metin Görselleştirici öğesine gönderilecek olan ifadeyi tanımlar. Örneğin, türü için aşağıdaki görselleştirmemiz olduğunu varsayalım `ATL::CStringT` :  

```xml  
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>  

```  

 `CStringT`Nesne şöyle görünür:  

 ![CStringT DisplayString öğesi](../debugger/media/dbg-natvis-displaystring-cstringt.png "DBG_NATVIS_DisplayString_CStringT")  

 Görselleştirme, bir `CStringT` nesneyi değişken penceresinde şöyle görüntüler:  

 Bir öğesi eklemek, `StringView` hata ayıklayıcıya bu değerin bir metin görselleştirmesi tarafından görüntülenebileceğini gösterir:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

 Büyüteç simgesinin aşağıdaki değerin yanında göründüğünü unutmayın. Simgeyi seçtiğinizde, işaret eden dizeyi görüntüleyen metin görselleştiricisi başlatılır `m_pszData` .  

 ![StringView görselleştiricisi ile CStringT verileri](../debugger/media/dbg-natvis-stringview-cstringt.png "DBG_NATVIS_StringView_CStringT")  

> [!NOTE]
> İfadenin, `{m_pszData,su}` `su` değeri bir Unicode dize olarak göstermek Için bir C++ Biçim belirleyicisi içerdiğini unutmayın. Daha fazla bilgi için bkz. [C++ Içindeki biçim belirticileri](../debugger/format-specifiers-in-cpp.md) .  

### <a name="expand"></a><a name="BKMK_Expand"></a> Genişletin  
 `Expand`Düğüm, Kullanıcı tarafından değişken Windows 'da genişlediğinde görselleştirilen türün alt öğelerini özelleştirmek için kullanılır. Alt öğeleri tanımlayan alt düğümlerin listesini kabul eder.  

 `Expand`Düğüm isteğe bağlıdır.  

- Bir `Expand` görselleştirme girişinde bir düğüm belirtilmemişse, Visual Studio 'nun varsayılan genişletme kuralları kullanılır.  

- `Expand`Düğüm altında alt düğüm olmayan bir düğüm belirtilmişse, tür hata ayıklayıcı penceresinde Genişletilebilir olmayacaktır.  

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Öğe genişletmesi  
 `Item`Öğesi, bir düğümde kullanılacak en temel ve en yaygın öğedir `Expand` . `Item` tek bir alt öğe tanımlar. Örneğin,,, `CRect` `top` `left` `right` ve `bottom` alanlarını ve aşağıdaki görselleştirme girişini içeren bir sınıfınız olduğunu varsayalım:  

```xml  
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  

```  

 `CRect`Tür şöyle görünür:  

 ![Öğe öğesi genişlemesiyle CRect](../debugger/media/dbg-natvis-expand-item-crect1.png "DBG_NATVIS_Expand_Item_CRect1")  

 Ve öğelerinde belirtilen ifadeler `Width` `Height` değerlendirilir ve değer sütununda gösterilir. `[Raw View]`Özel bir genişletme kullanıldığında düğüm, hata ayıklayıcı tarafından otomatik olarak oluşturulur. Nesnenin ham görünümünün görselleştirmeden farklı olduğunu göstermek için yukarıdaki ekran görüntüsünde genişletilir. Visual Studio varsayılan genişletmesi, temel sınıf için bir alt ağaç oluşturur ve temel sınıfın tüm veri üyelerini alt öğe olarak listeler.  

> [!NOTE]
> Öğe öğesinin ifadesi karmaşık bir türe işaret ediyorsa, `Item` düğümün kendisi Genişletilebilir olur.  

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

 ![std:: ArrayItems genişletmesi kullanan vektör](../debugger/media/dbg-natvis-expand-arrayitems-stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  

 Düğüm en azından şunları `ArrayItems` içermelidir:  

1. `Size`Hata ayıklayıcının dizi uzunluğunu anlaması için bir ifade (bir tamsayı olarak değerlendirilmesi gerekir)  

2. `ValuePointer`İlk öğeyi işaret eden bir ifade (olmayan bir öğe türünün işaretçisi olması gerekir `void*` ).  

   Dizi alt sınırının varsayılan değeri 0 ' dır. Değer bir öğesi kullanılarak geçersiz kılınabilir `LowerBound` (örnekler, Visual Studio ile birlikte gelen. natvis dosyalarında bulunabilir).  

   Artık `[]` işleci, örneğin bir genişletme ile kullanabilirsiniz `ArrayItems` `vector[i]` . [] İşleci, `ArrayItems` türü bu işlece izin vermediği halde, veya kullanan tek boyutlu bir dizinin herhangi bir görselleştirmesinde kullanılabilir `IndexListItems` (örneğin `CATLArray` ).  

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

 `Direction` dizinin satır birincil mı yoksa sütun için mi olduğunu belirtir. `Rank` dizinin derecesini belirtir. `Size`Öğesi, `$i` Bu boyuttaki dizinin uzunluğunu bulmak için boyut diziniyle birlikte bulunan örtük parametreyi kabul eder. Örneğin, önceki örnekte, ifadenin üstünde `_M_extent.M_base[0]` 0 ' ın uzunluğu, 1 ' i `_M_extent._M_base[1]` ve bu şekilde devam eder.  

 İki boyutlu bir `Concurrency::array` nesne hata ayıklayıcıda nasıl görünür:  

 ![ArrayItems genişletmesi olan iki boyutlu dizi](../debugger/media/dbg-natvis-expand-arrayitems-2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> IndexListItems genişletmesi  
 `ArrayItems`Genişletmeyi yalnızca dizi öğeleri bellekte bitişik olarak olarak düzenlense kullanabilirsiniz. Hata ayıklayıcı, yalnızca işaretçisini geçerli öğe ile arttırarak bir sonraki öğeye alınır. Dizini değer düğümüne göre değiştirmeniz gereken çalışmaları desteklemek için `IndexListItems` düğümler kullanılabilir. Düğüm kullanan bir görselleştirme aşağıda verilmiştir `IndexListItems` :  

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

 Artık `[]` işleci, örneğin bir genişletme ile kullanabilirsiniz `IndexListItems` `vector[i]` . `[]`İşleci, `ArrayItems` türü bu işlece izin vermediği halde, veya kullanan tek boyutlu bir dizinin herhangi bir görselleştirmesinde kullanılabilir `IndexListItems` (örneğin `CATLArray` ).  

 Ve arasındaki tek fark `ArrayItems` , `IndexListItems` `ValueNode` öğesinin örtük parametreyle i. öğesi için tam ifadeyi beklediği<sup>th</sup> olmamanızdır `$i` .  

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems genişletmesi  
 Görselleştirilmiş tür bağlantılı bir listeyi temsil ediyorsa, hata ayıklayıcı alt öğelerini bir düğüm kullanarak görüntüleyebilir `LinkedListItems` . `CAtlList`Bu özelliği kullanarak türün görselleştirmesi aşağıda verilmiştir:  

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

- `NextPointer`Ve `ValueNode` ifadeleri, ana liste türü değil, bağlantılı liste düğümü öğesi bağlamında değerlendirilir. Yukarıdaki örnekte, `CAtlList` `CNode` `atlcoll.h` bağlantılı listenin bir düğümünü temsil eden bir sınıfı (içinde bulunur) vardır. `m_pNext` ve `m_element` , `CNode` sınıfının değil, bu sınıfın alanlarıdır `CAtlList` .  

- `ValueNode`Boş bırakılabilir veya `this` bağlantılı liste düğümünün kendine başvurması gerekebilir.  

#### <a name="customlistitems-expansion"></a>CustomListItems genişletmesi  
 `CustomListItems`Genişletme, Hashtable gibi bir veri yapısına geçiş için özel mantık yazmanızı sağlar. `CustomListItems`Değerlendirmek için ihtiyaç duyduğunuz her şeyin C++ ifadeleriyle ifade edilmelidir, ancak, `ArrayItems` veya için tam olarak uygun olmayan veri yapılarını görselleştirip `TreeItems``LinkedListItems.`  

 CAtlMap 'in görselleştiricisi, uygun olduğu durumlarda mükemmel bir örnektir `CustomListItems` .  

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
 Görselleştirilen tür bir ağacı temsil ediyorsa, hata ayıklayıcı ağaca yol açabilir ve bir düğüm kullanarak alt öğelerini görüntüleyebilir `TreeItems` . `std::map`Bu özelliği kullanarak türün görselleştirmesi aşağıda verilmiştir:  

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

 Sözdizimi, düğüme çok benzer `LinkedListItems` . `LeftPointer`, `RightPointer` ve `ValueNode` ağaç düğümü sınıfının bağlamı altında değerlendirilir ve `ValueNode` boş bırakılabilir veya `this` Ağaç düğümünün kendine başvurması gerekir.  

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem genişletmesi  
 `ExpandedItem`Öğesi, temel sınıfların veya veri üyelerinin özelliklerini görselleştirilen türün alt öğeleri gibi görüntüleyerek toplanmış bir alt görünüm oluşturmak için kullanılabilir. Belirtilen ifade değerlendirilir ve sonucun alt düğümleri görselleştirilen türün alt listesine eklenir. Örneğin, genellikle şöyle görüntülenecek akıllı bir işaretçi türü olduğunu varsayalım `auto_ptr<vector<int>>` :  

 ![Otomatik&#95;PTR&#60;vektör&#60;int&#62;&#62; varsayılan genişletme](../debugger/media/dbg-natvis-expand-expandeditem-default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  

 Vector öğesinin değerlerini görmek için, değişken penceresinde _Myptr üye aracılığıyla geçen iki düzeyin detayına gidebilirsiniz. Bir öğesi ekleyerek `ExpandedItem` , `_Myptr` hiyerarşide değişkeni ortadan kaldırabilir ve vektör öğelerini doğrudan görüntüleyebilirsiniz::  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 ![Otomatik&#95;PTR&#60;vektör&#60;int&#62;&#62; ExpandedItem genişletmesi](../debugger/media/dbg-natvis-expand-expandeditem-visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  

 Aşağıdaki örnekte, türetilmiş bir sınıftaki temel sınıftan özelliklerin nasıl toplanacağını gösterilmektedir. `CPanel`Sınıfın türetildiğini varsayalım `CFrameworkElement` . Düğüm, temel sınıftan gelen özellikleri yinelemek yerine `CFrameworkElement` , `ExpandedItem` Bu özelliklerin sınıfın alt listesine eklenmesini sağlar `CPanel` . Türetilmiş sınıf için görselleştirme eşleştirmeyi kapatan **ND** Biçim belirleyicisi burada gereklidir. Aksi takdirde ifade, `*(CFrameworkElement*)this` `CPanel` görselleştirmenin yeniden uygulanmasını sağlar çünkü varsayılan görselleştirme türü eşleştirme kuralları en uygun olanı kabul eder. **ND** Biçim belirticisinin kullanılması, hata ayıklayıcıya temel sınıf görselleştirmesini veya temel sınıfın görselleştirmesi yoksa temel sınıf varsayılan genişletmesini kullanmasını söyler.  

```xml  
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  

```  

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Yapay öğe genişletmesi  
 `ExpandedItem`Öğesi hiyerarşiyi ortadan kaldırarak verilerin bir düzbir görünümünü sağladığından, `Synthetic` düğüm tersini yapar. Yapay bir alt öğe (yani, bir ifadenin sonucu olmayan bir alt öğe) oluşturmanızı sağlar. Bu alt öğe, kendi alt öğelerini içerebilir. Aşağıdaki örnekte, türü için görselleştirme, kullanıcıya bir `Concurrency::array` `Synthetic` tanılama iletisi göstermek için bir düğüm kullanır:  

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

### <a name="hresult"></a><a name="BKMK_HResult"></a> HResult  
 `HResult`Öğesi, hata ayıklayıcı penceresinde BIR HRESULT için görüntülenen bilgileri özelleştirmenize olanak sağlar. `HRValue`Öğesi, özelleştirilecek olan HRESULT 'nin 32 bitlik değerini içermelidir. `HRDescription`Öğesi, hata ayıklayıcıda görüntülenen bilgileri içerir.  

```  

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

### <a name="uivisualizer"></a><a name="BKMK_UIVisualizer"></a> UIVisualizer  
 Bir `UIVisualizer` öğesi bir grafik görselleştiricisi eklentisini hata ayıklayıcıyla kaydeder. Bir grafik görselleştiricisi eklentisi, bir değişken veya nesneyi veri türüne uygun şekilde göstermek için bir iletişim kutusu veya başka bir arabirim oluşturur. Görselleştiricisi eklentisi bir [VSPackage](../extensibility/internals/vspackages.md) olarak yazılmalıdır ve hata ayıklayıcı tarafından tüketilen bir hizmeti kullanıma sunmayı gerektirir. . Natvis dosyası, eklentinin adı, sunulan hizmetin GUID 'SI ve ayrıca görselleştirilecek türler gibi kayıt bilgilerini içerir.  

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

 Bir `UIVisualizer` öznitelik çifti tarafından tanımlanır `ServiceId`  -  `Id` . `ServiceId` , görselleştiricisi paketi tarafından kullanıma sunulan hizmetin GUID 'sidir, `Id` bir hizmet birden fazla Görselleştirici sağlıyorsa Görselleştiriciler için kullanılabilen benzersiz bir tanımlayıcıdır. Yukarıdaki örnekte, aynı görselleştiricisi hizmeti iki Görselleştiriciler sağlar.  

 `MenuName`Özniteliği, kullanıcıların hata ayıklayıcı değişken pencerelerinin büyüteç simgesinin yanında açılan menüyü açtıklarında Görselleştirici adı olarak gördükleri şeydir, örneğin:  

 ![UIVisualizer menü kısayol menüsü](../debugger/media/dbg-natvis-vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  

 . Natvis dosyasında tanımlanan her tür, bunları görüntüleyebilen UI görselleştiricilerini açıkça listemelidir. Hata ayıklayıcı, türleri kayıtlı Görselleştiriciler ile eşleştirmek için tür girişlerindeki Görselleştirici başvurularıyla eşleşir. Örneğin, için aşağıdaki tür girdisi `std::vector` Yukarıdaki örneğimizde UIVisualizer 'a başvurur.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Bellek içi bit eşlemler görüntülemek için kullanılan görüntü Izleme uzantısında UIVisualizer örneğini görebilirsiniz: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  

### <a name="customvisualizer-element"></a>CustomVisualizer öğesi  
 `CustomVisualizer` , Visual Studio 'da çalışan kodda görselleştirmeyi denetlemek için yazabileceğiniz bir VSıX uzantısı belirten bir genişletilebilirlik noktasıdır. VSıX uzantıları yazma hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md). Özel görselleştiricisi yazmak, bir XML Natvis tanımı yazmadan çok daha fazla çalışmadır, ancak Natvis 'ın neleri desteklediğine veya desteklemediği kısıtlamalardan ücretsizdir. Özel Görselleştiriciler, hata ayıklanan işlemi sorgulamak ve değiştirmek ya da Visual Studio 'nun diğer bölümleriyle iletişim kurmak için kullanılabilecek hata ayıklayıcı genişletilebilirlik API 'Lerinin tamamına erişebilir.  

 `Condition` `IncludeView` `ExcludeView` Customgörselleştiricisi öğelerinde, ve özniteliklerini kullanabilirsiniz.
