---
title: Veri bağlantılı ActiveX denetiminde hata ayıklama | Microsoft Docs
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
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6945d1ccf72385b4d2fbe76736668e84b804e446
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686749"
---
# <a name="debugging-a-data-bound-activex-control"></a>Veri Bağımlı ActiveX Denetiminde Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir veri kaynağı denetimine bağlanacak bir ActiveX denetimi geliştiriyorsanız, kendi kapsayıcı uygulamanızı oluşturabilir ve bu kapsayıcıyı ActiveX denetiminde hata ayıklamak için kullanabilirsiniz.  
  
 Örneğin, iletişim kutusuna bir iletişim kutusu tabanlı MFC uygulaması oluşturabilir ve veri bağlantılı denetiminizi ve bir veri kaynağı denetimini yerleştirebilirsiniz. Bu MFC uygulamasını, çalışma zamanı testi için ve veri bağlantılı ActiveX denetiminizin hata ayıklaması için kapsayıcı yürütülebilir dosyası olarak kullanabilirsiniz.  
  
## <a name="using-the-test-container"></a>Test kapsayıcısını kullanma  
 Denetim ya da kapsayıcıda çeşitli arabirimleri desteklemek üzere kolayca değiştirebileceğiniz bir kapsayıcı isterseniz, hata ayıklama oturumu için yürütülebilir dosya olarak ActiveX test kapsayıcısını kullanın. Farklı arabirimleri etkinleştirmek için, ActiveX test kapsayıcısında **kapsayıcı** menüsünde **Seçenekler** ' e tıklayın. Daha fazla bilgi için bkz. [Test kapsayıcısı Ile özellikleri ve olayları test etme](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 Hata ayıklarken kapsayıcının kodunu değiştirmeniz gerekiyorsa, kapsayıcının hata ayıklama sürümünü kullanın veya ActiveX test kapsayıcısının hata ayıklama sürümünü kullanın. Daha fazla bilgi için bkz. [tstcon örneği: ActiveX denetimi test kapsayıcısı](https://msdn.microsoft.com/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM ve ActiveX hata ayıklaması](../debugger/com-and-activex-debugging.md)   
 [ActiveX denetimleri](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)
