---
title: Komut Uygulaması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a536120c81c154cf894717a2af6a4e048d56e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709575"
---
# <a name="command-implementation"></a>Komut uygulaması
VSPackage'da bir komut uygulamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:

1. *.vsct* dosyasında, bir komut grubu ayarlayın ve ardından komutu ekleyin. Daha fazla bilgi için [Visual Studio komut tablosu (.vsct) dosyalarına](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)bakın.

2. Komutu Visual Studio'ya kaydedin.

3. Komutu uygulayın.

Aşağıdaki bölümlerde komutların nasıl kaydedilip uygulanacağı açıklanmıştır.

## <a name="register-commands-with-visual-studio"></a>Visual Studio ile komutları kaydedin
 Komutunuz bir menüde görünecekse, <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> vspackage'ınıza eklemeniz ve menünün adını veya kaynak kimliğini bir değer olarak kullanmanız gerekir.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Buna ek olarak, komutu <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. VSPackage'ınız <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> <xref:Microsoft.VisualStudio.Shell.Package>türetilmişse yöntemi kullanarak bu hizmeti alabilirsiniz.

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

## <a name="implement-commands"></a>Komutları uygulama
 Komutları uygulamanın birkaç yolu vardır. Her zaman aynı şekilde ve aynı menüde görünen bir komut olan statik bir menü komutu istiyorsanız, önceki bölümdeki örneklerde gösterildiği gibi kullanarak <xref:System.ComponentModel.Design.MenuCommand> komutu oluşturun. Statik bir komut oluşturmak için, komutu yürütmekten sorumlu bir olay işleyicisi sağlamanız gerekir. Komut her zaman etkin ve görünür olduğundan, visual studio için durumunu sağlamak zorunda değildir. Belirli koşullara bağlı olarak bir komutun durumunu değiştirmek istiyorsanız, komutu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> sınıfın bir örneği olarak oluşturabilir ve oluşturucusunda komutu yürütmek `QueryStatus` için bir olay işleyicisi ve komutun durumu değiştiğinde Visual Studio'ya bildirecek bir işleyici sağlayabilirsiniz. Ayrıca bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> komut sınıfının parçası olarak uygulayabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> veya projenin bir parçası olarak bir komut sağlıyorsanız uygulayabilirsiniz. İki arabirim ve <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> sınıfın tümü, Visual Studio'ya komutun durumundaki değişikliği bildiren yöntemler ve komutun yürütülmesini sağlayan diğer yöntemler vardır.

 Bir komut komut hizmetine eklendiğinde, komutlar zincirinden biri haline gelir. Komut için durum bildirimi ve yürütme yöntemlerini uyguladığınızda, yalnızca belirli komutu sağlamaya ve diğer tüm servis taleplerini zincirdeki diğer komutlara geçirmeye özen gösterirsiniz. Komutu (genellikle döndürerek) <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>geçiremezse, Visual Studio düzgün çalışmayı durdurabilir.

## <a name="querystatus-methods"></a>QueryDurum yöntemleri
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Yöntem veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> yöntem uyguluyorsanız, komutun ait olduğu komut kümesinin GUID'sini ve komutun kimliğini denetleyin. Aşağıdaki yönergeleri izleyin:

- GUID tanınmıyorsa, her iki yöntemin de uygulanmasınızı döndürmeniz <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>gerekir.

- Her iki yöntemin uygulamaGUID tanır ancak komutu uygulamadı, o <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>zaman yöntem dönmelidir.

- Her iki yöntemin de uygulamanız hem GUID'i hem de komutu tanıyorsa, yöntem `prgCmds` aşağıdaki <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> bayrakları kullanarak her komutun (parametredeki) komut bayrakları alanını ayarlamalıdır:

  - `OLECMDF_SUPPORTED`: Komut desteklenir.

  - `OLECMDF_INVISIBLE`: Komut görünür olmamalıdır.

  - `OLECMDF_LATCHED`: Komut değiştirildi ve kontrol edilmiş gibi görünüyor.

  - `OLECMDF_ENABLED`: Komut etkinleştirildi.

  - `OLECMDF_DEFHIDEONCTXTMENU`: Kısayol menüsünde görünüyorsa komut gizlenmelidir.

  - `OLECMDF_NINCHED`: Komut bir menü denetleyicisidir ve etkin değildir, ancak açılır menü listesi boş değildir ve hala kullanılabilir. (Bu bayrak nadiren kullanılır.)

- Komut `TextChanges` *.vsct* dosyasında bayrakla tanımlandıysa, aşağıdaki parametreleri ayarlayın:

  - Parametre `rgwz` öğesini `pCmdText` komutun yeni metnine ayarlayın.

  - `cwActual` Parametrenin öğesini `pCmdText` komut dizesinin boyutuna ayarlayın.

Ayrıca, komutunuz özellikle otomasyon işlevlerini işlemek için tasarlanmadıkça, geçerli bağlamın bir otomasyon işlevi olmadığından emin olun.

Belirli bir komutu desteklediğinizi <xref:Microsoft.VisualStudio.VSConstants.S_OK>belirtmek için geri dönün. Diğer tüm komutlar <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>için, geri dönün.

Aşağıdaki örnekte, `QueryStatus` yöntem önce bağlamın bir otomasyon işlevi olmadığından emin olur, sonra doğru komut kümesi GUID ve komut kimliğini bulur. Komutun kendisi etkinleştirilecek ve desteklenecek şekilde ayarlanır. Başka komut desteklenmez.

```csharp
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
 Yöntemin `Exec` uygulanması yöntemin uygulanmasına `QueryStatus` benzer. İlk olarak, bağlamın bir otomasyon işlevi olmadığından emin olun. Ardından, hem GUID hem de komut kimliği için test edin. GUID veya komut kimliği tanınmıyorsa, geri döndü. <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>

 Komutu işlemek için, yürütme <xref:Microsoft.VisualStudio.VSConstants.S_OK> başarılı olursa çalıştırın ve döndürün. Komutunuzun hata algılama ve bildirimsorumludur; bu nedenle, yürütme başarısız olursa bir hata kodu döndürün. Aşağıdaki örnek, yürütme yönteminin nasıl uygulanması gerektiğini göstermektedir.

```csharp
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

## <a name="see-also"></a>Ayrıca bkz.

- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
