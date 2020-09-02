---
title: VSPackage ile uzantı oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddad7149db75aa662f9427a301c04eaf925146f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197426"
---
# <a name="creating-an-extension-with-a-vspackage"></a>VSPackage İçeren Bir Uzantı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bir VSıX projesinin nasıl oluşturulduğunu ve bir VSPackage proje öğesi nasıl ekleneceğini gösterir. Bir ileti kutusu göstermek için UI kabuğu hizmetini almak üzere VSPackage kullanacağız.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>VSPackage oluşturma  
  
1. **Firstpackage**ADLı bir VSIX projesi oluşturun. VSıX proje şablonunu, **Visual C#/genişletilebilirlik**altında **Yeni proje** iletişim kutusunda bulabilirsiniz.  
  
2. Proje açıldığında, **Firstpackage**adlı bir Visual Studio paket öğe şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin. **Yeni öğe Ekle** Iletişim kutusunda **Visual C#/genişletilebilirlik** ' e gidin ve **Visual Studio paketi**' ni seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını **FirstPackage.cs**olarak değiştirin.  
  
3. Projeyi derleyin ve hata ayıklamayı başlatın.  
  
     Visual Studio 'nun deneysel örneği görüntülenir. Deneysel örnek hakkında daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).  
  
4. Deneysel örnekte, **Araçlar/Uzantılar ve güncelleştirmeler** penceresini açın. **Firstpackage** uzantısını burada görmeniz gerekir. (Visual Studio 'nun çalışma Örneğinizde **Uzantılar ve güncelleştirmeler** açarsanız, **firstpackage**' i görmezsiniz).  
  
## <a name="loading-the-vspackage"></a>VSPackage yükleniyor  
 Bu noktada, yüklenmesine neden olan hiçbir şey olmadığından uzantı yüklenmez. Genellikle bir uzantıyı, Kullanıcı arabirimiyle etkileşim kurarken (bir menü komutuna tıklayarak, bir araç penceresi açarak) veya VSPackage 'ın belirli bir kullanıcı arabirimi bağlamında yüklenmesi gerektiğini belirterek yükleyebilirsiniz. VSPackages ve UI bağlamlarını yükleme hakkında daha fazla bilgi için bkz. [VSPackages yükleme](../extensibility/loading-vspackages.md). Bu yordamda, bir çözüm açıkken VSPackage yükleme işlemini göstereceğiz.  
  
1. FirstPackage.cs dosyasını açın. FirstPackage sınıfının bildirimini bulun. Mevcut öznitelikleri şu şekilde değiştirin:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2. VSPackage 'un yüklendiğini bize bildirmek için bir ileti ekleyelim. Yalnızca VSPackage oluşturulduktan sonra Visual Studio hizmetlerini alabilmeniz için VSPackage Initialize () yöntemini kullanıyoruz. (Hizmetleri alma hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md).) FirstPackage Initialize () yöntemini hizmeti alan kodla değiştirin <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimi alır ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> yöntemini çağırır.  
  
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
