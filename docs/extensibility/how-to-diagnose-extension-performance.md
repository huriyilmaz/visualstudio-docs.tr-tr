---
title: 'Nasıl yapılır: uzantı performansını tanılama | Microsoft Docs'
description: Visual Studio, yavaş uzantıları kullanıcılarına bildirir. Uzantı etkisinin nasıl hesaplanacağını ve uzantı etkisinin yerel olarak nasıl çözümlenebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jmartens
ms.workload:
- bertaygu
ms.openlocfilehash: 05dda944ab2aecd429386e0e4c40646d21e9a3d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966415"
---
# <a name="measuring-extension-impact-in-startup"></a>Başlangıçta uzantı etkisini ölçme

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Visual Studio 2017 ' de uzantı performansına odaklanma

Müşteri geri bildirimlerine göre, Visual Studio 2017 Release için odak alanlarından biri başlangıç ve çözüm yükü performansı. Visual Studio platform ekibi olarak, başlangıç ve çözüm yükü performansını iyileştirmeye çalışıyoruz. Genel olarak, ölçümlerimizin yüklü uzantıları önermesi, bu senaryolar üzerinde önemli bir etkiye de sahip olabilir.

Kullanıcıların bu etkiyi anlamalarına yardımcı olmak için, yavaş uzantıları kullanıcılarına bildirmek üzere Visual Studio 'da yeni bir özellik ekledik. Bazen, Visual Studio çözüm yükünü veya başlatmayı yavaşlatan yeni bir uzantı algılar. Yavaşlama algılandığında, kullanıcılar IDE 'de yeni "Visual Studio performansını Yönet" iletişim kutusuna işaret eden bir bildirim görür. Bu iletişim kutusuna, daha önce algılanan uzantılara gözatabilmek için Yardım menüsünde her zaman da erişilebilir.

![Visual Studio performansını yönetme](media/manage-performance.png)

Bu belge, uzantı geliştiricilerinin uzantı etkilerine nasıl hesaplanacağını açıklayarak yardımcı olmaya yardımcı olur. Bu belge, uzantı etkisinin yerel olarak nasıl çözümlenebileceğinizi da açıklar. Uzantı etkisini yerel olarak analiz etmek, bir uzantının performansı etkileyen bir uzantı olarak gösterilip gösterilmeyeceğini tespit eder.

