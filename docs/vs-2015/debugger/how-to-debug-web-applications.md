---
title: 'Nasıl yapılır: Web uygulamalarında hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd3cbbcd740c0f124b8ab4379204a9d425cd541c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205396"
---
# <a name="how-to-debug-web-applications"></a>Nasıl Yapılır: Web Uygulamalarında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , ' de Web uygulamaları geliştirmeye yönelik birincil teknolojidir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Hata ayıklayıcı, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamalarında yerel olarak veya uzak bir sunucuda hata ayıklama için güçlü araçlar sağlar. Bu konu, geliştirme sırasında bir projenin hatalarını ayıklama işlemini açıklar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Bir üretim sunucusuna zaten dağıtılmış bir Web uygulamasının hatalarını ayıklama hakkında bilgi için bkz. [Dağıtılmış Web uygulamalarında hata ayıklama](../debugger/debugging-deployed-web-applications.md).  
  
 Bir uygulamada hata ayıklamak için [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] :  
  
- Gerekli izinlere sahip olmanız gerekir. Daha fazla bilgi için, bkz. [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]**proje özelliklerinde**hata ayıklama etkinleştirilmelidir.  
  
- Uygulamanızın yapılandırma dosyası (Web.config) hata ayıklama moduna ayarlanmalıdır. Hata ayıklama modu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] dinamik olarak oluşturulan dosyalar için semboller oluşturulmasına neden olur ve hata ayıklayıcının uygulamaya iliştirmesine olanak sağlar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projenizi web projeleri şablonundan oluşturduysanız, hata ayıklamaya başladığınızda bunu otomatik olarak ayarlar.  
  
- Daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET uygulamaları Için hata ayıklamayı etkinleştirme](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Geliştirme sırasında bir Web uygulamasında hata ayıklamak için  
  
1. **Hata Ayıkla** menüsünde, Web uygulamasında hata ayıklamaya başlamak için **Başlat** ' a tıklayın.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Web uygulaması projesini oluşturur, gerekirse uygulamayı dağıtır, yerel olarak hata ayıklaması yapıyorsanız ASP.NET geliştirme sunucusunu başlatır ve [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemine ekler.  
  
2. Herhangi bir uygulama için yaptığınız gibi kesme noktalarını ayarlamak ve temizlemek, adımı ve diğer hata ayıklama işlemlerini gerçekleştirmek için hata ayıklayıcıyı kullanın.  
  
     Daha fazla bilgi için bkz. [hata ayıklayıcı temelleri](../debugger/debugger-basics.md).  
  
3. **Hata ayıklama menüsünde hata** ayıklamayı **Durdur** ' a tıklayarak hata ayıklama oturumunu sonlandırın veya Internet Explorer 'daki **Dosya** menüsünde **Kapat**' a tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web uygulamalarında ve betikte hata ayıklama](../debugger/debugging-web-applications-and-script.md)   
 [ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Nasıl Yapılır: ASP.NET Uygulamaları için Hata Ayıklamayı Etkinleştirme](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
