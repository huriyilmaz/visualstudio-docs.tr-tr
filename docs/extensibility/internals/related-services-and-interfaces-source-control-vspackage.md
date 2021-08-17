---
title: İlgili Hizmetler ve Arabirimler (Kaynak Denetimi VSPackage’ı)
titleSuffix: ''
description: Visual Studio SDK'daki VSPackage ile ilgili arabirimler için kaynak denetimi hakkında bilgi edinebilirsiniz. Paket, bazı arabirimleri kullanır ve kaynak denetimi için diğerlerini kullanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a51c5894234aba9b0689ee5ff940720ebab4c3e6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042081"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>İlgili Hizmetler ve Arabirimler (Kaynak Denetimi VSPackage’ı)

Bu bölümde, içinde VSPackage ile ilgili tüm kaynak denetimi arabirimleri [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] listeleniyor. VsPackage kaynak denetimi bu arabirimlerden bazılarını uygulayan ve kaynak denetim görevlerini gerçekleştirmek için diğerlerini kullanır.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Kaynak Denetimi VSPackage'ları için ve tarafından Uygulanan Arabirimler

 Aşağıdaki arabirimler içinde açıklanmıştır ve VSPackage kaynak denetimi, istenen özellik kümesine bağlı olarak alt [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] kümelerini uygulamaya almaktadır. Bazı arabirimler gerekli olarak işaretlenir ve her kaynak denetimi VSPackage tarafından uygulanmalıdır.

 Bir paketin uygulamadığını arabirimler için, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] varsayılan bir uygulama sağlar. VsPackage kayıtlı ve hiçbir proje denetlenen durumda varsayılan uygulamanın tasarlanma olduğunu unutmayın. DÜZGÜN yazılmış bir kaynak denetimi VSPackage, bu arabirimlerin varsayılan uygulamasına bırakmak yerine tüm gerekli arabirimleri kullanır.

 Kaynak denetimi VSPackage aşağıdaki arabirimlerin bir veya hepsini kapsülleyen bir özel hizmet uygulamalı.

 Arabirimler:

- Gerekli: Uygun varlık (kaynak denetimi VSPackage, Kaynak Denetimi Saplama, proje) arabirimini uygulamalı.

- Önerilen: Varlık bu arabirimi uygulamalı; aksi takdirde, kaynak denetimi işlevselliği sınırlı olabilir.

- İsteğe bağlı: Varlık, daha zengin bir özellik kümesi sağlamak için bu arabirimi gerçekleştirebilirsiniz.

