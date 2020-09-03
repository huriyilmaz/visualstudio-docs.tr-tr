---
title: Komut uygulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a208fabd3d205793763698cde0f6fe367c7bb8b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195054"
---
# <a name="command-implementation"></a>Komut Uygulama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir VSPackage içinde bir komut uygulamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:  
  
1. . Vsct dosyasında, bir komut grubu ayarlayın ve ardından komutunu ekleyin. Daha fazla bilgi için bkz [. Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2. Komutu Visual Studio ile kaydedin.  
  
3. Komutunu uygulayın.  
  
   Aşağıdaki bölümlerde komutları kaydetme ve uygulama işlemlerinin nasıl yapılacağı açıklanmaktadır.  
  
## <a name="registering-commands-with-visual-studio"></a>Visual Studio ile komutları kaydetme  
 Komutunuz bir menüde yer alıyorsa, öğesini <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage 'a eklemeniz ve menünün adı ya da kaynak kimliği değeri olarak kullanmanız gerekir.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Ayrıca, komutunu ile kaydetmeniz gerekir <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> . <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>VSPackage, öğesinden türetildiyse yöntemini kullanarak bu hizmeti alabilirsiniz <xref:Microsoft.VisualStudio.Shell.Package> .  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Uygulama komutları  
 Komutları uygulamak için çeşitli yollar vardır. Her zaman aynı şekilde görüntülenen ve aynı menüdeki bir komut olan statik bir menü komutu istiyorsanız, <xref:System.ComponentModel.Design.MenuCommand> önceki bölümdeki örneklerde gösterildiği gibi kullanarak komutunu oluşturun. Statik bir komut oluşturmak için, komutu yürütmeden sorumlu bir olay işleyicisi sağlamanız gerekir. Komut her zaman etkin ve görünür olduğundan, durumunu Visual Studio 'ya sağlamanız gerekmez. Belirli koşullara bağlı olarak bir komutun durumunu değiştirmek istiyorsanız, sınıfının bir örneği olarak komutunu oluşturabilir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ve oluşturucusunda, komutun durumu değiştiğinde Visual Studio 'ya bildirim için bir olay işleyicisi ve bir sorgu durum işleyicisi sağlayabilirsiniz. Ayrıca <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , bir komut sınıfının parçası olarak uygulayabilir veya bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projenin parçası olarak bir komut sağlıyorsanız uygulayabilirsiniz. İki arabirim ve <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> sınıf hepsi, Visual Studio 'yu bir komutun durumunda bir değişikliğe bildiren yöntemlere ve komutun yürütülmesini sağlayan diğer yöntemlere sahiptir.  
  
 Komut hizmetine bir komut eklendiğinde, bir komut zincirinden biri olur. Komut için durum bildirimi ve yürütme yöntemlerini uyguladığınızda, yalnızca söz konusu komut için sağlamayı ve diğer tüm durumları zincirdeki diğer komutlara geçirmek için dikkatli olmanız gerekir. Komutuna (genellikle döndürerek) geçiş gerçekleştiremezseniz <xref:Microsoft.VisualStudio.OLE.Interop.Constants> , Visual Studio düzgün şekilde çalışmayı durdurabilir.  
  
## <a name="query-status-methods"></a>Sorgu durumu yöntemleri  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>Yöntemini veya yöntemini uygulamadıysanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> , komutun ait olduğu komut kümesinin GUID 'ini ve komutun kimliğini denetleyin. Aşağıdaki yönergeleri izleyin:  
  
- GUID tanınmazsa, her iki yöntemin uygulamanız döndürmelidir <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
- Her iki yöntemin uygulamanız GUID 'ı tanır ancak komutu gerçekten uygulamamışsa, Yöntemi döndürmelidir <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
- Her iki yöntemin uygulamanız hem GUID hem de komutunu tanırsa, yöntemi aşağıdaki bayrakları kullanarak her komutun (parametresinde) komut bayrakları alanını ayarlamış olmalıdır `prgCmds` :  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Eğer komut destekleniyorsa.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> komutun görünür olmaması gerekir.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Eğer komut açık olarak işaretlenmişse ve işaretliyse görünüyorsa.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> komut etkinse.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> bir kısayol menüsünde görünürse komutun gizlenmesi gerekir.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> komut bir menü denetleyicisiyse ve etkin değilse, ancak açılan menü listesi boş değildir ve hala kullanılabilir olur. (Bu bayrak nadiren kullanılır.)  
  
- Komut. vsct dosyasında `TextChanges` bayrağıyla tanımlanmışsa, aşağıdaki parametreleri ayarlayın:  
  
  - `rgwz` `pCmdText` Parametresinin öğesini komutun yeni metnine ayarlayın.  
  
  - `cwActual` `pCmdText` Parametresinin öğesini komut dizesinin boyutuna ayarlayın.  
  
  Ayrıca, komutunuz Otomasyon işlevlerini işlemek için özel olarak hedeflenmediği takdirde, geçerli bağlamın bir Otomasyon işlevi olmadığından emin olun.  
  
  Belirli bir komutu destekleistediğinizi belirtmek için döndürün <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Diğer tüm komutlar için döndürün <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
  Aşağıdaki örnekte, sorgu-durum yöntemi önce bağlamın bir Otomasyon işlevi olmadığından emin olur, ardından doğru komut kümesi GUID 'INI ve komut KIMLIĞINI bulur. Komutun kendisi etkinleştirilir ve desteklenir olarak ayarlanır. Başka komut desteklenmez.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Yürütme yöntemleri  
 Execute yönteminin uygulanması sorgu-durum yönteminin uygulamasına benzer. İlk olarak, bağlamın bir Otomasyon işlevi olmadığından emin olun. Ardından hem GUID hem de komut KIMLIĞI için test edin. GUID veya komut KIMLIĞI tanınmazsa, döndürün <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
 Komutu işlemek için yürütün ve <xref:Microsoft.VisualStudio.VSConstants.S_OK> yürütme başarılı olursa döndürün. Komut, hata algılama ve bildirimden sorumludur; Bu nedenle, yürütme başarısız olursa bir hata kodu döndürün. Aşağıdaki örnek, yürütme yönteminin nasıl uygulanması gerektiğini gösterir.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
