---
title: Gecikmiş Belge Yükleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708808"
---
# <a name="delayed-document-loading"></a>Gecikmiş belge yükleme

Bir kullanıcı Visual Studio çözümünün yeniden açılmasıyla, ilişkili belgelerin çoğu hemen yüklenmez. Belge penceresi çerçevesi bekleyen bir başlatma durumunda oluşturulur ve bir yer tutucu belge (saplama çerçevesi olarak adlandırılır) Çalışan Belge tablosuna (RDT) yerleştirilir.

Uzantınız, proje belgelerinin yüklenmeden önce belgelerdeki öğeleri sorgulayarak gereksiz yere yüklenmesine neden olabilir ve bu da Visual Studio'nun genel bellek ayak izini artırabilir.

## <a name="document-loading"></a>Belge yükleme

Saplama çerçevesi ve belge, örneğin pencere çerçevesinin sekmesini seçerek, kullanıcı belgeye eriştığında tamamen başolarak açılır. Belge, belge verilerini doğrudan elde etmek için RDT'ye erişerek veya aşağıdaki aramalardan birini yaparak dolaylı olarak RDT'ye erişerek belgenin verilerini isteyen bir uzantı tarafından da önolarak önolarak lanse edilebilir:

- Pencere çerçevesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> yöntemi.

- Aşağıdaki özelliklerden herhangi birinde pencere çerçevesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> yöntemi:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Uzantınız yönetilen kodu kullanıyorsa, belgenin bekleyen başlatma durumunda olmadığından emin değilseniz veya belgenin tamamen başlatılmasını istemiyorsanız aramamalısınız. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> Bunun nedeni, yöntemin her zaman doc veri nesnesini döndürerek gerekirse oluşturmasıdır. Bunun yerine, `IVsRunningDocumentTable4` arabirimdeki yöntemlerden birini aramalısınız.

- Uzantınız C++'ı kullanıyorsa, istemediğiniz parametreleri geçirebilirsiniz. `null`

- Diğer özellikleri sormadan önce ilgili özellikleri sormadan önce aşağıdaki yöntemlerden birini arayarak gereksiz belge yüklemesini önleyebilirsiniz:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>[__VSFPROPID6 kullanarak. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Bu yöntem, <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> _VSRDTFLAGS4 için bir değer içeren bir nesne döndürür. [ belge](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) henüz başharfe edilmemişse RDT_PendingInitialization.

Bir belge tamamen paraflandığında yükseltilen RDT olayına abone olarak bir belgenin ne zaman yüklendiğini öğrenebilirsiniz. İki olasılık vardır:

- Olay lavabo uygularsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>abone <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>olabilirsiniz ,

- Aksi takdirde, abone <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>olabilirsiniz.

Aşağıdaki örnek varsayımsal bir belge erişim senaryosudur: Visual Studio uzantısı, örneğin kilit sayısını ve belge verileriyle ilgili bir şey gibi açık belgeler le ilgili bazı bilgileri görüntülemek ister. RDT'deki belgeleri kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>sıralar, ardından <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> düzenkilidi sayısını ve belge verilerini almak için her belgeyi çağırır. Belge bekleyen başlatma durumundaysa, belge verilerinin istenmesi gereksiz yere başlatılmasına neden olur.

Bir belgeye erişmenin daha etkili <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> bir yolu, kilit sayısını edin ve belgenin baş olarak başolarak başolarak başlayıp başlatmadığını belirlemek için kullanmaktır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> Bayraklar _VSRDTFLAGS4 içermiyorsa. [ RDT_PendingInitialization,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)belge zaten başharfe alındı ve belge <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> verilerini istemek gereksiz bir başlatmaya neden olmaz. Bayraklar _VSRDTFLAGS4 [içeriyorsa. RDT_PendingInitialization,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)uzantı, belge başolarak başolarak başlatıldıktan önce belge verilerini istemekten kaçınmalıdır. Bu başlatma olay işleyicisi `OnAfterAttributeChange(Ex)` algılanabilir.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Başlatmayı zorlayıp zorlamadıklarını görmek için uzantıları test etme

Belgenin başolarak başharfe mi başlandığını belirtmek için görünür bir işaret yoktur, bu nedenle uzantınızın başlatmayı zorlayıp zorlamadığını bulmak zor olabilir. Doğrulamayı kolaylaştıran bir kayıt defteri anahtarı ayarlayabilirsiniz, çünkü başlıkta metin *[Stub]* olması için tam olarak başharfe fişeği olmayan her belgenin başlığına neden olur.

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**, **Set StubTabTitleFormatString** * {0} [Stub]* için.
