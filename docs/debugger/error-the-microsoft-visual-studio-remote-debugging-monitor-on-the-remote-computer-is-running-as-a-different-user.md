---
title: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi farklı kullanıcı olarak çalışıyor
titleSuffix: ''
description: Bu ileti, kimlik doğrulama modunda hata ayıklarken ve msvsmon Başlatan Kullanıcı Visual Studio çalıştıran kullanıcı olmadığında oluşur.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cee8ea9442ab88c280a11a0b73d74cac6888e9f9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146710"
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
- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
