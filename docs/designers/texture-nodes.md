---
title: Doku Düğümleri
description: Çeşitli doku türleri ve geometriler örneği oluşturan doku düğümleri hakkında bilgi edinin ve ardından gölgelendirici tasarımcısında doku koordinatları üretir veya dönüştürün.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3e45789358e49a0b224a6de3ea6e5dfea44bf01
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93133968"
---
# <a name="texture-nodes"></a>Doku düğümleri

Gölgelendirici tasarımcısında, doku düğümleri örnek olarak çeşitli doku türleri ve geometriler ve doku koordinatları üretir veya dönüştürürler. Dokular nesneler üzerinde renk ve aydınlatma ayrıntısı sağlar.

## <a name="texture-node-reference"></a>Doku düğüm başvurusu

|Node|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Cubemap örneği**|Belirtilen koordinatlardaki küp harita 'ten bir renk örneği alır.<br /><br /> Yansıma efektleri için renk ayrıntısı sağlamak üzere bir küp harita kullanabilir veya bir 2B dokusundaki daha az deformasyonu olan bir küresel nesneye uygulayabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UVW`: `float3`<br /> Örnek alınan doku küpünde konumu belirten bir vektör. Örnek, bu vector öğesinin kübü kesiştiği yerde alınır.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Renk örneği.|**Doku**<br /> Örnekleyici ile ilişkili doku kaydı.|
|**Normal harita örneği**|Belirtilen koordinatlardaki 2B normal eşlemden normal bir örnek alır<br /><br /> Bir nesnenin yüzeyindeki ek geometrik ayrıntıların görünümünün benzetimini yapmak için normal bir harita kullanabilirsiniz. Normal haritalar, renk verileri yerine bir birim vektörünü temsil eden paketlenmiş verileri içerir<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Örneğin çekildiği koordinatlar.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float3`<br /> Normal örnek.|**Eksen ayarlaması**<br /> Normal harita örneğinin el kullanımını ayarlamak için kullanılan faktör.<br /><br /> **Doku**<br /> Örnekleyici ile ilişkili doku kaydı.|
|**UV kaydır**|Belirtilen doku koordinatlarını zaman işlevi olarak bomkler.<br /><br /> Bunu, bir nesnenin yüzeyi genelinde bir dokuyu veya normal Haritayı taşımak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Kaydırma için koordinatlar.<br /><br /> `Time`: `float`<br /> Saniye cinsinden, kaydırma süresi (saniye cinsinden).<br /><br /> **Çıktıların**<br /><br /> `Output`: `float2`<br /> Panolduğunuz koordinatlar.|**Hız X**<br /> Saniyede x ekseni boyunca yatay olarak kullanılan dokklerin sayısı.<br /><br /> **Hız Y**<br /> Y ekseni boyunca, saniye başına yatay olarak kullanılan doklarca sayısı.|
|**Paralaks UV**|Yükseklik ve görüntüleme açısı işlevi olarak belirtilen doku koordinatlarından oluşan bir işlev.<br /><br /> Bu efekt, *paralaks eşlemesi* veya sanal öteleme eşlemesi olarak bilinir. Bunu, düz bir yüzey üzerinde bir derinlik yanılsaması oluşturmak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Displace için koordinatlar.<br /><br /> `Height`: `float`<br /> Koordinatlarla ilişkili olan heightmap değeri `UV` .<br /><br /> **Çıktıların**<br /><br /> `Output`: `float2`<br /> Hatalı yerleştirilen koordinatlar.|**Derinlik Düzlemi**<br /> Paralaks efektinin başvuru derinliği. Varsayılan olarak, değer 0,5 ' dir. Daha küçük değerler dokuyu kaldırın; daha büyük değerler, yüzeyi içine havuza ayırır.<br /><br /> **Derinlik Ölçeği**<br /> Paralaks efektinin ölçeği. Bu, görünür derinliği daha fazla veya daha az belirgin hale getirir. Tipik değerler 0,02 ile 0,1 arasında değişir.|
|**UV döndür**|Belirtilen doku koordinatlarını bir zaman işlevi olarak merkezi bir nokta etrafında döndürür.<br /><br /> Bunu, bir nesnenin yüzeyinde bir dokuyu veya normal Haritayı almak için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Döndürülecek koordinatlar.<br /><br /> `Time`: `float`<br /> Saniye cinsinden, kaydırma süresi (saniye cinsinden).<br /><br /> **Çıktıların**<br /><br /> `Output`: `float2`<br /> Döndürülen koordinatlar.|**Orta X**<br /> Döndürme merkezini tanımlayan x koordinatı.<br /><br /> **Orta Y**<br /> Döndürme merkezini tanımlayan y koordinatı.<br /><br /> **Hız**<br /> Dokunun saniye başına döndüğü radyan cinsinden açı.|
|**Doku koordinatı**|Geçerli pikselin doku koordinatları.<br /><br /> Doku koordinatları, yakın köşelerin doku koordinat öznitelikleri arasında enterpolasyonu tarafından belirlenir. Bunu, doku alanındaki geçerli pikselin konumu olarak düşünebilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float2`<br /> Doku koordinatları.|Yok|
|**Doku boyutları**|2B doku eşlemesinin genişlik ve yüksekliğini verir.<br /><br /> Bir gölgelendiricide dokunun genişliğini ve yüksekliğini göz önünde bulundurmanız için doku boyutlarını kullanabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float2`<br /> Dokunun bir vektör olarak ifade edilen genişliği ve yüksekliği. Genişlik, vector öğesinin ilk öğesinde saklanır. Yükseklik ikinci öğesinde saklanır.|**Doku**<br /> Doku boyutlarıyla ilişkili doku kaydı.|
|**Texel Delta**|Bir 2B doku haritasının dokun arasındaki Delta (mesafe) çıktısını verir.<br /><br /> Bir gölgelendiricide komşu doku hücresi değerinin değerlerini örneklemek için doku hücresi değerinin Delta öğesini kullanabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float2`<br /> Bir doku hücresi değerinin 'den sonraki doku hücresi değerinin 'ye (pozitif yönde çapraz geçiş), normalleştirilmiş doku alanında vektör olarak ifade edilen Delta (uzaklık). Delta 'un U veya V koordinatlarını seçerek veya negatifi atlayarak tüm komşu metinlerinizin konumlarını türetebilirsiniz.|**Doku**<br /> Doku hücresi değerinin Delta ile ilişkili doku kaydı.|
|**Doku örneği**|2B doku eşlemesinden belirtilen koordinatlarda bir renk örneği alır.<br /><br /> Bir nesnenin yüzeyi üzerinde renk ayrıntısı sağlamak için doku haritası kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `UV`: `float2`<br /> Örneğin çekildiği koordinatlar.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Renk örneği.|**Doku**<br /> Örnekleyici ile ilişkili doku kaydı.|
