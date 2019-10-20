---
title: Dokularla ve görüntülerle çalışma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 93813aa734c615e7f045c98c776e600be4ee3fab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663931"
---
# <a name="working-with-textures-and-images"></a>Dokularla ve Görüntülerle Çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dokuları ve görüntüleri oluşturmak ve değiştirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] görüntü düzenleyicisini kullanabilirsiniz. Görüntü Düzenleyicisi, DirectX uygulama geliştirmede kullanılanlarla benzer zengin doku ve görüntü biçimlerini destekler.

> [!NOTE]
> Görüntü Düzenleyicisi, simgeler veya imleçler gibi düşük renkli görüntüleri desteklemez. Bu tür resimleri oluşturmak veya değiştirmek için, [simgeler Için görüntü düzenleyicisini](https://msdn.microsoft.com/library/586d2b8b-0348-4883-a85d-1ff0ddbf14dd)kullanın.

## <a name="textures-and-images"></a>Dokular ve görüntüler
 Dokular ve görüntüler, temel düzeyde, yalnızca grafik uygulamalarında görsel ayrıntı sağlamak için kullanılan veri tablolarından oluşur. Bir dokunun veya görüntünün sağladığı ayrıntı türü, nasıl kullanıldığına bağlıdır, ancak renk örnekleri, Alfa (saydamlık) değerleri, yüzey Normals ve yükseklik değerleri ortak örnektir. Bir doku ve görüntü arasındaki birincil fark, bir dokunun, bir şeklin temsili ile birlikte kullanılması (genellikle 3-b model — tam bir nesne veya sahneyi ifade etmek, ancak bir görüntünün genellikle nesnenin veya sahnenin tek başına bir gösterimi olması anlamına gelir. .

 Yaygın dokuların türleri şunlardır:

 Doku haritaları doku haritaları, tek, iki veya üç boyutlu bir matris olarak düzenlenmiş renk değerleri içerir. Etkilenen nesnede renk ayrıntısı sağlamak için kullanılır. Renkler genellikle RGB (kırmızı, yeşil, mavi) renk kanalları kullanılarak kodlanır ve saydamlığı temsil eden bir dördüncü kanal olan Alpha içerebilir. Daha az yaygın olarak, renkler başka bir renk düzeninde kodlanamaz veya dördüncü kanal Alfa dışında bir veri içerebilir — Örneğin, yükseklik.

 Normal haritalar normal haritalar Yüzey normalleri içerir. Etkilenen nesne üzerinde aydınlatma ayrıntısı sağlamak için kullanılırlar. Normaller genellikle, vektör 'in x, y ve z boyutlarını depolamak için kırmızı, yeşil ve mavi renk bileşenleri kullanılarak kodlanır. Bununla birlikte, diğer kodlamalar vardır; örneğin, kutupsal koordinatları temel alan kodlamalar.

 Yükseklik haritaları yükseklik haritaları, yükseklik alanı verileri içerir. Bunlar, istenen etkiyi hesaplamak için gölgelendirici kodu kullanılarak veya teryağmm gibi kullanımlar için veri noktaları sağlamak üzere, etkilenen nesnede geometrik ayrıntı formu sağlamak için kullanılır. Yükseklik değerleri, bir dokusundaki bir kanal kullanılarak yaygın olarak kodlanır.

 Küp haritaları küp haritaları, farklı veri türleri içerebilir — Örneğin, renkler veya normaller —, ancak küpün yüzlerinde altı doku olarak düzenlenir. Bu nedenle, küp haritaları doku koordinatları sağlayarak örneklenmez, ancak kaynağı küpün ortası olan bir vektör sağlayarak; örnek, vector öğesinin kübü kesiştiği noktada alınır. Küp haritaları, yansıma gibi yansımaları hesaplamak için kullanılabilecek ortamın yaklaşık bir kısmını sağlamak için kullanılır. Bu, *ortam eşleme*olarak bilinir — ya da temel kıyasla daha az deformasyonu olan küresel nesnelere doku sağlamak için, iki boyutlu dokuların kullanılabilmesi için girmelisiniz.

 Herhangi bir doku, bir dokusunun tuttuğu verilerin türüne veya dokunun boyut veya "şekline" göre birbirine dik bir şekilde kodlanabilir ve sıkıştırılabilir. Ancak, farklı kodlama ve sıkıştırma yöntemleri farklı veri türleri için daha iyi sonuçlar verir.

 Görüntü düzenleyicisini, diğer resim düzenleyicilerine benzeyen dokular ve görüntüler oluşturmak ve değiştirmek için kullanabilirsiniz. Görüntü Düzenleyicisi Ayrıca, 3-b grafiklerle kullanılmak üzere, mı eşlemesi ve diğer özellikler sağlar ve DirectX 'in desteklediği yüksek oranda sıkıştırılmış, donanım hızlandırmalı doku biçimlerinin çoğunu destekler.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Görüntü Düzenleyicisi](../designers/image-editor.md)|Dokularla ve görüntülerle çalışmak için görüntü düzenleyicisinin nasıl kullanılacağını açıklar.|
|[Görüntü Düzenleyicisi Örnekleri](../designers/image-editor-examples.md)|Ortak görüntü işleme görevlerini gerçekleştirmek için görüntü düzenleyicisinin nasıl kullanılacağını gösteren konuların bağlantılarını sağlar.|
