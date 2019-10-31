---
title: UWP uygulamalarında ağ kullanımını analiz etme
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
ms.sourcegitcommit: bdccab4c2dbd50ea8adaaf88c69c9ca32db88099
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144691"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>UWP uygulamalarında ağ kullanımını analiz etme
Visual Studio **ağ** Tanılama Aracı, [Windows. Web. http API 'si](/uwp/api/windows.web.http)kullanılarak gerçekleştirilen ağ işlemleriyle ilgili verileri toplar. Verilerin çözümlenmesi, erişim ve kimlik doğrulama sorunları, yanlış önbellek kullanımı ve kötü ekran ve indirme performansı gibi sorunları çözmenize yardımcı olabilir.

 Ağ aracı yalnızca UWP uygulamalarını destekler. Diğer platformlar Şu anda desteklenmiyor.

> [!NOTE]
> Ağ aracının daha ayrıntılı bir açıklaması için bkz. [Visual Studio 'nun Ağ aracını tanıtma](https://devblogs.microsoft.com/visualstudio/introducing-visual-studios-network-tool/).

## <a name="collect-network-tool-data"></a>Ağ aracı verilerini topla
 **Ağ** aracını Visual Studio bilgisayarında açık bir Visual Studio projesiyle çalıştırmalısınız.

1. Projeyi Visual Studio 'da açın.

2. Menüsünde **Hata Ayıkla/performans profili Oluşturucu ' ya**tıklayın. **Ağ**' ı seçin ve ardından **Başlat**' ı seçin.

3. Ağ aracı, uygulamanızın HTTP trafiğini toplamaya başlar.

    Uygulamanızı çalıştırırken, sol bölmedeki Özet görünümü, yakalanan HTTP işlemlerinin bir listesini otomatik olarak görüntüler. Sağ bölmedeki Ayrıntılar panelinde daha fazla bilgi görmek için Özet görünümünde bir öğe seçin.

4. Uygulamayı kapatmak için **Durdur** ' ı seçin.

   Rapor penceresi şuna benzer şekilde görünmelidir:

   ![Ağ penceresi](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")

## <a name="analyze-data"></a>Verileri çözümleme
 Uygulamanızın çalıştığı sırada veya uygulama kapatıldıktan sonra bile, Özet görünümünde görünen ağ işlemlerinden herhangi birini seçerek yakalanan HTTP trafiğini çözümleyebilirsiniz.

 **Ağ** Özeti Görünümü, uygulamanızın çalıştırıldığı her bir ağ işleminin verilerini gösterir. Listeyi sıralamak için bir sütun üst bilgisi seçin ya da **Içerik türü** filtre görünümünde görüntülenecek içerik türlerini seçin.

 Fiddler gibi üçüncü taraf araçları tarafından tüketilen bir JSON dosyası oluşturmak için **farklı kaydet har** ' ı seçin.

 **Ağ** ayrıntıları görünümleri Özet görünümünde bir ağ işlemi hakkında daha fazla bilgi görüntüler.

 ![Ağ aracı ayrıntıları bölmesi](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")

|||
|-|-|
|**Bilgisinde**|Olayın istek üstbilgileri hakkında bilgi.|
|**Bölümü**|İstek ve yanıt yükü verileri.|
|**Parametreler**|Sorgu dizesi parametre adları ve değerleri.|
|**Çerezler**|Yanıt ve istek tanımlama bilgisi verileri.|
|**Zamanlama**|Seçilen kaynakları alırken aşamaların bir grafiği.|

 Ağ **Özet** çubuğu, herhangi bir noktada görüntülenen ağ işlemlerinin sayısını, ne kadar veri aktarıldığını, ne kadar zaman aktarılacağını ve kaç hatanın (4xx veya 5xx yanıtı) görünür olduğunu gösterir.

### <a name="analysis-tips"></a>Analiz ipuçları
 Bu araç, ağla ilgili analizler çalıştırırken yararlı olabilecek bazı alanı vurgular:

1. Önbellekten tam olarak sunulan istekler **alındı** sütununda **(önbellekten)** olarak gösterilir. Bu, önbelleği Kullanıcı bant genişliğini kaydetmek için etkin bir şekilde kullanıp kullanmayacağınızı ya da yanıtları yanlışlıkla önbelleğe alma ve güncel olmayan verilerle uygulamanızın son kullanıcısını sağlama işlemleri yapılıp yapılmayacağını belirlemenize yardımcı olabilir.

2. Hata yanıtları (4xx veya 5xx), **sonuçlar** sütununda kırmızı durum kodu ile görüntülenir ve ayrıca Özet çubuğunda vurgulanır. Bu, uygulamanızdaki birçok olası istek arasında hata belirlemeyi kolaylaştırır.

3. Yanıt oldukça yazdırma düğmesi (gövde sekmesi içinde), içeriğin okunabilirliğini artırarak JSON, XML, HTML, CSS, JavaScript ve TypeScript yanıt yükleri aracılığıyla ayrıştırmanıza yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçları çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Visual Studio blogu: Visual Studio 'nun ağ denetçisini tanıtma](https://devblogs.microsoft.com/visualstudio/)
- [Channel 9 videosu: VS tanılama araçları-yeni ağ profili Oluşturucu](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
- [Visual Studio 'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)