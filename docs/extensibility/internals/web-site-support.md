---
title: Web sitesi desteği | Microsoft Docs
description: Mevcut bir proje sistemine şablonlar ve kayıt öznitelikleri eklenerek oluşturulan Web sitesi proje sistemleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 16de0fdc2c4e65dfe6c2ae2c6dc3cdc6902fa8b0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069120"
---
# <a name="web-site-support"></a>Web Sitesi Desteği
Web sitesi proje sistemi, Web projeleri oluşturan bir proje sistemidir. Web projeleri Web uygulamaları oluşturur. Bir Web sitesi projesi, ilişkili kodu olan her bir Web sayfası için bir yürütülebilir dosya oluşturur. Ek yürütülebilir dosyalar/App_Code klasöründeki kaynak kod dosyalarından oluşturulur.

 Web sitesi proje sistemleri, var olan bir proje sistemine şablonlar ve kayıt öznitelikleri eklenerek oluşturulur. Bu özniteliklerden biri, dilin IntelliSense sağlayıcısını seçer. IntelliSense sağlayıcı uygulama, önbelleğe alınan bir akıllı Web sayfası istendiğinde, başvuruları işler ve dil derleyicisini çağırır.

 Web sayfalarını derlemek için kullanılan dil derleyicisinin ile kayıtlı olması gerekir [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] . Aşağıdaki örnekte olduğu gibi, derleyicisini kaydetmek için bir Web.config dosyasındaki [ \<compiler> öğesini](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) kullanabilirsiniz:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>Bu Bölümde
- [Web Sitesi Destek Şablonları](../../extensibility/internals/web-site-support-templates.md)

 Yeni Web sitesi projeleri ve ilişkili öğeler oluşturmak için kullanabileceğiniz şablonları listeler.

- [Web Sitesi Destek Öznitelikleri](../../extensibility/internals/web-site-support-attributes.md)

 Bir Web sitesi projesini ve ' a bağlayan kayıt özniteliklerini gösterir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] .

## <a name="related-sections"></a>İlgili Bölümler
- [Web Projeleri](../../extensibility/internals/web-projects.md)

 İki tür web projesine, Web sitesi projelerine ve Web uygulaması projelerine genel bir bakış sunar.