> [!NOTE]
> Bu belge, başlangıç ve çözüm yükünden uzantıların etkisine odaklanır. Uzantılar Ayrıca, Kullanıcı arabiriminin yanıt vermemesine neden olduğunda Visual Studio performansını da etkiler. Bu konu hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzantılardan kaynaklanan Kullanıcı arabirimi gecikmelerini tanılama](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Uzantıların başlangıcını nasıl etkileyebileceği

Uzantıların başlangıç performansını etkileyen en yaygın yöntemlerinden biri, NoSolutionExists veya Shelınalized gibi bilinen başlangıç Kullanıcı arabirimi bağlamlarından birinde otomatik olarak yüklemeyi seçmektir. Bu Kullanıcı arabirimi bağlamları başlangıç sırasında etkinleştirilir. `ProvideAutoLoad`Bu bağlamlara sahip tanımlarındaki özniteliği içeren tüm paketler, bu sırada yüklenip başlatılır.

Bir uzantının etkisini ölçyoruz, öncelikle yukarıdaki bağlamlarda otomatik olarak yüklemeyi tercih eden uzantılar tarafından harcanan zamana odaklanıyoruz. Ölçülen süreler dahil edilecek ancak bunlarla sınırlı olmamak üzere:

* Zaman uyumlu paketler için uzantı derlemelerinin yüklenmesi
* Zaman uyumlu paketler için paket sınıfı oluşturucusunda harcanan süre
* Zaman uyumlu paketler için paket başlatma (veya SetSite) yönteminde harcanan süre
* Zaman uyumsuz paketler için yukarıdaki işlemler arka plan iş parçacığında çalışır.  Bu nedenle, işlemler izlemenin dışında tutulur.
* Paket başlatma sırasında zamanlanan ve ana iş parçacığında çalıştırılacak zaman uyumsuz iş için harcanan süre
* Olay işleyicilerde harcanan süre, özellikle kabuğun bağlam etkinleştirmesini veya Shell zombi durum değişikliğini başlattığını
* Visual Studio 2017 güncelleştirme 3 ' ten başlayarak, kabuk başlatılmadan önce boşta aramalarda harcanan zamanı izlemeye de başlayacağız. Boşta işleyicilerde uzun işlemler ayrıca yanıt vermeyen IDE 'ye neden olur ve Kullanıcı tarafından algılanan başlangıç zamanına katkıda bulunur.

Visual Studio 2015 ' den başlayarak birçok özelliği ekledik. Bu özellikler, paketlerin otomatik olarak yüklenmesine yönelik ihtiyacı kaldırmaya yardımcı olur. Özellikler ayrıca paketlerin daha belirli durumlarda yüklenmesine yönelik ihtiyacı erteleyin. Bu durumlar, kullanıcıların uzantıyı kullanmak veya otomatik olarak yükleme sırasında bir uzantı etkisini azaltmak için daha fazla bilgi olabileceği örnekleri içerir.

Aşağıdaki belgelerde bu özelliklerle ilgili daha fazla ayrıntı bulabilirsiniz:

[Kural tabanlı kullanıcı arabirimi bağlamları](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): UI bağlamları etrafında yerleşik olarak bulunan daha zengin bir kural tabanlı altyapı, proje türleri, türleri ve öznitelikleri temel alan özel bağlamlar oluşturmanıza olanak sağlar. Özel bağlamlar, daha belirli senaryolar sırasında bir paket yüklemek için kullanılabilir. Bu belirli senaryolar, başlangıç yerine belirli bir özelliğe sahip bir projenin varlığını içerir. Özel bağlamlar Ayrıca, komut görünürlüğünün proje bileşenlerine veya diğer kullanılabilir koşullara göre [özel bir içeriğe](visibilityconstraints-element.md) bağlanmasına imkan tanır. Bu özellik, bir komut durumu sorgu işleyicisini kaydetmek için bir paket yükleme gereksinimini ortadan kaldırır.

[Zaman uyumsuz paket desteği](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): visual Studio 2015 ' deki yeni asyncpackage temel sınıfı, paket yükü bir otomatik yükleme özniteliği veya zaman uyumsuz hizmet sorgusu tarafından Isteniyorsa, Visual Studio paketlerinin arka planda zaman uyumsuz olarak yüklenmesine izin verir. Bu arka plan yüklemesi IDE 'nin yanıt vermesini sağlar. Uzantı arka planda başlatılırken ve başlangıç ve çözüm yükü etkilenmemesi gibi kritik senaryolarda IDE yanıt verir.

[Zaman uyumsuz hizmetler](how-to-provide-an-asynchronous-visual-studio-service.md): zaman uyumsuz paket desteğiyle, Hizmetleri zaman uyumsuz olarak sorgulamak ve zaman uyumsuz Hizmetleri kaydetmek için de destek ekledik. Daha da önemlisi, zaman uyumsuz bir sorgudaki çalışmanın çoğunluğunun arka plan iş parçacıklarında oluşması için, temel Visual Studio hizmetlerini, zaman uyumsuz sorguyu destekleyecek şekilde dönüştürmeye çalışıyoruz. SComponentModel (Visual Studio MEF ana bilgisayarı), uzantıların zaman uyumsuz yüklemeyi tam olarak desteklemesini sağlamak için artık zaman uyumsuz sorguyu destekleyen ana hizmetlerden biridir.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Otomatik yüklenen uzantıların etkisini azaltma

Bir paketin başlangıçta otomatik olarak yüklenmesi gerekiyorsa, paket başlatma sırasında yapılan çalışmanın en aza indirmek önemlidir. Paket başlatma işinin en aza düşürülmesi, uzantının başlangıcını etkileme olasılığını azaltır.

Paket başlatmasının pahalı olmasına neden olabilecek bazı örnekler şunlardır:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Zaman uyumsuz paket yükü yerine zaman uyumlu paket yükü kullanımı

Zaman uyumlu paketler ana iş parçacığında varsayılan olarak yüklendiği için, otomatik olarak yüklenen paketlere sahip uzantı sahiplerini, daha önce bahsedildiği gibi zaman uyumsuz paket Taban sınıfını kullanacak şekilde teşvik ediyoruz. Otomatik olarak yüklenen bir paketin zaman uyumsuz yüklemeyi destekleyecek şekilde değiştirilmesi, aşağıdaki diğer sorunları çözmeyi da kolaylaştırır.

### <a name="synchronous-filenetwork-io-requests"></a>Zaman uyumlu dosya/ağ GÇ istekleri

İdeal olarak, ana iş parçacığında herhangi bir zaman uyumlu dosya veya ağ GÇ isteğinin kaçınılması gerekir. Etkileri, makine durumuna bağlıdır ve bazı durumlarda uzun süreler için engelleyebilirler.

Zaman uyumsuz paket yükleme ve zaman uyumsuz GÇ API 'Leri kullanılması, paket başlatmasının bu gibi durumlarda ana iş parçacığını engellemediğinden emin olmanızı sağlamalıdır. Kullanıcılar ayrıca arka planda g/ç istekleri olduğunda Visual Studio ile etkileşime devam edebilir.

### <a name="early-initialization-of-services-components"></a>Hizmetleri, bileşenleri erken başlatma

Paket başlatmasında ortak desenlerden biri tarafından kullanılan veya paket ya da yöntemde tarafından kullanılan Hizmetleri başlatmalıdır `constructor` `initialize` . Bu, hizmetlerin kullanılmaya hazırlanmasını sağlarken, bu hizmetler hemen kullanılmazsa paket yüklemeye de gereksiz ücret eklenebilir. Bunun yerine, paket başlatılmasında yapılan çalışmanın en aza indirmek için bu tür hizmetlerin isteğe bağlı olarak başlatılması gerekir.

Bir paket tarafından sunulan küresel hizmetler için, `AddService` hizmeti yalnızca bir bileşen tarafından istendiğinde başlatılacak şekilde geç için bir işlev alan yöntemleri kullanabilirsiniz. Paket içinde kullanılan hizmetler için, \<T> \<T> ilk kullanımda hizmetlerin başlatılmış/sorgulanmasını sağlamak üzere geç veya zaman uyumsuz clazy kullanabilirsiniz.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Etkinlik günlüğünü kullanarak otomatik yüklenen uzantıların etkisini ölçme

Visual Studio 2017 güncelleştirme 3 ' ten başlayarak, Visual Studio etkinlik günlüğü artık, başlangıç ve çözüm yükü sırasında paketlerin performans etkisi için girişler içerir. Bu ölçümleri görmek için, Visual Studio 'Yu/log anahtarıyla açmanız ve *ActivityLog.xml* dosyasını açmanız gerekir.

Etkinlik günlüğünde, girişler "Visual Studio performansını Yönet" kaynağının altına alınır ve aşağıdaki örnekte olduğu gibi görünür:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Bu örnek, GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" ile Visual Studio 'nun başlangıcında 2008 MS harcandığını gösterir. Visual Studio 'Nun, kullanıcıların bu paketin uzantısını devre dışı bıraktıklarında göreceği tasarruf gibi bir paket etkisini hesaplarken, en üst düzey maliyeti birincil sayı olarak kabul ettikleri unutulmamalıdır.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>PerfView kullanarak otomatik yüklenen uzantıların etkisini ölçme

Kod Analizi, paket başlatmayı yavaşlatabilecek kod yollarının tanımlanmasına yardımcı olmakla çalışırken, Visual Studio başlangıcında bir paket yükünün etkisini anlamak için PerfView gibi uygulamaları kullanarak izlemeyi da kullanabilirsiniz.

PerfView, sistem genelinde bir izleme aracıdır. Bu araç, CPU kullanımı veya sistem çağrılarını engelleme gibi bir uygulamadaki etkin yolları anlamanıza yardımcı olur. Aşağıda, [Microsoft Indirme merkezi](https://www.microsoft.com/en-us/download/details.aspx?id=28567)' nde PerfView kullanılarak sunulan örnek bir uzantının çözümlenmesi hakkında hızlı bir örnektir.

**Örnek kod:**

Bu örnek, aşağıdaki örnek kodu temel alır ve bu durum, yaygın olarak karşılaşılan bazı nedenleri göstermek için tasarlanmıştır:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**PerfView ile izleme kaydetme:**

Uzantınızın yüklü olduğu Visual Studio ortamınızı ayarladıktan sonra, PerfView ' i açarak ve **topla menüsünden** **topla** iletişim kutusunu açarak bir başlangıç izlemesi kaydedebilirsiniz.

![PerfView toplama menüsü](media/perfview-collect-menu.png)

Varsayılan seçenekler, CPU tüketimi için çağrı yığınları sağlayacaktır, ancak bu süre içinde de ilgilendiğimiz için **Iş parçacığı zaman** yığınlarını etkinleştirmeniz gerekir. Ayarlar hazırlanıyor, **toplamayı Başlat** ' a tıklayıp kayıt başladıktan sonra Visual Studio 'yu açabilirsiniz.

Koleksiyonu durdurmadan önce, Visual Studio 'Nun tamamen başlatılmış olduğundan, ana pencerenin tamamen görünür olduğundan ve uzantınızın otomatik olarak gösteren herhangi bir kullanıcı arabirimi parçası varsa, bunlar da görünür olur. Visual Studio tamamen yüklendiğinde ve uzantınız başlatıldığında, izlemeyi çözümlemek için kaydı durdurabilirsiniz.

**Bir izleme PerfView ile çözümleniyor:**

Kayıt tamamlandığında PerfView, izlemeyi otomatik olarak açar ve seçenekleri genişletir.

Bu örneğin amaçları doğrultusunda, temel olarak **Gelişmiş Grup** altında bulabileceğiniz **Iş parçacığı zaman yığınları** görünümü ile ilgileniyoruz. Bu görünüm, bir iş parçacığında harcanan toplam süreyi, hem CPU süresi hem de engelleme süresi (örneğin, disk GÇ veya işleyiciler bekleniyor) dahil bir yöntemle gösterir.

 ![iş parçacığı zaman yığınları](media/perfview-thread-time-stacks.png)

 **Iş parçacığı zaman yığınları** görünümünü açarken Analize Başlamak için **devenv** işlemini seçmeniz gerekir.

PerfView, daha ayrıntılı analiz için kendi yardım menüsü altında iş parçacığı zaman yığınlarının nasıl okunbileceğine ilişkin ayrıntılı yönergeler içerir. Bu örneğin amaçları doğrultusunda, bu görünümü başka bir şekilde filtrelemek istiyoruz. yalnızca paketlerimizin modül adı ve başlangıç iş parçacığından oluşan yığınlar dahil.

1. Varsayılan olarak eklenen tüm Gruplandırmayı kaldırmak için **Grouppats** 'leri boş metin olarak ayarlayın.
2. **Inpats** 'yi, var olan işlem filtresine ek olarak, derleme adınızın ve başlangıç iş parçacığlarınızın bir kısmını içerecek şekilde ayarlayın. Bu durumda, **devenv olmalıdır; Başlangıç Iş parçacığı; MakeVsSlowExtension**.

Artık görünüm yalnızca uzantıyla ilgili Derlemelerle ilişkili maliyeti gösterecektir. Bu görünümde, başlangıç iş parçacığının **Inc (kapsamlı maliyet)** sütununda listelenen herhangi bir zaman filtrelenmiş uzantımız ile ilgilidir ve başlangıç olarak da başlatılır.

Yukarıdaki örnek için bazı ilginç çağrı yığınları şöyle olacaktır:

1. Sınıf kullanan GÇ `System.IO` : bu karelerin dahil maliyeti, izlemede çok pahalı olmayabilir, çünkü dosya GÇ hızı makineden makineye farklılık gösterecektir.

   ![Sistem GÇ çerçeveleri](media/perfview-system-io-frames.png)

2. Diğer zaman uyumsuz çalışmalarla bekleyen çağrıları engelleme: Bu durumda, iç zaman uyumsuz çalışmanın tamamlanmasında ana iş parçacığının engellendiği süreyi temsil eder.

   ![çağrı çerçevelerini engelleme](media/perfview-blocking-call-frames.png)

İzlem içindeki diğer görünümlerden biri, etkiyi tespit etmek için yararlı olacak **görüntü yükleme yığınları** olacaktır. **Iş parçacığı zaman yığınları** görünümüne uygulanan aynı filtreleri uygulayabilir ve otomatik olarak yüklenen pakette yürütülen kod nedeniyle yüklenen tüm derlemeleri bulabilirsiniz.

Her ek derleme, daha yavaş makinelerde başlatmayı önemli ölçüde yavaşlatabilecek ek disk g/ç 'yi içereceği için, bir paket başlatma yordamı içinde yüklü derlemelerin sayısını en aza indirmek önemlidir.

## <a name="summary"></a>Özet

Visual Studio 'nun başlatılması, sürekli geri bildirim aldığımız alanlardan biridir. Daha önce belirtilen amaç, tüm kullanıcıların, yüklemiş oldukları bileşenlere ve uzantılara bakılmaksızın tutarlı bir başlangıç deneyimine sahip olmasını sağlamaktır. Bu amaca ulaşmamıza yardımcı olması için uzantı sahipleri ile çalışmak istiyoruz. Yukarıdaki yönergeler, başlangıçtaki bir uzantı etkisini anlamak ve Kullanıcı verimliliğiyle ilgili etkiyi en aza indirmek için onu zaman uyumsuz olarak yükleme veya yükleme gereksinimini ortadan kaldırabilir.
