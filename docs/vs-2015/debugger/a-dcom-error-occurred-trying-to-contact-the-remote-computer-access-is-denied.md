---
title: Uzak bilgisayara erişilmeye çalışılırken DCOM hatası oluştu. Erişim reddedildi. | Microsoft Belgeleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0157b1ade2c38a2c10920b9674d7c9a58ac036b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156525"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Uzak bilgisayara erişilmeye çalışılırken DCOM hatası oluştu. Erişim reddedildi.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzaktan hata ayıklama, aşağıdaki durumlarda yerel ve uzak bilgisayarlar arasında iletişim kurmak için DCOM kullanır:  
  
- Hata ayıklayıcı **Yerel uyumluluk moduna** ayarlanır veya **yönetilen uyumluluk modu** **Araçlar/Seçenekler/hata ayıklama** sayfasında denetlenir  
  
- Yönetilen C++ (C++/CLı) kodunda hata ayıklaması yapıyorsanız.  
  
- Visual Studio 2013 ' de, **Yerel Düzenle ve devam et etkinleştir** ' de **Araçlar/Seçenekler/hata ayıklama** sayfasında işaretlenir  
  
- Bazı üçüncü taraf hata ayıklama senaryoları  
  
  Bu hata, Visual Studio işleminin kimlik doğrulaması yapamadığında (veya sağlanan kimlik bilgileri yetersiz olduğu kabul edildiğinde) DCOM üzerinden uzaktan hata ayıklayıcı işlemi için oluşur. Aşağıdaki geçici çözümlerden biri veya birkaçı sorunu çözebilir:  
  
- **Yerel uyumluluk modunu** ve **yönetilen uyumluluk modunu**kapatın.  
  
- Visual Studio 2013, **yerel düzenlemeyi etkinleştir ve devam et**' i kapatın.  
  
- Her iki bilgisayarı da yeniden başlatın.  
  
- Uzaktan hata ayıklama kimlik bilgilerini girmeyi gerektiriyorsa, kimlik bilgilerini kaydetme seçeneğini işaretleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
