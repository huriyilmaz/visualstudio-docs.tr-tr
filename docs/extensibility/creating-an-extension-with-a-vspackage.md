---
title: VSPackage ile Uzantı Oluşturma | Microsoft Dokümanlar
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1037ebcc58cc4183e6f02119bc7b46abfc132f52
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739530"
---
# <a name="create-an-extension-with-a-vspackage"></a>VSPackage ile uzantı oluşturma

Bu walkthrough nasıl bir VSIX proje oluşturmak ve bir VSPackage proje öğesi eklemek gösterir. Bir mesaj kutusu göstermek için UI Shell hizmetini almak için VSPackage'ı kullanacağız.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-vspackage"></a>VSPackage Oluşturma

1. **FirstPackage**adında bir VSIX projesi oluşturun. "vsix" aramasını yaparak **VSIX** proje şablonunu Yeni Proje iletişim kutusunda bulabilirsiniz.

2. Proje açıldığında, **FirstPackage**adlı bir Visual Studio paket öğesi şablonu ekleyin. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Yeni **Öğe Ekle** iletişim kutusunda Visual **C#** > **Genişletilebilirlik'e** gidin ve **Visual Studio Paketi'ni**seçin. Pencerenin altındaki **Ad** alanında, komut dosyası adını *FirstPackage.cs*olarak değiştirin.

3. Projeyi oluşturun ve hata ayıklamaya başlayın.

    Visual Studio'nun deneysel örneği ortaya çıkar. Deneysel örnek hakkında daha fazla bilgi için, [bkz.](../extensibility/the-experimental-instance.md)

4. Deneysel örnekte, **Araçlar** > **Uzantıları ve Güncelleştirmeleri** penceresini açın. **FirstPackage** uzantısını burada görmelisiniz. (Visual Studio'da **Uzantıları ve Güncelleştirmeleri** açarsanız, **FirstPackage'ı**görmezsiniz).

## <a name="load-the-vspackage"></a>VSPackage'ı yükleyin

Bu noktada, uzantı yüklenmez, çünkü yüklenmesine neden olan hiçbir şey yoktur. Kullanıcı Arabirimi ile etkileşimkurduğunuzda (menü komutunu tıklattığınızda, bir araç penceresini açtığınızda) veya VSPackage'ın belirli bir Kullanıcı Arabirimi bağlamında yüklenmesi gerektiğini belirterek genellikle uzantı yükleyebilirsiniz. VSPackages ve Kullanıcı Arabirimi bağlamları yükleme hakkında daha fazla bilgi için, [YÜKLEME VSPackages](../extensibility/loading-vspackages.md)bakın. Bu yordam için, bir çözüm açıldığında vspackage'ı nasıl yükleyeceğinizi göstereceğiz.

1. *FirstPackage.cs* dosyasını açın. Sınıfın bildirimine `FirstPackage` bakın. Varolan öznitelikleri aşağıdaki özniteliklerle değiştirin:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. VSPackage'ın yüklendiğini bilmemizi sağlayan bir ileti ekleyelim. Bunu yapmak için VSPackage'ın `Initialize()` yöntemini kullanıyoruz, çünkü Visual Studio hizmetlerini ancak VSPackage sited edildikten sonra alabilirsiniz. (Hizmet alma hakkında daha fazla bilgi için [bkz.](../extensibility/how-to-get-a-service.md) <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> Yöntemi, hizmeti `FirstPackage` alan, arabirimi alan ve yöntemini çağıran kodla değiştirin. `Initialize()`

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

3. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir.

4. Deneysel örnekte bir çözüm açın. **InitialPackage Inside Initial()** yazan bir ileti kutusu görmelisiniz.
