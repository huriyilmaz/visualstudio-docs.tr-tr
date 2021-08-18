---
title: Profil oluşturma karşılaştırma raporu oluşturma (komut satırı)
description: İki VSPerfReport.exe veri dosyalarının sonuçlarını karşılaştırmak için komut satırına bir komut satırı oluşturun. Karşılaştırma, profil oluşturma oturumları arasındaki farkları gösterir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ffa80280a5dda1d8fc25e40c8ed5269d3328a5ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150265"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Nasıl olur: Komut isteminden profil oluşturma karşılaştırma raporu oluşturma
İki profil oluşturma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları ( performans verilerini karşılaştıran bir rapor oluşturabilirsiniz.*vsp* /veya . *vsps*) Dosyaları. Rapor, bir profil oluşturma oturumundan diğerine yapılan farkları, performans regresyonlarını ve geliştirmeleri gösterir. Raporda yer alan değerler, belirttiğiniz ilk dosyanın temel çizgisinde değişiklik veya değişiklik gösterir. Bu delta, temel değer olan eski değer ile yeni analizden elde edilen sonuç değeri arasındaki fark belirlenerek hesaplanır. Profil oluşturma verileri karşılaştırmaları kod, uygulama modülleri, satırlar, yönerge işaretçileri (PS) ve türler gibi işlevlere dayalı olabilir.

 Karşılaştırma kategorileri ve alanlarının tanımlayıcılarını listeleyen aşağıdaki komut satırı yazın:

 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*

 Karşılaştırma raporunu oluşturmak için aşağıdaki söz dizimlerini kullanın:

 **VSPerfReport /diff** `VspFileName1` *VspFileName2* [ **/** `Options` ]  

 Aşağıdaki tablodan **VSPerfReport /diff komut satırına seçenekler** ebilirsiniz.

|Seçenek|Açıklama|
|------------|-----------------|
|**DiffThreshold:**[*Değer*]|Bu yüzde eşiği değerinin altında ise farkı göz ardı edin. Ayrıca, bu eşiğin altında değerlere sahip yeni veriler görünmez.|
|**DiffTable:** *TableName*|Dosyaları karşılaştırmak için bu tabloyu kullanın. Varsayılan olarak, işlevler tablosu kullanılır. **VSPerfReport /querydifftables içinde listelenen tanımlayıcıyı belirtin.**|
|**DiffColumn:** *ColumnName*|Değerleri karşılaştırmak için bu sütunu kullanın. Varsayılan olarak, özel örnekler yüzde sütunu kullanılır. **VSPerfReport /querydifftables içinde listelenen tanımlayıcıyı belirtin.**|
