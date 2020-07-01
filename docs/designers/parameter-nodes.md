---
title: Parametre Düğümleri
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 986b7bcc75dd39b0d41d8f614a68734a65afca0b
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768818"
---
# <a name="parameter-nodes"></a>Parametre düğümleri

Gölgelendirici tasarımcısında, parametre düğümleri, örneğin malzeme özellikleri, yön ışıkları, kamera konumu ve saat gibi uygulama denetimi altında bulunan gölgelendiriciye ait girişleri temsil eder. Bu parametreleri her çizim çağrısıyla değiştirebildiğinden, bir nesneye farklı görünümler vermek için aynı gölgelendiriciyi kullanabilirsiniz.

## <a name="parameter-node-reference"></a>Parametre düğümü başvurusu

|Node|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Kamera dünya konumu**|Kameranın dünya alanı konumu.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Kameranın konumu.|Hiçbiri|
|**Hafif Yön**|Dünya alanındaki bir ışık kaynağından ışığın saçıldığı yönü tanımlayan vektör.<br /><br /> Bunu, dünya alanındaki aydınlatma ve yansımalı katkıları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float3`<br /> Geçerli pikselden bir ışık kaynağına vektör.|Hiçbiri|
|**Malzeme çevresel**|Geçerli pikselin dolaylı aydınlatmaya yönelik olarak dağıtılmış renk katkısı.<br /><br /> Bir pikselin dağıtma rengi, aydınlatma 'ın kaba yüzeylerle nasıl etkileşime gireceğini taklit eder. Gerçek dünyadaki bir nesnenin görünümüne dolaylı aydınlatmanın nasıl katkıda bulunduğunu tahmin etmek için malzeme çevresel parametresini kullanabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin dolaylı ve yani çevresel — aydınlatma nedeniyle dağıtma rengi.|**Erişim**<br /> Özelliğin model düzenleyicisinden ayarlan, özelliği etkinleştirmek için **ortak** . Aksi takdirde, **özel**.<br /><br /> **Değer**<br /> Geçerli pikselin dolaylı ve yani çevresel — aydınlatma nedeniyle dağıtma rengi.|
|**Malzeme dağıtma**|Geçerli pikselin doğrudan aydınlatmayı nasıl kullandığını açıklayan bir renk.<br /><br /> Bir pikselin dağıtma rengi, aydınlatma 'ın kaba yüzeylerle nasıl etkileşime gireceğini taklit eder. Şu anki pikselin, yönlü, nokta ve spot ışıklar gibi geçerli pikselin yayılmış şeklini değiştirmek için malzeme dağıtma parametresini kullanabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin doğrudan aydınlatmayı nasıl kullandığını açıklayan bir renk.|**Erişim**<br /> Özelliğin model düzenleyicisinden ayarlan, özelliği etkinleştirmek için **ortak** . Aksi takdirde, **özel**.<br /><br /> **Değer**<br /> Geçerli pikselin doğrudan aydınlatmayı nasıl kullandığını açıklayan bir renk.|
|**Malzeme yanıltıcı**|Geçerli pikselin kendisine sağladığı aydınlatmaya sahip olan renk katkısı.<br /><br /> Bunu, bir IşIME nesnesinin benzetimini yapmak için kullanabilirsiniz; diğer bir deyişle, kendi ışığını sağlayan bir nesnesidir. Bu ışık diğer nesneleri etkilemez.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin kendi kendini sağlayan aydınlatma nedeniyle oluşan renk katkısı.|**Erişim**<br /> Özelliğin model düzenleyicisinden ayarlan, özelliği etkinleştirmek için **ortak** . Aksi takdirde, **özel**.<br /><br /> **Değer**<br /> Geçerli pikselin kendi kendini sağlayan aydınlatma nedeniyle oluşan renk katkısı.|
|**Malzeme yansımalı**|Geçerli pikselin doğrudan aydınlatmayı nasıl yansıttığını açıklayan bir renk.<br /><br /> Bir pikselin yansımalı rengi, aydınlatma 'ın yumuşak, ayna benzeri yüzeyler ile nasıl etkileşime gireceğini taklit eder. Geçerli pikselin doğrudan aydınlatmayı (yönlü, nokta ve spot ışıklar) nasıl yansıttığını değiştirmek için malzeme yansımalı parametresini kullanabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin doğrudan aydınlatmayı nasıl yansıttığını açıklayan bir renk.|**Erişim**<br /> Özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için **genel** . Aksi takdirde, **özel**.<br /><br /> **Değer**<br /> Geçerli pikselin doğrudan aydınlatmayı nasıl yansıttığını açıklayan bir renk.|
|**Malzeme yansımalı güç**|Yansımalı vurguların yoğunluğunu açıklayan skaler bir değer.<br /><br /> Yansımalı gücün ne kadar büyük olması, Yansımalı vurguların daha kuvvetli ve en yüksek olması olur.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float`<br /> Geçerli pikselde Yansımalı vurguların yoğunluğunu tanımlayan üstel bir terim.|**Erişim**<br /> Özelliğin model düzenleyicisinden ayarlan, özelliği etkinleştirmek için **ortak** . Aksi takdirde, **özel**.<br /><br /> **Değer**<br /> Geçerli pikselde Yansımalı vurguların yoğunluğunu tanımlayan üs.|
|**Normalleştirilmiş zaman**|[0, 1] aralığında normalleştirildiğinde, bu süre 1 ' e ulaştığında 0 olarak sıfırlanıyorsa, saniye cinsinden süre.<br /><br /> Bunu gölgelendirici hesaplamalarında bir parametre olarak kullanabilirsiniz. Örneğin doku koordinatlarına, renk değerlerine veya diğer özniteliklere animasyon uygulayabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float`<br /> Saniye cinsinden normalleştirilmiş zaman.|Hiçbiri|
|**Saat**|Saniye cinsinden süre.<br /><br /> Bunu gölgelendirici hesaplamalarında bir parametre olarak kullanabilirsiniz. Örneğin doku koordinatlarına, renk değerlerine veya diğer özniteliklere animasyon uygulayabilirsiniz.<br /><br /> **Çıktıların**<br /><br /> `Output`: `float`<br /> Saniye cinsinden süre.|Hiçbiri|