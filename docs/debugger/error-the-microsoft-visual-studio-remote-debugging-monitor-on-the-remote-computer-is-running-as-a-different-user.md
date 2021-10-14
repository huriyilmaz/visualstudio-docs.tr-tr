---
title: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi farklı kullanıcı olarak çalışıyor
titleSuffix: ''
description: Bu ileti, Kimlik Doğrulaması Yok modunda hata ayıklarken ve msvsmon'ı başlatan kullanıcı, msvsmon'ı çalıştıran kullanıcı Visual Studio.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a491fee3c58841aafd36933b58f91eee5d6dfa87
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969950"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Hata: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi farklı kullanıcı olarak çalışıyor.
Uzaktan hata ayıklama yapmaya çalışırken, aşağıdaki hata iletisini alabilirsiniz:

 Uzak Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi, farklı bir kullanıcı olarak çalışıyor.

## <a name="cause"></a>Nedeni
 Bu ileti, Kimlik Doğrulaması Yok modunda hata ayıklarken ve msvsmon'ı başlatan kullanıcı, msvsmon'ı çalıştıran kullanıcı Visual Studio.

## <a name="solution"></a>Çözüm
 En güvenli ve en iyi çözüm, Uzaktan Hata Ayıklama İzleyicisi (msvsmon.exe) hesabıyla aynı kullanıcı hesabı altında Visual Studio. Bunu yapamazsanız, Uzaktan Hata Ayıklama İzleyicisi Seçenekler iletişim kutusunda Herhangi bir  kullanıcının hata ayıklamasına izin ver seçeneği seçiliyken diğer hesap altında Uzaktan Hata Ayıklama İzleyicisi **çalıştırabilirsiniz.**

> [!CAUTION]
> Diğer kullanıcılara bağlanma izni vermek, yanlışlıkla yanlış uzaktan hata ayıklama oturumuna bağlanma olasılığını sağlar. Kimlik Doğrulaması Yok **modunda hata** ayıklama hiçbir zaman güvenli değildir ve dikkatli kullanılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
