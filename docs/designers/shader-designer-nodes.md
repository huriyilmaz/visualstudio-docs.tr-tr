---
title: Gölgelendirici Tasarımcısı Düğümleri
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23877f9b94b498d87a89ae8e657aa2fe52984953
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72634922"
---
# <a name="shader-designer-nodes"></a>Gölgeli Tasarımcı düğümleri
Belgelerin bu bölümündeki makaleler, grafik efektleri oluşturmak için kullanabileceğiniz çeşitli Shader Designer düğümleri hakkında bilgi içerir.

## <a name="nodes-and-node-types"></a>Düğüm ler ve düğüm türleri
Shader Designer görsel efektleri grafik olarak temsil eder. Bu grafikler, özellikle seçilen ve istenen etkiyi elde etmek için hassas yollarla bağlı düğümlerden oluşturulur. Her düğüm bir bilgi parçasını veya matematiksel bir işlevi temsil eder ve aralarındaki bağlantılar, sonucu oluşturmak için bilginin grafikte nasıl aktığını gösterir. Gölgeli Tasarımcısı filtreler, doku düğümleri, parametreler, sabitler, yardımcı program düğümleri ve matematik düğümleri olmak üzere altı farklı düğüm türü sağlar ve her türe ait birkaç ayrı düğüm vardır. Bu düğüm ve düğüm türleri bu bölümdeki diğer makalelerde açıklanmıştır. Daha fazla bilgi için bu belgenin sonundaki bağlantılara bakın.

## <a name="node-structure"></a>Düğüm yapısı
Tüm düğümler ortak öğelerin bir kombinasyonuoluşur. Her düğümün sağ tarafında en az bir çıkış terminali vardır (gölgenin çıktısını temsil eden son renk düğümü hariç). Hesaplamaları veya doku örnekleyicilerini temsil eden düğümlerin sol taraflarında giriş terminalleri vardır, ancak bilgileri temsil eden düğümlerin giriş terminalleri yoktur. Çıktı terminalleri, bilgileri bir düğümden diğerine taşımak için giriş terminallerine bağlanır.

### <a name="promotion-of-inputs"></a>Girdilerin tanıtımı
Shader Designer sonuçta etkisi bir oyun veya uygulamada kullanılabilir böylece HLSL kaynak kodu oluşturmak gerekir, çünkü Shader Designer düğümleri HLSL kullandığı tür promosyon kurallarına tabidir. Grafik donanımı öncelikle kayan nokta değerlerinde çalıştığından, farklı türler `int` `float`arasında promosyon `float` `double`yazın (örneğin, birinden, veya birinden- sık rastlanan bir durumdur. Bunun yerine, grafik donanımı aynı anda birden çok bilgi parçası üzerinde aynı işlemi kullandığından, bir dizi girdiden daha kısa olanın en uzun girdinin boyutuyla eşleşecek şekilde uzattığı farklı bir tür promosyon oluşabilir. Nasıl uzatılır giriş türüne ve ayrıca işlemin kendisine bağlıdır:

- **Küçük tür skaler bir değerse, o zaman:**

     Skaler değeri büyük giriş boyutu eşit bir vektör olarak çoğaltılır. Örneğin, skaler giriş 5.0, işlemin en büyük girişi, işlem ne olursa olsun üç öğeli bir vektör olduğunda vektör (5.0, 5.0, 5.0) olur.

- **Küçük tür bir vektörise ve işlem çarpanise\*(, /, %, vb.), sonra:**

     Vektörün değeri, büyük girişe eşit boyutta bir vektörün öncü elemanlarına kopyalanır ve sondaki öğeler 1,0 olarak ayarlanır. Örneğin, vektör girişi (5.0, 5.0) dört elemanlı bir vektörle çarpıldığında vektör (5.0, 5.0, 1.0, 1.0) olur. Bu, çarpıtma kimliği, 1.0 kullanarak çıktının üçüncü ve dördüncü öğelerini korur.

- **Küçük tür bir vektörse ve işlem katkı maddesiise (+, -, vb.), sonra:**

     Vektörün değeri, büyük girişe eşit boyutta bir vektörün öncü elemanlarına kopyalanır ve sondaki öğeler 0,0 olarak ayarlanır. Örneğin, vektör girişi (5.0, 5.0) dört öğeli bir vektöre eklendiğinde vektör (5.0, 5.0, 0.0, 0.0) olur. Bu, katkı kimliği 0.0'ı kullanarak çıktının üçüncü ve dördüncü öğelerini korur.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Sabit düğümler](../designers/constant-nodes.md)|Shader hesaplamalarında gerçek değerleri ve enterpol-durum bilgilerini temsil etmek için kullanabileceğiniz düğümleri açıklar. Vertex-durum enterpolasyonlu olduğundan ve bu nedenle, her piksel için farklı-her piksel-shader örneği sabitin farklı bir sürümünü alır.|
|[Parametre düğümleri](../designers/parameter-nodes.md)|Gölgeli hesaplamalarda kamera konumunu, malzeme özelliklerini, ışık parametrelerini, zamanı ve diğer uygulama durumu bilgilerini temsil etmek için kullanabileceğiniz düğümleri açıklar.|
|[Doku düğümleri](../designers/texture-nodes.md)|Çeşitli doku türlerini ve geometrileri örneklemek ve doku koordinatlarını ortak yollarla oluşturmak veya dönüştürmek için kullanabileceğiniz düğümleri açıklar.|
|[Matematik düğümleri](../designers/math-nodes.md)|Cebirsel, mantık, trigonometrik ve doğrudan HLSL yönergeleriyle eşleyen diğer matematiksel işlemleri gerçekleştirmek için kullanabileceğiniz düğümleri açıklar.|
|[Yardımcı program düğümleri](../designers/utility-nodes.md)|Ortak aydınlatma hesaplamaları gerçekleştirmek için kullanabileceğiniz düğümleri ve hlsl yönergeleriyle doğrudan eşlemeyen diğer yaygın işlemleri açıklar.|
|[Filtre düğümleri](../designers/filter-nodes.md)|Doku filtreleme ve renk filtreleme gerçekleştirmek için kullanabileceğiniz düğümleri açıklar.|
