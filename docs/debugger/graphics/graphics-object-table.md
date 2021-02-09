---
title: Grafik nesne tablosu | Microsoft Docs
description: Visual Studio grafik analizinde bir oyun veya uygulamanın çerçevesini destekleyen Direct3D nesnelerini anlamanıza yardımcı olan grafik nesne tablosu hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 095828e711f860662432edd767b19493b73c56c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887581"
---
# <a name="graphics-object-table"></a>Grafik Nesnesi Tablosu
Visual Studio grafik analizinde grafik nesne tablosu, oyununuzun veya uygulamanızın çerçevesini destekleyen Direct3D nesnelerini anlamanıza yardımcı olur.

 Bu, nesne tablosudur:

 ![Bir uygulama tarafından oluşturulan Direct3D nesneleri.](media/gfx_diag_demo_object_table_orientation.png "gfx_diag_demo_object_table_orientation")

## <a name="understanding-the-graphics-object-table"></a>Grafik nesne tablosunu anlama
 Nesne tablosunu kullanarak, belirli bir çerçeveyi işlemeyi destekleyen Direct3D nesnelerini çözümleyebilirsiniz. Bir işleme sorununu, özelliklerini ve verilerini inceleyerek belirli bir nesneye (tanılamada daha önce diğer Grafik Tanılama araçları kullanarak, beklediğiniz gibi olmayan nesnelerin listesini daraltabilirsiniz.) Sorunlu nesneyi bulduğunuz zaman, incelemek için türüne özgü bir görselleştirmeyi kullanabilirsiniz. Örneğin, doku içeriğini görüntülemek için görüntü düzenleyiciyi veya *arabellek görselleştirmesini* görüntülemek Için görüntü düzenleyicisini kullanabilirsiniz.

 Nesne tablosu kopyalamayı ve yapıştırmayı destekler, böylece başka bir araç (örneğin, Microsoft Excel) kullanarak içeriğini inceleyebilirsiniz.

 Ayrıca, sol üst köşedeki **tür** açılan listesini kullanarak, tür **arabelleklerinin**, **gölgelendiricilerin** veya **dokuların** veya bu öğelerin tümünün aynı anda görüntülenmesini sağlayabilirsiniz.  Ayrıca, gösterilen tüm veriler genelinde belirli satırları bulmak için sağ üst köşedeki arama kutusunu da kullanabilirsiniz.  Örneğin, listedeki bu biçimdeki tüm nesne örneklerini bulmak için *D32_FLOAT* araması yapabilirsiniz.

### <a name="graphics-object-table-format"></a>Grafik nesne tablosu biçimi
 Nesne tablosu, seçili olayla ilişkili çerçeveyi destekleyen Direct3D nesne ve kaynaklarını (örneğin, durum nesneleri, arabellekler, gölgelendiriciler, dokular ve diğer kaynaklar) görüntüler. Önceki çerçevede oluşturulan ancak yakalanan çerçeve sırasında kullanılmayan nesneler nesne tablosundan çıkarılır. Yakalanan çerçeve sırasında önceki olaylar tarafından yok edilmiş nesneler sonraki olaylarda atlanır. D3D10Device veya D3D11DeviceContext üzerinde ayarlı olmayan nesneler gri metin olarak görüntülenir. Nesneler tablo biçiminde görüntülenir.

|Sütun|Açıklama|
|------------|-----------------|
|**Tanımlayıcı**|Nesne KIMLIĞI.|
|**Ad**|Nesnesinde Direct3D işlevi kullanılarak ayarlanan uygulamaya özgü bilgiler, `SetPrivateData` genellikle bir nesne hakkında ek tanımlayıcı bilgi sağlamak için.|
|**Tür**|Nesne türü.|
|**Etkin**|Yakalanan çerçeve sırasında D3D10Device veya D3D11DeviceContext üzerinde ayarlanan bir nesne için "*" görüntüler.<br /><br /> Bu, gri metin olarak görüntülenen nesnelere karşılık gelir, ancak nesne tablosunun sıralanmasını sağlamak için kullanabileceğiniz bir sütun girişi sağlar.|
|**Boyut**|Nesnenin bayt cinsinden boyutu.|
|**Biçimlendir**|Nesnenin biçimi. Örneğin, bir doku nesnesinin biçimi veya bir gölgelendirici nesnesinin gölgelendirici modeli.|
|**Genişlik**|Bir doku nesnesinin genişliği. Diğer nesne türleri için de geçerlidir.|
|**Yükseklik**|Bir doku nesnesinin yüksekliği. Diğer nesne türleri için de geçerlidir.|
|**Derinliğini**|3-b doku nesnesinin derinliği. Doku 3-D değilse, değer 0 ' dır. Diğer nesne türleri için de geçerlidir.|
|**MIPS**|Bir doku nesnesinin sahip olduğu MıP düzeylerinin sayısı. Diğer nesne türleri için de geçerlidir.|
|**Dizi boyutu**|Bir doku dizisindeki dokuların sayısı. Aralık 1 ile geçerli özellik düzeyi tarafından tanımlanan bir üst sınırdır. Küp eşleme için, bu değer dizideki küp haritaları sayısının 6 katından fazla olur.|
|**Örnekler**|Piksel başına çok örnek sayısı.|

