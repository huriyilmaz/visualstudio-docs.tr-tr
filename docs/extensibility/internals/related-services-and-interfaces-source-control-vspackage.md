---
title: İlgili Hizmetler ve Arayüzler (Kaynak Kontrol VSPackage) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 533f1bf4fcfbaebb25ec10908abf4a46ddacd521
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705622"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>İlgili Hizmetler ve Arabirimler (Kaynak Denetimi VSPackage’ı)
Bu bölümde, tüm kaynak denetimi VSPackage ile [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]ilgili arabirimler listelenir. Kaynak denetimi VSPackage bu arabirimlerden bazılarını uygular ve kaynak denetim görevlerini gerçekleştirmek için diğerlerini kullanır.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Kaynak Kontrol VSPackages tarafından ve için Uygulanan Arayüzler
 Aşağıdaki arabirimler [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)],'de tanımlanır ve kaynak denetimi VSPackage, istenilen özellik kümesine bağlı olarak bunların bir alt kümesini uygular. Bazı arabirimler gerekli olarak işaretlenir ve her kaynak denetimi VSPackage tarafından uygulanmalıdır.

 Bir paketin uygulamadığı bu arabirimler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için varsayılan bir uygulama sağlar. Varsayılan uygulamanın VSPackage kaydedilmemiş ve proje denetlenmeyen servis talebi için tasarlanır. Düzgün yazılmış bir kaynak denetimi VSPackage, bu arabirimlerin varsayılan uygulamasına bırakmak yerine gerekli tüm arabirimleri uygular.

 Bir kaynak denetimi VSPackage, aşağıdaki arabirimlerin bazılarını veya tümlerini kapsayan özel bir hizmet uygulamalıdır.

 Arayüzler şunlardır:

- Gerekli: Uygun varlık (kaynak denetimi VSPackage, Kaynak Kontrol Saplama, proje) arabirimi uygulamak zorundadır.

- Önerilen: Varlık bu arabirimi uygulamalıdır; aksi takdirde, kaynak denetimi işlevselliği sınırlı olabilir.

- İsteğe bağlı: varlık daha zengin bir özellik kümesi sağlamak için bu arabirimi uygulayabilirsiniz.

