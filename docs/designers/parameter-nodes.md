---
title: Parametre Düğümleri
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f749d4ed6338919132e1c48d6da0572e3efe88
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72635012"
---
# <a name="parameter-nodes"></a>Parametre düğümleri

Shader Designer'da parametre düğümleri, uygulamanın her çekme başına kontrolü altında olan gölgeliye girişleri temsil eder, örneğin malzeme özellikleri, yön ışıkları, kamera konumu ve zaman. Bu parametreleri her çizim çağrısıyla değiştirebileceğinizden, bir nesneye farklı görünümler vermek için aynı gölgeleyiciyi kullanabilirsiniz.

## <a name="parameter-node-reference"></a>Parametre düğümü başvurusu

|Node|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Kamera Dünya Konumu**|Kameranın dünya uzasındaki konumu.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Kameranın konumu.|None|
|**Işık Yönü**|Işığın dünya uzayında bir ışık kaynağından döküldüğ yönü tanımlayan vektör.<br /><br /> Bunu, dünya uzayında aydınlatma ve aynasal katkıları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Geçerli pikselden bir ışık kaynağına vektör.|None|
|**Malzeme Ortam**|Dolaylı aydınlatmaya atfedilen geçerli pikselin dağınık renk katkısı.<br /><br /> Pikselin dağınık rengi, aydınlatmanın pürüzlü yüzeylerle nasıl etkileşime girdiğine benzetilir. Dolaylı aydınlatmanın gerçek dünyada bir nesnenin görünümüne nasıl katkıda olduğunu tahmin etmek için Malzeme Ortam parametresini kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Dolaylı olarak,yani ortam aydınlatmasına bağlı olan geçerli pikselin dağınık rengi.|**Erişim**<br /> Özelliğin Model Düzenleyicisi'nden ayarlanabilmesi için **herkese açık;** aksi takdirde, **Özel**.<br /><br /> **Değer**<br /> Dolaylı olarak,yani ortam aydınlatmasına bağlı olan geçerli pikselin dağınık rengi.|
|**Malzeme Diffüz**|Geçerli pikselin doğrudan aydınlatmayı nasıl yaydığını açıklayan bir renk.<br /><br /> Pikselin dağınık rengi, aydınlatmanın pürüzlü yüzeylerle nasıl etkileşime girdiğine benzetilir. Geçerli pikselin doğrudan aydınlatmayı nasıl yaydığını değiştirmek için Malzeme Diffuse parametresini kullanabilirsiniz, yani yön, nokta ve spot ışıkları.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin doğrudan aydınlatmayı nasıl yaydığını açıklayan bir renk.|**Erişim**<br /> Özelliğin Model Düzenleyicisi'nden ayarlanabilmesi için **herkese açık;** aksi takdirde, **Özel**.<br /><br /> **Değer**<br /> Geçerli pikselin doğrudan aydınlatmayı nasıl yaydığını açıklayan bir renk.|
|**Malzeme Elçisi**|Kendisine sağladığı aydınlatmaya atfedilen geçerli pikselin renk katkısı.<br /><br /> Bunu parlayan bir nesneyi simüle etmek için kullanabilirsiniz; yani, kendi ışığını sağlayan bir nesnedir. Bu ışık diğer nesneleri etkilemez.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Kendi kendine sağlanan aydınlatma nedeniyle geçerli pikselin renk katkısı.|**Erişim**<br /> Özelliğin Model Düzenleyicisi'nden ayarlanabilmesi için **herkese açık;** aksi takdirde, **Özel**.<br /><br /> **Değer**<br /> Kendi kendine sağlanan aydınlatma nedeniyle geçerli pikselin renk katkısı.|
|**Malzeme Aynalı**|Geçerli pikselin doğrudan aydınlatmayı nasıl yansıttığını açıklayan bir renk.<br /><br /> Bir pikselin aynasal rengi, aydınlatmanın pürüzsüz, ayna benzeri yüzeylerle nasıl etkileştiğini simüle eder. Geçerli pikselin doğrudan aydınlatmayı nasıl yansıttığını değiştirmek için Malzeme Aynasal parametresini kullanabilirsiniz, yani yön, nokta ve spot ışıkları.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin doğrudan aydınlatmayı nasıl yansıttığını açıklayan bir renk.|**Erişim**<br /> Özelliğin Model Düzenleyicisi'nden ayarlanabilmesi için **herkese açık;** aksi takdirde, **Özel**.<br /><br /> **Değer**<br /> Geçerli pikselin doğrudan aydınlatmayı nasıl yansıttığını açıklayan bir renk.|
|**Malzeme Specular Güç**|Aynasal vurguların yoğunluğunu açıklayan skaler değer.<br /><br /> Daha büyük aynasal güç, daha yoğun ve geniş aynasal vurgular haline gelir.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float`<br /> Geçerli pikseldeki aynasal vurguların yoğunluğunu açıklayan üstel bir terim.|**Erişim**<br /> Özelliğin Model Düzenleyicisi'nden ayarlanabilmesi için **herkese açık;** aksi takdirde, **Özel**.<br /><br /> **Değer**<br /> Geçerli pikseldeki aynasal vurguların yoğunluğunu tanımlayan üs.|
|**Normalleştirilmiş Zaman**|Saniye cinsinden, [0, 1]aralığına normalleştirilmiş zaman, zaman 1'e ulaştığında, 0'a sıfırlanır.<br /><br /> Bunu, örneğin doku koordinatlarını, renk değerlerini veya diğer öznitelikleri animasyonu yapmak için gölgelendirme hesaplamalarında parametre olarak kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float`<br /> Normalleştirilmiş zaman, saniyeler içinde.|None|
|**Zaman**|Saniyeler içinde zaman.<br /><br /> Bunu, örneğin doku koordinatlarını, renk değerlerini veya diğer öznitelikleri animasyonu yapmak için gölgelendirme hesaplamalarında parametre olarak kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float`<br /> Zaman, saniyeler içinde.|None|