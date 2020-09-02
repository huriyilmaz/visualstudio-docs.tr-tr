---
title: Dinamik araç penceresi açılıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09b81294abc708cf7616dad03b5dd7333d6a1719
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64816859"
---
# <a name="opening-a-dynamic-tool-window"></a>Dinamik Araç Penceresini Açma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Araç pencereleri genellikle menüdeki bir komuttan veya eşdeğer bir klavye kısayoluna açılır. Ancak, her zaman belirli bir kullanıcı arabirimi bağlamı geçerli olduğunda açılan bir araç penceresine gerek duyabilirsiniz ve Kullanıcı arabirimi bağlamı artık geçerli olmadığında kapanır. Bunlar gibi araç pencereleri *dinamik* veya *Otomatik görünür*olarak adlandırılır.  
  
> [!NOTE]
> Önceden tanımlanmış UI bağlamlarının bir listesi için bkz <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> .. İçin  
  
 Başlangıçta dinamik bir araç penceresi açmak isterseniz ve oluşturma işlemi başarısız olması durumunda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> arabirimini uygulamanız ve hata koşullarını yöntemde test etmeniz gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> . Kabuğun başlangıçta açılması gereken dinamik bir araç penceresi olduğunu bilmesi için, `SupportsDynamicToolOwner` değeri (1 olarak ayarlanmalıdır) paket kaydımız olarak eklemeniz gerekir. Bu değer standart bir parçası değildir, bu <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> nedenle eklemek için özel bir öznitelik oluşturmanız gerekir. Özel öznitelikler hakkında daha fazla bilgi için bkz. bir [uzantıyı kaydetmek Için özel bir kayıt özniteliği kullanma](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>Bir araç penceresi açmak için kullanın. Araç penceresi gerektiğinde oluşturulur.  
  
> [!NOTE]
> Dinamik bir araç penceresi Kullanıcı tarafından kapatılabilir. Kullanıcının araç penceresini yeniden açmasını sağlamak üzere bir menü komutu oluşturmak istiyorsanız, menü komutunun araç penceresini açan aynı kullanıcı arabirimi bağlamında etkinleştirilmesi ve aksi takdirde devre dışı bırakılması gerekir.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Dinamik bir araç penceresi açmak için  
  
1. **DynamicToolWindow** ADLı bir VSIX projesi oluşturun ve **DynamicWindowPane.cs**adlı bir araç penceresi öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir araç penceresi Ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2. DynamicWindowPanePackage.cs dosyasında, Dynamicwindowbölmesi paket bildirimini bulun. <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>Araç penceresini kaydetmek için ve T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute özniteliklerini ekleyin.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Bu, DynamicWindowPane adlı araç penceresini, Visual Studio kapatılıp yeniden açıldığında kalıcı olmayan geçici bir pencere olarak kaydeder. DynamicWindowPane, her uygulandığı zaman açılır <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> ve aksi takdirde kapatılır.  
  
3. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir. Araç penceresini görmemelisiniz.  
  
4. Deneysel örnekte bir proje açın. Araç penceresi görünmelidir.
