---
title: Sabit Düğümler
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6868a5dc7cbace1d061c43cd507d32c271436a26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769307"
---
# <a name="constant-nodes"></a>Sabit düğümler

Gölgelendirici tasarımcısında, sabit düğümler sabit değerleri ve piksel gölgelendirici hesaplamalarında enterpolasyonlu köşe özniteliklerini temsil eder. Köşe öznitelikleri enterpolacağından ve bu nedenle her bir piksel için farklı olduğundan, her piksel gölgelendirici örneği, sabit 'in farklı bir sürümünü alır. Bu, her piksele benzersiz bir görünüm sağlar.

## <a name="vertex-attribute-interpolation"></a>Köşe özniteliği ilişkilendirme

Bir oyun veya uygulamadaki 3B sahnenin görüntüsü, köşeler, köşe öznitelikleri ve temel tanımlar tarafından tanımlanan bir dizi nesneyi, ekran piksellerine göre ve matematiksel olarak dönüştürerek yapılır. Bir piksel benzersiz görünümü sağlamak için gereken tüm bilgiler, temel öznitelikleri aracılığıyla sağlanır ve bu da, *temel*bir şekilde bir piksel oluşturan farklı köşelere göre karışrdı. Temel bir temel işleme öğesidir; diğer bir deyişle, nokta, çizgi veya üçgen gibi basit bir şekil. Köşelerin yalnızca birine yakın bir piksel, bu köşenin neredeyse aynısı olan sabitleri alır, ancak bir ilkel öğenin tüm köşeleri arasında eşit aralıklı bir piksel, bu köşelerin ortalaması olan sabitleri alır. Grafik programlamada, piksellerin aldığı sabitler, *enterpolasyonda*denir. Bu şekilde piksellere sabit veri sağlanması çok iyi bir görsel kalite oluşturur ve aynı zamanda, bellek ayak ve bant genişliği gereksinimlerini azaltır.

Her piksel gölgelendirici örneği yalnızca bir sabit değer kümesi alırsa ve bu değerleri değiştiremese de, farklı piksel gölgelendirici örnekleri farklı sabit veri kümelerini alır. Bu tasarım, gölgelendirici programının ilkel içindeki her bir piksel için farklı bir renk çıkışı üretmesine olanak sağlar.

## <a name="constant-node-reference"></a>Sabit düğüm başvurusu

|Node|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Kamera vektörü**|Dünya alanındaki geçerli pikselden kameraya genişleyen vektör.<br /><br /> Bunu, dünya alanındaki yansımaları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselden kameraya olan vektör.|Yok|
|**Renk sabiti**|Sabit bir renk değeri.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Renk değeri.|**Çıktı**<br /> Renk değeri.|
|**Sabit**|Sabit bir skaler değer.<br /><br /> **Çıktı**<br /><br /> `Output`: `float`<br /> Skaler değer.|**Çıktı**<br /> Skaler değer.|
|**2B sabit**|İki bileşenden oluşan vektör sabiti.<br /><br /> **Çıktı**<br /><br /> `Output`: `float2`<br /> Vektör değeri.|**Çıktı**<br /> Vektör değeri.|
|**3B sabiti**|Üç bileşenden oluşan bir vektör sabiti.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Vektör değeri.|**Çıktı**<br /> Vektör değeri.|
|**4D sabiti**|Dört bileşenden oluşan vektör sabiti.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Renk değeri.|**Çıktı**<br /> Vektör değeri.|
|**Normalleştirilmiş konum**|Normalleştirilmiş cihaz koordinatları olarak ifade edilen geçerli pikselin konumu.<br /><br /> X koordinatı ve y koordinatı [-1, 1] aralığında değerler içeriyor, z koordinatı [0, 1] aralığında bir değere sahip ve w bileşeni görünüm alanındaki nokta derinliği değerini içeriyor; w normalleştirilemez.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|Yok|
|**Nokta rengi**|Malzeme dağıtma rengi ve köşe rengi özniteliklerinin bir birleşimi olan geçerli pikselin dağıtma rengi.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin dağıtma rengi.|Yok|
|**Nokta derinliği**|Görünüm alanındaki geçerli pikselin derinliği.<br /><br /> **Çıktı**<br /><br /> `Output`: `float`<br /> Geçerli pikselin derinliği.|Yok|
|**Normalleştirilmiş nokta derinliği**|Normalleştirilmiş cihaz koordinatlarında ifade edilen geçerli pikselin derinliği.<br /><br /> Sonucun [0, 1] aralığında bir değeri vardır.<br /><br /> **Çıktı**<br /><br /> `Output`: `float`<br /> Geçerli pikselin derinliği.|Yok|
|**Ekran konumu**|Geçerli pikselin ekran koordinatları olarak ifade edilen konumu.<br /><br /> Ekran koordinatları geçerli görünüm penceresini temel alır. X ve y bileşenleri ekran koordinatlarını içerir, z bileşeni bir [0, 1] aralığına normalleştirilmiş derinliği içerir ve w bileşeni görünüm alanındaki derinlik değerini içerir.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|Yok|
|**Yüzey normal**|Nesne alanında geçerli pikselin yüzey normal.<br /><br /> Bunu, nesne alanındaki aydınlatma katkılarını ve yansımaları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin yüzey normal.|Yok|
|**Teğet alanı kamera vektörü**|Teğet alanında geçerli pikselden kameraya genişleyen vektör.<br /><br /> Bu alanı, tanjant alanındaki yansımaları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselden kameraya olan vektör.|Yok|
|**Teğet boşluk ışığı yönü**|Işığın, geçerli pikselin teğet alanındaki bir ışık kaynağından saçıldığı yönü tanımlayan vektör.<br /><br /> Bu bunu, tanjant alanında aydınlatma ve yansımalı katkıları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float3`<br /> Geçerli pikselden bir ışık kaynağına vektör.|Yok|
|**Dünya normal**|Dünya alanındaki geçerli pikselin yüzey normal.<br /><br /> Bunu, dünya alanındaki aydınlatma katlamalarını ve yansımaları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin yüzey normal.|Yok|
|**Dünya konumu**|Dünya alanındaki geçerli pikselin konumu.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|Yok|