---
title: Performans Veri Dosyalarını Karşılaştırma | Microsoft Docs
description: Farkları, performans regresyonlarını ve performans geliştirmelerini bulmak için iki farklı profil oluşturma veri dosyalarının (.vsp veya .vsps) sonuçlarını karşılaştırmayı öğrenin.
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
ms.openlocfilehash: 59421f44a2b5d9d30285f9959ea22d090b6bddcc3d4777a29e0de1e4cf98483e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231177"
---
# <a name="how-to-compare-performance-data-files"></a>Nasıl yapılır: Performans veri dosyalarını karşılaştırma
İki farklı profil oluşturma veri dosyalarının sonuçlarını karşılaştırabilirsiniz (.*vsp* veya . *vsps*) karşılaştırma ("Fark") raporu veya görünümü oluşturarak. Karşılaştırma, bir profil oluşturma oturumundan diğer oturuma yapılan farkları, performans regresyonlarını ve geliştirmeleri gösterir.

 Fark raporu verilerin tablo görünümünü sunar. Tablo deltayı gösterir veya temelden değiştirir. Bu, eski değer, temel değer ve yeni analizden elde edilen sonuç değeri arasındaki fark belirlenerek hesaplanır.

 Profil oluşturma verileri karşılaştırmaları kod, uygulama modülleri, satırlar, yönerge işaretçileri (PS) ve türler işlevlerine dayalı olabilir.

 Gürültüyü azaltmak ve belirtilen miktarda değişmemiş satırların tablo görünümündeki verileri filtrelemek için bir eşik belirlenilebilir.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Bir proje için karşılaştırma dosyası görünümü oluşturmak için Performans Gezgini

1. Rapor **Performans Gezgini** **altında** öğesini seçin. *vsp* veya . Karşılaştırma için temel değerler olarak kullanmak istediğiniz *vsps* rapor dosyası.

2. öğesini seçin. *vsp* veya . karşılaştırmak istediğiniz *vsps* rapor dosyaları.

3. Seçili dosyalardan birini sağ tıklatın ve ardından Raporları **Karşılaştır'a tıklayın.**

### <a name="to-compare-values"></a>Değerleri karşılaştırmak için

1. Rapor **Görünümü penceresinde** Karşılaştırma Raporu sekmesini seçin.

2. Tablo **açılan** listesinde karşılaştırmak istediğiniz işlevi veya modülleri seçin.

3. Sütun **açılan** listesinde karşılaştırmak istediğiniz değeri seçin.

4. (isteğe bağlı) Eşik için bir değer **yazın.**

5. **Uygula**’ya tıklayın.

### <a name="to-compare-report-files"></a>Rapor dosyalarını karşılaştırmak için

1. Analiz menüsünde **Performans** Raporlarını **Karşılaştır'ı seçin.**

2. Karşılaştırma için **analiz dosyalarını seçin penceresinde** Temel Dosya analiz dosyasını **()** bulun ve seçin.*vsp* veya . *vsps*) ve **Karşılaştırma Dosyası** (.*vsp* veya . *vsps*).

3. **Tamam**'a tıklayın.
