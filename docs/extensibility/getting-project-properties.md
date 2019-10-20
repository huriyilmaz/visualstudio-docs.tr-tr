---
title: Proje özelliklerini alma | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cac5c55dd8fdeb1ba231d144d94c8be9b680cc6e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633163"
---
# <a name="get-project-properties"></a>Proje özelliklerini al

Bu izlenecek yol, bir araç penceresinde proje özelliklerinin nasıl görüntüleneceğini gösterir.

## <a name="prerequisites"></a>Prerequisites

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Bir VSıX projesi oluşturmak ve araç penceresi eklemek için

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSıX dağıtım projesiyle başlar. @No__t_1 adlı bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSıX projesi oluşturun. "VSIX" araması yaparak VSıX proje şablonunu **Yeni proje** iletişim kutusunda bulabilirsiniz.

2. @No__t_0 adlı özel bir araç penceresi öğe şablonu ekleyerek bir araç penceresi ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve  > **Yeni öğe** **Ekle** ' yi seçin. **Yeni öğe Ekle iletişim kutusunda** **görsel C# öğeler**  > **genişletilebilirlik** ' e gidin ve **özel araç penceresi**' ni seçin. İletişim kutusunun alt kısmındaki **ad** alanında, dosya adını `ProjectPropertiesToolWindow.cs` değiştirin. Özel bir araç penceresi oluşturma hakkında daha fazla bilgi için bkz. [bir araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Çözümü oluşturun ve hata olmadan derlendiğini doğrulayın.

### <a name="to-display-project-properties-in-a-tool-window"></a>Proje özelliklerini bir araç penceresinde görüntüleme

1. ProjectPropertiesToolWindowCommand.cs dosyasında, aşağıdaki using yönergelerini ekleyin.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. *ProjectPropertiesToolWindowControl. xaml*dosyasında, var olan düğmeyi kaldırın ve araç kutusundan bir TreeView ekleyin. Ayrıca, Click olay işleyicisini *ProjectPropertiesToolWindowControl.xaml.cs* dosyasından kaldırabilirsiniz.

3. *ProjectPropertiesToolWindowCommand.cs*' de, projeyi açmak ve özelliklerini okumak için `ShowToolWindow()` yöntemini kullanın, sonra özellikleri TreeView öğesine ekleyin. ShowToolWindow için kod aşağıdaki gibi görünmelidir:

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

4. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir.

5. Deneysel örnekte bir proje açın.

6. **Görünüm**  > **diğer pencereler** **ProjectPropertiesToolWindow**' e tıklayın.

  Araç penceresinde ağaç denetimini, ilk projenin adı ve tüm proje özellikleri ile birlikte görmeniz gerekir.
