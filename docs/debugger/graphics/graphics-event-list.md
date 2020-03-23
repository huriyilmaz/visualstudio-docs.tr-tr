---
title: Grafik Etkinlik Listesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5c4e8f39ff77779985536e53d98ddc2785b109b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302128"
---
# <a name="graphics-event-list"></a>Grafik Olay Listesi
Oyununuzun veya uygulamanızın bir çerçevesini işlerken kaydedilen Direct3D olaylarını keşfetmek için Visual Studio Graphics Analyzer'daki Grafik Olay Listesini kullanın.

 Bu Olay Listesi:

 ![Adlarında "Dizin" olan olayların listesi.](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Etkinlik listesini kullanma
 Olay listesinde bir olay seçtiğinizde, diğer Grafik Analizi araçları tarafından görüntülenen bilgilere yansıtılır; bu diğer araçlarla birlikte olay listesini kullanarak nedenini belirlemek için bir işleme sorununu ayrıntılı olarak inceleyebilirsiniz. Olay listesini diğer Grafik Analizi araçlarıyla birlikte kullanarak oluşturma sorunlarını nasıl çözebileceğiniz hakkında daha fazla bilgi edinmek için [Örnekler'e](graphics-diagnostics-examples.md)bakın.

 Etkinlik listesinin özelliklerini etkili bir şekilde kullanmak, binlerce olay içerebilecek karmaşık çerçevelerin etrafından dolaşmak için önemlidir. Etkinlik listesini etkili bir şekilde kullanmak için, görünümün sizin için en uygun olduğunu seçin, olay listesini filtrelemek için aramayı kullanın, olayla ilişkili Direct3D nesneleri hakkında daha fazla bilgi edinmek için bağlantıları izleyin ve çekme çağrıları arasında hızlı bir şekilde hareket etmek için ok düğmelerini kullanın.

### <a name="color-coded-events-in-direct3d-12"></a>Direct3D 12'de renk kodlu olaylar
 Direct3D 12, farklı donanım işlevlerine karşılık gelen birden çok sıra yı ortaya çıkarır. Direct3D 12'de belirli bir grafik olayıyla ilişkili sırayı tanımlamaya yardımcı olmak için, direct3D 12 uygulamasının yakalanmasıyla çalışırken olaylar sıralarına göre Olay Listesi'nde renk kodlanır.

|Direct3D 12 Sıra|Renk|
|-----------------------|-----------|
|İşle tonu|Yeşil|
|İşlem sırası|Yellow|
|Sırayı kopyalama|Orange|

 Direct3D 11 birden fazla sırayı ortaya çıkarmadığından, Direct3D 11 uygulamasının yakalanmasıyla çalışırken olaylar Olay Listesinde renk kodlu değildir.

### <a name="event-list-views"></a>Olay listesi görünümleri
 Etkinlik listesi, iş akışınızı ve tercihlerinizi desteklemek için grafik etkinliklerini farklı şekillerde düzenleyen iki farklı görünümü destekler. İlk görünüm, olayları ve bunların ilişkili durum hiyerarşik olarak düzenleyen *GPU iş görünümüdür.* İkinci görünüm, olayları kronolojik olarak düz bir listede düzenleyen *zaman çizelgesi görünümüdür.*

 **GPU İş** görünümü yakalanan olayları ve durumlarını bir hiyerarşi içinde görüntüler. Hiyerarşinin en üst düzeyi, çağrıları çekme, temizleme, mevcut ve görünümlerle ilgilenen olaylardan oluşur. Olay listesinde, çekme çağrısı sırasında geçerli olan aygıt durumunu görüntülemek için çizim çağrılarını genişletebilirsiniz; ve değerlerini belirleyen olayları görüntülemek için her tür durumu daha da genişletebilirsiniz. Bu düzeyde, belirli bir durum önceki bir çerçevede ayarlanmış olup olmadığını veya son çekme çağrısından bu yana birden fazla kez ayarlanmış olup olmadığını da görebilirsiniz.

 **Zaman Çizelgesi** görünümü yakalanan her olayı kronolojik sırada görüntüler. Etkinlik listesini düzenleme nin bu yolu Visual Studio'nun önceki sürümleriyle aynıdır.

##### <a name="to-change-the-event-list-view-mode"></a>Olay listesi görünüm modunu değiştirmek için

- Grafik **Olay Listesi** penceresinde, olaylar listesinin üzerinde, **Görünüm** açılır yerini bulun ve **Zaman Çizelgesi** görünümünü veya **GPU İş** görünümünü seçti.

### <a name="filtering-events"></a>Olayları filtreleme
 **Grafik Olay Listesi** penceresinin sağ üst köşesinde bulunan Arama kutusunu kullanarak etkinlik listesini yalnızca adları belirli anahtar kelimeler içeren olayları içerecek şekilde filtreleyebilirsiniz. Önceki resimde gösterildiği `Vertex`gibi tek anahtar kelime veya adlarında `Draw;Primitive` `Draw` veya `Primitive` adlarında olan olaylarla eşleşen yarı sütunlu sınırlı bir liste kullanarak birden çok anahtar kelime belirtebilirsiniz. Aramalar beyaz alana duyarlıdır `VSSet` (örneğin `VS Set` ve farklı aramalardır-bu nedenle aramaları dikkatlice oluşturduğundan emin olun.

### <a name="moving-between-draw-calls"></a>Çekme çağrıları arasında taşıma
 Aramaları incelemek özellikle önemli olduğundan, çizim çağrılarını hızlı bir şekilde bulmak ve arasında hareket etmek için Bir **sonraki çekme çağrısına git** ve Grafik Olay **Listesi** penceresinin sol üst köşesinde bulunan önceki beraberlik çağrısı düğmelerine git düğmesini kullanabilirsiniz. **Go to the previous draw call** `Draw`

### <a name="links-to-graphics-objects"></a>Grafik nesnelerine bağlantılar
 Belirli grafik olaylarını anlamak için, Doğrudan 3D'nin geçerli durumu veya olay tarafından başvurulan Direct3D nesneleri hakkında ek bilgilere ihtiyacınız olabilir. Birçok olay, daha fazla ayrıntı için takip edebilirsiniz bu bilgilere bağlantılar sağlar.

## <a name="kinds-of-events-and-event-markers"></a>Etkinlik türleri ve olay işaretçileri
 Etkinlik listesinde görüntülenen olaylar dört kategoride düzenlenir: genel olaylar, çizim olayları, kullanıcı tanımlı olay grupları ve kullanıcı tanımlı olay işaretleri. Genel olaylar dışında, her olay ait olduğu kategoriyi gösteren bir simgeyle birlikte görüntülenir.

|Simge|Olay açıklaması|
|----------|-----------------------|
|(simge yok)|Genel olay<br /> Kullanıcı tanımlı bir olay, kullanıcı tanımlı olay grubu veya beraberlik olayı olmayan herhangi bir olay.|
|![Beraberlik olay simgesi](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Beraberlik olayı<br /> Yakalanan çerçeve sırasında oluşan bir beraberlik olayını işaretler.|
|![Kullanıcı tanımlı olay işaretçisi simgesi&#45;](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Kullanıcı tanımlı olay grubu<br /> Uygulama tarafından tanımlandığı şekilde, ilgili olayları grupla.|
|![Kullanıcı tanımlı olay işaretçisi simgesi&#45;](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Kullanıcı tanımlı olay işaretçisi<br /> Uygulama tarafından tanımlandığı gibi belirli bir konumu işaretler.|

## <a name="marking-user-defined-events-in-your-app"></a>Uygulamanızda kullanıcı tanımlı olayları işaretleme
 Kullanıcı tanımlı etkinlikler uygulamanıza özgür. Bunları, uygulamanızda meydana gelen önemli olayları Grafik Etkinlik Listesi'ndeki olaylarla ilişkilendirmek için kullanabilirsiniz. Örneğin, etkinlik listesine daha kolay göz atabilmeniz için kullanıcı arabiriminizi oluşturanlar gibi ilgili olayları (örneğin) düzenlemek için kullanıcı tanımlı etkinlik grupları oluşturabilirsiniz veya belirli bir tür nesne olduğunda işaretçiler oluşturabilirsiniz kolayca olay listesinde kendi grafik olayları bulabilirsiniz böylece çizilmiş.

 Uygulamanızda gruplar ve işaretçiler oluşturmak için Direct3D'nin diğer Direct3D hata ayıklama araçları tarafından kullanılmasını sağladığı API'leri kullanırsınız. Bu API'ler bazen Direct3D sürümleri arasında değişir, ancak temel işlevsellik aynıdır.

### <a name="user-defined-events-in-direct3d-12"></a>Direct3D 12'de kullanıcı tanımlı olaylar
 Direct3D 12'de gruplar ve işaretçiler oluşturmak için bu bölümde açıklanan API'leri kullanın. Aşağıdaki tablo, bir komut kuyruğuveya komut listesindeolayları işaretleme olup olmadığını bağlı olarak kullanabileceğiniz API'leri özetler.

|API Açıklama|[ID3D12Komut Sırası](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Kullanıcı tanımlı etkinlik kullanılabilirliğini denetleme|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|
|Etkinlik grubunu başlatma|[PIXBeginOlay](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[PIXBeginOlay](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|Etkinlik grubunu sonlandırma|[PIXEndOlay](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[PIXEndOlay](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|Olay işaretçisi oluşturma|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Direct3D 11 ve önceki kullanıcı tanımlı olaylar
 Direct3D 11 veya daha önceki gruplar ve işaretçiler oluşturmak için bu bölümde açıklanan API'leri kullanın. Aşağıdaki tabloda Direct3D 11'in farklı sürümleri ve Direct3D'nin önceki sürümleri için kullanabileceğiniz API'ler özetlenmiştir.

|API Açıklama|[ID3D11DeviceContext2 (Direct3D](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) 11.2)|[ID3DUserDefinedAnation](/windows/win32/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) (Direct3D 11.1)|D3DPerf_ API ailesi (Direct3D 11.0 ve önceki)|
|---------------------| - | - | - |
|Etkinlik grubunu başlatma|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|Etkinlik grubunu sonlandırma|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Olay işaretçisi oluşturma|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 Direct3D sürümünüzün desteklediği bu API'lerden herhangi birini kullanabilirsiniz-örneğin, Direct3D 11.1 API'yi `SetMarker` `D3DPerf_SetMarker` hedefliyorsanız, bir olay `SetMarkerInt` işaretçisini veya bir olay işaretçisini oluşturuyorsanız, ancak yalnızca Direct3D 11.2'de mevcut olduğu için kullanabilirsiniz ve hatta Direct3D'nin farklı sürümlerini destekleyenleri aynı uygulamada bir araya getirebilirsiniz.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Kaynak Geçmişi
Visual Studio 2017 ve üzeri **Kaynak Geçmişi** penceresini içerir.  **Etkinlik Listesi** penceresindeki](media/gfx_watch.png) bir girişin yanındaki saat simgesini ![seçmek, aşağıda gösterilen **Kaynak Geçmişi** penceresini gündeme getirir:

![Kaynak Geçmişi](media/gfx_diag_resource_history.png)

Bu pencere, olay listesinde seçili öğenin geçmişini görüntülemenizi sağlar.  Üstteki açılır bırakma, geçmişini görüntülemek için diğer öğeleri seçmek için kullanılabilir.  Pencerenin üst yarısında **Çerçeve Kurulum Olayları**içerir.  Bunlar, *Oluşturma* türü kategorisine giren ve genellikle kaynağı niçin baş harfe dönüştüren ve oluşturan çağrılardır.  Pencerenin alt yarısında **Çerçeve Olayları** bölümü bulunur.  Bunlar, kaynağın kullanımı sırasında meydana gelen normal okuma ve yazma olaylarıdır.

| Sütun | Açıklama |
|-----------| - |
| **Tür** | Giriş türünü gösterir, genellikle *Oluştur*, *Oku* ve *Yaz.* |
| **Görünüm** | Kaynağın o anda bir küçük resmini gösterir.  O anda kaynağın ayrıntıları görünümünü açmak için küçük resmi çift tıklatın. |
| **Olay** | Olayı oluşturan yöntem çağrısını gösterir.  Tek tek öğelerle ilgili herhangi bir ek geçmiş,](media/gfx_watch.png) uygun satırdaki saat simgesini ![seçerek görüntülenebilir.  Ayrıca, yukarıdaki ekran görüntüsünde olduğu gibi `m_commandList` mavi metinle çizilen herhangi bir öğe daha fazla ayrıntı için seçilebilir. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek Yol: Cihaz Durumu Nedeniyle Nesnelerin Eksikliği](walkthrough-missing-objects-due-to-device-state.md)