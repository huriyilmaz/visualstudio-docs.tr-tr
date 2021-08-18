---
title: Performans veri dosyalarını karşılaştırma | Microsoft Docs
description: Farkları, performans gerilemeleri ve performans iyileştirmeleri bulmak için iki farklı profil oluşturucu veri dosyası (. vsp veya. vsps) sonuçlarının nasıl karşılaştırılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 68ca77065935ca0635523471479988ea2ba9de47
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061031"
---
# <a name="how-to-compare-performance-data-files"></a>Nasıl yapılır: Performans veri dosyalarını karşılaştırma
İki farklı profil oluşturucu veri dosyasının sonuçlarını karşılaştırabilirsiniz (.*VSP* veya. *vsps*) bir karşılaştırma ("fark") raporu ya da görünümü oluşturarak. Karşılaştırma, bir profil oluşturma oturumundan diğerine gerçekleşen farkları, performans gerilemeleri ve geliştirmeleri gösterir.

 Fark raporu, verilerin tablo görünümünü sunar. Tablo, Delta veya taban çizgisinden göre değişiklik gösterir. Bu, eski değer, taban çizgisi değeri ve yeni analizin sonucu değeri arasındaki farkı belirleyerek hesaplanır.

 Profiler verilerinin karşılaştırmaları, koddaki işlevlere, uygulamadaki modüllerde, satırlarda, yönerge işaretçilerine (IP) ve türlere göre yapılabilir.

 Bir eşik, paraziti azaltmak ve belirli bir miktarda değişmemiş satırların tablo görünümündeki verileri filtrelemek için ayarlanabilir.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Performans Gezgini bir proje için karşılaştırma dosyası görünümü oluşturmak için

1. **Performans Gezgini**, **raporlar** altında öğesini seçin. *VSP* veya. Karşılaştırma için taban çizgisi değerleri olarak kullanmak istediğiniz *vsps* rapor dosyası.

2. Öğesini seçin. *VSP* veya. karşılaştırmak istediğiniz *vsps* rapor dosyaları.

3. Seçili dosyalardan birine sağ tıklayın ve ardından **raporları Karşılaştır**' a tıklayın.

### <a name="to-compare-values"></a>Değerleri karşılaştırmak için

1. Rapor Görünümü penceresinde **karşılaştırma raporu** sekmesini seçin.

2. **Tablo** açılan listesinde, Karşılaştırılacak işlev veya modülleri seçin.

3. **Sütun** açılan listesinde, karşılaştırmak istediğiniz değeri seçin.

4. seçim **Eşik** için bir değer yazın.

5. **Uygula**’ya tıklayın.

### <a name="to-compare-report-files"></a>Rapor dosyalarını karşılaştırmak için

1. **Çözümle** menüsünde, **performans raporlarını karşılaştır**' ı seçin.

2. **Karşılaştırma için analiz dosyalarını Seç** penceresinde, **taban çizgisi dosya** Analizi dosyasını (.*VSP* veya. *vsps*) ve **karşılaştırma dosyası** (.*VSP* veya. *vsps*).

3. **Tamam**'a tıklayın.
