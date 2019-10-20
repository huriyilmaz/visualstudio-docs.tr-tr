---
title: Yardımcı program düğümleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ff732221-b731-424c-ad5b-82ef5f21dff5
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5de2331be498cf9c9a4b121318433bcb5a47c501
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664062"
---
# <a name="utility-nodes"></a>Yardımcı Program Düğümleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gölgelendirici tasarımcısında, yardımcı program düğümleri diğer kategorilere göre uygun olmayan ortak, yararlı gölgelendirici hesaplamalarını temsil eder. Bazı yardımcı düğümler, vektör ekleme veya sonuçları koşullu olarak seçme gibi basit işlemler gerçekleştirir, diğerleri ise popüler aydınlatma modellerine göre aydınlatma katkıları hesaplama gibi karmaşık işlemleri gerçekleştirir.

## <a name="utility-node-reference"></a>Yardımcı program düğümü başvurusu

|Düğüm|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Vektör Ekle**|Belirtilen girişleri birlikte ekleyerek bir vektör oluşturur.<br /><br /> **Girişinin**<br /><br /> `Vector`: `float`, `float2` veya `float3`<br /> Eklenecek değerler.<br /><br /> `Value to Append`: `float`<br /> Eklenecek değer.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float2`, `float3` veya `float4` `Vector` giriş türüne göre<br /> Yeni vektör.|Yok.|
|**Fresnel düşüşünü**|Belirtilen yüzey normal temelinde Fresnel düşüşünü Fall hesaplar.<br /><br /> Fresnel düşüşünü Fall değeri, görünüm vektörü ile geçerli pikselin yüzey normalin ne kadar yakın olduğunu ifade eder. Vektörler hizalandığında, işlevin sonucu 0 ' dır; vektörler daha az benzer hale geldiği ve vektörler birbirine dikleşdiğinde en yüksek düzeye ulaştığında sonuç artar. Bunu, geçerli pikselin ve kameranın yönlendirmesi arasındaki ilişkiye bağlı olarak daha fazla veya daha az görünür hale getirmek için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `Surface Normal`: `float3`<br /> Geçerli pikselin teğet alanında tanımlanan, geçerli pikselin yüzey normal. Bunu, normal eşlemede olduğu gibi, görünür yüzeyi normal şekilde kullanmak için kullanabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float`<br /> Geçerli pikselin reflectivity.|**S**<br /> Fresnel düşüşünü Fall hesaplamak için kullanılan üs.|
|**If**|Bileşen başına üç olası sonuçtan birini koşullu olarak seçer. Koşul, belirtilen iki giriş arasındaki ilişki tarafından tanımlanır.<br /><br /> Sonucun her bileşeni için, ilk iki girişin karşılık gelen bileşenleri arasındaki ilişkiye bağlı olarak, olası üç sonuçtan birine karşılık gelen bileşen seçilir.<br /><br /> **Girişinin**<br /><br /> `X`: `float`, `float2`, `float3` veya `float4`<br /> Karşılaştırılacak sol taraftaki değer.<br /><br /> `Y`: giriş `X` aynı tür<br /> Karşılaştırılacak olan sağ taraftaki değer.<br /><br /> `X > Y`: giriş `X` aynı tür<br /> @No__t_0 `Y` daha büyük olduğunda seçilen değerler.<br /><br /> `X = Y`: giriş `X` aynı tür<br /> @No__t_0 `Y` eşit olduğunda seçilen değerler.<br /><br /> `X < Y`: giriş `X` aynı tür<br /> @No__t_0 `Y` daha az olduğunda seçilen değerler.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float3`<br /> Seçilen sonuç, bileşen başına.|Yok.|
|**Lambert**|Belirtilen yüzeyi normal kullanarak Lambert aydınlatma modeline göre geçerli pikselin rengini hesaplar.<br /><br /> Bu renk, ortam renginin toplamıdır ve doğrudan aydınlatma altındaki aydınlatma katkılarını dağıtma. Çevresel renk, dolaylı aydınlatmanın toplam katkısını yaklaştırır, ancak ek aydınlatma yardımı olmadan düz ve donuk bir şekilde görünür. Dağıtılmış aydınlatma bir nesneye şekil ve derinlik eklemenize yardımcı olur.<br /><br /> **Girişinin**<br /><br /> `Surface Normal`: `float3`<br /> Geçerli pikselin teğet alanında tanımlanan, geçerli pikselin yüzey normal. Bunu, normal eşlemede olduğu gibi, görünür yüzeyi normal şekilde kullanmak için kullanabilirsiniz.<br /><br /> `Diffuse Color`: `float3`<br /> Geçerli pikselin, genellikle **nokta rengi**olan dağıtma rengi. Giriş sağlanmazsa, varsayılan değer beyazdır.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin dağıtma rengi.|Yok.|
|**Maske vektörü**|Belirtilen vektörün maske bileşenleri.<br /><br /> Bu, belirli renk kanallarını bir renk değerinden kaldırmak veya belirli bileşenlerin sonraki hesaplamalarda etkili olmasını engellemek için kullanabilirsiniz.<br /><br /> **Girişinin**<br /><br /> `Vector`: `float4`<br /> Maskelenmesi için vektör.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Maskelenmiş vektör.|**Kırmızı/X**<br /> Red (x) bileşenini maskelemek için **false** ; Aksi takdirde, **doğru**.<br /><br /> **Yeşil/Y**<br /> Yeşil (y) bileşeni maskelemek için **false** ; Aksi takdirde, **doğru**.<br /><br /> **Mavi/Z**<br /> Mavi (z) bileşenini maskelemek için **false** ; Aksi takdirde, **doğru**.<br /><br /> **Alfa/W**<br /> Alfa (w) bileşenini maskelemek için **false** ; Aksi takdirde, **doğru**.|
|**Yansıma vektörü**|Geçerli piksel için, kamera konumuna göre, teğet alanındaki yansıma vektörünü hesaplar.<br /><br /> Bu durum, yansımaları, küp harita koordinatlarını ve yansımalı aydınlatma katkıları hesaplamak için kullanabilirsiniz<br /><br /> **Girişinin**<br /><br /> `Tangent Space Surface Normal`: `float3`<br /> Geçerli pikselin teğet alanında tanımlanan, geçerli pikselin yüzey normal. Bunu, normal eşlemede olduğu gibi, görünür yüzeyi normal şekilde kullanmak için kullanabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float3`<br /> Yansıma vektörü.|Yok.|
|**Yansımalı**|Belirtilen yüzeyi normal kullanarak Phong aydınlatma modeline göre yansımalı aydınlatma katkısını hesaplar.<br /><br /> Yansımalı aydınlatma, örneğin su, plastik veya Metals gibi bir nesneye parçalı, yansıtmalı bir görünüm sağlar.<br /><br /> **Girişinin**<br /><br /> `Surface Normal`: `float3`<br /> Geçerli pikselin teğet alanında tanımlanan, geçerli pikselin yüzey normal. Bunu, normal eşlemede olduğu gibi, görünür yüzeyi normal şekilde kullanmak için kullanabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float3`<br /> Yansımalı vurguların renk katkısı.|Yok.|
