---
title: Kodlanmış UI Testinin Anatomisi
description: Kodlanmış UI Testi oluşturmada kodlanmış UI test çözümünüze eklenen dosyalar hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 840a0b0b1e322bca6a47999cf1c92b0e47bd684a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068592"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Kodlanmış UI testinin anatomisi

Kodlanmış ui test projesinde Kodlanmış UI Testi oluşturma, çözüme birkaç dosya eklenir. Bu makale dosyalar hakkında bilgi sağlar.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="contents-of-a-coded-ui-test"></a>Kodlanmış UI testinin içeriği

Kodlanmış UI Testi oluştururken, Kodlanmış **UI Test Oluşturucusu** test altında kullanıcı arabiriminin bir haritasını ve tüm testler için test yöntemlerini, parametrelerini ve onaylarını oluşturur. Ayrıca her test için bir sınıf dosyası oluşturur.

|Dosya|İçindekiler|Düzenlen -ebilir?|
|-|-|-|
|[Uımap.designer.cs](#UIMapDesignerFile)|[Bildirim bölümü](#UIMapDesignerFile)<br /><br /> [UIMap sınıfı](#UIMapClass) (kısmi, otomatik oluşturulan)<br /><br /> [Yöntemler](#UIMapMethods)<br /><br /> [Özellikler](#UIMapProperties)|Hayır|
|[Uımap.cs](#UIMapCS)|[UIMap sınıfı](#UIMapCS) (kısmi)|Yes|
|[CodedUITest1.cs](#CodedUITestCS)|[CodedUITest1 sınıfı](#CodedUITestCS)<br /><br /> [Yöntemler](#CodedUITestMethods)<br /><br /> [Özellikler](#CodedUITestProperties)|Yes|
|[Uitest](#UIMapuitest)|Test için kullanıcı arabiriminin XML eşlemesi.|Hayır|

### <a name="uimapdesignercs"></a><a name="UIMapDesignerFile"></a> Uımap.designer.cs
Bu dosya, bir test oluşturulduğunda Kodlanmış **UI Test Oluşturucusu** tarafından otomatik olarak oluşturulan kodu içerir. Bu dosya, bir test her değiştirisinde yeniden oluşturulur, böylece kod ekliyebilirsiniz veya değiştiresiniz.

#### <a name="declarations-section"></a>Bildirim bölümü
Bu bölüm, bir kullanıcı arabirimi için aşağıdaki Windows içerir.

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

Ad <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> alanı, bir kullanıcı Windows (UI) için dahil edilir. Web sayfası kullanıcı arabirimi için ad alanı olacaktır; bir <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls> web Windows Presentation Foundation için ad alanı <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls> olur.

#### <a name="uimap-class"></a><a name="UIMapClass"></a> UIMap sınıfı
Dosyanın sonraki bölümü [UIMap sınıfıdır.](/previous-versions/dd580454(v=vs.140))

```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

Sınıf kodu, kısmi <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> sınıf olarak bildirilen sınıfına uygulanan bir öznitelikle başlar. özniteliğinin bu dosyada yer alan her sınıfa da uygulandığına dikkat olun. Bu sınıf için daha fazla kod içeren diğer dosya, daha sonra *ele alınan UIMap.cs* dosyasıdır.

Oluşturulan `UIMap` sınıf, test kaydedilirken belirtilen her yöntem için kod içerir.

```csharp
public void LaunchCalculator()
public void AddItems()
public void VerifyTotal()
public void CleanUp()
```

[UIMap](/previous-versions/dd580454(v=vs.140)) sınıfının bu bölümü, yöntemler için gereken her özellik için oluşturulan kodu da içerir.

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

##### <a name="uimap-methods"></a><a name="UIMapMethods"></a> UIMap yöntemleri
Her yöntemin yöntemine benzer bir yapısı `AddItems()` vardır. Bu, netlik sağlamak için satır sonları ile birlikte sunulan kod altında daha ayrıntılı olarak açıklanmıştır.

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

Her yöntem tanımının özet açıklaması, bu yöntem için parametre değerleri için hangi sınıfın kullanıLL olduğunu söyler. Bu durumda, daha `AddItemsParams` sonra *UIMap.cs* dosyasında tanımlanan ve özelliği tarafından döndürülen değer türü olan `AddItemsParams` sınıfıdır.

Yöntem kodunun en üstünde, yöntemi tarafından kullanılan kullanıcı `Variable Declarations` arabirimi nesneleri için yerel değişkenleri tanımlayan bir bölge vardır.

Bu yöntemde hem `UIItemWindow` hem `UIItemEdit` de, `UICalculatorWindow` *uimap.cs* dosyasında daha sonra tanımlanan sınıfı kullanılarak erişilen özelliklerdir.

Sonraki satırlar, nesnenin özelliklerini kullanarak klavyeden Hesap makinesi uygulamasına metin gönderecek `AddItemsParams` satırlardır.

yöntemi `VerifyTotal()` benzer bir yapıya sahiptir ve aşağıdaki onay kodunu içerir:

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

Windows Calculator uygulamasının geliştiricisi denetim için genel kullanıma açık bir ad sağlamay olduğundan metin kutusu adı bilinmiyor olarak listelenir. Gerçek değer beklenen değere eşit olmazsa yöntemi başarısız olur ve bu da <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> testin başarısız olmasına neden olur. Ayrıca beklenen değerin ardından boşluk gelen ondalık ayırıcıyı da içerir. Bu testin işlevselliğini değiştirmeniz gerekirse, bu ondalık nokta ve boşluk için izin ver gerekir.

##### <a name="uimap-properties"></a><a name="UIMapProperties"></a> UIMap özellikleri
Her özelliğin kodu da sınıf genelinde standarttır. özelliği için aşağıdaki `AddItemsParams` kod yönteminde `AddItems()` kullanılır.

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

özelliğinin değeri döndürmeden önce tutmak için adlı `mAddItemsParams` özel bir yerel değişken kullandığına dikkat etmek. Özellik adı ve döndüren nesnenin sınıf adı aynıdır. sınıfı daha sonra *UIMap.cs dosyasında tanımlanır.*

Bir özellik tarafından döndürülen her sınıf benzer şekilde yapılandırılmıştır. Sınıfı aşağıdaki `AddItemsParams` şekildedir:

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

*UIMap.cs* dosyasındaki tüm sınıflarda olduğu gibi, bu sınıf ile <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> başlar. Bu küçük sınıfta, daha önce ele alınmıştır yönteminde kullanılan yöntemi için parametre olarak kullanılacak `Fields` <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> `UIMap.AddItems()` dizeleri tanımlayan bir bölgedir. Bu parametrelerin kullanılma yöntemi çağrılmadan önce bu dize alanlarındaki değerleri değiştirmek için kod yazabilirsiniz.

### <a name="uimapcs"></a><a name="UIMapCS"></a> Uımap.cs
Varsayılan olarak, bu dosya hiçbir yöntemi `UIMap` veya özelliği olan kısmi bir sınıf içerir.

#### <a name="uimap-class"></a>UIMap sınıfı
Burada [UIMap](/previous-versions/dd580454(v=vs.140)) sınıfının işlevselliğini genişletmek için özel kod oluşturabilirsiniz. Bu dosyada, bir test her değiştirildiğinde Kodlanmış **UI Test Oluşturucusu** tarafından oluşturulacak kodun üzerine yazılmaz.

[UIMap'in tüm](/previous-versions/dd580454(v=vs.140)) bölümleri [UIMap](/previous-versions/dd580454(v=vs.140)) sınıfının başka bir parçasından yöntemleri ve özellikleri kullanabilir.

### <a name="codeduitest1cs"></a><a name="CodedUITestCS"></a> CodedUITest1.cs
Bu dosya Kodlanmış **UI Test Oluşturucusu** tarafından oluşturulur, ancak test her değiştirildiğinde yeniden oluşturulmaz, böylece bu dosyada kodu değiştirebilirsiniz. Dosyanın adı, oluşturulduğunda test için belirttiğiniz addan oluşturulur.

#### <a name="codeduitest1-class"></a>CodedUITest1 sınıfı

Varsayılan olarak, bu dosya yalnızca bir sınıfın tanımını içerir.

```csharp
[CodedUITest]
public class CodedUITest1
```

[CodedUITestAttribute,](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)) test çerçevesinin bunu bir test uzantısı olarak tanımasını sağlayan sınıfına otomatik olarak uygulanır. Ayrıca bunun kısmi bir sınıf olmadığını da dikkat. Tüm sınıf kodu bu dosyada yer alan.

##### <a name="codeduitest1-properties"></a><a name="CodedUITestProperties"></a> CodedUITest1 özellikleri

sınıfı, dosyanın en altında bulunan iki varsayılan özellik içerir. Bunları değiştirmeyin.

```csharp
/// <summary>
/// Gets or sets the test context which provides
/// information about and functionality for the current test run.
///</summary>
public TestContext TestContext
public UIMap UIMap
```

##### <a name="codeduitest1-methods"></a><a name="CodedUITestMethods"></a> CodedUITest1 yöntemleri
Varsayılan olarak, sınıfı yalnızca bir yöntem içerir.

```csharp
public void CodedUITestMethod1()
```

Bu yöntem, testini kaydettiklerinizi belirttiğiniz her yöntemi çağırarak `UIMap` UIMap Sınıfı bölümünde [açıklanmıştır.](#UIMapClass)

başlıklı bir bölge, `Additional test attributes` açıklanmamışsa, isteğe bağlı iki yöntem içerir.

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

yöntemine uygulanmıştır ve bu da test çerçevesine diğer test yöntemden önce `MyTestInitialize()` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> bu yöntemi çağırmalarını söyler. Benzer şekilde, yöntemine uygulanmıştır ve test çerçevesine diğer tüm test yöntemleri çağrıldıktan sonra bu yöntemi `MyTestCleanup()` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> çağırmalarını söyler. Bu yöntemlerin kullanımı isteğe bağlıdır. Bu test için yöntemi , yöntemi de yerine yönteminden `UIMap.LaunchCalculator()` `MyTestInitialize()` `UIMap.CloseCalculator()` `MyTestCleanup()` çağrıl `CodedUITest1Method1()` olabilir.

[CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))kullanarak bu sınıfa daha fazla yöntem eklersanız, test çerçevesi testin bir parçası olarak her yöntemi çağırabilir.

### <a name="uimapuitest"></a><a name="UIMapuitest"></a> Uitest
Bu, kodlanmış UI test kaydının ve tüm parçalarının yapısını temsil eden bir XML dosyasıdır. Bunlar, bu sınıfların yöntemlerine ve özelliklerine ek olarak eylemleri ve sınıfları içerir. [UIMap.Designer.cs](#UIMapDesignerFile) dosyası, testin yapısını yeniden oluşturmak için Kodlanmış UI Builder tarafından oluşturulan kodu içerir ve test çerçevesine bağlantı sağlar.

*UIMap.uitest* dosyası doğrudan düzenlenemez. Ancak, testte değişiklik yapmak için Kodlanmış UI Oluşturucusu'nu kullanabilirsiniz. Bu, *UIMap.uitest* dosyasını ve [*UIMap.Designer.cs*](#UIMapDesignerFile) dosyasını otomatik olarak değiştirir.

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
- [Kodunuzu test etmek için UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)
- [Birden çok UI haritası ile büyük bir uygulamayı test etme](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen konfigürasyonlar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
