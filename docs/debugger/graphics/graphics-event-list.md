---
title: Grafik Olay Listesi | Microsoft Docs
description: Oyun veya uygulamanıza ait bir çerçeveyi Visual Studio Direct3D olaylarını keşfetmek için Visual Studio Graphics Analyzer'daki Grafik Olay Listesi'ne tıklayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2cb03305b036e5954340dc04a3c14d786b7735d7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052089"
---
# <a name="graphics-event-list"></a>Grafik Olay Listesi
Oyun veya uygulamanıza ait bir çerçeveyi Visual Studio Direct3D olaylarını keşfetmek için Visual Studio Graphics Analyzer'daki Grafik Olay Listesi'ne tıklayın.

 Bu, Olay Listesidir:

 ![Adlarında "Dizin" olan olayların listesi.](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Olay listesini kullanma
 Olay listesinden bir olay seçerek diğer Grafik Analizi araçları tarafından görüntülenen bilgilere yansıtabilirsiniz; Olay listesini bu diğer araçlarla birlikte kullanarak bir işleme sorununu ayrıntılı bir şekilde inceler ve nedenini tespit edin. Olay listesini diğer Grafik Analizi araçlarıyla birlikte kullanarak işleme sorunlarını nasıl çözebilirsiniz hakkında daha fazla bilgi edinmek için bkz. [Örnekler](graphics-diagnostics-examples.md).

 Olay listesinin özelliklerini etkili bir şekilde kullanmak, binlerce olay içerilebilecek karmaşık kareler elde etme açısından önemlidir. Olay listesini etkili bir şekilde kullanmak için en uygun görünümü seçin, olay listesini filtrelemek için arama kullanın, bir olayla ilişkili Direct3D nesneleri hakkında daha fazla bilgi edinmek için bağlantıları izleyin ve çizim çağrıları arasında hızla geçiş yapmak için ok düğmelerini kullanın.

### <a name="color-coded-events-in-direct3d-12"></a>Direct3D 12'de renk kodlu olaylar
 Direct3D 12, farklı donanım işlevlerine karşılık gelen birden çok kuyruğu ortaya çıkarır. Direct3D 12'de belirli bir grafik olayıyla ilişkili kuyruğun belirlenmesine yardımcı olmak için, Direct3D 12 uygulamasının yakalanması üzerinde çalışırken olaylar, olay listesinde kuyruklarına göre renk kodludur.

|Direct3D 12 Kuyruğu|Renk|
|-----------------------|-----------|
|Kuyruğu işleme|Yeşil|
|İşlem kuyruğu|Yellow|
|Kuyruğu kopyalama|Orange|

 Direct3D 11 birden çok kuyruğu açığa çıkarmaz, bu nedenle Direct3D 11 uygulamasının yakalaması üzerinde çalışırken olaylar Olay Listesinde renk kodlu olarak kodlu olarak yer değiştirmez.

### <a name="event-list-views"></a>Olay listesi görünümleri
 Olay listesi, grafik olaylarını iş akışınızı ve tercihlerinizi desteklemek için farklı şekillerde düzenleyen iki farklı görünümleri destekler. İlk görünüm, olayları *ve ilişkili durumlarını* hiyerarşik olarak düzenleyen GPU iş görünümü olur. İkinci görünüm, olayları *kronolojik* olarak düz bir listede düzenleyen zaman çizelgesi görünümüdür.

 **GPU çalışma görünümü** Yakalanan olayları ve bunların durumlarını bir hiyerarşide görüntüler. Hiyerarşinin en üst düzeyi çizim çağrıları, temizlemeler, mevcut ve görünümlerle ilgili olanlar gibi olaylardan oluşur. Olay listesinde, çizim çağrısı sırasında geçerli olan cihaz durumunu görüntülemek için draw çağrılarını genişletebilirsiniz; ve değerlerini ayaran olayları görüntülemek için her tür durumu daha da genişletebilirsiniz. Bu düzeyde, belirli bir durum önceki çerçevede mi yoksa son çizim çağrısından bu yana birden çok kez ayarlanmış mı olduğunu da görebilir.

 Zaman **Çizelgesi** görünümü Yakalanan her olayı kronolojik sırada görüntüler. Olay listesini düzenlemenin bu yolu, olay listesinin önceki sürümlerindeki Visual Studio.

##### <a name="to-change-the-event-list-view-mode"></a>Olay listesi görünüm modunu değiştirmek için

- Grafik **Olay Listesi penceresinde,** olay listesinin üstünde  Görünüm açılan listesini bulun ve Zaman Çizelgesi görünümünü **veya** GPU İş **görünümünü** seçin.

### <a name="filtering-events"></a>Olayları filtreleme
 Olaylar listesini yalnızca adları belirli anahtar sözcükleri içeren  olayları içerecek şekilde filtrelemek için Grafik Olay Listesi penceresinin sağ üst köşesinde bulunan Arama kutusunu kullanabilirsiniz. Gibi tek anahtar sözcükler (önceki çizimde gösterildiği gibi) veya gibi noktalı virgülle ayrılmış bir liste kullanarak birden çok anahtar sözcük belirtebilirsiniz. Bu liste, adlarında veya olan olaylarla `Vertex` `Draw;Primitive` eş `Draw` `Primitive` görünür. Aramalar boşluklara duyarlıdır (örneğin, `VSSet` farklı `VS Set` aramalardır) bu nedenle aramaların dikkatli bir şekilde uzamlara uygun olduğundan emin olun.

### <a name="moving-between-draw-calls"></a>Çizim çağrıları arasında geçiş
 Çağrıları inceleme özellikle önemli olduğundan, çekme çağrılarını hızla bulmak ve aralarında geçiş yapmak için Sonraki çizim çağrısına git ve Grafik Olay Listesi penceresinin sol üst köşesinde bulunan önceki çizim çağrısı düğmelerine git'i `Draw` kullanabilirsiniz.   

### <a name="links-to-graphics-objects"></a>Grafik nesnelerine bağlantılar
 Belirli grafik olaylarını anlamak için Direct3D'nin geçerli durumu veya olay tarafından başvurulan Direct3D nesneleri hakkında ek bilgilere ihtiyacınız olabilir. Birçok olay, daha fazla ayrıntı için bu bilgilerin bağlantılarını sağlar.

## <a name="kinds-of-events-and-event-markers"></a>Olay türleri ve olay işaretçileri
 Olay listesinde görüntülenen olaylar dört kategoriye ayrılır: genel olaylar, çizim olayları, kullanıcı tanımlı olay grupları ve kullanıcı tanımlı olay işaretçileri. Genel olaylar dışında, her olay ait olduğu kategoriyi belirten bir simgeyle birlikte görüntülenir.

|Simge|Olay açıklaması|
|----------|-----------------------|
|(simge yok)|Genel olay<br /> Kullanıcı tanımlı olay, kullanıcı tanımlı olay grubu veya çizim olayı olmayan herhangi bir olay.|
|![Çizim olayı simgesi](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Draw olayı<br /> Yakalanan kare sırasında meydana gelen bir çizim olayı işaretler.|
|![Kullanıcı tanımlı&#45;işareti simgesine sahip](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Kullanıcı tanımlı olay grubu<br /> Uygulama tarafından tanımlanan ilgili olayları gruplar.|
|![Kullanıcı tanımlı&#45;işareti simgesine sahip](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Kullanıcı tanımlı olay işaretçisi<br /> Uygulama tarafından tanımlanan belirli bir konumu işaretler.|

## <a name="marking-user-defined-events-in-your-app"></a>Uygulamanıza kullanıcı tanımlı olayları işaretleme
 Kullanıcı tanımlı olaylar uygulamanıza özeldir. Bunları, uygulamanıza gelen önemli olayları Grafik Olay Listesi'nin olaylarla arasında ilişkide kullanmak için kullanabilirsiniz. Örneğin, kullanıcı arabiriminizi işleyecek olaylar gibi ilgili olayları düzenlemek için kullanıcı tanımlı olay grupları oluşturabilir, böylece olay listesine daha kolay göz atabilir veya olay listesinde grafik olaylarını kolayca bulmak için belirli türdeki nesneler çizilirken işaretçiler oluşturabilirsiniz.

 Uygulamanıza grup ve işaretçi oluşturmak için, Direct3D'nin diğer Direct3D hata ayıklama araçları tarafından kullanımına yönelik olarak sağladığı API'leri kullanırsanız. Bu API'ler bazen Direct3D sürümleri arasında değişir, ancak temel işlevler aynıdır.

### <a name="user-defined-events-in-direct3d-12"></a>Direct3D 12'de kullanıcı tanımlı olaylar
 Direct3D 12'de grup ve işaretçi oluşturmak için bu bölümde açıklanan API'leri kullanın. Aşağıdaki tabloda, bir komut kuyruğunda veya komut listesinde olayları işaretlemenize bağlı olarak kullanabileceğiniz API'ler özetlenmiştir.

|API Açıklaması|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Kullanıcı tanımlı olay kullanılabilirliğini denetleme|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|
|Olay grubu başlat|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|Olay grubunu sona erdir|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|Olay işaretçisi oluşturma|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Direct3D 11 ve önceki sürümlerde kullanıcı tanımlı olaylar
 Direct3D 11 veya önceki sürümlerde gruplar ve işaretçiler oluşturmak için bu bölümde açıklanan API'leri kullanın. Aşağıdaki tabloda Farklı Direct3D 11 sürümleri ve Direct3D'nin önceki sürümleri için kullanabileceğiniz API'ler özetlenmiştir.

|API Açıklaması|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](/windows/win32/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) (Direct3D 11.1)|D3DPerf_ API ailesi (Direct3D 11.0 ve önceki sürümler)|
|---------------------| - | - | - |
|Olay grubu başlat|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|Olay grubunu sona erdir|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Olay işaretçisi oluşturma|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 Direct3D sürümünüz tarafından desteklenen bu API'lerden herhangi birini kullanabilirsiniz. Örneğin, Direct3D 11.1 API'sini hedefiyorsanız veya kullanarak bir olay işaretçisi oluşturabilirsiniz, ancak yalnızca `SetMarker` `D3DPerf_SetMarker` Direct3D 11.2'de kullanılabilir olduğundan ve hatta direct3D'nin farklı sürümlerini destekleyenleri aynı uygulamada bir arada `SetMarkerInt` kullanabilirsiniz.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Kaynak Geçmişi
Visual Studio 2017 ve daha yenisi kaynak **geçmişi penceresini** içerir.  Olay Listesi penceresindeki bir girişin yanındaki saat simgesini izleme simgesi seçerek ![ aşağıda gösterilen Kaynak ](media/gfx_watch.png) **Geçmişi** penceresi açılır: 

![Kaynak Geçmişi](media/gfx_diag_resource_history.png)

Bu pencere, olay listesinde seçili öğenin geçmişini görüntülemeye olanak sağlar.  Üst menü, geçmişini görüntülemek için diğer öğeleri seçmek için kullanılabilir.  Pencerenin ilk yarısı Çerçeve Kurulum **Olayları'nı içerir.**  Bunlar, Oluşturma türü kategorisine *ait olaylardır* ve genellikle kaynağı başlatan ve oluşturan çağrılardır.  Pencerenin alt yarısında Çerçeve Olayları **bölümü** yer almaktadır.  Bunlar, kaynağın kullanımı sırasında oluşan normal okuma ve yazma olaylarıdır.

| Sütun | Açıklama |
|-----------| - |
| **Tür** | Girişin türünü ( genellikle Oluştur , *Oku* ve *Yaz)* *gösterir.* |
| **Görünüm** | O anda kaynağın küçük resmini gösterir.  Bu sırada kaynağın ayrıntılar görünümünü açmak için küçük resime çift tıklayın. |
| **Olay** | Olayı oluşturan yöntem çağrısını gösterir.  Tek tek öğelerdeki tüm ek geçmişler, uygun satırdaki saat simgesi ![ saat simgesi ](media/gfx_watch.png) seçerek viewedebilirsiniz.  Ayrıca, yukarıdaki ekran görüntüsünde olduğu gibi mavi metinle çizilen herhangi bir öğe `m_commandList` daha fazla ayrıntı için seçilebilir. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Cihaz Durumu Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-device-state.md)