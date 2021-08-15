---
title: Gölgelendiricilerle Çalışma
description: Grafik tabanlı Gölgelendirici Tasarımcısını kullanarak özel gölgelendirici etkileri tasarlamayı Visual Studio. DirectX tabanlı oyun veya uygulamanıza gölgelendiriciler kullanabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: cbf23b1e57e2677fba142b1711b74437239e2f63c24b1209b2b832e9aa35c81c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239486"
---
# <a name="work-with-shaders"></a>Gölgelendiricilerle çalışma

Grafik tabanlı Gölgelendirici Tasarımcısı'Visual Studio özel gölgelendirici etkileri tasarlamak için kullanabilirsiniz. DirectX tabanlı oyun veya uygulamanıza bu gölgelendiricileri kullanabilirsiniz.

## <a name="shaders"></a>Gölgelendiriciler

*Gölgelendirici,* köşe dönüştürmeleri veya piksel renklendirme gibi grafik hesaplamaları gerçekleştiren ve genellikle CPU yerine grafik işlem biriminde (GPU) çalışan bir bilgisayar programıdır. Geleneksel, sabit işlevli grafik işlem hattının çoğu aşaması artık gölgelendirici programları tarafından gerçekleştirilene kadar, bunları kullanarak uygulamanıza özgü bir işlem hattı oluşturabilirsiniz.

En yaygın gölgelendirici türleri, köşe başına hesaplamalar gerçekleştiren ve programlandırılamaz grafik donanımlarında sabit işlev dönüştürme ve aydınlatma devresini, piksel rengini belirleyen piksel başına hesaplamalar gerçekleştiren ve programlandırılamaz grafik donanımlarında sabit işlev renk birleyici devresini alan piksel başına hesaplamalar gerçekleştiren piksel gölgelendiricileridir.  Modern grafik donanımı; gölge gölgelendiricileri,etki alanı gölgelendiricileri  *ve* grafik hesaplamaları için  geometri gölgelendiricileri ve grafik olmayan hesaplamalar için işlem gölgelendiricileri gibi daha da fazla gölgelendirici türü mümkün hale geldi. Bu aşamaların hiçbiri programlanabilir olmayan grafik donanımlarında bile kullanılamaz. Gölgelendiriciler başlangıçta veri paralel (SIMD) ve grafik merkezli (nokta ürünü) yönergelerini kullanan derlemeye benzer bir dil kullanılarak oluşturulmuş. Artık gölgelendiriciler genellikle HLSL (Üst Düzey Gölgelendirici Dili) gibi üst düzey C'ye benzer diller kullanılarak oluşturulur.

Kod girmek ve derlemek yerine piksel gölgelendiricilerini etkileşimli olarak oluşturmak için Gölgelendirici Tasarımcısı'nın kullanabilirsiniz. Gölgelendirici Tasarımcısı'nda gölgelendirici, veri ve işlemleri temsil eden bir dizi düğüm ve gölgelendirici aracılığıyla veri değerlerinin akışını ve ara sonuçları temsil eden düğümler arasındaki bağlantılar ile tanımlanır. Gölgelendirici Tasarımcısı'nda bu yaklaşımı ve gerçek zamanlı önizlemeyi kullanarak, gölgelendiricinin yürütülmesini daha kolay görselleştirebilir ve denemeler aracılığıyla ilginç gölgelendirici çeşitlemelerini "keşfedebilirsiniz".

## <a name="dgsl-documents"></a>DGSL belgeleri

Gölgelendirici Tasarımcısı gölgelendiricileri, Directed Graph Biçimlendirme Dili'ne (DGML) dayalı bir XML biçimi olan Yönlendiren Graph Gölgelendirici Dili (DGSL) biçiminde kaydeder. DGSL gölgelendiricilerini Doğrudan Model Düzenleyicisi'nde 3D modellere uygulayabilirsiniz. Ancak, uygulamanıza bir DGSL gölgelendiricisi kullanamadan önce, bunu DirectX'in anlayacaktır bir biçime (örneğin, HLSL) dışarı aktarmanız gerekir.

DGSL DGML ile uyumlu olduğundan DGSL gölgelendiricilerinizi analiz etmek için DGML belgelerini analiz etmek üzere tasarlanmış araçları kullanabilirsiniz. DGML hakkında daha fazla bilgi için [bkz. Directed Graph Biçimlendirme Dili (DGML) anlama.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Gölgelendirici Tasarımcısı](../designers/shader-designer.md)|Gölgelendiriciler ile çalışmak için Visual Studio Gölgelendirici Tasarımcısı'nın nasıl kullanacağız?|
|[Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)|Grafik etkileri elde etmek için kullanabileceğiniz Gölgelendirici Tasarımcısı düğümlerinin türleri ele almaktadır.|
|[Gölgelendirici Tasarımcısı örnekleri](../designers/how-to-create-a-basic-color-shader.md)|Sık kullanılan grafik etkilerini elde etmek için Gölgelendirici Tasarımcısı'nın nasıl kullanıLllarını gösteren konulara bağlantılar sağlar.|
