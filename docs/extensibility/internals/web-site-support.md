---
title: Web Sitesi Destek | Microsoft Docs
description: Mevcut bir proje sistemine şablon ve kayıt öznitelikleri ekleyerek oluşturulan web sitesi proje sistemleri hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3d5a1d8291a304ca1376bd5eba1d24715f162ddb7fe4214a30e48ed663cf5417
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305470"
---
# <a name="web-site-support"></a>Web Sitesi Desteği
Web sitesi proje sistemi, Web projeleri oluşturan bir proje sistemidir. Web projeleri de Web uygulamaları oluşturabilir. Web sitesi projesi, ilişkili kodu olan her Web sayfası için bir yürütülebilir dosya üretir. /App_Code klasöründeki kaynak kod dosyalarından ek yürütülebilir App_Code oluşturulur.

 Web sitesi proje sistemleri, mevcut bir proje sistemine şablonlar ve kayıt öznitelikleri ekleyerek oluşturulur. Bu özniteliklerden biri, dil için IntelliSense sağlayıcısını seçer. IntelliSense sağlayıcısı uygulaması başvuruları işler ve önbelleğe alınmamış bir akıllı Web sayfası isten geldiğinde dil derleyicisini arar.

 Web sayfalarını derlemek için kullanılan dil derleyicisi ile kayıtlı olması [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] gerekir. Aşağıdaki örnekte olduğu [ \<compiler> gibi,](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) Web.config kaydetmek için bir Web.config öğesi kullanabilirsiniz:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>Bu Bölümde
- [Web Sitesi Destek Şablonları](../../extensibility/internals/web-site-support-templates.md)

 Yeni Web sitesi projeleri ve ilişkili öğeler oluşturmak için kullanabileceğiniz şablonları listeler.

- [Web Sitesi Destek Öznitelikleri](../../extensibility/internals/web-site-support-attributes.md)

 Bir Web sitesi projesini ve 'ye bağlamak için kayıt özniteliklerini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] sunar.

## <a name="related-sections"></a>İlgili Bölümler
- [Web Projeleri](../../extensibility/internals/web-projects.md)

 Web sitesi projeleri ve Web uygulaması projeleri olmak için iki tür Web projesine genel bir bakış sunar.
