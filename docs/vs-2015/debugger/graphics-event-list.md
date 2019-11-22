---
title: Grafik olay listesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b1d8bdeb4497af57c385e73ff0dcd34041a2097
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297324"
---
# <a name="graphics-event-list"></a>Grafik Olay Listesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oyununuzun veya uygulamanızın bir çerçevesini işlerken kaydedilen Direct3D olaylarını araştırmak için Visual Studio Grafik Çözümleyicisi 'deki grafik olay listesini kullanın.  
  
 Bu olay listesidir:  
  
 ![Adında "Index" olan olayların listesi.](../debugger/media/gfx-diag-demo-event-list-orientation.png "gfx_diag_demo_event_list_orientation")  
  
## <a name="using-the-event-list"></a>Olay listesini kullanma  
 Olay listesinden bir olay seçtiğinizde, bu, diğer grafik çözümleme araçları tarafından görüntülenen bilgilere yansıtılır; diğer araçlarla konser içindeki olay listesini kullanarak, nedenini öğrenmek için işleme sorununu ayrıntılı olarak inceleyebilirsiniz. Olay listesini diğer grafik analizi araçlarıyla birlikte kullanarak işleme sorunlarını nasıl çözebileceğiniz hakkında daha fazla bilgi için bkz. [örnekler](../debugger/graphics-diagnostics-examples.md).  
  
 Olay listesinin özelliklerinin etkili bir şekilde kullanılması, binlerce olay içerebilecek karmaşık çerçevelerin etrafında alınması açısından önemlidir. Olay listesini etkin bir şekilde kullanmak için, görünümü sizin için en uygun şekilde kullanın, olay listesini filtrelemek için arama 'yı kullanın, bir olayla ilişkili Direct3D nesneleri hakkında daha fazla bilgi edinmek için bağlantıları izleyin ve çizim çağrıları arasında hızlıca geçiş yapmak için ok düğmelerini kullanın.  
  
### <a name="color-coded-events-in-direct3d-12"></a>Direct3D 12 ' de renk kodlu olaylar  
 Direct3D 12, farklı donanım işlevlerine karşılık gelen birden çok sırayı gösterir. Direct3D 12 ' deki belirli bir grafik olayı ile ilişkili sırayı belirlemek için, bir Direct3D 12 uygulaması yakalamayla çalışırken, olaylar, kuyruğuna göre olay listesinde renk kodludur.  
  
|Direct3D 12 kuyruğu|Renk|  
|-----------------------|-----------|  
|İşleme kuyruğu|Renkli|  
|İşlem kuyruğu|Renkle|  
|Kopyalama kuyruğu|Al|  
  
 Direct3D 11 birden çok kuyruğu kullanıma sunmadığından, bir Direct3D 11 uygulaması yakalamayla çalışırken olay listesinde olaylar renk kodlanmamış.  
  
### <a name="event-list-views"></a>Olay listesi görünümleri  
 Olay listesi, grafik olaylarını, iş akışınızı ve tercihlerinizi desteklemeye yönelik farklı yollarla düzenleyen iki farklı görünümü destekler. İlk görünüm, olayları ve bunlarla ilişkili durumlarını hiyerarşik olarak düzenleyen *çizim çağrıları görünümüdür* . İkinci görünüm, olayları kronolojik olarak düz bir listede düzenleyen *zaman çizelgesi görünümüdür* .  
  
 **Çizim çağrıları** görünümü  
 Yakalanan olayları ve bunların durumlarını hiyerarşide görüntüler. Hiyerarşinin en üst düzeyi, çizim çağrıları, Temizleme, sunma ve görünümlerle ilgilenme gibi olaylardan oluşur. Olay listesinde, çizim çağrıları ' nı genişleterek arama sırasında geçerli olan cihaz durumunu görüntüleyebilirsiniz; Ayrıca, değerlerinin ayarlandığı olayları göstermek için her bir durum türünü daha da genişletebilirsiniz. Bu düzeyde, belirli bir durumun önceki çerçevede ayarlanmış olup olmadığını veya son çizim çağrısından bu yana birden çok kez ayarlandığını da görebilirsiniz.  
  
 **Zaman çizelgesi** görünümü  
 Yakalanan her olayı kronolojik sırada görüntüler. Olay listesini düzenlemenin bu yolu, Visual Studio 'nun önceki sürümlerindeki ile aynıdır.  
  
