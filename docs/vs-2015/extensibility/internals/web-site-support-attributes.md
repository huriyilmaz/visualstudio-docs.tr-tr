---
title: Web sitesi destek öznitelikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75401eb0d5acd5d363d05aec57909eef5b9855e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144304"
---
# <a name="web-site-support-attributes"></a>Web Sitesi Destek Öznitelikleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Web sitesi projesi, Web programlama dilleri için destek sağlamak üzere genişletilebilir. Dil [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] seçildiğinde proje şablonlarının **Yeni Web sitesi** iletişim kutusunda görünebilmesi için dilin kendisini ile kaydetmesi gerekir.  
  
 IronPython Studio örneği, Web sitesi desteğini içerir. Bu dosyayı [VSSDK örnekleri](../../misc/vssdk-samples.md)ile bulabilirsiniz. Bu, IronPython 'u yeni Web projeleri için bir codebehind dili olarak kaydettirmek üzere aşağıdaki öznitelik sınıflarını içerir.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Bu öznitelik, dil projesine yerleştirilir. Dili Web programlama dilleri listesine **Yeni Web sitesi** Iletişim kutusunda **dil** listesinde ekler. Örneğin, aşağıdaki listeye IronPython ekler:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Bu öznitelik, şablonlar klasörünü işaret etmek için şablon yolunu da ayarlar. Şablonlar klasörünün konumu hakkında daha fazla bilgi için bkz. [Web sitesi destek şablonları](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Bu öznitelik, dil projesine yerleştirilir. Web sitesi projesinin, **Çözüm Gezgini**başka bir dosya türü (birincil) altına bir dosya türünü (ilişkili) iç içe almasına izin verir.  
  
 Örneğin:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 bir IronPython codebehind dosyasının bir. aspx dosyasıyla ilişkili olduğunu belirtir. IronPython Web sitesi çözümünde yeni bir. aspx Web sayfası oluşturulduğunda, yeni bir. Kopyala kaynak dosyası oluşturulur ve. aspx sayfasının alt düğümü olarak görüntülenir.  
  
## <a name="provideintellisenseproviderattribute"></a>Provideıntellisenseproviderattribute  
 Bu öznitelik, dil proje paketine yerleştirilir. Dil için IntelliSense sağlayıcısını seçer.  
  
 Örneğin:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 bir PythonIntellisenseProvider örneğinin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> dil hizmetleri sağlamak için isteğe bağlı olarak oluşturulması gerektiğini belirtir.  
  
 IVsIntellisenseProject uygulama, kod içeren bir Web sayfası istendiğinde ancak önbelleğe alınmadığında, başvuruları işler ve dil derleyicisini çağırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Sitesi Desteği](../../extensibility/internals/web-site-support.md)
