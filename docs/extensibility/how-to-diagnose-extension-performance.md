---
title: 'Nasıl yapabilirsiniz: Uzantı performansını tanılama| Microsoft Docs'
description: Visual Studio yavaş uzantılar hakkında kullanıcılara bilgi sağlar. Uzantı etkisinin nasıl hesaplanmış olduğunu ve uzantı etkisinin yerel olarak nasıl analiz edilir olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- bertaygu
ms.openlocfilehash: e875075b4f2a060011746e9058ecec448efdbe58
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050370"
---
# <a name="measuring-extension-impact-in-startup"></a>Başlatmada uzantı etkisini ölçme

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Visual Studio 2017'de uzantı performansına odaklanma

Müşteri geri bildirimlerine dayanarak, 2017'nin Visual Studio alanlarından biri başlangıç ve çözüm yükü performansıdır. Platform Visual Studio olarak, başlangıç ve çözüm yük performansını geliştirmek için çalışıyoruz. Genel olarak, ölçümlerimiz yüklü uzantıların bu senaryolar üzerinde önemli bir etkisi olduğunu önermektedir.

Kullanıcıların bu etkiyi anlarına yardımcı olmak için, kullanıcılara yavaş Visual Studio bildirmek için yeni bir özellik ekledik. Bazen Visual Studio veya başlatmayı yavaşlatan yeni bir uzantı algılanabilir. Bir yavaşlama algılandığında, kullanıcılar IDE'de yeni "Performansı Yönet" iletişim kutusunu işaret Visual Studio bir bildirim alır. Bu iletişim kutusuna, önceden algılanan uzantılara göz atmak için yardım menüsü tarafından da erişilebilir.

![performans Visual Studio yönetme](media/manage-performance.png)

Bu belge, uzantı etkisinin nasıl hesaplanmasına yardımcı olmak için uzantı geliştiricilerine yardımcı olmak için tasarlanmıştır. Bu belgede ayrıca uzantı etkisinin yerel olarak nasıl analiz edilir? Uzantının etkisini yerel olarak analiz etmek, uzantının performansı etkileyen bir uzantı olarak gösterip gösterilene olmadığını belirler.

