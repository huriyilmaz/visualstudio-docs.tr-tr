---
title: "Nasıl Yapılsın: Komut İstemi'nden Profil OluşturLayıcı Karşılaştırma Raporu Oluşturma | Microsoft Dokümanlar"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0328e04067770f8837d10d532abb67d16c65e50
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776452"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Nasıl yapilir: Komut isteminden profil oluşturucu karşılaştırma raporu oluşturma
İki profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturma verisinin performans verilerini karşılaştıran bir Profil Oluşturma Araçları raporu oluşturabilirsiniz (.* vsp* /veya . *vsps*) Dosyaları. Rapor, bir profil oluşturma oturumundan diğerine gerçekleşen farklılıkları, performans gerilemelerini ve iyileştirmeleri gösterir. Rapordaki değerler, belirttiğiniz ilk dosyanın taban çizgisinden delta'yı veya değişikliği sunar. Bu delta, temel değer olan eski değer ile yeni çözümlemeden elde edilen sonuç değeri arasındaki fark belirlenerek hesaplanır. Profil oluşturucu verilerinin karşılaştırılması, koddaki işlevlere, uygulamadaki modüllere, çizgilere, talimat işaretçilerine (IP) ve türlerine dayalı olabilir.

 Karşılaştırma kategorilerinin ve alanlarının tanımlayıcılarını listelemek için aşağıdaki komut satırını yazın:

 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*

 Karşılaştırma raporunu oluşturmak için aşağıdaki sözdizimini kullanın:

 **VSPerfReport /diff** `VspFileName1` *VspFileName2* [**/**`Options`]  

 Aşağıdaki tablodan **VSPerfReport /diff** komut satırına seçenekler ekleyebilirsiniz.

|Seçenek|Açıklama|
|------------|-----------------|
|**DiffThreshold:**[*Değer*]|Bu yüzde eşik değerinin altındaysa farkı göz ardı edin. Ayrıca, bu eşiğin altında değerlere sahip yeni veriler görünmez.|
|**DiffTable:** *Tablo Adı*|Dosyaları karşılaştırmak için bu tabloyu kullanın. Varsayılan olarak, işlevler tablosu kullanılır. **VSPerfReport /querydifftables'ta**listelenen tanımlayıcıyı belirtin.|
|**DiffColumn:** *Sütun Adı*|Değerleri karşılaştırmak için bu sütunu kullanın. Varsayılan olarak, özel örnekler yüzdesi sütunu kullanılır. **VSPerfReport /querydifftables'ta**listelenen tanımlayıcıyı belirtin.|
