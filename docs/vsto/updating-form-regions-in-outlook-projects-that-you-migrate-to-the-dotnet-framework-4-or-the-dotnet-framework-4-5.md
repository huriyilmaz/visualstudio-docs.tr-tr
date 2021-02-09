---
title: .NET Framework 4,5 ' e geçirildiğinde Outlook form bölgelerini Güncelleştir
description: Bir form bölgesi olan bir Outlook VSTO eklentisi projesinin hedef çatısı .NET Framework 4 ' e veya sonraki bir sürüme değiştirilmişse kodunuzu değiştirmeniz gerekir.
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
ms.workload:
- office
ms.openlocfilehash: 15b212a8b7dde85e66b18b78d356bdb31c62836a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921895"
---
# <a name="update-outlook-form-regions-when-migrated-to-net-framework-45"></a>.NET Framework 4,5 ' e geçirildiğinde Outlook form bölgelerini Güncelleştir

  Bir form bölgesi olan bir Outlook VSTO eklentisi projesinin hedef çatısı [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonraki bir sürümüne değiştiyse, oluşturulan form bölgesi kodunda ve çalışma zamanında belirli form bölgesi sınıflarını Başlatan tüm kodlar üzerinde bazı değişiklikler yapmanız gerekir.

## <a name="update-the-generated-form-region-code"></a>Oluşturulan form bölgesi kodunu Güncelleştir
 Projenin hedef çerçevesi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonraki bir sürümüne değiştirildiyse, oluşturulan form bölgesi kodunu değiştirmeniz gerekir. Yaptığınız değişiklikler, Visual Studio 'da tasarladığınız form bölgeleri ve Outlook 'tan içeri aktardığınız form bölgeleri için farklıdır. Bu form bölgesi türleri arasındaki farklar hakkında daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Visual Studio 'da tasarladığınız bir form bölgesinin oluşturulan kodunu güncelleştirmek için

1. Kod düzenleyicisinde form bölgesi arka plan kod dosyasını açın. Bu dosya *YourFormRegion* olarak adlandırılır. Designer.cs veya *YourFormRegion*. Designer. vb. Bu dosyayı Visual Basic projelerinde görmek için, **Çözüm Gezgini** **tüm dosyaları göster** düğmesine tıklayın.

2. Form bölgesi sınıfının bildirimini yerine öğesinden türeten önce değiştirin <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> `Microsoft.Office.Tools.Outlook.FormRegionControl` .

3. Form bölgesi sınıfının yapıcısını aşağıdaki kod örneklerinde gösterildiği gibi değiştirin.

     Aşağıdaki kod örneği, .NET Framework 3,5 ' i hedefleyen bir projede form bölgesi sınıfının yapıcısını gösterir.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.InitializeComponent();
    }
    ```

     Aşağıdaki kod örneği, bir form bölgesi sınıfının oluşturucusunu, ' i hedefleyen bir projede gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.InitializeComponent();
    }
    ```

4. `InitializeManifest`Metodun imzasını aşağıda gösterildiği gibi değiştirin. Yönteminde kodu değiştirdiğinizden emin olun; Bu kod, tasarımcıda uyguladığınız form bölge ayarlarını temsil eder. Visual C# projelerinde, `Form Region Designer generated code` Bu yöntemi görmek için adlı bölgeyi genişletmeniz gerekir.

     Aşağıdaki kod örneği, `InitializeManifest` .NET Framework 3,5 ' i hedefleyen bir projedeki yönteminin imzasını gösterir.

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)
    {
        // Do not change code in this method.
    }
    ```

     Aşağıdaki kod örneğinde `InitializeManifest` , hedefleyen bir projedeki Signature yöntemi gösterilmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,
        Microsoft.Office.Tools.Outlook.Factory factory)
    {
        // Do not change code in this method.
    }
    ```

5. Projenize yeni bir Outlook form bölgesi öğesi ekleyin. Yeni form bölgesi için arka plan kod dosyasını açın, dosyadaki *YourNewFormRegion* `Factory` ve `WindowFormRegionCollection` sınıflarını bulun ve bu sınıfları panoya kopyalayın.

6. Projenize eklediğiniz yeni form bölgesini silin.

7. Yeniden hedeflenen projede çalışmak üzere güncelleştirdiğiniz form bölgesinin arka plan kod dosyasında, *YourOriginalFormRegion* `Factory` ve `WindowFormRegionCollection` sınıflarını bulun ve yeni form bölgesinden kopyaladığınız kodla değiştirin.

