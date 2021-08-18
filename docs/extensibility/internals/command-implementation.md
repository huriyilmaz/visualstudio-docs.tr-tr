---
title: Komut uygulama | Microsoft Docs
description: Visual Studio 'de komut uygulaması hakkında bilgi edinin, vspackage 'ta bir komut grubunu ayarlama, bir komut ekleme, komutu kaydetme ve uygulamayı uygulama hakkında bilgi edinin.
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
ms.openlocfilehash: 76cb43ec2df05480563f0f7f70e1e4fbecbf44c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095029"
---
# <a name="command-implementation"></a>Komut uygulama
Bir VSPackage içinde bir komut uygulamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:

1. *. Vsct* dosyasında, bir komut grubu ayarlayın ve ardından komutunu ekleyin. daha fazla bilgi için bkz. [Visual Studio komut tablosu (. vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

2. Komutu Visual Studio kaydedin.

3. Komutunu uygulayın.

Aşağıdaki bölümlerde komutları kaydetme ve uygulama işlemlerinin nasıl yapılacağı açıklanmaktadır.

## <a name="register-commands-with-visual-studio"></a>Komutları Visual Studio Kaydet
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

## <a name="implement-commands"></a>Komutları Uygula
 Komutları uygulamak için çeşitli yollar vardır. Her zaman aynı şekilde görüntülenen ve aynı menüdeki bir komut olan statik bir menü komutu istiyorsanız, <xref:System.ComponentModel.Design.MenuCommand> önceki bölümdeki örneklerde gösterildiği gibi kullanarak komutunu oluşturun. Statik bir komut oluşturmak için, komutu yürütmeden sorumlu bir olay işleyicisi sağlamanız gerekir. Komut her zaman etkin ve görünür olduğundan, durumunu Visual Studio sağlamanız gerekmez. belirli koşullara bağlı olarak bir komutun durumunu değiştirmek istiyorsanız, sınıfının bir örneği olarak komutunu oluşturabilir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ve oluşturucusunda, komutun durumu değiştiğinde Visual Studio bildirimi için bir olay işleyicisi sağlayabilirsiniz ve bir `QueryStatus` işleyici sağlayabilirsiniz. Ayrıca <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , bir komut sınıfının parçası olarak uygulayabilir veya bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projenin parçası olarak bir komut sağlıyorsanız uygulayabilirsiniz. iki arabirim ve <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> sınıf hepsi, bir komutun durumundaki bir değişikliğin Visual Studio bildiren yöntemlere ve komutun yürütülmesini sağlayan diğer yöntemlere sahiptir.

 Komut hizmetine bir komut eklendiğinde, bir komut zincirinden biri olur. Komut için durum bildirimi ve yürütme yöntemlerini uyguladığınızda, yalnızca söz konusu komut için sağlamayı ve diğer tüm durumları zincirdeki diğer komutlara geçirmek için dikkatli olmanız gerekir. komutuna (genellikle döndürerek) geçiş gerçekleştiremezseniz <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> , Visual Studio düzgün şekilde çalışmayı durdurabilir.

## <a name="querystatus-methods"></a>QueryStatus yöntemleri
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>Yöntemini veya yöntemini uygulamadıysanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> , komutun ait olduğu komut kümesinin GUID 'ini ve komutun kimliğini denetleyin. Şu yönergeleri izleyin:

- GUID tanınmazsa, her iki yöntemin uygulamanız döndürmelidir <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP> .

- Her iki yöntemin uygulamanız GUID 'ı tanır ancak komutunu uygulamadıysanız, Yöntemi döndürmelidir <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

- Her iki yöntemin uygulamanız hem GUID hem de komutunu tanırsa, yöntemi aşağıdaki bayrakları kullanarak her komutun (parametresinde) komut bayrakları alanını ayarlamış olmalıdır `prgCmds` <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> :

  - `OLECMDF_SUPPORTED`: Komut destekleniyor.

  - `OLECMDF_INVISIBLE`: Komut görünür olmamalıdır.

  - `OLECMDF_LATCHED`: Komut açık ve işaretli olarak görünüyor.

  - `OLECMDF_ENABLED`: Komut etkin.

  - `OLECMDF_DEFHIDEONCTXTMENU`: Kısayol menüsünde görünürse komutun gizlenmesi gerekir.

  - `OLECMDF_NINCHED`: Komut bir menü denetleyicisi ve etkin değil, ancak açılan menü listesi boş değil ve hala kullanılabilir. (Bu bayrak nadiren kullanılır.)

- Komut *. vsct* dosyasında `TextChanges` bayrağıyla tanımlanmışsa, aşağıdaki parametreleri ayarlayın:

  - `rgwz` `pCmdText` Parametresinin öğesini komutun yeni metnine ayarlayın.

  - `cwActual` `pCmdText` Parametresinin öğesini komut dizesinin boyutuna ayarlayın.

Ayrıca, komutunuz Otomasyon işlevlerini işlemek için özel olarak hedeflenmediği takdirde, geçerli bağlamın bir Otomasyon işlevi olmadığından emin olun.

Belirli bir komutu destekleistediğinizi belirtmek için döndürün <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Diğer tüm komutlar için döndürün <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

Aşağıdaki örnekte, `QueryStatus` yöntemi önce bağlamın bir Otomasyon işlevi olmadığından emin olur, ardından doğru komut kümesi GUID 'ini ve komut kimliğini bulur. Komutun kendisi etkinleştirilir ve desteklenir olarak ayarlanır. Başka komut desteklenmez.

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
 `Exec`Yönteminin uygulanması metodun uygulamasına benzer `QueryStatus` . İlk olarak, bağlamın bir Otomasyon işlevi olmadığından emin olun. Ardından, hem GUID hem de komut KIMLIĞI için test edin. GUID veya komut KIMLIĞI tanınmazsa, döndürün <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

 Komutu işlemek için yürütün ve <xref:Microsoft.VisualStudio.VSConstants.S_OK> yürütme başarılı olursa döndürün. Komut, hata algılama ve bildirimden sorumludur; Bu nedenle, yürütme başarısız olursa bir hata kodu döndürün. Aşağıdaki örnek, yürütme yönteminin nasıl uygulanması gerektiğini gösterir.

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

- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
