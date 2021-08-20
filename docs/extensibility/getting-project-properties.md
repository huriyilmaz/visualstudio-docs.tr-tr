---
title: Project özellikleri alınıyor | Microsoft Docs
description: Proje özelliklerini bir araç penceresinde görüntülemeyi öğrenin. Bu örnekte, araç penceresindeki ağaç denetimi gösterilmektedir.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 434f45bcf06fc46b9cbafe1b8ecd267619fec405
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125068"
---
# <a name="get-project-properties"></a>Proje özelliklerini al

Bu izlenecek yol, bir araç penceresinde proje özelliklerinin nasıl görüntüleneceğini gösterir.

## <a name="prerequisites"></a>Önkoşullar

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezi ' nden yüklemeyin. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>vsıx Project oluşturmak ve araç penceresi eklemek için

1. her Visual Studio uzantısı, uzantı varlıklarını içeren bir vsıx dağıtım projesiyle başlar. Adlı bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projesi oluşturun `ProjectPropertiesExtension` . vsıx proje şablonunu, **yeni Project** iletişim kutusunda "vsıx" arayarak bulabilirsiniz.

2. Adlı özel bir araç penceresi öğe şablonu ekleyerek bir araç penceresi ekleyin `ProjectPropertiesToolWindow` . **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle iletişim kutusunda**, **Visual C# öğeleri**  >  **genişletilebilirliği** ' ne gidin ve **özel araç penceresi**' ni seçin. İletişim kutusunun alt kısmındaki **ad** alanında, dosya adını olarak değiştirin `ProjectPropertiesToolWindow.cs` . Özel bir araç penceresi oluşturma hakkında daha fazla bilgi için bkz. [bir araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Çözümü oluşturun ve hata olmadan derlendiğini doğrulayın.

### <a name="to-display-project-properties-in-a-tool-window"></a>Proje özelliklerini bir araç penceresinde görüntüleme

1. ProjectPropertiesToolWindowCommand. cs dosyasında, aşağıdaki using yönergelerini ekleyin.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. *ProjectPropertiesToolWindowControl. xaml* dosyasında, var olan düğmeyi kaldırın ve araç kutusundan bir TreeView ekleyin. Ayrıca, Click olay işleyicisini *ProjectPropertiesToolWindowControl. xaml. cs* dosyasından da kaldırabilirsiniz.

3. *ProjectPropertiesToolWindowCommand. cs* dosyasında, bu `ShowToolWindow()` yöntemi kullanarak projeyi açın ve özelliklerini okuyun, sonra da özellikleri TreeView öğesine ekleyin. ShowToolWindow için kod aşağıdaki gibi görünmelidir:

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

6. diğer **görünüm**  >  **Windows** **ProjectPropertiesToolWindow**' ye tıklayın.

  Araç penceresinde ağaç denetimini, ilk projenin adı ve tüm proje özellikleri ile birlikte görmeniz gerekir.
