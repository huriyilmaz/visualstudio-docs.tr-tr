---
title: VSPackage Yapısı (Kaynak Denetimi VSPackage) | Microsoft Docs
description: Bir VSPackage'a kaynak denetimi uygulayan ve bu uygulamayla tümleştirilsin diye yönergeler sağlayan Kaynak Denetim Paketi SDK'sı hakkında Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b95c382342675d79c0c6e854b5fc087d495827e2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898828"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage Yapısı (Kaynak Denetimi VSPackage’ı)

Kaynak Denetim Paketi SDK'sı, bir kaynak denetimi uygulayanın kendi kaynak denetimi işlevselliğini kendi kaynak denetimi işlevselliğini uygulama ortamıyla tümleştirerek vsPackage oluşturmaya Visual Studio sağlar. VSPackage, genellikle paket tarafından kayıt defteri girdilerinde tanıtılmış hizmetlere göre Visual Studio tümleşik geliştirme ortamı (IDE) tarafından isteğe bağlı olarak yüklenen bir COM bileşenidir. Her VSPackage uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> gerekir. VSPackage genellikle Visual Studio IDE tarafından sunulan hizmetleri tüketir ve bazı hizmetleri kendi başına sunar.

VSPackage, menü öğelerini belirtir ve .vsct dosyası aracılığıyla varsayılan öğe durumu belirtir. Bu Visual Studio IDE, VSPackage yüklenene kadar bu durumdaki menü öğelerini görüntüler. Ardından VSPackage'ın yöntemi uygulaması, menü öğelerini <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> etkinleştirmek veya devre dışı bırakmak için çağrılır.

## <a name="source-control-package-characteristics"></a>Kaynak Denetim Paketi Özellikleri

VsPackage kaynak denetimi, veri kaynağı ile Visual Studio. VSPackage semantiği şunları içerir:

- VSPackage (arabirim) olma sayesinde uygulanacak `IVsPackage` arabirim

- UI Komutu uygulaması (.vsct dosyası ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabiriminin uygulanması)

- VSPackage'ın Visual Studio.

VSPackage kaynak denetimi, aşağıdaki diğer Visual Studio kurmalıdır:

- Projeler

- Düzenleyiciler

- Çözümler

- Windows

- Çalışan belge tablosu

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio Ortam Hizmetleri

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider Hizmeti

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Uygulanan ve Çağrılmış VSIP Arabirimleri

Kaynak denetim paketi bir VSPackage'dır ve bu nedenle bu paketle kayıtlı diğer VSPackage'larla doğrudan Visual Studio. Kaynak denetimi işlevselliğinin tamamını sağlamak için VSPackage kaynak denetimi, projeler veya kabuk tarafından sağlanan arabirimlerle ilgilenebilirsiniz.

IDE içinde Visual Studio proje olarak tanınması için uygulamalı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> ve Visual Studio gerekir. Ancak, bu arabirim kaynak denetimi için yeterince özel değildir. Kaynak denetimi altında olması beklenen projeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> uygulanır. Bu arabirim, VSPackage kaynak denetimi tarafından bir projeyi içeriği için sorgulamak ve bu projeye glyphs ve bağlama bilgileri sağlamak için kullanılır (kaynak denetimi altındaki projenin sunucu konumu ile disk konumu arasında bağlantı kurmak için gereken bilgiler).

VSPackage kaynak denetimi, projelerin kendilerini kaynak denetimine kaydetmelerine ve durum ifadelerini almalarına olanak sağlayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> uygulamasıdır.

VSPackage kaynak denetimi tarafından göz önünde bulundurmalıdır arabirimlerin tam listesi için bkz. [İlgili Hizmetler ve Arabirimler.](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [İlgili Hizmetler ve Arabirimler](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
