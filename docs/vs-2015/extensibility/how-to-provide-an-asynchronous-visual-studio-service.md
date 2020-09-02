---
title: 'Nasıl yapılır: zaman uyumsuz hizmet sağlama | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c58b0be10bf10a21b783a48d52806bf769381ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204111"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Nasıl Yapılır: Zaman Uyumsuz Visual Studio Hizmeti Sağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UI iş parçacığını engellemeden bir hizmet almak istiyorsanız, zaman uyumsuz bir hizmet oluşturmanız ve paketi bir arka plan iş parçacığına yüklemeniz gerekir. Bu amaçla <xref:Microsoft.VisualStudio.Shell.AsyncPackage> , yerine bir kullanabilir <xref:Microsoft.VisualStudio.Shell.Package> ve hizmeti zaman uyumsuz paketin özel zaman uyumsuz yöntemleriyle birlikte ekleyebilirsiniz

 Zaman uyumlu Visual Studio hizmetleri sağlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet sağlama](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Zaman uyumsuz hizmet uygulama

1. VSıX projesi oluşturun (**dosya/yeni/proje/Visual C#/Extensiblity/VSIX projesi**). Projeyi **Testasync**olarak adlandırın.

2. Projeye VSPackage ekleyin. **Çözüm Gezgini** proje düğümünü seçin ve **Ekle/yeni öğe/Visual C# öğeleri/genişletilebilirlik/Visual Studio paketi**' ne tıklayın. Bu dosyayı **TestAsyncPackage.cs**olarak adlandırın.

3. TestAsyncPackage.cs ' de paketini paket yerine AsyncPackage 'ten devralacak şekilde değiştirin:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:

    - Hizmeti tanımlayan bir arabirim. Bu arabirimlerin birçoğu boştur, yani bir yöntemi yoktur.

    - Hizmet arabirimini tanımlayan bir arabirim. Bu arabirim uygulanacak yöntemleri içerir.

    - Hem hizmeti hem de hizmet arabirimini uygulayan bir sınıf.

5. Aşağıdaki örnek, üç türün temel bir uygulamasını gösterir. Hizmet sınıfının Oluşturucusu, hizmet sağlayıcısını ayarlamış olmalıdır. Bu örnekte, hizmeti yalnızca paket kodu dosyasına ekleyeceğiz.

6. Aşağıdaki using deyimlerini paket dosyasına ekleyin:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7. Zaman uyumsuz hizmet uygulamasını burada bulabilirsiniz. Oluşturucuda zaman uyumlu hizmet sağlayıcısı yerine zaman uyumsuz hizmet sağlayıcısını ayarlamanız gerektiğini unutmayın:

    ```
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)
        {
            serviceProvider = provider;
        }
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
        public TaskAwaiter GetAwaiter()
        {
            return new TaskAwaiter();
        }
    }
    public interface STextWriterService
    {
    }
    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
        TaskAwaiter GetAwaiter();
    }
    ```

## <a name="registering-a-service"></a>Hizmet kaydetme
 Bir hizmeti kaydetmek için, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> hizmetini hizmeti sağlayan pakete ekleyin. Zaman uyumlu hizmeti kaydetmenin iki farkı vardır:

- Paketi yeniden yüklüyorsanız, bu <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> özniteliğe BackgroundLoad değerini eklemeniz gerekir. VSPackages 'yi oto yükleme hakkında daha fazla bilgi için bkz. [VSPackages yükleme](../extensibility/loading-vspackages.md).

- **Allowsbackgroundyükleme = true** alanını öğesine eklemeniz gerekir <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> . PackageRegistrationAttribute hakkında daha fazla bilgi için bkz. [VSPackages kaydetme ve kaydını silme](../extensibility/registering-and-unregistering-vspackages.md).

  Zaman uyumsuz hizmet kaydıyla bir AsyncPackage örneği aşağıda verilmiştir:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>Hizmet ekleme

1. TestAsyncPackage.cs içinde, yöntemini kaldırın `Initialize()` ve yöntemi geçersiz kılın `InitializeAsync()` . Hizmeti ekleyin ve hizmetleri oluşturmak için bir geri arama yöntemi ekleyin. Hizmet ekleme zaman uyumsuz başlatıcısının bir örneği aşağıda verilmiştir:

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2. Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll bir başvuru ekleyin.

3. Geri çağırma yöntemini, hizmeti oluşturan ve döndüren zaman uyumsuz bir yöntem olarak uygulayın.

    ```csharp
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        STextWriterService service = null;
        await System.Threading.Tasks.Task.Run(() => {
                    service = new TextWriterService(this);
             });

        return service;
    }

    ```

## <a name="using-a-service"></a>Hizmet kullanma
 Artık hizmeti alabilir ve yöntemlerini kullanabilirsiniz.

1. Bunu başlatıcıda göstereceğiz, ancak hizmeti, hizmeti kullanmak istediğiniz her yerde edinebilirsiniz.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     *\<userpath>* Makinenizde anlamlı bir dosya adı ve yola geçiş yapmayı unutmayın!

2. Kodu derleyin ve çalıştırın. Visual Studio 'nun deneysel örneği göründüğünde bir çözüm açın. Bu, AsyncPackage 'in oto yüklemesine neden olur. Başlatıcı çalıştırıldığında, belirttiğiniz konumda bir dosya bulmanız gerekir.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Bir komut Işleyicisinde zaman uyumsuz bir hizmet kullanma
 Bir menü komutunda zaman uyumsuz bir hizmetin nasıl kullanılacağına ilişkin bir örnek aşağıda verilmiştir. Hizmeti, zaman uyumsuz olmayan diğer yöntemlerle kullanmak için burada gösterilen yordamı kullanabilirsiniz.

1. Projenize bir menü komutu ekleyin. ( **Çözüm Gezgini**, proje düğümünü seçin, sağ tıklayın ve **Ekle/yeni öğe/genişletilebilirlik/özel komut**' i seçin.) Komut dosyasını TestAsyncCommand.cs olarak adlandırın **.**

2. Özel komut şablonu, `Initialize()` komutu başlatmak için yöntemi TestAsyncPackage.cs dosyasına yeniden ekler. Initialize () yönteminde, komutu Başlatan satırı kopyalayın. Şu şekilde görünmelidir:

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Bu satırı `InitializeAsync()` AsyncPackageForService.cs dosyasındaki yöntemine taşıyın. Bu zaman uyumsuz bir başlatmada olduğundan, komutunu kullanarak çalıştırmadan önce ana iş parçacığına geçmeniz gerekir <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Şimdi şöyle görünmelidir:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        TestAsyncCommand.Initialize(this);

        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync((<userpath>, "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

3. Yöntemi silin `Initialize()` .

4. TestAsyncCommand.cs dosyasında `MenuItemCallback()` yöntemini bulun. Metodun gövdesini silin.

5. Using deyimleri ekleme:

    ```
    using System.IO;
    ```

6. `GetAsyncService()`Hizmeti alıp ve kendi yöntemlerini kullanan adlı bir zaman uyumsuz yöntem ekleyin:

    ```csharp
    private async System.Threading.Tasks.Task GetAsyncService()
    {
        ITextWriterService textService =
           this.ServiceProvider.GetService(typeof(STextWriterService))
              as ITextWriterService;
        // don’t forget to change <userpath> to a local path
        await writer.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7. Yönteminden bu yöntemi çağırın `MenuItemCallback()` :

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8. Çözümü oluşturun ve hata ayıklamayı başlatın. Visual Studio 'nun deneysel örneği göründüğünde, **Araçlar** menüsüne gidin ve **testasynccommand** menü öğesini çağır ' ı arayın. Bu öğeyi tıklattığınızda, TextWriterService belirttiğiniz dosyaya yazar. (Bir çözümü açmanız gerekmez, çünkü komutu çağırmak da paketin yüklenmesine neden olur.)

## <a name="see-also"></a>Ayrıca Bkz.
 [Hizmetleri Kullanma ve Sağlama](../extensibility/using-and-providing-services.md)
