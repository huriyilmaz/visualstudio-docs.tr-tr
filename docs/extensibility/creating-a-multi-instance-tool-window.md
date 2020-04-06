---
title: Çok Örnekli Araç Penceresi Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739619"
---
# <a name="create-a-multi-instance-tool-window"></a>Çok örnekli araç penceresi oluşturma
Bir araç penceresini, birden çok örneğinaynı anda açAbilmesi için programlayabilirsiniz. Varsayılan olarak, araç pencerelerinden yalnızca bir örnek açık olabilir.

Çok örnekli bir araç penceresi kullandığınızda, aynı anda birkaç ilgili bilgi kaynağı gösterebilirsiniz. Örneğin, çok örnekli bir <xref:System.Windows.Forms.TextBox> araç penceresine çok satırlı bir denetim koyarak programlama oturumu sırasında aynı anda birden çok kod parçacıkları kullanılabilir. Ayrıca, örneğin, birden çok <xref:System.Windows.Forms.DataGrid> örnekli araç penceresine bir denetim ve açılır liste kutusu koyabilirsiniz, böylece birkaç gerçek zamanlı veri kaynağı aynı anda izlenebilir.

## <a name="create-a-basic-single-instance-tool-window"></a>Temel (tek örnekli) araç penceresi oluşturma

1. VSIX şablonu kullanarak **MultiInstanceToolWindow** adında bir proje oluşturun ve **MIToolWindow**adlı özel bir araç penceresi öğesi şablonu ekleyin.

    > [!NOTE]
    > Araç penceresi yle uzantı oluşturma hakkında daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="make-a-tool-window-multi-instance"></a>Bir araç penceresi çok örnekli yapma

1. *MIToolWindowPackage.cs* dosyasını `ProvideToolWindow` açın ve özniteliği bulun. ve `MultiInstances=true` parametre, aşağıdaki örnekte gösterildiği gibi:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. *MIToolWindowCommand.cs* dosyasında `ShowToolWindos()` yöntemi bulun. Bu yöntemde, <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> yöntemi çağırın `create` ve `false` kullanılabilir bulunana kadar `id` varolan araç penceresi örnekleri arasında yinelenecek şekilde bayrağını ayarlayın.

3. Bir araç penceresi örneği oluşturmak <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> için, `id` yöntemi arayın ve `create` kullanılabilir `true`bir değer ve bayrağını ' a ayarlayın.

    Varsayılan olarak, `id` <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> yöntemin parametre değeri `0`. Bu değer, tek örnekli bir araç penceresi yapar. Birden fazla örneğin barındırılması için her örneğin kendine `id`özgü olması gerekir.

4. Araç <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> penceresi örneğinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> özelliği tarafından döndürülen nesne üzerindeki yöntemi çağırın.

5. Varsayılan olarak, `ShowToolWindow` araç penceresi öğesi şablonu tarafından oluşturulan yöntem tek örnekli bir araç penceresi oluşturur. Aşağıdaki örnek, yöntemin `ShowToolWindow` birden çok örnek oluşturmak için nasıl değiştirileceğigösterilmektedir.

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
