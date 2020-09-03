---
title: Kodlanmış UI testinin anatomumu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
ms.assetid: 9c5d82fc-3fb7-4bb1-a9ac-ac1fa3a4b500
caps.latest.revision: 25
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 305c0b33b52c54e7d241b4e86e974d25e58d1e51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660701"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Kodlanmış UI Testinin Anatomisi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI testi projesinde kodlanmış bir UI testi oluşturduğunuzda, çözümünüze birkaç dosya eklenir. Bu konu başlığında, bu dosyaları araştırmak için örnek bir kodlanmış UI testi kullanacağız.

 **Gereksinimler**

- Visual Studio Enterprise

## <a name="contents-of-a-coded-ui-test"></a>Kodlanmış UI testinin içeriği
 Kodlanmış UI testi oluşturduğunuzda, **KODLANMıŞ UI Test Oluşturucusu** test altında Kullanıcı arabiriminin bir haritasını ve ayrıca tüm testler için test yöntemleri, parametreleri ve onayları oluşturur. Ayrıca her test için bir sınıf dosyası oluşturur.

|Dosya|İçindekiler|Yapılamaz?|
|----------|--------------|---------------|
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Bildirimler bölümü](#UIMapDesignerFile)<br /><br /> [UIMap sınıfı](#UIMapClass) (kısmi, otomatik olarak oluşturulan)<br /><br /> [Yöntemler](#UIMapMethods)<br /><br /> [Özellikler](#UIMapProperties)|No|
|[UIMap.cs](#UIMapCS)|[UIMap sınıfı](#UIMapCS) (kısmi)|Yes|
|[CodedUITest1.cs](#CodedUITestCS)|[Codeduıtest1 sınıfı](#CodedUITestCS)<br /><br /> [Yöntemler](#CodedUITestMethods)<br /><br /> [Özellikler](#CodedUITestProperties)|Yes|
|[UIMap. UITest](#UIMapuitest)|Test için Kullanıcı arabiriminin XML eşlemesi.|No|

### <a name="uimapdesignercs"></a><a name="UIMapDesignerFile"></a> UIMap.Designer.cs
 Bu dosya, bir test oluşturulduğunda, **KODLANMıŞ UI Test Oluşturucusu** tarafından otomatik olarak oluşturulan kodu içerir. Bu dosya, bir testin her değiştiği her seferinde yeniden oluşturulur. böylece kod ekleyebileceğiniz veya değiştiremeyeceğiniz bir dosya olmaz.

#### <a name="declarations-section"></a>Bildirimler bölümü
 Bu bölüm, bir Windows Kullanıcı arabirimi için aşağıdaki bildirimleri içerir.

```csharp
using System;
using System.CodeDom.Compiler;
using System.Collections.Generic;
using System.Drawing;
using System.Text.RegularExpressions;
using System.Windows.Input;
using Microsoft.VisualStudio.TestTools.UITest.Extension;
using Microsoft.VisualStudio.TestTools.UITesting;
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;
using MouseButtons = System.Windows.Forms.MouseButtons;
```

 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>Ad alanı bir Windows Kullanıcı arabirimi (UI) için dahil edilmiştir. Web sayfası kullanıcı arabirimi için, ad alanı olur <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls> ; Windows Presentation Foundation Kullanıcı arabirimi için ad alanı olur <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls> .

#### <a name="uimap-class"></a><a name="UIMapClass"></a> UIMap sınıfı
 Dosyanın sonraki bölümü [UIMap](/previous-versions/dd580454(v=vs.140)) sınıfıdır.

```
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

 Sınıf kodu, <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> kısmi sınıf olarak belirtilen sınıfına uygulanan bir ile başlar. Özniteliğin bu dosyadaki her sınıfa da uygulandığını fark edeceksiniz. Bu sınıf için daha fazla kod içerebilen diğer dosya `UIMap.cs` daha sonra ele alınmıştır.

 Oluşturulan `UIMap` sınıf, test kaydedildiğinde belirtilen her bir yöntem için kod içerir.

```
public void LaunchCalculator()
public void AddItems()
public void VerifyTotal()
public void CleanUp()
```

 [UIMap](/previous-versions/dd580454(v=vs.140)) sınıfının bu bölümü, yöntemler için gereken her bir özellik için oluşturulan kodu da içerir.

```
public virtual LaunchCalculatorParams LaunchCalculatorParams
public virtual AddItemsParams AddItemsParams
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues
public virtual CalculateItemsParams CalculateItemsParams
public virtual VerifyMathAppTotalExpectedValues
    VerifyMathAppTotalExpectedValues
public UIStartMenuWindow UIStartMenuWindow
public UIRunWindow UIRunWindow
public UICalculatorWindow UICalculatorWindow
public UIStartWindow UIStartWindow
public UIMathApplicationWindow UIMathApplicationWindow
```

##### <a name="uimap-methods"></a><a name="UIMapMethods"></a> UIMap yöntemleri
 Her yöntemin yöntemine benzer bir yapısı vardır `AddItems()` . Bu, kod altında daha ayrıntılı olarak açıklanmıştır ve bu, açıklık eklemek için satır sonları ile birlikte sunulur.

```
/// <summary>
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.
/// </summary>
public void AddItems()
{
    #region Variable Declarations
    WinControl uICalculatorDialog =
        this.UICalculatorWindow.UICalculatorDialog;
    WinEdit uIItemEdit =
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;
    #endregion

    // Type '{NumPad7}' in 'Calculator' Dialog
    Keyboard.SendKeys(uICalculatorDialog,
        this.AddItemsParams.UICalculatorDialogSendKeys,
        ModifierKeys.None);

    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    Keyboard.SendKeys(uIItemEdit,
        this.AddItemsParams.UIItemEditSendKeys,
        ModifierKeys.None);
}
```

 Her yöntem tanımına ait Özet yorumu, bu yöntemin parametre değerleri için hangi sınıfın kullanılacağını söyler. Bu durumda,, `AddItemsParams` dosyasında daha sonra tanımlanan `UIMap.cs` ve özelliği tarafından döndürülen değer türü olan sınıftır `AddItemsParams` .

 Yöntem kodunun üst kısmında, `Variable Declarations` yöntemi tarafından kullanılacak kullanıcı arabirimi nesneleri için yerel değişkenleri tanımlayan bir bölgedir.

 Bu yöntemde, her ikisi de, `UIItemWindow` `UIItemEdit` `UICalculatorWindow` dosyasında daha sonra tanımlanan sınıfı kullanılarak erişilen özelliklerdir `UIMap.cs` .

 Daha sonra, nesnenin özelliklerini kullanarak klavyeden Hesaplayıcı uygulamasına metin gönderen satırlar bulunur `AddItemsParams` .

 `VerifyTotal()`Yöntemi çok benzer bir yapıya sahiptir ve aşağıdaki onaylama kodunu içerir.

```
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

 Windows Hesaplayıcı uygulamasının geliştiricisi denetim için genel kullanıma açık bir ad sağlamadığından metin kutusu adı bilinmiyor olarak listelenir. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>Gerçek değer beklenen değere eşit olmadığında yöntem başarısız olur, bu da testin başarısız olmasına neden olur. Ayrıca, beklenen değerin bir boşluk tarafından izlenen bir ondalık nokta içerdiğine dikkat edin. Bu özel testin işlevselliğini değiştirmeniz gerekiyorsa, bu ondalık noktaya ve alana izin vermeniz gerekir.

##### <a name="uimap-properties"></a><a name="UIMapProperties"></a> UIMap özellikleri
 Her bir özelliğin kodu, sınıf boyunca de çok standart. Özelliği için aşağıdaki kod `AddItemsParams` `AddItems()` yönteminde kullanılır.

```
public virtual AddItemsParams AddItemsParams
{
    get
    {
        if ((this.mAddItemsParams == null))
        {
            this.mAddItemsParams = new AddItemsParams();
        }
        return this.mAddItemsParams;
    }
}
```

 Özelliğin, `mAddItemsParams` değeri döndürülmadan önce değerini tutmak için adlı özel bir yerel değişken kullandığını unutmayın. Döndürdüğü nesnenin özellik adı ve sınıf adı aynıdır. Sınıfı, dosyasında daha sonra tanımlanır `UIMap.cs` .

 Bir özellik tarafından döndürülen her sınıf benzer şekilde yapılandırılır. Sınıfı aşağıda verilmiştir `AddItemsParams` .

```
/// <summary>
/// Parameters to be passed into 'AddItems'
/// </summary>
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public class AddItemsParams
{
    #region Fields
    /// <summary>
    /// Type '{NumPad7}' in 'Calculator' Dialog
    /// </summary>
    public string UICalculatorDialogSendKeys = "{NumPad7}";

    /// <summary>
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    /// </summary>
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";
    #endregion
}
```

 Dosyadaki tüm sınıflarda olduğu gibi `UIMap.cs` , bu sınıf ile başlar <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> . Bu küçük sınıfta, `Fields` <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> `UIMap.AddItems()` daha önce açıklanan yöntemde kullanılan yöntemi için parametre olarak kullanılacak dizeleri tanımlayan bir bölgedir. Bu dize alanlarındaki değerleri bu parametrelerin kullanıldığı yöntemden önce değiştirmek için kod yazabilirsiniz.

### <a name="uimapcs"></a><a name="UIMapCS"></a> UIMap.cs
 Varsayılan olarak, bu dosya, `UIMap` yöntemi veya özellikleri olmayan kısmi bir sınıf içerir.

#### <a name="uimap-class"></a>UIMap sınıfı
 Bu, [Umap](/previous-versions/dd580454(v=vs.140)) sınıfının işlevlerini genişletmek için özel kod oluşturabileceğiniz yerdir. Bu dosyada oluşturduğunuz kod, bir testin her değiştirildiği her seferinde **KODLANMıŞ UI Test Oluşturucusu** tarafından yeniden üretilmeyecektir.

 [UIMap](/previous-versions/dd580454(v=vs.140)) 'in tüm kısımları [umap](/previous-versions/dd580454(v=vs.140)) sınıfının diğer bölümlerinden Yöntemler ve özellikleri kullanabilir.

### <a name="codeduitest1cs"></a><a name="CodedUITestCS"></a> CodedUITest1.cs
 Bu dosya, **KODLANMıŞ UI Test Oluşturucusu**tarafından oluşturulur, ancak bu dosyadaki kodu değiştirebilmek için test her değiştirildiğinde yeniden oluşturulmaz. Dosyanın adı, oluşturduğunuzda test için belirttiğiniz adından oluşturulur.

#### <a name="codeduitest1-class"></a>Codeduıtest1 sınıfı
 Varsayılan olarak, bu dosya yalnızca bir sınıfın tanımını içerir.

```
[CodedUITest]
public class CodedUITest1
```

 [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)) , test çerçevesinin onu test uzantısı olarak tanımasını sağlayan sınıfına otomatik olarak uygulanır. Ayrıca bunun kısmi bir sınıf olmadığına dikkat edin. Tüm sınıf kodu bu dosyada yer alır.

##### <a name="codeduitest1-properties"></a><a name="CodedUITestProperties"></a> Codeduıtest1 özellikleri
 Sınıfı, dosyanın en altında bulunan iki varsayılan özelliği içerir. Değiştirilmemelidir.

```
/// <summary>
/// Gets or sets the test context which provides
/// information about and functionality for the current test run.
///</summary>
public TestContext TestContext
public UIMap UIMap
```

##### <a name="codeduitest1-methods"></a><a name="CodedUITestMethods"></a> Codeduıtest1 yöntemleri
 Varsayılan olarak, sınıfı yalnızca bir yöntem içerir.

```
public void CodedUITestMethod1()
```

 Bu yöntem, testinizi kaydettiğinizde belirttiğiniz her yöntemi çağırır, bu, `UIMap` [UIMap sınıfının](#UIMapClass)bölümünde açıklanmıştır.

 `Additional test attributes`Açıklama kaldırıdıysanız başlıklı bir bölge, iki isteğe bağlı yöntem içerir.

```
// Use TestInitialize to run code before running each test
[TestInitialize()]
public void MyTestInitialize()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.LaunchCalculator();
}

// Use TestCleanup to run code after each test has run
[TestCleanup()]
public void MyTestCleanup()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.CloseCalculator();
}
```

 `MyTestInitialize()`Yöntemi <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> kendisine uygulandı. Bu, test çerçevesinin diğer test yöntemlerinden önce bu yöntemi çağırmasını söyler. Benzer şekilde, `MyTestCleanup()` yöntemi <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> kendisine uygulanmış olur, bu da test çerçevesinin tüm diğer test yöntemleri çağrıldıktan sonra bu yöntemi çağırmasını söyler. Bu yöntemlerin kullanımı isteğe bağlıdır. Bu test için `UIMap.LaunchCalculator()` yöntemi öğesinden çağrılabilir `MyTestInitialize()` ve `UIMap.CloseCalculator()` yöntemi from yerine öğesinden çağrılabilir `MyTestCleanup()` `CodedUITest1Method1()` .

 [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))kullanarak bu sınıfa daha fazla yöntem eklerseniz, test çerçevesi testin bir parçası olarak her bir yöntemi çağırır.

### <a name="uimapuitest"></a><a name="UIMapuitest"></a> UIMap. UITest
 Bu, kodlanmış UI testi kaydının yapısını ve tüm parçalarını temsil eden bir XML dosyasıdır. Bunlar, bu sınıfların yöntemlerine ve özelliklerine ek olarak eylemleri ve sınıfları içerir. [UIMap.Designer.cs](#UIMapDesignerFile) dosyası, test yapısını yeniden oluşturmak IÇIN kodlanmış UI Oluşturucu tarafından oluşturulan kodu içerir ve test çerçevesiyle bağlantı sağlar.

 `UIMap.uitest`Dosya doğrudan düzenlenebilir değil. Ancak, `UIMap.uitest` dosyayı ve [UIMap.Designer.cs](#UIMapDesignerFile) dosyasını otomatik olarak değiştiren testi DEğIşTIRMEk Için kodlanmış UI oluşturucusunu kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>
- <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>
- [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>
- [Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Kodlanmış UI Testleri için En İyi Yöntemler](../test/best-practices-for-coded-ui-tests.md)
- [Birden Çok UI Eşlemesi Bulunan Büyük Uygulamaları Sınama](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
