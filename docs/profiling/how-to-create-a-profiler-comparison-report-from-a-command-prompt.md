---
title: Profil Oluşturucu karşılaştırma raporu oluşturma (komut satırı)
description: İki profil oluşturucu veri dosyasının sonuçlarını karşılaştırmak için komut satırından VSPerfReport.exe kullanın. Karşılaştırma, profil oluşturma oturumları arasındaki farkları gösterir.
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
ms.openlocfilehash: 73ce7084a959e5ba21bcc22075c7452abc0186fed53abc72b1c97cc493200631
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426956"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Nasıl yapılır: komut isteminden profil oluşturucu karşılaştırma raporu oluşturma
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]İki profil oluşturma verisinin performans verilerini karşılaştıran bir profil oluşturma araçları raporu oluşturabilirsiniz (.*VSP* /or. *vsps*) dosyalarý. Rapor, bir profil oluşturma oturumundan diğerine gerçekleşen farkları, performans gerilemeleri ve geliştirmeleri gösterir. Rapordaki değerler, belirttiğiniz ilk dosyanın taban çizgisinden Delta veya değişiklik sunar. Bu Delta, taban çizgisi değeri olan eski değer ve yeni analizin sonucu değeri arasındaki farkı belirleyerek hesaplanır. Profiler verilerinin karşılaştırmaları, koddaki işlevlere, uygulamadaki modüllerde, satırlarda, yönerge işaretçilerine (IP) ve türlere göre yapılabilir.

 Karşılaştırma kategorilerinin ve alanlarının tanımlayıcılarını listelemek için aşağıdaki komut satırını yazın:

 **VSPerfReport/querydifftables**  *VspFileName1* *VspFileName2*

 Karşılaştırma raporu oluşturmak için aşağıdaki sözdizimini kullanın:

 **VSPerfReport/diff** `VspFileName1` *VspFileName2* [ **/** `Options` ]  

 Aşağıdaki tablodan **VSPerfReport/diff** komut satırına seçenekler ekleyebilirsiniz.

|Seçenek|Açıklama|
|------------|-----------------|
|**Diffthreshold:**[*değer*]|Bu yüzde eşik değerinin altındaysa farkı dikkate almaz. Ayrıca, bu eşiğin altındaki değerlere sahip olan yeni veriler görünmez.|
|**Difftable:** *TableName*|Dosyaları karşılaştırmak için bu tabloyu kullanın. Varsayılan olarak, işlevler tablosu kullanılır. **VSPerfReport/querydifftables** içinde listelenen tanımlayıcıyı belirtin.|
|**Diffcolumn:** *ColumnName*|Değerleri karşılaştırmak için bu sütunu kullanın. Varsayılan olarak, dışlayıcı örnek yüzdesi sütunu kullanılır. **VSPerfReport/querydifftables** içinde listelenen tanımlayıcıyı belirtin.|
