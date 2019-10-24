---
title: BC doku sıkıştırma varyantı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5faf19632d746105deed3a36af6943627594175
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736157"
---
# <a name="bc-texture-compression-variant"></a>BC Doku Sıkıştırma Çeşidi
B8G8R8X8, B8G8R8A8 veya R8G8B8A8 çeşitlemesi olan bir piksel biçimi olan dokuların blok sıkıştırmasını sunar.

## <a name="interpretation"></a>Korunur
 BC1, BC2 ve BC3 gibi blok tabanlı sıkıştırma biçimleri, sıkıştırılmamış görüntü biçimlerinden önemli ölçüde daha az bellek kaplar ve bu nedenle önemli ölçüde daha az bellek bant genişliği tüketir. Piksel başına 32 bit kullanan sıkıştırılmamış bir biçime kıyasla, BC1 (eski adıyla DXT1) 8:1 Compression ve BC3 (eski adıyla, daha önce DXT5 olarak bilinirdi) 4:1. BC1 ve BC3 arasındaki fark BC1 bir alfa kanalını desteklemekte olsa da, BC3 blok ile sıkıştırılmış bir alfa kanalını destekler. Yüksek sıkıştırma oranlarına rağmen, tipik dokuların görüntü kalitesinde yalnızca küçük bir azalma vardır. Bununla birlikte, belirli dokuların (örneğin, küçük bir alanda önemli renk çeşitlemelerine sahip olanlar) sıkıştırılması, kabul edilemez sonuçlara neden olabilir.

 Dokularınız blok tabanlı sıkıştırma için uygun ise ve kusursuz renge uygunluk gerekmiyorsa, bellek kullanımını azaltmak ve daha az bant genişliği kullanmak için blok ile sıkıştırılmış bir biçim kullanmayı düşünün.

## <a name="remarks"></a>Açıklamalar
 Bir kaynak dokusu oluşturan `ID3DDevice::CreateTexture2D` her çağrıda blok tabanlı bir sıkıştırma biçimi kullanarak dokuları sıkıştırın. Özellikle, dokular şu durumlarda sıkıştırılır:

- @No__t_1 geçirilen `D3D11_TEXTURE2D_DESC` nesne, değişmeyen bir gölgelendirici kaynağını açıklar; Yani:

  - BindFlags üyesinin yalnızca D3D11_BIND_SHADER_RESOURCE bayrağı kümesi vardır.

  - Kullanım üyesi D3D11_USAGE_DEFAULT ya da D3D11_USAGE_IMMUTABLE olarak ayarlanır.

  - CPUAccessFlags üyesi 0 olarak ayarlanır (CPU erişimi yok).

  - SamplerDesc üyesinin Count üyesi 1 olarak ayarlanmış (çok örnekli bir kenar yumuşatma (MSAA)).

- İlk veriler `CreateTexture2D` çağrısına sağlanır.

  Desteklenen kaynak biçimleri ve blok sıkıştırılmış biçimleri aşağıda verilmiştir.

|Özgün biçim (başlangıç)|Sıkıştırılmış biçim (için)|
|------------------------------|------------------------------|
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (eski adıyla DXT1)|
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (eski adıyla DXT5)|
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|

 Dokuınızın listede bulunmayan bir biçimi varsa doku değiştirilmez.

## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar
 Bazen B8G8R8A8 veya R8G8B8A8 görüntü biçimlerinin bir çeşitlemesi ile oluşturulan dokular, gerçekte alfa kanalını kullanmaz, ancak değişkenin kullanılıp kullanılmadığını bilmeleri için bir yol yoktur. Alfa kanalının kullanıldığı durumda, değişken her zaman bu biçimleri daha az etkin BC3 biçimine kodluyor. Bu değişkenle, değişkenin daha verimli BC1 biçimini kullanabilmesi için alfa kanalını kullanmadığınız durumlarda B8G8R8X8 görüntü biçiminin bir varyasyonunu kullanarak, uygulamanızın olası işleme performansını daha iyi anlamanıza yardımcı olabilirsiniz Grafik Çerçeve Çözümlemesi.

## <a name="example"></a>Örnek
 Bu değişken bloğu-`CreateTexture2D` çağrısından önce, çalışma zamanında dokuları sıkıştırır. Sıkıştırılmamış dokular daha fazla disk alanı tükettiğinden ve blok tabanlı sıkıştırma için önemli bir değer gerektirdiğinden ek adım uygulamanızdaki yükleme sürelerini önemli ölçüde artırabildiğinden, üretim kodu için bu yaklaşıma önerilir Kodlanacak kaynakları hesaplama. Bunun yerine, yapı işlem hattınızın bir parçası olan bir görüntü Düzenleyicisi veya görüntü işlemcisi kullanarak dokularınızı çevrimdışına sıkıştırmanız önerilir. Bu yaklaşımlar, disk alanı gereksinimlerini azaltır, uygulamanızdaki çalışma zamanı ek yükünü ortadan kaldırır ve en iyi görüntü kalitesini sürdürebilmeniz için daha fazla işleme süresine sahiptir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yarı/Çeyrek Doku Boyutları Çeşidi](half-quarter-texture-dimensions-variant.md)