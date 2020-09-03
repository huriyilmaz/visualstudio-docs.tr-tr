---
title: Gecikmeli belge yükleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196867"
---
# <a name="delayed-document-loading"></a>Gecikmeli Belge Yüklemesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir Kullanıcı bir Visual Studio çözümünü yeniden açtığında, ilişkili belgelerin çoğu hemen yüklenmez. Belge penceresi çerçevesi, bekleyen bir başlatma durumunda oluşturulur ve bir yer tutucu belge (saplama çerçevesi denir) çalışan belge tablosuna (RDT) yerleştirilir.  
  
 Uzantınız, belgelerde yüklenmeden önce öğeleri sorgulayarak, proje belgelerinin gereksiz yere yüklenmesine neden olabilir. Bu, Visual Studio için genel bellek parmak izini artırabilir.  
  
## <a name="document-loading"></a>Belge yükleme  
 Saplama çerçevesi ve belge, Kullanıcı belgeye eriştiğinde, örneğin pencere çerçevesinin sekmesini seçerek tamamen başlatılır. Belge, doğrudan belge verilerini almak için RDT 'e erişerek ya da aşağıdaki çağrılardan birini yaparak RDT 'e dolaylı olarak erişerek belge verilerini isteyen bir uzantı tarafından da başlatılabilir:  
  
- Pencere çerçevesi yöntemi göster: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .  
  
- Aşağıdaki özelliklerden herhangi birinde pencere çerçevesi GetProperty yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> :  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Uzantınızın yönetilen kodu kullanması durumunda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> belgenin bekleyen başlatma durumunda olmaması veya belgenin tamamen başlatılmasını istiyorsanız, çağrı yapmadığınız bir durumdur. Bunun nedeni, bu yöntemin her zaman belge veri nesnesini döndürmesi, gerekirse oluşturulması. Bunun yerine, IVsRunningDocumentTable4 arabirimindeki yöntemlerden birini çağırmanız gerekir.  
  
  Uzantınız C++ kullanıyorsa, istemediğiniz parametrelere geçiş yapabilirsiniz `null` .  
  
  İlgili özellikleri sormadan önce aşağıdaki yöntemlerden birini çağırarak gereksiz belge yüklemekten kaçınabilirsiniz: diğer özellikleri sormadan önce.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> kullanılarak <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Bu yöntem <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , belge henüz başlatılmamış ise için bir değer içeren bir nesnesi döndürür.  
  
  Belge tam olarak başlatıldığında oluşturulan RDT olayına abone olunarak bir belgenin ne zaman yüklendiğini öğrenebilirsiniz. İki olasılık vardır:  
  
- Olay havuzu uygularsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> abone olabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,  
  
- Aksi takdirde, abone olabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .  
  
  Aşağıda kuramsal bir belge erişim senaryosu yer verilmiştir. Visual Studio uzantısı, açık belgeler hakkında bazı bilgileri, örneğin düzenleme kilidi sayısını ve belge verileriyle ilgili bir şeyi göstermek istiyor. Kullanarak RDT içindeki belgeleri numaralandırır <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> ve ardından her belge için, düzenleme kilidi sayısını ve belge verilerini almak için çağırır. Belge bekleyen başlatma durumundaysa, belge verileri istemek bunun gereksiz şekilde başlatılmasına neden olur.  
  
  Bunu yapmanın daha verimli bir yolu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> , düzenleme kilidi sayısını almak ve ardından <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> belgenin başlatılmış olup olmadığını anlamak için kullanmaktır. Bayraklar içermiyorsa <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , belge zaten başlatılmış ve belge verilerinin ile bulunması <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> gereksiz başlatmaya neden olmaz. Bayraklar içeriyorsa <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , uzantı belge başlatılana kadar belge verilerinin istenmesine engel olmalıdır. Bu, OnAfterAttributeChange (Ex) olay işleyicisinde tespit edilebilir.  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Başlatma zorlaması olup olmadığını görmek için uzantıları test etme  
 Bir belgenin başlatılmış olup olmadığını göstermek için görünür bir ipucu yoktur, bu nedenle uzantınızın başlatmayı zorluyor olup olmadığına ulaşmak zor olabilir. Bir kaydı daha kolay hale getiren bir kayıt defteri anahtarı ayarlayabilirsiniz, çünkü tamamen başlatılmayan her belgenin başlığına başlık içinde metin sahip olacak şekilde neden olur `[Stub]` .  
  
 **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]** Içinde, **StubTabTitleFormatString** değerini ** {0} [stub]** olarak ayarlayın.
