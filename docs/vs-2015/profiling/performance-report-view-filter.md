---
title: Performans raporu görünüm filtresi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8620e5a372d764fef3a75126af52a6212ecc6cd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161968"
---
# <a name="performance-report-view-filter"></a>Performans Raporu Görünüm Filtresi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil Oluşturucu rapor görünümü filtresi penceresi, performans raporu penceresinin en üstünde bulunur. Bunu göremiyorsanız **filtre göster** düğmesine tıklayın.  
  
 Sonuçlarınızı iyileştirmek için her bir filtre yan tümcesini değiştirebilirsiniz. Aşağıdaki sütunlar, filtre Oluşturucusu 'nda mevcuttur.  
  
|Filtre öğesi|Açıklama|  
|-----------------|-----------------|  
|Ve/veya|Bu yan **tümce ve Next** yan tümcesinin bir sonuçla eşleştirmek için true olması gerekir. Bu yan **tümce veya sonraki** yan tümce bir sonuçla eşleşecek şekilde doğru olabilir.|  
|Alan|Geçerli rapor dosyasında kullanılabilir olan veri alanları listesinden filtre yan tümcesinde kullanılacak alanı seçin.|  
|Operatör|Alan ve değer arasında istediğiniz ilişkiyi belirten işleci seçin.<br /><br /> = Eşittir<br /><br /> Eşit değildir <>  <br /><br /> < küçüktür<br /><br /> Şundan büyük ><br /><br /> <= küçüktür veya eşittir<br /><br /> >= büyüktür veya eşittir|  
|Değer|Aranacak değeri seçin veya girin. Bazı alanlar alan için kullanılabilir değerleri listeler.|  
  
 Filtrenin size en iyi sonuçları vermesini hissetene kadar filtre tümceleri ekleyebilirsiniz. Filtreyi veri dosyasına uygulamak için **filtreyi Yürüt** ' e tıklayın.  
  
 **İşaretler** rapor görünümünden, rapor görünümlerindeki verileri iki işaret arasında toplanan verilerle sınırlamak için filtre yan tümceleri oluşturabilirsiniz. Başlamak istediğiniz işaretleri seçin ve rapor verilerini sonlandırın, sonra sağ tıklayın ve **Işaretlere Filtre Ekle** ya da **Zaman Damgalarına Filtre Ekle**' yi seçin. Her iki filtre de geçerli veri dosyasındaki verileri aynı yayılma ile sınırlar; **Işaretlere filtre ekleme** , diğer. vsp dosyalarına uygulanabilir.  
  
 Filtreyi kaydetmek için performans raporu araç çubuğunda **filtreyi dışarı aktar** ' a tıklayın ve ardından. vspf dosyası için bir konum ve dosya adı belirtin. Daha önce kaydedilen bir filtreyi yüklemek için **filtreyi Içeri aktar** ' a tıklayın ve kaydedilen filtre dosyasını bulun. Filtre dosyaları, tek başına Profil Oluşturma Araçları yüklü bilgisayarlardaki veri dosyalarını filtrelemek için de kullanılabilir. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans araçları verilerini çözümleme](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