## <a name="graphics-object-viewers"></a>Grafik nesne görüntüleyicileri
 Bir nesne hakkındaki ayrıntıları görüntülemek için, nesne tablosunda adını seçerek açın. Nesnesi hakkındaki ayrıntılar, nesnenin türüne bağlı olarak farklı biçimlerde görüntülenir. Örneğin, dokular doku Görüntüleyicisi kullanılarak, D3D11 cihaz bağlamı gibi cihaz durumu ise biçimli bir liste olarak görüntülenir. Farklı Direct3D sürümleri farklı nesneler kullanır ve her sürümün en önemli nesneleri için genellikle belirli Görselleştiriciler vardır.

 Bu, çıktı Merger ardışık düzen aşamasının içeriğini gösteren doku görüntüleyicisine sahiptir.

 ![Çıktı Merini görüntüleyen doku önizlemesi](media/gfx_diag_texture_preview.png "gfx_diag_texture_preview")

### <a name="d3d12-command-list"></a>D3D12 komut listesi
 Direct3D 12 ' de bir komut listesi, komutları tek bir istek olarak GPU 'ya gönderilebilmeleri için komut ayırıcılarına kaydeden bir nesnedir. Komut listeleri genellikle bir dizi durum ayarı, çizim, temizleme ve kopyalama komutu gerçekleştirir. Bu, özellikle önemlidir çünkü Direct3D 12 ' de işleme için tercih edilen yöntem olduklarından, performansı artırmaya yardımcı olmak için çerçeveler arasında yeniden kullanılabilir. Komut listesi ayrıntıları, kendi sekmesinde sunulan her bir ardışık düzen aşaması ile ilgili bilgiler içeren yeni bir belge penceresinde görüntülenir.

### <a name="d3d12-pipeline-state-object-pso"></a>D3D12 işlem hattı durumu nesnesi (PSO)
 Direct3D 12 ' de bir ardışık düzen durumu nesnesi, şu anda ayarlanmış tüm gölgelendiriciler ve belirli sabit işlevli durum nesneleri dahil olmak üzere GPU durumunun önemli bir kısmını temsil eder. Oluşturulduktan sonra bir işlem hattı durum nesnesi sabittir — bir uygulama, yalnızca farklı bir işlem hattı durum nesnesi bağlayarak işlem hattının yapılandırmasını değiştirebilir. PSO ayrıntıları, ardışık düzen yapılandırmasının ayrıntılarıyla hiyerarşik olarak düzenlendiği yeni bir belge penceresinde görüntülenir.

### <a name="d3d12-root-signature"></a>D3D12 kök Imzası
 Direct3D 12 ' de, kök imzası bir grafik veya işlem ardışık düzenine bağlanan tüm kaynakları tanımlar ve gölgelendiricilerin gerektirdiği kaynakları komut listelerine bağlar. Genellikle, grafikler için bir kök imzası ve bir uygulamada işlem için bir tane vardır. Kök imzası ayrıntıları, yeni bir belge penceresinde görüntülenir ve kök imzasının ayrıntıları hiyerarşik olarak düzenlenir.

### <a name="d3d12-resources"></a>D3D12 kaynakları
 Direct3D 12 ' de kaynaklar, işleme ardışık düzenine veri sağlayan tüm nesneler yakalar; Bu, farklı tür ve kaynak boyutları için çok sayıda belirli nesne tanımlayan Direct3D11 'e karşılık gelir. Direct3D 12 kaynağı doku verileri, köşe verileri, gölgelendirici verileri ve daha fazlasını içerebilir. Bu, derinlik arabelleği gibi işleme hedeflerini de temsil edebilirler. Direct3D 12 kaynağının ayrıntıları yeni bir belge penceresinde görüntülenir; Grafik analizi, türünü tespit edebilise kaynak nesnesinin içeriği için uygun görüntüleyiciyi kullanacaktır. Örneğin, doku verileri içeren bir kaynak nesnesi, tıpkı bir D3D11 Texture2D nesnesi gibi doku Görüntüleyicisi kullanılarak görüntülenir.

