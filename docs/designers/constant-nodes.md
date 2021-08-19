---
title: Sabit Düğümler
description: Gölgelendirici tasarımcısında sabit düğümler hakkında bilgi edinmek için, piksel gölgelendirici hesaplamalarında değişmez değerleri ve enterpolasyonlu köşe özniteliklerini temsil edin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: ecab9a768c7103838e2f79ee668ccf81081a7d4c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153738"
---
# <a name="constant-nodes"></a>Sabit düğümler

Gölgelendirici tasarımcısında, sabit düğümler sabit değerleri ve piksel gölgelendirici hesaplamalarında enterpolasyonlu köşe özniteliklerini temsil eder. Köşe öznitelikleri enterpolacağından ve bu nedenle her bir piksel için farklı olduğundan, her piksel gölgelendirici örneği, sabit 'in farklı bir sürümünü alır. Bu, her piksele benzersiz bir görünüm sağlar.

## <a name="vertex-attribute-interpolation"></a>Köşe özniteliği ilişkilendirme

Bir oyun veya uygulamadaki 3B sahnenin görüntüsü, köşeler, köşe öznitelikleri ve temel tanımlar tarafından tanımlanan bir dizi nesneyi, ekran piksellerine göre ve matematiksel olarak dönüştürerek yapılır. Bir piksel benzersiz görünümü sağlamak için gereken tüm bilgiler, temel öznitelikleri aracılığıyla sağlanır ve bu da, *temel* bir şekilde bir piksel oluşturan farklı köşelere göre karışrdı. Temel bir temel işleme öğesidir; diğer bir deyişle, nokta, çizgi veya üçgen gibi basit bir şekil. Köşelerin yalnızca birine yakın bir piksel, bu köşenin neredeyse aynısı olan sabitleri alır, ancak bir ilkel öğenin tüm köşeleri arasında eşit aralıklı bir piksel, bu köşelerin ortalaması olan sabitleri alır. Grafik programlamada, piksellerin aldığı sabitler, *enterpolasyonda* denir. Bu şekilde piksellere sabit veri sağlanması çok iyi bir görsel kalite oluşturur ve aynı zamanda, bellek ayak ve bant genişliği gereksinimlerini azaltır.

Her piksel gölgelendirici örneği yalnızca bir sabit değer kümesi alırsa ve bu değerleri değiştiremese de, farklı piksel gölgelendirici örnekleri farklı sabit veri kümelerini alır. Bu tasarım, gölgelendirici programının ilkel içindeki her bir piksel için farklı bir renk çıkışı üretmesine olanak sağlar.

## <a name="constant-node-reference"></a>Sabit düğüm başvurusu

|Düğüm|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Kamera vektörü**|Dünya alanındaki geçerli pikselden kameraya genişleyen vektör.<br /><br /> Bunu, dünya alanındaki yansımaları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselden kameraya olan vektör.|Hiçbiri|
|**Renk sabiti**|Sabit bir renk değeri.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Renk değeri.|**Çıktı**<br /> Renk değeri.|
|**Sabit**|Sabit bir skaler değer.<br /><br /> **Çıktı**<br /><br /> `Output`: `float`<br /> Skaler değer.|**Çıktı**<br /> Skaler değer.|
|**2B sabit**|İki bileşenden oluşan vektör sabiti.<br /><br /> **Çıktı**<br /><br /> `Output`: `float2`<br /> Vektör değeri.|**Çıktı**<br /> Vektör değeri.|
|**3B sabiti**|Üç bileşenden oluşan bir vektör sabiti.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Vektör değeri.|**Çıktı**<br /> Vektör değeri.|
|**4D sabiti**|Dört bileşenden oluşan vektör sabiti.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Renk değeri.|**Çıktı**<br /> Vektör değeri.|
|**Normalleştirilmiş konum**|Normalleştirilmiş cihaz koordinatları olarak ifade edilen geçerli pikselin konumu.<br /><br /> X koordinatı ve y koordinatı [-1, 1] aralığında değerler içeriyor, z koordinatı [0, 1] aralığında bir değere sahip ve w bileşeni görünüm alanındaki nokta derinliği değerini içeriyor; w normalleştirilemez.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|Hiçbiri|
|**Nokta rengi**|Malzeme dağıtma rengi ve köşe rengi özniteliklerinin bir birleşimi olan geçerli pikselin dağıtma rengi.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin dağıtma rengi.|Hiçbiri|
|**Nokta derinliği**|Görünüm alanındaki geçerli pikselin derinliği.<br /><br /> **Çıktı**<br /><br /> `Output`: `float`<br /> Geçerli pikselin derinliği.|Hiçbiri|
|**Normalleştirilmiş nokta derinliği**|Normalleştirilmiş cihaz koordinatlarında ifade edilen geçerli pikselin derinliği.<br /><br /> Sonucun [0, 1] aralığında bir değeri vardır.<br /><br /> **Çıktı**<br /><br /> `Output`: `float`<br /> Geçerli pikselin derinliği.|Hiçbiri|
|**Ekran konumu**|Geçerli pikselin ekran koordinatları olarak ifade edilen konumu.<br /><br /> Ekran koordinatları geçerli görünüm penceresini temel alır. X ve y bileşenleri ekran koordinatlarını içerir, z bileşeni bir [0, 1] aralığına normalleştirilmiş derinliği içerir ve w bileşeni görünüm alanındaki derinlik değerini içerir.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|Hiçbiri|
|**Yüzey normal**|Nesne alanında geçerli pikselin yüzey normal.<br /><br /> Bunu, nesne alanındaki aydınlatma katkılarını ve yansımaları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin yüzey normal.|Hiçbiri|
|**Teğet alanı kamera vektörü**|Teğet alanında geçerli pikselden kameraya genişleyen vektör.<br /><br /> Bu alanı, tanjant alanındaki yansımaları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselden kameraya olan vektör.|Hiçbiri|
|**Teğet boşluk ışığı yönü**|Işığın, geçerli pikselin teğet alanındaki bir ışık kaynağından saçıldığı yönü tanımlayan vektör.<br /><br /> Bu bunu, tanjant alanında aydınlatma ve yansımalı katkıları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float3`<br /> Geçerli pikselden açık bir kaynaktan vektör.|Hiçbiri|
|**Dünya Normal**|Dünya boşluğundaki geçerli pikselin normal yüzeyi.<br /><br /> Bunu kullanarak dünya alanıyla ilgili aydınlatma katkılarını ve yansımalarını hesapabilirsiniz.<br /><br /> **Çıktı**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin normal yüzeyi.|Hiçbiri|
|**Dünya Konumu**|Dünya boşluğundaki geçerli pikselin konumu.<br /><br /> **Çıktı**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|Hiçbiri|