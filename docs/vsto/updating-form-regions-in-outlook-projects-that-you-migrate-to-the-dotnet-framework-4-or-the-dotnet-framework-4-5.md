---
title: .NET Framework 4.5'e geçirilirken Outlook form bölgelerini güncelleştirme
description: Form bölgelerine sahip bir Outlook VSTO Eklenti projesinin hedef çerçevesi 4 veya daha sonraki bir .NET Framework kodunu değiştirmeniz gerekir.
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
ms.openlocfilehash: 4237b4412a1175260643e7fe3e0ef9c89bb31540
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115011"
---
# <a name="update-outlook-form-regions-when-migrated-to-net-framework-45"></a>.NET Framework 4.5'e geçirilirken Outlook form bölgelerini güncelleştirme

  Form bölgesi olan bir Outlook VSTO Eklenti projesinin hedef çerçevesi veya sonraki bir ile değiştirilirse, oluşturulan form bölgesi kodunda ve çalışma zamanında belirli form bölgesi sınıflarının örneğini oluşturan herhangi bir kodda bazı değişiklikler [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] yapın.

## <a name="update-the-generated-form-region-code"></a>Oluşturulan form bölgesi kodunu güncelleştirme
 Projenin hedef çerçevesi veya sonrası olarak [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] değiştirilirse, oluşturulan form bölgesi kodunu değiştirebilirsiniz. Yaptığınız değişiklikler, Visual Studio'den içe aktardı Visual Studio form bölgeleri için Outlook. Bu tür form bölgeleri arasındaki farklar hakkında daha fazla bilgi için [bkz. Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Bir form bölgesi için oluşturulan kodu güncelleştirmek için Visual Studio

1. Form bölgesi arka arkasındaki kod dosyasını kod düzenleyicisinde açın. Bu dosya *YourFormRegion olarak adlandırılmıştır.* Designer.cs veya *YourFormRegion*. Tasarımcı.vb. Bu dosyayı projelerde Visual Basic için, dosyanın **içinde Tüm** Dosyaları Göster **düğmesine Çözüm Gezgini.**

2. yerine türetmesi için form bölgesi sınıfının <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> bildirimini `Microsoft.Office.Tools.Outlook.FormRegionControl` değiştirme.

3. Form bölgesi sınıfının oluşturucusu aşağıdaki kod örneklerde gösterildiği gibi değişiklik yapın.

     Aşağıdaki kod örneği, 3.5'i hedef alan bir projede form .NET Framework sınıfını gösterir.

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

     Aşağıdaki kod örneği, hedefleyen bir proje içinde form bölgesi sınıfının oluşturucusu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] gösterir.

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

4. Yönteminin imzasını `InitializeManifest` aşağıda gösterildiği gibi değiştirme. yönteminde kodu değiştirmeyebilirsiniz; Bu kod, tasarımcıda uygulanan form bölgesi ayarlarını temsil eder. Visual C# projelerinde, bu yöntemi görmek için adlı `Form Region Designer generated code` bölgeyi genişletmeniz gerekir.

     Aşağıdaki kod örneği, 3.5'i hedef alan bir projede `InitializeManifest` .NET Framework gösterir.

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

     Aşağıdaki kod örneği, hedef `InitializeManifest` alan bir projede imza yöntemini [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] gösterir.

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

5. Projenize yeni Outlook Form Bölgesi öğesi ekleyin. Yeni form bölgesi için arkadaki kod dosyasını açın, dosyadaki *YourNewFormRegion* ve sınıflarını bulun ve bu `Factory` `WindowFormRegionCollection` sınıfları Panoya kopyalayın.

6. Projenize eklenen yeni form bölgesini silin.

7. Yeniden hedefli projede çalışmak için güncelleştiriyorsanız form bölgesi arka kod dosyasında *YourOriginalFormRegion* ve sınıflarını bulun ve bunları yeni form bölgesinden kopyalanan kodla `Factory` `WindowFormRegionCollection` değiştirin.

8. *YourNewFormRegion* ve sınıflarında YourNewFormRegion sınıfına yapılan tüm başvuruları arayın ve her bir başvuru için `Factory` `WindowFormRegionCollection` *yourOriginalFormRegion* sınıfını kullanın.  Örneğin, güncelleştiriyorsanız ve 5. adımda oluşturduğunuz yeni form bölgesi olarak adlandırılmışsa tüm başvurularını olarak `SalesDataFormRegion` `FormRegion1` `FormRegion1` `SalesDataFormRegion` değiştirebilirsiniz.

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Bir form bölgesinden içe aktarılmış form bölgesi için oluşturulan kodu Outlook

