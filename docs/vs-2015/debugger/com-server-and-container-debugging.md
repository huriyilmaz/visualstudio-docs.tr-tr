---
title: COM sunucusu ve kapsayıcı hata ayıklaması | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 631b1d35a0878bfc362b03751f35909839c7da19
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161561"
---
# <a name="com-server-and-container-debugging"></a>COM Sunucusunda ve Kapsayıcısında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

COM uygulamaları, programcının doğrudan denetimi dışında çeşitli görevler gerçekleştirir. Dll 'Ler, nesnelerde kullanım sayıları ve Pano işlemlerinde iletişim, beklenmeyen davranışlarla karşılaşabileceğiniz alanlardan yalnızca birkaçı. Bu durumda, ilk adımınız sorunun kaynağını izlemenizde olur.  
  
 Visual Studio hata ayıklayıcı, kapsayıcılar ve sunucular üzerinde ve içinde adımlamayı destekler. Bu, uzak yordam çağrılarında (RPC) adım adım özelliği içerir.  
  
## <a name="debugging-a-com-server-and-container-in-the-same-solution"></a><a name="BKMK_COMServerandContainerintheSameSolution"></a> Aynı çözümde bir COM sunucusunda ve kapsayıcıda hata ayıklama  
 Aynı çözüm içinde iki proje kullanarak bir COM sunucusunda ve kapsayıcıda hata ayıklaması yapabilirsiniz. Her projede uygun kesme noktaları ayarlayın ve hata ayıklayın. Kapsayıcı, bir kesme noktasına isabet eden sunucuya bir çağrı yaptığında, kapsayıcı sunucu kodu dönene kadar bekler (yani, hata ayıklamayı bitirmeden).  
  
 COM kapsayıcısının hata ayıklaması, Standart programda hata ayıklamaya benzer. Bir fark, geri çağırma üreten bir olayda hata ayıkladığınızda (örneğin, kapsayıcı uygulama üzerinde veri sürükleme). Bu durumda, geri arama işlevinde bir kesme noktası ayarlamanız gerekir.  
  
## <a name="debugging-a-server-application-without-container-information"></a><a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Kapsayıcı bilgileri olmadan sunucu uygulamasında hata ayıklama  
 Kapsayıcı uygulamanız için hata ayıklama bilgilerini kullanmak veya istemiyorsanız, sunucu uygulamasında hata ayıklamaya başlamak üç adımlı bir işlemdir:  
  
1. Normal bir uygulama olarak sunucuda hata ayıklamayı başlatın.  
  
2. Kesme noktalarını istediğiniz gibi ayarlayın.  
  
3. Kapsayıcı uygulamasını başlatın.  
  
## <a name="debugging-a-server-and-domain-isolation-sdi-application"></a><a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Sunucu ve etki alanı yalıtımı (SDI) uygulamasında hata ayıklama  
 Bir SDI Sunucu uygulamasında hata ayıklaması yapıyorsanız, `/Embedding` `/Automation` C/C++, C# veya Visual Basic projeleri için *Proje* Özellik sayfaları iletişim kutusundaki **komut satırı bağımsız değişkenleri** özelliğini belirtmeniz gerekir.  
  
 Bu komut satırı bağımsız değişkenleriyle, hata ayıklayıcı sunucu uygulamasını bir kapsayıcıdan başlatılmış gibi başlatabilir. Kapsayıcının Program Yöneticisi 'nden veya dosya yöneticisinden başlatılması, kapsayıcının hata ayıklayıcıda başlatılan sunucu örneğini kullanmasına neden olur.  
  
 *Proje* Özellik sayfaları iletişim kutusuna erişmek için Çözüm Gezgini ' de projenize sağ tıklayın ve ardından kısayol menüsünden Özellikler ' i seçin. Komut satırı bağımsız değişkenleri özelliğini bulmak için yapılandırma özellikleri kategorisini genişletin ve hata ayıklama sayfasına tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM ve ActiveX Hata Ayıklaması](../debugger/com-and-activex-debugging.md)
