---
title: VSPackage yapısı (kaynak denetimi VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08bb0a296daca0de1c02b905a75fb10ce05f254e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206005"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage Yapısı (Kaynak Denetimi VSPackage’ı)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetim paketi SDK 'Sı, kaynak denetimi uygulayıcısı ile ortamla tümleştirilmesine izin veren bir VSPackage oluşturmaya yönelik yönergeler sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . VSPackage, genellikle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kayıt defteri girişlerinde paketin tanıtıldığı hizmetlere bağlı olarak tümleşik geliştirme ortamı (IDE) tarafından isteğe bağlı olarak yüklenen BIR COM bileşenidir. Her VSPackage öğesini uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . VSPackage genellikle IDE tarafından sunulan hizmetleri kullanır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve bunların belirli hizmetlerini temin etmek için kullanılır.  
  
 VSPackage, menü öğelerini bildirir ve. vsct dosyası aracılığıyla varsayılan bir öğe durumu oluşturur. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE, VSPackage yükleninceye kadar bu durumdaki menü öğelerini görüntüler. Daha sonra, VSPackage 'ın <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi, menü öğelerini etkinleştirmek veya devre dışı bırakmak için çağrılır.  
  
## <a name="source-control-package-characteristics"></a>Kaynak denetimi paket özellikleri  
 Kaynak denetimi VSPackage, ile arasında daha fazla tümleştirilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 VSPackage semantiği şunları içerir:  
  
- VSPackage (arabirim) olarak sanallaştırılan tarafından uygulanacak arabirim `IVsPackage`  
  
- UI komut uygulama (. vsct dosyası ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimin uygulanması)  
  
- İle VSPackage kaydı [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
  Kaynak denetimi VSPackage bu diğer varlıklarla iletişim kurmalıdır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] :  
  
- Projeler  
  
- Düzenleyiciler  
  
- Çözümler  
  
- Windows  
  
- Çalışan belge tablosu  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Tüketilen Visual Studio ortam hizmetleri  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Svsregistersccıprovider hizmeti  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>Uygulanan ve çağrılan VSıP arabirimleri  
 Kaynak denetim paketi bir VSPackage ve bu nedenle, ile kaydedilen diğer VSPackages ile doğrudan etkileşime girebilirler [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Kaynak denetimi işlevselliğinin tam kapsamını sağlamak için, bir kaynak denetimi VSPackage, projeler veya kabuğun sağladığı arabirimlerle ilgilenebilirler.  
  
 İçindeki her proje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> IDE içinde proje olarak tanınmak için öğesini uygulamalıdır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Ancak, bu arabirim kaynak denetimi için yeterince uzmanlaşmış değildir. Kaynak denetimi altında olması beklenen projeler öğesini uygular <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Bu arabirim, bir projeyi içerikleri için sorgulamak ve BT glifleri ile bağlama bilgilerini sağlamak için kaynak denetimi VSPackage tarafından kullanılır (sunucu konumu ve kaynak denetimi altındaki bir projenin disk konumu arasında bir bağlantı kurmak için gereken bilgiler).  
  
 Kaynak denetimi VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> öğesini uygular, bu da projelerin kaynak denetimine kaydolmasını ve durum gliflerinden alınmasını sağlar.  
  
 Bir kaynak denetimi VSPackage 'ın göz önünde bulundurmanız gereken arabirimlerin tüm listesi için bkz. [Ilgili hizmetler ve arabirimler](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tasarım öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [İlgili Hizmetler ve Arabirimler](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
