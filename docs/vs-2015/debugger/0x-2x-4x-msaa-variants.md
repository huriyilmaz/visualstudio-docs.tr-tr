---
title: 0x-2x-4X MSAA çeşitleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6cc62e4ba56cb7be461bbf3cee5435cb404b7fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64797191"
---
# <a name="0x2x4x-msaa-variants"></a>0x/2x/4x MSAA Çeşitleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tüm işleme hedefleri ve takas zincirlerinde çok örnekli düzgünleştirme (MSAA) ayarlarını geçersiz kılar.  
  
## <a name="interpretation"></a>Yorumlama  
 Çoklu örnek kenar yumuşatma, her pikselde birden çok konumda örnek alarak görsel kaliteyi artırır; daha fazla MSAA düzeyi daha fazla örnek alır ve MSAA olmadan, pikselin merkezinden yalnızca bir örnek alınır. Uygulamanızda MSAA 'nın etkinleştirilmesi, genellikle işleme performansında düşük bir maliyetle oluşur ancak bazı iş yükleri veya belirli GPU 'Larda, neredeyse hiçbir etkisi yoktur.  
  
 Uygulamanızda zaten MSAA etkinse, daha az MSAA çeşitlemeleri mevcut, daha üst düzey MSAA 'nın ilgili performans maliyetini gösterir. Özellikle, 0x MSAA değişkeni, MSAA olmadan uygulamanızın göreli performansını gösterir.  
  
 Uygulamanızda zaten MSAA etkin değilse, 2x MSAA ve 4X MSAA türevleri, bunları uygulamanızda etkinleştirmenin göreli performans maliyetini gösterir. Maliyet kabul edilebilir olduğunda, uygulamanızın görüntü kalitesini artırmak için MSAA 'yı etkinleştirmeyi düşünün.  
  
> [!NOTE]
> Donanımınız, tüm biçimler için MSAA 'yi tam olarak desteklemeyebilir. Bu çeşitlerden herhangi biri, içinde çalışılabilecek bir donanım sınırlamasıyla karşılaştığında, performans Özeti tablosundaki sütunu boş olur ve bir hata iletisi oluşturulur.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu çeşitler, `ID3DDevice::CreateTexture2D` işleme hedefleri oluşturmaya yönelik çağrılarındaki örnek sayısı ve örnek kalitesi bağımsız değişkenlerini geçersiz kılar. Özellikle, bu parametreler şu durumlarda geçersiz kılınır:  
  
- `D3D11_TEXTURE2D_DESC`Geçirilen nesne `pDesc` bir işleme hedefini açıklar; yani:  
  
  - BindFlags üyesi D3D11_BIND_TARGET bayrak ya da D3D11_BIND_DEPTH_STENCIL bayrak kümesine sahip.  
  
  - Kullanım üyesi D3D11_USAGE_DEFAULT olarak ayarlanır.  
  
  - CPUAccessFlags üyesi 0 olarak ayarlanır.  
  
  - MIN düzeyleri üyesi 1 olarak ayarlanır.  
  
- Cihaz, tarafından belirlendiği şekilde, istenen işleme hedefi biçimi (D3D11_TEXTURE2D_DESC:: biçim üyesi) için istenen örnek sayısı (0, 2 veya 4) ve örnek kalitesi (0) destekler `ID3D11Device::CheckMultisampleQualityLevels` .  
  
  D3D11_TEXTURE2D_DESC:: BindFlags üyesinin D3D_BIND_SHADER_RESOURCE veya D3D11_BIND_UNORDERED_ACCESS bayrakları ayarlandıysa, dokunun iki sürümü oluşturulur; İlki, render hedefi olarak kullanılmak üzere bu bayrakları temizledi ve diğeri, ilk sürüm için bir çözümleme arabelleği olarak davranması için bu bayrakları içeren bir MSAA olmayan dokudır. Bu gereklidir çünkü bir MSAA dokusunun gölgelendirici kaynağı olarak kullanılması veya sıralanmamış erişimin geçerli olması olası değildir. Örneğin, üzerinde işlem yapan bir gölgelendirici, MSAA olmayan bir doku beklediği için hatalı sonuçlar üretir. Değişken ikincil bir MSAA dışı doku oluşturmışsa, MSAA işleme hedefi cihaz bağlamından her ayarlanmadığında, içeriği MSAA olmayan dokuya çözümlenir. Benzer şekilde, MSAA render hedefi bir gölgelendirici kaynağı olarak bağlanması veya sıralanmamış bir erişim görünümünde kullanılması gerektiğinde, çözümlenen MSAA olmayan doku bunun yerine bağlanır.  
  
  Bu çeşitler Ayrıca,,, ve kullanılarak oluşturulan tüm takas zincirlerinde MSAA ayarlarını geçersiz kılar `IDXGIFactory::CreateSwapChain` `IDXGIFactory2::CreateSwapChainForHwnd` `IDXGIFactory2::CreateSwapChainForCoreWindow` `IDXGIFactory2::CreateSwapChainForComposition` `ID3D11CreateDeviceAndSwapChain` .  
  
  Bu değişikliklerin net etkisi, tüm işlemenin bir MSAA işleme hedefine yapıldığından, ancak uygulamanız bu işleme hedeflerinden birini ya da bir gölgelendirici kaynak görünümü veya sırasız erişim görünümü olarak takas zinciri arabelleklerini kullanıyorsa, veriler işleme hedefinin çözümlenmiş, MSAA olmayan kopyasından örneklenir.  
  
## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar  
 Direct3D11 ' de, MSAA dokuları, MSAA olmayan dokulardan daha kısıtlanıyor. Örneğin, `ID3D11DeviceContext::UpdateSubresource` BIR MSAA dokusundaki `ID3D11DeviceContext::CopySubresourceRegion` arayamadıysanız ve kaynak kaynağın ve hedef kaynağın örnek sayısı ve örnek kalitesi eşleşmezse, bu değişken BIR kaynağın MSAA ayarlarını geçersiz kıldığında meydana gelebilir.  
  
 Kayıttan yürütme bu tür çakışmaları algıladığında, amaçlanan davranışı çoğaltmak için en iyi çabayı yapar, ancak sonuçları tam olarak eşleştirmek mümkün olmayabilir. Bu, bu varyantlar performansını yanlış temsil eden bir şekilde etkilemek için bunun yaygın bir durumdur olsa da, örneğin, bir piksel gölgelendiricisi içindeki akış denetimi bir dokunun kesin içeriğine göre belirlenir; çünkü çoğaltılan doku aynı içeriğe sahip olmayabilir.  
  
## <a name="example"></a>Örnek  
 Bu çeşitler, kullanılarak oluşturulan işleme hedefleri için aşağıdaki `ID3D11Device::CreateTexture2D` gibi kod kullanılarak yeniden oluşturulabilir:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
target_description.SampleDesc.Quality = 0;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```  
  
## <a name="example"></a>Örnek  
 Ya da ıdxgiswapzincirine:: Createswapzinciri veya D3D11CreateDeviceAndSwapChain kullanılarak oluşturulan takas zincirlerini şunun gibi kod kullanarak:  
  
```  
DXGI_SWAP_CHAIN_DESC chain_description;  
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
chain_description.SampleDesc.Quality = 0;  
  
// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.  
```
