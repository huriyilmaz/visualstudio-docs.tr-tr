---
title: UWP uygulamalarında ağ kullanımını analiz etme
description: Visual Studio Tanılama aracının ağ tanılama aracı kullanılarak gerçekleştirilen ağ işlemleri hakkında nasıl veri top Windows. Web.Http API'si.
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: ed223022d9d9d8033f854247815f44cb3531df83
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141655"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>UWP uygulamalarında ağ kullanımını analiz etme
Ağ Visual Studio **aracı,** ağ tanılama aracı kullanılarak gerçekleştirilen ağ işlemleriyle ilgili [Windows. Web.Http API'si](/uwp/api/windows.web.http). Verileri analiz etmek, erişim ve kimlik doğrulaması sorunları, yanlış önbellek kullanımı, düşük görüntü ve indirme performansı gibi sorunları çözmenize yardımcı olabilir.

 Ağ aracı yalnızca UWP uygulamalarını destekler. Diğer platformlar şu anda desteklenmiyor.

> [!NOTE]
> Ağ aracının daha eksiksiz bir açıklaması için [bkz. Visual Studio'nin ağ aracına tanıtma.](https://devblogs.microsoft.com/visualstudio/introducing-visual-studios-network-tool/)

## <a name="collect-network-tool-data"></a>Ağ aracı verilerini toplama
 Ağ aracını, **Visual Studio** bilgisayarda açık bir Visual Studio projesiyle Visual Studio gerekir.

1. Projeyi Visual Studio'da açın.

2. Menüde Hata Ayıkla **/Hata Ayıkla'ya Performans Profili Oluşturucu.** **Ağ'ı** ve ardından Başlat'ı **seçin.**

3. Ağ aracı, uygulamanın HTTP trafiğini toplamaya başlar.

    Siz uygulamayı çalıştırarak sol bölmede özet görünümü otomatik olarak yakalanan HTTP işlemlerinin listesini görüntüler. Sağ bölmede ayrıntılar panelinde daha fazla bilgi görmek için özet görünümünden bir öğe seçin.

4. Uygulamayı **kapatmak** için Durdur'a seçin.

   Rapor penceresi aşağıdakine benzer görünse:

   ![Ağ penceresi](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")

## <a name="analyze-data"></a>Verileri çözümleme
 Özet görünümünde görüntülenen ağ işlemlerden herhangi birini seçerek, yakalanan HTTP trafiğini, uygulama çalışırken veya uygulama kapatıldıktan sonra bile analiz edin.

 Ağ **özeti** görünümü, uygulama çalıştırması sırasındaki her ağ işlemi için verileri gösterir. Listeyi sıralamak için bir sütun üst bilgisi seçin veya İçerik Türü filtre görünümünde **görüntülemek istediğiniz içerik türlerini** seçin.

 Fiddler gibi üçüncü taraf araçlar tarafından tüketilebilir bir JSON dosyası oluşturmak için **HAR** olarak kaydet'i seçin.

 Ağ **ayrıntıları** görünümleri özet görünümünde bir ağ işlemi hakkında daha fazla bilgi görüntüler.

 ![Ağ aracı ayrıntıları bölmesi](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")

|Ad|Açıklama|
|-|-|
|**Üst Bilgiler**|Olayın istek üst bilgileri hakkında bilgi.|
|**Gövde**|İstek ve yanıt yükü verileri.|
|**Parametreler**|Sorgu dizesi parametre adları ve değerleri.|
|**Kurabiye**|Tanımlama bilgisi verilerine yanıt ve istek.|
|**Zamanlama**|Seçilen kaynakları edinen aşamaların grafiği.|

 Ağ **özet** çubuğu herhangi bir noktada görüntülenen ağ işlemlerinin sayısını, ne kadar verinin aktarıldığına, bunları indirmenin ne kadar zaman ağına ve kaç hatanın (4xx veya 5xx yanıtına sahip istekler) görünür olduğunu gösterir.

### <a name="analysis-tips"></a>Analiz ipuçları
 Bu araç, ağ ile ilgili analizler çalıştırıyorsanız yararlı olacak belirli alanları vurgular:

1. Önbellekten tam olarak sunulan istekler, Alınan sütununda **(önbellekten)** **olarak** gösterilir. Bu, kullanıcı bant genişliğinden tasarruf etmek için önbelleği etkili bir şekilde mi, yoksa yanıtları yanlışlıkla önbelleğe mi asanız ve son kullanıcıya uygulamanın son kullanıcıya süresiz veriler mi sağlıyorsanız belirlemenize yardımcı olabilir.

2. Hata yanıtları (4xx veya 5xx),  Sonuçlar sütununda kırmızı durum koduyla görüntülenir ve özet çubuğunda da vurgulanır. Bu, uygulamanıza yapılan çok sayıda olası istek arasında hataların tespitini kolaylaştırır.

3. Yanıt düzgün yazdırma düğmesi (gövde sekmesinin içinde) içeriğin okunabilirliğini artırarak JSON, XML, HTML, CSS, JavaScript ve TypeScript yanıt yüklerini ayrıştırmanıza yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçları çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Visual Studio blog: Visual Studio'nin ağ denetçisi ile tanışma](https://devblogs.microsoft.com/visualstudio/)
- [Channel 9 Video: VS tanılama araçları - yeni Ağ Profili Oluşturma](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
- [Visual Studio'de profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)