> [!NOTE]
> Bu belge, uzantıların başlangıç ve çözüm yükü üzerindeki etkisine odaklanır. Uzantılar, Visual Studio kullanıcı arabiriminin yanıt vermemeye neden olduğu zaman performansı da etkiler. Bu konu hakkında daha fazla bilgi için, [bkz. How to: Diagnose UI delays caused by extensions](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Uzantılar başlatmayı nasıl etkiler?

Uzantıların başlangıç performansını etkilemesi için en yaygın yöntemlerden biri, NoSolutionExists veya ShellInitialized gibi bilinen başlangıç kullanıcı arabirimi bağlamlarından birini otomatik olarak yüklemektir. Bu kullanıcı arabirimi bağlamları başlatma sırasında etkinleştirilir. Bu bağlamlarla tanımlarına özniteliğini içeren tüm paketler `ProvideAutoLoad` o anda yüklenir ve başlatılır.

Bir uzantının etkisini ölçtük, öncelikli olarak yukarıdaki bağlamlarda otomatik yüklemeyi seçen uzantılar tarafından harcanan zamanlara odaklanır. Ölçülen süreler şunları içerebilir ancak bunlarla sınırlı değildir:

* Zaman uyumlu paketler için uzantı derlemelerini yükleme
* Zaman uyumlu paketler için paket sınıfı oluşturucusnda harcanan süre
* Zaman uyumlu paketler için Initialize (veya SetSite) yönteminde harcanan süre
* Zaman uyumsuz paketler için yukarıdaki işlemler arka plan iş parçacığında çalışır.  Bu nedenle, işlemler izlemenin dışında tutulacak.
* Ana iş parçacığında çalışmak üzere paket başlatma sırasında zamanlanan herhangi bir zaman uyumsuz çalışmada harcanan süre
* Olay işleyicilerde, özellikle kabuk tarafından başlatılan bağlam etkinleştirme veya kabuk kabuk durumu değişikliğinde harcanan süre
* 2017 Güncelleştirme 3 Visual Studio den başlayarak, kabuk başlatılmadan önce boştaki çağrılarda harcanan izleme süresini de başlatmış oluruz. Boşta işleyicilerde uzun işlemler de yanıt vermemeye neden olur ve kullanıcı tarafından algılanan başlangıç süresine katkıda bulunabilirsiniz.

2015'te Visual Studio birçok özellik ekledik. Bu özellikler, paketlerin otomatik yükleme ihtiyacının ortadan kaldırılmasına yardımcı olur. Özellikler ayrıca paketlerin daha belirli durumlara yüklenme ihtiyacının ertelenmesini sağlar. Bu durumlar, kullanıcıların uzantıyı kullanmaya daha kesin olduğu veya otomatik olarak yüklenirken uzantı etkisini azaltan örnekler içerir.

Bu özellikler hakkında daha fazla ayrıntıyı aşağıdaki belgelerde bulabilirsiniz:

[Kural tabanlı UI bağlamları:](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)Ui bağlamları çerçevesinde yerleşik daha zengin bir kural tabanlı altyapı, proje türlerine, türlere ve özniteliklere göre özel bağlamlar oluşturmanıza olanak sağlar. Özel bağlamlar, daha belirli senaryolar sırasında bir paketi yüklemek için kullanılabilir. Bu belirli senaryolar, başlangıç yerine belirli bir özelliğe sahip bir projenin varlığını içerir. Özel bağlamlar, komut [görünürlüğünün proje bileşenlerine veya](visibilityconstraints-element.md) diğer kullanılabilir terimlere bağlı olarak özel bir bağlama bağlı olmasına da olanak sağlar. Bu özellik, bir komut durumu sorgu işleyicisini kaydetmek için paket yükleme ihtiyacı ortadan kaldırıyor.

[Zaman uyumsuz](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)paket desteği: Visual Studio 2015'te yeni AsyncPackage temel sınıfı, bir otomatik yükleme özniteliği veya zaman uyumsuz bir hizmet sorgusu tarafından paket yüklemesi istenen Visual Studio paketlerinin arka planda zaman uyumsuz olarak yüklenmelerine olanak sağlar. Bu arka plan yüklemesi, IDE'nin yanıt vermede kalmasını sağlar. Uzantı arka planda başlatılırken bile IDE yanıt verir ve başlangıç ve çözüm yükü gibi kritik senaryolar etkilenmez.

[Zaman uyumsuz hizmetler:](how-to-provide-an-asynchronous-visual-studio-service.md)Zaman uyumsuz paket desteğiyle, hizmetleri zaman uyumsuz olarak sorgulama ve zaman uyumsuz hizmetleri kaydetme desteği de ekledik. Daha da önemlisi, zaman uyumsuz sorgunun Visual Studio arka plan iş parçacıklarında gerçekleşmesi için çekirdek Visual Studio hizmetlerini zaman uyumsuz sorguyu destekleyecek şekilde dönüştürmeye çalışıyoruz. SComponentModel (Visual Studio MEF ana bilgisayarı), uzantıların zaman uyumsuz yüklemeyi tamamen desteklemesine olanak sağlayan zaman uyumsuz sorguyu destekleyen ana hizmetlerden biri.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Otomatik yüklenen uzantıların etkisini azaltma

Bir paketin başlangıçta hala otomatik olarak yüklenmiş olması gerekirse, paket başlatma sırasında yapılan işi en aza indirmek önemlidir. Paket başlatma çalışmalarını en aza indirmek, uzantının başlatmayı etkileme ihtimalini azaltır.

Paket başlatmanın pahalı olmasıyla ilgili bazı örnekler aşağıda verilmiştir:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Zaman uyumsuz paket yükü yerine zaman uyumlu paket yüklemesi kullanımı

Zaman uyumlu paketler varsayılan olarak ana iş parçacığına yüklendiğinden, otomatik yüklenen paketleri olan uzantı sahiplerini daha önce belirtildiği gibi zaman uyumsuz paket temel sınıfını kullanmaları için teşvik ettik. Otomatik yüklenen bir paketin zaman uyumsuz yüklemeyi destekleyecek şekilde değiştirilmesi, aşağıdaki diğer sorunların çözülmesini de kolaylaştırır.

### <a name="synchronous-filenetwork-io-requests"></a>Zaman uyumlu dosya/ağ IO istekleri

İdeal olarak tüm zaman uyumlu dosya veya ağ IO isteği ana iş parçacığında kaçınılmalıdır. Etkileri makine durumuna bağlıdır ve bazı durumlarda uzun süreler boyunca engellenmiş olabilir.

Zaman uyumsuz paket yükleme ve zaman uyumsuz IO API'lerinin kullanımı, paket başlatmanın bu tür durumlarda ana iş parçacığını engellemey olduğundan emin olun. Kullanıcılar ayrıca, arka planda I/Visual Studio istekleri olurken bu isteklerle etkileşime devam eder.

### <a name="early-initialization-of-services-components"></a>Hizmetleri, bileşenleri erken başlatma

Paket başlatmanın yaygın desenlerinden biri, tarafından kullanılan veya bu paket tarafından paket veya yöntemde sağlanan hizmetleri `constructor` `initialize` başlatmaktır. Bu, hizmetlerin kullanılmaya hazır olmasıyla birlikte, bu hizmetler hemen kullanılmazsa paket yüklemesi için gereksiz maliyetler de ekleyebilir. Bunun yerine, paket başlatmada yapılan işi en aza indirmek için bu tür hizmetler isteğe bağlı olarak başlatılmış olur.

Bir paket tarafından sağlanan genel hizmetler için, yalnızca bir bileşen tarafından istenerek hizmeti başlatan bir işlev alan `AddService` yöntemleri kullanabilirsiniz. Paket içinde kullanılan hizmetler için, hizmetlerin ilk kullanımda başlatılmış/sorgulanan olduğundan emin olmak için Yavaş veya \<T> AsyncLazy \<T> kullanabilirsiniz.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Etkinlik günlüğünü kullanarak otomatik yüklenen uzantıların etkisini ölçme

2017 güncelleştirme 3 Visual Studio den itibaren, Visual Studio etkinlik günlüğü artık başlatma ve çözüm yüklemesi sırasında paketlerin performans etkisine ait girdileri içerir. Bu ölçümleri görmek için /log anahtarıyla Visual Studio açmalı ve bir dosya *ActivityLog.xml* açabilirsiniz.

Etkinlik günlüğünde, girdiler "Performans Visual Studio Yönet" kaynağı altında olur ve aşağıdaki örnekteki gibi olur:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Bu örnekte GUID içeren bir paketin "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" guid'inin Visual Studio. Bu Visual Studio, bir paketin etkisini hesaplarken en üst düzey maliyeti birincil sayı olarak kabul ediyor. Bu, kullanıcıların bu paket için uzantıyı devre dışı bırakmaları sırasında göreceği tasarruf miktarıdır.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>PerfView kullanarak otomatik yüklenen uzantıların etkisini ölçme

Kod analizi, paket başlatmayı yavaşlatan kod yollarını tanımlamaya yardımcı olabilir ancak perfView gibi uygulamaları kullanarak izlemeden faydalanarak paket yüklemenin başlangıçtaki etkisini Visual Studio kullanabilirsiniz.

PerfView, sistem genelindeki bir izleme aracıdır. Bu araç, CPU kullanımı veya sistem çağrılarını engelleme nedeniyle uygulamanın hızlı yollarını anlamanıza yardımcı olur. Aşağıda, Microsoft İndirme Merkezi'nde bulunan PerfView kullanarak örnek bir uzantıyı analiz etmeyle ilgili hızlı [bir örnek verilmiştir.](https://www.microsoft.com/en-us/download/details.aspx?id=28567)

**Örnek kod:**

Bu örnek, bazı yaygın gecikme nedenlerini göstermek için tasarlanmış aşağıdaki örnek kodu temel almaktadır:

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

Uzantınız yüklü olarak Visual Studio ortamınızı ayarlayan, PerfView'u açarak ve Topla menüsünden  Topla iletişim kutusunu açarak başlatma izlemesi **kaydedebilirsiniz.**

![perfview toplama menüsü](media/perfview-collect-menu.png)

Varsayılan seçenekler CPU tüketimi için çağrı yığınları sağlar, ancak biz de zamanı engellemeyle ilgilendiğimiz için İş Parçacığı Süresi yığınlarını **da etkinleştirmeniz** gerekir. Ayarlar hazır olduğunda Koleksiyonu Başlat'a **tıklar** ve kayıt başladıktan sonra Visual Studio açabilirsiniz.

Koleksiyonu durdurmadan önce, Visual Studio, ana pencerenin tamamen görünür olduğundan ve uzantınız otomatik olarak görünen kullanıcı arabirimi parçalarına sahipse bunların da görünür olduğundan emin olmak istersiniz. Uzantı Visual Studio yüklendiğinde ve uzantınız başlatılmışsa, izlemeyi analiz etmek için kaydı durdurabilirsiniz.

**PerfView ile izleme analizi:**

Kayıt tamamlandıktan sonra PerfView izleme ve genişletme seçeneklerini otomatik olarak açar.

Bu örneğin amaçları doğrultusunda, daha çok Gelişmiş Grup altında bulabilirsiniz **İş** Parçacığı Zaman Yığınları **görünümüyle ilgileniyoruz.** Bu görünümde, hem CPU süresi hem de disk IO gibi engellenen süre veya tanıtıcıları bekleme gibi bir yöntem tarafından bir iş parçacığında harcanan toplam süre gösterir.

 ![iş parçacığı zaman yığınları](media/perfview-thread-time-stacks.png)

 İş Parçacığı **Zaman Yığınları görünümünü** a açma sırasında analizi başlatmak **için devenv** işlemini seçmeniz gerekir.

PerfView, daha ayrıntılı analiz için kendi Yardım menüsü altında iş parçacığı zaman yığınlarını okuma konusunda ayrıntılı kılavuza sahip. Bu örneğin amaçları doğrultusunda, yalnızca paket modülü adımıza ve başlangıç iş parçacığımıza sahip yığınları dahil etmek için bu görünümü daha fazla filtrelemek istiyoruz.

1. Varsayılan olarak eklenen tüm gruplamaları kaldırmak için **GroupPats'ı** boş metin olarak ayarlayın.
2. **IncPats'i** mevcut işlem filtresine ek olarak derlemenizin ve Başlangıç İş Parçacığının bir kısmını içerecek şekilde ayarlayın. Bu durumda, **devenv olması gerekir; Başlangıç İş Parçacığı; MakeVsSlowExtension**.

Artık görünüm yalnızca uzantıyla ilgili derlemelerle ilişkili maliyeti gösterir. Bu görünümde, başlangıç iş **parçacığının Inc (Kapsayıcı maliyet)** sütununda listelenen her zaman filtrelenmiş uzantımız ile ilgili olur ve başlatmayı etkiler.

Yukarıdaki örnekte bazı ilginç çağrı yığınları şöyle olabilir:

1. Sınıf kullanan IO: Bu karelerin kapsayıcı maliyeti izlemede çok pahalı olmayacaktır ancak dosyanın IO hızı makineden makineye değişe bir soruna `System.IO` yol açabilecektir.

   ![sistem io çerçeveleri](media/perfview-system-io-frames.png)

2. Diğer zaman uyumsuz işlerde bekleyen çağrıları engelleme: Bu durumda kapsayıcı süre, zaman uyumsuz çalışma tamamlandığında ana iş parçacığının engellenmiş olduğu zamanı temsil ediyor olabilir.

   ![çağrı çerçevelerini engelleme](media/perfview-blocking-call-frames.png)

İzlemede etkiyi belirlemek için yararlı olacak diğer görünümlerden biri Görüntü Yükleme **Yığınları olacaktır.** İş Parçacığı Zaman Yığınları  görünümüne uygulanan filtrelerin aynısını uygulayabilir ve otomatik yüklenen paketiniz tarafından yürütülen kod nedeniyle yüklenen tüm derlemeleri bulabilirsiniz.

Her ek derleme daha yavaş makinelerde başlatmayı önemli ölçüde yavaşlatan ek disk I/O'ları sürece dahil olduğundan, paket başlatma yordamı içinde yüklenen derlemelerin sayısını en aza indirmek önemlidir.

## <a name="summary"></a>Özet

Yeni Visual Studio sürekli geri bildirim alan alanlardan biri oldu. Daha önce belirtildiği gibi hedefimiz, tüm kullanıcıların yüklemiş olduğu bileşenlerden ve uzantılardan bağımsız olarak tutarlı bir başlangıç deneyimine sahip olmasıdır. Bu hedefe ulaşmamıza yardımcı olmak için uzantı sahipleriyle birlikte çalışmak istiyorum. Yukarıdaki kılavuz, uzantıların başlatma üzerindeki etkisini anlama ve kullanıcı üretkenliği üzerindeki etkiyi en aza indirmek için zaman uyumsuz olarak yükleme veya otomatik yükleme ihtiyacının önüne geçilmesi konusunda yardımcı olacaktır.
