---
title: Web sitesi destek öznitelikleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07486ea3a962bcb81f65ad0b61ea2e41b3248678
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721605"
---
# <a name="web-site-support-attributes"></a>Web Sitesi Destek Öznitelikleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Web sitesi projesi, Web programlama dilleri için destek sağlamak üzere genişletilebilir. Dil seçildiğinde proje şablonlarının **Yeni Web sitesi** iletişim kutusunda görünebilmesi için dilin kendisini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaydetmesi gerekir.

IronPython Studio örneği, Web sitesi desteğini içerir. Örnek, IronPython 'u yeni Web projeleri için bir codebehind dili olarak kaydettirmek üzere aşağıdaki öznitelik sınıflarını içerir.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Bu öznitelik, dil projesine yerleştirilir. Dili Web programlama dilleri listesine **Yeni Web sitesi** Iletişim kutusunda **dil** listesinde ekler. Örneğin, aşağıdaki kod, listeye IronPython ekler:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Bu öznitelik, şablonlar klasörünü işaret etmek için şablon yolunu da ayarlar. Şablonlar klasörünün konumu hakkında daha fazla bilgi için bkz. [Web sitesi destek şablonları](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Bu öznitelik, dil projesine yerleştirilir. Web sitesi projesinin, **Çözüm Gezgini**başka bir dosya türü (birincil) altına bir dosya türünü (ilişkili) iç içe almasına izin verir.

 Örneğin, aşağıdaki kod bir IronPython codebehind dosyasının bir. aspx dosyasıyla ilişkili olduğunu belirtir. IronPython Web sitesi çözümünde yeni bir. aspx Web sayfası oluşturulduğunda, yeni bir. Kopyala kaynak dosyası oluşturulur ve. aspx sayfasının alt düğümü olarak görüntülenir.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>Provideıntellisenseproviderattribute
 Bu öznitelik, dil proje paketine yerleştirilir. Dil için IntelliSense sağlayıcısını seçer.

 Örneğin, aşağıdaki kod, dil hizmetleri sağlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> uygulayan bir PythonIntellisenseProvider örneğinin oluşturulması gerektiğini belirtir.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Kod içeren bir Web sayfası istendiğinde ancak önbelleğe alınmadığında, IVsIntellisenseProject uygulamasının başvuruları işler ve dil derleyicisini çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Sitesi Desteği](../../extensibility/internals/web-site-support.md)