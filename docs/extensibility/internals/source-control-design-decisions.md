---
title: Kaynak Denetimi Tasarım Kararları | Microsoft Docs
description: Kaynak denetimi uygulanırken projeler için göz önünde bulunduracak birkaç önemli tasarım kararı hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 79cbc22b16835e0f6c3fa9caa41ac9720c7022d8786520b1baf89d33c3b64948
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275183"
---
# <a name="source-control-design-decisions"></a>Kaynak Denetimi Tasarım Kararları
Kaynak denetimi uygulanırken projeler için aşağıdaki tasarım kararları dikkate alınmalıdır.

## <a name="will-information-be-shared-or-private"></a>Bilgiler paylaşılacak mı yoksa özel mi olacak?
 Karar vermenin en önemli tasarım kararı, paylaşılabilir bilgiler ve özel olandır. Örneğin, proje için dosya listesi paylaşılır, ancak bu dosya listesinde bazı kullanıcılar özel dosyalara sahip olmak istiyor olabilir. Derleyici ayarları paylaşılır, ancak başlangıç projesi genellikle özeldir. Ayarlar tamamen paylaşılır, geçersiz kılmayla paylaşılır veya tamamen özeldir. Tasarıma göre, Çözüm kullanıcı seçenekleri (.suo) dosyaları gibi özel öğeler içine [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] iadelanmaz. .suo dosyası gibi özel dosyalarda veya visual c# için .csproj.user dosyası ya da .vbproj.user dosyası gibi özel dosyalarda depolayabilirsiniz Visual Basic.

 Bu karar her şeyi içerir değildir ve öğe temelinde olabilir.

## <a name="will-the-project-include-special-files"></a>Proje özel dosyalar içerecek mi?
 Bir diğer önemli tasarım kararı da proje yapınız için özel dosyalar olup olmadığıdır. Özel dosyalar, iade etme ve iade etme iletişim Çözüm Gezgini görünen dosyaların altında yatan gizli dosyalardır. Özel dosyalar kullanıyorsanız şu yönergeleri izleyin:

1. Özel dosyaları proje kök düğümüyle, yani proje dosyasının kendisiyle ilişkilendirme. Proje dosyanız tek bir dosya olması gerekir.

2. Bir projede özel dosyalar ekleniyor, kaldırılıyor veya yeniden adlandırılıyorsa, uygun olaylar dosyaların özel dosyalar olduğunu belirten bayrak <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> kümesiyle birlikte çıkarılmalıdır. Bu olaylar, uygun yöntemleri çağıran projeye yanıt olarak ortam tarafından <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> çağrılır.

3. Projeniz veya düzenleyiciniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> bir dosyayı çağırsa, bu dosyayla ilişkili özel dosyalar otomatik olarak kullanıma alınmış olmaz. Özel dosyaları üst dosyayla birlikte iletir. Ortam, geçirilen tüm dosyalar arasındaki ilişkiyi algılar ve özel dosyaları iade kullanıcı arabiriminde uygun şekilde gizler.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
