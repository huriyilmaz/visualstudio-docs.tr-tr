---
title: MİP eşleme oluşturma varyantı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3ac567677776c225008a581cc4d5de85ec2c882d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64821008"
---
# <a name="mip-map-generation-variant"></a>Mip-map Oluşturma Çeşidi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oluşturma hedefleri olmayan dokuların MIP haritalarını sunar.  
  
## <a name="interpretation"></a>Yorumlama  
 MIP haritaları öncelikle dokudaki dokuların daha küçük sürümlerini önceden hesaplayarak, kele kapsamındaki dokuların diğer ad yapılarını ortadan kaldırmak için kullanılır. Bu ek dokular GPU belleğini tüketse de orijinal dokundan daha fazla yüzde 33 daha fazla olan yüzey alanı GPU dokusu önbelleğine sığdığı ve içeriği daha fazla kullanım elde ettiğinden daha verimli olur.  
  
 3B sahneler için, her iki işleme performansı ve görüntü kalitesini arttıkları için bellek ek dokuları depolamak için kullanılabilir olduğunda MIP eşlemeleri önerilir.  
  
 Bu varyant önemli bir performans kazancı gösteriyorsa, MIP haritalarını etkinleştirmeden dokuları kullandığınızı ve bu nedenle doku önbelleğinden en iyi şekilde yer almadığını gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
 MİP eşleme oluşturma, kaynak dokusu oluşturan her çağrıda zorlanır `ID3D11Device::CreateTexture2D` . Özellikle, geçirilen D3D11_TEXTUR2D_DESC nesne, `pDesc` değişmeyen bir gölgelendirici kaynağını açıkladığında, MIP-Map üretimi zorlanır.  
  
- BindFlags üyesi yalnızca D3D11_BIND_SHADER_RESOURCE bayrak kümesine sahiptir.  
  
- Kullanım üyesi D3D11_USAGE_DEFUALT ya da D3D11_USAGE_IMMUTABLE olarak ayarlanır.  
  
- CPUAccessFlags üyesi 0 olarak ayarlanır (CPU erişimi yok).  
  
- SampleDesc üyesinin Count üyesi 1 olarak ayarlanmış (çok örnekli bir kenar yumuşatma (MSAA)).  
  
- MIP düzeyleri üyesi 1 olarak ayarlanır (varolan MIP-Map yok).  
  
  Uygulama tarafından ilk veriler sağlandığında, biçim BC1, BC2 veya BC3 olmadığı sürece doku biçimi D3D11_FORMAT_SUPPORT_MIP_AUTOGEN tarafından belirlendiği şekilde otomatik MIP eşleme üretimini desteklemelidir — Aksi takdirde doku değiştirilmez ve ilk veriler sağlandığında hiçbir MIP eşlemesi oluşturulmaz.  
  
  MIP haritaları bir doku için otomatik olarak oluşturulduysa, ' ye yapılan çağrılar, `ID3D11Device::CreateShaderResourceView` doku örnekleme sırasında MIP zincirini kullanmak üzere kayıttan yürütme sırasında değiştirilir.  
  
## <a name="example"></a>Örnek  
 **MİP eşleme oluşturma** değişkeni aşağıdaki gibi kod kullanılarak yeniden oluşturulabilir:  
  
```  
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
  
 Tam MIP zinciri içeren bir doku oluşturmak için `D3D11_TEXTURE2D_DESC::MipLevels` 0 olarak ayarlayın. Tam MIP zincirindeki MIP düzeylerinin sayısı Floor (log2 (n) + 1), burada n, dokunun en büyük boyutudur.  
  
 İçin ilk verileri sağladığınızda `CreateTexture2D` , her MIP düzeyi için bir D3D11_SUBRESOURCE_DATA nesnesi sağlamanız gerektiğini unutmayın.  
  
> [!NOTE]
> Otomatik olarak oluşturmak yerine kendi MIP düzeyi içeriklerinizi sağlamak istiyorsanız, MIP eşlenmiş dokuları destekleyen bir görüntü Düzenleyicisi kullanarak dokularınızı oluşturmanız ve ardından dosyayı yükleyip MIP düzeylerini uygulamasına iletmeniz gerekir `CreateTexture2D` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yarı/çeyrek doku boyutları varyantı](../debugger/half-quarter-texture-dimensions-variant.md)
