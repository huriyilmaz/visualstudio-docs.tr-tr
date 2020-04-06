---
title: 'Nasıl: Bir Asynchronous Visual Studio Service | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65362e465beec5465903083beca069104a48166b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710763"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Nasıl: Bir eşzamanlı Visual Studio hizmeti sağlayın
Kullanıcı Giçin iş parçacığı engellemeden bir hizmet almak istiyorsanız, bir eşzamanlı hizmet oluşturmalı ve paketi bir arka plan iş parçacığına yüklemelisiniz. Bu amaçla bir <xref:Microsoft.VisualStudio.Shell.AsyncPackage> <xref:Microsoft.VisualStudio.Shell.Package>yerine kullanabilirsiniz , ve asynchronous paketinözel asynchronous yöntemleri ile hizmet ekleyebilirsiniz.

 Eşzamanlı Visual Studio hizmetleri sağlama hakkında daha fazla bilgi için [bkz.](../extensibility/how-to-provide-a-service.md)

## <a name="implement-an-asynchronous-service"></a>Eşzamanlı bir hizmet uygulama

1. Bir VSIX projesi oluşturun (**Dosya** > **Yeni** > **Proje** > **Görsel C#** > **Genişletilebilirlik** > **VSIX Projesi**). Proje **TestAsync**adı .

2. Projeye bir VSPackage ekleyin. **Çözüm Gezgini'ndeki** proje düğümünü seçin ve**Yeni öğe** > **Görsel C# Öğeleri** > **Genişletilebilirlik** > **Görsel Stüdyo Paketi'ni** **tıklatın.** >  Bu dosyayı *TestAsyncPackage.cs.*

3. *TestAsyncPackage.cs*olarak, yerine devralma `AsyncPackage` paketi `Package`değiştirin:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:

    - Hizmeti tanımlayan bir arabirim. Bu arabirimlerin çoğu boştur, diğer bir süre önce yalnızca hizmeti sorgulamak için kullanıldıkları için yöntemleri yoktur.

    - Hizmet arabirimini açıklayan bir arabirim. Bu arabirim, uygulanacak yöntemleri içerir.

    - Hem hizmet hem de hizmet arabirimini uygulayan bir sınıf.

5. Aşağıdaki örnek, üç tür çok temel bir uygulama gösterir. Hizmet sınıfının oluşturucusu servis sağlayıcıyı ayarlamalıdır. Bu örnekte, hizmeti paket kodu dosyasına eklememiz daha caizdir.

6. Paket dosyasına yönergeleri kullanarak aşağıdakileri ekleyin:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. İşte asynchronous hizmet uygulaması. Oluşturucudaki senkron servis sağlayıcısı yerine eşzamanlı servis sağlayıcısını ayarlamanız gerektiğini unutmayın:

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

## <a name="register-a-service"></a>Bir hizmeti kaydetme
 Bir hizmeti kaydetmek için, hizmeti sağlayan pakete ekleyin. <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Senkron bir hizmeti kaydetmekiçin farklı olarak, hem paket hem de hizmetin async yüklemeyi desteklediğinden emin olmanız gerekir:

- Paketin eşsenkronize olarak başlatılmasını sağlamak <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> için **AllowsBackgroundLoading = true** field eklemeniz gerekir PackageRegistrationAttribute hakkında daha fazla bilgi için, [Bkz. Kayıt ve kayıt dışı VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Hizmet örneğinin eşzamanlı olarak başlatılmasını sağlamak <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> için **IsAsyncQueryable = true** field eklemeniz gerekir.

  Burada bir eşzamanlı `AsyncPackage` hizmet kaydı ile bir örnektir:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Hizmet ekleme

1. *TestAsyncPackage.cs,* `Initialize()` yöntemi kaldırın ve `InitializeAsync()` yöntemi geçersiz kılın. Hizmeti ekleyin ve hizmetleri oluşturmak için bir geri arama yöntemi ekleyin. Aşağıda, bir hizmet ekleyerek asynchronous başharfbir örnektir:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Bu hizmeti bu paketin dışında görünür hale getirmek için, son parametre olarak tanıtım bayrağı değerini *doğru* olarak ayarlayın:`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*adresine başvuru ekleyin.

3. Geri arama yöntemini, hizmeti oluşturan ve döndüren eşzamanlı bir yöntem olarak uygulayın.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Hizmet kullanma
 Şimdi hizmeti alabilir ve yöntemlerini kullanabilirsiniz.

1. Bunu baş harflerinde göstereceğiz, ancak hizmeti kullanmak istediğiniz her yerde alabilirsiniz.

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

     Makinenizde anlamlı bir `userpath` dosya adı ve yol değiştirmeyi unutmayın!

2. Kodu oluşturun ve çalıştırın. Visual Studio'nun deneysel örneği göründüğünde, bir çözüm açın. Bu otomatik `AsyncPackage` yüklenmesine neden olur. Baş harfi çalıştırıldığında, belirttiğiniz konumda bir dosya bulmanız gerekir.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Komut işleyicisinde eşzamanlı hizmet kullanma
 Menü komutunda asynchronous hizmetinin nasıl kullanılacağına dair bir örnek aşağıda verilmiştir. Hizmeti diğer eşzamanlı olmayan yöntemlerde kullanmak için burada gösterilen yordamı kullanabilirsiniz.

1. Projenize bir menü komutu ekleyin. (Çözüm **Gezgini'nde**proje düğümünü, sağ tıklatma öğesini seçin ve**Yeni Öğe** > **Genişletilebilirlik** > **Özel Komutu** **Ekle'yi** > seçin.) Komut dosyasını *TestAsyncCommand.cs.*

2. Özel komut şablonu, `Initialize()` komutu başlatmayı kolaylaştırmak için yöntemi *TestAsyncPackage.cs* dosyasına yeniden ekler. `Initialize()` Yöntemde, komutu başharfleyen satırı kopyalayın. Şu şekilde görünmelidir:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Bu satırı `InitializeAsync()` *AsyncPackageForService.cs* dosyasındaki yönteme taşıyın. Bu bir eşzamanlı başlatma olduğundan, komutu kullanarak <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>başlatmadan önce ana iş parçacığına geçmeniz gerekir. Şimdi bu gibi görünmelidir:

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

3. `Initialize()` Yöntemi silin.

4. *TestAsyncCommand.cs* dosyasında `MenuItemCallback()` yöntemi bulun. Yöntemin gövdesini silin.

5. Kullanma yönergesi ekleyin:

    ```csharp
    using System.IO;
    ```

6. Hizmeti alan ve yöntemlerini `UseTextWriterAsync()`kullanan asynchronous yöntemini ekleyin:

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

7. Bu yöntemi yöntemden çağırın: `MenuItemCallback()`

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Çözümü oluşturun ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneği **göründüğünde, Araçlar** menüsüne gidin ve **Invoke TestAsyncCommand** menü öğesini arayın. Tıklattığınızda, TextWriterService belirttiğiniz dosyaya yazar. (Bir çözüm açmanız gerekmez, çünkü komutu çağırmak paketin yüklenmesine de neden olur.)

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanım ve hizmet sağlama](../extensibility/using-and-providing-services.md)
