---
title: VSPackage Paketi ile Uzantı | Microsoft Docs
description: İleti kutusu göstermek için UI Kabuğu hizmetini almak için VSPackage kullanarak VSIX projesi oluşturma ve VSPackage proje öğesi ekleme hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5791dc2b8ac6714fa5595ba9e5336c4d0f99cc85
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089686"
---
# <a name="create-an-extension-with-a-vspackage"></a>VSPackage ile uzantı oluşturma

Bu kılavuzda vsIX projesi oluşturma ve VSPackage proje öğesi ekleme adımlarını gösterir. BIR ileti kutusu göstermek üzere UI Kabuğu hizmetini almak için VSPackage'i kullanacağız.

## <a name="prerequisites"></a>Önkoşullar

2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-vspackage"></a>VSPackage oluşturma

1. **FirstPackage** adlı bir VSIX projesi oluşturun. VSIX proje şablonunu **"vsix"** Project Yeni Uygulama iletişim kutusunda bulabilirsiniz.

2. Proje açıldığında **FirstPackage** adlı Visual Studio bir paket öğesi şablonu ekleyin. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Yeni Öğe **Ekle iletişim kutusunda** Visual **C#**  >  **Genişletilebilirliği'ne gidin ve** Paketle'Visual Studio **seçin.** Pencerenin **en** altındaki Ad alanında, komut dosyası adını *FirstPackage.cs olarak değiştirebilirsiniz.*

3. Projeyi derleme ve hata ayıklamayı başlatma.

    Deneysel örnek Visual Studio görünür. Deneysel örnek hakkında daha fazla bilgi için [bkz. Deneysel örnek.](../extensibility/the-experimental-instance.md)

4. Deneysel örnekte Araçlar Uzantıları **ve**  >  **Güncelleştirmeler penceresini** açın. **FirstPackage uzantısını burada** görüyorsanız. (Çalışma **örneğinizin Çalışma Örneği'Visual Studio** Uzantılar ve Güncelleştirmeler'i açarsanız **FirstPackage'i görmezsiniz).**

## <a name="load-the-vspackage"></a>VSPackage'i yükleme

Bu noktada uzantı yüklenmez çünkü yüklemeye neden olan bir şey yoktur. Bir uzantıyı genellikle kullanıcı arabirimiyle etkileşim kurduğunda (bir menü komutuna tıklayarak, araç penceresini açarak) veya VSPackage'ın belirli bir kullanıcı arabirimi bağlamında yüklensin. VSPackage'ları ve UI bağlamlarını yükleme hakkında daha fazla bilgi için [bkz. VSPackage'ları Yükleme.](../extensibility/loading-vspackages.md) Bu yordamda, bir çözüm açık olduğunda VSPackage'ın nasıl yük dengelemesi olduğunu gösteriz.

1. *FirstPackage.cs dosyasını* açın. sınıfının bildirimini `FirstPackage` bakın. Mevcut öznitelikleri aşağıdaki özniteliklerle değiştirin:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. ŞIMDI VSPackage'ın yükleniyor olduğunu bize haber sağlayan bir ileti ekalım. Bunu yapmak için VSPackage'ın yöntemini kullanırız, çünkü Visual Studio hizmetleri `Initialize()` yalnızca VSPackage sited edildikten sonra edinebilirsiniz. (Hizmetleri alma hakkında daha fazla bilgi için [bkz. Nasıl: Hizmet alma.)](../extensibility/how-to-get-a-service.md) yöntemini, `Initialize()` `FirstPackage` hizmeti alan, arabirimini <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> alan ve yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> çağıran kodla <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> değiştirin.

    ```csharp
    protected override void Initialize()
    {
        base.Initialize();

        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(
            0,
            ref clsid,
            "FirstPackage",
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result));
    }
    ```

3. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür.

4. Deneysel örnekte bir çözüm açın. Initialize() İçinde İlk Paket olduğunu **söyleyen bir ileti kutusu görüyorsanız.**