##### <a name="to-change-the-event-list-view-mode"></a>Olay listesi görünüm modunu değiştirmek için  
  
- **Grafik olay listesi** penceresinde, olay listesinin üstünde, **Görünüm** açılır menüsünü bulun ve **zaman çizelgesi** görünümünü ya da **çizim çağrıları** görünümünü seçin.  
  
### <a name="filtering-events"></a>Olayları filtreleme  
 Olaylar listesini yalnızca adları belirli anahtar sözcükleri içeren olayları içerecek şekilde filtrelemek için, **grafik olay listesi** penceresinin sağ üst köşesinde bulunan arama kutusunu kullanabilirsiniz. Önceki çizimde gösterildiği gibi `Vertex`gibi tek bir anahtar sözcük veya `Draw;Primitive`gibi noktalı virgülle ayrılmış bir liste kullanarak birden çok anahtar sözcük belirtebilirsiniz. Bu, adlarında `Draw` ya da `Primitive` olan olaylarla eşleşir. Aramalar, boşluk ile duyarlıdır — Örneğin, `VSSet` ve `VS Set` farklı aramalardır; bu nedenle, aramaları dikkatle ayarladığınızdan emin olun.  
  
### <a name="moving-between-draw-calls"></a>Çizim çağrıları arasında dolaşma  
 `Draw` çağrılarının incelenmesi özellikle önemli olduğundan, **sonraki çizim aramasına git** ' i kullanarak, çizim çağrılarını hızla bulmak ve aralarında gezinmek Için **grafik olay listesi** penceresinin sol üst köşesinde bulunan **önceki çizim çağrı düğmelerine gidebilirsiniz** .  
  
### <a name="links-to-graphics-objects"></a>Grafik nesnelerine bağlantılar  
 Belirli grafik olaylarını anlamak için, Direct3D 'nin geçerli durumu veya olay tarafından başvurulan Direct3D nesneleri hakkında ek bilgilere ihtiyaç duyabilirsiniz. Birçok olay, daha fazla ayrıntı için izleyebileceğiniz bu bilgilere bağlantılar sağlar.  
  
## <a name="kinds-of-events-and-event-markers"></a>Olay ve olay işaretçileri türleri  
 Olay listesinde görüntülenen olaylar dört kategoride düzenlenmiştir: genel olaylar, çizim olayları, Kullanıcı tanımlı olay grupları ve Kullanıcı tanımlı olay işaretçileri. Genel olaylar hariç her olay, ait olduğu kategoriyi gösteren bir simgeyle birlikte görüntülenir.  
  
