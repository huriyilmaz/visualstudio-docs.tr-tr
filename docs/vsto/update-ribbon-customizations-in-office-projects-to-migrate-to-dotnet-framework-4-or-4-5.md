---
title: .NET Framework 4,5 ' e geçirilen şerit özelleştirmelerini güncelleştirme
description: Hedef Framework .NET Framework 4 veya üzeri olarak değiştirilirse proje kodunuzda değişiklik yapmanız gerektiğini öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a831bced793f13394a89d278a6be1cda959c775a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527933"
---
# <a name="update-ribbon-customizations-migrated-to-net-framework-45"></a>.NET Framework 4,5 ' e geçirilen şerit özelleştirmelerini güncelleştirme

  Projeniz **Şerit (görsel Tasarımcı)** proje öğesi kullanılarak oluşturulmuş bir Şerit özelleştirmesi içeriyorsa, hedef Framework [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha yeni olarak değiştirilirse proje kodunuzda aşağıdaki değişiklikleri yapmanız gerekir.

- Oluşturulan Şerit kodunu değiştirin.

- Çalışma zamanında Şerit denetimleri örnekleyen, Şerit olaylarını işleyen veya bir Şerit bileşeninin konumunu programlı olarak ayarlayan tüm kodları değiştirin.

## <a name="update-the-generated-ribbon-code"></a>Oluşturulan Şerit kodunu güncelleştirme
 Projenizin hedef çatısı [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürümüne değiştirilirse, aşağıdaki adımları gerçekleştirerek şerit öğesi için oluşturulan kodu değiştirmeniz gerekir. Güncelleştirmeniz gereken kod dosyaları programlama diline ve projeyi nasıl oluşturduğunuza bağlıdır:

- Visual Basic projelerinde veya içinde oluşturduğunuz Visual C# projelerinde ya da [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] Şerit arka plan kod dosyasında (*YourRibbonItem*) tüm adımları gerçekleştirin. Designer.cs veya *YourRibbonItem*. Designer. vb). Visual Basic projelerindeki arka plan kod dosyasını görmek için **Çözüm Gezgini** **tüm dosyaları göster** düğmesine tıklayın.

- Visual Studio 2008 ' de oluşturduğunuz ve ardından sürümüne yükselttiğiniz Visual C# projelerinde [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , Şerit kod dosyasında (*YourRibbonItem*. cs veya *YourRibbonItem*. vb) Ilk iki adımı gerçekleştirin ve şerit arka plan kod dosyasında kalan adımları gerçekleştirin.

### <a name="to-change-the-generated-ribbon-code"></a>Oluşturulan Şerit kodunu değiştirmek için

1. Şerit sınıfının bildirimini yerine öğesinden türeten önce değiştirin <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> `Microsoft.Office.Tools.Ribbon.OfficeRibbon` .

2. Ribbon sınıfının yapıcısını aşağıda gösterildiği gibi değiştirin. Kurucuya kendi kodunuzu eklediyseniz, kodunuzu değiştirmeyin. Visual Basic projelerinde yalnızca parametresiz oluşturucuyu değiştirin. Diğer oluşturucuyu yoksayın.

     Aşağıdaki kod örneği, .NET Framework 3,5 ' i hedefleyen bir projede Ribbon sınıfının varsayılan oluşturucusunu gösterir.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
    {
        InitializeComponent();
    }
    ```

     Aşağıdaki kod örneği, veya daha sonra hedefleyen bir projedeki bir şerit sınıfının varsayılan oluşturucusunu gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

    ```vb
    Public Sub New()
        MyBase.New(Globals.Factory.GetRibbonFactory())
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
        : base(Globals.Factory.GetRibbonFactory())
    {
        InitializeComponent();
    }
    ```

3. `InitializeComponent`Yönteminde, bir Şerit denetimi oluşturan herhangi bir kodu değiştirerek kodun, nesnenin yardımcı yöntemlerinden birini kullanması gerekir <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> .

    > [!NOTE]
    > Visual C# projelerinde, yöntemi görmek için adlı bölgeyi genişletmeniz gerekir `Component Designer generated code` `InitializeComponent` .

     Örneğin, dosyanızın <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> `button1` .NET Framework 3,5 ' i hedefleyen bir projede adlandırılmış bir örneği oluşturan aşağıdaki kod satırını içerdiğini varsayalım.

    ```vb
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()
    ```

    ```csharp
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();
    ```

     Veya sonrasını hedefleyen bir projede [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , bunun yerine aşağıdaki kodu kullanmanız gerekir.

    ```vb
    Me.button1 = Me.Factory.CreateRibbonButton()
    ```

    ```csharp
    this.button1 = this.Factory.CreateRibbonButton();
    ```

     Şerit denetimleri için yardımcı yöntemlerin tam listesi için bkz. [Şerit denetimlerini oluştur](#ribboncontrols).

4. Visual C# projelerinde, `InitializeComponent` <xref:System.EventHandler%601> bunun yerine belirli bir şerit temsilcisini kullanmak için bir temsilci kullanan yöntemdeki herhangi bir kod satırını değiştirin.

     Örneğin, dosyanızın <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> .NET Framework 3,5 ' i hedefleyen bir projede olayı işleyen aşağıdaki kod satırını içerdiğini varsayalım.

    \<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> veya sonraki bir sürümü hedefleyen bir projede [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , bunun yerine aşağıdaki kodu kullanmanız gerekir.

    \<CodeContentPlaceHolder>9 </CodeContentPlaceHolder> Şerit temsilcilerinin tam listesi için bkz. [Şerit olaylarını işleme](#ribbonevents).

5. Visual Basic projelerinde, `ThisRibbonCollection` dosyanın sonundaki sınıfı bulun. Bu sınıfın bildirimini artık öğesinden devralınmayacak şekilde değiştirin `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection` .

## <a name="instantiate-ribbon-controls"></a><a name="ribboncontrols"></a> Şerit denetimlerini oluştur
 Şerit denetimlerini dinamik olarak örnekleyen herhangi bir kodu değiştirmeniz gerekir. .NET Framework 3,5 ' i hedefleyen projelerde şerit denetimleri, belirli senaryolarda doğrudan örneklenebilen sınıflardır. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya daha sonra hedeflenen projelerde, bu denetimler doğrudan örnek oluşturabileceksiniz arayüzlerdir. Denetimleri, nesne tarafından sunulan yöntemleri kullanarak oluşturmanız gerekir <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> .

 Nesnesine erişmenin iki yolu vardır <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> :

- Şerit sınıfının Factory özelliğini kullanarak. Şerit sınıfınızın kodundaki bu yaklaşımı kullanın.

- `Globals.Factory.GetRibbonFactory`Yöntemini kullanarak. Şerit sınıfınızın dışındaki koddan Bu yaklaşımı kullanın. Globals sınıfı hakkında daha fazla bilgi için bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md).

  Aşağıdaki kod örneği <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> , veya üstünü hedefleyen bir projede Şerit sınıfında nasıl oluşturulacağını gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

\<CodeContentPlaceHolder>10 </CodeContentPlaceHolder> 
 \<CodeContentPlaceHolder> 11 </CodeContentPlaceHolder> Aşağıdaki tabloda, program aracılığıyla oluşturabileceğiniz denetimler ve veya daha sonra hedeflenen projelerde denetimleri oluşturmak için kullanılacak yöntem listelenmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

|Denetim|Ve sonraki projelerde kullanılacak RibbonFactory yöntemi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|
|-------------| - |
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|

## <a name="handle-ribbon-events"></a><a name="ribbonevents"></a> Şerit olaylarını işle
 Şerit denetimlerinin olaylarını işleyen herhangi bir kodu değiştirmeniz gerekir. .NET Framework 3,5 ' i hedefleyen projelerde, bu olaylar genel temsilci tarafından işlenir <xref:System.EventHandler%601> . [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya daha sonra hedeflenen projelerde, bu olaylar artık diğer temsilciler tarafından işlenir.

 Aşağıdaki tabloda, veya daha sonra hedeflenen projelerde ilişkili Şerit olayları ve temsilcileri listelenmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

|Olay|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Ve sonraki projelerde kullanılacak temsilci|
|-----------| - |
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> oluşturulan şerit sınıfındaki olay|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Şerit bileşeninin konumunu programlı olarak ayarlama
 Şerit gruplarının, sekmelerinin veya denetimlerin konumunu ayarlayan herhangi bir kodu değiştirmeniz gerekir. .NET Framework 3,5 ' i hedefleyen projelerde, `AfterOfficeId` `BeforeOfficeId` `Microsoft.Office.Tools.Ribbon.RibbonPosition` `Position` bir grup, sekme veya denetim özelliğini atamak için statik sınıfın ve yöntemlerini kullanabilirsiniz. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya sonrasını hedefleyen projelerde, bu yöntemlere <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> nesne tarafından sunulan özelliği kullanarak erişmeniz gerekir <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> .

 Nesnesine erişmenin iki yolu vardır <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> :

- `Factory`Şerit sınıfının özelliğini kullanarak. Şerit sınıfınızın kodundaki bu yaklaşımı kullanın.

- `Globals.Factory.GetRibbonFactory`Yöntemini kullanarak. Şerit sınıfınızın dışındaki koddan Bu yaklaşımı kullanın. Globals sınıfı hakkında daha fazla bilgi için bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md).

  Aşağıdaki kod örneği, `Position` .NET Framework 3,5 ' i hedefleyen bir projedeki Şerit sınıfında bir sekmenin özelliğinin nasıl ayarlanacağını göstermektedir.

```vb
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");
```

 Aşağıdaki kod örneği, ' i hedefleyen bir projede aynı görevi gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

```vb
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");
```

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
