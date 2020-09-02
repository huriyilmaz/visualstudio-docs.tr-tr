---
title: Performans araçları verilerini kaydetme ve dışarı aktarma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3be6d5d732e5cbb2050c68ac8c7db722c3f709f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795242"
---
# <a name="saving-and-exporting-performance-tools-data"></a>Performans Araçları Verilerini Kaydetme ve Dışarı Aktarma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, performans veri dosyalarının nasıl kaydedileceği ve dışarı aktarılacağı açıklanmaktadır.  
  
## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a><a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Nasıl yapılır: performans veri dosyalarını çözümlenmiş rapor dosyaları olarak kaydetme  
 Profil oluşturma veri (. vsp) dosyaları için filtrelenmiş veya filtrelenmemiş görünümleri analiz edilen rapor (. vsps) dosyaları olarak kaydedebilirsiniz. Analiz edilen rapor dosyası rapor görünümü penceresinde görüntülenebilir ve özgün. vsp dosyasından önemli ölçüde küçüktür. Ancak, bir. vsps dosyasının verilerine filtre uygulayamazsınız. Dosyayı tümleşik geliştirme ortamında (IDE) açmadan Performans Gezgini analiz edilebilir bir rapor dosyası oluşturabilir veya. vsp dosyasını açıp filtreleyip sonuçları kaydedebilirsiniz.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Analiz edilen bir performans raporunu Performans Gezgini kaydetmek için  
  
1. **Raporlar**' ın altında, analiz etmek istediğiniz profil oluşturma veri dosyasına sağ tıklayın ve ardından **Çözümlenmiş**' e tıklayın.  
  
2. **Çözümlenen verileri kaydet** iletişim kutusunda, dizini belirtin ve ardından dosya adını yazın.  
  
3. Kaydet ' e tıklayın **.**  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Analiz edilen bir performans raporunu rapor görünümü penceresinden kaydetme  
  
1. Profil oluşturma verileri (. vsp) dosyasını rapor görünümü penceresinde açın.  
  
2. Seçim Verilere filtre uygulayın. Daha fazla bilgi için bkz. [Performans raporu görünüm filtresi](../profiling/performance-report-view-filter.md).  
  
3. Rapor görünümü penceresi araç çubuğunda **analiz kaydet** ' e tıklayın.  
  
4. **Çözümlenen verileri kaydet** iletişim kutusunda, dizini belirtin ve ardından dosya adını yazın.  
  
5. Kaydet ' e tıklayın **.**  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Nasıl yapılır: Profil Oluşturma Araçları raporlarını bir öğesine aktarma. XML veya. CSV dosyası  
 Bir. vsp dosyasından veya. vsps profil oluşturma veri dosyasından bir veya daha fazla rapor görünümünü virgülle ayrılmış veya bir XML dosyası olarak dışarı aktarabilirsiniz. Dışarı aktarmadan önce rapor görünümü penceresindeki verileri filtreleyebilir veya tüm veri dosyasının rapor görünümlerini **Performans Gezgini** penceresinden dışarı aktarabilirsiniz.  
  
> [!NOTE]
> Ayrıca, seçili satırları, sekme ile ayrılmış değerler olarak rapor görünümü penceresinden kopyalayabilir ve yapıştırabilirsiniz.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Performans Gezgini penceresinden performans raporlarını dışarı aktarmak için  
  
1. **Performans Gezgini**, raporu seçin ve ardından sağ tıklayıp **dışarı aktar**' ı seçin.  
  
     **Raporu dışarı aktar** iletişim kutusu görünür.  
  
2. Dışarı aktarmak istediğiniz rapor görünümlerini seçin.  
  
3. **Ile önek raporu**' nun altında, rapor adına eklemek istediğiniz öneki belirtin.  
  
4. **Verdiğiniz rapor konumu**altında, dizini belirtin.  
  
5. **Aktarılmış rapor biçimi**altında (virgülle sınırlandırılmış) (*. csv) veya XML verileri ( \* . xml) öğesini seçin.  
  
6. **Dışarı aktar**'a tıklayın.  
  
     Her rapor görünümü _ adlı ayrı bir dosyaya kaydedilir \<prefix> \<report view name> .\<csv&#124;xml>  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Performans raporlarını rapor görünümü penceresinden dışarı aktarmak için  
  
1. Rapor Görünümü penceresinde. vsp dosyasını açın.  
  
2. Seçim Verilere filtre uygulayın. Daha fazla bilgi için bkz. [Performans raporu görünüm filtresi](../profiling/performance-report-view-filter.md).  
  
3. Rapor görünümü penceresi araç çubuğunda **raporu dışarı aktar** ' a tıklayın.  
  
4. Dışarı aktarmak istediğiniz rapor görünümlerini seçin.  
  
5. **Ile önek raporu**' nun altında, rapor adına eklemek istediğiniz öneki belirtin.  
  
6. **Verdiğiniz rapor konumu**altında, dizini belirtin.  
  
7. **Aktarılmış rapor biçimi**altında (virgülle sınırlandırılmış) (*. csv) veya XML verileri ( \* . xml) öğesini seçin.  
  
8. **Dışarı aktar**'a tıklayın.  
  
     Her rapor görünümü _ adlı ayrı bir dosyaya kaydedilir \<prefix> \<report view name> .\<csv&#124;xml>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Gezgini](../profiling/performance-explorer.md)   
 [Performans araçları verilerini çözümleme](../profiling/analyzing-performance-tools-data.md)   
 [Performans veri dosyalarını karşılaştırma](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
