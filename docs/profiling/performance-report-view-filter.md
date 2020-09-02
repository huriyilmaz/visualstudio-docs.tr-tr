---
title: Performans raporu görünüm filtresi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9a5642a8e153a4dfc7705d91d933397b6f8acb37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778460"
---
# <a name="performance-report-view-filter"></a>Performans Raporu Görünüm Filtresi
**Profil Oluşturucu rapor görünümü filtresi** penceresi, **Performans raporu** penceresinin en üstünde bulunur. Bunu göremiyorsanız **filtre göster** düğmesine tıklayın.

 Sonuçlarınızı iyileştirmek için her bir filtre yan tümcesini değiştirebilirsiniz. Aşağıdaki sütunlar, filtre Oluşturucusu 'nda mevcuttur.

|Filtre öğesi|Description|
|-----------------|-----------------|
|Ve/veya|Bu yan **tümce ve Next** yan tümcesinin bir sonuçla eşleştirmek için true olması gerekir. Bu yan **tümce veya sonraki** yan tümce bir sonuçla eşleşecek şekilde doğru olabilir.|
|Alan|Geçerli rapor dosyasında kullanılabilir olan veri alanları listesinden filtre yan tümcesinde kullanılacak alanı seçin.|
|Operatör|Alan ve değer arasında istediğiniz ilişkiyi belirten işleci seçin.<br /><br /> = Eşittir<br /><br /> Eşit değildir <>  <br /><br /> < küçüktür<br /><br /> Şundan büyük ><br /><br /> <= küçüktür veya eşittir<br /><br /> >= büyüktür veya eşittir|
|Değer|Aranacak değeri seçin veya girin. Bazı alanlar alan için kullanılabilir değerleri listeler.|

 Filtrenin size en iyi sonuçları vermesini hissetene kadar filtre tümceleri ekleyebilirsiniz. Filtreyi veri dosyasına uygulamak için **filtreyi Yürüt** ' e tıklayın.

 **İşaretler** rapor görünümünden, rapor görünümlerindeki verileri iki işaret arasında toplanan verilerle sınırlamak için filtre yan tümceleri oluşturabilirsiniz. Başlamak istediğiniz işaretleri seçin ve rapor verilerini sonlandırın, sonra sağ tıklayın ve **Işaretlere Filtre Ekle** ya da **Zaman Damgalarına Filtre Ekle**' yi seçin. Her iki filtre de geçerli veri dosyasındaki verileri aynı yayılma ile sınırlar; **Işaretlere filtre ekleme** , diğer. vsp dosyalarına uygulanabilir.

 Filtreyi kaydetmek için **Performans raporu** araç çubuğunda **filtreyi dışarı aktar** ' a tıklayın ve ardından için bir konum ve dosya adı belirtin. *vspf* dosyası. Daha önce kaydedilen bir filtreyi yüklemek için **filtreyi Içeri aktar** ' a tıklayın ve kaydedilen filtre dosyasını bulun. Filtre dosyaları, tek başına Profil Oluşturma Araçları yüklü bilgisayarlardaki veri dosyalarını filtrelemek için de kullanılabilir. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
- [VSPerfReport](../profiling/vsperfreport.md)
