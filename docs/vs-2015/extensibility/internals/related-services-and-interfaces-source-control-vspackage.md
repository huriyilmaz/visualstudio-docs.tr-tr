---
title: İlgili hizmetler ve arabirimler (kaynak denetimi VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c5b040a8c5d0cbe2daff07f279cfd6a78cbd2b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157399"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>İlgili Hizmetler ve Arabirimler (Kaynak Denetimi VSPackage’ı)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu bölümde, içindeki tüm kaynak denetimi VSPackage ile ilgili arabirimlerin listesi yer almaktadır [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] . Kaynak denetimi VSPackage, bu arabirimlerden bazılarını uygular ve kaynak denetimi görevlerini gerçekleştirmek için diğerlerini kullanır.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Kaynak denetimi VSPackages için ve tarafından uygulanan arabirimler  
 Aşağıdaki arabirimler içinde açıklanmaktadır [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] ve kaynak denetimi VSPackage, istenen özellik kümesine bağlı olarak bunların bir alt kümesini uygular. Bazı arabirimler gerekli olarak işaretlenir ve her kaynak denetimi VSPackage tarafından uygulanmalıdır.  
  
 Bir paketin uygulamadığından bu arabirimler için [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] varsayılan bir uygulama sağlar. Varsayılan uygulamanın, VSPackage kayıtlı olmadığında ve proje denetleniyorsa, bu durum için tasarlandığını unutmayın. Düzgün şekilde yazılmış bir kaynak denetimi VSPackage, bu arabirimlerin varsayılan uygulamasına ayrılmaktansa tüm gerekli arabirimleri uygular.  
  
 Kaynak denetimi VSPackage, aşağıdaki arabirimlerin bazılarını veya tümünü kapsülleyen bir özel hizmet uygulamalıdır.  
  
 Arabirimler şunlardır:  
  
- Gerekli: uygun varlık (kaynak denetimi VSPackage, kaynak denetimi saplaması, proje) arabirimini gerçekleştirmelidir.  
  
- Önerilen: varlık bu arabirimi uygulamalıdır; Aksi takdirde, kaynak denetimi işlevselliği sınırlı olabilir.  
  
- İsteğe bağlı: varlık bu arabirimi, daha zengin bir özellik kümesi sağlamak için uygulayabilir.  
  
|Arabirim|Amaç|Uygulayan|Uygulamaktır?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Düzenleyiciler bir dosyayı değiştirmeden veya kaydetmeden önce bu arabirimi çağırır. Kaynak denetimi VSPackage dosyayı kullanıma alabilir veya kullanıma alma başarısız olursa işlemi reddedebilir.|Kaynak denetimi VSPackage|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Bu arabirim, projeler için temel kaynak denetim işlevlerini sağlar; örneğin, kaynak denetimiyle Proje kaydetme ve kaydı silme ve temel kaynak denetim glifleri için destek sağlama.|Kaynak denetimi VSPackage|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Bu arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> işlevini kullanarak veya yalnızca öğesine uygulayan nesne atama yoluyla elde edilir `IVsHierarchy` `IVsSccProject2` . Dosyaları bir projede kaynak denetimi altında veya geçerli kaynak denetimi durumu veya konumu projesine bildirerek almak için kullanılır.|Project|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|Tümleştirme modülü geçerli etkin VSPackage 'ı ayarlamak için bu arabirimi kullanır.|Kaynak denetimi VSPackage|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Bu arabirim bir abonelik modelini temel alır. Herhangi bir VSPackage, belge olaylarını almak istediğini ve gerçekleşmeyi izleyen olaylar üzerinde kabuk önermeyi işaret edebilir. Tarafından uygulanır ve işlenir; [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Bu, ' de ' i uygulayan olayları `IVsTrackProjectDocumentsEvents2` VSPackage 'a geçirir.|Kaynak denetimi saplaması|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Bu arabirim toplu işleme, eşitlenen okuma/yazma işlemleri ve gelişmiş bir yöntem sağlar `OnQueryAddFiles` .|Kaynak denetimi saplaması|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Çözüm Gezgini** ve projeleri projelere yeni dosyalar eklendiğinde veya dosyalar ve klasörler yeniden adlandırıldığında veya projelerden silindiğinde bu arabirimi çağırır. Kaynak denetimi VSPackage proje dosyasını kullanıma alabilir veya işlemi iptal edebilir.|Kaynak denetimi VSPackage|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Çözüm Gezgini** ve projeleri, IVstrackProjectDocuments3 arabiriminin yöntemlerine yapılan çağrılara yanıt olarak bu arabirimi çağırır. Kaynak denetimi VSPackage toplu işlemleri izleyebilir, okuma/yazma işlemlerini eşitler ve daha gelişmiş bir `OnQueryAddFiles` yöntemle çalışır.|Kaynak denetimi VSPackage|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Bu arabirim, Web projeleri için kayıt yönetimi desteği sağlar.|Kaynak denetimi VSPackage|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Bu arabirim, projelerdeki kaynak denetimli dosyalar için araç Ipuçlarını almak için kullanılır.|Kaynak denetimi VSPackage|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Bu arabirim, ad alanı uzantısı desteği sağlar.|Kaynak denetimi VSPackage|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage, bir ad alanı uzantısını **Yeni**, **Aç**veya **Kaydet** iletişim kutularıyla bütünleştirmek için bu arabirimi kullanır. Sonuç olarak, projeler oluşturma sırasında kaynak denetimine otomatik olarak eklenebilir veya bir Kaydet işlemi etkin olduğunda kaynak denetimine eklenebilir.|Kaynak denetimi VSPackage|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage, **Çözüm Gezgini**içindeki düğümler için kaynak denetim glifleri olarak ek Glifler tanımlamak üzere bu arabirimi kullanır.|Kaynak denetimi VSPackage|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|Web projeleri için **Ekle** iletişim kutusu bu arabirimi kullanır. Kaynak denetim konumuna göz atmak ve bu konumdaki kaynak denetim deposuna daha önce eklenmiş bir Web projesini açmak için yöntemler sağlar.|Kaynak denetimi VSPackage|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Bu arabirim, kaynak denetiminden projelerin zaman uyumsuz (arka plan) yüklemesi için destek sağlar.|Kaynak denetimi VSPackage|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Bu arabirim, projelerin tarafından başlatılan zaman uyumsuz yüklemenin ilerlemesini izlemesini sağlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> .|Project|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Bu arabirim, IDE 'nin etkin kaynak denetimi VSPackage 'ı sorgulamasını sağlar. IDE, etkin kaynak denetimi VSPackage kaydı olmadığında bile anlamı olan kaynak denetimi ayarlarının değerini sorgular. Bu arabirim tarafından uygulanır ve işlenir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .|Kaynak denetimi saplaması|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Bu arabirim, kaynak denetimi VSPackage kaydı sırasında kullanılır.|Kaynak denetimi saplaması|Gerekli|  
|<xref:EnvDTE.SourceControl>|Bu arabirim Otomasyon 'da kullanılır. Bu nedenle, yalnızca herhangi bir kullanıcı arabirimi görüntülenmeden yürütülebilecek işlevleri kullanıma sunar.|Kaynak denetimi VSPackage|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Bu arabirim, kaynak denetimi ayarlarını çözüm (. sln) dosyasına kaydetmek için kullanılır. Ayarlar, kaynak denetim konumu ve kaynak denetimi durum bayraklarını içerir.|Kaynak denetimi VSPackage|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Bu arabirim, kaynak denetimi ayarlarını çözüm seçenekleri (. suo) dosyasına kaydetmek için kullanılır. Bu, geçerli kullanıcının kayıt konumu gibi kullanıcıya özgü kaynak denetimi ayarlarını içerebilir.|Kaynak denetimi VSPackage|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Bu arabirim, çözümleri kapatmadan önce proje dosyalarını iade etme ya da bir projeyi açarken kaynak denetiminden yeni dosya alma gibi işlemleri gerçekleştirmek için olayları izlemek üzere kullanılır.|Kaynak denetimi VSPackage|Önerilen|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
