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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 398779b06ec74d7c7902eb617aa27b28e9f66d4bcc33651c456436b360acee6f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240097"
---
# <a name="error-firewall-no-authentication"></a>Hata: Güvenlik Duvarı Kimlik Doğrulaması Yok
Uzak makinedeki Internet bağlantısı güvenlik duvarı, uzaktan hata ayıklamaya izin verecek şekilde ayarlanmadı. Uzaktan hata ayıklama için `No Authentication` , msvsmon.exe özel durumlar listesine eklenmelidir. Bazı ıPSEC bağlantı noktalarının açılması de gerekebilir.

> [!NOTE]
> uzaktan hata ayıklayıcı Windows güvenlik duvarını otomatik olarak yapılandırabiliyor. üçüncü taraf yazılım güvenlik duvarı veya bir donanım güvenlik duvarı gibi Windows güvenlik duvarı dışında bir güvenlik duvarı kullanırken, uzaktan hata ayıklamaya izin verecek şekilde güvenlik duvarının el ile yapılandırılması gerekir. Bunu yapmak için msvsmon.exe TCP/IP bağlantı noktalarında dinlerken trafiğe izin verin. varsayılan olarak, bu bağlantı noktası 4018 ve 4019 ' dir; burada 4018 tüm işletim sistemlerinde kullanılır ve 4019 yalnızca Windows x64 üzerinde x86 işlemlerine izin vermek için kullanılır.

 Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).
