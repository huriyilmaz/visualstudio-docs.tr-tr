---
title: Gölgelendirici Tasarımcısı Düğümleri
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75d13aaf5d5b4257ff6ec7c2efc52adbdca7df92
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768791"
---
# <a name="shader-designer-nodes"></a>Gölgelendirici Tasarımcısı düğümleri
Belgelerinin bu bölümündeki makaleler, grafik etkileri oluşturmak için kullanabileceğiniz çeşitli gölgelendirici tasarımcı düğümleri hakkında bilgiler içerir.

## <a name="nodes-and-node-types"></a>Düğümler ve düğüm türleri
Gölgelendirici Tasarımcısı görsel etkileri bir grafik olarak temsil eder. Bu grafikler, özel olarak seçilen ve hedeflenen etkiyi elde etmek için kesin yollarla bağlanan düğümlerden oluşturulmuştur. Her düğüm bir bilgi parçasını veya bir matematik işlevini temsil eder ve aralarındaki bağlantılar, bilgilerin, sonucu oluşturmak için grafik üzerinden nasıl akacağını gösterir. Gölgelendirici Tasarımcısı, üç farklı düğüm türü (filtreler, doku düğümleri, parametreler, sabitler, yardımcı program düğümleri ve matematik düğümleri) ve birçok tekil düğüm her bir türe aittir. Bu düğümler ve düğüm türleri, bu bölümün diğer makalelerinde açıklanmıştır. Daha fazla bilgi için bu belgenin sonundaki bağlantılara bakın.

## <a name="node-structure"></a>Düğüm yapısı
Tüm düğümler ortak öğelerin birleşiminden oluşur. Her düğümün sağ tarafında en az bir çıkış terminali vardır (gölgelendirici çıkışını temsil eden son renk düğümü hariç). Hesaplamaları veya doku örnekleyicileri temsil eden düğümler, sol taraflarındaki giriş terminallerine sahiptir, ancak bilgileri temsil eden düğümlerin giriş terminalleri yoktur. Çıkış terminalleri, bir düğümden diğerine bilgi taşımak için giriş terminallere bağlanır.

### <a name="promotion-of-inputs"></a>Girişlerin yükseltilmesi
Gölgelendirici Tasarımcısının, efektin bir oyun veya uygulamada kullanılabilmesi için sonunda HLSL kaynak kodu oluşturması gerektiğinden, gölgelendirici tasarımcı düğümleri HLSL 'ın kullandığı tür yükseltme kurallarına tabidir. Grafik donanımı öncelikli olarak kayan nokta değerlerinde çalıştığından, farklı türler arasında yükseltme yapın — Örneğin, öğesinden `int` `float` veya türünden `float` `double` - Bunun yerine, grafik donanımı birden çok bilgi halinde aynı işlemi aynı anda kullandığından, bir dizi girişin daha kısa olması, en uzun giriş boyutuyla eşleşecek şekilde uzadığı için farklı bir promosyon türü meydana gelebilir. Nasıl boyunun, girişin türüne ve ayrıca işlemin kendisine göre belirlenir:

- **Daha küçük tür skaler bir değer ise:**

     Skalar değerin değeri, daha büyük girişe eşit olan bir Vector öğesine çoğaltılır. Örneğin, işlemin en büyük girişi işlemin ne olursa olsun üç öğeli bir vektör olduğunda, 5,0 skaler girişi vektörü (5,0, 5,0, 5,0) olur.

- **Küçük tür bir Vector ise ve işlem çarpanda ( \* ,/,%, vb.) varsa:**

     Vector değeri, daha büyük girişe eşit olan bir Vector öğesinin önde gelen öğelerine kopyalanır ve sondaki öğeler 1,0 olarak ayarlanır. Örneğin, vektör girişi (5,0, 5,0) dört öğeli vektörle çarpıldığı zaman vektör (5,0, 5,0, 1,0, 1,0) olur. Bu, çarpma kimliği, 1,0 kullanılarak çıktının üçüncü ve dördüncü öğelerini korur.

- **Daha küçük tür bir Vector ise ve işlem eklenebilir (+,-, vb.) ise:**

     Vector değeri, daha büyük girişe eşit olan bir Vector öğesinin önde gelen öğelerine kopyalanır ve sondaki öğeler 0,0 olarak ayarlanır. Örneğin, vektör girişi (5,0, 5,0) dört öğeli bir Vector öğesine eklendiğinde vektör (5,0, 5,0, 0,0, 0,0) olur. Bu, 0,0 ek kimliğini kullanarak çıktının üçüncü ve dördüncü öğelerini korur.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Sabit düğümler](../designers/constant-nodes.md)|Sabit değerleri temsil etmek için kullanabileceğiniz düğümleri ve gölgelendirici hesaplamalarında ara durum bilgilerini enterpolasyonlarla dengeleyebileceğinizi açıklar. Köşe durumu enterpolacağından ve bu nedenle her bir piksel için farklı olduğundan, her piksel gölgelendirici örneği, sabit 'in farklı bir sürümünü alır.|
|[Parametre düğümleri](../designers/parameter-nodes.md)|Gölgelendirici hesaplamalarında kamera konumunu, malzeme özelliklerini, aydınlatma parametrelerini, saati ve diğer uygulama durumu bilgilerini temsil etmek için kullanabileceğiniz düğümleri açıklar.|
|[Doku düğümleri](../designers/texture-nodes.md)|Çeşitli doku türlerini ve geometrileri örneklemek ve ortak yollarla doku koordinatları oluşturmak veya dönüştürmek için kullanabileceğiniz düğümleri açıklar.|
|[Matematik düğümleri](../designers/math-nodes.md)|Algebraic, Logic, trigonometrik ve doğrudan HLSL yönergelerine eşlenen diğer matematiksel işlemleri gerçekleştirmek için kullanabileceğiniz düğümleri açıklar.|
|[Yardımcı program düğümleri](../designers/utility-nodes.md)|Genel aydınlatma hesaplamalarını ve doğrudan HLSL yönergelerine eşlenmez diğer yaygın işlemleri gerçekleştirmek için kullanabileceğiniz düğümleri açıklar.|
|[Filtre düğümleri](../designers/filter-nodes.md)|Doku filtrelemesi ve renk filtrelemesi gerçekleştirmek için kullanabileceğiniz düğümleri açıklar.|
