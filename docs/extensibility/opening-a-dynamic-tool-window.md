---
title: Dinamik Araç Penceresi Açma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff971f980b0a9b2fb0e22f56fb0ace752829c2c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702256"
---
# <a name="open-a-dynamic-tool-window"></a>Dinamik bir araç penceresi açma
Araç pencereleri genellikle menüdeki bir komuttan veya eşdeğer klavye kısayolundan açılır. Ancak bazen, belirli bir Ara Bilgi bağlamı uygulandığında açılan ve UI bağlamı artık geçerli olmadığında kapanan bir araç penceresine ihtiyacınız olabilir. Bu tür araç pencerelerine *dinamik* veya *otomatik görünür*denir.

> [!NOTE]
> Önceden tanımlanmış UI bağlamlarının listesi <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>için bkz.

 Başlangıçta dinamik bir araç penceresi açmak istiyorsanız ve oluşturmanın başarısız olması mümkünse, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> arabirimi uygulamanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> ve yöntemdeki hata koşullarını test etmeniz gerekir. Shell'in başlangıçta açılması gereken dinamik bir araç penceresine sahip olduğunuzu bilmesi `SupportsDynamicToolOwner` için paket kaydınıza değeri (1'e ayarlanmış) eklemeniz gerekir. Bu değer standardın <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>bir parçası değildir, bu nedenle eklemek için özel bir öznitelik oluşturmanız gerekir. Özel öznitelikler hakkında daha fazla bilgi için [bkz.](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)

 Araç <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> penceresini açmak için kullanın. Araç penceresi gerektiği gibi oluşturulur.

> [!NOTE]
> Dinamik bir araç penceresi kullanıcı tarafından kapatılabilir. Kullanıcının araç penceresini yeniden açabilmesi için bir menü komutu oluşturmak istiyorsanız, menü komutu araç penceresini açan aynı Kullanıcı Arabirimi bağlamında etkinleştirilmeli ve aksi takdirde devre dışı bırakılır.

## <a name="to-open-a-dynamic-tool-window"></a>Dinamik bir araç penceresi açmak için

1. **DynamicToolWindow** adında bir VSIX projesi oluşturun ve *DynamicWindowPane.cs*adlı bir araç penceresi öğesi şablonu ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-tool-window.md)

2. *DynamicWindowPanePackage.cs* dosyasında DynamicWindowPanePackage bildirimini bulun. Araç <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> penceresini kaydetmek için öznitelikleri ve <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> öznitelikleri ekleyin.

    ```vb
    [ProvideToolWindow(typeof(DynamicWindowPane)]
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]
    [Guid(DynamicWindowPanePackage.PackageGuidString)]
    public sealed class DynamicWindowPanePackage : Package
    {. . .}
    ```

     Yukarıdaki öznitelikler, Visual Studio kapatıldığında ve yeniden açıldığında kalıcı olmayan geçici bir pencere olarak DynamicWindowPane adlı araç penceresini kaydeder. DynamicWindowPane uygulandığı nda <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> açılır ve aksi takdirde kapatılır.

3. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görünmelidir. Araç penceresini görmemelisiniz.

4. Deneysel örnekte bir proje açın. Araç penceresi görünmelidir.
