---
title: Web Sitesi Destek Özellikleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef75f99480145475278357a552f3ac74c0289800
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703492"
---
# <a name="web-site-support-attributes"></a>Web Sitesi Destek Öznitelikleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Web sitesi projesi, Web programlama dilleri için destek sağlamak için genişletilebilir. Dil seçildiğinde proje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] şablonlarının **Yeni Web Sitesi** iletişim kutusunda görünebilmeleri için dilin kendisini kaydetmesi gerekir.

IronPython Studio örneği web sitesi desteği içerir. Örnek, IronPython'u yeni Web projeleri için kod arkasında bir dil olarak kaydetmek için aşağıdaki öznitelik sınıflarını içerir.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Bu öznitelik dil projesine yerleştirilir. **Dili Yeni Web Sitesi** iletişim kutusundaki **Dil** listesindeki Web programlama dilleri listesine ekler. Örneğin, aşağıdaki kod ironpython'u listeye ekler:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Bu öznitelik, şablonlar klasörünü işaret etmek için şablonlar yolunu da ayarlar. Şablonlar klasörünün konumu hakkında daha fazla bilgi için [Web Sitesi Destek Şablonları'na](../../extensibility/internals/web-site-support-templates.md)bakın.

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Bu öznitelik dil projesine yerleştirilir. Web Sitesi projesinin Çözüm Gezgini'nde bir dosya türünü (ilgili) **Solution Explorer**başka bir dosya türü (birincil) altında yerleştirmesine olanak tanır.

 Örneğin, aşağıdaki kod, bir IronPython codebehind dosyasının bir .aspx dosyasıyla ilişkili olduğunu belirtir. Bir IronPython Web sitesi çözümünde yeni bir .aspx Web sayfası oluşturulduğunda, yeni bir .py kaynak dosyası oluşturulur ve .aspx sayfasının alt düğümü olarak görüntülenir.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseSağlayıcıAttribute
 Bu öznitelik dil proje paketine yerleştirilir. Dil için IntelliSense sağlayıcısını seçer.

 Örneğin, aşağıdaki kod, <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>dil hizmetleri sağlamak için isteğe bağlı olarak pythonintellisenseProvider bir örneği oluşturulması gerektiğini belirtir.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 IVsIntellisenseProject uygulaması referansları işler ve kodlu bir Web sayfası istendiğinde ancak önbelleğe alınmıyorsa dil derleyicisini çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Sitesi Desteği](../../extensibility/internals/web-site-support.md)
