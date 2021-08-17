---
title: Oyunlar ve uygulamalar için 3B varlıklarla çalışma
description: DirectX tabanlı oyunlar ve uygulamalar için 3b modeller, dokular ve gölgelendiriciler oluşturmak veya değiştirmek üzere kullanabileceğiniz Visual Studio araçları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 1f4332e8eefb4c1d8c2ea5ce8d1b25eab840fcdd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073610"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Oyunlar ve uygulamalar için 3B varlıklarla çalışma

bu makalede, DirectX tabanlı oyunlar ve uygulamalar için 3b modeller, dokular ve gölgelendiriciler oluşturmak veya değiştirmek üzere kullanabileceğiniz Visual Studio araçları açıklanmaktadır.

## <a name="directx-app-development-in-visual-studio"></a>Visual Studio 'de DirectX uygulama geliştirme

DirectX uygulaması genellikle programlama mantığını, DirectX API 'sini ve yüksek düzeyde gölgeleme dili (HLSL) programlarını zengin ve etkileşimli bir multimedya deneyimi sunmak için ses ve 3B görsel varlıklarla birlikte birleştirir. Visual Studio, ıde 'yi başka bir araç kullanmak için uygulamadan çıkmadan görüntüler, dokular, 3b modeller ve gölgelendiriciler ile çalışmak için kullanabileceğiniz araçlar içerir. Visual Studio araçları, üretim için uygun varlıkları komisyondan önce kodu test etmek için kullanabileceğiniz, ve uygulamanızda hata ayıklarken üretime uygun varlıkları inceleme ve değiştirme amacıyla kullanabileceğiniz *yer tutucu* varlıklar oluşturmaya oldukça uygundur.

İşte Visual Studio ' de çalışabilmeniz için kullanabileceğiniz varlıkların türleri hakkında daha fazla bilgi.

### <a name="images-and-textures"></a>Görüntüler ve dokular

Görüntüler ve dokular, Oyunlar ve uygulamalar için renk ve görsel ayrıntı sağlar. 3B grafiklerde, dokular farklı kullanımları desteklemek için çeşitli biçimlerde, türlere ve geometrileri gelir. Örneğin, normal haritalar 3B modellerin daha ayrıntılı ışıklandırma için piksel başına yüzey normaller sağlar ve küp haritaları, gök kutulama, yansıma ve küresel doku eşleme gibi kullanımlar için tüm yönlerde doku sağlar. Dokular, farklı ayrıntı düzeylerinde verimli işlemeyi desteklemek için mı haritaları sağlayabilir ve farklı renk kanallarını ve renk sıralamayı destekleyebilir. Dokular, daha az ayrılmış grafik belleği kaplayan ve GPU erişim dokularının daha verimli bir şekilde yardım eden çeşitli sıkıştırılmış biçimlerde depolanabilir.

birçok ortak tür ve biçimdeki görüntülerle ve dokularla çalışmak için Visual Studio görüntü düzenleyicisini kullanabilirsiniz.

### <a name="3d-models"></a>3B Modeller

3B modeller, Oyunlar ve uygulamalarda boşluk ve şekil oluşturur. En düşük düzeyde, modeller, *köşe* olarak bilinen ve modelin şeklini temsil eden çizgileri ya da üçgenleri tanımlamak üzere verileri dizinleyen 3B alanda noktaların konumunu kodlayarak tanımlar. Ek veriler, bu köşelerle ilişkilendirilebilir (örneğin, renk bilgileri, normal vektörler veya uygulamaya özel öznitelikler). Her model, nesne genelinde öznitelikler de tanımlayabilir — Örneğin, nesnenin yüzeyinin görünümünü hesaplamak için hangi gölgelendirici kullanılıyor, ya da buna uygulanan doku.

birkaç ortak biçimdeki 3b modellerle çalışmak için Visual Studio Model düzenleyicisini kullanabilirsiniz.

### <a name="shaders"></a>Gölgelendiriciler

Gölgelendiriciler, grafik işleme birimi (GPU) üzerinde çalışan küçük, etki alanına özgü programlardır. Gölgelendiriciler 3B modellerin ekran şekillerine nasıl dönüştürüleceğini ve bu şekillerdeki her pikselin nasıl renklendirileceğini belirlenir. Bir gölgelendirici oluşturup oyununuzda veya uygulamanızdaki bir nesneye uygulayarak nesneye benzersiz bir görünüm verebilirsiniz.

hlsl programlamayı bilmeden özel görsel etkiler oluşturmak için grafik tabanlı gölgelendirici tasarım aracı olan Visual Studio gölgelendirici tasarımcısını kullanabilirsiniz.

> [!NOTE]
> DirectX programlama ile başlama hakkında daha fazla bilgi için bkz. [DirectX](/windows/win32/directx). DirectX tabanlı bir uygulamada hata ayıklama hakkında daha fazla bilgi için bkz. [Grafik Tanılama (DirectX grafik hatalarını ayıklama)](../debugger/graphics/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>DirectX sürümü uyumluluğu

Visual Studio, 2b ve 3b varlıkları işlemek için DirectX kullanır. DirectX 11 oluşturucuyu veya Windows gelişmiş tarama platformu (WARP) yazılım oluşturucuyu seçebilirsiniz. DirectX 11 Oluşturucu, DirectX 11 ve DirectX 10 GPU 'Larda yüksek performanslı, donanım hızlandırmalı işleme sağlar. WARP işleyicisi, varlıklarınızın çok çeşitli bilgisayarlarla çalıştığından emin olmanıza yardımcı olur. Bu, modern grafik donanımı ve tümleşik grafik donanımına sahip olmayan bilgisayarlar dahil olmak üzere, bu bilgisayarlara sahip olmayan bilgisayarları içerir. WARP hakkında daha fazla bilgi için bkz. [gelişmiş tarama platformu (warp) kılavuzu Windows](/windows/win32/direct3darticles/directx-warp).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Dokularla ve görüntülerle çalışma](../designers/working-with-textures-and-images.md)|görüntüleri ve dokuları ile çalışmak için Visual Studio kullanmayı açıklar.|
|[3D modellerle çalışma](../designers/working-with-3-d-models.md)|3b modellerle çalışmak için Visual Studio kullanmayı açıklar.|
|[Gölgelendiricilerle çalışma](../designers/working-with-shaders.md)|özel gölgelendirici efektlerini oluşturmak ve değiştirmek için Visual Studio gölgelendirici tasarımcısının nasıl kullanılacağını açıklar.|
|[Oyununuzda veya uygulamanızda 3B varlıkları kullanma](../designers/using-3-d-assets-in-your-game-or-app.md)|Oyununuzda veya uygulamanızda görüntü düzenleyicisini, model düzenleyicisini veya gölgelendirici tasarımcısını kullanarak oluşturduğunuz varlıkların nasıl kullanılacağını açıklar.|
