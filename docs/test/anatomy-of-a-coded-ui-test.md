---
title: Kodlanmış UI Testinin Anatomisi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7100c6bb5c1dfb4c7d336ec110cf532f1f998d4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591209"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Kodlanmış ui testinin anatomisi

Kodlanmış bir UI test projesinde Kodlanmış Bir UI Testi oluşturduğunuzda, çözüme birkaç dosya eklenir. Bu makalede, dosyalar hakkında bilgi sağlar.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="contents-of-a-coded-ui-test"></a>Kodlanmış bir UI testinin içeriği

Kodlanmış Kullanıcı Arabirimi Testi oluşturduğunuzda, **Kodlanmış Kullanıcı Arabirimi Test Oluşturucusu,** test altında kullanıcı arabiriminin bir haritasını ve ayrıca tüm testler için test yöntemlerini, parametreleri ve iddialarını oluşturur. Ayrıca her test için bir sınıf dosyası oluşturur.

|Dosya|İçindekiler|Düzenlen -ebilir?|
|-|-|-|
|[Uımap.designer.cs](#UIMapDesignerFile)|[Bildirimler bölümü](#UIMapDesignerFile)<br /><br /> [UIMap sınıfı](#UIMapClass) (kısmi, otomatik oluşturulan)<br /><br /> [Yöntemler](#UIMapMethods)<br /><br /> [Özellikler](#UIMapProperties)|Hayır|
|[Uımap.cs](#UIMapCS)|[UIMap sınıfı](#UIMapCS) (kısmi)|Evet|
|[CodedUITest1.cs](#CodedUITestCS)|[CodedUITest1 sınıfı](#CodedUITestCS)<br /><br /> [Yöntemler](#CodedUITestMethods)<br /><br /> [Özellikler](#CodedUITestProperties)|Evet|
|[Uitest](#UIMapuitest)|Test için UI'nin XML haritası.|Hayır|

### <a name="uimapdesignercs"></a><a name="UIMapDesignerFile"></a>Uımap.designer.cs
Bu dosya, bir test oluşturulduğunda **Kodlanmış UI Test Oluşturucu** tarafından otomatik olarak oluşturulan kod içerir. Bu dosya, bir test her değiştiğinde yeniden oluşturulur, böylece kod ekleyebileceğiniz veya değiştirebileceğiniz bir dosya değildir.

#### <a name="declarations-section"></a>Bildirimler bölümü
Bu bölümde, windows arabirimi için aşağıdaki bildirimler ilerler.

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

Ad <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> alanı, Windows kullanıcı arabirimi (UI) için dahildir. Bir web sayfası kullanıcı arabirimi için, ad alanı; <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls> Bir Windows Presentation Foundation Kullanıcı Arabirimi <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>için, ad alanı .

#### <a name="uimap-class"></a><a name="UIMapClass"></a>UIMap sınıfı
Dosyanın bir sonraki bölümü [UIMap](/previous-versions/dd580454(v=vs.140)) sınıfıdır.

```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

Sınıf kodu, kısmi <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> sınıf olarak bildirilen sınıfa uygulanan bir öznitelik ile başlar. Özniteliğin bu dosyadaki her sınıfa da uygulandığına dikkat edin. Bu sınıf için daha fazla kod içerebilecek diğer dosya, daha sonra tartışılan *UIMap.cs.*

Oluşturulan `UIMap` sınıf, test kaydedildiğinde belirtilen her yöntem için kod içerir.

```csharp
public void LaunchCalculator()
public void AddItems()
public void VerifyTotal()
public void CleanUp()
```

[UIMap](/previous-versions/dd580454(v=vs.140)) sınıfının bu bölümü, yöntemlertarafından gerekli olan her özellik için oluşturulan kodu da içerir.

```csharp
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

##### <a name="uimap-methods"></a><a name="UIMapMethods"></a>UIMap yöntemleri
Her yöntemin `AddItems()` yönteme benzeyen bir yapısı vardır. Bu, netlik eklemek için satır sonları ile birlikte sunulan kod altında daha ayrıntılı olarak açıklanır.

```csharp
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

Her yöntem tanımı için özet açıklama, bu yöntem için parametre değerleri için hangi sınıfın kullanılacağını söyler. Bu durumda, daha `AddItemsParams` sonra *UIMap.cs* dosyasında tanımlanan ve aynı zamanda `AddItemsParams` özellik tarafından döndürülen değer türü olan sınıftır.

Yöntem kodunun üst kısmında `Variable Declarations` yöntem tarafından kullanılan UI nesneleri için yerel değişkenleri tanımlayan bir bölge dir.

Bu yöntemde, `UIItemWindow` `UIItemEdit` hem de daha sonra `UICalculatorWindow` *UIMap.cs* dosyasında tanımlanan sınıf kullanılarak erişilen özellikleri vardır.

`AddItemsParams` Aşağıda, nesnenin özelliklerini kullanarak klavyeden Hesap Makinesi uygulamasına metin gönderen satırlar yer alır.

Yöntem `VerifyTotal()` benzer bir yapıya sahiptir ve aşağıdaki savkodu içerir:

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

Windows Calculator uygulamasının geliştiricisi denetim için herkese açık bir ad sağlamadığından metin kutusu adı bilinmiyor olarak listelenir. Gerçek <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> değer beklenen değere eşit olmadığında yöntem başarısız olur ve bu da testin başarısız olmasıyla olur. Ayrıca, beklenen değerin bir boşluk tarafından izlenen ondalık bir nokta içerdiğini de unutmayın. Bu testin işlevselliğini değiştirmeniz gerekiyorsa, bu ondalık sayıya ve alana izin vermelisiniz.

##### <a name="uimap-properties"></a><a name="UIMapProperties"></a>UIMap özellikleri
Her özellik için kod da sınıf boyunca standarttır. `AddItemsParams` Yöntemde özellik için aşağıdaki kod `AddItems()` kullanılır.

```csharp
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

Özelliğin, değeri iade etmeden önce `mAddItemsParams` tutmak için adlandırılmış özel bir yerel değişken kullandığına dikkat edin. Döndürdüğü nesnenin özellik adı ve sınıf adı aynı sınır adı aynı Sınıf daha sonra *UIMap.cs* dosyasında tanımlanır.

Bir özellik tarafından döndürülen her sınıf benzer şekilde yapılandırılır. Sınıf aşağıdakigibidir: `AddItemsParams`

```csharp
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

*UIMap.cs* dosyasındaki tüm sınıflarda olduğu gibi, <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>bu sınıf . Bu küçük sınıfta `Fields` daha önce tartışılan <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> `UIMap.AddItems()` yöntemde kullanılan yöntem için parametreler olarak kullanılacak dizeleri tanımlayan bir bölgedir. Bu parametrelerin kullanıldığı yöntem çağrılmadan önce bu dize alanlarındaki değerleri değiştirmek için kod yazabilirsiniz.

### <a name="uimapcs"></a><a name="UIMapCS"></a>Uımap.cs
Varsayılan olarak, bu dosya `UIMap` hiçbir yöntem veya özellikleri olan kısmi bir sınıf içerir.

#### <a name="uimap-class"></a>UIMap sınıfı
Bu, [UIMap](/previous-versions/dd580454(v=vs.140)) sınıfının işlevselliğini genişletmek için özel kod oluşturabileceğiniz yerdir. Bu dosyada oluşturduğunuz kod, bir test her **değiştirildiğinde Kodlanmış UI Test Oluşturucusu** tarafından üzerine yazılmaz.

[UIMap'in](/previous-versions/dd580454(v=vs.140)) tüm bölümleri, [UIMap](/previous-versions/dd580454(v=vs.140)) sınıfının diğer bölümlerindeki yöntemleri ve özellikleri kullanabilir.

### <a name="codeduitest1cs"></a><a name="CodedUITestCS"></a>CodedUITest1.cs
Bu dosya **Kodlanmış UI Test Oluşturucu**tarafından oluşturulur, ancak test her değiştirildiğinde yeniden oluşturulmaz, böylece bu dosyadaki kodu değiştirebilirsiniz. Dosyanın adı, oluşturduğunuzda test için belirttiğiniz addan oluşturulur.

#### <a name="codeduitest1-class"></a>CodedUITest1 sınıfı

Varsayılan olarak, bu dosya yalnızca bir sınıfın tanımını içerir.

```csharp
[CodedUITest]
public class CodedUITest1
```

[CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)) otomatik olarak test çerçevesi bir test uzantısı olarak tanımak için izin veren sınıfa uygulanır. Ayrıca bu kısmi bir sınıf olmadığını unutmayın. Tüm sınıf kodu bu dosyada yer almaktadır.

##### <a name="codeduitest1-properties"></a><a name="CodedUITestProperties"></a>CodedUITest1 özellikleri

Sınıf, dosyanın alt kısmında bulunan iki varsayılan özellik içerir. Bunları değiştirmeyin.

```csharp
/// <summary>
/// Gets or sets the test context which provides
/// information about and functionality for the current test run.
///</summary>
public TestContext TestContext
public UIMap UIMap
```

##### <a name="codeduitest1-methods"></a><a name="CodedUITestMethods"></a>CodedUITest1 yöntemleri
Varsayılan olarak, sınıf yalnızca bir yöntem içerir.

```csharp
public void CodedUITestMethod1()
```

Bu yöntem, `UIMap` [UIMap Sınıfı'ndaki](#UIMapClass)bölümde açıklanan testinizi kaydederken belirttiğiniz her yöntemi çağırır.

"Yorumlanmamışsa" başlıklı `Additional test attributes`bir bölge, iki isteğe bağlı yöntem içerir.

```csharp
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

Yöntem, `MyTestInitialize()` test <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> çerçevesine bu yöntemi diğer test yöntemlerinden önce çağırmasını söyleyen bir yönteme uygulanmıştır. Benzer şekilde, `MyTestCleanup()` yöntem, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> diğer tüm test yöntemleri çağrıldıktan sonra bu yöntemi aramak için test çerçevesi söyler, uygulanan vardır. Bu yöntemlerin kullanımı isteğe bağlıdır. Bu test için `UIMap.LaunchCalculator()` yöntem çağrılabilir `MyTestInitialize()` `UIMap.CloseCalculator()` ve yöntem 'den değil, 'den `MyTestCleanup()` `CodedUITest1Method1()`çağrılabilir.

[CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))kullanarak bu sınıfa daha fazla yöntem eklerseniz, test çerçevesi testin bir parçası olarak her yöntemi çağırır.

### <a name="uimapuitest"></a><a name="UIMapuitest"></a>Uitest
Bu, kodlanmış UI test kaydının yapısını ve tüm parçalarını temsil eden bir XML dosyasıdır. Bunlar, bu sınıfların yöntemlerine ve özelliklerine ek olarak eylemleri ve sınıfları içerir. [UIMap.Designer.cs](#UIMapDesignerFile) dosyası, testyapısını yeniden oluşturmak için Kodlanmış Kullanıcı Arabirimi Oluşturucusu tarafından oluşturulan kodu içerir ve test çerçevesine bağlantı sağlar.

*UIMap.uitest* dosyası doğrudan editable değildir. Ancak, *uimap.uitest* dosyasını ve [*UIMap.Designer.cs*](#UIMapDesignerFile) dosyayı otomatik olarak değiştiren testi değiştirmek için Kodlanmış UI Oluşturucu'yu kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Uımap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>
- <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>
- [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>
- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlu UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış Ara Birimi testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)
- [Birden çok Kullanıcı Altı Bilgi Har(R)'li büyük bir uygulamayı test etme](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
