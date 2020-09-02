---
title: 'Hata Ayıklama Hazırlığı: ASP.NET Web uygulamaları | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a80587062442688551d07128a2cec49a712adf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691456"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Hata Ayıklama Hazırlığı: ASP.NET Web Uygulamaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Web sitesi şablonu bir Web form uygulaması oluşturur. Bu şablonu kullanarak bir Web sitesi oluşturduğunuzda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata ayıklama için varsayılan ayarları oluşturur. **Proje özellikleri** iletişim kutusunda, Web sayfasının bir başlangıç sayfası olmasını isteyip istemediğinizi belirtebilirsiniz. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Bu varsayılan ayarlarla bir Web sitesinde hata ayıklamaya başladığınızda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Internet Explorer 'ı başlatır ve hata ayıklayıcıyı [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işleme iliştirir (aspnet_wp.exe veya w3wp.exe). Daha fazla bilgi için, bkz. [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Web Forms uygulaması oluşturmak için  
  
1. **Dosya** menüsünde **Yeni Web sitesi**' ni seçin.  
  
2. **Yeni Web sitesi** iletişim kutusunda [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **Web sitesi**' ni seçin.  
  
3. **Tamam**’a tıklayın.  
  
### <a name="to-debug-your-web-form"></a>Web formunuzda hata ayıklamak için  
  
1. İşlevleriniz ve olay İşleyicileriniz içindeki bir veya daha fazla kesme noktası ayarlayın.  
  
     Daha fazla bilgi için bkz. [kesme noktaları ve Izleme noktaları](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Bir kesme noktası isabet edildiğinde, işlevin içindeki kodla adım adım ilerleyin. Sorunu yalıtana kadar kodunuzun yürütülmesini gözlemleyin.  
  
     Daha fazla bilgi için bkz [Stepping](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) . [Web uygulamalarını ve betiği atlama ve hata ayıklama](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Varsayılan yapılandırma değiştirme  
 Tarafından oluşturulan varsayılan hata ayıklama ve sürüm yapılandırmasını değiştirmek istiyorsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bunu yapabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama ve yayın yapılandırmasını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Varsayılan hata ayıklama yapılandırmasını değiştirmek için  
  
1. **Çözüm Gezgini**' de, Web sitesine sağ tıklayın ve **Özellik sayfaları ' nı seçerek** **Özellik sayfaları** iletişim kutusunu açın.  
  
2. **Başlangıç seçenekleri**' ne tıklayın.  
  
3. İlk olarak görüntülenecek Web sayfasına **Başlangıç eylemini** ayarla.  
  
4. Hata **ayıklayıcılar**altında **ASP.NET hata ayıklamanın** seçili olduğundan emin olun.  
  
     Daha fazla bilgi için bkz. [Web projeleri Için özellik sayfaları ayarları](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [Hata ayıklayıcı temelleri](../debugger/debugger-basics.md)   
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
