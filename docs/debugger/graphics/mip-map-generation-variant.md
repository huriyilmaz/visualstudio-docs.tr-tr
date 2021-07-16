---
title: Mip eşlemesi Oluşturma Varyantı | Microsoft Docs
description: Mip eşlemesi oluşturma büyük performans kazançları gösteriyorsa, mip eşlemelerini etkinleştirmeden dokuları kullanmakta ve doku önbelleğinden en iyi şekilde performans elde etmek mümkün değildir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e17981b819ccc719399a6ed14071615f2deb54a
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232446"
---
# <a name="mip-map-generation-variant"></a>Mip-map Oluşturma Çeşidi
Hedef işleme olmayan dokularda mip eşlemelerini sağlar.

## <a name="interpretation"></a>Yorum
Mip eşlemeleri öncelikle dokuların daha küçük sürümlerini önceden hesaplarak küçültme altındaki dokularda diğer ad yapıtlarını ortadan kaldırmak için kullanılır. Bu ek dokular özgün dokudan yaklaşık yüzde 33 daha fazla GPU belleği tüketse de, yüzey alanının çoğu GPU doku önbelleğine sığar ve içerikleri daha yüksek kullanım elde eder.

3B sahneler için, bellek ek dokuları depolamak için kullanılabilir olduğunda mip eşlemelerini öneririz çünkü bunlar hem işleme performansını hem de görüntü kalitesini artırır.

Bu değişken önemli bir performans kazancı gösteriyorsa, mip eşlemelerini etkinleştirmeden dokuları kullanmakta olduğunu ve bu sayede doku önbelleğinden en iyi şekilde elde olmadığını gösterir.

## <a name="remarks"></a>Açıklamalar
Mip eşlemesi oluşturma, kaynak doku oluşturan `ID3D11Device::CreateTexture2D` her çağrısına zorlar. Özellikle, içinde geçirilen nesne değişmeyen bir gölgelendirici D3D11_TEXTURE2D_DESC açık olduğunda mip eşlemesi oluşturma `pDesc` zorlar; yani:

- BindFlags üyesinin yalnızca D3D11_BIND_SHADER_RESOURCE ayarlanmıştır.

- Kullanım üyesi, D3D11_USAGE_DEFAULT veya D3D11_USAGE_IMMUTABLE.

- CPUAccessFlags üyesi 0 olarak ayarlanır (CPU erişimi yoktur).

- SampleDesc üyesinin Sayı üyesi 1 olarak ayarlanmıştır (Çok Örnekli Anti-Aliasing (MSAA) yoktur).

- MipLevels üyesi 1 olarak ayarlanır (mevcut mip eşlemesi yoktur).

  Uygulama tarafından ilk veriler sağlandıkça, biçim BC1, BC2 veya BC3 değilse doku biçiminin otomatik mip eşlemesi oluşturmasını (D3D11_FORMAT_SUPPORT_MIP_AUTOGEN tarafından belirlendiği şekilde) desteklemesi gerekir; aksi takdirde doku değiştirilmez ve ilk veriler sağlanmalıdır.

  Doku için mip eşlemeleri otomatik olarak oluşturulmuşsa, doku örnekleme sırasında mip zincirini kullanmak üzere kayıttan yürütme sırasında çağrıları `ID3D11Device::CreateShaderResourceView` değiştirilir.

## <a name="example"></a>Örnek
**Mip-map Oluşturma** varyantı, aşağıdaki gibi bir kod kullanılarak yeniden üretılabilir:

```cpp
D3D11_TEXTURE2D_DESC texture_description;

// ...

texture_description.MipLevels = 0; // generate a full mipchain

std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);

for (auto&& mip_level : initial_data)
{
    // fill mip_level with the application-supplied initial data
}

d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)
```

Tam mip zincirine sahip bir doku oluşturmak için `D3D11_TEXTURE2D_DESC::MipLevels` 0 olarak ayarlayın. Tam mip zincirinde mip düzeylerinin sayısı floor(log2(n) + 1'tir; burada n, dokuda en büyük boyut olur.

için ilk verileri sağlarken, her `CreateTexture2D` mip düzeyi için D3D11_SUBRESOURCE_DATA nesnesi sağlamanız gerektiğini unutmayın.

> [!NOTE]
> Otomatik olarak oluşturmak yerine kendi mip düzeyi içeriğinizi sağlamak için, mip ile eşlenen dokuları destekleyen bir görüntü düzenleyicisi kullanarak dokularınızı oluşturmanız ve ardından dosyayı yükleyip mip düzeylerini 'ye geçmeniz `CreateTexture2D` gerekir.

## <a name="see-also"></a>Ayrıca bkz.
[Yarı/Çeyrek Doku Boyutları Çeşidi](half-quarter-texture-dimensions-variant.md)
