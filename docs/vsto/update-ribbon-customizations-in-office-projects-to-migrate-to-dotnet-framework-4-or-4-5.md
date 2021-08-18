---
title: .NET Framework 4.5'e geçirilen Şerit özelleştirmelerini güncelleştirme
description: Hedef çerçeve 4 veya sonraki bir sonraki bir sonraki hedef çerçeveye değiştirilirse proje .NET Framework gerektiğini öğrenin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0f40e0e3bfd2e5aed59cddb9d99f7d89c3b2aaaa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025699"
---
# <a name="update-ribbon-customizations-migrated-to-net-framework-45"></a>.NET Framework 4.5'e geçirilen Şerit özelleştirmelerini güncelleştirme

  Projeniz Şerit **(Görsel Tasarımcı)** proje öğesi kullanılarak oluşturulmuş bir Şerit özelleştirmesi içeriyorsa, hedef çerçeve veya sonraki bir ile değiştirildiyse proje kodunda aşağıdaki [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] değişiklikleri yapın.

- Oluşturulan Şerit kodunu değiştirme.

- Çalışma zamanında Şerit denetimleri örneği olan, Şerit olaylarını işen veya Şerit bileşeninin konumunu program aracılığıyla ayar eden tüm kodu değiştirme.

## <a name="update-the-generated-ribbon-code"></a>Oluşturulan Şerit kodunu güncelleştirme
 Projenizin hedef çerçevesi veya sonrası olarak değiştirilirse, aşağıdaki adımları gerçekleştirerek Şerit öğesi için [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oluşturulan kodu değiştirebilirsiniz. Güncelleştirmeniz gereken kod dosyaları programlama diline ve projeyi nasıl oluşturduğunuza bağlıdır:

- Diğer Visual Basic veya Içinde oluşturduğunuz Visual C# projelerinde veya Şerit arka arkasındaki kod dosyasındaki tüm adımları [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] gerçekleştirin (*YourRibbonItem*. Designer.cs veya *YourRibbonItem*. Designer.vb). Arka Visual Basic projelerinde arka Çözüm Gezgini için, **dosyanın** içinde Tüm Dosyaları Göster **düğmesine Çözüm Gezgini.**

- Visual Studio 2008'de oluşturduğunuz ve sonra sürümüne yükseltilen Visual C# projelerinde, Şerit kod [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] dosyasındaki (*YourRibbonItem*.cs veya *YourRibbonItem*.vb) ilk iki adımı gerçekleştirin ve Şerit kodu arka arkasındaki dosyasında kalan adımları gerçekleştirin.

### <a name="to-change-the-generated-ribbon-code"></a>Oluşturulan Şerit kodunu değiştirmek için

1. Şerit sınıfının bildirimini yerine 'den türetmesi <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> için `Microsoft.Office.Tools.Ribbon.OfficeRibbon` değiştirme.

2. Aşağıda gösterildiği gibi Şerit sınıfının oluşturucuslarını değiştirme. Oluşturucuya kendi kodunuzu eklediyebilirsiniz, kodunuzu değiştirme. Bu Visual Basic, yalnızca parametresiz oluşturucuda değişiklik. Diğer oluşturucusu yoksayın.

     Aşağıdaki kod örneği, 3.5'i hedefleyen bir projede Şerit sınıfının varsayılan .NET Framework gösterir.

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

     Aşağıdaki kod örneği, veya sonrakini hedef alan bir projede Şerit sınıfının varsayılan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oluşturucusu gösterir.

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

3. yönteminde, bir Şerit denetimi oluşturmakta olan tüm kodu değiştirerek kodun nesnenin yardımcı `InitializeComponent` yöntemlerinden birini kullanması <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> için kullanın.

    > [!NOTE]
    > Visual C# projelerinde, yöntemini görmek için adlı `Component Designer generated code` bölgeyi genişletmeniz `InitializeComponent` gerekir.

     Örneğin, dosyanız 3.5'i hedef alan bir projede adlandırılmış bir örneği .NET Framework <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> `button1` kod satırı içerdiğini varsayalım.

    ```vb
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()
    ```

    ```csharp
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();
    ```

     veya sonrakini hedef alan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] bir projede bunun yerine aşağıdaki kodu kullanabilirsiniz.

    ```vb
    Me.button1 = Me.Factory.CreateRibbonButton()
    ```

    ```csharp
    this.button1 = this.Factory.CreateRibbonButton();
    ```

     Şerit denetimlerinin yardımcı yöntemlerinin tam listesi için bkz. [Şerit denetimleri örneği.](#ribboncontrols)

4. Visual C# projelerinde, yönteminde belirli bir Şerit temsilcisini kullanmak için `InitializeComponent` temsilci kullanan herhangi bir kod satırı <xref:System.EventHandler%601> değiştirebilirsiniz.

     Örneğin, dosyanız 3.5'i hedef alan bir projede olayı işleyen aşağıdaki <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> kod .NET Framework varsayalım.

    \<CodeContentPlaceHolder>8 veya sonraki bir sonrakini hedef alan bir projede </CodeContentPlaceHolder> bunun yerine aşağıdaki kodu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] kullanabilirsiniz.

    \<CodeContentPlaceHolder>9 </CodeContentPlaceHolder> Şerit temsilcilerinin tam listesi için bkz. [Şerit olaylarını işleme.](#ribbonevents)

5. Visual Basic `ThisRibbonCollection` projelerinde, dosyanın sonundaki sınıfını bulun. Artık 'den devralmak için bu sınıfın bildirimini `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection` değiştirme.

## <a name="instantiate-ribbon-controls"></a><a name="ribboncontrols"></a> Şerit denetimleri örneği
 Şerit denetimlerinin dinamik olarak örneğini oluşturması için tüm kodu değiştirmeniz gerekir. Şerit denetimleri, .NET Framework 3.5'i hedef alan projelerde doğrudan belirli senaryolarda örnek olarak gösterebilirsiniz. veya sonraki bir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sonrakini hedef alan projelerde, bu denetimler doğrudan örnekleyemini alamayabilirsiniz. Nesnesi tarafından sağlanan yöntemleri kullanarak denetimleri oluşturmanız <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> gerekir.

 Nesneye erişmenin iki yolu <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> vardır:

- Şerit sınıfının Factory özelliğini kullanarak. Şerit sınıfınıza koddan bu yaklaşımı kullanın.

- yöntemini `Globals.Factory.GetRibbonFactory` kullanarak. Şerit sınıfınız dışındaki kodlardan bu yaklaşımı kullanın. Globals sınıfı hakkında daha fazla bilgi için bkz. Office [projelerinde nesnelere genel erişim.](../vsto/global-access-to-objects-in-office-projects.md)

  Aşağıdaki kod örneğinde, veya sonrakini hedef alan bir projede Şerit sınıfında bir oluşturma <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] adımları yer almaktadır.

