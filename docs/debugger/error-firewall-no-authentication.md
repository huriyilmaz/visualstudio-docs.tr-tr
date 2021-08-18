---
description: Uzak makinede İnternet Bağlantısı Güvenlik Duvarı uzaktan hata ayıklamaya izin verecek şekilde ayarlanmaz.
title: Güvenlik Duvarı Kimlik Doğrulaması | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7e42a9dd2856c9bee14b480b261231932dc30236
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030959"
---
# <a name="error-firewall-no-authentication"></a>Hata: Güvenlik Duvarı Kimlik Doğrulaması Yok
Uzak makinede İnternet Bağlantısı Güvenlik Duvarı uzaktan hata ayıklamaya izin verecek şekilde ayarlanmaz. ile uzaktan hata ayıklama `No Authentication` msvsmon.exe özel durumlar listesine eklenmiştir. Bazı IPSEC bağlantı noktalarının açılması da gerekebilir.

> [!NOTE]
> Uzaktan hata ayıklayıcı, Güvenlik Duvarı'nı Windows yapılandırabilirsiniz. Üçüncü taraf yazılım güvenlik duvarı veya donanım güvenlik duvarı gibi Windows Güvenlik Duvarı dışında bir güvenlik duvarı kullanırken, güvenlik duvarı uzaktan hata ayıklamaya izin verecek şekilde el ile yapılandırıldı. Bunu yapmak için, dinleyen TCP/IP bağlantı msvsmon.exe trafiğe izin ver. Varsayılan olarak, bunlar 4018 ve 4019 bağlantı noktasıdır; burada 4018 tüm İşletim Sistemlerinde kullanılır ve x86 işlemlerde hata ayıklamaya izin vermek için yalnızca Windows x64'te 4019 kullanılır.

 Daha fazla bilgi için [bkz. Uzaktan Hata Ayıklama.](../debugger/remote-debugging.md)
