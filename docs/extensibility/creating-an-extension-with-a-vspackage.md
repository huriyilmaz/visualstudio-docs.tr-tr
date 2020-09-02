---
title: VSPackage ile uzantı oluşturma | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68ade2f8d334c1f93349e396d910fa300f6b5417
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903850"
---
# <a name="create-an-extension-with-a-vspackage"></a>VSPackage ile uzantı oluşturma

Bu izlenecek yol, bir VSıX projesinin nasıl oluşturulduğunu ve bir VSPackage proje öğesi nasıl ekleneceğini gösterir. Bir ileti kutusu göstermek için UI kabuğu hizmetini almak üzere VSPackage kullanacağız.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>VSPackage oluşturma

1. **Firstpackage**ADLı bir VSIX projesi oluşturun. "VSIX" araması yaparak VSıX proje şablonunu **Yeni proje** iletişim kutusunda bulabilirsiniz.

2. Proje açıldığında, **Firstpackage**adlı bir Visual Studio paket öğe şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Add**  >  **Yeni öğe**Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **Visual Studio paketi**' ni seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *FirstPackage.cs*olarak değiştirin.

3. Projeyi derleyin ve hata ayıklamayı başlatın.

    Visual Studio 'nun deneysel örneği görüntülenir. Deneysel örnek hakkında daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).

4. Deneysel örnekte, **Araçlar**  >  **Uzantılar ve güncelleştirmeler** penceresini açın. **Firstpackage** uzantısını burada görmeniz gerekir. (Visual Studio 'nun çalışma Örneğinizde **Uzantılar ve güncelleştirmeler** açarsanız, **firstpackage**' i görmezsiniz).

## <a name="load-the-vspackage"></a>VSPackage yükleme

Bu noktada, yüklenmesine neden olan hiçbir şey olmadığından uzantı yüklenmez. Genellikle bir uzantıyı, Kullanıcı arabirimiyle etkileşim kurarken (bir menü komutuna tıklayarak, bir araç penceresi açarak) veya VSPackage 'ın belirli bir kullanıcı arabirimi bağlamında yüklenmesi gerektiğini belirterek yükleyebilirsiniz. VSPackages ve UI bağlamlarını yükleme hakkında daha fazla bilgi için bkz. [VSPackages yükleme](../extensibility/loading-vspackages.md). Bu yordamda, bir çözüm açıkken VSPackage yükleme işlemini göstereceğiz.

1. *FirstPackage.cs* dosyasını açın. Sınıfının bildirimini bulun `FirstPackage` . Mevcut öznitelikleri aşağıdaki özniteliklerle değiştirin:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. VSPackage 'un yüklendiğini bize bildirmek için bir ileti ekleyelim. `Initialize()`Yalnızca VSPackage oluşturulduktan sonra Visual Studio hizmetlerini alabilmeniz Için VSPackage 'un yöntemini kullanırız. (Hizmetleri alma hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md).) `Initialize()` Yöntemini `FirstPackage` hizmeti alan kodla değiştirin <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimini alır ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> yöntemini çağırır.

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

3. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

4. Deneysel örnekte bir çözüm açın. **Ilk paketin Initialize () içinde**olduğunu belirten bir ileti kutusu görmeniz gerekir.
