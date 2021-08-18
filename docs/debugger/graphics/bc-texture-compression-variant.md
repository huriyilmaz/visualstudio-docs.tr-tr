---
title: BC Doku Sıkıştırma Varyantı | Microsoft Docs
description: B8G8R8X8, B8G8R8A8 veya R8G8B8A8'in bir varyasyonu olan dokularda blok sıkıştırmaya (BC) izin vermek için BC doku sıkıştırma varyantı kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6723493257ef7df194c0987d60879a3222651b2d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154284"
---
# <a name="bc-texture-compression-variant"></a>BC Doku Sıkıştırma Çeşidi
Piksel biçimi B8G8R8X8, B8G8R8A8 veya R8G8B8A8 olan dokularda blok sıkıştırmayı sağlar.

## <a name="interpretation"></a>Yorum
 BC1, BC2 ve BC3 gibi blok tabanlı sıkıştırma biçimleri sıkıştırılmamış görüntü biçimlerinden çok daha az bellek kaplar ve bu nedenle çok daha az bellek bant genişliği kullanır. Piksel başına 32 bit kullanan sıkıştırılmamış bir biçimle karşılaştırıldığında BC1 (eski adıyla DXT1), 8:1 sıkıştırma ve BC3 (eski adıyla DXT5) 4:1'i elde eder. BC1 ile BC3 arasındaki fark, BC1'in bir alfa kanalını, BC3 ise blok sıkıştırılmış alfa kanalını desteklemesidir. Yüksek sıkıştırma oranlarına rağmen, tipik dokular için görüntü kalitesinde yalnızca küçük bir azalma vardır. Ancak, belirli doku türlerinde blok sıkıştırma (örneğin, küçük bir alanda önemli renk varyasyonu olanlar) kabul edilemez sonuçlara sahip olabilir.

 Dokularınız blok tabanlı sıkıştırma için uygunsa ve mükemmel renk aslına uygun olması gerekmese, bellek kullanımını azaltmak ve daha az bant genişliği kullanmak için blok sıkıştırılmış bir biçim kullanmayı göz önünde bulundurabilirsiniz.

## <a name="remarks"></a>Açıklamalar
 Dokuları, kaynak doku oluşturan her çağrısında blok tabanlı sıkıştırma `ID3DDevice::CreateTexture2D` biçimi kullanarak sıkıştırırsanız. Özellikle dokular şu anda sıkıştırılır:

- geçirilen `D3D11_TEXTURE2D_DESC` nesne `pDesc` değişmeyen bir gölgelendirici kaynağını açıklar; yani:

  - BindFlags üyesinin yalnızca D3D11_BIND_SHADER_RESOURCE ayarlanmıştır.

  - Kullanım üyesi, D3D11_USAGE_DEFAULT veya D3D11_USAGE_IMMUTABLE.

  - CPUAccessFlags üyesi 0 olarak ayarlanır (CPU erişimi yoktur).

  - SamplerDesc üyesinin Sayı üyesi 1 olarak ayarlanmıştır (Çok Örnekli Anti-Aliasing (MSAA) yoktur).

- çağrısına ilk veriler `CreateTexture2D` sağlanır.

  Desteklenen kaynak biçimleri ve bunların blok sıkıştırılmış biçimleri aşağıdaki gibidir.

|Özgün biçim (gelen)|Sıkıştırılmış biçim (için)|
|------------------------------|------------------------------|
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (eski adı DXT1)|
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (eski adı DXT5)|
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|

 Dokun listede yer alan bir biçime sahipse doku değiştirilmez.

## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar
 Bazen B8G8R8A8 veya R8G8B8A8 görüntü biçimlerinin bir varyasyonu ile oluşturulan dokular aslında alfa kanalı kullanmaz, ancak çeşitlemenin kullanıla mı yoksa kullanılma mı olduğunu anlayan bir yol yoktur. Alfa kanalının kullanılma durumunda doğruluğu korumak için değişken her zaman bu biçimleri daha az verimli BC3 biçimine kodlar. Alfa kanalı Grafik Çerçeve Çözümlemesi B8G8R8X8 görüntü biçiminin bir varyasyonu kullanarak, varyantın daha verimli BC1 biçimini kullanamalarını sağlamak için, bu varyantla uygulamanın olası işleme performansını daha iyi anlamanıza yardımcı olabilirsiniz.

## <a name="example"></a>Örnek
 Bu değişken, çalışma zamanında dokuları çağrısının öncesinde `CreateTexture2D` sıkıştırır. Sıkıştırılmamış dokular daha fazla disk alanı tükettiği ve blok tabanlı sıkıştırmanın kodlanması için önemli hesaplama kaynakları gerektirdiği için ek adım uygulamanıza yükleme sürelerini önemli ölçüde artırayabli olduğundan üretim kodu için bu yaklaşıma karşı öneririz. Bunun yerine, derleme işlem hattınıza bir parçası olan görüntü düzenleyicisi veya görüntü işlemcisi kullanarak dokularınızı çevrimdışı olarak sıkıştırmanızı öneririz. Bu yaklaşımlar disk alanı gereksinimlerini azaltır, uygulamanıza çalışma zamanı ek yükünü ortadan kaldırmak ve en iyi görüntü kalitesini koruyabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Yarı/Çeyrek Doku Boyutları Çeşidi](half-quarter-texture-dimensions-variant.md)