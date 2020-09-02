---
title: Web sitesi desteği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a96504783de466551c6fb9d055b95ba38df760
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687687"
---
# <a name="web-site-support"></a>Web Sitesi Desteği
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Web sitesi proje sistemi, Web projeleri oluşturan bir proje sistemidir. Web projeleri Web uygulamaları oluşturur. Bir Web sitesi projesi, ilişkili kodu olan her bir Web sayfası için bir yürütülebilir dosya oluşturur. Ek yürütülebilir dosyalar/App_Code klasöründeki kaynak kod dosyalarından oluşturulur.  
  
 Web sitesi proje sistemleri, var olan bir proje sistemine şablonlar ve kayıt öznitelikleri eklenerek oluşturulur. Bu özniteliklerden biri, dilin IntelliSense sağlayıcısını seçer. IntelliSense sağlayıcı uygulama, önbelleğe alınan bir akıllı Web sayfası istendiğinde, başvuruları işler ve dil derleyicisini çağırır.  
  
 Web sayfalarını derlemek için kullanılan dil derleyicisinin ile kayıtlı olması gerekir [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Aşağıdaki örnekte olduğu gibi, derleyicisini kaydetmek için bir Web.config dosyasındaki [ \<compiler> öğesini](https://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) kullanabilirsiniz:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Web Sitesi Destek Şablonları](../../extensibility/internals/web-site-support-templates.md)  
 Yeni Web sitesi projeleri ve ilişkili öğeler oluşturmak için kullanabileceğiniz şablonları listeler.  
  
 [Web Sitesi Destek Öznitelikleri](../../extensibility/internals/web-site-support-attributes.md)  
 Bir Web sitesi projesini ve ' a bağlayan kayıt özniteliklerini gösterir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] .  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Web Projeleri](../../extensibility/internals/web-projects.md)  
 İki tür web projesine, Web sitesi projelerine ve Web uygulaması projelerine genel bir bakış sunar.
