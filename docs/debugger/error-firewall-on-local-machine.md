---
title: Hata-yerel makinede güvenlik duvarı | Microsoft Docs
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
ms.openlocfilehash: 115546a0fd3a9aad804391816ce8bac88429d0ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460758"
---
# <a name="error-firewall-on-local-machine"></a>Hata: Güvenlik Duvarı Yerel Makinede
Yerel makinedeki, Visual Studio 'Yu çalıştırdığınız makine olan Internet bağlantısı güvenlik duvarı, uzaktan hata ayıklamaya izin verecek şekilde ayarlanmadı. Varsayılan aktarımlarla yönetilen veya yerel uzaktan hata ayıklama için, DCOM trafiği için TCP 135 bağlantı noktasının açılması gerekir. Dosya ve yazıcı paylaşımının açılması gerekir ve devenv.exe özel durumlar listesine eklenmelidir. Bazı ıPSEC bağlantı noktalarının açılması de gerekebilir.

 Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).