---
title: Kaynak denetimi tasarım kararları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a7c8a902520323f548a7dd77a84b07a56bfc9a0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723610"
---
# <a name="source-control-design-decisions"></a>Kaynak Denetimi Tasarım Kararları
Kaynak denetimi uygulama sırasında projeler için aşağıdaki tasarım kararları göz önünde bulundurulmalıdır.

## <a name="will-information-be-shared-or-private"></a>Bilgiler paylaşılan mi yoksa özel mi olacak?
 Yapabileceğiniz en önemli tasarım kararı, hangi bilgilerin paylaşılabilir olduğu ve özel nedir? Örneğin, proje için dosya listesi paylaşılır, ancak bu dosya listesinde, bazı kullanıcılar özel dosyalar kullanmak isteyebilir. Derleyici ayarları paylaşılır, ancak başlangıç projesi genellikle özeldir. Ayarlar tamamen paylaşılır, bir geçersiz kılma ile paylaşılır ya da yalnızca özel. Tasarım, çözüm Kullanıcı seçenekleri (. suo) dosyaları gibi özel öğeler [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] iade edilmez. Tüm özel bilgileri. suo dosyası gibi özel dosyalarda veya oluşturduğunuz belirli bir özel dosyada (örneğin, görsel C# için. csproj. user dosyası veya Visual Basic için. vbproj. user dosyası) depoladığınızdan emin olun.

 Bu karar, hepsi dahil değildir ve öğe öğe temelinde yapılabilir.

## <a name="will-the-project-include-special-files"></a>Proje özel dosyalar içeriyor mu?
 Diğer önemli tasarım kararı, proje yapınızın özel dosyalar kullanıp kullanmadığını belirtir. Özel dosyalar, Çözüm Gezgini görünür olan dosyaları ve iade etme ve kullanıma alma iletişim kutularında görünen gizli dosyalardır. Özel dosyalar kullanıyorsanız, aşağıdaki yönergeleri izleyin:

1. Özel dosyaları proje kök düğümü ile ilişkilendirmeyin — diğer bir deyişle, proje dosyası. Proje dosyanız tek bir dosya olmalıdır.

2. Bir projede özel dosyalar eklendiğinde, kaldırıldığında veya yeniden adlandırıldığında, uygun <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> olayları, dosyaların özel dosyalar olduğunu gösteren bayrak kümesiyle birlikte tetiklenmelidir. Bu olaylar, uygun <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> yöntemlerini çağıran projeye yanıt olarak ortam tarafından çağırılır.

3. Projeniz veya düzenleyiciniz bir dosya için <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> çağırdığında, bu dosyayla ilişkili özel dosyalar otomatik olarak kullanıma alınır. Özel dosyaları ana dosyayla birlikte geçirin. Ortam, geçirilen tüm dosyalar arasındaki ilişkiyi algılayacak ve kullanıma alma Kullanıcı arabirimindeki özel dosyaları uygun şekilde gizleyecek.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)