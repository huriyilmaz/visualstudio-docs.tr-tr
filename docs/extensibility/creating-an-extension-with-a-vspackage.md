---
title: VSPackage ile uzantı oluşturma | Microsoft Docs
description: Bir VSıX projesi oluşturmayı ve bir ileti kutusu göstermek için UI kabuğu hizmetini almak amacıyla VSPackage kullanarak VSPackage proje öğesi eklemeyi öğrenin.
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
ms.openlocfilehash: 29b7dd4a3cd6da6a13d999419bfef5a7eafa839adc53df115860e0785d534f75
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293527"
---
# <a name="create-an-extension-with-a-vspackage"></a>VSPackage ile uzantı oluşturma

Bu izlenecek yol, bir VSıX projesinin nasıl oluşturulduğunu ve bir VSPackage proje öğesi nasıl ekleneceğini gösterir. Bir ileti kutusu göstermek için UI kabuğu hizmetini almak üzere VSPackage kullanacağız.

## <a name="prerequisites"></a>Önkoşullar

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezi ' nden yüklemeyin. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>VSPackage oluşturma

1. **Firstpackage** ADLı bir VSIX projesi oluşturun. vsıx proje şablonunu, **yeni Project** iletişim kutusunda "vsıx" arayarak bulabilirsiniz.

2. proje açıldığında, **firstpackage** adlı bir Visual Studio paket öğesi şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **yeni öğe ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **Visual Studio paketi**' ni seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *firstpackage. cs* olarak değiştirin.

3. Projeyi derleyin ve hata ayıklamayı başlatın.

    Visual Studio deneysel örneği görüntülenir. Deneysel örnek hakkında daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).

4. Deneysel örnekte, **Araçlar**  >  **Uzantılar ve güncelleştirmeler** penceresini açın. **Firstpackage** uzantısını burada görmeniz gerekir. (Visual Studio çalışma örneğinizde **uzantılar ve güncelleştirmeler** açarsanız, **firstpackage**' i görmezsiniz).

## <a name="load-the-vspackage"></a>VSPackage yükleme

Bu noktada, yüklenmesine neden olan hiçbir şey olmadığından uzantı yüklenmez. Genellikle bir uzantıyı, Kullanıcı arabirimiyle etkileşim kurarken (bir menü komutuna tıklayarak, bir araç penceresi açarak) veya VSPackage 'ın belirli bir kullanıcı arabirimi bağlamında yüklenmesi gerektiğini belirterek yükleyebilirsiniz. VSPackages ve UI bağlamlarını yükleme hakkında daha fazla bilgi için bkz. [VSPackages yükleme](../extensibility/loading-vspackages.md). Bu yordamda, bir çözüm açıkken VSPackage yükleme işlemini göstereceğiz.

1. *Firstpackage. cs* dosyasını açın. Sınıfının bildirimini bulun `FirstPackage` . Mevcut öznitelikleri aşağıdaki özniteliklerle değiştirin:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. VSPackage 'un yüklendiğini bize bildirmek için bir ileti ekleyelim. `Initialize()`yalnızca vspackage oluşturulduktan sonra Visual Studio hizmetleri alabilmeniz için vspackage 'un yöntemini kullanacağız. (Hizmetleri alma hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md).) `Initialize()` Yöntemini `FirstPackage` hizmeti alan kodla değiştirin <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimini alır ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> yöntemini çağırır.

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

4. Deneysel örnekte bir çözüm açın. **Ilk paketin Initialize () içinde** olduğunu belirten bir ileti kutusu görmeniz gerekir.
