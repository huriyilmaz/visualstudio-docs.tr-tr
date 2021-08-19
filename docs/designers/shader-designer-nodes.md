---
title: Gölgelendirici Tasarımcısı Düğümleri
description: Grafik etkileri oluşturmak için kullanabileceğiniz çeşitli Gölgelendirici Tasarımcısı düğümleri hakkında bilgi edinmek için belgelerin bu bölümündeki makaleleri kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: b6359f48339bdaff781960d5fcbaafcfc8c1a9d7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112054"
---
# <a name="shader-designer-nodes"></a>Gölgelendirici Tasarımcısı düğümleri
Belgelerin bu bölümündeki makaleler, grafik etkileri oluşturmak için kullanabileceğiniz çeşitli Gölgelendirici Tasarımcısı düğümleri hakkında bilgi içerir.

## <a name="nodes-and-node-types"></a>Düğümler ve düğüm türleri
Gölgelendirici Tasarımcısı görsel etkileri grafik olarak temsil eder. Bu graflar, hedeflenen etkiyi elde etmek için özel olarak seçilen ve bağlanan düğümlerden tasarlanmıştır. Her düğüm bir bilgi parçasını veya matematiksel işlevi temsil eder ve aralarındaki bağlantılar, sonucu elde etmek için bilgilerin grafikten nasıl akmaya devam ettiğini temsil eder. Gölgelendirici Tasarımcısı altı farklı düğüm türü (filtreler, doku düğümleri, parametreler, sabitler, yardımcı düğümler ve matematik düğümleri) sağlar ve her türe ait birkaç tek düğüm vardır. Bu düğümler ve düğüm türleri bu bölümdeki diğer makalelerde açıklanmıştır. Daha fazla bilgi için bu belgenin sonundaki bağlantılara bakın.

## <a name="node-structure"></a>Düğüm yapısı
Tüm düğümler ortak öğelerin birleşimini içerir. Her düğümün sağ tarafında en az bir çıkış terminali vardır (gölgelendiricinin çıkışını temsil eden son renk düğümü dışında). Hesaplamaları veya doku örnekleyicileri temsil eden düğümlerin sol tarafında giriş terminalleri vardır, ancak bilgileri temsil eden düğümlerde giriş terminali yoktur. Çıkış terminalleri, bilgileri bir düğümden diğerine taşımak için giriş terminaline bağlanır.

### <a name="promotion-of-inputs"></a>Girişlerin yükseltmesi
Gölgelendirici Tasarımcısı'nın sonuç olarak bir oyun veya uygulamada etkinin kullanılana kadar HLSL kaynak kodu oluşturması gerekir, çünkü Gölgelendirici Tasarımcısı düğümleri HLSL'nin kullandığı tür yükseltme kurallarına tabi olur. Grafik donanımı öncelikli olarak kayan nokta değerleri üzerinde çalıştıklarından, farklı türler arasında tür yükseltmesi (örneğin, 'den veya 'den'e) `int` `float` yaygın `float` `double` değildir. Bunun yerine, grafik donanımı aynı anda birden çok bilgi parçası üzerinde aynı işlemi kullandığı için, en uzun girişin boyutuyla eşleşmesi için bir dizi girişin daha kısa süresinin uzatıldı olduğu farklı bir yükseltme işlemi oluşabilir. Nasıl uzatıldıkları girişin türüne ve ayrıca işlem türüne bağlıdır:

- **Küçük tür skaler bir değerse:**

     Skaler değeri, daha büyük girişe eşit boyutta bir vektöre çoğaltılır. Örneğin, skaler giriş 5.0, işlemdeki en büyük giriş, işlem ne olursa olsun üç öğeli bir vektör olduğunda vektör (5.0, 5.0, 5.0) olur.

- **Daha küçük tür bir vektörse ve işlem çok işlevli ( , /, %, gibi) \* ise:**

     Vektör değeri, daha büyük girişe eşit olan bir vektörde önde gelen öğelere kopyalanır ve sonda yer alan öğeler 1,0 olarak ayarlanır. Örneğin, vektör girişi (5.0, 5.0), dört öğeli bir vektörle çarpılırken vektör (5.0, 5.0, 1.0, 1.0) haline gelir. Bu, çarpma kimliği olan 1.0'ı kullanarak çıkışın üçüncü ve dördüncü öğelerini korur.

- **Daha küçük tür bir vektörse ve işlem eklenebilirse (+, -, gibi) o halde:**

     Vektör değeri, daha büyük girişe eşit olan bir vektörde önde gelen öğelere kopyalanır ve sonda yer alan öğeler 0,0 olarak ayarlanır. Örneğin, vektör girişi (5.0, 5.0), dört öğeli bir vektöre ekli olduğunda vektör (5.0, 5.0, 0.0, 0.0) olur. Bu, 0,0 ek kimliğini kullanarak çıkışın üçüncü ve dördüncü öğelerini korur.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Sabit düğümler](../designers/constant-nodes.md)|Gölgelendirici hesaplamalarında değişmez değerleri ve irdelenmiş köşe durumu bilgilerini temsil etmek için kullanabileceğiniz düğümleri açıklar. Köşe durumu ilişkilendirmeli olduğundan ve bu nedenle her piksel için farklı olduğundan, her piksel gölgelendirici örneği sabitin farklı bir sürümünü alır.|
|[Parametre düğümleri](../designers/parameter-nodes.md)|Gölgelendirici hesaplamalarında kamera konumunu, malzeme özelliklerini, aydınlatma parametrelerini, saati ve diğer uygulama durumu bilgilerini temsil etmek için kullanabileceğiniz düğümleri açıklar.|
|[Doku düğümleri](../designers/texture-nodes.md)|Çeşitli doku türlerini ve geometrilerini örneklemek ve doku koordinatlarını ortak yollarla üretmek veya dönüştürmek için kullanabileceğiniz düğümleri açıklar.|
|[Matematik düğümleri](../designers/math-nodes.md)|Cebirsel, mantık, trigonometrik ve doğrudan HLSL yönergeleriyle eşlene diğer matematik işlemlerini gerçekleştirmek için kullanabileceğiniz düğümleri açıklar.|
|[Yardımcı program düğümleri](../designers/utility-nodes.md)|Genel aydınlatma hesaplamaları gerçekleştirmek için kullanabileceğiniz düğümleri ve doğrudan HLSL yönergeleriyle eş kullanmayan diğer yaygın işlemleri açıklar.|
|[Filtre düğümleri](../designers/filter-nodes.md)|Doku filtreleme ve renk filtreleme gerçekleştirmek için kullanabileceğiniz düğümleri açıklar.|
