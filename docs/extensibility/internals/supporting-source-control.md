---
title: Kaynak Denetimi Destek | Microsoft Docs
description: Projeniz Visual Studio için dosya iadelerini, iadeleri ve diğer kaynak denetimi işlemlerini nasıl desteklediğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4601c7e10d3f3092ad274e0570148bb348a7f41a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086488"
---
# <a name="supporting-source-control"></a>Kaynak Denetimini Destekleme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeniz veya düzenleyiciniz için dosya iadelerini, iadeleri ve diğer kaynak denetimi işlemlerini destekler. Kaynak denetim istemcisi olarak, dinamik olarak tanımlanmış bir dosya kümesi için arşivleme, sürüm oluşturma ve denetim özellikleri sağlayan gibi bir kaynak denetim paketiyle etkileşim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] kurmak için tasarlanmıştır.

## <a name="in-this-section"></a>Bu Bölümde
- [Kaynak Denetimi Paketleri için Model](../../extensibility/internals/model-for-source-control-packages.md)

 Bir proje türünün kaynak denetimi desteklemek için uygulaması gereken arabirimleri açıklar.

- [Tasarım Kararları](../../extensibility/internals/source-control-design-decisions.md)

 Yanıtlarının proje türünü uygulamada değişikliklerini sağlayan sorular sağlar.

- [Yapılandırma Ayrıntıları](../../extensibility/internals/source-control-configuration-details.md)

 Kaynak denetimi desteğinin proje türünün uygulamasını nasıl değiştirir?

- [Projeler ve Düzenleyiciler için Ek Yönergeler](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Proje türleri ve düzenleyiciler için en iyi yöntemleri ele almaktadır.

- [Çalışma Zamanı Ayrıntıları](../../extensibility/internals/source-control-runtime-details.md)

 Bir kullanıcı projeyi kaynak denetim sistemine eklense de projenin nasıl kayded açıklar.

## <a name="reference"></a>Başvuru
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Ortama veya kaynak denetim paketine, bir dosyanın bellekte değişmek veya kaydedilebilir olduğunu gösterir.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> Projelerin ve hiyerarşilerin kendilerini kaynak denetimine kaydetmelerine ve kaynak denetimi durumu hakkında bilgi edinlerine izin verir.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Proje dosyaları ve proje öğeleri için kaynak denetimi sağlamak için bir proje sisteminde uygulanır.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Bir çözümde dosya veya dizin ekleme, kaldırma veya yeniden adlandırma izni için ortamı sorgulamak için projeler tarafından kullanılır.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> İstemcilere proje dosyalarında veya dizinlerde yapılan değişiklikleri iletir.

## <a name="related-sections"></a>İlgili Bölümler
- [Proje Türleri](../../extensibility/internals/project-types.md)

 Tümleşik geliştirme ortamının (IDE) temel yapı taşları olarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projelere genel bir bakış sağlar. Projelerin kodu derlemeyi ve derlemeyi denetlemeyi açıklayan ek konulara bağlantılar sağlanır.
