---
title: Web Sitesi Destek Öznitelikleri | Microsoft Docs
description: Web sitesi projelerini kullanarak web sitelerinin işlevselliğini genişletmek için gereken web sitesi Visual Studio özniteliklerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fc98f580b8619cb68ccc929b0e529dcead683e68
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041977"
---
# <a name="web-site-support-attributes"></a>Web Sitesi Destek Öznitelikleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Web sitesi projesi, Web programlama dilleri için destek sağlayacak şekilde genişletilmiştir. Dil seçildiğinde proje şablonlarının Yeni Web Sitesi iletişim kutusunda görünmesi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **için** dilin kendisini ile kaydetmesi gerekir.

IronPython Studio örneği web sitesi desteği içerir. Örnek, IronPython'un yeni Web projeleri için bir codebehind dili olarak kaydolması için aşağıdaki öznitelik sınıflarını içerir.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Bu öznitelik dil projesine yerleştirilir. Dili Yeni Web Sitesi iletişim kutusundaki Dil listesinde **Web programlama** dilleri **listesine** ekler. Örneğin, aşağıdaki kod Listeye IronPython ekler:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Bu öznitelik ayrıca şablonlar yolunu templates klasörüne işaret etmek için ayarlar. Şablonlar klasörünün konumu hakkında daha fazla bilgi için bkz. [Web Sitesi Destek Şablonları.](../../extensibility/internals/web-site-support-templates.md)

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Bu öznitelik dil projesine yerleştirilir. Web Sitesi projesinin bir dosya türünü (ilgili) içinde başka bir dosya türü (birincil) altında iç içe **yerleştirmesini Çözüm Gezgini.**

 Örneğin, aşağıdaki kod IronPython codebehind dosyasının bir .aspx dosyasıyla ilişkili olduğunu belirtir. IronPython Web sitesi çözümünde yeni bir .aspx Web sayfası oluşturulduğunda, yeni bir .py kaynak dosyası oluşturulur ve .aspx sayfasının alt düğümü olarak görünür.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Bu öznitelik dil projesi paketine yerleştirilir. Dil için IntelliSense sağlayıcısını seçer.

 Örneğin, aşağıdaki kod dil hizmetleri sağlamak için isteğe bağlı olarak pythonIntellisenseProvider uygulayan bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> örneğinin oluşturul olacağını belirtir.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 IVsIntellisenseProject uygulaması, kod içeren bir Web sayfası istensin ancak önbelleğe alınmazsa başvuruları işler ve dil derleyicisini çağırabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Sitesi Desteği](../../extensibility/internals/web-site-support.md)
