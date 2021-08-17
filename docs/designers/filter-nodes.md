---
title: Filtre Düğümleri
description: Gölgelendirici Tasarımcısı'nda renk veya doku örneği gibi bir girişi mecazi bir renk değerine dönüştüren filtre düğümleri hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 8af162b4e2ff81cab74bc364e85c965d6f5c0004c5b1e7959b5afc9f9faf5e5c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390829"
---
# <a name="filter-nodes"></a>Filtre düğümleri

Gölgelendirici Tasarımcısı'nda, filtre düğümleri bir girişi (örneğin, renk veya doku örneği) belirli bir renk değerine dönüştürer. Bu mecazi renk değerleri genellikle fotoğraf gerçekliği olmayan işlemede veya diğer görsel etkilerde bileşenler olarak kullanılır.

## <a name="filter-node-reference"></a>Filtre düğümü başvurusu

|Düğüm|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Bulanık -lık**|Gauss işlevi kullanarak pikselleri dokuda bulanıklaştırır.<br /><br /> Dokuda renk ayrıntısını veya kirliliği azaltmak için bunu kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Test etmek için teselin koordinatları.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Doku**<br /> Bulanıklık sırasında kullanılan örnekleyiciyle ilişkili doku yazmacı.|
|**Desaturate**|Belirtilen renk miktarını azaltır.<br /><br /> Renk kaldırıldığı için renk değeri, gri ölçekli eşdeğeri yaklaşımını benimser.<br /><br /> **Giriş:**<br /><br /> `RGB`: `float3`<br /> Doygunluğun doymama rengi.<br /><br /> `Percent`: `float`<br /> Kaldırılan rengin, [0, 1] aralığında normalleştirilmiş bir değer olarak ifade edilmiş olan yüzde değeri.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Doymamış renk.|**Parlak -lık**<br /> Kırmızı, yeşil ve mavi renk bileşenlerine verilen ağırlıklar.|
|**Uç Algılama**|Canny kenar algılayıcısı kullanarak dokuda kenarları algılar. Kenar pikselleri beyaz olarak çıktıdır; kenar olmayan pikseller siyah olarak çıktılı olur.<br /><br /> Kenar piksellerini tedavi etmek için ek etkiler kullanmak üzere bir dokuda kenarları belirlemek için bunu kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Test etmek için teselin koordinatları.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Tesel bir kenarda ise beyaz; aksi takdirde, siyah.|**Doku**<br /> Uç algılama sırasında kullanılan örnekleyiciyle ilişkili doku yazmacı.|
|**Keskinleştirmek**|Dokuyu yeniler.<br /><br /> Dokuda ince ayrıntıları vurgulamak için bunu kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Test etmek için teselin koordinatları.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Doku**<br /> Yapıtlama sırasında kullanılan örnekleyiciyle ilişkili doku yazmacı.|