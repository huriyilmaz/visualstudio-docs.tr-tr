---
title: Düğümleri filtrele | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50f34f9706e9160cedaed09467fcf73b337a8329
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664670"
---
# <a name="filter-nodes"></a>Filtre Düğümleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gölgelendirici tasarımcısında, filtre düğümleri bir girişi (örneğin, bir renk veya doku örneği), bir yapılandırma rengi değerine dönüştürür. Bu renk değerleri, yaygın olarak gerçekçi olmayan işlemede veya diğer görsel efektlerdeki bileşenler olarak kullanılır.

## <a name="filter-node-reference"></a>Filtre düğümü başvurusu

|Düğüm|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Bulanıklaştırma**|Bir dokudaki pikselleri bir Gauss işlevi kullanarak bulanıklaştırır.<br /><br /> Bu, bir dokusundaki renk ayrıntılarını veya paraziti azaltmak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Test etmek için doku hücresi değerinin koordinatları.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Uyla**<br /> Bulanıklaştırma sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|
|**Gri oranını artır**|Belirtilen renkteki renk miktarını azaltır.<br /><br /> Renk kaldırıldığında, renk değeri gri ölçekli eşdeğerine yaklaşır.<br /><br /> **Girişinin**<br /><br /> `RGB`: `float3`<br /> Doygunluğu ortadan kaldırma rengi.<br /><br /> `Percent`: `float`<br /> [0, 1] aralığında normalleştirilmiş değer olarak ifade edilen, kaldırılacak rengin yüzdesi.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float3`<br /> Doygunluğu doymuş renk.|**Işıklılık**<br /> Kırmızı, yeşil ve mavi renk bileşenlerine verilen ağırlıklar.|
|**Kenar algılama**|Canny kenar algılayıcısı kullanarak dokudaki kenarları algılar. Uç pikseller beyaz olarak çıktı; uç olmayan pikseller siyah olarak çıktı.<br /><br /> Bu, kenar piksellerini işlemek için ek etkileri kullanabilmeniz amacıyla bir dokusundaki kenarları tanımlamak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Test etmek için doku hücresi değerinin koordinatları.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Doku hücresi değerinin bir kenar üzerinde ise beyaz; Aksi halde, siyah.|**Uyla**<br /> Kenar algılama sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|
|**Netleştirmek**|Bir dokuyu keskinleştirir.<br /><br /> Bu, bir dokusundaki hassas ayrıntıları vurgulamak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Test etmek için doku hücresi değerinin koordinatları.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Uyla**<br /> Keskinleştirme sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|
