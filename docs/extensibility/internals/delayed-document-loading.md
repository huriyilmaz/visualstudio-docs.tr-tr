---
title: Gecikmeli belge yükleme | Microsoft Docs
description: Visual Studio 'da gecikmeli belge yükleme hakkında bilgi edinin ve bir belgedeki öğeleri yüklenmeden önce sorgulayıp uzantıları nasıl kodlarlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 80c12780b2177c6715af9dc047a5652633993127
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902910"
---
# <a name="delayed-document-loading"></a>Gecikmeli belge yükleme

Bir Kullanıcı bir Visual Studio çözümünü yeniden açtığında, ilişkili belgelerin çoğu hemen yüklenmez. Belge penceresi çerçevesi, bekleyen bir başlatma durumunda oluşturulur ve bir yer tutucu belge (saplama çerçevesi denir) çalışan belge tablosuna (RDT) yerleştirilir.

Uzantınız, belgelerde yüklenmeden önce öğeleri sorgulayarak, Visual Studio için genel bellek ayak izini artırabilen, proje belgelerinin gereksiz yere yüklenmesine neden olabilir.

## <a name="document-loading"></a>Belge yükleme

Saplama çerçevesi ve belge, Kullanıcı belgeye eriştiğinde, örneğin pencere çerçevesinin sekmesini seçerek tamamen başlatılır. Belge, doğrudan belge verilerini almak için RDT 'e erişerek ya da aşağıdaki çağrılardan birini yaparak RDT 'e dolaylı olarak erişerek belge verilerini isteyen bir uzantı tarafından da başlatılabilir:

- Pencere çerçevesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> yöntemi.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>Aşağıdaki özelliklerden herhangi birinde pencere çerçevesi yöntemi:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Uzantınızın yönetilen kodu kullanması durumunda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> belgenin bekleyen başlatma durumunda olmaması veya belgenin tamamen başlatılmasını istiyorsanız, çağrı yapmadığınız bir durumdur. Bunun nedeni, yöntemin her zaman belge veri nesnesini döndürmesi, gerekirse oluşturulması. Bunun yerine, arabirimindeki yöntemlerden birini çağırmanız gerekir `IVsRunningDocumentTable4` .

- Uzantınız C++ kullanıyorsa, istemediğiniz parametrelere geçiş yapabilirsiniz `null` .

- Diğer özellikleri sormadan önce ilgili özellikleri sormadan önce aşağıdaki yöntemlerden birini çağırarak gereksiz belge yüklemekten kaçınabilirsiniz:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>[__VSFPROPID6 kullanma. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Bu yöntem <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , _VSRDTFLAGS4 için bir değer içeren bir nesnesi döndürür [. ](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) Belge henüz başlatılmamışsa RDT_PendingInitialization.

Belge tam olarak başlatıldığında oluşturulan RDT olayına abone olunarak bir belgenin ne zaman yüklendiğini öğrenebilirsiniz. İki olasılık vardır:

- Olay havuzu uygularsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> abone olabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,

- Aksi takdirde, abone olabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .

Aşağıdaki örnek bir kuramsal belge erişim senaryosudur: bir Visual Studio uzantısı, açık belgeler hakkında bazı bilgileri, örneğin düzenleme kilidi sayısını ve belge verileriyle ilgili bir şeyi göstermek istemektedir. Kullanarak RDT içindeki belgeleri numaralandırır <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> ve ardından her belge için, düzenleme kilidi sayısını ve belge verilerini almak için çağırır. Belge bekleyen başlatma durumundaysa, belge verileri istemek bunun gereksiz şekilde başlatılmasına neden olur.

Belgeye erişmenin daha verimli bir yolu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> düzenleme kilidi sayısını almak için kullanılır ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> belgenin başlatılmış olup olmadığını anlamak için öğesini kullanır. Bayraklar [_VSRDTFLAGS4 içermiyorsa. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), belge zaten başlatılmış ve belge verilerinin ile istenmesine <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> gerek yok, hiçbir gereksiz başlatmaya neden olmaz. Bayraklar [_VSRDTFLAGS4 içeriyorsa. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), uzantı belge başlatılmadan belge verilerinin istenmesine engel olmalıdır. Bu başlatma `OnAfterAttributeChange(Ex)` olay işleyicisinde algılanabilir.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Başlatmayı zorlarsa görmek için test uzantıları

Bir belgenin başlatılmış olup olmadığını göstermek için görünür bir ipucu yoktur, bu nedenle uzantınızın başlatmayı zorluyor olup olmadığına ulaşmak zor olabilir. Bir kaydı daha kolay hale getiren bir kayıt defteri anahtarı ayarlayabilirsiniz, çünkü tam olarak başlatılmamış her belge başlığına, başlığında *[stub]* metni sahip olacak şekilde neden olur.

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**'de **StubTabTitleFormatString** öğesini *{0} [stub]* olarak ayarlayın.
