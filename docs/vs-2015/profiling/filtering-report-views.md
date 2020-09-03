---
title: Rapor Görünümlerini Filtreleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 344a2dbe0e629f62f609806008b963be2be058a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164058"
---
# <a name="filtering-report-views"></a>Rapor Görünümlerini Filtreleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Performans raporu görünümlerinde görüntülenen profil oluşturma verilerini sınırlandırmak ve rapor dosyalarına aktarmak için profil oluşturma veri dosyalarına filtre uygulayabilirsiniz. Zaman damgası değerleri arasındaki verilerle bir raporu sınırlayabilir ve verileri belirli işlemlerle ve iş parçacıklarıyla sınırlayabilirsiniz. Filtreleri bir dosyaya kaydedebilir ve sonra kaydedilen filtreyi içeri aktararak farklı bir profil oluşturma veri dosyasında bir filtre oluşturabilirsiniz.  
  
 Ayrıca Özet görünümündeki grafik zaman çizelgesini kullanarak bir raporu zaman kesimiyle sınırlandırabilirsiniz. Bkz. [nasıl yapılır: Özet zaman çizelgesinden Rapor Görünümlerini Filtreleme](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
 Bir rapordan sistem ve üçüncü taraf kodu hariç tutmak için bkz [. nasıl yapılır: profil oluşturma araçları rapor görünümlerini görüntülemek Için filtreleme yalnızca kendi kodum](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-profiler-report-filter"></a>Profil Oluşturucu rapor filtresi oluşturmak için  
  
1. Performans raporu görünümü filtre penceresi görüntülenmiyorsa, performans raporu görünümü araç çubuğunda **filtreyi göster** ' e tıklayın.  
  
     Performans raporu görünüm filtresi bir tablodur. Tablonun her satırı, filtrenin bir yan tümcesini temsil eder. Filtre uygulamak istediğiniz kadar çok sayıda yan tümce ekleyebilirsiniz.  
  
2. Bir filtreye eklemek istediğiniz her yan tümce için, bir satırın aşağıdaki alanlarına değerler seçin veya girin.  
  
    |Alan|Açıklama|  
    |-----------|-----------------|  
    |**Ve/veya**|Bu yan **tümce ve Next** yan tümcesinin bir sonuçla eşleştirmek için true olması gerekir. Bu yan **tümce veya sonraki** yan tümce bir sonuçla eşleşecek şekilde doğru olabilir.|  
    |**Alan**|Görüntülenecek veri alanları listesinden filtre yan tümcesinde kullanılacak rapor alanını seçin.|  
    |**Operatör**|Alan ve değer arasındaki yan tümce içinde istediğiniz ilişkiyi belirten işleci seçin.<br /><br /> = Eşittir<br /><br /> Eşit değildir <>  <br /><br /> < küçüktür<br /><br /> Şundan büyük ><br /><br /> <= küçüktür veya eşittir<br /><br /> >= büyüktür veya eşittir|  
    |**Değer**|Aranacak değeri seçin veya girin. Bazı alanlar alan için kullanılabilir değerleri listeler.|  
  
3. 
  
#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Işaretler rapor görünümünden bir profil Oluşturucu rapor filtresi oluşturmak için  
  
1. Performans raporu görünümü araç çubuğundaki **geçerli görünüm** listesinden **işaretler** ' i seçin.  
  
    Işaretler profil Oluşturucu raporu görüntülenir.  
  
2. Raporun başlangıç noktası olarak kullanmak istediğiniz ETW veya örnekleme 'yi seçin.  
  
3. CTRL tuşuna basın ve basılı tutun ve raporun bitiş noktası olarak kullanmak istediğiniz olaya tıklayın.  
  
4. Sağ tıklayın ve ardından aşağıdaki seçeneklerden birine tıklayın:  
  
   - **Işaretlere Filtre Ekle** , işaret sütununu filtre alanı olarak kullanan filtre yan tümceleri oluşturur.  
  
   - **Zaman Damgalarına Filtre Ekle** , filtre alanı olarak milisaniye sütununda zaman damgasını kullanan filtre yan tümceleri oluşturur.  
  
     İki seçenek, geçerli veri dosyasını aynı başlangıç ve bitiş noktalarında filtreleyin. Her iki seçenek de, başka raporlarda kullanmak üzere filtreyi dışa aktardığınızda daha iyi olabilir.  
  
#### <a name="to-load-an-existing-filter-from-a-file"></a>Bir dosyadan varolan bir filtreyi yüklemek için  
  
1. Performans raporu görünümü araç çubuğunda **filtreyi Içeri aktar**' a tıklayın.  
  
     **Yükleme filtresi** iletişim kutusu görüntülenir.  
  
2. Yüklenecek filtre (. vspf) dosyasının konumunu ve dosya adını belirtin.  
  
#### <a name="to-execute-a-filter"></a>Bir filtreyi yürütmek için  
  
- Performans raporu görünümü araç çubuğunda **filtreyi Yürüt**' e tıklayın.  
  
#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Yürütülmesi çok uzun süren bir filtreyi durdurmak için  
  
- Performans raporu görünümü araç çubuğunda **filtreyi durdur**' a tıklayın.  
  
#### <a name="to-remove-a-filter-on-a-report-view"></a>Bir rapor görünümündeki filtreyi kaldırmak için  
  
1. Performans raporu görünümü filtresindeki yan tümce satırlarını silin.  
  
2. Performans raporu görünümü araç çubuğunda **filtreyi Yürüt**' e tıklayın.  
  
#### <a name="to-save-a-filter-to-a-file"></a>Bir dosyaya filtre kaydetmek için  
  
1. Performans raporu görünümü araç çubuğunda, **filtreyi dışarı aktar**' a tıklayın.  
  
     **Filtre kaydet** iletişim kutusu görüntülenir.  
  
2. Kaydedilecek filtre (. vspf) dosyasının konumunu ve dosya adını belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Araçları Rapor Görünümlerini Özelleştirme](../profiling/customizing-performance-tools-report-views.md)
