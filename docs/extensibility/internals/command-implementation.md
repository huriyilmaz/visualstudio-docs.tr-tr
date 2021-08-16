---
title: Komut Uygulama | Microsoft Docs
description: Visual Studio'de komut uygulaması, VSPackage'da komut grubu ayarlama, buna komut ekleme, komutu kaydetme ve uygulama hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2e9ba7dcaf1f9e2f0e98e7cbb773256d117fcb47edf49d9b8f9815c985156b38
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414668"
---
# <a name="command-implementation"></a>Komut uygulaması
VSPackage'da komut uygulamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:

1. *.vsct dosyasında* bir komut grubu ayarlayın ve komutu buna ekleyin. Daha fazla bilgi için [bkz. Visual Studio tablosu (.vsct) dosyaları.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

2. Komutu Visual Studio.

3. komutunu uygulama.

Aşağıdaki bölümlerde, komutları kaydetme ve uygulama açıklanmaktadır.

## <a name="register-commands-with-visual-studio"></a>Komutları Visual Studio
 Komutunuz bir menüde görünecekse, VSPackage'nıza eklemeniz ve menü adını veya kaynak kimliğini değer <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> olarak kullansanız gerekir.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Ayrıca, komutunu ile <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> kaydetmelisiniz. VSPackage'nız 'den <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> türetildi ise yöntemini kullanarak bu hizmeti <xref:Microsoft.VisualStudio.Shell.Package> eldeabilirsiniz.

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
 Komutları uygulamanın birkaç yolu vardır. Her zaman aynı şekilde ve aynı menüde görünen bir komut olan statik menü komutunu kullanmak için, önceki bölümdeki örneklerde gösterildiği gibi kullanarak <xref:System.ComponentModel.Design.MenuCommand> komutunu oluşturun. Statik bir komut oluşturmak için, komutu yürütmekle sorumlu bir olay işleyicisi sağlayabilirsiniz. Komut her zaman etkin ve görünür olduğundan, komut için durumunu Visual Studio. Belirli koşullara bağlı olarak bir komutun durumunu değiştirmek için, komutu sınıfın bir örneği olarak oluşturabilir ve oluşturucusu içinde, komutu yürütmek için bir olay işleyicisi ve komutun durumu değişse Visual Studio bildirmek için bir işleyici <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> `QueryStatus` sebilirsiniz. Komut sınıfının bir parçası olarak da uygulayabilirsiniz veya bir projenin parçası olarak komut <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> sağlıyorsanız bunu da gerçekleştirebilirsiniz. İki arabirim ve sınıfının hepsinde, bir Visual Studio durumundaki bir değişikliği bildiren yöntemler ve komutun yürütülmesini sağlayan <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> diğer yöntemler vardır.

 Komut hizmetine bir komut ekleniyorsa, bir komut zinciri haline gelir. Komut için durum bildirimi ve yürütme yöntemlerini uygulamaya alırken, yalnızca bu komut için sağlamayı ve diğer tüm durumları zincirde diğer komutlara geçirebilirsiniz. komutuna geçemiyorsanız (genellikle <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> döndürerek), Visual Studio çalışmayı durdurabilir.

## <a name="querystatus-methods"></a>QueryStatus yöntemleri
 yöntemini veya yöntemini uygulayıyorsanız, komutun ait olduğu komut kümesi GUID'ini ve komutun <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> kimliğini kontrol edin. Şu yönergeleri izleyin:

- GUID tanınmıyorsa, her iki yöntemden birini uygulamanız dönüş <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP> gerekir.

- Her iki yöntemin de uygulanması GUID'i tanısa ama komutu uygulamamışsa, yöntemi tarafından dönüş <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> gerekir.

- Herhangi bir yöntemin uygulaması hem GUID'i hem de komutu tanırsa, yöntemi aşağıdaki bayrakları kullanarak her komutun komut bayrakları alanını (parametresinde) `prgCmds` <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> ayarlaması gerekir:

  - `OLECMDF_SUPPORTED`: Komut de destekler.

  - `OLECMDF_INVISIBLE`: Komut görünür durumda olmayacaktır.

  - `OLECMDF_LATCHED`: Komut açık olarak açılır ve denetlendi gibi görünür.

  - `OLECMDF_ENABLED`: Komut etkindir.

  - `OLECMDF_DEFHIDEONCTXTMENU`: Komut bir kısayol menüsünde görünüyorsa gizlenir.

  - `OLECMDF_NINCHED`: Komut bir menü denetleyicisidir ve etkin değildir, ancak açılan menü listesi boş değildir ve hala kullanılabilir durumdadır. (Bu bayrak nadiren kullanılır.)

- Komut *.vsct* dosyasında bayrağıyla `TextChanges` tanımlanmışsa aşağıdaki parametreleri ayarlayın:

  - parametresinin `rgwz` öğesini `pCmdText` komutun yeni metnine ayarlayın.

  - parametresinin `cwActual` öğesini `pCmdText` komut dizesinin boyutuna ayarlayın.

Ayrıca, komutunuz özellikle otomasyon işlevlerini işlemeye yönelik değilse geçerli bağlamın bir otomasyon işlevi olduğundan emin olun.

Belirli bir komutu destekleyesiniz belirtmek için komutunu geri <xref:Microsoft.VisualStudio.VSConstants.S_OK> yazın. Diğer tüm komutlar için <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> dönüş.

Aşağıdaki örnekte, yöntemi önce bağlamın bir otomasyon işlevi olduğundan emin olur, ardından doğru komut kümesi `QueryStatus` GUID'lerini ve komut kimliğini bulur. Komutun kendisi etkin ve destekli olarak ayarlanır. Başka hiçbir komut desteklenmiyor.

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
 Yöntemin `Exec` uygulanması, yönteminin uygulanmasına `QueryStatus` benzer. İlk olarak bağlamın bir otomasyon işlevi olduğundan emin olun. Ardından hem GUID hem de komut kimliği için testte bulundurabilirsiniz. GUID veya komut kimliği tanınmıyorsa, <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> yazın.

 Komutu işlemek için yürütün ve yürütme <xref:Microsoft.VisualStudio.VSConstants.S_OK> başarılı olursa geri döner. Komutunuz hata algılama ve bildirimden sorumludur; bu nedenle, yürütme başarısız olursa bir hata kodu döndürür. Aşağıdaki örnekte yürütme yönteminin nasıl uygulanması gerektiği açıklanır.

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

- [VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
