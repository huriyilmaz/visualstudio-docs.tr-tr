---
title: 'Nasıl Visual Studio: Zaman Uyumsuz | Microsoft Docs'
description: Zaman uyumsuz bir hizmet sağlamayı Visual Studio öğrenin. Bu yaklaşım, kullanıcı arabirimi iş parçacığını engellemeden bir hizmet elde etmek sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 41777f9b04060928799c621de8262d50d027014aaa4a2831ad0a6656bfa0b9c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401719"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Nasıl Visual Studio: Zaman uyumsuz Visual Studio sağlama
Kullanıcı arabirimi iş parçacığını engellemeden bir hizmet almak için zaman uyumsuz bir hizmet oluşturmanız ve paketi arka plan iş parçacığına yüklemeniz gerekir. Bu amaç için yerine kullanabilir ve zaman uyumsuz paketin özel zaman uyumsuz yöntemleriyle <xref:Microsoft.VisualStudio.Shell.AsyncPackage> hizmeti eklemek için <xref:Microsoft.VisualStudio.Shell.Package> kullanabilirsiniz.

 Zaman uyumlu hizmet sağlama hakkında Visual Studio için bkz. [Nasıl: Hizmet sağlama.](../extensibility/how-to-provide-a-service.md)

## <a name="implement-an-asynchronous-service"></a>Zaman uyumsuz hizmet uygulama

1. VSIX projesi oluşturma (**Visual**  >    >  **C# Project**  >    >    >  Dosya Yeni Uzantısı VSIX Project ). Projeye **TestAsync adını girin.**

2. Projeye bir VSPackage ekleyin. Proje düğümünde proje düğümünü **seçin Çözüm Gezgini** Ekle Yeni öğe Visual C# Öğeleri Genişletilebilirlik   >    >    >    >  **Visual Studio Paketi'ne tıklayın.** Bu dosyaya *TestAsyncPackage.cs adını girin.*

3. *TestAsyncPackage.cs içinde,* paketini yerine 'den `AsyncPackage` devralınacak şekilde `Package` değiştirir:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:

    - Hizmeti tanımlayan bir arabirim. Bu arabirimlerin çoğu boştur, yani yalnızca hizmeti sorgulamak için kullanıldıkları için yöntemleri yoktur.

    - Hizmet arabirimini açıklayan bir arabirim. Bu arabirim, uygulanacak yöntemleri içerir.

    - Hem hizmeti hem de hizmet arabirimini uygulayan bir sınıf.

5. Aşağıdaki örnek, üç türün çok temel bir uygulamasını gösterir. Hizmet sınıfının oluşturucusu hizmet sağlayıcısını ayarlamalıdır. Bu örnekte, yalnızca hizmeti paket kodu dosyasına ekleyacağız.

6. Paket dosyasına aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Zaman uyumsuz hizmet uygulaması şu şekildedir. Oluşturucuda zaman uyumlu hizmet sağlayıcısı yerine zaman uyumsuz hizmet sağlayıcısını ayarlamanız gerekir:

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
 Bir hizmeti kaydetmek için, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> hizmetini sağlayan pakete ekleyin. Zaman uyumlu bir hizmeti kaydetmeden farklı olarak, hem paket hem de hizmetin zaman uyumsuz yüklemeyi desteklediğini emin olun:

- Paketin zaman uyumsuz olarak başlatılabölmesinden emin olmak için **AllowsBackgroundLoading = true** alanını eklemeniz gerekir PackageRegistrationAttribute hakkında daha fazla bilgi için <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> bkz. [VSPackages'ı](../extensibility/registering-and-unregistering-vspackages.md)kaydetme ve kaydını geri alma.

- Hizmet örneğinin zaman uyumsuz olarak başlatılabilir olduğundan emin olmak için **IsAsyncQueryable = true** <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> alanını 'a eklemeniz gerekir.

  Zaman uyumsuz hizmet `AsyncPackage` kaydına sahip bir örneği aşağıdaki gibidir:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Hizmet ekleme

1. *TestAsyncPackage.cs içinde* yöntemini `Initialize()` kaldırın ve yöntemini geçersiz `InitializeAsync()` kılın. Hizmeti ekleyin ve hizmetleri oluşturmak için bir geri çağırma yöntemi ekleyin. Zaman uyumsuz başlatıcının bir hizmet ekleme örneği:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Bu hizmeti bu paketin dışında görünür hale yapmak için, yükselt bayrağı değerini son parametre olarak *true* olarak ayarlayın:  `this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll. **

3. Geri çağırma yöntemini hizmeti oluşturan ve döndüren zaman uyumsuz bir yöntem olarak uygulama.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Hizmet kullanma
 Artık hizmeti ve yöntemlerini kullanabilirsiniz.

1. Bunu başlatıcıda gösteracağız, ancak hizmeti kullanmak istediğiniz her yerde elde etmek için kullanabilirsiniz.

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

     Makineniz için mantıklı `userpath` olan bir dosya adı ve yol ile değiştirmeyi unutmayın!

2. Kodu derleme ve çalıştırma. Deneysel Visual Studio bir çözüm açın. Bu, otomatik `AsyncPackage` yüklemeye neden olur. Başlatıcı çalıştırılmışsa, belirttiğiniz konumda bir dosya bulmanız gerekir.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Komut işleyicisinde zaman uyumsuz hizmet kullanma
 Burada, bir menü komutunda zaman uyumsuz bir hizmetin nasıl kullanacağız? Hizmeti diğer zaman uyumsuz yöntemlerde kullanmak için burada gösterilen yordamı kullanabilirsiniz.

1. Projenize bir menü komutu ekleyin. (Çözüm Gezgini **proje** düğümünü seçin, sağ tıklayın ve Ekle'yi **seçin**  >  **Yeni Öğe**  >  **Genişletilebilirlik**  >  **Özel Komut**.) Komut dosyasını *TestAsyncCommand.cs olarak adlandırabilirsiniz.*

2. Özel komut şablonu, komutu başlatmak `Initialize()` için *testAsyncPackage.cs* dosyasına yöntemini yeniden ekler. `Initialize()`yönteminde, komutu başlatan satırı kopyalayın. Şu şekilde görünmelidir:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Bu satırı `InitializeAsync()` *AsyncPackageForService.cs dosyasındaki yöntemine* taşıma. Bu zaman uyumsuz başlatmada olduğundan, komutunu kullanarak başlatmadan önce ana iş parçacığına <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> geçmelisiniz. Şimdi şu şekilde olması gerekir:

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

3. yöntemini `Initialize()` silin.

4. *TestAsyncCommand.cs* dosyasında yöntemini `MenuItemCallback()` bulun. Yönteminin gövdeyi silin.

5. Using yönergesi ekleyin:

    ```csharp
    using System.IO;
    ```

6. hizmeti alan ve yöntemlerini kullanan `UseTextWriterAsync()` adlı zaman uyumsuz bir yöntem ekleyin:

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

7. yönteminden bu yöntemi `MenuItemCallback()` çağır:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Çözümü derleme ve hata ayıklamayı başlatma. Deneysel Visual Studio görüntülendiğinde Araçlar **menüsüne** gidin ve **TestAsyncCommand** Çağır menü öğesini seçin. Bu dosyaya tıklarsanız TextWriterService belirttiğiniz dosyaya yazar. (Komutun iptali paketin yüklenmeye neden olduğu için bir çözüm açmana gerek yok.)

## <a name="see-also"></a>Ayrıca bkz.
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
