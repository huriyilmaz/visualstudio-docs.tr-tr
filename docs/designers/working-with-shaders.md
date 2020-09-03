---
title: Gölgelendiricilerle Çalışma
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7ccb4f838c702cb1843d5c0f44dd7f54219f27a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75589779"
---
# <a name="work-with-shaders"></a>Gölgelendiricilerle çalışma

Özel gölgelendirici efektlerini tasarlamak için, Visual Studio 'da grafik tabanlı gölgelendirici tasarımcısını kullanabilirsiniz. Bu gölgelendiriciler, DirectX tabanlı oyununuzda veya uygulamanızda kullanabilirsiniz.

## <a name="shaders"></a>Gölgelendiriciler

*Gölgelendirici* , grafik hesaplamaları gerçekleştiren bir bilgisayar programıdır — Örneğin, köşe dönüştürmeleri veya piksel renklendirme — ve genellikle CPU yerine bir grafik işleme BIRIMI (GPU) üzerinde çalışır. Geleneksel, sabit işlevli grafik işlem hattının çoğu aşamaları gölgelendirici programları tarafından gerçekleştirildiğinden, uygulamanızın ihtiyaçlarına özgü bir işlem hattı oluşturmak için bunları kullanabilirsiniz.

En yaygın tür gölgelendiriciler, köşe *gölgelendiricilerin*kullanıldığı ve sabit işlevli bir dönüştürme ve aydınlatma devresi ile programlanabilir olmayan grafik donanımlarını değiştirme ve bir pikselin rengini belirleyen ve sabit işlevli renk-birleştirici devresi *' i programlanabilir*grafik donanımında değiştirme. Modern grafik*donanımı, grafik*hesaplamaları için çok sayıda gölgelendiriciler, *etki alanı gölgelendiriciler*ve grafik hesaplamaları için *geometri gölgelendiriciler* ve grafik olmayan hesaplamalar için bilgi *işlem gölgelendiricileri* daha da yaptı. Bu aşamaların hiçbiri programlanabilir olmayan grafik donanımında bile kullanılabilir değildir. Gölgelendiriciler, veri-paralel (SıMD) ve grafik merkezli (nokta ürün) yönergelerini sağlayan bütünleştirilmiş kod benzeri bir dil kullanılarak oluşturulmuştur. Artık gölgelendiriciler, genellikle HLSL (yüksek düzey gölgelendirici dili) gibi yüksek düzey, C benzeri diller kullanılarak oluşturulur.

Gölgelendirici tasarımcısını, kod girip derlemek yerine etkileşimli olarak Piksel gölgelendiricileri oluşturmak için kullanabilirsiniz. Gölgelendirici tasarımcısında bir gölgelendirici, verileri ve işlemleri temsil eden bir dizi düğüm ve veri değerleri akışını temsil eden düğümler ve gölgelendirici üzerinden ara sonuçlar arasındaki bağlantıları tarafından tanımlanır. Gölgelendirici tasarımcısında bu yaklaşımı ve gerçek zamanlı önizlemeyi kullanarak, gölgelendirici yürütülmesini daha kolay bir şekilde görselleştirin ve deneme aracılığıyla ilginç gölgelendirici varyasyonlarını keşfedebilirsiniz.

## <a name="dgsl-documents"></a>DGSL belgeleri

Gölgelendirici Tasarımcısı, gölgelendirilmemiş grafik biçimlendirme dili (DGML) tabanlı bir XML biçimi olan yönlendirilmiş Graf gölgelendirici dili (DGSL) biçiminde gölgelendiriciler kaydeder. DGSL gölgelendiricileri doğrudan model düzenleyicisinde 3B modellere uygulayabilirsiniz. Bununla birlikte, uygulamanızda bir DGSL gölgelendiricisi kullanabilmeniz için, bunu DirectX 'in anladığı bir biçime dışarı aktarmanız gerekir — örneğin, HLSL.

DGSL, DGML ile uyumlu olduğundan, bir DGML belgelerini analiz etmek için tasarlanan araçları kullanarak DGSL Gölgelendiricinizi analiz edebilirsiniz. DGML hakkında daha fazla bilgi için bkz. [yönlendirilmiş grafik biçimlendirme dilini (DGML) anlama](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Gölgelendirici Tasarımcısı](../designers/shader-designer.md)|Gölgelendiricilerle çalışmak için Visual Studio gölgelendirici Tasarımcısı 'nın nasıl kullanılacağını açıklar.|
|[Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)|Grafik efektlerini başarmak için kullanabileceğiniz Gölgelendirici Tasarımcısı düğümlerinin türlerini açıklar.|
|[Gölgelendirici Tasarımcısı örnekleri](../designers/how-to-create-a-basic-color-shader.md)|Yaygın grafik efektlerini başarmak için Gölgelendirici Tasarımcısının nasıl kullanılacağını gösteren konuların bağlantılarını sağlar.|
