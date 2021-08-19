---
title: 16bpp İşleme Hedef Biçimi Varyantı | Microsoft Docs
description: Piksel biçimini tüm işleme hedefleri ve geri arabellekleri için DXGI_FORMAT_B5G6R5_UNORM olarak ayarerek piksel başına 16 bit (bpp) işleme hedef biçimi çeşidini uygulama.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a1713dba828af71b1a6a23cc7de0f46fd28bab70
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154323"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bpp İşleme Hedefi Biçim Çeşidi
Tüm işleme hedefleri ve DXGI_FORMAT_B5G6R5_UNORM arabellekleri için piksel biçimini farklı olacak şekilde ayarlar.

## <a name="interpretation"></a>Yorum
 İşleme hedefi veya geri arabelleği genellikle 32 bpp (piksel başına 32 bit) biçiminde (örneğin, B8G8R8A8_UNORM. 32 bpp biçimleri büyük miktarda bellek bant genişliği tüketir. B5G6R5_UNORM biçimi 32 bpp biçimlerinin yarısı boyutta olan 16 bpp biçiminde olduğundan, bunu kullanmak bellek bant genişliği üzerindeki baskıyı hafifletmeye yardımcı olabilir, ancak daha düşük renk uygunluğu maliyetiyle.

 Bu değişken büyük bir performans kazancı gösteriyorsa, büyük olasılıkla uygulamanın çok fazla bellek bant genişliği tükettiğine işaret ediyordur. Özellikle profili yapılan çerçevede önemli miktarda fazla çizim veya alfa karıştırma olduğunda önemli bir performans geliştirmesi elde etmek için.

16 bpp işleme hedefi biçimi, uygulamanıza aşağıdaki koşullar olduğunda bellek bantını kullanımla birlikte azaltabilirsiniz:
- Yüksek uygunlukta renk yeniden üretilmesi gerektirmez.
- Alfa kanalı gerektirmez.
- Genellikle düzgün gradyanlara sahip değildir (yapıtları düşük renk uygunluk altında bantlama konusunda duyarlıdır).

Bellek bant genişliğini azaltmaya yardımcı olacak diğer stratejiler şunlardır:
- Fazla çizim veya alfa karıştırma miktarını azaltma.
- Çerçeve arabelleğinin boyutlarını azaltma.
- Doku kaynaklarının boyutlarını azaltma.
- Doku kaynaklarının sıkıştırmasını azaltma.

Her zamanki gibi, bu iyileştirmelerden herhangi biri ile birlikte gelen görüntü kalitesiyle ilgili bazı takasları göz önünde bulundurabilirsiniz.

Değiştirme zincirinin bir parçası olan uygulamalar, 16 bpp'yi desteklemez bir geri arabellek biçimine (DXGI_FORMAT_B5G6R5_UNORM) sahiptir. Bu takas zincirleri veya kullanılarak `D3D11CreateDeviceAndSwapChain` `IDXGIFactory::CreateSwapChain` oluşturulur. Bu sınırlamaya bir çözüm olarak aşağıdaki adımları uygulayın:
1. kullanarak B5G6R5_UNORM biçimi işleme hedefi oluşturun `CreateTexture2D` ve bu hedefe işlenin.
2. İşleme hedefini kaynak doku olarak işleme hedefiyle tam ekran bir dörtlü çizerek değiştirme zinciri arka kasasına kopyalayın.
3. Değiştirme zinciriniz üzerinde Present çağrısı.

   Bu strateji, işleme hedefini takas zinciri arka kasasına kopyalayıp tüketilenden daha fazla bant genişliği tasarrufu sağlarsa işleme performansı artırıldı.

   Kutucuk işleme tekniklerini kullanan GPU mimarileri, 16 bpp çerçeve arabelleği biçimi kullanarak önemli performans avantajlarına sahip olabilir. Bu geliştirmenin nedeni, çerçeve arabelleğinin büyük bir kısmının her kutucuğun yerel çerçeve arabelleği önbelleğine sığma olmasıdır. Kutucuklu işleme mimarileri bazen mobil cihazlarda ve tablet bilgisayarlarda GPU'larda bulunur; bu özelin dışında nadiren görünürler.

## <a name="remarks"></a>Açıklamalar
 İşleme hedefi biçimi, işleme DXGI_FORMAT_B5G6R5_UNORM her çağrısında `ID3D11Device::CreateTexture2D` hedefine sıfırlanır. Özellikle, pDesc'de geçirilen D3D11_TEXTURE2D_DESC işleme hedefi açık olduğunda biçim geçersiz kılınır; Yani:

- BindFlags üyesi, D3D11_BIND_REDNER_TARGET ayarlanmıştır.

- BindFlags üyesi, D3D11_BIND_DEPTH_STENCIL temizli.

- Kullanım üyesi, D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar
 B5G6R5 biçimi bir alfa kanalına sahip değildir, alfa içeriği bu değişken tarafından korunmaz. Uygulama işlemesi için işleme hedefinize alfa kanalı gerekirse B5G6R5 biçimine geçebilirsiniz.

## <a name="example"></a>Örnek
 **16 bpp İşleme Hedefi Biçimi** çeşidi, aşağıdaki gibi kod kullanılarak oluşturulan işleme `CreateTexture2D` hedefleri için yeniden oluşturulabilir:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
