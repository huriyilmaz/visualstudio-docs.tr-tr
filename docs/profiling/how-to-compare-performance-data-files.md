---
title: 'Nasıl Kullanılır: Performans Veri Dosyalarını Karşılaştır | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c6dc9d485f6f40eb345ade8f9680be9e0b948106
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779005"
---
# <a name="how-to-compare-performance-data-files"></a>Nasıl yapılır: Performans veri dosyalarını karşılaştırma
İki farklı profil oluşturucu veri dosyasının sonuçlarını karşılaştırabilirsiniz (.* vsp* veya . *vsps*) bir karşılaştırma ("Diff") raporu veya görünümü oluşturarak. Karşılaştırma, bir profil oluşturma oturumundan diğerine gerçekleşen farklılıkları, performans gerilemelerini ve geliştirmeleri gösterir.

 Diff raporu verilerin tablo görünümünü sunar. Tablo delta yı veya taban çizgisinden değişiklik sunar. Bu, eski değer, temel değer ve yeni çözümlemeden elde edilen sonuç değeri arasındaki fark belirlenerek hesaplanır.

 Profil oluşturucu verilerinin karşılaştırılması, koddaki işlevlere, uygulamadaki modüllere, çizgilere, talimat işaretçilerine (IP) ve türlerine dayalı olabilir.

 Gürültüyü azaltmak ve belirli bir miktar değişmemiş satırların tablo görünümündeki verileri filtrelemek için bir eşik ayarlanabilir.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Performans Gezgini'ndeki bir proje için karşılaştırma dosyası görünümü oluşturmak için

1. **Performans Gezgini'nde**, **Raporlar**altında , . *vsp* veya . karşılaştırma için temel değerler olarak kullanmak istediğiniz *vsps* rapor dosyası.

2. 'yi seçin. *vsp* veya . *vsps* karşılaştırmak istediğiniz dosyaları rapor.

3. Seçili dosyalardan birini sağ tıklatın ve ardından **Raporları Karşılaştır'ı**tıklatın.

### <a name="to-compare-values"></a>Değerleri karşılaştırmak için

1. Rapor Görünümü penceresinde **Karşılaştırma Raporu** sekmesini seçin.

2. **Tablo** açılır listesinde, karşılaştırmak için işlev veya modülleri seçin.

3. **Sütun** açılır listesinde karşılaştırmak istediğiniz değeri seçin.

4. (isteğe bağlı) **Eşik**için bir değer yazın.

5. **Uygula**’ya tıklayın.

### <a name="to-compare-report-files"></a>Rapor dosyalarını karşılaştırmak için

1. **Analiz** menüsünde **Performans Raporlarını Karşılaştır'ı**seçin.

2. Karşılaştırma penceresi **için analiz dosyalarını** seç'te, **Temel Dosya** çözümleme dosyasına göz atın ve seçin (.* vsp* veya . *vsps*) ve **Karşılaştırma Dosyası** (.* vsp* veya . *vsps*).

3. **Tamam**'a tıklayın.
