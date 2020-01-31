---
title: 'Nasıl yapılır: zaman uyumsuz Visual Studio hizmeti sağlama | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d486aac8e990fef6b139bca989a51d74146ecb67
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826412"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Nasıl yapılır: zaman uyumsuz bir Visual Studio hizmeti sağlama
UI iş parçacığını engellemeden bir hizmet elde etmek istiyorsanız, zaman uyumsuz bir hizmet oluşturma ve arka plan iş parçacığında paketi gerekir. Bu amaçla, bir <xref:Microsoft.VisualStudio.Shell.Package>yerine bir <xref:Microsoft.VisualStudio.Shell.AsyncPackage> kullanabilir ve hizmeti zaman uyumsuz paketin özel zaman uyumsuz yöntemleriyle birlikte ekleyebilirsiniz.

 Zaman uyumlu Visual Studio hizmetleri sağlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet sağlama](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Zaman uyumsuz hizmet uygulama

1. **Visual C#**  > **Extensiblity** > **VSIX projesi**) bir VSIX projesi oluşturun (**Dosya** > **Yeni** > **projesi** > . Projeyi adlandırın **TestAsync**.

2. Bir VSPackage'ı projeye ekleyin. **Çözüm Gezgini** proje düğümünü seçin ve > **yeni öğe** **Ekle** >  **C# görsel öğeler** > **genişletilebilirlik** > **Visual Studio paketi**' ne tıklayın. Bu dosya adı *TestAsyncPackage.cs*.

3. *TestAsyncPackage.cs*' de, paketi `Package`yerine `AsyncPackage` devralacak şekilde değiştirin:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:

    - Hizmeti tanımlayan arabirim. Bu arabirimlerin birçoğu boştur, diğer bir deyişle, yalnızca hizmeti sorgulamak için kullanılan hiçbir yöntemi yoktur.

    - Hizmet arabirimi açıklayan bir arabirim. Bu arabirim, uygulanacak yöntemleri içerir.

    - Hem hizmet hem de hizmet arabirimi uygulayan bir sınıf.

5. Aşağıdaki örnek, üç tür çok basit bir uygulamasını gösterir. Hizmet sınıfının oluşturucusu, hizmet sağlayıcısı ayarlamanız gerekir. Bu örnekte, hizmeti yalnızca paket kodu dosyasına ekleyeceğiz.

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

7. Zaman uyumsuz hizmet uygulamasını burada bulabilirsiniz. Zaman uyumlu bir hizmet sağlayıcısı yerine zaman uyumsuz bir hizmet sağlayıcısı oluşturucuda ayarlanacak gerektiğini unutmayın:

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
 Bir hizmeti kaydetmek için ekleme <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> hizmeti sağlayan paket. Zaman uyumlu bir hizmeti kaydetmeye farklı olarak, hem paket hem de hizmetin zaman uyumsuz yüklemeyi desteklediğinden emin olmanız gerekir:

- PackageRegistrationAttribute hakkında daha fazla bilgi Için, paketin zaman uyumsuz olarak başlatılabilmesi için <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> **Allowsbackgroundyüklenmekte = true** alanını eklemeniz gerekir, bkz. [VSPackages kaydetme ve kaydını kaldırma](../extensibility/registering-and-unregistering-vspackages.md).

- Hizmet örneğinin zaman uyumsuz olarak başlatılabilmesi için, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> **ısasyncqueryable = true** alanını eklemeniz gerekir.

  Zaman uyumsuz hizmet kaydıyla bir `AsyncPackage` örneği aşağıda verilmiştir:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Hizmet Ekle

1. *TestAsyncPackage.cs*içinde `Initialize()` yöntemini kaldırın ve `InitializeAsync()` yöntemini geçersiz kılın. Hizmet Ekle ve hizmetleri oluşturmak için bir geri çağırma yöntemi ekleyin. Bir hizmeti eklemek, zaman uyumsuz Başlatıcı bir örneği aşağıda verilmiştir:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Bu hizmeti bu paketin dışında görünür yapmak için, yükseltme bayrağı değerini son parametre olarak *true* olarak ayarlayın: `this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. *Microsoft. VisualStudio. Shell. Interop. 14.0. DesignTime. dll*için bir başvuru ekleyin.

3. Geri arama yöntemi oluşturur ve hizmet döndüren zaman uyumsuz bir yöntem uygulayın.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Hizmet kullanma
 Artık hizmet alma ve onun yöntemlerini kullanın.

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

     `userpath`, makinenizde anlamlı bir dosya adı ve yol olarak değiştirmeyi unutmayın!

2. Kodunu derleme ve çalıştırma. Visual Studio'nun deneysel örneğinde göründüğünde, bir çözüm açın. Bu, `AsyncPackage` oto yüklemesine neden olur. Başlatıcı çalıştırıldığında, belirtilen konumda bir dosya bulmanız gerekir.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Bir komut işleyicisinde zaman uyumsuz bir hizmet kullanma
 Bir menü komutunda zaman uyumsuz bir hizmetin nasıl kullanılacağına ilişkin bir örnek aşağıda verilmiştir. Hizmetini zaman uyumsuz olmayan diğer yöntemleri kullanmayı burada gösterilen yordam kullanabilirsiniz.

1. Bir menü komutu projenize ekleyin. ( **Çözüm Gezgini**, proje düğümünü seçin, sağ tıklayın ve > **yeni öğe** **Ekle** > **genişletilebilirlik** > **özel komut**öğesini seçin.) Komut dosyasını *TestAsyncCommand.cs*olarak adlandırın.

2. Özel komut şablonu, komutu başlatmak için `Initialize()` yöntemini *TestAsyncPackage.cs* dosyasına yeniden ekler. `Initialize()` yönteminde, komutu Başlatan çizgiyi kopyalayın. Şu şekilde görünmelidir:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Bu satırı *AsyncPackageForService.cs* dosyasındaki `InitializeAsync()` yöntemine taşıyın. Bu zaman uyumsuz bir başlatma olduğundan, komutu kullanarak başlatılmadan önce ana iş parçacığından geçmelidir <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Bunu artık şöyle görünmelidir:

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

3. Silme `Initialize()` yöntemi.

4. *TestAsyncCommand.cs* dosyasında `MenuItemCallback()` yöntemini bulun. Yöntemin gövdesi silin.

5. Using yönergesini ekleyin:

    ```csharp
    using System.IO;
    ```

6. Adlı bir zaman uyumsuz bir yöntem ekleyin `UseTextWriterAsync()`, hizmet alır ve kendi yöntemlerini kullanır:

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

7. Bu yöntemi çağırın `MenuItemCallback()` yöntemi:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Çözümü derleyin ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneğinde göründüğünde, Git **Araçları** menü ve Ara **çağırma TestAsyncCommand** menü öğesi. Düğmeyi tıklattığınızda TextWriterService, belirtilen dosyaya yazar. (Bir çözümü açmanız gerekmez, çünkü komutu çağırmak da paketin yüklenmesine neden olur.)

## <a name="see-also"></a>Ayrıca bkz.
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
