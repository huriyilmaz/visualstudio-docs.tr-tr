---
title: Kaynak denetimi tasarım kararları | Microsoft Docs
description: Kaynak denetimi uygularken projeler için göz önünde bulundurmanız gereken çeşitli önemli tasarım kararları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b7335e3c5b15365680d70486f5f8ec8d19e90af4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846497"
---
# <a name="source-control-design-decisions"></a>Kaynak Denetimi Tasarım Kararları
Kaynak denetimi uygulama sırasında projeler için aşağıdaki tasarım kararları göz önünde bulundurulmalıdır.

## <a name="will-information-be-shared-or-private"></a>Bilgiler paylaşılan mi yoksa özel mi olacak?
 Yapabileceğiniz en önemli tasarım kararı, hangi bilgilerin paylaşılabilir olduğu ve özel nedir? Örneğin, proje için dosya listesi paylaşılır, ancak bu dosya listesinde, bazı kullanıcılar özel dosyalar kullanmak isteyebilir. Derleyici ayarları paylaşılır, ancak başlangıç projesi genellikle özeldir. Ayarlar tamamen paylaşılır, bir geçersiz kılma ile paylaşılır ya da yalnızca özel. Tasarım ile, çözüm Kullanıcı seçenekleri (. suo) dosyaları gibi özel öğeler iade edilmez [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] . . Suo dosyası gibi özel dosyalardaki özel bilgileri veya oluşturduğunuz özel bir dosyayı (örneğin, Visual C# için. csproj. user dosyası veya Visual Basic için. vbproj. user dosyası) sakladığınızdan emin olun.

 Bu karar, hepsi dahil değildir ve öğe öğe temelinde yapılabilir.

## <a name="will-the-project-include-special-files"></a>Proje özel dosyalar içeriyor mu?
 Diğer önemli tasarım kararı, proje yapınızın özel dosyalar kullanıp kullanmadığını belirtir. Özel dosyalar, Çözüm Gezgini görünür olan dosyaları ve iade etme ve kullanıma alma iletişim kutularında görünen gizli dosyalardır. Özel dosyalar kullanıyorsanız, aşağıdaki yönergeleri izleyin:

1. Özel dosyaları proje kök düğümü ile ilişkilendirmeyin — diğer bir deyişle, proje dosyası. Proje dosyanız tek bir dosya olmalıdır.

2. Bir projede özel dosyalar eklendiğinde, kaldırıldığında veya yeniden adlandırıldığında, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> dosyaların özel dosya olduğunu gösteren bayrak kümesiyle birlikte uygun olaylar tetiklenmelidir. Bu olaylar, uygun yöntemleri çağıran projeye yanıt olarak ortam tarafından çağırılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> .

3. Projeniz veya düzenleyiciniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> bir dosya için çağrı yaparken, bu dosyayla ilişkili özel dosyalar otomatik olarak kullanıma alınmamış. Özel dosyaları ana dosyayla birlikte geçirin. Ortam, geçirilen tüm dosyalar arasındaki ilişkiyi algılayacak ve kullanıma alma Kullanıcı arabirimindeki özel dosyaları uygun şekilde gizleyecek.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
