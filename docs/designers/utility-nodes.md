---
title: Yardımcı Program Düğümleri
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ff732221-b731-424c-ad5b-82ef5f21dff5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be9c4c82d74c3878dd9937f81a83510e12f34a82
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72634570"
---
# <a name="utility-nodes"></a>Yardımcı program düğümleri

Shader Designer'da, yardımcı program düğümleri diğer kategorilere düzgün bir şekilde uymayan yaygın, yararlı gölgeli hesaplamaları temsil eder. Bazı yardımcı program düğümleri, vektörleri birbirine eklemek veya sonuçları koşullu olarak seçmek gibi basit işlemler gerçekleştirirken, diğerleri popüler aydınlatma modellerine göre aydınlatma katkılarını hesaplamak gibi karmaşık işlemler gerçekleştirir.

## <a name="utility-node-reference"></a>Yardımcı program düğümü başvurusu

|Node|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Ek Vektör**|Belirtilen girdileri bir araya getirerek bir vektör oluşturur.<br /><br /> **Giriş:**<br /><br /> `Vector`: `float` `float2`, veya`float3`<br /> Ekilen değerler.<br /><br /> `Value to Append`: `float`<br /> Ekilen değer.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float2` `float3`, `float4` veya giriş türüne bağlı olarak`Vector`<br /> Yeni vektör.|None|
|**Fresnel**|Fresnel düşüşünü belirtilen yüzeynormale göre hesaplar.<br /><br /> Fresnel düşme değeri, geçerli pikselin normal yüzeyinin görünüm vektörüyle ne kadar yakın örtüştünü ifade eder. Vektörler hizalandığında, fonksiyonun sonucu 0'dır; vektörler daha az benzer hale geldikçe sonuç artar ve vektörler ortogonal olduğunda maksimuma ulaşır. Geçerli pikselin yönü yle kamera arasındaki ilişkiye bağlı olarak, bir efekti az ya da çok belirgin hale getirmek için bunu kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `Surface Normal`: `float3`<br /> Geçerli pikselin teğet alanında tanımlanan geçerli pikselin yüzey normali. Bunu, normal haritalamada olduğu gibi görünen yüzeyi normal eve getirmek için kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float`<br /> Geçerli pikselin yansıtıcılığı.|**Üs**<br /> Fresnel düşüşünü hesaplamak için kullanılan üs.|
|**Eğer**|Koşullu bileşen başına üç olası sonuçlardan birini seçer. Koşul, diğer iki belirtilen giriş arasındaki ilişki ile tanımlanır.<br /><br /> Sonucun her bileşeni için, ilk iki girdinin ilgili bileşenleri arasındaki ilişkiye bağlı olarak, üç olası sonuçtan birinin ilgili bileşeni seçilir.<br /><br /> **Giriş:**<br /><br /> `X`: `float` `float2`, `float3`, veya`float4`<br /> Karşılaştırmak için sol taraf değeri.<br /><br /> `Y`: girişle aynı türde`X`<br /> Karşılaştırmak için sağ yan değeri.<br /><br /> `X > Y`: girişle aynı türde`X`<br /> 'den `Y`büyük olduğunda `X` seçilen değerler.<br /><br /> `X = Y`: girişle aynı türde`X`<br /> Ne zaman `X` seçilen değerler `Y`eşittir.<br /><br /> `X < Y`: girişle aynı türde`X`<br /> 'den `Y`az olduğunda `X` seçilen değerler<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Seçilen sonuç, bileşen başına.|None|
|**Lambert**|Belirtilen yüzey normal kullanarak, Lambert aydınlatma modeline göre geçerli pikselin rengini hesaplar.<br /><br /> Bu renk, doğrudan aydınlatma altında ortam rengi ve yaygın aydınlatma katkılarının toplamıdır. Ortam rengi dolaylı aydınlatmanın toplam katkısına yaklaşık olarak gelir, ancak ek aydınlatma yardımı olmadan düz ve mat görünür. Diffüz aydınlatma, nesneye şekil ve derinlik eklemeye yardımcı olur.<br /><br /> **Giriş:**<br /><br /> `Surface Normal`: `float3`<br /> Geçerli pikselin teğet alanında tanımlanan geçerli pikselin yüzey normali. Bunu, normal haritalamada olduğu gibi görünen yüzeyi normal eve getirmek için kullanabilirsiniz.<br /><br /> `Diffuse Color`: `float3`<br /> Geçerli pikselin dağınık rengi, genellikle **Point Color**. Giriş sağlanmadıysa, varsayılan değer beyazdır.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin dağınık rengi.|None|
|**Maske Vektörü**|Belirtilen vektörün bileşenlerini maskeler.<br /><br /> Bunu, belirli renk kanallarını renk değerinden kaldırmak veya belirli bileşenlerin sonraki hesaplamalar üzerinde etkili olmasını önlemek için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `Vector`: `float4`<br /> Maskeye vektör.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Maskeli vektör.|**Kırmızı / X**<br /> Kırmızı (x) bileşenini maskelemek için **yanlış;** aksi takdirde, **True**.<br /><br /> **Yeşil / Y**<br /> Yeşil (y) bileşenini maskelemek için **yanlış;** aksi takdirde, **True**.<br /><br /> **Mavi / Z**<br /> Mavi (z) bileşenini maskelemek için **yanlış;** aksi takdirde, **True**.<br /><br /> **Alfa / W**<br /> Alfa (w) bileşenini maskelemek için **yanlış;** aksi takdirde, **True**.|
|**Yansıma Vektörü**|Kamera konumuna bağlı olarak teğet uzaydaki geçerli pikselin yansıma vektörü hesaplar.<br /><br /> Yansımaları, küp eşgüdümlü koordinatları ve aynasal aydınlatma katkılarını hesaplamak için bunu kullanabilirsiniz<br /><br /> **Giriş:**<br /><br /> `Tangent Space Surface Normal`: `float3`<br /> Geçerli pikselin teğet alanında tanımlanan geçerli pikselin yüzey normali. Bunu, normal haritalamada olduğu gibi görünen yüzeyi normal eve getirmek için kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Yansıma vektörü.|None|
|**Yansımalı**|Belirtilen yüzey normal kullanarak, Phong aydınlatma modeline göre aynasal aydınlatma katkısını hesaplar.<br /><br /> Aynasal aydınlatma, bir nesneye, örneğin su, plastik veya metallere parlak, yansıtıcı bir görünüm verir.<br /><br /> **Giriş:**<br /><br /> `Surface Normal`: `float3`<br /> Geçerli pikselin teğet alanında tanımlanan geçerli pikselin yüzey normali. Bunu, normal haritalamada olduğu gibi görünen yüzeyi normal eve getirmek için kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Aynasal vurgular renk katkısı.|None|