1. Form bölgesi arka arkasındaki kod dosyasını kod düzenleyicisinde açın. Bu dosya *YourFormRegion olarak adlandırılmıştır.* Designer.cs veya *YourFormRegion*. Tasarımcı.vb. Bu dosyayı projelerde Visual Basic için, dosyanın **içinde Tüm** Dosyaları Göster **düğmesine Çözüm Gezgini.**

2. yerine türetmesi için form bölgesi sınıfının <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> bildirimini `Microsoft.Office.Tools.Outlook.ImportedFormRegion` değiştirme.

3. Form bölgesi sınıfının oluşturucusu aşağıdaki kod örneklerde gösterildiği gibi değişiklik yapın.

     Aşağıdaki kod örneği, 3.5'i hedef alan bir projede form .NET Framework sınıfını gösterir.

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

     Aşağıdaki kod örneği, hedefleyen bir proje içinde form bölgesi sınıfının oluşturucuslarının imzasını [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] gösterir.

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

4. form bölgesi sınıfında bir denetim başlatan yönteminde her kod `InitializeControls` satırı için, kodu aşağıda gösterildiği gibi değiştirebilirsiniz.

     Aşağıdaki kod örneği, 3.5'i hedef alan bir projede .NET Framework başlatmayı gösterir. Bu kodda `GetFormRegionControl` yöntemi, döndürülen denetimin türünü belirten bir tür parametresine sahip olur.

    ```vb
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")
    ```

    ```csharp
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");
    ```

     Aşağıdaki kod örneğinde, hedefli bir projede denetimin nasıl başlatılmış olduğu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] gösterir. Bu kodda <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> yönteminin bir tür parametresi yok. Dönüş değerini, başlatan denetimin türüne yazmalısiniz.

    ```vb
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)
    ```

    ```csharp
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");
    ```

5. Projenize yeni Outlook Form Bölgesi öğesi ekleyin. Yeni form bölgesi için arkadaki kod dosyasını açın, dosyadaki *YourNewFormRegion* ve sınıflarını bulun ve bu `Factory` `WindowFormRegionCollection` sınıfları Panoya kopyalayın.

6. Projenize eklenen yeni form bölgesini silin.

7. Yeniden hedefli projede çalışmak için güncelleştiriyorsanız form bölgesi arka kod dosyasında *YourOriginalFormRegion* ve sınıflarını bulun ve bunları yeni form bölgesinden kopyalanan kodla `Factory` `WindowFormRegionCollection` değiştirin.

8. *YourNewFormRegion* ve sınıflarında YourNewFormRegion sınıfına yapılan tüm başvuruları arayın ve her bir başvuru için `Factory` `WindowFormRegionCollection` *yourOriginalFormRegion* sınıfını kullanın.  Örneğin, güncelleştiriyorsanız ve 5. adımda oluşturduğunuz yeni form bölgesi olarak adlandırılmışsa tüm başvurularını olarak `SalesDataFormRegion` `FormRegion1` `FormRegion1` `SalesDataFormRegion` değiştirebilirsiniz.

## <a name="instantiate-form-region-classes"></a>Form bölgesi sınıflarını örneği oluşturma
 Belirli form bölgesi sınıflarını dinamik olarak örnek alan herhangi bir kodu değiştirmeniz gerekir. 3.5'.NET Framework hedef alan projelerde, doğrudan gibi form bölgesi sınıflarını `Microsoft.Office.Tools.Outlook.FormRegionManifest` örnekleyebilirsiniz. veya sonraki bir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sonrakini hedef alan projelerde, bu sınıflar doğrudan örnekleyemini alamzın arabirimlerdir.

 Projenizin hedef çerçevesi veya sonraki bir sonraki ile değiştirilirse, özelliği tarafından sağlanan yöntemleri kullanarak [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] arabirimleri `Globals.Factory` örnekleniz gerekir. özelliği hakkında daha fazla `Globals.Factory` bilgi için [bkz. Office projelerinde nesnelere genel erişim.](../vsto/global-access-to-objects-in-office-projects.md)

 Aşağıdaki tabloda form bölgesi türleri ve veya sonrakini hedef alan projelerde türlerin örneğini oluşturmak için kullanılan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] yöntem listelemektedir.

|Tür|Kullanmak için fabrika yöntemi|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerini .NET Framework 4 veya sonraki bir 4.](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
