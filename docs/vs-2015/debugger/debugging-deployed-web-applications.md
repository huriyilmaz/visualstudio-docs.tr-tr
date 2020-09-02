---
title: Dağıtılmış Web uygulamalarında hata ayıklama | Microsoft Docs
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
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9608643801255d6c2cbf278cbfd96908f1f3911d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64832450"
---
# <a name="debugging-deployed-web-applications"></a>Dağıtılmış Web Uygulamalarında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir üretim sunucusunda çalışan bir Web uygulamasında hata ayıklaması yapmanız gerekiyorsa, bu, dikkatli bir şekilde yapılmalıdır. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Hata ayıklama için çalışan işlemine iliştirmiş ve bir kesme noktasına isabet alırsanız (örneğin, çalışan işlemindeki tüm yönetilen kodlar). Çalışan işlemdeki tüm yönetilen kodların kilitlenmesine, sunucudaki tüm kullanıcılar için bir iş durdurma sayfasına neden olabilir. Bir üretim sunucusunda hata ayıklamadan önce, üretim işlerinde olası etkiyi göz önünde bulundurun.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Dağıtılan bir uygulamada hata ayıklamak için kullanmak üzere, çalışan işleme iliştirmeli [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ve hata ayıklayıcının uygulama için simgelere erişimi olduğundan emin olmanız gerekir. Ayrıca, uygulamanın kaynak dosyalarını bulup açmanız gerekir. Daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [nasıl yapılır: ASP.NET işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md)ve [sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
> Birçok [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması, iş mantığını veya diğer yararlı kodu Içeren dll 'lere başvurur. Bu tür bir başvuru, DLL 'yi otomatik olarak yerel bilgisayarınızdan Web uygulamasının sanal dizininin \bin klasörüne kopyalar. Hata ayıklarken, Web uygulamanızın yerel bilgisayarınızdaki kopya değil, DLL 'nin kopyasına başvurduğundan emin olabilirsiniz.  
  
 Çalışan işleme ekleme işlemi, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] başka bir uzak işleme iliştirme ile aynıdır. İliştirdikten sonra, doğru proje açık değilse, uygulama kesildiğinde bir iletişim kutusu görünür. Bu iletişim kutusu, uygulamanın kaynak dosyalarının konumunu sorar. İletişim kutusunda belirttiğiniz dosya adı, Web sunucusundaki hata ayıklama sembollerinde belirtilen dosya adıyla aynı olmalıdır. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Web uygulamalarında ve betikte hata ayıklama](../debugger/debugging-web-applications-and-script.md)   
 [Nasıl yapılır: ASP.NET uygulamaları için hata ayıklamayı etkinleştirme](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Nasıl yapılır: ASP.NET Işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
