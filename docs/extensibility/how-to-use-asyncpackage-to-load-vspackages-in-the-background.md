---
title: 'Nasıl Kullanılır: Arka Planda VSPackages Yüklemek için AsyncPackage kullanın | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 77690a1947f82f97c4aa12809a80ea61335d216d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710625"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Nasıl kullanılır: Arka planda VSPackages yüklemek için AsyncPackage kullanın
Bir VS paketinin yüklenmesi ve başlatılması disk G/Ç'ye neden olabilir. Böyle bir G/Ç Kullanıcı Bira iş parçacığı nda gerçekleşirse, yanıt verme sorunlarına neden olabilir. Bu sorunu gidermek için Visual Studio 2015, arka plan iş parçacığına paket yüklemesini sağlayan <xref:Microsoft.VisualStudio.Shell.AsyncPackage> sınıfı tanıttı.

## <a name="create-an-asyncpackage"></a>AsyncPackage Oluşturma
 Bir VSIX projesi oluşturarak başlayabilirsiniz **(Dosya** > **Yeni** > **Proje** > Görsel**C#** > **Genişletilebilirlik** > **VSIX Projesi)** ve projeye bir VSPackage ekleyerek (projeye sağ tıklayın ve Yeni**Öğe** > **C# öğesi** > **Genişletilebilirlik** > **Görsel Stüdyo Paketi** **ekleyin).** >  Daha sonra hizmetlerinizi oluşturabilir ve bu hizmetleri paketinize ekleyebilirsiniz.

1. Paketi <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.

2. Sorgulama paketinizin yüklenmesine neden olabilecek hizmetler sağlıyorsanız:

    Visual Studio'ya paketinizin arka plan yüklemesi için güvenli <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> olduğunu belirtmek ve bu davranışı tercih etmek **için, AllowsBackgroundLoading** özelliğini öznitelik oluşturucuda doğru olarak ayarlamanız gerekir.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Visual Studio'ya hizmetinizi bir arka plan iş parçacığı üzerinde anında eklemenin <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> güvenli olduğunu <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> belirtmek için, özelliği oluşturucuda doğru şekilde ayarlamanız gerekir.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Kullanıcı Arabirimi bağlamları üzerinden yükleniyorsanız, paketinizin otomatik yük girişinin değeri olarak yazılmış bayraklara <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> OR değeri (0x2) için **PackageAutoLoadFlags.BackgroundLoad** belirtmeniz gerekir.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Yapmanız gereken eşzamanlı başlatma çalışmanız varsa, geçersiz kılmanız <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>gerekir. VSIX `Initialize()` şablonu tarafından sağlanan yöntemi kaldırın. `Initialize()` **(AsyncPackage'deki** yöntem mühürlüdür). Paketinize eşzamanlı hizmetler <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> eklemek için yöntemlerden herhangi birini kullanabilirsiniz.

    NOT: Aramak `base.InitializeAsync()`için, kaynak kodunuzu şu şekilde değiştirebilirsiniz:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Asynchronous başlatma kodunuzdan **(InitializeAsync'de)** RPC (Uzaktan Yordam Çağrısı) yapmamaya dikkat etmelisiniz. Bunlar, doğrudan veya <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> dolaylı olarak aradiğinizde oluşabilir.  Eşitleme yükleri gerektiğinde, UI iş <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>parçacığı kullanarak engelleyecektir. Varsayılan engelleme modeli RPC'leri devre dışı bırakıyor. Bu, async görevlerinizden bir RPC kullanmaya çalışırsanız, Kullanıcı Arabirimi iş parçacığı paketinizin yüklenmesini bekliyorsa kilitlediğiniz anlamına gelir. Genel alternatif, **Birleştirilebilir Görev Fabrikası**'veya <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> bir RPC kullanmayan başka bir mekanizma gibi bir şey kullanarak gerekirse, UI iş parçacığı için kodunuzu mareşal etmektir.  **ThreadHelper.Generic.Invoke** veya genellikle Kullanıcı Arası iş parçacığı almak için bekleyen arama iş parçacığı engellemeyin.

    NOT: Yönteminizde `InitializeAsync` **GetService veya QueryService'i** kullanmaktan kaçınmalısınız. **QueryService** Bunları kullanmanız gerekiyorsa, önce UI iş parçacığına geçmeniz gerekir. Alternatif <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> **AsyncPackage** kullanmaktır (döküm <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>tarafından .)

   C#: Bir AsyncPackage oluşturun:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]
public sealed class TestPackage : AsyncPackage
{
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(SMyTestService), CreateService, true);
        return Task.FromResult<object>(null);
    }
}
```

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Varolan bir VSPackage'ı AsyncPackage'a dönüştürün
 Çalışmanın çoğunluğu yeni bir **AsyncPackage**oluşturma aynıdır. Yukarıdaki 1'den 5'e kadar olan adımları izleyin. Ayrıca aşağıdaki önerilerle ekstra dikkatli olmanız gerekir:

1. Paketinizde bulunan `Initialize` geçersiz kılmayı kaldırmayı unutmayın.

2. Kilitlenmeleri önle: Kodunuzda gizli RPC'ler olabilir. şimdi bir arka plan iş parçacığı üzerinde olur. Bir RPC yapıyorsanız (örneğin, **GetService),**(1) ana iş parçacığına geçmeniz veya (2) varsa API'nin eşzamanlı sürümünü kullanmanız gerektiğinden emin olun (örneğin, **GetServiceAsync).**

3. İş parçacıkları arasında çok sık geçiş yapmayın. Yükleme süresini azaltmak için arka plan iş parçacığında gerçekleşebilecek çalışmayı yerelleştirmeye çalışın.

## <a name="querying-services-from-asyncpackage"></a>AsyncPackage'dan hizmetleri sorgulama
 **Bir AsyncPackage,** arayana bağlı olarak eşit olarak yüklenebilir veya yüklemeyebilir. Örneğin,

- **Arayan GetService** veya **QueryService** (her ikisi de eşzamanlı API'ler) veya

- Arayan **IVsShell::LoadPackage** (veya **IVsShell5::LoadPackageWithContext)** veya

- Yük bir Kullanıcı Altı Anlama bağlamı tarafından tetiklenir, ancak kullanıcı bir kullanıcı tarafından kullanıcı bir şekilde yüklenebileceğiniz Kullanıcı Bire-i bilgi bağlam mekanizması belirtmemişsiniz

  sonra paketiniz senkronize olarak yüklenir.

  Paketinizin hala kullanıcı arabirimi iş parçacığı dışında çalışmak için bir fırsatı vardır (asynchronous başlatma aşamasında) ancak ui iş parçacığı bu çalışmanın tamamlanması için engellenir. Arayan, hizmetiniz için eşzamanlı bir şekilde sorgulamak için **IAsyncServiceProvider** kullanıyorsa, yüklemeniz ve başlatmanız, ortaya çıkan görev nesnesini hemen engellemediklerini varsayarak eş senkronize olarak yapılır.

  C#: Hizmeti eşit bir şekilde sorgulama:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
