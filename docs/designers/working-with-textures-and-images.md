---
title: Dokularla ve Görüntülerle Çalışma
description: DirectX uygulama geliştirmede kullanılanlar gibi biçimlerdeki dokuları ve görüntüleri oluşturmak ve değiştirmek için Visual Studio görüntü düzenleyicisini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 37a5d3b0766013b127aa939943f7811202d935db
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035351"
---
# <a name="work-with-textures-and-images"></a>Dokularla ve görüntülerle çalışma

dokuları ve görüntüleri oluşturmak ve değiştirmek için Visual Studio görüntü düzenleyicisini kullanabilirsiniz. Görüntü Düzenleyicisi, DirectX uygulama geliştirmede kullanılanlarla benzer zengin doku ve görüntü biçimlerini destekler.

> [!NOTE]
> Görüntü Düzenleyicisi, simgeler veya imleçler gibi düşük renkli görüntüleri desteklemez. Bu tür resimleri oluşturmak veya değiştirmek için, [simgeler Için görüntü düzenleyicisini kullanın (C++)](/cpp/windows/image-editor-for-icons).

## <a name="textures-and-images"></a>Dokular ve görüntüler

Dokular ve görüntüler, temel düzeyde, yalnızca grafik uygulamalarında görsel ayrıntı sağlamak için kullanılan veri tablolarından oluşur. Bir dokunun veya görüntünün sağladığı ayrıntı türü, nasıl kullanıldığına bağlıdır, ancak renk örnekleri, Alfa (saydamlık) değerleri, yüzey Normals ve yükseklik değerleri ortak örnektir. Bir doku ve görüntü arasındaki birincil fark, bir dokunun bir şeklin temsili ile birlikte kullanılması (genellikle 3B model), tam bir nesne veya sahneyi ifade etmek için, ancak bir görüntü genellikle nesnenin veya sahnenin tek başına gösterimidir.

Herhangi bir doku, bir dokusunun tuttuğu verilerin türüne veya dokunun boyut veya "şekline" göre birbirine dik bir şekilde kodlanabilir ve sıkıştırılabilir. Ancak, farklı kodlama ve sıkıştırma yöntemleri farklı veri türleri için daha iyi sonuçlar verir.

Görüntü düzenleyicisini, diğer resim düzenleyicilerine benzeyen dokular ve görüntüler oluşturmak ve değiştirmek için kullanabilirsiniz. Görüntü Düzenleyicisi Ayrıca, 3B grafiklerle kullanılmak üzere mı eşlemesi ve diğer özellikler sağlar ve DirectX 'in desteklediği, yüksek oranda sıkıştırılmış, donanım hızlandırmalı doku biçimlerinin çoğunu destekler.

Yaygın dokuların türleri şunlardır:

### <a name="texture-maps"></a>Doku haritaları

Doku haritaları bir, iki veya üç boyutlu matris olarak düzenlenmiş renk değerleri içerir. Etkilenen nesnede renk ayrıntısı sağlamak için kullanılır. Renkler genellikle RGB (kırmızı, yeşil, mavi) renk kanalları kullanılarak kodlanır ve saydamlığı temsil eden bir dördüncü kanal olan Alpha içerebilir. Daha az yaygın olarak, renkler başka bir renk düzeninde kodlanamaz veya dördüncü kanal Alfa dışında bir veri içerebilir — Örneğin, yükseklik.

### <a name="normal-maps"></a>Normal haritalar

Normal haritalar Yüzey normalleri içerir. Etkilenen nesne üzerinde aydınlatma ayrıntısı sağlamak için kullanılırlar. Normaller genellikle, vektör 'in x, y ve z boyutlarını depolamak için kırmızı, yeşil ve mavi renk bileşenleri kullanılarak kodlanır. Bununla birlikte, diğer kodlamalar vardır; örneğin, kutupsal koordinatları temel alan kodlamalar.

### <a name="height-maps"></a>Yükseklik haritaları

Yükseklik haritaları, yükseklik alanı verileri içerir. Bunlar, istenen etkiyi hesaplamak için gölgelendirici kodu kullanılarak veya teryağmm gibi kullanımlar için veri noktaları sağlamak üzere, etkilenen nesnede geometrik ayrıntı formu sağlamak için kullanılır. Yükseklik değerleri, bir dokusundaki bir kanal kullanılarak yaygın olarak kodlanır.

### <a name="cube-maps"></a>Küp haritaları

Küp haritaları, farklı veri türleri içerebilir — Örneğin, renkler veya normaller —, ancak küpün yüzlerinde altı doku olarak düzenlenir. Bu nedenle, küp haritaları doku koordinatları sağlayarak örneklenmez, ancak kaynağı küpün ortası olan bir vektör sağlayarak; örnek, vector öğesinin kübü kesiştiği noktada alınır. Küp haritaları, yansıma gibi yansımaları hesaplamak için kullanılabilecek ortamın yaklaşık bir kısmını sağlamak için kullanılır. Bu, *ortam eşleme* olarak bilinir — ya da temel kıyasla daha az deformasyonu olan küresel nesnelere doku sağlamak için, iki boyutlu dokuların sağlayabildiği bir değer sağlar.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Görüntü Düzenleyicisi](../designers/image-editor.md)|Dokularla ve görüntülerle çalışmak için görüntü düzenleyicisinin nasıl kullanılacağını açıklar.|
|[Görüntü Düzenleyicisi örnekleri](../designers/how-to-create-a-basic-texture.md)|Ortak görüntü işleme görevlerini gerçekleştirmek için görüntü düzenleyicisinin nasıl kullanılacağını gösteren konuların bağlantılarını sağlar.|
