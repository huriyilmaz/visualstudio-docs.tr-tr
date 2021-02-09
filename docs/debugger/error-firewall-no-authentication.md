---
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
ms.openlocfilehash: cdd1b0bc56c0316d3a79cf59f744a7e2b0a2aece
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871617"
---
# <a name="error-firewall-no-authentication"></a>Hata: Güvenlik Duvarı Kimlik Doğrulaması Yok
Uzak makinedeki Internet bağlantısı güvenlik duvarı, uzaktan hata ayıklamaya izin verecek şekilde ayarlanmadı. Uzaktan hata ayıklama için `No Authentication` , msvsmon.exe özel durumlar listesine eklenmelidir. Bazı ıPSEC bağlantı noktalarının açılması de gerekebilir.

> [!NOTE]
> Uzaktan hata ayıklayıcı Windows güvenlik duvarını otomatik olarak yapılandırabiliyor. Üçüncü taraf yazılım güvenlik duvarı veya bir donanım güvenlik duvarı gibi Windows Güvenlik Duvarı dışında bir güvenlik duvarı kullanırken, uzaktan hata ayıklamaya izin verecek şekilde güvenlik duvarının el ile yapılandırılması gerekir. Bunu yapmak için msvsmon.exe TCP/IP bağlantı noktalarında dinlerken trafiğe izin verin. Varsayılan olarak, bu bağlantı noktası 4018 ve 4019 ' dir; burada 4018 tüm Işletim sistemlerinde kullanılır ve 4019 yalnızca Windows x64 üzerinde, x86 işlemlerine hata ayıklama sağlamak için kullanılır.

 Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).