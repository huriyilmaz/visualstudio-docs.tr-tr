---
title: Gölgelendiricilerle çalışma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3a22be61d5f4c05720a5ff223806f2e14a8bfbc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663954"
---
# <a name="working-with-shaders"></a>Gölgelendiricilerle Çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel gölgelendirici efektlerini tasarlamak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ' de grafik tabanlı gölgelendirici tasarımcısını kullanabilirsiniz. Bu gölgelendiriciler, DirectX tabanlı oyununuzda veya uygulamanızda kullanabilirsiniz.

## <a name="shaders"></a>Gölgelendiriciler
 *Gölgelendirici* , grafik hesaplamaları gerçekleştiren bir bilgisayar programıdır — Örneğin, köşe dönüştürmeleri veya piksel renklendirme — ve genellikle CPU yerine bir grafik işleme BIRIMI (GPU) üzerinde çalışır. Geleneksel, sabit işlevli grafik işlem hattının çoğu aşamaları gölgelendirici programları tarafından gerçekleştirildiğinden, uygulamanızın ihtiyaçlarına özgü bir işlem hattı oluşturmak için bunları kullanabilirsiniz.

 En yaygın gölgelendiriciler türleri köşe *gölgelendiricsahiptir*ve bu, her köşe için hesaplamaları gerçekleştirir ve sabit işlev dönüştürme ve aydınlatma devresi ile programlanabilir olmayan grafik donanımlarını ve bunu gerçekleştiren *piksel gölgelendiricilerini*değiştirir bir pikselin rengini belirleyecek ve sabit işlevli Color-birleştirici devresi öğesini programlanabilir olmayan grafik donanımında değiştirecek piksel başına hesaplamalar. Modern grafik*donanımı, grafik*hesaplamaları için çok sayıda gölgelendiriciler, *etki alanı gölgelendiriciler*ve grafik hesaplamaları için *geometri gölgelendiriciler* ve grafik olmayan hesaplamalar için bilgi *işlem gölgelendiricileri* daha da yaptı. Bu aşamaların hiçbiri programlanabilir olmayan grafik donanımında bile kullanılabilir değildir. Gölgelendiriciler, veri-paralel (SıMD) ve grafik merkezli (nokta ürün) yönergelerini sağlayan bütünleştirilmiş kod benzeri bir dil kullanılarak oluşturulmuştur. Artık gölgelendiriciler, genellikle HLSL (yüksek düzey gölgelendirici dili) gibi yüksek düzey, C benzeri diller kullanılarak oluşturulur.

 Gölgelendirici tasarımcısını, kod girip derlemek yerine etkileşimli olarak Piksel gölgelendiricileri oluşturmak için kullanabilirsiniz. Gölgelendirici tasarımcısında bir gölgelendirici, verileri ve işlemleri temsil eden bir dizi düğüm ve veri değerleri akışını temsil eden düğümler ve gölgelendirici üzerinden ara sonuçlar arasındaki bağlantıları tarafından tanımlanır. Gölgelendirici tasarımcısında bu yaklaşımı ve gerçek zamanlı önizlemeyi kullanarak, gölgelendirici yürütülmesini daha kolay bir şekilde görselleştirin ve deneme aracılığıyla ilginç gölgelendirici varyasyonlarını keşfedebilirsiniz.

## <a name="dgsl-documents"></a>DGSL belgeleri
 Gölgelendirici Tasarımcısı, gölgelendirilmemiş grafik biçimlendirme dili (DGML) tabanlı bir XML biçimi olan yönlendirilmiş Graf gölgelendirici dili (DGSL) biçiminde gölgelendiriciler kaydeder. Model düzenleyicisinde DGSL gölgelendiricileri doğrudan 3-b modellere uygulayabilirsiniz. Bununla birlikte, uygulamanızda bir DGSL gölgelendiricisi kullanabilmeniz için, bunu DirectX 'in anladığı bir biçime dışarı aktarmanız gerekir — örneğin, HLSL.

 DGSL, DGML ile uyumlu olduğundan, bir DGML belgelerini analiz etmek için tasarlanan araçları kullanarak DGSL Gölgelendiricinizi analiz edebilirsiniz. DGML hakkında daha fazla bilgi için bkz. [yönlendirilmiş grafik biçimlendirme dilini (DGML) anlama](https://msdn.microsoft.com/library/ee842619.aspx).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Gölgelendirici Tasarımcısı](../designers/shader-designer.md)|Gölgelendiricilerle çalışmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Gölgelendirici Tasarımcısının nasıl kullanılacağını açıklar.|
|[Gölgelendirici Tasarımcısı Düğümleri](../designers/shader-designer-nodes.md)|Grafik efektlerini başarmak için kullanabileceğiniz Gölgelendirici Tasarımcısı düğümlerinin türlerini açıklar.|
|[Gölgelendirici Tasarımcısı Örnekleri](../designers/shader-designer-examples.md)|Yaygın grafik efektlerini başarmak için Gölgelendirici Tasarımcısının nasıl kullanılacağını gösteren konuların bağlantılarını sağlar.|
