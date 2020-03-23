---
title: Oyunlar ve Uygulamalar için 3D Varlıklarla Çalışma
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa9fc04df3e817730492353e54d74c1e46c3775e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589805"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Oyunlar ve uygulamalar için 3B varlıklarla çalışma

Bu makalede, DirectX tabanlı oyunlar ve uygulamalar için 3B modeller, dokular ve gölgeliler oluşturmak veya değiştirmek için kullanabileceğiniz Visual Studio araçları açıklanmaktadır.

## <a name="directx-app-development-in-visual-studio"></a>Visual Studio'da DirectX uygulama geliştirme

DirectX uygulaması genellikle programlama mantığını, DirectX API'sını ve Yüksek Düzeygölgeleme Dili (HLSL) programlarını, zengin, etkileşimli bir multimedya deneyimi sunmak için ses ve 3B görsel varlıklarla birleştirir. Visual Studio, ide'den başka bir araç kullanmak için ayrılmadan görüntüler ve dokularla, 3B modellerle ve gölgelilerle çalışmak için kullanabileceğiniz araçlar içerir. Visual Studio araçları özellikle, üretime hazır varlıkları devreye almadan önce kodu test etmek veya prototip oluşturmak için kullanabileceğiniz *yer tutucu* varlıkları oluşturmak ve uygulamanızı hata ayıklarken üretime hazır varlıkları incelemek ve değiştirmek için uygundur.

Visual Studio'da çalışabileceğiniz varlık türleri hakkında daha fazla bilgi aşağıda verebilirsiniz.

### <a name="images-and-textures"></a>Görüntüler ve dokular

Görüntüler ve dokular oyunlarda ve uygulamalarda renk ve görsel ayrıntılar sağlar. 3B grafiklerde dokular, farklı kullanımları desteklemek için çeşitli biçimlerde, türlerde ve geometrilerde gelir. Örneğin, normal haritalar 3B modellerin daha ayrıntılı aydınlatması için piksel başına yüzey normalleri sağlarken, küp eşlemler gökyüzü kutulama, yansımalar ve küresel doku eşleme gibi kullanımlar için her yönde doku sağlar. Dokular, farklı ayrıntı düzeylerinde verimli işlemeyi desteklemek için mipmaps sağlayabilir ve farklı renk kanallarını ve renk sıralamalarını destekleyebilir. Dokular, daha az özel grafik belleği kaplayan ve GPU'ların dokulara daha verimli erişmelerine yardımcı olan çeşitli sıkıştırılmış biçimlerde depolanabilir.

Birçok yaygın tür ve biçimde görüntüler ve dokular ile çalışmak için Visual Studio Image Editor kullanabilirsiniz.

### <a name="3d-models"></a>3B Modeller

3D modeller oyunlarda ve uygulamalarda alan ve şekil oluşturur. Modeller, modelin şeklini temsil eden çizgileri veya üçgenleri tanımlamak için verileri dizine eklemeyle birlikte, *tepe noktaları*olarak bilinen 3B alandaki noktaların konumunu en aza kodlar. Ek veriler bu temel verilerle ilişkilendirilebilir(örneğin, renk bilgileri, normal vektörler veya uygulamaya özgü öznitelikler). Her model nesne genelinde öznitelikleri de tanımlayabilir(örneğin, nesnenin yüzeyinin görünümünü hesaplamak için hangi gölgeli kullanılır veya hangi doku uygulanır.

Çeşitli ortak biçimlerde 3B modeller ile çalışmak için Visual Studio Model Editor kullanabilirsiniz.

### <a name="shaders"></a>Gölgelendiriciler

Gölgeli küçük, etki alanına özgü programlardır ve grafik işleme biriminde (GPU) çalışır. Gölgelendirciler, 3B modellerin ekrandaki şekillere nasıl dönüştürüldüğünü ve bu şekillerdeki her pikselin nasıl renkli olduğunu belirler. Bir gölgeleyici oluşturarak ve bunu oyununuzdaki veya uygulamanızdaki bir nesneye uygulayarak nesneye benzersiz bir görünüm verebilirsiniz.

HLSL programlamabilmeden özel görsel efektler oluşturmak için grafik tabanlı bir shader tasarım aracı olan Visual Studio Shader Designer'ı kullanabilirsiniz.

> [!NOTE]
> DirectX programlama ile nasıl başlayacağınız hakkında daha fazla bilgi için [DirectX'e](/windows/win32/directx)bakın. DirectX tabanlı bir uygulamanın hata ayıklanması hakkında daha fazla bilgi için [Grafik tanılama (DirectX grafiklerini hata ayıklama)](../debugger/graphics/visual-studio-graphics-diagnostics.md)bölümüne bakın.

## <a name="directx-version-compatibility"></a>DirectX sürümü uyumluluğu

Visual Studio, 2B ve 3B varlıkları işlemek için DirectX'i kullanır. DirectX 11 görüntüleyicisini veya Windows Advanced Rasterization Platform (WARP) yazılım işleyicisini seçebilirsiniz. DirectX 11 renderer, DirectX 11 ve DirectX 10 GPU'larında yüksek performanslı, donanım hızlandırmalı görüntüleme sağlar. WARP görüntüleyici, varlıklarınızın çok çeşitli bilgisayarlarla çalışmasını sağlamaya yardımcı olur — buna modern grafik donanımı olmayan bilgisayarlar ve tümleşik grafik donanımına sahip bilgisayarlar dahildir. WARP hakkında daha fazla bilgi için [Windows Advanced Rasterization Platform (WARP) kılavuzuna](/windows/win32/direct3darticles/directx-warp)bakın.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Dokular ve görüntülerle çalışma](../designers/working-with-textures-and-images.md)|Görseller ve dokularla çalışmak için Visual Studio'nun nasıl kullanılacağını açıklar.|
|[3B modellerle çalışma](../designers/working-with-3-d-models.md)|Visual Studio'nun 3B modellerle çalışmak için nasıl kullanılacağını açıklar.|
|[Gölgeleyicilerle çalışma](../designers/working-with-shaders.md)|Özel gölgeli efektler oluşturmak ve değiştirmek için Visual Studio Shader Designer'ın nasıl kullanılacağını açıklar.|
|[Oyununuzda veya uygulamanızda 3B varlıkları kullanma](../designers/using-3-d-assets-in-your-game-or-app.md)|Oyununuzda veya uygulamanızda Görüntü Düzenleyicisi, Model Düzenleyicisi veya Shader Designer'ı kullanarak oluşturduğunuz varlıkların nasıl kullanılacağını açıklar.|