\<CodeContentPlaceHolder>10 11 Aşağıdaki tabloda, program aracılığıyla oluşturabilirsiniz denetimleri ve veya sonrakini hedef alan projelerde denetimleri oluşturmak için kullanabileceğiniz </CodeContentPlaceHolder> 
 \<CodeContentPlaceHolder> </CodeContentPlaceHolder> yöntem [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] listelemektedir.

|Denetim|ve sonraki projelerde kullanmak için RibbonFactory [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] yöntemi|
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

## <a name="handle-ribbon-events"></a><a name="ribbonevents"></a> Şerit olaylarını işleme
 Şerit denetimlerinin olaylarını işlemek için herhangi bir kodu değiştirmeniz gerekir. 3.5'.NET Framework hedeflenen projelerde, bu olaylar genel temsilci tarafından <xref:System.EventHandler%601> ele alır. veya sonraki bir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sonrakini hedef alan projelerde bu olaylar artık diğer temsilciler tarafından iş almaktadır.

 Aşağıdaki tabloda, veya sonrakini hedef alan projelerde şerit olayları ve onlarla ilişkilendirilmiş [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] temsilciler liste almaktadır.

|Olay|Ve sonraki projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] kullanmak üzere temsilci seç|
|-----------| - |
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> oluşturulan Şerit sınıfındaki olay|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Şerit bileşeninin konumunu program aracılığıyla ayarlama
 Şerit gruplarının, sekmelerin veya denetimlerin konumunu ayar eden tüm kodu değiştirmeniz gerekir. .NET Framework 3.5'i hedef alan projelerde, bir grubun, sekmenin veya denetimin özelliğini atamak için statik sınıfın ve `AfterOfficeId` `BeforeOfficeId` yöntemlerini `Microsoft.Office.Tools.Ribbon.RibbonPosition` `Position` kullanabilirsiniz. veya sonraki bir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sonrakini hedef alan projelerde, nesnesi tarafından sağlanan özelliği kullanarak <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> bu yöntemlere erişmeniz <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> gerekir.

 Nesneye erişmenin iki yolu <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> vardır:

- Şerit sınıfının `Factory` özelliğini kullanarak. Şerit sınıfınıza koddan bu yaklaşımı kullanın.

- yöntemini `Globals.Factory.GetRibbonFactory` kullanarak. Şerit sınıfınız dışındaki kodlardan bu yaklaşımı kullanın. Globals sınıfı hakkında daha fazla bilgi için bkz. Office [projelerinde nesnelere genel erişim.](../vsto/global-access-to-objects-in-office-projects.md)

  Aşağıdaki kod örneği, 3.5'i hedefleyen bir projede Şerit sınıfındaki bir sekmenin `Position` özelliğinin .NET Framework göstermektedir.

```vb
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");
```

 Aşağıdaki kod örneği, hedef alan bir projede aynı görevi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] gösterir.

```vb
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");
```

## <a name="see-also"></a>Ayrıca bkz.
- [Office 4 veya sonraki .NET Framework geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
