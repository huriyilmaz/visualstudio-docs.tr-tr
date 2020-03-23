---
title: Rapor Görünümlerini Filtreleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: acdfe8f96d30ad881d8c9c0f0a9ff48c3353afee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779252"
---
# <a name="filter-report-views"></a>Rapor görünümlerini filtreleme
Performans Raporu görünümlerinde görüntülenen ve rapor dosyalarına dışa aktarılan profil oluşturma verilerini sınırlamak için veri dosyalarını profil oluşturmaya filtreler uygulayabilirsiniz. Bir raporu zaman damgası değerleri arasındaki verilerle sınırlayabilir ve verileri belirli işlemler ve iş parçacıklarıyla sınırlayabilirsiniz. Filtreleri bir dosyaya kaydedebilir ve sonra kaydedilen filtreyi içe aktararak farklı bir profil oluşturma veri dosyasında bir filtre oluşturabilirsiniz.

 Özet Görünümü'ndeki grafik zaman çizelgesini kullanarak raporu bir zaman segmenti ile de sınırlayabilirsiniz. [Bkz. Nasıl: Özet Zaman Çizelgesinden Rapor Görünümlerini Filtreleyin.](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)

 Sistem ve üçüncü taraf kodunu bir rapordan hariç tutmak [için bkz: Profil Oluşturma Araçları Yalnızca Kodumu Görüntülemek Için Profil Oluşturma Araçları Rapor Görünümlerini Filtrele](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)

## <a name="procedures"></a>Yordamlar

#### <a name="to-create-a-profiler-report-filter"></a>Profil oluşturucu rapor filtresi oluşturmak için

1. Performans Raporu Görünümü Filtresi penceresi görüntülenmiyorsa, Performans Raporu Görünümü araç çubuğunda **Filtreyi Göster'i** tıklatın.

     Performans Raporu Görünüm Filtresi bir tablodur. Tablonun her satırı filtrenin bir yan tümcesini temsil eder. Bir filtreye istediğiniz kadar yan tümce ekleyebilirsiniz.

2. Bir filtreye eklemek istediğiniz her yan tümce için, bir satırın aşağıdaki alanlarındadeğerleri seçin veya girin.

    |Alan|Açıklama|
    |-----------|-----------------|
    |**Veya**|Bu **And** yan tümce nin ve bir sonraki tümcenin bir sonuca uyacak şekilde doğru olması gerekiyorsa ve seçin. Bu **Or** yan tümcenin veya bir sonraki yan tümcenin bir sonuca uyacak şekilde doğru olup olmadığını seçin.|
    |**Alan**|Görüntülenen veri alanları listesinden filtre yan tümcesinde kullanılacak rapor alanını seçin.|
    |**Işleç**|Alan ve değer arasındaki yan tümcede istediğiniz ilişkiyi belirten işleci seçin.<br /><br /> = Eşittir<br /><br /> <>  Eşit Değil<br /><br /> < Az<br /><br /> > Büyük<br /><br /> <= Az veya Eşittir<br /><br /> >= Büyük veya Eşittir|
    |**Değer**|Arayacakdeğeri seçin veya girin. Bazı alanlar, alan için kullanılabilir değerleri listeler.|

#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Marks Raporu görünümünden profil oluşturucu raporu filtresi oluşturmak için

1. Performans Raporu Görünümü araç çubuğundaki **Geçerli Görünüm** listesinden **İşaretler'i** seçin.

    Marks profil oluşturucu raporu görüntülenir.

2. Raporun başlangıç noktası olarak kullanmak istediğiniz ETW'yi veya örneklemeyi seçin.

3. CTRL tuşuna basın ve basılı tutun ve raporun bitiş noktası olarak kullanmak istediğiniz olayı tıklatın.

4. Sağ tıklatın ve ardından aşağıdaki seçeneklerden birini tıklatın:

   - **İşaretler üzerine Filtre Ekle,** Filtre alanı olarak Mark sütununa sahip filtre yan tümceleri oluşturur.

   - **Zaman Damgalarına Filtre Ekle,** Zaman Damgası Milisaniye cinsinden sütunu filtre alanı olarak kullanan filtre yan tümceleri oluşturur.

     İki seçenek, geçerli veri dosyasını aynı başlangıç ve bitiş noktalarında filtreler. Filtreyi diğer raporlarda kullanmak üzere dışa aktarSanız, her iki seçenek de daha iyi olabilir.

#### <a name="to-load-an-existing-filter-from-a-file"></a>Varolan bir filtreyi bir dosyadan yüklemek için

1. Performans Raporu Görünüm araç çubuğunda, **Filtreyi İçe Aktar'ı**tıklatın.

     **Yük Filtresi** iletişim kutusu görüntülenir.

2. Yüklenmesi gereken filtre (.vspf) dosyasının konumunu ve dosya adını belirtin.

#### <a name="to-execute-a-filter"></a>Bir filtreyi çalıştırmak için

- Performans Raporu Görünüm araç çubuğunda, **Filtreyi Yürüt'e**tıklayın.

#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Çalıştırılamayacak kadar uzun süren bir filtreyi durdurmak için

- Performans Raporu Görünüm araç çubuğunda **Filtreyi Durdur'u**tıklatın.

#### <a name="to-remove-a-filter-on-a-report-view"></a>Rapor görünümünde filtreyi kaldırmak için

1. Performans Raporu Görünümü Filtresi'ndeki yan tümce satırlarını silin.

2. Performans Raporu Görünüm araç çubuğunda, **Filtreyi Yürüt'e**tıklayın.

#### <a name="to-save-a-filter-to-a-file"></a>Filtreyi dosyaya kaydetmek için

1. Performans Raporu Görünüm araç çubuğunda **Dışa Aktar Filtresi'ni**tıklatın.

     **Filtreyi Kaydet** iletişim kutusu görüntülenir.

2. Kaydetmek için filtrenin (.vspf) dosyanın konumunu ve dosya adını belirtin.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Araçları Rapor Görünümlerini Özelleştirme](../profiling/customizing-performance-tools-report-views.md)
