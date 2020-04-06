---
title: Web Sitesi Desteği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22047ad1b0709cefa200656e61f8e0d39ace94c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703437"
---
# <a name="web-site-support"></a>Web Sitesi Desteği
Web sitesi proje sistemi, Web projeleri oluşturan bir proje sistemidir. Web projeleri sırayla Web uygulamaları oluşturur. Bir Web sitesi projesi, ilişkili kodu olan her Web sayfası için bir yürütülebilir dosya oluşturur. /App_Code klasöründeki kaynak kod dosyalarından ek yürütülebilir dosyalar oluşturulur.

 Web sitesi proje sistemleri, varolan bir proje sistemine şablonlar ve kayıt öznitelikleri eklenerek oluşturulur. Bu özniteliklerden biri dil için IntelliSense sağlayıcısını seçer. IntelliSense sağlayıcısı uygulaması, önbelleğe alınmayan akıllı bir Web sayfası istendiğinde başvuruları işler ve dil derleyicisini çağırır.

 Web sayfalarını derlemek için kullanılan dil [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]derleyicisi ' ne kaydedilmelidir. [ \<Derleyiciyi](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) aşağıdaki örnekte olduğu gibi, derleyiciyi kaydetmek için web.config dosyasındaki derleyici> Öğesi'ni kullanabilirsiniz:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>Bu Bölümde
- [Web Sitesi Destek Şablonları](../../extensibility/internals/web-site-support-templates.md)

 Yeni Web sitesi projeleri ve ilişkili öğeler oluşturmak için kullanabileceğiniz şablonları listeler.

- [Web Sitesi Destek Öznitelikleri](../../extensibility/internals/web-site-support-attributes.md)

 Bir Web sitesi projesini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].

## <a name="related-sections"></a>İlgili Bölümler
- [Web Projeleri](../../extensibility/internals/web-projects.md)

 İki tür Web projesine, Web sitesi projelerine ve Web uygulama projelerine genel bir bakış sunar.
