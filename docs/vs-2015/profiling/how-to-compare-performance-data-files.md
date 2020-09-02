---
title: 'Nasıl yapılır: performans veri dosyalarını karşılaştırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 185494623e019ef666374bd46e52bca0d58738f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185945"
---
# <a name="how-to-compare-performance-data-files"></a>Nasıl yapılır: performans veri dosyalarını karşılaştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir karşılaştırma ("fark") raporu ya da görünümü oluşturarak iki farklı profil oluşturucu veri dosyasının (. vsp veya. vsps) sonuçlarını karşılaştırabilirsiniz. Karşılaştırma, bir profil oluşturma oturumundan diğerine gerçekleşen farkları, performans gerilemeleri ve geliştirmeleri gösterir.  
  
 Fark raporu, verilerin tablo görünümünü sunar. Tablo, Delta veya taban çizgisinden göre değişiklik gösterir. Bu, eski değer, taban çizgisi değeri ve yeni analizin sonucu değeri arasındaki farkı belirleyerek hesaplanır.  
  
 Profiler verilerinin karşılaştırmaları, koddaki işlevlere, uygulamadaki modüllerde, satırlarda, yönerge işaretçilerine (IP) ve türlere göre yapılabilir.  
  
 Bir eşik, paraziti azaltmak ve belirli bir miktarda değişmemiş satırların tablo görünümündeki verileri filtrelemek için ayarlanabilir.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Performans Gezgini bir proje için karşılaştırma dosyası görünümü oluşturmak için  
  
1. **Performans Gezgini**, **raporlar**altında, karşılaştırma için taban çizgisi değerleri olarak kullanmak istediğiniz. vsp veya. vsps rapor dosyasını seçin.  
  
2. Karşılaştırmak istediğiniz. vsp veya. vsps rapor dosyalarını seçin.  
  
3. Seçili dosyalardan birine sağ tıklayın ve ardından **raporları Karşılaştır**' a tıklayın.  
  
### <a name="to-compare-values"></a>Değerleri karşılaştırmak için  
  
1. Rapor Görünümü penceresinde **karşılaştırma raporu** sekmesini seçin.  
  
2. **Tablo** açılan listesinde, Karşılaştırılacak işlev veya modülleri seçin.  
  
3. **Sütun** açılan listesinde, karşılaştırmak istediğiniz değeri seçin.  
  
4. seçim **Eşik**için bir değer yazın.  
  
5. **Uygula**’ya tıklayın.  
  
### <a name="to-compare-report-files"></a>Rapor dosyalarını karşılaştırmak için  
  
1. **Çözümle** menüsünde, **performans raporlarını karşılaştır**' ı seçin.  
  
2. **Karşılaştırma için analiz dosyalarını Seç** penceresinde, **taban çizgisi dosya** Analizi dosyasına (. vsp veya. vsps) ve **karşılaştırma dosyasına** (. vsp veya. vsps) gözatıp seçin.  
  
3. **Tamam**’a tıklayın.
