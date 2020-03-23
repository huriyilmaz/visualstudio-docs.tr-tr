---
title: Doku Düğümleri
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3393bb979b73694c4ac65120ae794ef1205b37c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589819"
---
# <a name="texture-nodes"></a>Doku düğümleri

Shader Designer'da doku düğümleri çeşitli doku türlerini ve geometrileri örnekler ve doku koordinatlarını üretir veya dönüştürür. Dokular nesnelerüzerinde renk ve aydınlatma ayrıntısı sağlar.

## <a name="texture-node-reference"></a>Doku düğümü başvurusu

|Node|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Küp Eşlem Örneği**|Belirtilen koordinatlarda bir küp eşlembir renk örneği alır.<br /><br /> Yansıma efektleri için renk ayrıntısı sağlamak veya 2B dokudan daha az bozulmaya sahip bir doku olan küresel bir nesneye uygulamak için bir küp eşlemi kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UVW`: `float3`<br /> Örneğin alındığı doku küpündeki konumu belirten bir vektör. Örnek, bu vektörün küple kesiştiği yerde alınır.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Renk örneği.|**Doku**<br /> Örnekleyiciyle ilişkili doku kaydı.|
|**Normal Harita Örneği**|Belirtilen koordinatlarda 2B normal haritadan normal bir örnek alır<br /><br /> Bir nesnenin yüzeyindeek geometrik ayrıntı görünümünü simüle etmek için normal bir harita kullanabilirsiniz. Normal haritalar, renk verileri yerine birim vektörü temsil eden paketlenmiş veriler içerir<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Numunenin alındığı koordinatlar.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Normal örnek.|**Eksen Ayarı**<br /> Normal harita örneğinin el ini ayarlamak için kullanılan faktör.<br /><br /> **Doku**<br /> Örnekleyiciyle ilişkili doku kaydı.|
|**Pan UV**|Zaman fonksiyonu olarak belirtilen doku koordinatlarını pans.<br /><br /> Bunu, bir dokuyu veya normal haritayı bir nesnenin yüzeyinde taşımak için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Kaydırma nın koordinatları.<br /><br /> `Time`: `float`<br /> Saniyeler içinde kaydırma süresi.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float2`<br /> Panned koordinatları.|**Hız X**<br /> Saniyede x ekseni boyunca kaydırılan texelsayısı.<br /><br /> **Hız Y**<br /> Saniye başına y ekseni boyunca kaydırılan texelsayısı.|
|**Paralaks UV**|Yükseklik ve görüntüleme açısının bir fonksiyonu olarak belirtilen doku koordinatlarını yerinden eder.<br /><br /> Bunun yarattığı etki *paralaks eşleme*veya sanal yer değiştirme eşleme olarak bilinir. Düz bir yüzeyüzerinde derinlik bir yanılsama oluşturmak için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Yerinden etmek için koordinatlar.<br /><br /> `Height`: `float`<br /> `UV` Koordinatlarla ilişkili yükseklik haritası değeri.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float2`<br /> Yerlerinden edilmiş koordinatlar.|**Derinlik Düzlemi**<br /> Paralaks efekti için referans derinliği. Varsayılan olarak, değer 0,5'tir. Daha küçük değerler dokuyu kaldırır; daha büyük değerler yüzeye batırın.<br /><br /> **Derinlik Ölçeği**<br /> Paralaks etkisinin ölçeği. Bu, belirgin derinliği az ya da çok belirgin hale getirir. Tipik değerler 0,02 ile 0,1 arasında değişir.|
|**UV'yi döndür**|Zaman fonksiyonu olarak merkezi bir nokta etrafında belirtilen doku koordinatları döndürür.<br /><br /> Bunu, bir nesnenin yüzeyinde bir doku veya normal harita döndürmek için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Döndürülecek koordinatlar.<br /><br /> `Time`: `float`<br /> Saniyeler içinde kaydırma süresi.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float2`<br /> Döndürülen koordinatlar.|**Merkez X**<br /> Döndürme merkezini tanımlayan x koordinatı.<br /><br /> **Merkez Y**<br /> Dönüş merkezini tanımlayan y koordinatı.<br /><br /> **Hız**<br /> Radyanlarda, dokunun saniyede döndüğü açı.|
|**Doku Koordinatı**|Geçerli pikselin doku koordinatları.<br /><br /> Doku koordinatları, yakındaki vertices doku koordinat öznitelikleri arasında interpolating tarafından belirlenir. Bunu, geçerli pikselin doku alanındaki konumu olarak düşünebilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float2`<br /> Doku koordinatları.|None|
|**Doku Boyutları**|2B doku haritasının genişliğini ve yüksekliğini çıkarır.<br /><br /> Bir gölgeli de doku genişliği ve yüksekliği dikkate almak için doku boyutlarını kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float2`<br /> Bir vektör olarak ifade edilen dokunun genişliği ve yüksekliği. Genişlik vektörün ilk öğesinde depolanır. Yükseklik ikinci öğede depolanır.|**Doku**<br /> Doku boyutlarıyla ilişkili doku kaydı.|
|**Texel Deltası**|2B doku haritasının texel'leri arasındaki deltayı (mesafeyi) çıkarır.<br /><br /> Bir gölgeli komşu texel değerleri örnek texel delta kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float2`<br /> Delta (mesafe) bir texel sonraki texel (pozitif yönde çapraz hareket), normalleştirilmiş doku uzayda bir vektör olarak ifade. Deltanın U veya V koordinatlarını seçerek yok sayarak veya inkâr ederek tüm komşu texellerin konumlarını elde edebilirsiniz.|**Doku**<br /> Texel deltasıyla ilişkili doku kaydı.|
|**Doku Örneği**|Belirtilen koordinatlarda 2B doku haritasından renk örneği alır.<br /><br /> Bir nesnenin yüzeyinde renk ayrıntısı sağlamak için bir doku eşlemi kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Numunenin alındığı koordinatlar.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Renk örneği.|**Doku**<br /> Örnekleyiciyle ilişkili doku kaydı.|
