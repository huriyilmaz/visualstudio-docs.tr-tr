---
title: Kaynak Kontrol Tasarım Kararları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c36bb2b50a72a52aeaeb7712f4ed711845b5e6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705252"
---
# <a name="source-control-design-decisions"></a>Kaynak Denetimi Tasarım Kararları
Kaynak denetimi uygularken projeler için aşağıdaki tasarım kararları göz önünde bulundurulmalıdır.

## <a name="will-information-be-shared-or-private"></a>Bilgiler paylaşılacak mı yoksa özel mi?
 Yapabileceğiniz en önemli tasarım kararı, hangi bilgilerin sharable ve ne özel olduğudur. Örneğin, proje için dosya listesi paylaşılır, ancak bu dosya listesinde bazı kullanıcılar özel dosyalara sahip olmak isteyebilir. Derleyici ayarları paylaşılır, ancak başlangıç projesi genellikle özeldir. Ayarlar tamamen paylaşılır, geçersiz kılmayla paylaşılır veya tamamen özeldir. Tasarım gereği, Çözüm kullanıcı seçenekleri (.suo) dosyaları gibi özel [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]öğeler işaretlenmez. Özel bilgilerinizi .suo dosyası veya oluşturduğunuz özel bir dosya gibi özel dosyalarda depoladığınızdan emin olun, örneğin Visual C# için bir .csproj.user dosyası veya Visual Basic için .vbproj.user dosyası.

 Bu karar her şey dahil değildir ve madde bazında alınabilir.

## <a name="will-the-project-include-special-files"></a>Proje özel dosyalar içerecek mi?
 Bir diğer önemli tasarım kararı, proje yapınızın özel dosyalar kullanıp kullanmadığıdır. Özel dosyalar, Çözüm Gezgini'nde ve check-out ve kullanıma aliletişim kutularında görünen dosyaların altında yatan gizli dosyalardır. Özel dosyalar kullanıyorsanız, aşağıdaki yönergeleri izleyin:

1. Özel dosyaları proje kök düğümüyle, yani proje dosyasının kendisiyle ilişkilendirmeyin. Proje dosyanız tek bir dosya olmalıdır.

2. Özel dosyalar bir projeye eklendiğinde, kaldırıldığında veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> yeniden adlandırıldıklarında, dosyaların özel dosyalar olduğunu gösteren bayrak kümesiyle uygun olayların ateşlemesi gerekir. Bu olaylar, uygun <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> yöntemleri çağıran projeye yanıt olarak çevre tarafından çağrılır.

3. Projeniz veya düzenleyiciniz bir dosya aradığında, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> bu dosyayla ilişkili özel dosyalar otomatik olarak kullanıma alınmaz. Özel dosyaları ana dosyayla birlikte geçirin. Ortam, geçirilen tüm dosyalar arasındaki ilişkiyi algılar ve kullanıma alınan özel dosyaları kullanıma alan arabirimi'nde uygun şekilde gizler.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
