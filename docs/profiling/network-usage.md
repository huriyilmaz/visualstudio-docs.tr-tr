---
title: UWP uygulamalarında ağ kullanımını analiz edin
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 16c17c6f39980b115b34869fdc6b4912ca94ab0b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73144691"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>UWP uygulamalarında ağ kullanımını analiz edin
Visual Studio **Network** tanılama [aracı, Windows.Web.Http API](/uwp/api/windows.web.http)kullanılarak gerçekleştirilen ağ işlemleri hakkında veri toplar. Verileri çözümleme, erişim ve kimlik doğrulama sorunları, yanlış önbellek kullanımı ve düşük görüntüleme ve indirme performansı gibi sorunları çözmenize yardımcı olabilir.

 Ağ aracı yalnızca UWP uygulamalarını destekler. Diğer platformlar şu anda desteklenmez.

> [!NOTE]
> Ağ aracının daha eksiksiz bir açıklaması için [Visual Studio'nun ağ aracını tanıtın](https://devblogs.microsoft.com/visualstudio/introducing-visual-studios-network-tool/)bölümüne bakın.

## <a name="collect-network-tool-data"></a>Ağ aracı verilerini toplama
 **Network** aracını Visual Studio bilgisayarında açık bir Visual Studio projesiyle çalıştırmalısınız.

1. Projeyi Visual Studio'da açın.

2. Menüde Hata **Ayıklama / Performans Profilleyici'sini**tıklatın. **Ağ'ı**seçin ve ardından **Başlat'ı**seçin.

3. Ağ aracı uygulamanızın HTTP trafiğini toplamaya başlar.

    Uygulamanızı çalıştırdığınızda, sol bölmedeki özet görünümü otomatik olarak yakalanan HTTP işlemlerinin listesini görüntüler. Sağ bölmedeki ayrıntılar panelinde daha fazla bilgi görmek için özet görünümünde bir öğe seçin.

4. Uygulamayı kapatmak için **Dur'u** seçin.

   Rapor penceresi aşağıdaki gibi görünmelidir:

   ![Ağ penceresi](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")

## <a name="analyze-data"></a>Verileri çözümleme
 Yakalanan HTTP trafiğini, uygulamanız çalışırken veya uygulama kapatıldıktan sonra bile özet görünümünde görüntülenen ağ işlemlerinden herhangi birini seçerek analiz edebilirsiniz.

 **Ağ** özeti görünümü, uygulamanızın çalışmasındaki her ağ işlemiiçin verileri gösterir. Listeyi sıralamak için bir sütun üstbilgiseçin veya **İçerik Türü** filtresi görünümünde görüntülenecek içerik türlerini seçin.

 Fiddler gibi üçüncü taraf araçlar tarafından tüketilebilen bir JSON dosyası oluşturmak için **HAR olarak kaydet'i** seçin.

 **Ağ** ayrıntıları görünümleri özet görünümünde bir ağ işlemi hakkında daha fazla bilgi görüntüler.

 ![Ağ aracı ayrıntıları bölmesi](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")

|||
|-|-|
|**Üst Bilgiler**|Olayın istek üstbilgileri hakkında bilgi.|
|**Gövde**|İstek ve yanıt yükü verileri.|
|**Parametre**|Sorgu dize parametre adları ve değerleri.|
|**Çerezler**|Yanıt ve istek çerez verileri.|
|**Zamanlama**|Seçili kaynakları edinme aşamalarının grafiği.|

 Ağ **özeti** çubuğu, belirli bir noktada görüntülenen ağ işlemleri sayısını, ne kadar veri aktarıldığını, bunları karşıdan yüklemenin ne kadar sürdüğünü ve kaç hata (4xx veya 5xx yanıtı içeren istekler) görünür olduğunu gösterir.

### <a name="analysis-tips"></a>Analiz ipuçları
 Bu araç, ağla ilgili çözümlemesi çalıştırırken yararlı olabilecek belirli alanları vurgular:

1. Önbellekten tam olarak sunulan **istekler, Alınan** sütunda **(önbellekten)** olarak gösterilir. Bu, önbelleği kullanıcı bant genişliğini kaydetmek için etkili bir şekilde kullanıp kullanmadığınızı veya yanıtları yanlışlıkla önbelleğe alıp almadığınızı ve uygulamanızın son kullanıcısını eski verilerle mi sağladığınızı belirlemenize yardımcı olabilir.

2. Hata yanıtları (4xx veya 5xx) **Sonuçlar** sütununda kırmızı durum koduyla görüntülenir ve özet çubuğunda da vurgulanır. Bu, uygulamanızdaki birçok olası istek arasında hataları tespit etmeyi kolaylaştırır.

3. Yanıt oldukça yazdırma düğmesi (gövde sekmesi içinde) içeriğin okunabilirliğini artırarak JSON, XML, HTML, CSS, JavaScript ve TypeScript yanıt yükleri ile ayrıştırmak yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçları çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Visual Studio blog: Visual Studio ağ müfettişi tanıtımı](https://devblogs.microsoft.com/visualstudio/)
- [Kanal 9 Video: VS tanılama araçları - yeni Network Profiler](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
- [Visual Studio'da Profil Oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)