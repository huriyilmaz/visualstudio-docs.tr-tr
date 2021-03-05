---
description: Uzak makinedeki Internet bağlantısı güvenlik duvarı, uzaktan hata ayıklamaya izin verecek şekilde ayarlanmadı.
title: Kimlik doğrulaması olmayan güvenlik duvarı | Microsoft Docs
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
ms.workload:
- multiple
ms.openlocfilehash: 2bb46b09af4f87ac93fd7001ff1de02a782ae263
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146996"
---
# <a name="error-firewall-no-authentication"></a>Hata: Güvenlik Duvarı Kimlik Doğrulaması Yok
Uzak makinedeki Internet bağlantısı güvenlik duvarı, uzaktan hata ayıklamaya izin verecek şekilde ayarlanmadı. Uzaktan hata ayıklama için `No Authentication` , msvsmon.exe özel durumlar listesine eklenmelidir. Bazı ıPSEC bağlantı noktalarının açılması de gerekebilir.

> [!NOTE]
> Uzaktan hata ayıklayıcı Windows güvenlik duvarını otomatik olarak yapılandırabiliyor. Üçüncü taraf yazılım güvenlik duvarı veya bir donanım güvenlik duvarı gibi Windows Güvenlik Duvarı dışında bir güvenlik duvarı kullanırken, uzaktan hata ayıklamaya izin verecek şekilde güvenlik duvarının el ile yapılandırılması gerekir. Bunu yapmak için msvsmon.exe TCP/IP bağlantı noktalarında dinlerken trafiğe izin verin. Varsayılan olarak, bu bağlantı noktası 4018 ve 4019 ' dir; burada 4018 tüm Işletim sistemlerinde kullanılır ve 4019 yalnızca Windows x64 üzerinde, x86 işlemlerine hata ayıklama sağlamak için kullanılır.

 Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).
