---
title: Performans Raporu Görünüm Filtresi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778460"
---
# <a name="performance-report-view-filter"></a>Performans Raporu Görünüm Filtresi
**Profiler Report View Filtresi** penceresi **Performans Raporu** penceresinin en üstünde yer alır. **Göremiyorsanız, Filtreyi Göster** düğmesini tıklatın.

 Sonuçlarınızı hassaslaştırmak için her filtre yan tümcesini değiştirebilirsiniz. Aşağıdaki sütunlar filtre oluşturucuda kullanılabilir.

|Filtre öğesi|Açıklama|
|-----------------|-----------------|
|Veya|Bu **And** yan tümce nin ve bir sonraki tümcenin bir sonuca uyacak şekilde doğru olması gerekiyorsa ve seçin. Bu **Or** yan tümcenin veya bir sonraki yan tümcenin bir sonuca uyacak şekilde doğru olup olmadığını seçin.|
|Alan|Geçerli rapor dosyasında bulunan veri alanları listesinden filtre yan tümcesinde kullanılacak alanı seçin.|
|İşleç|Alan ve değer arasında istediğiniz ilişkiyi belirten işleci seçin.<br /><br /> = Eşittir<br /><br /> <>  Eşit Değil<br /><br /> < Az<br /><br /> > Büyük<br /><br /> <= Az veya Eşittir<br /><br /> >= Büyük veya Eşittir|
|Değer|Arayacakdeğeri seçin veya girin. Bazı alanlar, alan için kullanılabilir değerleri listeler.|

 Filtrenin size en iyi sonuçları vereceğini hissedene kadar filtre yan tümceleri ekleyebilirsiniz. Filtreyi veri dosyasına uygulamak için **Filtreyi Yürüt'e** tıklayın.

 **Marks** rapor görünümünden, rapor görünümlerinde bulunan verileri iki işaret arasında toplanan verilerle sınırlamak için filtre yan tümceleri oluşturabilirsiniz. Rapor verilerini başlatmak ve bitirmek istediğiniz işaretleri seçin, ardından sağ tıklatın ve **Zaman Damgaları'nda İşaretlere Filtre Ekle** veya **Filtre Ekle'yi**seçin. Her iki filtre de geçerli veri dosyasındaki verileri aynı açıklıkla sınırlar; **Markalara Filtre Ekle** diğer .vsp dosyalarına uygulanabilir.

 Filtreyi kaydetmek **için, Performans Raporu** araç çubuğunda **Dışa** Aktar Filtresi'ni tıklatın ve ardından ' ın yerini ve dosya adını belirtin. *vspf* dosyası. Daha önce kaydedilmiş bir filtreyi yüklemek için **Filtreyi İçe Aktar'ı** tıklatın ve kaydedilen filtre dosyasını bulun. Filtre dosyaları, tek başına Profil Oluşturma Araçları yüklü olan bilgisayarlardaki veri dosyalarını filtrelemek için de kullanılabilir. Daha fazla bilgi için [VSPerfReport'a](../profiling/vsperfreport.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
- [VSPerfReport](../profiling/vsperfreport.md)
