---
title: Filtre Düğümleri
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfc74287706976f96a5e565bef3da1493cd44866
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769278"
---
# <a name="filter-nodes"></a>Filtre düğümleri

Gölgelendirici tasarımcısında, filtre düğümleri bir girişi (örneğin, bir renk veya doku örneği), bir yapılandırma rengi değerine dönüştürür. Bu renk değerleri, yaygın olarak gerçekçi olmayan işlemede veya diğer görsel efektlerdeki bileşenler olarak kullanılır.

## <a name="filter-node-reference"></a>Filtre düğümü başvurusu

|Node|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Bulanıklaştırma**|Bir dokudaki pikselleri bir Gauss işlevi kullanarak bulanıklaştırır.<br /><br /> Bu, bir dokusundaki renk ayrıntılarını veya paraziti azaltmak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Test etmek için doku hücresi değerinin koordinatları.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Doku**<br /> Bulanıklaştırma sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|
|**Gri oranını artır**|Belirtilen renkteki renk miktarını azaltır.<br /><br /> Renk kaldırıldığında, renk değeri gri ölçekli eşdeğerine yaklaşır.<br /><br /> **Girişinin**<br /><br /> `RGB`: `float3`<br /> Doygunluğu ortadan kaldırma rengi.<br /><br /> `Percent`: `float`<br /> [0, 1] aralığında normalleştirilmiş değer olarak ifade edilen, kaldırılacak rengin yüzdesi.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float3`<br /> Doygunluğu doymuş renk.|**Işıklılık**<br /> Kırmızı, yeşil ve mavi renk bileşenlerine verilen ağırlıklar.|
|**Kenar algılama**|Canny kenar algılayıcısı kullanarak dokudaki kenarları algılar. Uç pikseller beyaz olarak çıktı; uç olmayan pikseller siyah olarak çıktı.<br /><br /> Bu, kenar piksellerini işlemek için ek etkileri kullanabilmeniz amacıyla bir dokusundaki kenarları tanımlamak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Test etmek için doku hücresi değerinin koordinatları.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Doku hücresi değerinin bir kenar üzerinde ise beyaz; Aksi halde, siyah.|**Doku**<br /> Kenar algılama sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|
|**Netleştirmek**|Bir dokuyu keskinleştirir.<br /><br /> Bu, bir dokusundaki hassas ayrıntıları vurgulamak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Test etmek için doku hücresi değerinin koordinatları.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Doku**<br /> Keskinleştirme sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|