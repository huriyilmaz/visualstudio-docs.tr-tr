---
title: Sabit Düğümler
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86fd5a9b2d179a27ec0cf34f5388b30ebb563ad4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72637351"
---
# <a name="constant-nodes"></a>Sabit düğümler

Shader Designer'da, sabit düğümler piksel gölgeli hesaplamalarda gerçek değerleri ve enterpolasyonlu vertex özniteliklerini temsil eder. Vertex öznitelikleri enterpolasyonlu olduğundan ve bu nedenle, her piksel için farklı-her piksel-shader örnek sabitfarklı bir sürümünü alır. Bu, her piksele benzersiz bir görünüm kazandırır.

## <a name="vertex-attribute-interpolation"></a>Vertex öznitelik enterpolasyonu

Bir oyun veya uygulamadaki 3B sahnenin görüntüsü, vertices, tepe noktası öznitelikleri ve ilkel tanımlar tarafından tanımlanan bir dizi nesnenin matematiksel olarak ekran piksellerine dönüştürülmesiyle yapılır. Bir piksele benzersiz bir görünüm kazandırmak için gereken tüm bilgiler, pikselin *ilkel*liğini oluşturan farklı tepe lere olan yakınlığına göre bir araya getirilmiş olan vertex öznitelikleri aracılığıyla sağlanır. İlkel bir temel işleme öğesidir; yani, bir nokta, çizgi veya üçgen gibi basit bir şekildir. Tepe tepelerinden birine çok yakın olan bir piksel, bu tepe noktasıyla neredeyse aynı olan sabitleri alır, ancak ilkel bir pikselin tüm tepeleri arasında eşit aralıklı bir piksel, bu tepe lerin ortalaması olan sabitleri alır. Grafik programlamada, piksellerin aldığı sabitlerin *enterpolasyona tabi*olduğu söylenir. Bu şekilde piksellere sabit veri sağlamak çok iyi bir görsel kalite üretir ve aynı zamanda bellek ayak izi ve bant genişliği gereksinimlerini azaltır.

Her piksel shader örneği yalnızca bir sabit değer kümesi alsa ve bu değerleri değiştiremese de, farklı piksel shader örnekleri farklı sabit veri kümeleri alır. Bu tasarım, bir gölgelendirme programının ilkel deki her piksel için farklı bir renk çıktısı üretmesini sağlar.

## <a name="constant-node-reference"></a>Sabit düğüm başvurusu

|Node|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Kamera Vektörü**|Dünya uzayında geçerli pikselden kameraya uzanan vektör.<br /><br /> Bunu dünya uzayında yansımaları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselden kameraya vektör.|None|
|**Renk Sabiti**|Sabit renk değeri.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Renk değeri.|**Çıktı**<br /> Renk değeri.|
|**Sabit**|Sabit bir skaler değer.<br /><br /> **Çıktı**<br /><br /> `Output`: `float`<br /> Skaler değer.|**Çıktı**<br /> Skaler değer.|
|**2B Sabit**|İki bileşenli vektör sabiti.<br /><br /> **Çıktı**<br /><br /> `Output`: `float2`<br /> Vektör değeri.|**Çıktı**<br /> Vektör değeri.|
|**3B Sabit**|Üç bileşenli vektör sabiti.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Vektör değeri.|**Çıktı**<br /> Vektör değeri.|
|**4D Sabit**|Dört bileşenli vektör sabiti.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Renk değeri.|**Çıktı**<br /> Vektör değeri.|
|**Normalleştirilmiş Pozisyon**|Normalleştirilmiş aygıt koordinatlarında ifade edilen geçerli pikselin konumu.<br /><br /> X-koordinat ve y-koordinatının [-1, 1] aralığında değerleri vardır, z-koordinatının [0, 1] aralığında bir değeri vardır ve w bileşeni görüş alanında nokta derinliği değerini içerir; w normalleştirilemedi.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|None|
|**Nokta Rengi**|Madde sel renk ve tepe noktası renk özniteliklerinin bir birleşimi olan geçerli pikselin dağınık rengi.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin dağınık rengi.|None|
|**Nokta Derinliği**|Görünüm alanındaki geçerli pikselin derinliği.<br /><br /> **Çıktı**<br /><br /> `Output`: `float`<br /> Geçerli pikselin derinliği.|None|
|**Normalleştirilmiş Nokta Derinliği**|Normalleştirilmiş aygıt koordinatlarında ifade edilen geçerli pikselin derinliği.<br /><br /> Sonuç [0, 1] aralığında bir değere sahiptir.<br /><br /> **Çıktı**<br /><br /> `Output`: `float`<br /> Geçerli pikselin derinliği.|None|
|**Ekran Konumu**|Geçerli pikselin konumu, ekran koordinatlarında ifade edilir.<br /><br /> Ekran koordinatları geçerli görüntü bağlantı noktasını temel atanır. X ve y bileşenleri ekran koordinatlarını içerir, z bileşeni [0, 1] aralığında normalleştirilmiş derinliği içerir ve w bileşeni görünüm alanında derinlik değerini içerir.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|None|
|**Yüzey Normal**|Nesne uzayında geçerli pikselin yüzeynormali.<br /><br /> Bunu, nesne alanındaki aydınlatma katkılarını ve yansımalarını hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin yüzeyi normaldir.|None|
|**Teğet Uzay Kamera Vektörü**|Geçerli pikselden kameraya teğet uzayda uzanan vektör.<br /><br /> Bunu teğet uzaydaki yansımaları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselden kameraya vektör.|None|
|**Teğet Uzay Işık Yönü**|Işığın geçerli pikselin teğet uzayında bir ışık kaynağından döküldüğ yönü tanımlayan vektör.<br /><br /> Bunu, teğet alandaki aydınlatma ve aynasal katkıları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Geçerli pikselden bir ışık kaynağına vektör.|None|
|**Dünya Normal**|Dünya uzayında geçerli pikselin yüzeyi normaldir.<br /><br /> Bunu, dünya uzayında aydınlatma katkılarını ve yansımalarını hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin yüzeyi normaldir.|None|
|**Dünya Konumu**|Geçerli pikselin dünya uzayındaki konumu.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|None|