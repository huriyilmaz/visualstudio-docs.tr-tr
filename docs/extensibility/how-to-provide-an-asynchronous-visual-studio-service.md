---
title: 'Nasıl yapılır: zaman uyumsuz Visual Studio hizmeti sağlama | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad178bf93e49c3d695c1ebd0a5d4f6b151175953
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905734"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Nasıl yapılır: zaman uyumsuz bir Visual Studio hizmeti sağlama
UI iş parçacığını engellemeden bir hizmet almak istiyorsanız, zaman uyumsuz bir hizmet oluşturmanız ve paketi bir arka plan iş parçacığına yüklemeniz gerekir. Bu amaçla <xref:Microsoft.VisualStudio.Shell.AsyncPackage> , yerine bir kullanabilir <xref:Microsoft.VisualStudio.Shell.Package> ve hizmeti zaman uyumsuz paketin özel zaman uyumsuz yöntemleriyle birlikte ekleyebilirsiniz.

 Zaman uyumlu Visual Studio hizmetleri sağlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet sağlama](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Zaman uyumsuz hizmet uygulama

1. VSIX projesi oluşturun (**Dosya**  >  **Yeni**  >  **Proje**  >  **Visual C#**  >  **Extensiblity**  >  **VSIX projesi**). Projeyi **Testasync**olarak adlandırın.

2. Projeye VSPackage ekleyin. **Çözüm Gezgini** proje düğümünü seçin ve **Add**  >  **Yeni öğe**Ekle  >  **Visual C# öğeleri**  >  **genişletilebilirlik**  >  **Visual Studio paketi**' ne tıklayın. Bu dosyayı *TestAsyncPackage.cs*olarak adlandırın.

3. *TestAsyncPackage.cs*' de, paketi yerine şuradan devralacak şekilde değiştirin `AsyncPackage` `Package` :

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:

    - Hizmeti tanımlayan arabirim. Bu arabirimlerin birçoğu boştur, diğer bir deyişle, yalnızca hizmeti sorgulamak için kullanılan hiçbir yöntemi yoktur.

    - Hizmet arabirimini tanımlayan bir arabirim. Bu arabirim uygulanacak yöntemleri içerir.

    - Hem hizmeti hem de hizmet arabirimini uygulayan bir sınıf.

5. Aşağıdaki örnek, üç türün temel bir uygulamasını gösterir. Hizmet sınıfının Oluşturucusu, hizmet sağlayıcısını ayarlamış olmalıdır. Bu örnekte, hizmeti yalnızca paket kodu dosyasına ekleyeceğiz.

6. Aşağıdaki using yönergelerini paket dosyasına ekleyin:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Zaman uyumsuz hizmet uygulamasını burada bulabilirsiniz. Oluşturucuda zaman uyumlu hizmet sağlayıcısı yerine zaman uyumsuz hizmet sağlayıcısını ayarlamanız gerektiğini unutmayın:

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>Hizmet kaydetme
 Bir hizmeti kaydetmek için, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> hizmetini hizmeti sağlayan pakete ekleyin. Zaman uyumlu bir hizmeti kaydetmeye farklı olarak, hem paket hem de hizmetin zaman uyumsuz yüklemeyi desteklediğinden emin olmanız gerekir:

- **AllowsBackgroundLoading = true** <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> PackageRegistrationAttribute hakkında daha fazla bilgi için paketin zaman uyumsuz olarak başlatılabilmesi Için Allowsbackgroundyüklenmekte = true alanını öğesine eklemeniz gerekir, bkz. [VSPackages 'i kaydetme ve kaydını kaldırma](../extensibility/registering-and-unregistering-vspackages.md).

- Hizmet örneğinin zaman uyumsuz olarak başlatılabilmesi için **ısasyncqueryable = true** alanını öğesine eklemeniz gerekir <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> .

  `AsyncPackage`Zaman uyumsuz hizmet kaydıyla bir örneği aşağıda verilmiştir:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Hizmet ekleme

1. *TestAsyncPackage.cs*içinde, yöntemini kaldırın `Initialize()` ve yöntemi geçersiz kılın `InitializeAsync()` . Hizmeti ekleyin ve hizmetleri oluşturmak için bir geri arama yöntemi ekleyin. Hizmet ekleme zaman uyumsuz başlatıcısının bir örneği aşağıda verilmiştir:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Bu hizmeti bu paketin dışında görünür yapmak için, yükseltme bayrağı değerini son parametre olarak *true* olarak ayarlayın:  `this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*bir başvuru ekleyin.

3. Geri çağırma yöntemini, hizmeti oluşturan ve döndüren zaman uyumsuz bir yöntem olarak uygulayın.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Hizmet kullanma
 Artık hizmeti alabilir ve yöntemlerini kullanabilirsiniz.

1. Bunu başlatıcıda göstereceğiz, ancak hizmeti, hizmeti kullanmak istediğiniz her yerde edinebilirsiniz.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     `userpath`Makinenizde anlamlı bir dosya adı ve yola geçiş yapmayı unutmayın!

2. Kodu derleyin ve çalıştırın. Visual Studio 'nun deneysel örneği göründüğünde bir çözüm açın. Bu, ' nin `AsyncPackage` oto yüklemesine neden olur. Başlatıcı çalıştırıldığında, belirttiğiniz konumda bir dosya bulmanız gerekir.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Bir komut işleyicisinde zaman uyumsuz bir hizmet kullanma
 Bir menü komutunda zaman uyumsuz bir hizmetin nasıl kullanılacağına ilişkin bir örnek aşağıda verilmiştir. Hizmeti, zaman uyumsuz olmayan diğer yöntemlerle kullanmak için burada gösterilen yordamı kullanabilirsiniz.

1. Projenize bir menü komutu ekleyin. ( **Çözüm Gezgini**, proje düğümünü seçin, sağ tıklayın ve **Ekle**  >  ' yi seçin. **Yeni öğe**  >  **Genişletilebilirlik**  >  **Özel komut**.) Komut dosyasını *TestAsyncCommand.cs*olarak adlandırın.

2. Özel komut şablonu, `Initialize()` komutu başlatmak için yöntemi *TestAsyncPackage.cs* dosyasına yeniden ekler. `Initialize()`Yönteminde, komutu Başlatan satırı kopyalayın. Şu şekilde görünmelidir:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Bu satırı `InitializeAsync()` *AsyncPackageForService.cs* dosyasındaki yöntemine taşıyın. Bu zaman uyumsuz bir başlatmada olduğundan, komutunu kullanarak çalıştırmadan önce ana iş parçacığına geçmeniz gerekir <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Şimdi şöyle görünmelidir:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Yöntemi silin `Initialize()` .

4. *TestAsyncCommand.cs* dosyasında `MenuItemCallback()` yöntemini bulun. Metodun gövdesini silin.

5. Using yönergesini ekleyin:

    ```csharp
    using System.IO;
    ```

6. `UseTextWriterAsync()`Hizmeti alıp ve kendi yöntemlerini kullanan adlı bir zaman uyumsuz yöntem ekleyin:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Yönteminden bu yöntemi çağırın `MenuItemCallback()` :

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Çözümü oluşturun ve hata ayıklamayı başlatın. Visual Studio 'nun deneysel örneği göründüğünde, **Araçlar** menüsüne gidin ve **testasynccommand** menü öğesini çağır ' ı arayın. Bu öğeyi tıklattığınızda, TextWriterService belirttiğiniz dosyaya yazar. (Bir çözümü açmanız gerekmez, çünkü komutu çağırmak da paketin yüklenmesine neden olur.)

## <a name="see-also"></a>Ayrıca bkz.
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
