---
title: Kaynak Denetimini Destekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84de3120783528d209b1475477aee5087edac42b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704726"
---
# <a name="supporting-source-control"></a>Kaynak Denetimini Destekleme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]projeniz veya düzenleyiciniz için dosya kullanıma sunmaları, iadeler ve diğer kaynak denetim işlemlerini destekler. Kaynak denetim istemcisi olarak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dinamik olarak tanımlanmış bir [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]dosya kümesi için arşivleme, sürüm ve denetim olanakları sağlayan bir kaynak denetim paketiyle etkileşime girerek tasarlanmıştır.

## <a name="in-this-section"></a>Bu Bölümde
- [Kaynak Denetimi Paketleri için Model](../../extensibility/internals/model-for-source-control-packages.md)

 Kaynak denetimini desteklemek için proje türünün uygulaması gereken arabirimleri açıklar.

- [Tasarım Kararları](../../extensibility/internals/source-control-design-decisions.md)

 Yanıtları proje türünü uygulama şeklinizi değiştiren sorular sağlar.

- [Yapılandırma Ayrıntıları](../../extensibility/internals/source-control-configuration-details.md)

 Destekleyici kaynak denetiminin proje türünün uygulanmasını nasıl değiştirdiğini açıklar.

- [Projeler ve Düzenleyiciler için Ek Yönergeler](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Proje türleri ve editörler için en iyi uygulamaları tartışır.

- [Çalışma Zamanı Ayrıntıları](../../extensibility/internals/source-control-runtime-details.md)

 Bir kullanıcı projeyi kaynak denetim sistemine eklediğinde projeyi nasıl kaydedilen açıklar.

## <a name="reference"></a>Başvuru
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>Ortama veya kaynak denetim paketine bir dosyanın bellekte değiştirilmek veya kaydolmak üzere olduğunu gösterir.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>Projelerin ve hiyerarşilerin kendilerini kaynak denetimine kaydetmelerine ve kaynak denetimi durumu hakkında bilgi edinmelerine olanak tanır.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>Proje dosyaları ve proje öğeleri için kaynak denetimi sağlamak için bir proje sisteminde uygulanır.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>Bir çözümde dosya veya dizin ekleme, kaldırma veya yeniden adlandırma izni için ortamı sorgulamak için projeler tarafından kullanılır.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>İstemcileri proje dosyalarında veya dizinlerde yapılan değişiklikleri not eder.

## <a name="related-sections"></a>İlgili Bölümler
- [Proje Türleri](../../extensibility/internals/project-types.md)

 Entegre geliştirme ortamının (IDE) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] temel yapı taşları olarak projelere genel bir bakış sağlar. Bağlantılar, projelerin oluşturma ve kod derlemeyi nasıl denetlediğini açıklayan ek konulara verilir.
