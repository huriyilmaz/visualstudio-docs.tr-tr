---
title: Proje Özelliklerini Alma | Microsoft Dokümanlar
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ddfd48827bc762c9189f9b7600cfe9200e5c866
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711406"
---
# <a name="get-project-properties"></a>Proje özelliklerini alma

Bu gözden geçirme, proje özelliklerini bir araç penceresinde nasıl görüntülenebildiğini gösterir.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>VSIX Projesi oluşturmak ve bir araç penceresi eklemek için

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSIX dağıtım projesiyle başlar. Adlı `ProjectPropertiesExtension` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir VSIX projesi oluşturun. "vsix" aramasını yaparak **VSIX** proje şablonunu Yeni Proje iletişim kutusunda bulabilirsiniz.

2. Özel Araç Penceresi öğesi şablonu ekleyerek `ProjectPropertiesToolWindow`bir araç penceresi ekleyin. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Yeni **Öğe Ekle iletişim kutusunda,** **Visual C# Items** > **Extensibility'e** gidin ve **Özel Araç Penceresi'ni**seçin. İletişim kutusunun altındaki **Ad** alanında, dosya adını ' `ProjectPropertiesToolWindow.cs`da ' olarak değiştirin Özel bir araç penceresi oluşturma hakkında daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-tool-window.md)

3. Çözümü oluşturun ve hatasız derlediğini doğrulayın.

### <a name="to-display-project-properties-in-a-tool-window"></a>Proje özelliklerini bir araç penceresinde görüntülemek için

1. ProjectPropertiesToolWindowCommand.cs dosyasına, yönergeleri kullanarak aşağıdaki yönergeleri ekleyin.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. *ProjectPropertiesToolWindowControl.xaml'da*varolan düğmeyi kaldırın ve Araç Kutusundan bir TreeView ekleyin. Ayrıca ProjectPropertiesToolWindowControl.xaml.cs *dosyasından* tıklama olay işleyicisi kaldırabilirsiniz.

3. *ProjectPropertiesToolWindowCommand.cs,* projeyi `ShowToolWindow()` açmak ve özelliklerini okumak için yöntemi kullanın, ardından özellikleri TreeView'a ekleyin. ShowToolWindow için kod aşağıdaki gibi görünmelidir:

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create window.");
        }
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        // Get the tree view and populate it if there is a project open.
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;
        TreeView treeView = control.treeView;

        // Reset the TreeView to 0 items.
        treeView.Items.Clear();

        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));
        Projects projects = dte.Solution.Projects;
        if (projects.Count == 0)   // no project is open
        {
            TreeViewItem item = new TreeViewItem();
            item.Name = "Projects";
            item.ItemsSource = new string[]{ "no projects are open." };
            item.IsExpanded = true;
            treeView.Items.Add(item);
            return;
        }

        Project project = projects.Item(1);
        TreeViewItem item1 = new TreeViewItem();
        item1.Header = project.Name + "Properties";
        treeView.Items.Add(item1);

        foreach (Property property in project.Properties)
        {
            TreeViewItem item = new TreeViewItem();
            item.ItemsSource = new string[] { property.Name };
            item.IsExpanded = true;
            treeView.Items.Add(item);
        }
    }
    ```

4. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görünmelidir.

5. Deneysel örnekte, bir proje açın.

6. **Görünüm** > **Diğer Windows'da** **ProjectPropertiesToolWindow'u**tıklatın.

  Takım penceresindeki ağaç denetimini ilk projenin adı ve tüm proje özellikleriyle birlikte görmeniz gerekir.
