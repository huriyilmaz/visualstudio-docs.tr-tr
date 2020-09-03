---
title: Hata-uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi farklı bir kullanıcı olarak çalışıyor
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a69745a051af0ec44eb813054e40fb9f6c6a0aa6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460409"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Hata: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi farklı kullanıcı olarak çalışıyor.
Uzaktan hata ayıklama yapmaya çalışırken, aşağıdaki hata iletisini alabilirsiniz:

 Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi farklı bir kullanıcı olarak çalışıyor.

## <a name="cause"></a>Nedeni
 Bu ileti, kimlik doğrulama modunda hata ayıklarken ve msvsmon Başlatan Kullanıcı Visual Studio çalıştıran kullanıcı olmadığında oluşur.

## <a name="solution"></a>Çözüm
 En güvenli ve en iyi çözüm, Uzaktan Hata Ayıklama İzleyicisi (msvsmon.exe) Visual Studio ile aynı kullanıcı hesabı altında çalıştırmaktır. Bunu yapmazsanız, Uzaktan Hata Ayıklama İzleyicisi **seçenekleri** iletişim kutusunda **herhangi bir kullanıcının hata ayıklamasına izin ver** seçeneğiyle diğer hesap altında uzaktan hata ayıklama İzleyicisi çalıştırabilirsiniz.

> [!CAUTION]
> Diğer kullanıcıların bağlanmasına izin verilmesi, yanlışlıkla yanlış uzaktan hata ayıklama oturumuna bağlanma olasılığa izin verir. **Kimlik doğrulama** modunda hata ayıklama hiçbir şekilde güvende değildir ve dikkatli kullanılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)