---
title: Grafik olay listesi | Microsoft Docs
description: Oyununuzun veya uygulamanızın bir çerçevesini işlerken kaydedilen Direct3D olaylarını araştırmak için Visual Studio Grafik Çözümleyicisi 'deki grafik olay listesini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c964cda5cbe2903cf9511659b9a8f9bfb9f4aad6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884526"
---
# <a name="graphics-event-list"></a>Grafik Olay Listesi
Oyununuzun veya uygulamanızın bir çerçevesini işlerken kaydedilen Direct3D olaylarını araştırmak için Visual Studio Grafik Çözümleyicisi 'deki grafik olay listesini kullanın.

 Bu olay listesidir:

 ![Adında "Index" olan olayların listesi.](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Olay listesini kullanma
 Olay listesinden bir olay seçtiğinizde, bu, diğer grafik çözümleme araçları tarafından görüntülenen bilgilere yansıtılır; diğer araçlarla konser içindeki olay listesini kullanarak, nedenini öğrenmek için işleme sorununu ayrıntılı olarak inceleyebilirsiniz. Olay listesini diğer grafik analizi araçlarıyla birlikte kullanarak işleme sorunlarını nasıl çözebileceğiniz hakkında daha fazla bilgi için bkz. [örnekler](graphics-diagnostics-examples.md).

 Olay listesinin özelliklerinin etkili bir şekilde kullanılması, binlerce olay içerebilecek karmaşık çerçevelerin etrafında alınması açısından önemlidir. Olay listesini etkin bir şekilde kullanmak için, görünümü sizin için en uygun şekilde kullanın, olay listesini filtrelemek için arama 'yı kullanın, bir olayla ilişkili Direct3D nesneleri hakkında daha fazla bilgi edinmek için bağlantıları izleyin ve çizim çağrıları arasında hızlıca geçiş yapmak için ok düğmelerini kullanın.

### <a name="color-coded-events-in-direct3d-12"></a>Direct3D 12 ' de renk kodlu olaylar
 Direct3D 12, farklı donanım işlevlerine karşılık gelen birden çok sırayı gösterir. Direct3D 12 ' deki belirli bir grafik olayı ile ilişkili sırayı belirlemek için, bir Direct3D 12 uygulaması yakalamayla çalışırken, olaylar, kuyruğuna göre olay listesinde renk kodludur.

|Direct3D 12 kuyruğu|Renk|
|-----------------------|-----------|
|İşleme kuyruğu|Yeşil|
|İşlem kuyruğu|Yellow|
|Kopyalama kuyruğu|Orange|

 Direct3D 11 birden çok kuyruğu kullanıma sunmadığından, bir Direct3D 11 uygulaması yakalamayla çalışırken olay listesinde olaylar renk kodlanmamış.

### <a name="event-list-views"></a>Olay listesi görünümleri
 Olay listesi, grafik olaylarını, iş akışınızı ve tercihlerinizi desteklemeye yönelik farklı yollarla düzenleyen iki farklı görünümü destekler. İlk görünüm, olayları ve bunlarla ilişkili durumlarını hiyerarşik olarak düzenleyen *GPU iş görünümüdür* . İkinci görünüm, olayları kronolojik olarak düz bir listede düzenleyen *zaman çizelgesi görünümüdür* .

 **GPU iş** görünümü yakalanan olayları ve bunların durumlarını bir hiyerarşide görüntüler. Hiyerarşinin en üst düzeyi, çizim çağrıları, Temizleme, sunma ve görünümlerle ilgilenme gibi olaylardan oluşur. Olay listesinde, çizim çağrıları ' nı genişleterek arama sırasında geçerli olan cihaz durumunu görüntüleyebilirsiniz; Ayrıca, değerlerinin ayarlandığı olayları göstermek için her bir durum türünü daha da genişletebilirsiniz. Bu düzeyde, belirli bir durumun önceki çerçevede ayarlanmış olup olmadığını veya son çizim çağrısından bu yana birden çok kez ayarlandığını da görebilirsiniz.

 **Zaman çizelgesi** görünümü yakalanan her olayı kronolojik sırada görüntüler. Olay listesini düzenlemenin bu yolu, Visual Studio 'nun önceki sürümlerindeki ile aynıdır.

##### <a name="to-change-the-event-list-view-mode"></a>Olay listesi görünüm modunu değiştirmek için

- **Grafik olay listesi** penceresinde, olay listesinin üstünde, **Görünüm** açılır menüsünü bulun ve **zaman çizelgesi** görünümünü ya da **GPU iş** görünümünü seçin.

### <a name="filtering-events"></a>Olayları filtreleme
 Olaylar listesini yalnızca adları belirli anahtar sözcükleri içeren olayları içerecek şekilde filtrelemek için, **grafik olay listesi** penceresinin sağ üst köşesinde bulunan arama kutusunu kullanabilirsiniz. `Vertex`Önceki çizimde gösterildiği gibi tek bir anahtar sözcük veya adında noktalı virgülle ayrılmış bir liste kullanarak birden çok anahtar sözcük belirtebilirsiniz `Draw;Primitive` (örneğin `Draw` , adlarına veya adlarını içeren olaylarla eşleşir) `Primitive` . Aramalar, boşluk ile duyarlıdır — Örneğin, `VSSet` ve `VS Set` farklı aramalardır; bu nedenle, aramaları dikkatle ayarladığınızdan emin olun.

### <a name="moving-between-draw-calls"></a>Çizim çağrıları arasında dolaşma
 Çağrıları İnceleme `Draw` özellikle önemli olduğundan, **sonraki çizim çağrısına git** ' i kullanabilir ve çizim çağrılarını hızla bulmak ve arasında gezinmek Için **grafik olay listesi** penceresinin sol üst köşesinde bulunan **önceki çizim çağrı düğmelerine gidebilirsiniz** .

### <a name="links-to-graphics-objects"></a>Grafik nesnelerine bağlantılar
 Belirli grafik olaylarını anlamak için, Direct3D 'nin geçerli durumu veya olay tarafından başvurulan Direct3D nesneleri hakkında ek bilgilere ihtiyaç duyabilirsiniz. Birçok olay, daha fazla ayrıntı için izleyebileceğiniz bu bilgilere bağlantılar sağlar.

## <a name="kinds-of-events-and-event-markers"></a>Olay ve olay işaretçileri türleri
 Olay listesinde görüntülenen olaylar dört kategoride düzenlenmiştir: genel olaylar, çizim olayları, Kullanıcı tanımlı olay grupları ve Kullanıcı tanımlı olay işaretçileri. Genel olaylar hariç her olay, ait olduğu kategoriyi gösteren bir simgeyle birlikte görüntülenir.

|Simge|Olay açıklaması|
|----------|-----------------------|
|(simge yok)|Genel olay<br /> Kullanıcı tanımlı olay, Kullanıcı tanımlı olay grubu veya çizim olayı olmayan herhangi bir olay.|
|![Çizim olayı simgesi](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Çizim olayı<br /> Yakalanan çerçeve sırasında oluşan bir çizim olayını işaretler.|
|![Kullanıcı&#45;tanımlı olay işaretleyici simgesi](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Kullanıcı tanımlı olay grubu<br /> Uygulama tarafından tanımlanan şekilde ilgili olayları gruplandırır.|
|![Kullanıcı&#45;tanımlı olay işaretleyici simgesi](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Kullanıcı tanımlı olay işaretleyicisi<br /> Uygulama tarafından tanımlanan belirli bir konumu işaretler.|

## <a name="marking-user-defined-events-in-your-app"></a>Uygulamanızda Kullanıcı tanımlı olayları işaretleme
 Kullanıcı tanımlı olaylar uygulamanıza özeldir. Bunları, uygulamanızda, grafik olay listesindeki olaylarla oluşan önemli olayları ilişkilendirmek için kullanabilirsiniz. Örneğin, olay listesine daha kolay gözatabilmeniz için, Kullanıcı tanımlı olay gruplarını gruplar veya hiyerarşiler halinde düzenlemek için Kullanıcı tanımlı olay grupları oluşturabilirsiniz veya belirli nesne türleri çizildiğinde, bu sayede grafik olaylarını olay listesinde kolayca bulabilmeniz için işaretçiler oluşturabilirsiniz.

 Uygulamanızda gruplar ve işaretçiler oluşturmak için, Direct3D 'nin diğer Direct3D hata ayıklama araçları tarafından kullanılması için sağladığı API 'Leri kullanın. Bu API 'Ler bazen Direct3D sürümleri arasında değişir ancak temel işlevler aynıdır.

### <a name="user-defined-events-in-direct3d-12"></a>Direct3D 12 ' de Kullanıcı tanımlı olaylar
 Direct3D 12 ' de gruplar ve işaretçiler oluşturmak için bu bölümde açıklanan API 'Leri kullanın. Aşağıdaki tabloda, olayları bir komut kuyruğu veya komut listesine işaret ettiğinize bağlı olarak kullanabileceğiniz API 'Ler özetlenmektedir.

|API açıklaması|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Kullanıcı tanımlı olay kullanılabilirliğini denetle|[Pikselgetstatus](/previous-versions//dn788637(v=vs.85))|[Pikselgetstatus](/previous-versions//dn788637(v=vs.85))|
|Bir olay grubuna başla|[Piksellerle Beginevent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[Piksellerle Beginevent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|Bir olay grubunu Sonlandır|[Pikselendevent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[Pikselendevent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|Olay işaretleyicisi oluşturma|[Pikselsetişaretleyicisi](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[Pikselsetişaretleyicisi](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Direct3D 11 ve önceki sürümlerde Kullanıcı tanımlı olaylar
 Direct3D 11 veya daha önceki sürümlerde gruplar ve işaretçiler oluşturmak için bu bölümde açıklanan API 'Leri kullanın. Aşağıdaki tabloda, Direct3D 11 ve daha önceki Direct3D sürümlerinin farklı sürümleri için kullanabileceğiniz API 'Ler özetlenmektedir.

|API açıklaması|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11,2)|[ID3DUserDefinedAnnotation](/windows/win32/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) (Direct3D 11,1)|D3DPerf_ API ailesi (Direct3D 11,0 ve öncesi)|
|---------------------| - | - | - |
|Bir olay grubuna başla|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|Bir olay grubunu Sonlandır|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Olay işaretleyicisi oluşturma|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 Direct3D sürümünüzün desteklediği bu API 'lerden herhangi birini kullanabilirsiniz. Örneğin, Direct3D 11,1 API 'sini hedefliyorsanız, `SetMarker` `D3DPerf_SetMarker` bir olay işaretleyicisi oluşturmak için ya da `SetMarkerInt` yalnızca Direct3D 11.2 'de kullanılabilir olduğundan, ancak farklı Direct3D sürümlerini aynı uygulamada bir araya getiden de karıştırabilirsiniz.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Kaynak geçmişi
Visual Studio 2017 ve üzeri, **kaynak geçmişi** penceresini içerir.  ![ ](media/gfx_watch.png) **Olay listesi** penceresindeki bir girdinin yanındaki izle simgesini izle simgesini seçmek, aşağıda gösterilen **kaynak geçmişi** penceresini getirir:

![Kaynak geçmişi](media/gfx_diag_resource_history.png)

Bu pencere, etkinlik listesindeki seçili öğenin geçmişini görüntülemenize olanak sağlar.  Üstteki açılan menü, geçmişini görüntülemek için diğer öğeleri seçmek üzere kullanılabilir.  Pencerenin üst yarısında **çerçeve kurulum olayları** bulunur.  Bunlar, *oluşturma* türü kategorisine giren olaylardır ve genellikle kaynağı başlatıp oluşturan çağrılardır.  Pencerenin alt yarısında **çerçeve olayları** bölümü bulunur.  Bunlar, kaynağın kullanımı sırasında oluşan normal okuma ve yazma olaylardır.

| Sütun | Açıklama |
|-----------| - |
| **Tür** | Girişin türünü gösterir, genellikle *oluşturun*, *okuyun* ve *yazın*. |
| **Görünüm** | Bu anda kaynağın bir küçük resmini gösterir.  Söz konusu zamanda kaynağın Ayrıntılar görünümünü açmak için küçük resme çift tıklayın. |
| **Olay** | Olayı oluşturan oluşan yöntem çağrısını gösterir.  Her öğe için herhangi bir ek geçmiş, ![ uygun satırdaki izle simgesi izle simgesi seçilerek görüntülenebilir ](media/gfx_watch.png) .  Ayrıca, yukarıdaki ekran görüntüsünde olduğu gibi mavi metinde çizilen herhangi bir öğe, `m_commandList` daha fazla ayrıntı için seçilebilir. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Cihaz Durumu Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-device-state.md)