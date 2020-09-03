---
title: Kaynak denetimini destekleme | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704726"
---
# <a name="supporting-source-control"></a>Kaynak Denetimini Destekleme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , projeniz veya düzenleyiciniz için dosya kullanıma alma işlemleri, iadeler ve diğer kaynak denetimi işlemlerini destekler. Kaynak Denetim istemcisi olarak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] dinamik olarak tanımlanmış bir dosya kümesi için arşivleme, sürüm oluşturma ve denetim olanakları sağlayan gibi bir kaynak denetimi paketiyle etkileşime geçmek üzere tasarlanmıştır.

## <a name="in-this-section"></a>Bu Bölümde
- [Kaynak Denetimi Paketleri için Model](../../extensibility/internals/model-for-source-control-packages.md)

 Kaynak denetimini desteklemek için bir proje türünün uygulanması gereken arayüzleri açıklar.

- [Tasarım Kararları](../../extensibility/internals/source-control-design-decisions.md)

 Yanıtları bir proje türünü nasıl uygulayacağınızı değiştiren sorular sağlar.

- [Yapılandırma Ayrıntıları](../../extensibility/internals/source-control-configuration-details.md)

 Destekleyici kaynak denetiminin bir proje türünün uygulamasını nasıl değiştirdiği açıklanmaktadır.

- [Projeler ve Düzenleyiciler için Ek Yönergeler](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Proje türleri ve düzenleyicilerle ilgili en iyi yöntemleri açıklar.

- [Çalışma Zamanı Ayrıntıları](../../extensibility/internals/source-control-runtime-details.md)

 Bir kullanıcının bir kaynak denetimi sistemine eklemesi durumunda projenin nasıl kaydedileceği açıklanmaktadır.

## <a name="reference"></a>Başvuru
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Bir dosyanın bellekte veya kaydedilmiş olarak değiştirilmesinin olduğu ortam veya kaynak denetimi paketine bildirir.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> Projelerin ve hiyerarşilerin kendilerini kaynak denetimi ile kaydetmesini ve kaynak denetimi durumu hakkında bilgi almasını sağlar.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Proje dosyaları ve proje öğeleri için kaynak denetimi sağlamak üzere bir proje sisteminde uygulanır.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Bir çözümde dosya veya dizin ekleme, kaldırma veya yeniden adlandırma izni için ortamı sorgulamak üzere kullanılır.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> İstemcilere proje dosyaları veya dizinlerinde yapılan değişiklikleri bildirir.

## <a name="related-sections"></a>İlgili Bölümler
- [Proje Türleri](../../extensibility/internals/project-types.md)

 , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamının (IDE) temel yapı taşları olarak projelere genel bir bakış sağlar. Bağlantılar, projelerin kod oluşturma ve derleme şeklini açıklayan ek konulara sağlanır.
