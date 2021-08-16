---
title: ARKA planda VSPackage yüklemek için AsyncPackage kullanma
description: Disk G/Ç'lerinden gelen yanıt hızı sorunlarını önleyen bir arka plan iş parçacığında paket yüklenmesini sağlayan AsyncPackage sınıfını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: 32017e3755a85142876f9616f45f300e323b6752affa1773db5bcdd548b1ef1f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359903"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Nasıllı: Arka planda VSPackage yüklemek için AsyncPackage kullanma
VS paketinin yüklenmesi ve başlatması, disk I/O'ya neden olabilir. Bu tür bir I/O kullanıcı arabirimi iş parçacığında gerçekleşirse yanıt verme sorunlarına yol açabilirsiniz. Bu konuyu ele Visual Studio 2015'te arka plan iş <xref:Microsoft.VisualStudio.Shell.AsyncPackage> parçacığında paket yüklenmesini sağlayan sınıfı tanıtıldı.

## <a name="create-an-asyncpackage"></a>AsyncPackage oluşturma
 İlk olarak bir VSIX projesi **(** Dosya Yeni Project Visual C# Genişletilebilirliği VSIX Project ) ve projeye bir  >    >    >    >    >  **VSPackage** ekleyerek (projeye  >    >    >    >  sağ tıklar ve Yeni Öğe Ekle C# öğesi Genişletilebilirlik Visual Studio Paketi) ile başlayabilirsiniz. Daha sonra hizmetlerinizi oluşturabilir ve bu hizmetleri paketinize eklersiniz.

1. Paketi'den <xref:Microsoft.VisualStudio.Shell.AsyncPackage> türetin.

2. Sorgulaması paketinizin yüklenmeye neden olduğu hizmetler sağlıyorsanız:

    Paketinizin arka Visual Studio güvenli olduğunu belirtmek ve bu davranışı kabul etmek için, öznitelik oluşturucuda <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> **AllowsBackgroundLoading** özelliğini true olarak ayarlamanız gerekir.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Hizmetinizi Visual Studio bir arka plan iş parçacığında oluşturmanın güvenli olduğunu belirtmek için, oluşturucuda <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> özelliğini true olarak <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> ayarlamalıdır.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Kullanıcı arabirimi bağlamları aracılığıyla yükleniyorsanız, OR değeri (0x2) için **PackageAutoLoadFlags.BackgroundLoad** değerini, paketinizin otomatik yükleme girdisi olarak yazılan bayraklara belirtmeniz <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> gerekir.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Zaman uyumsuz başlatmayı yapmak için çalışıyorsanız, geçersiz <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> kılmalı. `Initialize()`VSIX şablonu tarafından sağlanan yöntemi kaldırın. `Initialize()` **(AsyncPackage'daki yöntem korumalıdır).** Paketinize zaman <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> uyumsuz hizmetler eklemek için yöntemlerden herhangi birini kullanabilirsiniz.

    NOT: çağrısı yapmak `base.InitializeAsync()` için kaynak kodunuzu şu şekilde değiştirebilirsiniz:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Zaman uyumsuz başlatma kodunuzdan **(InitializeAsync** içinde) RPC'ler (Uzaktan Yordam Çağrısı) yapmamanıza dikkat edin. Bunlar doğrudan veya dolaylı <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> olarak çağırarak ortaya çıkabilir.  Eşitleme yükleri gerekli olduğunda, kullanıcı arabirimi iş parçacığı kullanılarak <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> engellenir. Varsayılan engelleme modeli RPC'leri devre dışı bırakıyor. Bu, zaman uyumsuz görevlerinizin RPC'lerini kullanmayı denemeniz, kullanıcı arabirimi iş parçacığının kendisi paketinizin yüklenmek üzere beklediğinde kilitlenmeniz anlamına gelir. Genel alternatif, **Joinable Task Factory** gibi bir şey veya RPC kullanmayan başka bir mekanizma kullanarak gerekirse kodunuzu kullanıcı arabirimi iş parçacığına <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> sıralamaktır.  **ThreadHelper.Generic.Invoke** kullanma veya genellikle kullanıcı arabirimi iş parçacığına almak için bekleyen çağıran iş parçacığını engelleme.

    NOT: Yönteminde **GetService veya** **QueryService kullanmaktan** kaçınmanız `InitializeAsync` gerekir. Bu öğeleri kullanmak zorundasanız önce kullanıcı arabirimi iş parçacığına geçmeniz gerekir. Alternatif, <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> **AsyncPackage'ından kullanmaktır** (bunu olarak <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> atarak).

   C#: AsyncPackage oluşturun:

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

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Var olan bir VSPackage'i AsyncPackage'a dönüştürme
 Çalışmaların çoğunluğu yeni bir **AsyncPackage oluşturmakla aynıdır.** Yukarıdaki 1-5. adımları izleyin. Ayrıca aşağıdaki önerilerle birlikte çok dikkatli olmalısınız:

1. Paketiniz içinde `Initialize` olan geçersiz kılmayı kaldırmayı unutmayın.

2. Kilitlenmeleri önleme: Kodunda gizliRPC'ler olabilir. artık bir arka plan iş parçacığında oluyor. Bir RPC **(örneğin, GetService)** yapıyorsanız ana iş parçacığına (1) geçmeniz veya (2) varsa API'nin zaman uyumsuz sürümünü (örneğin, **GetServiceAsync)** kullanmalısınız.

3. İş parçacıkları arasında çok sık geçiş yapma. Yük süresini azaltmak için arka plan iş parçacığında gerçekleşecek işi yerelleştirmeyi deneyin.

## <a name="querying-services-from-asyncpackage"></a>AsyncPackage'dan hizmetleri sorgulama
 Bir **AsyncPackage,** çağırana bağlı olarak zaman uyumsuz olarak yüklensin veya yüklenmez. Örneğin,

- Çağıranın **GetService veya** **QueryService** (her ikisi de zaman uyumlu API'ler) veya

- Çağıranın **IVsShell::LoadPackage** (veya **IVsShell5::LoadPackageWithContext) çağıran** veya

- Yük bir kullanıcı arabirimi bağlamı tarafından tetiklenir, ancak kullanıcı arabirimi bağlam mekanizmasının sizi zaman uyumsuz olarak yükleyemedik

  ardından paketiniz zaman uyumlu olarak yüklensin.

  Paketinizin yine de kullanıcı arabirimi iş parçacığından iş parçacığını kapatmaya (zaman uyumsuz başlatma aşamasında) bir fırsatı vardır, ancak bu iş parçacığının tamamlanması için kullanıcı arabirimi iş parçacığı engellenir. Çağıran, hizmetinizi zaman uyumsuz olarak sorgulamak için **IAsyncServiceProvider** kullanıyorsa, sonuçta elde edilen görev nesnesinde hemen engellememeleri varsayarak yük ve başlatmanız zaman uyumsuz olarak yapılır.

  C#: Hizmeti zaman uyumsuz olarak sorgulama:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
