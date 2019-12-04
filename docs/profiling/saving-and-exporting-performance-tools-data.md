---
title: Performans araçları verilerini kaydetme ve dışarı aktarma | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773905"
---
# <a name="save-and-export-performance-tools-data"></a>Performans araçları verilerini kaydetme ve dışarı aktarma
Bu makalede, performans veri dosyalarının nasıl kaydedileceği ve dışarı aktarılacağı açıklanır.

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Nasıl yapılır: performans veri dosyalarını çözümlenmiş rapor dosyaları olarak kaydetme
 Profil oluşturma verilerinin filtrelenmiş veya filtrelenmemiş görünümlerini kaydedebilirsiniz (. *VSP*) Çözümlenmiş rapor (. *vsps*) dosyaları. Analiz edilen rapor dosyası rapor görünümü penceresinde görüntülenebilir ve orijinalden önemli ölçüde küçüktür. *VSP* dosyası. Ancak, bir ' a ait verilere filtre uygulayamazsınız. *vsps* dosyası. Dosyayı tümleşik geliştirme ortamında (IDE) açmadan Performans Gezgini analiz edilen bir rapor dosyası oluşturabilir veya öğesini açıp filtrelemeniz sağlayabilirsiniz. *VSP* dosyası ve sonra sonuçları kaydedin.

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Analiz edilen bir performans raporunu Performans Gezgini kaydetmek için

1. **Raporlar**' ın altında, analiz etmek istediğiniz profil oluşturma veri dosyasına sağ tıklayın ve ardından **Çözümlenmiş**' e tıklayın.

2. **Çözümlenen verileri kaydet** iletişim kutusunda, dizini belirtin ve ardından dosya adını yazın.

3. Kaydet ' e tıklayın **.**

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Analiz edilen bir performans raporunu rapor görünümü penceresinden kaydetme

1. Profil oluşturma verilerini açın (. *VSP*) dosyasını rapor görünümü penceresinde görebilirsiniz.

2. Seçim Verilere filtre uygulayın. Daha fazla bilgi için bkz. [Performans raporu görünüm filtresi](../profiling/performance-report-view-filter.md).

3. Rapor görünümü penceresi araç çubuğunda **analiz kaydet** ' e tıklayın.

4. **Çözümlenen verileri kaydet** iletişim kutusunda, dizini belirtin ve ardından dosya adını yazın.

5. Kaydet ' e tıklayın **.**

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Nasıl yapılır: profil araçları raporlarını bir. xml veya. csv dosyasına dışarı aktarma
 ' Dan bir veya daha fazla rapor görünümü dışarı aktarabilirsiniz. *VSP* dosyası veya bir. *vsps* profil oluşturma veri dosyası virgülle ayrılmış veya bir XML dosyası olarak. Dışarı aktarmadan önce rapor görünümü penceresindeki verileri filtreleyebilir veya tüm veri dosyasının rapor görünümlerini **Performans Gezgini** penceresinden dışarı aktarabilirsiniz.

> [!NOTE]
> Ayrıca, seçili satırları, sekme ile ayrılmış değerler olarak rapor görünümü penceresinden kopyalayabilir ve yapıştırabilirsiniz.

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Performans Gezgini penceresinden performans raporlarını dışarı aktarmak için

1. **Performans Gezgini**, raporu seçin ve ardından sağ tıklayıp **dışarı aktar**' ı seçin.

     **Raporu dışarı aktar** iletişim kutusu görünür.

2. Dışarı aktarmak istediğiniz rapor görünümlerini seçin.

3. **Ile önek raporu**' nun altında, rapor adına eklemek istediğiniz öneki belirtin.

4. **Verdiğiniz rapor konumu**altında, dizini belirtin.

5. **Aktarılmış rapor biçimi**altında (virgülle sınırlandırılmış) (\*. csv\)veya XML verisi (\*. xml\)seçin.

6. **Dışarı aktar**' a tıklayın.

     Her rapor görünümü, \<önek > _\<rapor görünümü adı > olarak adlandırılan ayrı bir dosyaya kaydedilir.\<CSV&#124;XML >

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Performans raporlarını rapor görünümü penceresinden dışarı aktarmak için

1. Öğesini açın. Rapor Görünümü penceresinde *VSP* dosyası.

2. Seçim Verilere filtre uygulayın. Daha fazla bilgi için bkz. [Performans raporu görünüm filtresi](../profiling/performance-report-view-filter.md).

3. Rapor görünümü penceresi araç çubuğunda **raporu dışarı aktar** ' a tıklayın.

4. Dışarı aktarmak istediğiniz rapor görünümlerini seçin.

5. **Ile önek raporu**' nun altında, rapor adına eklemek istediğiniz öneki belirtin.

6. **Verdiğiniz rapor konumu**altında, dizini belirtin.

7. **Aktarılmış rapor biçimi**altında (virgülle sınırlandırılmış) (\*. csv) veya XML verisi (\*. xml) seçeneğini belirleyin.

8. **Dışarı aktar**' a tıklayın.

     Her rapor görünümü, \<önek > _\<rapor görünümü adı > olarak adlandırılan ayrı bir dosyaya kaydedilir.\<CSV&#124;XML >

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
- [Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
- [Performans veri dosyalarını karşılaştırma](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)
