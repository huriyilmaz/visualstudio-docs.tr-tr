---
title: Kaynak denetimi tasarım kararları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89d125dc52340e8528ee9692d5de00784632e6f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187895"
---
# <a name="source-control-design-decisions"></a>Kaynak Denetimi Tasarım Kararları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetimi uygulama sırasında projeler için aşağıdaki tasarım kararları göz önünde bulundurulmalıdır.  
  
## <a name="will-information-be-shared-or-private"></a>Bilgiler paylaşılan mi yoksa özel mi olacak?  
 Yapabileceğiniz en önemli tasarım kararı, hangi bilgilerin paylaşılabilir olduğu ve özel nedir? Örneğin, proje için dosya listesi paylaşılır, ancak bu dosya listesinde, bazı kullanıcılar özel dosyalar kullanmak isteyebilir. Derleyici ayarları paylaşılır, ancak başlangıç projesi genellikle özeldir. Ayarlar tamamen paylaşılır, bir geçersiz kılma ile paylaşılır ya da yalnızca özel. Tasarım ile, çözüm Kullanıcı seçenekleri (. suo) dosyaları gibi özel öğeler iade edilmez [!INCLUDE[vsvss](../../includes/vsvss-md.md)] . . Suo dosyası gibi özel dosyalardaki özel bilgileri veya oluşturduğunuz özel bir dosyayı (örneğin, Visual C# için. csproj. user dosyası veya Visual Basic için. vbproj. user dosyası) sakladığınızdan emin olun.  
  
 Bu karar, hepsi dahil değildir ve öğe öğe temelinde yapılabilir.  
  
## <a name="will-the-project-include-special-files"></a>Proje özel dosyalar içeriyor mu?  
 Diğer önemli tasarım kararı, proje yapınızın özel dosyalar kullanıp kullanmadığını belirtir. Özel dosyalar, Çözüm Gezgini görünür olan dosyaları ve iade etme ve kullanıma alma iletişim kutularında görünen gizli dosyalardır. Özel dosyalar kullanıyorsanız, aşağıdaki yönergeleri izleyin:  
  
1. Özel dosyaları proje kök düğümü ile ilişkilendirmeyin — diğer bir deyişle, proje dosyası. Proje dosyanız tek bir dosya olmalıdır.  
  
2. Bir projede özel dosyalar eklendiğinde, kaldırıldığında veya yeniden adlandırıldığında, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> dosyaların özel dosya olduğunu gösteren bayrak kümesiyle birlikte uygun olaylar tetiklenmelidir. Bu olaylar, uygun yöntemleri çağıran projeye yanıt olarak ortam tarafından çağırılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> .  
  
3. Projeniz veya düzenleyiciniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> bir dosya için çağrı yaparken, bu dosyayla ilişkili özel dosyalar otomatik olarak kullanıma alınmamış. Özel dosyaları ana dosyayla birlikte geçirin. Ortam, geçirilen tüm dosyalar arasındaki ilişkiyi algılayacak ve kullanıma alma Kullanıcı arabirimindeki özel dosyaları uygun şekilde gizleyecek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
