---
title: 'Hata: IIS Yönetici hizmeti yanıt vermediğinden bir güvenlik denetimi başarısız oldu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65eb724d14123292a0694623bf46859f8a3966f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197083"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Hata: IIS Yönetici Hizmeti Yanıt Vermediğinden Güvenlik Denetimi Başarısız
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hata, IIS Yönetim hizmeti yanıt vermezse oluşur. Bu, genellikle IIS yüklemesiyle ilgili bir sorun olduğunu gösterir. İlk olarak, hizmetin **yönetim araçlarından** **Hizmetler** aracını kullanarak çalıştığını doğrulayın.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- **Program Ekle veya Kaldır** denetim MASASıNı kullanarak IIS 'yi yeniden yükleyin.  
  
- -veya-  
  
- Program Ekle veya Kaldır denetim masasını kullanarak IIS 'yi makinenizden kaldırın. IIS 'yi kaldırdıysanız ve sorun yaşamaya devam ediyorsanız, kayıt defterini denetleyin ve bu anahtarın artık mevcut olmadığından emin olun:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     -veya-  
  
- Yönetim Araçları denetim masasını kullanarak IIS Yönetim hizmetini devre dışı bırakın. Bu, makinenizde IIS 'yi devre dışı bırakır.  
  
     Bu üç adımdan herhangi birini gerçekleştirdikten sonra makinenizi yeniden başlatın.  
  
     Daha fazla bilgi için bkz. IIS belgeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