8. *YourNewFormRegion* `Factory` ve `WindowFormRegionCollection` sınıflarında, *YourNewFormRegion* sınıfına yapılan tüm başvuruları arayın ve bunun yerine her bir başvuruyu *YourOriginalFormRegion* sınıfına değiştirin. Örneğin, güncelleştirdiğiniz form bölgesi adlandırılmış ise `SalesDataFormRegion` ve 5. adımda oluşturduğunuz yeni form bölgesi olarak adlandırılmışsa `FormRegion1` , tüm başvurularını `FormRegion1` öğesine değiştirin `SalesDataFormRegion` .

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Outlook 'tan içeri aktardığınız bir form bölgesinin oluşturulan kodunu güncelleştirmek için

1. Kod düzenleyicisinde form bölgesi arka plan kod dosyasını açın. Bu dosya *YourFormRegion* olarak adlandırılır. Designer.cs veya *YourFormRegion*. Designer. vb. Bu dosyayı Visual Basic projelerinde görmek için, **Çözüm Gezgini** **tüm dosyaları göster** düğmesine tıklayın.

2. Form bölgesi sınıfının bildirimini yerine öğesinden türeten önce değiştirin <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> `Microsoft.Office.Tools.Outlook.ImportedFormRegion` .

3. Form bölgesi sınıfının yapıcısını aşağıdaki kod örneklerinde gösterildiği gibi değiştirin.

     Aşağıdaki kod örneği, .NET Framework 3,5 ' i hedefleyen bir projede form bölgesi sınıfının yapıcısını gösterir.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

     Aşağıdaki kod örneği, hedefleyen bir projedeki form bölgesi sınıfının oluşturucusunun imzasını gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

4. `InitializeControls`Form bölgesi sınıfında bir denetimi Başlatan yöntemdeki her kod satırı için, kodu aşağıda gösterildiği gibi değiştirin.

     Aşağıdaki kod örneği, .NET Framework 3,5 ' i hedefleyen bir projede bir denetimin nasıl başlatılacağını göstermektedir. Bu kodda, `GetFormRegionControl` yöntemi döndürülen denetimin türünü belirten bir tür parametresine sahiptir.

    ```vb
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")
    ```

    ```csharp
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");
    ```

     Aşağıdaki kod örneğinde, hedefleyen bir projede bir denetimin nasıl başlatıldığı gösterilmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Bu kodda, <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> yöntemin bir tür parametresi yoktur. Dönüş değerini, başlatmakta olduğunuz denetimin türüne atamalısınız.

    ```vb
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)
    ```

    ```csharp
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");
    ```

5. Projenize yeni bir Outlook form bölgesi öğesi ekleyin. Yeni form bölgesi için arka plan kod dosyasını açın, dosyadaki *YourNewFormRegion* `Factory` ve `WindowFormRegionCollection` sınıflarını bulun ve bu sınıfları panoya kopyalayın.

6. Projenize eklediğiniz yeni form bölgesini silin.

7. Yeniden hedeflenen projede çalışmak üzere güncelleştirdiğiniz form bölgesinin arka plan kod dosyasında, *YourOriginalFormRegion* `Factory` ve `WindowFormRegionCollection` sınıflarını bulun ve yeni form bölgesinden kopyaladığınız kodla değiştirin.

8. *YourNewFormRegion* `Factory` ve `WindowFormRegionCollection` sınıflarında, *YourNewFormRegion* sınıfına yapılan tüm başvuruları arayın ve bunun yerine her bir başvuruyu *YourOriginalFormRegion* sınıfına değiştirin. Örneğin, güncelleştirdiğiniz form bölgesi adlandırılmış ise `SalesDataFormRegion` ve 5. adımda oluşturduğunuz yeni form bölgesi olarak adlandırılmışsa `FormRegion1` , tüm başvurularını `FormRegion1` öğesine değiştirin `SalesDataFormRegion` .

## <a name="instantiate-form-region-classes"></a>Form bölgesi sınıflarını oluştur
 Belirli form bölgesi sınıflarını dinamik olarak örnekleyen herhangi bir kodu değiştirmeniz gerekir. .NET Framework 3,5 ' i hedefleyen projelerde, doğrudan gibi form bölgesi sınıflarının örneğini oluşturabilirsiniz `Microsoft.Office.Tools.Outlook.FormRegionManifest` . [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya daha sonra hedeflenen projelerde, bu sınıflar doğrudan örnek oluşturabileceksiniz arayüzlerdir.

 Projenizin hedef çatısı [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürümüne değiştirilirse, özelliği tarafından sunulan yöntemleri kullanarak arabirimleri örneklemelisiniz `Globals.Factory` . Özelliği hakkında daha fazla bilgi için `Globals.Factory` bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md).

 Aşağıdaki tabloda, veya daha sonra hedeflenen projelerdeki türlerin örneğini oluşturmak için kullanılacak olan form bölgesi türleri ve yöntemi listelenmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

|Tür|Kullanılacak Fabrika yöntemi|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
