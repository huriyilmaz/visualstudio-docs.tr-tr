---
title: 'Hata: uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi farklı bir kullanıcı olarak çalışıyor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dffaafbca80828a7501f5f7d24e525225284f5a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697306"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Hata: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi farklı kullanıcı olarak çalışıyor.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzaktan hata ayıklama yapmaya çalışırken, aşağıdaki hata iletisini alabilirsiniz:  
  
 Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi farklı bir kullanıcı olarak çalışıyor.  
  
## <a name="cause"></a>Nedeni  
 Bu ileti, kimlik doğrulama modunda hata ayıklarken ve msvsmon Başlatan Kullanıcı Visual Studio çalıştıran kullanıcı olmadığında oluşur.  
  
## <a name="solution"></a>Çözüm  
 En güvenli ve en iyi çözüm, Uzaktan Hata Ayıklama İzleyicisi (msvsmon.exe) Visual Studio ile aynı kullanıcı hesabı altında çalıştırmaktır. Bunu yapmazsanız, Uzaktan Hata Ayıklama İzleyicisi **seçenekleri** iletişim kutusunda **herhangi bir kullanıcının hata ayıklamasına izin ver** seçeneğiyle diğer hesap altında uzaktan hata ayıklama İzleyicisi çalıştırabilirsiniz.  
  
> [!CAUTION]
> Diğer kullanıcıların bağlanmasına izin verilmesi, yanlışlıkla yanlış uzaktan hata ayıklama oturumuna bağlanma olasılığa izin verir. **Kimlik doğrulama** modunda hata ayıklama hiçbir şekilde güvende değildir ve dikkatli kullanılmalıdır.  
  
 Daha fazla bilgi için bkz. [Uzaktan hata ayıklama İzleyicisi başlatma](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