### <a name="device-context-object"></a>Cihaz bağlamı nesnesi
 Direct3D 11 ve Direct3D 10 ' da, cihaz bağlamı (**d3d11 cihaz bağlamı** veya **D3D10 cihazı**) nesnesi özellikle önemlidir çünkü en önemli durum bilgilerini barındırır ve şu anda ayarlanmış olan diğer durum nesnelerine bağlantı sağlar. Cihaz bağlamı ayrıntıları yeni bir belge penceresinde görüntülenir ve her bilgi kategorisi kendi sekmesinde sunulur. Geçerli cihaz durumunu yansıtmak için yeni bir olay seçildiğinde cihaz bağlamı değişir.

### <a name="buffer-object"></a>Buffer nesnesi
 Arabellek nesnesi ayrıntıları (D3D11 buffer veya D3D10 buffer), bir tablodaki arabellek içeriğini gösteren yeni bir belge penceresinde görüntülenir ve arabellek içeriklerinin nasıl görüntülendiğini değiştirmek için bir arabirim sağlar. **Arabellek verileri** tablosu, içeriğini incelemek için başka bir araç (örneğin, Microsoft Excel) kullanabilmeniz için kopyalama ve yapıştırmayı destekler. Arabelleğin içeriği, **arabellek veri** tablosunun üstünde bulunan **Biçim** Birleşik giriş kutusunun değerine göre yorumlanır. Kutusunda, aşağıdaki tabloda listelenen veri türlerinden oluşan bir bileşik veri biçimi girebilirsiniz. Örneğin, "float int", 32 bitlik kayan noktalı bir değer ve ardından 32 bit işaretli bir tamsayı değeri içeren yapıların listesini görüntüler. Belirttiğiniz bileşik veri biçimleri, daha sonra kullanılmak üzere Birleşik giriş kutusuna eklenir.

 Ayrıca, arabellekteki her bir öğenin sapmasını gizlemek veya görüntülemek için de kaydırmayı **göster** onay kutusunu işaretleyebilirsiniz.

|Tür|Description|
|----------|-----------------|
|**float**|32 bitlik kayan nokta değeri.|
|**float2**|2 32 bitlik kayan nokta değerlerini içeren bir vektör.|
|**float3**|3 32 bitlik kayan nokta değerlerini içeren bir vektör.|
|**float4**|4 32 bitlik kayan nokta değerlerini içeren bir vektör.|
|**bayt**|8 bit işaretli tamsayı değeri.|
|**2 bayt**|16 bit işaretli tamsayı değeri.|
|**4 bayt**|32 bitlik işaretli bir tamsayı değeri. **İnt** ile aynı.|
|**8 bayt**|64 bitlik işaretli bir tamsayı değeri. **Int64** ile aynıdır.|
|**xbyte**|8 bit onaltılı değer.|
|**x2byte**|16 bit onaltılı değer.|
|**x4byte**|32 bitlik bir onaltılık değer. **XINT** ile aynı.|
|**x8byte**|64 bitlik bir onaltılık değer. **Xint64** ile aynı.|
|**ubde**|8 bit işaretsiz tamsayı değeri.|
|**u2byte**|16 bit işaretsiz tamsayı değeri.|
|**u4byte**|32 bitlik işaretsiz bir tamsayı değeri. **Uint** ile aynı.|
|**u8byte**|64 bitlik işaretsiz bir tamsayı değeri. **Uint64** ile aynı.|
|**yarısını**|16 bit kayan nokta değeri.|
|**half2**|2 16 bitlik kayan nokta değerlerini içeren bir vektör.|
|**half3**|3 16 bitlik kayan nokta değerlerini içeren bir vektör.|
|**half4**|4 16 bitlik kayan nokta değerlerini içeren bir vektör.|
|**double**|64 bitlik kayan nokta değeri.|
|**int**|32 bitlik işaretli bir tamsayı değeri. **4byte** ile aynıdır.|
|**tutulamaz**|64 bitlik işaretli bir tamsayı değeri. **8byte** ile aynıdır.|
|**xint**|32 bitlik bir onaltılık değer. **X4byte** ile aynı.|
|**xint64**|64 bitlik bir onaltılık değer. **X8byte** ile aynı.|
|**uint**|32 bitlik işaretsiz bir tamsayı değeri. **U4byte** ile aynı.|
|**Int64**|64 bitlik işaretsiz bir tamsayı değeri. **U8byte** ile aynı.|
|**bool**|Boole ( `true` veya `false` ) değeri. Her Boole değeri 32 bitlik bir değer ile temsil edilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Grafik Tanılama (DirectX Grafiklerinde Hata Ayıklama)](visual-studio-graphics-diagnostics.md)
- [İzlenecek yol: Cihaz Durumu Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-device-state.md)