---
title: Yerel makinede güvenlik duvarı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b729c3e7e82a13d86aed16dfb52fda6864aa7f9
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852712"
---
# <a name="error-firewall-on-local-machine"></a>Hata: Güvenlik Duvarı Yerel Makinede
Yerel makinedeki, Visual Studio 'Yu çalıştırdığınız makine olan Internet bağlantısı güvenlik duvarı, uzaktan hata ayıklamaya izin verecek şekilde ayarlanmadı. Varsayılan aktarımlarla yönetilen veya yerel uzaktan hata ayıklama için, DCOM trafiği için TCP 135 bağlantı noktasının açılması gerekir. Dosya ve yazıcı paylaşımının açılması gerekir ve devenv.exe özel durumlar listesine eklenmelidir. Bazı ıPSEC bağlantı noktalarının açılması de gerekebilir.

 Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).