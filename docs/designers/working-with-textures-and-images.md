---
title: Dokularla ve Görüntülerle Çalışma
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 110cbbb01f5b86d462a9a5f196735fd4d477fb10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589870"
---
# <a name="work-with-textures-and-images"></a>Dokularla ve görüntülerle çalışma

Visual Studio'daki Görüntü Düzenleyicisi'ni dokular ve görüntüler oluşturmak ve değiştirmek için kullanabilirsiniz. Image Editor, DirectX uygulama geliştirmede kullanılanlar gibi zengin doku ve görüntü biçimlerini destekler.

> [!NOTE]
> Görüntü Düzenleyicisi, simgeler veya imleçler gibi düşük renkli görüntüleri desteklemez. Bu tür görüntüler oluşturmak veya değiştirmek [için, simgeler (C++) için Görüntü Düzenleyicisi'ni](/cpp/windows/image-editor-for-icons)kullanın.

## <a name="textures-and-images"></a>Dokular ve görüntüler

Dokular ve görüntüler, temel düzeyde, grafik uygulamalarında görsel ayrıntı sağlamak için kullanılan veri tablolarıdır. Bir dokunun veya görüntünün sağladığı ayrıntı türü nasıl kullanıldığına bağlıdır, ancak renk örnekleri, alfa (saydamlık) değerleri, yüzey normalleri ve yükseklik değerleri sık karşılaşılan örneklerdir. Doku ve görüntü arasındaki temel fark, bir dokunun şeklin bir temsili ile birlikte kullanılması gerektiğidir (genellikle 3B model— tam bir nesneyi veya sahneyi ifade etmek için), ancak görüntü genellikle nesne nin veya sahnenin tek başına bir temsilidir.

Herhangi bir doku kodlanabilir ve bir doku tutar veri türüne ortogonal bir dizi şekilde sıkıştırılmış, ya da boyutsallık veya doku "şekil" için. Ancak, farklı kodlama ve sıkıştırma yöntemleri farklı veri türleri için daha iyi sonuçlar verir.

Dokuları ve görüntüleri diğer görüntü düzenleyicilerine benzer şekilde oluşturmak ve değiştirmek için Görüntü Düzenleyicisi'ni kullanabilirsiniz. Image Editor ayrıca 3D grafiklerle kullanılmak üzere mipmapping ve diğer özellikleri sağlar ve DirectX'in desteklediği yüksek sıkıştırılmış, donanım hızlandırılmış doku biçimlerinin çoğunu destekler.

Yaygın doku türleri şunlardır:

### <a name="texture-maps"></a>Doku haritaları

Doku eşlemleri, tek, iki veya üç boyutlu matris olarak düzenlenmiş renk değerleri içerir. Bunlar etkilenen nesne üzerinde renk ayrıntısı sağlamak için kullanılır. Renkler genellikle RGB (kırmızı, yeşil, mavi) renk kanalları kullanılarak kodlanır ve saydamlığı temsil eden dördüncü bir kanal olan alfa içerebilir. Daha az yaygın olarak, renkler başka bir renk düzeninde kodlanabilir veya dördüncü kanal alfa dışında veri içerebilir(örneğin, yükseklik).

### <a name="normal-maps"></a>Normal haritalar

Normal haritalar yüzey normalleri içerir. Bunlar etkilenen nesne üzerinde aydınlatma ayrıntısı sağlamak için kullanılır. Normaller genellikle vektörün x, y ve z boyutlarını depolamak için kırmızı, yeşil ve mavi renk bileşenleri kullanılarak kodlanır. Ancak, diğer kodlamalar var-örneğin, kutupsal koordinatları dayalı kodlamalar.

### <a name="height-maps"></a>Yükseklik haritaları

Yükseklik haritaları yükseklik alanı verilerini içerir. İstenilen etkiyi hesaplamak için gölgeli kodu kullanarak etkilenen nesne üzerinde geometrik ayrıntı biçimi sağlamak veya arazi üretimi gibi kullanımlar için veri noktaları sağlamak için kullanılırlar. Yükseklik değerleri genellikle bir dokuda bir kanal kullanılarak kodlanır.

### <a name="cube-maps"></a>Küp haritaları

Küp eşlemleri farklı veri türleri (örneğin, renkler veya normaller) içerebilir, ancak küpün yüzlerinde altı doku olarak düzenlenir. Bu nedenle, küp haritaları doku koordinatları sağlayarak değil, kökeni küpün merkezi olan bir vektör sağlayarak örneklenir; örnek, vektörün küple kesiştiği noktada alınır. Küp eşlemleri yansımaları hesaplamak için kullanılabilecek ortamın yaklaşık bir kısmını sağlamak için kullanılır—bu *ortam eşleme*olarak bilinir —veya temel, iki boyutlu dokulardan daha az distorsiyona sahip küresel nesnelere doku sağlamak için kullanılır.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Görüntü Düzenleyici](../designers/image-editor.md)|Dokular ve görüntülerle çalışmak için Görüntü Düzenleyicisi'nin nasıl kullanılacağını açıklar.|
|[Resim Düzenleyiciörnekleri](../designers/how-to-create-a-basic-texture.md)|Ortak görüntü işleme görevlerini gerçekleştirmek için Görüntü Düzenleyicisi'nin nasıl kullanılacağını gösteren konulara bağlantılar sağlar.|
