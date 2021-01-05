---
title: Dinamik araç penceresi açılıyor | Microsoft Docs
description: Belirli bir kullanıcı arabirimi bağlamı geçerli olduğunda açılan dinamik araç pencereleri hakkında bilgi edinin ve Kullanıcı arabirimi bağlamı artık geçerli olmadığında kapanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12b08f676e02a9023374c709aa18edfc0e8815db
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863512"
---
# <a name="open-a-dynamic-tool-window"></a>Dinamik araç penceresi aç
Araç pencereleri genellikle menüdeki bir komuttan veya eşdeğer bir klavye kısayoluna açılır. Ancak, her zaman belirli bir kullanıcı arabirimi bağlamı geçerli olduğunda açılan bir araç penceresine gerek duyabilirsiniz ve Kullanıcı arabirimi bağlamı artık geçerli olmadığında kapanır. Bu tür araç pencereleri *dinamik* veya *Otomatik görünür* olarak adlandırılır.

> [!NOTE]
> Önceden tanımlanmış UI bağlamlarının bir listesi için bkz <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> ..

 Başlangıçta dinamik bir araç penceresi açmak isterseniz ve oluşturma işlemi başarısız olması durumunda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> arabirimini uygulamanız ve hata koşullarını yöntemde test etmeniz gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> . Kabuğun başlangıçta açılması gereken dinamik bir araç penceresi olduğunu bilmesi için, `SupportsDynamicToolOwner` değeri (1 olarak ayarlanmalıdır) paket kaydımız olarak eklemeniz gerekir. Bu değer standart bir parçası değildir, bu <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> nedenle eklemek için özel bir öznitelik oluşturmanız gerekir. Özel öznitelikler hakkında daha fazla bilgi için bkz. bir [uzantıyı kaydetmek için özel bir kayıt özniteliği kullanma](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).

 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>Bir araç penceresi açmak için kullanın. Araç penceresi gerektiğinde oluşturulur.

> [!NOTE]
> Dinamik bir araç penceresi Kullanıcı tarafından kapatılabilir. Kullanıcının araç penceresini yeniden açmasını sağlamak üzere bir menü komutu oluşturmak istiyorsanız, menü komutunun araç penceresini açan aynı kullanıcı arabirimi bağlamında etkinleştirilmesi ve aksi takdirde devre dışı bırakılması gerekir.

## <a name="to-open-a-dynamic-tool-window"></a>Dinamik bir araç penceresi açmak için

1. **DynamicToolWindow** ADLı bir VSIX projesi oluşturun ve *DynamicWindowPane.cs* adlı bir araç penceresi öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).

2. *DynamicWindowPanePackage.cs* dosyasında, Dynamicwindowbölmesi paket bildirimini bulun. <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> Araç penceresini kaydetmek için ve özniteliklerini ekleyin.

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

     Yukarıdaki öznitelikler, Visual Studio kapatılıp yeniden açıldığı zaman kalıcı olmayan geçici bir pencere olarak DynamicWindowPane adlı araç penceresini kaydeder. DynamicWindowPane, her uygulandığı zaman açılır <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> ve aksi takdirde kapatılır.

3. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir. Araç penceresini görmemelisiniz.

4. Deneysel örnekte bir proje açın. Araç penceresi görünmelidir.
