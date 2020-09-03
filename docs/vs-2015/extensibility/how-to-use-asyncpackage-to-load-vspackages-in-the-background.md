---
title: 'Nasıl yapılır: arka planda VSPackages yüklemek için AsyncPackage kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: f59838913ed3f9bc6679336393f6db9181291e3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204033"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Nasıl Yapılır: AsyncPackage Kullanarak Arka Planda VSPackage Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VS paketini yükleme ve başlatma, disk g/ç ile sonuçlanabilir. Bu tür g/ç, UI iş parçacığında gerçekleşdiğinde, yanıt hızı sorunlarına yol açabilir. Visual Studio 2015,  <xref:Microsoft.VisualStudio.Shell.AsyncPackage> bir arka plan iş parçacığında paket yüklemeyi sağlayan sınıfı kullanıma sunmuştur.  
  
## <a name="creating-an-asyncpackage"></a>AsyncPackage oluşturma  
 Bir VSıX projesi (**dosya/yeni/proje/Visual C#/genişletilebilirlik/VSIX projesi**) oluşturarak başlayabilir ve projeye bir VSPackage ekleyebilirsiniz (projeye sağ tıklayın ve **Ekle/yeni öğe/C# öğesi/genişletilebilirlik/Visual Studio paketi**). Daha sonra hizmetlerinizi oluşturabilir ve bu hizmetleri paketinize ekleyebilirsiniz.  
  
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
  
4. Yapılacak zaman uyumsuz başlatma çalışmadıysanız, öğesini geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> . VSıX şablonu tarafından sunulan **Initialize ()** yöntemini kaldırın. ( **Asyncpackage** içindeki **Initialize ()** yöntemi mühürlü). <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A>Paketinize zaman uyumsuz hizmetler eklemek için herhangi bir yöntemi kullanabilirsiniz.  
  
    NOTE: **base.InitializeAsync ()** çağırmak için, kaynak kodunuzu şu şekilde değiştirebilirsiniz:  
  
   ```csharp  
   await base.InitializeAsync(cancellationToken, progress);  
   ```  
  
5. Zaman uyumsuz başlatma kodınızdan ( **ınitializtem eşitlemesi**) RPC (yordam çağrısını Kaldır) yapmayın. Bunlar doğrudan veya dolaylı olarak çağırdığınızda meydana gelebilir <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> .  Eşitleme yükleri gerektiğinde, UI iş parçacığı kullanımını engeller <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . Varsayılan engelleme modeli, RPC 'yi devre dışı bırakır. Yani, zaman uyumsuz görevlerinize bir RPC kullanmaya çalışırsanız, UI iş parçacığının kendisi paketinizin yüklenmesini bekliyorsa kilitlenirsiniz. Genel alternatif, birlikte bulunan **görev fabrikasının** <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> veya RPC kullanmayan başka bir mekanizmaya benzer şekilde, gerekirse, kodunuzu kullanıcı arabirimi iş parçacığına sıralayamaz.  **ThreadHelper. Generic. Invoke** kullanmayın veya genellikle UI iş parçacığına alınması bekleyen çağıran iş parçacığını engelleyin.  
  
    NOTE: **ınitialsensync** yönteminde **GetService** veya **QueryService** kullanmaktan kaçının. Bunları kullanmanız gerekiyorsa, önce UI iş parçacığına geçmeniz gerekir. Alternatif, <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> **asyncpackage** 'ten (' ye aktararak <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> ) kullanmaktır.  
  
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
 İşin büyük bölümü, yeni bir **Asyncpackage**oluşturma ile aynıdır. Yukarıdaki 1 ile 5 arasındaki adımları izlemeniz gerekir. Ayrıca, aşağıdakiler için de daha fazla dikkatli olmanız gerekir:  
  
1. Paketinizin sahip olduğunuz **başlatma** geçersiz kılmayı kaldırmayı unutmayın.  
  
2. Kilitlenmeleri önleyin: kodunuzda, bir arka plan iş parçacığında gerçekleşen gizli RPC 'ler olabilir. Bir RPC (ör. **GetService**) yapıyorsanız, ana iş parçacığına (1) geçiş yapmak ya da (2) varsa API 'nin zaman uyumsuz sürümünü kullanmanız gerekir (ör. **GetServiceAsync**).  
  
3. İş parçacıkları arasında çok sık geçiş yapma. Bir arka plan iş parçacığında gerçekleşebilirler işi yerelleştirmeye çalışın. Bu, yükleme süresini azaltır.  
  
## <a name="querying-services-from-asyncpackage"></a>AsyncPackage Hizmetleri sorgulanıyor  
 Bir **Asyncpackage** , çağırana bağlı olarak zaman uyumsuz olarak olabilir veya yüklenmeyebilir. Örneğin,  
  
- Çağıran, **GetService** veya **QueryService** (her Ikisi de zaman uyumlu API) olarak adlandırıldığında veya  
  
- Çağıran **IVsShell:: LoadPackage** (veya **IVsShell5:: LoadPackageWithContext**) olarak adlandırıldığında veya  
  
- Yük bir kullanıcı arabirimi bağlamı tarafından tetiklenir, ancak kullanıcı arabirimi bağlam mekanizmasını sizin tarafınızdan zaman uyumsuz olarak yükleyemeyeceğini belirtmedi  
  
  ardından, paketiniz zaman uyumlu olarak yüklenir.  
  
  Paketinizin Kullanıcı arabirimi iş parçacığı devre dışı bırakmak için bir fırsata (zaman uyumsuz başlatma aşamasında) hala bir fırsat olduğuna, ancak kullanıcı arabirimi iş parçacığı söz konusu çalışmanın tamamlanmasına izin verdiğine unutmayın. Çağıran, hizmetinize yönelik zaman uyumsuz sorgu için **ıasyncserviceprovider** kullanıyorsa, yükleme ve başlatma zaman uyumsuz olarak elde edilen görev nesnesi üzerinde engellenmeyecektir.  
  
  C#: hizmeti zaman uyumsuz olarak sorgulama:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
