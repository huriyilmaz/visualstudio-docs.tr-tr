---
title: Oyunlar ve uygulamalar için 3B varlıklarla çalışma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9cc4f8038906de89afd86fd666fbb011e974362d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298094"
---
# <a name="working-with-3-d-assets-for-games-and-apps"></a>Oyunlar ve Uygulamalar için 3B Varlıklarla Çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede, DirectX tabanlı oyunlar ve uygulamalar için 3-b modeller, dokular ve gölgelendiriciler oluşturmak veya değiştirmek üzere kullanabileceğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] araçları açıklanmaktadır.

## <a name="directx-app-development-in-visual-studio"></a>Visual Studio 'da DirectX uygulama geliştirme
 DirectX uygulaması genellikle programlama mantığını, DirectX API 'sini ve yüksek düzeyde gölgeleme dili (HLSL) programlarını, zengin ve etkileşimli bir multimedya deneyimi sunmak için ses ve 3-D görsel varlıklarla birlikte birleştirir.[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , IDE 'yi başka bir araç kullanmak için uygulamadan çıkmadan görüntüler ve dokular, 3-b modelleri ve gölgelendiriciler ile çalışmak için kullanabileceğiniz araçlar içerir. Visual Studio Araçları özellikle, üretime uygun varlıkları komisyondan önce kodu test etmek için kullanabileceğiniz ve uygulamanızda hata ayıklarken üretime uygun varlıkları İnceleme ve değiştirme amacıyla kullanabileceğiniz *yer tutucu* varlıklar oluşturmaya uygundur.

 İşte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]' de kullanabileceğiniz varlıkların türleri hakkında daha fazla bilgi.

### <a name="images-and-textures"></a>Görüntüler ve dokular
 Görüntüler ve dokular, Oyunlar ve uygulamalar için renk ve görsel ayrıntı sağlar. 3-b grafiklerde, dokular farklı kullanımları desteklemek için çeşitli biçimlerde, türlerde ve geometrileri gelir. Örneğin, normal haritalar, 3-b modellerin daha ayrıntılı ışıklandırma için piksel başına yüzey normaller sağlar ve küp haritaları, çatkutulama, yansıma ve küresel doku eşleme gibi kullanımlar için tüm yönlerde doku sağlar. Dokular, farklı ayrıntı düzeylerinde verimli işlemeyi desteklemek için MIP haritaları sağlayabilir ve farklı renk kanallarını ve renk sırasını destekleyebilir. Dokular, daha az ayrılmış grafik belleği kaplayan ve GPU erişim dokularının daha verimli bir şekilde yardım eden çeşitli sıkıştırılmış biçimlerde depolanabilir.

 Birçok ortak tür ve biçimdeki görüntülerle ve dokularla çalışmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] görüntü düzenleyicisini kullanabilirsiniz.

### <a name="3-d-models"></a>3B modeller
 3-b modeller, Oyunlar ve uygulamalarda boşluk ve şekil oluşturur. En düşük düzeyde, modeller, *köşeler olarak bilinen*ve modelin şeklini temsil eden çizgileri ya da üçgenleri tanımlamak üzere verileri dizinleyen 3-b Space içindeki noktaların konumunu kodlayıp. Ek veriler, bu köşelerle ilişkilendirilebilir (örneğin, renk bilgileri, normal vektörler veya uygulamaya özel öznitelikler). Her model, nesne genelinde öznitelikler de tanımlayabilir — Örneğin, nesnenin yüzeyinin görünümünü hesaplamak için hangi gölgelendirici kullanılıyor, ya da buna uygulanan doku.

 Birkaç ortak biçimdeki 3-b modelleriyle çalışmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] model düzenleyicisini kullanabilirsiniz.

### <a name="shaders"></a>Gölgelendiriciler
 Gölgelendiriciler, grafik işleme birimi (GPU) üzerinde çalışan küçük, etki alanına özgü programlardır. Gölgelendiriciler 3-b modellerin ekran şekillerine nasıl dönüştürüleceğini ve bu şekillerdeki her pikselin nasıl renklendirileceğini belirlenir. Bir gölgelendirici oluşturup oyununuzda veya uygulamanızdaki bir nesneye uygulayarak nesneye benzersiz bir görünüm verebilirsiniz.

 HLSL programlamayı bilmeden özel görsel etkiler oluşturmak için grafik tabanlı gölgelendirici tasarım aracı olan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gölgelendirici tasarımcısını kullanabilirsiniz.

> [!NOTE]
> DirectX programlama ile başlama hakkında daha fazla bilgi için bkz. [DirectX](https://go.microsoft.com/fwlink/p/?LinkId=224633). DirectX tabanlı bir uygulamada hata ayıklama hakkında daha fazla bilgi için bkz. [Grafik Tanılama (DirectX grafik hatalarını ayıklama)](../debugger/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>DirectX sürümü uyumluluğu
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 2-b ve 3-b varlıklarını işlemek için DirectX kullanır. DirectX 11 oluşturucuyu ya da Windows Gelişmiş Tarama Platformu (WARP) yazılım oluşturucuyu seçebilirsiniz. DirectX 11 Oluşturucu, DirectX 11 ve DirectX 10 GPU 'Larda yüksek performanslı, donanım hızlandırmalı işleme sağlar. WARP işleyicisi, varlıklarınızın çok çeşitli bilgisayarlarla çalıştığından emin olmanıza yardımcı olur. Bu, modern grafik donanımı ve tümleşik grafik donanımına sahip olmayan bilgisayarlar dahil olmak üzere, bu bilgisayarlara sahip olmayan bilgisayarları içerir. WARP hakkında daha fazla bilgi için bkz. [Windows Gelişmiş Tarama Platformu (warp) Kılavuzu](https://go.microsoft.com/fwlink/p/?LinkId=224634).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Dokularla ve Görüntülerle Çalışma](../designers/working-with-textures-and-images.md)|Görüntüleri ve dokuları ile çalışmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanmayı açıklar.|
|[3B Modelleriyle Çalışma](../designers/working-with-3-d-models.md)|3-b modelleriyle çalışmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanmayı açıklar.|
|[Gölgelendiricilerle Çalışma](../designers/working-with-shaders.md)|Özel gölgelendirici efektlerini oluşturmak ve değiştirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Gölgelendirici Tasarımcısının nasıl kullanılacağını açıklar.|
|[Oyunlarda veya Uygulamalarda 3B Varlıklar Kullanma](../designers/using-3-d-assets-in-your-game-or-app.md)|Oyununuzda veya uygulamanızda görüntü düzenleyicisini, model düzenleyicisini veya gölgelendirici tasarımcısını kullanarak oluşturduğunuz varlıkların nasıl kullanılacağını açıklar.|
