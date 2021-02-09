---
title: Web sitesi destek öznitelikleri | Microsoft Docs
description: Web sitesi projelerini kullanarak Visual Studio 'nun işlevselliğini genişletmek için gerekli olan Web sitesi destek öznitelikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 452760974207c4ad30e18dd0c4917bcf7b7aa55d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886840"
---
# <a name="web-site-support-attributes"></a>Web Sitesi Destek Öznitelikleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Web sitesi projesi, Web programlama dilleri için destek sağlamak üzere genişletilebilir. Dil [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seçildiğinde proje şablonlarının **Yeni Web sitesi** iletişim kutusunda görünebilmesi için dilin kendisini ile kaydetmesi gerekir.

IronPython Studio örneği, Web sitesi desteğini içerir. Örnek, IronPython 'u yeni Web projeleri için bir codebehind dili olarak kaydettirmek üzere aşağıdaki öznitelik sınıflarını içerir.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Bu öznitelik, dil projesine yerleştirilir. Dili Web programlama dilleri listesine **Yeni Web sitesi** Iletişim kutusunda **dil** listesinde ekler. Örneğin, aşağıdaki kod, listeye IronPython ekler:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Bu öznitelik, şablonlar klasörünü işaret etmek için şablon yolunu da ayarlar. Şablonlar klasörünün konumu hakkında daha fazla bilgi için bkz. [Web sitesi destek şablonları](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Bu öznitelik, dil projesine yerleştirilir. Web sitesi projesinin, **Çözüm Gezgini** başka bir dosya türü (birincil) altına bir dosya türünü (ilişkili) iç içe almasına izin verir.

 Örneğin, aşağıdaki kod bir IronPython codebehind dosyasının bir. aspx dosyasıyla ilişkili olduğunu belirtir. IronPython Web sitesi çözümünde yeni bir. aspx Web sayfası oluşturulduğunda, yeni bir. Kopyala kaynak dosyası oluşturulur ve. aspx sayfasının alt düğümü olarak görüntülenir.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>Provideıntellisenseproviderattribute
 Bu öznitelik, dil proje paketine yerleştirilir. Dil için IntelliSense sağlayıcısını seçer.

 Örneğin, aşağıdaki kod, bir PythonIntellisenseProvider örneğinin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> dil hizmetleri sağlamak için isteğe bağlı olarak oluşturulması gerektiğini belirtir.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Kod içeren bir Web sayfası istendiğinde ancak önbelleğe alınmadığında, IVsIntellisenseProject uygulamasının başvuruları işler ve dil derleyicisini çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Sitesi Desteği](../../extensibility/internals/web-site-support.md)
