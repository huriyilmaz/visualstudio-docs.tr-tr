---
title: Performans Araçları Verilerini Kaydetme ve Dışa Aktarma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 729dc2e28446420dd2590e132b7ec8a5444fcb9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773905"
---
# <a name="save-and-export-performance-tools-data"></a>Performans araçları verilerini kaydetme ve dışarı aktarma
Bu makalede, performans veri dosyalarının nasıl kaydedilip dışa aktarılacak şekilde kaydedilen ve dışa aktarılabilmek açıklanmaktadır.

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Nasıl kullanılır: Performans veri dosyalarını çözümlenmiş rapor dosyaları olarak kaydetme
 Profil oluşturma verilerinin filtrelenmiş veya filtrelenmemiş görünümlerini kaydedebilirsiniz (.* vsp*) dosyaları analiz raporu olarak (.* vsps*) dosyaları. Çözümlenen rapor dosyası Rapor görünümü penceresinde görüntülenebilir ve orijinaldosyadan önemli ölçüde daha küçüktür. *vsp* dosyası. Ancak, bir ' in verilerine bir filtre uygulayamazsınız. *vsps* dosyası. Tümleşik geliştirme ortamında (IDE) dosyayı açmadan Performans Gezgini'nden çözümlenmiş bir rapor dosyası oluşturabilir veya 'yi açıp filtreleyebilirsiniz. *vsp* dosya ve sonra sonuçları kaydedin.

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Çözümlenmiş bir performans raporunu Performans Gezgini'nden kaydetmek için

1. **Raporlar**altında, çözümlemek istediğiniz profil oluşturma veri dosyasını sağ tıklatın ve ardından **Çözümlü Kaydet'i**tıklatın.

2. **Çözümlenmiş Verileri Kaydet** iletişim kutusunda, dizini belirtin ve ardından dosya adını yazın.

3. **Kaydet'i tıklatın.**

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Çözümlenmiş bir performans raporunu Rapor görünümü penceresinden kaydetmek için

1. Profil oluşturma verilerini açın (.* vsp*) dosyası Rapor görünümü penceresinde.

2. (İsteğe bağlı) Verilere filtre uygulayın. Daha fazla bilgi için Bkz. [Performans raporu görünüm filtresi.](../profiling/performance-report-view-filter.md)

3. Rapor görünümü penceresinde **Çözümle çözümle'yi tıklatın.**

4. **Çözümlenmiş Verileri Kaydet** iletişim kutusunda, dizini belirtin ve ardından dosya adını yazın.

5. **Kaydet'i tıklatın.**

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Nasıl yapilir: Profil oluşturma araçları raporlarını bir .xml veya .csv dosyasına dışa aktarma
 Bir veya daha fazla rapor görünümü dışa aktarabilirsiniz. *vsp* dosyası veya . *vsps* profil oluşturma veri dosyası ya virgül delimited veya bir XML dosyası olarak. Dışa aktarmadan önce Rapor görünümü penceresindeki verileri filtreleyebilir veya **Performans Gezgini** penceresinden tüm veri dosyasının rapor görünümlerini dışa aktarabilirsiniz.

> [!NOTE]
> Ayrıca, seçili satırları Rapor görünümü penceresinden sekme ayrılmış değerler olarak kopyalayıp yapıştırabilirsiniz.

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Performans Gezgini penceresinden performans raporları dışa aktarmak için

1. **Performans Gezgini'nde,** raporu seçin ve sonra sağ tıklatın ve **Dışa Aktar'ı**seçin.

     **Dışa** Aktarma Raporu iletişim kutusu görüntülenir.

2. Dışa aktarmak istediğiniz rapor görünümlerini seçin.

3. **Önek raporu**altında, rapor adına eklemek istediğiniz önek belirtin.

4. **Dışa Aktarılan rapor konumu**altında, dizini belirtin.

5. **Dışa aktarılan rapor biçimi**altında ,\*select (Virgül le sınırlı) ( .csv\)veya XML Verileri (\*.xml\).

6. **Dışarı aktar**'a tıklayın.

     Her rapor görünümü, rapor görünümü adı \<>\<>_ öneki adlı ayrı bir dosyaya kaydedilir. \<csv&#124;xml>

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Rapor görünümü penceresinden performans raporları dışa aktarmak için

1. Açın. rapor görünümü penceresinde *vsp* dosyası.

2. (İsteğe bağlı) Verilere filtre uygulayın. Daha fazla bilgi için Bkz. [Performans raporu görünüm filtresi.](../profiling/performance-report-view-filter.md)

3. Rapor görünümü araç çubuğunda **Dışa** Aktar Raporu'nu tıklatın.

4. Dışa aktarmak istediğiniz rapor görünümlerini seçin.

5. **Önek raporu**altında, rapor adına eklemek istediğiniz önek belirtin.

6. **Dışa Aktarılan rapor konumu**altında, dizini belirtin.

7. **Dışa Aktarılan rapor biçimi**altında ,\*(Virgül lesınırlı) (.csv) veya XML Verileri (.xml)\*seçin.

8. **Dışarı aktar**'a tıklayın.

     Her rapor görünümü, rapor görünümü adı \<>\<>_ öneki adlı ayrı bir dosyaya kaydedilir. \<csv&#124;xml>

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
- [Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
- [Performans veri dosyalarını karşılaştırma](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)
