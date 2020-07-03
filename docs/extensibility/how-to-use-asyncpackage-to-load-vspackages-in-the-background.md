---
title: 'Nasıl yapılır: arka planda VSPackages yüklemek için AsyncPackage kullanma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 7727d53c84ab876fe6616c8ec5d438033216481e
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905601"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Nasıl yapılır: arka planda VSPackages yüklemek için AsyncPackage kullanma
VS paketini yükleme ve başlatma, disk g/ç ile sonuçlanabilir. Bu tür g/ç, UI iş parçacığında gerçekleşdiğinde, yanıt hızı sorunlarına yol açabilir. Visual Studio 2015, <xref:Microsoft.VisualStudio.Shell.AsyncPackage> bir arka plan iş parçacığında paket yüklemeyi sağlayan sınıfı kullanıma sunmuştur.

## <a name="create-an-asyncpackage"></a>AsyncPackage oluşturma
 Bir VSIX projesi oluşturarak**başlayabilir (**  >  **Yeni**  >  **Proje**  >  **Visual C#**  >  **genişletilebilirlik**  >  **VSIX projesi**) ve projeye VSPackage **ekleyebilirsiniz**(projeye sağ tıklayıp  >  **Yeni öğe**Ekle  >  **C# öğe**  >  **genişletilebilirlik**  >  **Visual Studio paketi**). Daha sonra hizmetlerinizi oluşturabilir ve bu hizmetleri paketinize ekleyebilirsiniz.

1. Paketini öğesinden türet <xref:Microsoft.VisualStudio.Shell.AsyncPackage> .

2. Sorgusu, paketinizin yüklenmesine neden olabilecek hizmetler sağlıyorsanız:

    Paketinizin arka plan yüklemesi için güvenli olduğunu ve bu davranışı kabul etmek için, Visual Studio 'ya, <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> öznitelik oluşturucusunda **Allowsbackgroundyükleme** özelliğini true olarak ayarlamanız gerekir.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Visual Studio 'Nun, bir arka plan iş parçacığında hizmetinizin örneğini oluşturmak için güvenli olduğunu belirtmek üzere, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> oluşturucuda özelliği true olarak ayarlamanız gerekir <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> .

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Kullanıcı arabirimi bağlamları aracılığıyla yüklüyorsanız, paketinizin otomatik yük girişinin değeri olarak yazılmış bayraklarda, veya değeri (0x2) için **Packageotoloadflags. BackgroundLoad** değerini belirtmeniz gerekir <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> .

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Yapılacak zaman uyumsuz başlatma çalışmadıysanız, öğesini geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> . `Initialize()`VSIX şablonu tarafından sunulan yöntemi kaldırın. ( `Initialize()` **Asyncpackage** yöntemi mühürlü). <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A>Paketinize zaman uyumsuz hizmetler eklemek için herhangi bir yöntemi kullanabilirsiniz.

    NOTE: çağırmak Için `base.InitializeAsync()` , kaynak kodunuzu şu şekilde değiştirebilirsiniz:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Zaman uyumsuz başlatma kodınızdan RPC (uzaktan yordam çağrısı) yapmayın ( **ınitializeasync**içinde). Bunlar doğrudan veya dolaylı olarak çağırdığınızda meydana gelebilir <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> .  Eşitleme yükleri gerektiğinde, UI iş parçacığı kullanımını engeller <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . Varsayılan engelleme modeli, RPC 'yi devre dışı bırakır. Yani, zaman uyumsuz görevlerinize bir RPC kullanmaya çalışırsanız, UI iş parçacığının kendisi paketinizin yüklenmesini bekliyorsa kilitlenirsiniz. Genel alternatif, birlikte bulunan **görev fabrikasının** <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> veya RPC kullanmayan başka bir mekanizmaya benzer şekilde, gerekirse, kodunuzu kullanıcı arabirimi iş parçacığına sıralayamaz.  **ThreadHelper. Generic. Invoke** kullanmayın veya genellikle UI iş parçacığına alınması bekleyen çağıran iş parçacığını engelleyin.

    NOTE: yönteyinizdeki **GetService** veya **QueryService** kullanmaktan kaçının `InitializeAsync` . Bunları kullanmanız gerekiyorsa, önce UI iş parçacığına geçmeniz gerekir. Alternatif, <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> **asyncpackage** 'ten (' ye aktararak <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> ) kullanmaktır.

   C#: Asyncpackage oluşturma:

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

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Mevcut bir VSPackage 'ı AsyncPackage 'e Dönüştür
 İşin büyük bölümü, yeni bir **Asyncpackage**oluşturma ile aynıdır. Yukarıdaki 1 ile 5 arasındaki adımları izleyin. Ayrıca aşağıdaki önerilerden de daha fazla dikkatli olmanız gerekir:

1. `Initialize`Paketinizin sahip olduğunuz geçersiz kılmayı kaldırmayı unutmayın.

2. Kilitlenmeleri önleyin: kodunuzda gizli RPC 'ler olabilir. Artık bir arka plan iş parçacığında meydana gelir. Bir RPC (örneğin, **GetService**) yapıyorsanız, ana iş parçacığına veya (2) varsa API 'nin zaman uyumsuz sürümünü kullandığınızdan emin olun (örneğin, **GetServiceAsync**).

3. İş parçacıkları arasında çok sık geçiş yapma. Yükleme süresini azaltmak için bir arka plan iş parçacığında gerçekleşebilirler işi yerelleştirmeye çalışın.

## <a name="querying-services-from-asyncpackage"></a>AsyncPackage Hizmetleri sorgulanıyor
 Bir **Asyncpackage** , çağırana bağlı olarak zaman uyumsuz olarak olabilir veya yüklenmeyebilir. Örneğin,

- Çağıran, **GetService** veya **QueryService** (her Ikisi de zaman uyumlu API) olarak adlandırıldığında veya

- Çağıran **IVsShell:: LoadPackage** (veya **IVsShell5:: LoadPackageWithContext**) olarak adlandırıldığında veya

- Yük bir kullanıcı arabirimi bağlamı tarafından tetiklenir, ancak kullanıcı arabirimi bağlam mekanizmasını sizin tarafınızdan zaman uyumsuz olarak yükleyemeyeceğini belirtmedi

  ardından, paketiniz zaman uyumlu olarak yüklenir.

  Paketinizin Kullanıcı arabirimi iş parçacığı devre dışı bırakmak için bir fırsata (zaman uyumsuz başlatma aşamasında) hala bir fırsat vardır. Çağıran, hizmetinize yönelik zaman uyumsuz sorgu için **ıasyncserviceprovider** kullanıyorsa, yükleme ve başlatma zaman uyumsuz olarak elde edilen görev nesnesi üzerinde engellenmeyecektir.

  C#: hizmeti zaman uyumsuz olarak sorgulama:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
