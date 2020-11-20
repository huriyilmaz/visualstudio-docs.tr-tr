---
title: Çok örnekli bir araç penceresi oluşturma | Microsoft Docs
description: Birden çok örneğinin aynı anda açılmasını sağlamak üzere bir araç penceresini nasıl değiştireceğinizi öğrenin. Araç pencerelerinin varsayılan olarak yalnızca bir örnek açık olabilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10de60620bcd0b56f251955f478d4d06c984d021
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94973995"
---
# <a name="create-a-multi-instance-tool-window"></a>Çok örnekli bir araç penceresi oluşturma
Bir araç penceresini, birden çok örneğinin aynı anda açılmasını sağlayacak şekilde programlayabilirsiniz. Araç pencerelerinin varsayılan olarak yalnızca bir örnek açık olabilir.

Çok örnekli bir araç penceresi kullandığınızda, aynı anda birkaç ilgili bilgi kaynağını gösterebilirsiniz. Örneğin, <xref:System.Windows.Forms.TextBox> bir programlama oturumu sırasında birçok kod parçacıklarının eşzamanlı olarak kullanılabilmesi için çok örnekli bir araç penceresine çok satırlı bir denetim koyabilirsiniz. Ayrıca, örneğin, <xref:System.Windows.Forms.DataGrid> çeşitli gerçek zamanlı veri kaynaklarının eşzamanlı olarak izlenebilmesi için, bir denetimi ve bir açılan liste kutusunu çok örnekli bir araç penceresine koyabilirsiniz.

## <a name="create-a-basic-single-instance-tool-window"></a>Temel (tek örnekli) araç penceresi oluşturma

1. VSıX şablonunu kullanarak **MultiInstanceToolWindow** adlı bir proje oluşturun ve **MIToolWindow** adlı özel bir araç penceresi öğesi şablonu ekleyin.

    > [!NOTE]
    > Araç penceresiyle uzantı oluşturma hakkında daha fazla bilgi için bkz. [bir araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Araç penceresini çoklu örnek yapın

1. *MIToolWindowPackage.cs* dosyasını açın ve `ProvideToolWindow` özniteliğini bulun. `MultiInstances=true`Aşağıdaki örnekte gösterildiği gibi parametresi:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. *MIToolWindowCommand.cs* dosyasında `ShowToolWindos()` yöntemini bulun. Bu yöntemde, <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> yöntemi çağırın ve `create` bayrağını olarak ayarlayın `false` . böylece, kullanılabilir araç penceresi örnekleri arasında yineleme olacak şekilde bir kullanılabilir `id` .

3. Bir araç penceresi örneği oluşturmak için <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> yöntemini çağırın ve öğesini `id` kullanılabilir bir değere ve `create` bayrağını olarak ayarlayın `true` .

    Varsayılan olarak, `id` yönteminin parametresinin değeri <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> `0` . Bu değer, tek örnekli bir araç penceresi oluşturur. Birden fazla örneğin barındırılması için, her örneğin kendi benzersiz olması gerekir `id` .

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Araç penceresi örneğinin özelliği tarafından döndürülen nesnede yöntemi çağırın <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> .

5. Varsayılan olarak, `ShowToolWindow` araç penceresi öğe şablonu tarafından oluşturulan yöntem tek örnekli bir araç penceresi oluşturur. Aşağıdaki örnek, `ShowToolWindow` birden çok örnek oluşturmak için yönteminin nasıl değiştirileceğini gösterir.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```