|Simge|Olay açıklaması|  
|----------|-----------------------|  
|(simge yok)|Genel olay<br /> Kullanıcı tanımlı olay, Kullanıcı tanımlı olay grubu veya çizim olayı olmayan herhangi bir olay.|  
|![Çizim olayı simgesi](../debugger/media/vsg-eventlist-icon-draw.png "vsg_eventlist_icon_draw")|Çizim olayı<br /> Yakalanan çerçeve sırasında oluşan bir çizim olayını işaretler.|  
|![Kullanıcı&#45;tanımlı olay işaret simgesi](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Kullanıcı tanımlı olay grubu<br /> Uygulama tarafından tanımlanan şekilde ilgili olayları gruplandırır.|  
|![Kullanıcı&#45;tanımlı olay işaret simgesi](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Kullanıcı tanımlı olay işaretleyicisi<br /> Uygulama tarafından tanımlanan belirli bir konumu işaretler.|  
  
## <a name="marking-user-defined-events-in-your-app"></a>Uygulamanızda Kullanıcı tanımlı olayları işaretleme  
 Kullanıcı tanımlı olaylar uygulamanıza özeldir. Bunları, uygulamanızda, grafik olay listesindeki olaylarla oluşan önemli olayları ilişkilendirmek için kullanabilirsiniz. Örneğin, olay listesine daha kolay gözatabilmeniz için, Kullanıcı tanımlı olay gruplarını gruplar veya hiyerarşiler halinde düzenlemek üzere Kullanıcı tanımlı olay grupları oluşturabilirsiniz veya belirli nesne türleri olduğunda işaretçiler oluşturabilirsiniz. grafik olaylarını olay listesinde kolayca bulabilmeniz için çizilir.  
  
 Uygulamanızda gruplar ve işaretçiler oluşturmak için, Direct3D 'nin diğer Direct3D hata ayıklama araçları tarafından kullanılması için sağladığı API 'Leri kullanın. Bu API 'Ler bazen Direct3D sürümleri arasında değişir ancak temel işlevler aynıdır.  
  
### <a name="user-defined-events-in-direct3d-12"></a>Direct3D 12 ' de Kullanıcı tanımlı olaylar  
 Direct3D 12 ' de gruplar ve işaretçiler oluşturmak için bu bölümde açıklanan API 'Leri kullanın. Aşağıdaki tabloda, olayları bir komut kuyruğu veya komut listesine işaret ettiğinize bağlı olarak kullanabileceğiniz API 'Ler özetlenmektedir.  
  
|API açıklaması|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|  
|---------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Kullanıcı tanımlı olay kullanılabilirliğini denetle|[Pikselgetstatus](https://msdn.microsoft.com/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[Pikselgetstatus](https://msdn.microsoft.com/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|  
|Bir olay grubuna başla|[Piksellerle Beginevent](https://msdn.microsoft.com/5f51fff7-f313-4558-965b-2a443653cd7b)|[Piksellerle Beginevent](https://msdn.microsoft.com/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|  
|Bir olay grubunu Sonlandır|[Pikselendevent](https://msdn.microsoft.com/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[Pikselendevent](https://msdn.microsoft.com/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|  
|Olay işaretleyicisi oluşturma|[Pikselsetişaretleyicisi](https://msdn.microsoft.com/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[Pikselsetişaretleyicisi](https://msdn.microsoft.com/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|  
  
### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Direct3D 11 ve önceki sürümlerde Kullanıcı tanımlı olaylar  
 Direct3D 11 veya daha önceki sürümlerde gruplar ve işaretçiler oluşturmak için bu bölümde açıklanan API 'Leri kullanın. Aşağıdaki tabloda, Direct3D 11 ve daha önceki Direct3D sürümlerinin farklı sürümleri için kullanabileceğiniz API 'Ler özetlenmektedir.  
  
|API açıklaması|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11,2)|[ID3DUserDefinedAnnotation](https://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11,1)|D3DPerf_ API ailesi (Direct3D 11,0 ve öncesi)|  
|---------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------|  
|Bir olay grubuna başla|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|  
|Bir olay grubunu Sonlandır|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|  
|Olay işaretleyicisi oluşturma|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|  
  
 Direct3D sürümünüzün desteklediği bu API 'lerden herhangi birini kullanabilirsiniz. Örneğin, Direct3D 11,1 API 'sini hedefliyorsanız, bir olay işaretleyicisi oluşturmak için `SetMarker` ya da `D3DPerf_SetMarker` kullanabilirsiniz, `SetMarkerInt` ancak yalnızca Direct3D 11.2 'de kullanılabilir olduğundan, farklı Direct3D sürümlerini destekleenler de aynı uygulamada de karıştırabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Cihaz Durumu Nedeniyle Nesnelerin Eksikliği](../debugger/walkthrough-missing-objects-due-to-device-state.md)
