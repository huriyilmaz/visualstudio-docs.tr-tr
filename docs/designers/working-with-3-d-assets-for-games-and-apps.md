---
title: Oyunlar ve uygulamalar için 3B varlıklarla çalışma
description: DirectX tabanlı oyunlar ve uygulamalar için 3B modeller, dokular ve gölgelendiriciler oluşturmak veya değiştirmek için kullanabileceğiniz Visual Studio Araçları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 11f031aa3e3767af3132e68f92c492dc7e3fae6f
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134569"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Oyunlar ve uygulamalar için 3B varlıklarla çalışma

Bu makalede, DirectX tabanlı oyunlar ve uygulamalar için 3B modeller, dokular ve gölgelendiriciler oluşturmak veya değiştirmek için kullanabileceğiniz Visual Studio araçları açıklanmaktadır.

## <a name="directx-app-development-in-visual-studio"></a>Visual Studio 'da DirectX uygulama geliştirme

DirectX uygulaması genellikle programlama mantığını, DirectX API 'sini ve yüksek düzeyde gölgeleme dili (HLSL) programlarını zengin ve etkileşimli bir multimedya deneyimi sunmak için ses ve 3B görsel varlıklarla birlikte birleştirir. Visual Studio, IDE 'yi başka bir araç kullanmak için uygulamadan çıkmadan görüntüler, dokular, 3B modeller ve gölgelendiriciler ile çalışmak için kullanabileceğiniz araçlar içerir. Visual Studio Araçları özellikle, üretime uygun varlıkları komisyondan önce kodu test etmek için kullanabileceğiniz ve uygulamanızda hata ayıklarken üretime uygun varlıkları İnceleme ve değiştirme amacıyla kullanabileceğiniz *yer tutucu* varlıklar oluşturmaya uygundur.

Visual Studio 'da çalıştığınız varlık türleri hakkında daha fazla bilgi edinebilirsiniz.

### <a name="images-and-textures"></a>Görüntüler ve dokular

Görüntüler ve dokular, Oyunlar ve uygulamalar için renk ve görsel ayrıntı sağlar. 3B grafiklerde, dokular farklı kullanımları desteklemek için çeşitli biçimlerde, türlere ve geometrileri gelir. Örneğin, normal haritalar 3B modellerin daha ayrıntılı ışıklandırma için piksel başına yüzey normaller sağlar ve küp haritaları, gök kutulama, yansıma ve küresel doku eşleme gibi kullanımlar için tüm yönlerde doku sağlar. Dokular, farklı ayrıntı düzeylerinde verimli işlemeyi desteklemek için mı haritaları sağlayabilir ve farklı renk kanallarını ve renk sıralamayı destekleyebilir. Dokular, daha az ayrılmış grafik belleği kaplayan ve GPU erişim dokularının daha verimli bir şekilde yardım eden çeşitli sıkıştırılmış biçimlerde depolanabilir.

Birçok ortak tür ve biçimdeki görüntülerle ve dokularla çalışmak için Visual Studio görüntü düzenleyicisini kullanabilirsiniz.

### <a name="3d-models"></a>3B Modeller

3B modeller, Oyunlar ve uygulamalarda boşluk ve şekil oluşturur. En düşük düzeyde, modeller, *köşe* olarak bilinen ve modelin şeklini temsil eden çizgileri ya da üçgenleri tanımlamak üzere verileri dizinleyen 3B alanda noktaların konumunu kodlayarak tanımlar. Ek veriler, bu köşelerle ilişkilendirilebilir (örneğin, renk bilgileri, normal vektörler veya uygulamaya özel öznitelikler). Her model, nesne genelinde öznitelikler de tanımlayabilir — Örneğin, nesnenin yüzeyinin görünümünü hesaplamak için hangi gölgelendirici kullanılıyor, ya da buna uygulanan doku.

Visual Studio model düzenleyicisini kullanarak birkaç ortak biçimdeki 3B modellerle çalışabilirsiniz.

### <a name="shaders"></a>Gölgelendiriciler

Gölgelendiriciler, grafik işleme birimi (GPU) üzerinde çalışan küçük, etki alanına özgü programlardır. Gölgelendiriciler 3B modellerin ekran şekillerine nasıl dönüştürüleceğini ve bu şekillerdeki her pikselin nasıl renklendirileceğini belirlenir. Bir gölgelendirici oluşturup oyununuzda veya uygulamanızdaki bir nesneye uygulayarak nesneye benzersiz bir görünüm verebilirsiniz.

Bir grafik tabanlı gölgelendirici tasarım aracı olan Visual Studio gölgelendirici Tasarımcısı ' nı kullanarak, HLSL programlamayı bilmeden özel görsel etkiler oluşturabilirsiniz.

> [!NOTE]
> DirectX programlama ile başlama hakkında daha fazla bilgi için bkz. [DirectX](/windows/win32/directx). DirectX tabanlı bir uygulamada hata ayıklama hakkında daha fazla bilgi için bkz. [Grafik Tanılama (DirectX grafik hatalarını ayıklama)](../debugger/graphics/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>DirectX sürümü uyumluluğu

Visual Studio, 2B ve 3B varlıkları işlemek için DirectX kullanır. DirectX 11 oluşturucuyu ya da Windows Gelişmiş Tarama Platformu (WARP) yazılım oluşturucuyu seçebilirsiniz. DirectX 11 Oluşturucu, DirectX 11 ve DirectX 10 GPU 'Larda yüksek performanslı, donanım hızlandırmalı işleme sağlar. WARP işleyicisi, varlıklarınızın çok çeşitli bilgisayarlarla çalıştığından emin olmanıza yardımcı olur. Bu, modern grafik donanımı ve tümleşik grafik donanımına sahip olmayan bilgisayarlar dahil olmak üzere, bu bilgisayarlara sahip olmayan bilgisayarları içerir. WARP hakkında daha fazla bilgi için bkz. [Windows Gelişmiş Tarama Platformu (warp) Kılavuzu](/windows/win32/direct3darticles/directx-warp).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Dokularla ve görüntülerle çalışma](../designers/working-with-textures-and-images.md)|Görüntüler ve dokularla çalışmak için Visual Studio 'Nun nasıl kullanılacağını açıklar.|
|[3D modellerle çalışma](../designers/working-with-3-d-models.md)|3D modellerle çalışmak için Visual Studio 'Nun nasıl kullanılacağını açıklar.|
|[Gölgelendiricilerle çalışma](../designers/working-with-shaders.md)|Özel gölgelendirici efektlerini oluşturmak ve değiştirmek için Visual Studio gölgelendirici Tasarımcısı 'nın nasıl kullanılacağını açıklar.|
|[Oyununuzda veya uygulamanızda 3B varlıkları kullanma](../designers/using-3-d-assets-in-your-game-or-app.md)|Oyununuzda veya uygulamanızda görüntü düzenleyicisini, model düzenleyicisini veya gölgelendirici tasarımcısını kullanarak oluşturduğunuz varlıkların nasıl kullanılacağını açıklar.|
