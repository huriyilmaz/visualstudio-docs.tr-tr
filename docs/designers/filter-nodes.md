---
title: Filtre Düğümleri
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7627a5df1b3fcc5d26e33353e91f525b8083ccdf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72637305"
---
# <a name="filter-nodes"></a>Filtre düğümleri

Shader Designer'da filtre düğümleri bir girişi (örneğin, renk veya doku örneği) figüratif bir renk değerine dönüştürür. Bu figüratif renk değerleri genellikle fotogerçekçi olmayan görüntülemede veya diğer görsel efektlerde bileşen olarak kullanılır.

## <a name="filter-node-reference"></a>Filtre düğümü başvurusu

|Node|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Bulanık -lık**|Gaussian işlevi kullanarak dokudaki pikselleri bulanıklaştırır.<br /><br /> Bunu, dokudaki renk ayrıntılarını veya gürültüyü azaltmak için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Texel'in koordinatlarını test etmek için.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Doku**<br /> Bulanıklaştırma sırasında kullanılan örnekleyiciyle ilişkili doku kaydı.|
|**Desaturate**|Belirtilen renkteki renk miktarını azaltır.<br /><br /> Renk kaldırıldıkça, renk değeri gri ölçekli eşdeğerine yaklaşır.<br /><br /> **Giriş:**<br /><br /> `RGB`: `float3`<br /> Doygunluk için renk.<br /><br /> `Percent`: `float`<br /> Kaldırılacak renk yüzdesi, aralıkta normalleştirilmiş bir değer olarak ifade edilir [0, 1].<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Doymuş renk.|**Parlak -lık**<br /> Kırmızı, yeşil ve mavi renk bileşenlerine verilen ağırlıklar.|
|**Kenar Algılama**|Canny kenar dedektörü kullanarak dokudaki kenarları algılar. Kenar pikselleri beyaz olarak çıkar; kenar dışı pikseller siyah olarak çıktıdır.<br /><br /> Bunu, kenar piksellerini tedavi etmek için ek efektler kullanabilmeniz için dokudaki kenarları tanımlamak için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Texel'in koordinatlarını test etmek için.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Texel bir kenarda ise beyaz; aksi takdirde, siyah.|**Doku**<br /> Kenar algılama sırasında kullanılan örnekleyiciyle ilişkili doku kaydı.|
|**Keskinleştirmek**|Bir dokuyu keskinleştirir.<br /><br /> Bunu, dokudaki ince ayrıntıları vurgulamak için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Texel'in koordinatlarını test etmek için.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Doku**<br /> Keskinleştirme sırasında kullanılan örnekleyiciyle ilişkili doku kaydı.|