| Arabirim | Amaç | Uygulama tarafından | Uygulamak? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Düzenleyiciler, bir dosyayı değiştirmeden veya kaydetmeden önce bu arabirimi çağırır. VsPackage kaynak denetimi dosyayı kontrol edebilir veya iade etme başarısız olursa işlemi reddeder. | Kaynak denetimi VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Bu arabirim, projeler için, projeleri kaynak denetimiyle kaydetme ve kaydetmeyi geri kaydetme ve temel kaynak denetimi özellikleri için destek sağlama gibi temel kaynak denetimi işlevleri sağlar. | Kaynak denetimi VSPackage | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Bu arabirim, işlevi kullanılarak veya yalnızca uygulayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> nesnesinin türüne geçirerek elde `IVsHierarchy` `IVsSccProject2` edilir. Dosyaları bir proje içinde kaynak denetimi altına almak veya projeye geçerli kaynak denetimi durumunu veya konumunu bildirmek için kullanılır. | Project | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Tümleştirme modülü, geçerli etkin VSPackage'i ayarlamak için bu arabirimi kullanır. | Kaynak denetimi VSPackage | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Bu arabirim bir abonelik modelini temel alan bir arabirimdir. Herhangi bir VSPackage, belge olaylarını almak istediğini ve kabuk tarafından gerçekleşecek olaylar hakkında bilgi almak istediğini işaret ediyor olabilir. tarafından uygulanır ve iş uygulanır ve bu da tarafından uygulanan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] olayları `IVsTrackProjectDocumentsEvents2` VSPackage'a iletir. | Kaynak Denetimi Saplama | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Bu arabirim toplu işlem, eşitlenmiş okuma/yazma işlemleri ve gelişmiş bir yöntem `OnQueryAddFiles` sağlar. | Kaynak Denetimi Saplama | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Çözüm Gezgini** ve projeler, projelere yeni dosyalar ekleniyorsa veya dosyalar ve klasörler yeniden adlandırıldı veya projelerden silindiğinde bu arabirimi çağırıyor. VSPackage kaynak denetimi proje dosyasını kontrol edebilir veya işlemi iptal edebilir. | Kaynak denetimi VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Çözüm Gezgini** projeleri ve projeleri, IVstrackProjectDocuments3 arabiriminin yöntemlerine yapılan çağrılara yanıt olarak bu arabirimi arar. VSPackage kaynak denetimi toplu işlemleri, eşitlenmiş okuma/yazma işlemlerini izleyebilir ve daha gelişmiş bir yöntemle `OnQueryAddFiles` çalışabilir. | Kaynak denetimi VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Bu arabirim, Web projeleri için liste yönetimi desteği sağlar. | Kaynak denetimi VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Bu arabirim, projelerde kaynak denetimli dosyaların ToolTips'ini almak için kullanılır. | Kaynak denetimi VSPackage | İsteğe Bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Bu arabirim ad alanı uzantısı desteği sağlar. | Kaynak denetimi VSPackage | İsteğe Bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | VSPackage bu arabirimi kullanarak ad alanı uzantısını **Yeni,** Aç veya **Kaydet** iletişim **kutularıyla** tümleştirin. Sonuç olarak, oluşturma sırasında projeler otomatik olarak kaynak denetimine eklenebilir veya bir kaydetme işlemi etkili olduğunda kaynak denetimine eklenebilir. | Kaynak denetimi VSPackage | İsteğe Bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | VSPackage, içinde yer alan düğümler için kaynak denetimi glyph'leri olarak ek glyph'ler tanımlamak için **bu arabirimi Çözüm Gezgini.** | Kaynak denetimi VSPackage | İsteğe Bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Web **projeleri** için Ekle iletişim kutusu bu arabirimi kullanır. Bir kaynak denetimi konumu için gözatma ve daha önce bu konumdaki kaynak denetim deposuna eklenen bir Web projesini açmak için yöntemler sağlar. | Kaynak denetimi VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Bu arabirim, kaynak denetiminden projelerin zaman uyumsuz (arka plan) yüklenmesi için destek sağlar. | Kaynak denetimi VSPackage | İsteğe Bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Bu arabirim, projelerin tarafından başlatılan zaman uyumsuz yüklemenin ilerlemesini izlemesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> sağlar. | Project | İsteğe Bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Bu arabirim, IDE'nin etkin kaynak denetimi VSPackage'larını sorgulamaya olanak sağlar. IDE, VSPackage'ın kayıtlı etkin kaynak denetimi olmadığını bile anlama gelen kaynak denetimi ayarlarının değerini sorgular. Bu arabirim tarafından uygulanır ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] işleniyor. | Kaynak Denetimi Saplama | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Bu arabirim, VSPackage kaynak denetimi kaydında kullanılır. | Kaynak Denetimi Saplama | Gerekli |
| <xref:EnvDTE.SourceControl> | Bu arabirim otomasyonda kullanılır. Bu nedenle, herhangi bir kullanıcı arabirimini görüntülemeden yalnızca yürütülebilir işlevleri gösterir. | Kaynak denetimi VSPackage | İsteğe Bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Bu arabirim, kaynak denetimi ayarlarını çözüm (.sln) dosyasına kaydetmek için kullanılır. Ayarlar, kaynak denetimi konumunu ve kaynak denetimi durum bayraklarını içerir. | Kaynak denetimi VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Bu arabirim, kaynak denetimi ayarlarını çözüm seçenekleri (.suo) dosyasına kaydetmek için kullanılır. Bu, geçerli kullanıcının liste konumu gibi kullanıcıya özgü kaynak denetimi ayarlarını içerebilir. | Kaynak denetimi VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Bu arabirim, çözümleri kapatmadan önce proje dosyalarını denetleme veya bir projeyi a açma işlemi için kaynak denetiminden yeni dosyalar alma gibi işlemleri gerçekleştirmek üzere olayları izlemek için kullanılır. | Kaynak denetimi VSPackage | Önerilen |

## <a name="see-also"></a>Ayrıca bkz.
- [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