| Arabirim | Amaç | Tarafından uygulanan | Uygulamak? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Düzenleyiciler, bir dosyayı değiştirmeden veya kaydetmeden önce bu arabirimi çağırır. Kaynak denetimi VSPackage dosyayı kullanıma alabilir veya ödeme başarısız olursa işlemi reddedebilir. | Kaynak kontrolü VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Bu arabirim, projelerin kaynak denetimiyle kaydedilmesi ve kaydedilmesi ve kaydedilmesi ve temel kaynak denetimi glifleri için destek sağlanması gibi projeler için temel kaynak denetimi işlevselliği sağlar. | Kaynak kontrolü VSPackage | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirim <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> işlevi kullanarak elde edilir, ya da `IVsHierarchy` sadece `IVsSccProject2`nesne uygulayarak döküm tarafından . Bir projede dosyaları kaynak denetimi altında almak veya projeyi geçerli kaynak denetimi durumu veya konumu hakkında bilgilendirmek için kullanılır. | Project | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Tümleştirme modülü, geçerli etkin VSPackage'ı ayarlamak için bu arabirimi kullanır. | Kaynak kontrolü VSPackage | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Bu arabirim bir abonelik modeline dayanır. Herhangi bir VSPackage, belge etkinliklerialmak istediğini belirtebilir ve gerçekleşmek üzere olan olaylar hakkında kabuk tarafından bilgilendirilebilir. VsPackage'a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]uygulayan `IVsTrackProjectDocumentsEvents2` olaylardan geçer. | Kaynak Kontrol Saplama | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Bu arabirim toplu işleme, senkronize okuma/yazma `OnQueryAddFiles` işlemleri ve gelişmiş bir yöntem sağlar. | Kaynak Kontrol Saplama | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Çözüm Gezgini** ve projeler, projelere yeni dosyalar eklendiğinde veya dosya ve klasörler yeniden adlandırıldıklarında veya projelerden silindiğinde bu arabirimi çağırır. Kaynak denetimi VSPackage proje dosyasını kullanıma alabilir veya işlemi iptal edebilir. | Kaynak kontrolü VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Çözüm Gezgini** ve projeler, IVstrackProjectDocuments3 arabiriminin yöntemlerine yapılan çağrılara yanıt olarak bu arabirimi çağırır. Kaynak denetimi VSPackage toplu işlemleri, senkronize okuma/yazma işlemlerini izleyebilir ve `OnQueryAddFiles` daha gelişmiş bir yöntemle çalışabilir. | Kaynak kontrolü VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Bu arabirim, Web projeleri için listment yönetimi desteği sağlar. | Kaynak kontrolü VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Bu arabirim, projelerdeki kaynak denetimli dosyalar için ToolTips almak için kullanılır. | Kaynak kontrolü VSPackage | İsteğe bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Bu arabirim namespace uzantı desteği sağlar. | Kaynak kontrolü VSPackage | İsteğe bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | VSPackage, bir ad alanı uzantısını **Yeni,** **Aç**veya **Kaydet** iletişim kutularına entegre etmek için bu arabirimi kullanır. Sonuç olarak, projeler oluşturma üzerinde kaynak denetimine otomatik olarak eklenebilir veya bir kaydetme işlemi etkin olduğunda kaynak denetimine eklenebilir. | Kaynak kontrolü VSPackage | İsteğe bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | **VSPackage, Solution Explorer'daki**düğümler için kaynak denetim glifleri olarak ek glifleri tanımlamak için bu arabirimi kullanır. | Kaynak kontrolü VSPackage | İsteğe bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Web projeleri için **Ekle** iletişim kutusu bu arabirimi kullanır. Kaynak denetim konumuiçin tarama ve daha önce bu konumdaki kaynak denetim deposuna daha önce eklenen bir Web projesini açmak için yöntemler sağlar. | Kaynak kontrolü VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Bu arabirim, projelerin kaynak denetiminden asynchronous (arka plan) yüklemesi için destek sağlar. | Kaynak kontrolü VSPackage | İsteğe bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Bu arayüz, projelerin asynchronous yüklemenin ilerlemesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>izlemesine olanak sağlar. | Project | İsteğe bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Bu arabirim, IDE'nin etkin kaynak denetimi VSPackage'ı sorgulamasına olanak tanır. IDE, etkin kaynak denetimi VSPackage kayıtlı olmadığında bile anlam ifade eden kaynak denetim ayarlarının değerini sorgular. Bu arabirim, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].. | Kaynak Kontrol Saplama | Gerekli |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Bu arabirim, kaynak denetimi VSPackage'ın kaydedilmesinde kullanılır. | Kaynak Kontrol Saplama | Gerekli |
| <xref:EnvDTE.SourceControl> | Bu arabirim otomasyonda kullanılır. Bu nedenle, yalnızca herhangi bir uI görüntülemeden yürütülebilecek işlevleri ortaya çıkarır. | Kaynak kontrolü VSPackage | İsteğe bağlı |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Bu arabirim, çözüm (.sln) dosyasındaki kaynak denetim ayarlarını kaydetmek için kullanılır. Ayarlar, kaynak denetim konumunu ve kaynak denetimi durum bayraklarını içerir. | Kaynak kontrolü VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Bu arabirim, çözüm seçenekleri (.suo) dosyasındaki kaynak denetim ayarlarını kaydetmek için kullanılır. Bu, geçerli kullanıcının askere alma konumu gibi kullanıcıya özgü kaynak denetim ayarlarını içerebilir. | Kaynak kontrolü VSPackage | Önerilen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Bu arabirim, çözümleri kapatmadan önce proje dosyalarını denetleme veya proje açarken kaynak denetiminden yeni dosyalar alma gibi işlemleri gerçekleştirmek için olayları izlemek için kullanılır. | Kaynak kontrolü VSPackage | Önerilen |

## <a name="see-also"></a>Ayrıca bkz.
- [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
