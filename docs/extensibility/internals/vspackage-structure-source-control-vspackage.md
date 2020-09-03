---
title: VSPackage yapısı (kaynak denetimi VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3f09b189e1e4b47187586e66c74315ee32495c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703803"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage Yapısı (Kaynak Denetimi VSPackage’ı)

Kaynak denetim paketi SDK 'Sı, kaynak denetim işlevlerini Visual Studio ortamıyla tümleştirmesine izin veren bir VSPackage oluşturmaya yönelik yönergeler sağlar. VSPackage, genellikle kayıt defteri girişlerinde paketin tanıtıldığı hizmetlere bağlı olarak, Visual Studio tümleşik geliştirme ortamı (IDE) tarafından isteğe bağlı olarak yüklenen bir COM bileşenidir. Her VSPackage uygulaması gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . VSPackage, genellikle Visual Studio IDE tarafından sunulan hizmetleri kullanır ve bunların bazı hizmetlerini temin etmek için kullanılır.

VSPackage, menü öğelerini bildirir ve. vsct dosyası aracılığıyla varsayılan bir öğe durumu oluşturur. Visual Studio IDE, VSPackage yükleninceye kadar menü öğelerini bu durumda görüntüler. Daha sonra, VSPackage 'ın <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi, menü öğelerini etkinleştirmek veya devre dışı bırakmak için çağrılır.

## <a name="source-control-package-characteristics"></a>Kaynak denetimi paket özellikleri

Kaynak denetimi VSPackage, Visual Studio 'ya çok daha tümleştirilmiştir. VSPackage semantiği şunları içerir:

- VSPackage (arabirim) olarak sanallaştırılan tarafından uygulanacak arabirim `IVsPackage`

- UI komut uygulama (. vsct dosyası ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimin uygulanması)

- Visual Studio ile VSPackage kaydı.

Kaynak denetimi VSPackage, diğer Visual Studio varlıkları ile iletişim kurmalıdır:

- Projeler

- Düzenleyiciler

- Çözümler

- Windows

- Çalışan belge tablosu

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Tüketilen Visual Studio ortam hizmetleri

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Svsregistersccıprovider hizmeti

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Uygulanan ve çağrılan VSıP arabirimleri

Kaynak denetim paketi bir VSPackage ve bu nedenle doğrudan Visual Studio ile kaydedilmiş diğer VSPackages ile etkileşime girebilirler. Kaynak denetimi işlevselliğinin tam kapsamını sağlamak için, bir kaynak denetimi VSPackage, projeler veya kabuğun sağladığı arabirimlerle ilgilenebilirler.

Visual Studio 'daki her projenin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> , Visual STUDIO IDE içinde bir proje olarak tanınması için uygulanması gerekir. Ancak, bu arabirim kaynak denetimi için yeterince uzmanlaşmış değildir. Kaynak denetimi altında olması beklenen projelerin uygulanması bekleniyor <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Bu arabirim, bir projeyi içerikleri için sorgulamak ve BT glifleri ile bağlama bilgilerini sağlamak için kaynak denetimi VSPackage tarafından kullanılır (sunucu konumu ve kaynak denetimi altındaki bir projenin disk konumu arasında bir bağlantı kurmak için gereken bilgiler).

Kaynak denetimi VSPackage uygular <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , bu da projelerin kaynak denetimine kaydolmasını ve durum glifleri almasına izin verir.

Bir kaynak denetimi VSPackage 'ın göz önünde bulundurmanız gereken arabirimlerin tüm listesi için bkz. [Ilgili hizmetler ve arabirimler](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [İlgili Hizmetler ve Arabirimler](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
