---
title: VSPackage Yapısı (Kaynak Kontrol VSPackage) | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703803"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage Yapısı (Kaynak Denetimi VSPackage’ı)

Kaynak Denetim Paketi SDK, kaynak denetim uygulayıcısının kaynak denetim işlevini Visual Studio ortamıyla tümleştirmesine olanak tanıyan bir VSPackage oluşturmak için yönergeler sağlar. VSPackage, genellikle Visual Studio tümleşik geliştirme ortamı (IDE) tarafından talep üzerine yüklenen bir COM bileşenidir. Her VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>uygulamak gerekir. BIR VSPackage genellikle Visual Studio IDE tarafından sunulan hizmetleri tüketir ve kendi bazı hizmetleri sunar.

VSPackage menü öğelerini bildirir ve .vsct dosyası üzerinden varsayılan öğe durumu belirler. Visual Studio IDE, VSPackage yüklenene kadar menü öğelerini bu durumda görüntüler. Daha sonra, vspackage'ın yöntemin uygulanması, menü öğelerini <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> etkinleştirmek veya devre dışı etmek için çağrılır.

## <a name="source-control-package-characteristics"></a>Kaynak Kontrol Paketi Özellikleri

Bir kaynak kontrolü VSPackage derinden Visual Studio entegre edilmiştir. VSPackage semantik şunlardır:

- VsPackage `IVsPackage` (arayüz) olması sayesinde uygulanacak arayüz

- UI Komutu uygulaması (.vsct <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> dosyası ve arabirimin uygulanması)

- VSPackage'ın Visual Studio ile kaydedilmesi.

Kaynak denetimi VSPackage bu diğer Visual Studio varlıkları ile iletişim kurmalıdır:

- Projeler

- Düzenleyiciler

- Çözümler

- Windows

- Çalışan belge tablosu

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Tüketilebilecek Görsel Stüdyo Çevre Hizmetleri

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciSağlayıcı Hizmeti

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>VSIP Arayüzleri Uygulandı ve Çağrıldı

Kaynak kontrol paketi bir VSPackage'dir ve bu nedenle Visual Studio'ya kayıtlı diğer VSPackage'larla doğrudan etkileşime girebiliyor. Kaynak denetimi işlevselliğinin tamamını sağlamak için, bir kaynak denetimi VSPackage projeler veya kabuk tarafından sağlanan arayüzler ile başa çıkabilir.

Visual Studio IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> içinde bir proje olarak kabul edilmesi için Visual Studio her proje uygulamak gerekir. Ancak, bu arabirim kaynak denetimi için yeterince özel değildir. Kaynak denetimi altında olması beklenen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>projeler uygulanır. Bu arabirim, bir projeyi içeriği için sorgulamak ve glifleri ve bağlayıcı bilgileri (sunucu konumu ile kaynak denetimi altında olan projenin disk konumu arasında bağlantı kurmak için gereken bilgiler) sağlamak için kaynak denetimi VSPackage tarafından kullanılır.

Kaynak denetimi VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>projelerin kaynak denetimi için kendilerini kaydetmelerine ve durum larını geri almalarına olanak tanıyan bir uygulama uygular.

Kaynak denetimi VSPackage'ın göz önünde bulundurması gereken arabirimlerin tam listesi için [Bkz. İlgili Hizmetler ve Arabirimler.](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [İlgili Hizmetler ve Arabirimler](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
