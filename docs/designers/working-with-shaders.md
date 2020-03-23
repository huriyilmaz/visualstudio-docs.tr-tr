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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589779"
---
# <a name="work-with-shaders"></a>Gölgelendiricilerle çalışma

Özel gölgeefektleri tasarlamak için Visual Studio'daki grafik tabanlı Shader Designer'ı kullanabilirsiniz. Bu gölgelileri DirectX tabanlı oyununuzda veya uygulamanızda kullanabilirsiniz.

## <a name="shaders"></a>Gölgelendiriciler

*Gölgelendirme,* grafik hesaplamaları gerçekleştiren (örneğin, tepe noktası dönüşümleri veya piksel boyama) gerçekleştiren ve genellikle CPU yerine grafik işleme birimi (GPU) üzerinde çalışan bir bilgisayar programıdır. Geleneksel, sabit işlevli grafik ardışık ardışık yapının çoğu aşaması artık gölgeli programlar tarafından gerçekleştirildiği için, bunları uygulamanızın gereksinimlerine özel bir ardışık yol hattı oluşturmak için kullanabilirsiniz.

Gölgeli lerin en yaygın türleri, vertex başına hesaplamalar gerçekleştiren ve programlanamayan grafik donanımındaki sabit işlevli dönüşüm ve aydınlatma devrelerinin yerini alan *vertex gölgeleyicilerdir*ve piksel başına bir pikselin rengini belirleyen ve programlanamayan grafik donanımındaki sabit işlevli renk birleştirici devresini değiştiren piksel başına hesaplamalar yapan *piksel gölgeleyicilerdir.* Modern grafik*donanımı, gövde gölgeleyicileri,* etki alanı *gölgeleyicileri*ve grafik hesaplamaları için *geometri shaders* ve grafik dışı hesaplamalar için *işlem gölgeleyiciler* gibi daha da fazla gölgeli türü mümkün kılmıştır. Bu aşamaların hiçbiri programlanabilir olmayan grafik donanımı bile mevcut değildir. Gölgelendirler başlangıçta veri paraleli (SIMD) ve grafik merkezli (nokta ürünü) yönergeleri sağlayan montaj benzeri bir dil kullanılarak oluşturulmuştur. Şimdi, gölgeli genellikle HLSL (High Level Shader Language) gibi üst düzey, C benzeri diller kullanılarak oluşturulur.

Kod girerek ve derleyerek yerine etkileşimli olarak piksel gölgeleyicileri oluşturmak için Shader Designer'ı kullanabilirsiniz. Gölgeli Tasarımcısı'nda, gölgeli veri ve işlemleri temsil eden bir dizi düğüm ve gölgeleyici aracılığıyla veri değerlerinin akışını temsil eden düğümler ile ara sonuçlar arasındaki bağlantılarla tanımlanır. Bu yaklaşımı ve Shader Designer'daki gerçek zamanlı önizlemeyi kullanarak, gölgeleyicinin yürütülmesini daha kolay görselleştirebilir ve deneme yoluyla ilginç gölgeli varyasyonları "keşfedebilirsiniz".

## <a name="dgsl-documents"></a>DGSL belgeleri

Shader Designer, Yönlendirilmiş Grafik İşaretleyici Dili 'ni (DGML) temel alan bir XML biçimi olan Yönlendirilmiş Grafik Shader Dili (DGSL) biçiminde gölgeli leri kaydeder. MODEL Düzenleyicisi'ndeki 3D modellere doğrudan DGSL shaders uygulayabilirsiniz. Ancak, uygulamanızda bir DGSL shader kullanabilmeniz için, uygulamayı DirectX'in anladığı bir biçime (örneğin HLSL) dışa aktarmanız gerekir.

DGSL DGML ile uyumlu olduğundan, DGSL gölgeleme analiz etmek için DGML belgeleri analiz etmek için tasarlanmış araçlar kullanabilirsiniz. DGML hakkında bilgi için [bkz.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Shader Tasarımcısı](../designers/shader-designer.md)|Gölgelilerle çalışmak için Visual Studio Shader Designer'ın nasıl kullanılacağını açıklar.|
|[Gölgeli Tasarımcı düğümleri](../designers/shader-designer-nodes.md)|Grafik efektleri elde etmek için kullanabileceğiniz Shader Designer düğümlerinin türlerini tartışır.|
|[Shader Designer örnekleri](../designers/how-to-create-a-basic-color-shader.md)|Ortak grafik efektleri elde etmek için Shader Designer'ın nasıl kullanılacağını gösteren konulara bağlantılar sağlar.|
