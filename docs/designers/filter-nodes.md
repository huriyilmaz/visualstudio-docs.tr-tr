---
title: Filtre Düğümleri
description: Gölgelendirici tasarımcısında bir renk veya doku örneği gibi bir girişi bir yapılandırma rengi değerine dönüştüren filtre düğümleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d2fe2d0c7f6d156e8a9a88a474c59f75b70a5dac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917064"
---
# <a name="filter-nodes"></a>Filtre düğümleri

Gölgelendirici tasarımcısında, filtre düğümleri bir girişi (örneğin, bir renk veya doku örneği), bir yapılandırma rengi değerine dönüştürür. Bu renk değerleri, yaygın olarak gerçekçi olmayan işlemede veya diğer görsel efektlerdeki bileşenler olarak kullanılır.

## <a name="filter-node-reference"></a>Filtre düğümü başvurusu

|Düğüm|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Bulanıklaştırma**|Bir dokudaki pikselleri bir Gauss işlevi kullanarak bulanıklaştırır.<br /><br /> Bu, bir dokusundaki renk ayrıntılarını veya paraziti azaltmak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Test etmek için doku hücresi değerinin koordinatları.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Doku**<br /> Bulanıklaştırma sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|
|**Gri oranını artır**|Belirtilen renkteki renk miktarını azaltır.<br /><br /> Renk kaldırıldığında, renk değeri gri ölçekli eşdeğerine yaklaşır.<br /><br /> **Girişinin**<br /><br /> `RGB`: `float3`<br /> Doygunluğu ortadan kaldırma rengi.<br /><br /> `Percent`: `float`<br /> [0, 1] aralığında normalleştirilmiş değer olarak ifade edilen, kaldırılacak rengin yüzdesi.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float3`<br /> Doygunluğu doymuş renk.|**Işıklılık**<br /> Kırmızı, yeşil ve mavi renk bileşenlerine verilen ağırlıklar.|
|**Kenar algılama**|Canny kenar algılayıcısı kullanarak dokudaki kenarları algılar. Uç pikseller beyaz olarak çıktı; uç olmayan pikseller siyah olarak çıktı.<br /><br /> Bu, kenar piksellerini işlemek için ek etkileri kullanabilmeniz amacıyla bir dokusundaki kenarları tanımlamak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Test etmek için doku hücresi değerinin koordinatları.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Doku hücresi değerinin bir kenar üzerinde ise beyaz; Aksi halde, siyah.|**Doku**<br /> Kenar algılama sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|
|**Netleştirmek**|Bir dokuyu keskinleştirir.<br /><br /> Bu, bir dokusundaki hassas ayrıntıları vurgulamak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Test etmek için doku hücresi değerinin koordinatları.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Doku**<br /> Keskinleştirme sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|