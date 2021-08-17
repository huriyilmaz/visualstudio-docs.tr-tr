---
description: Yerel makinede İnternet Bağlantısı Güvenlik Duvarı'Visual Studio, uzaktan hata ayıklamaya izin verecek şekilde ayarlanmaz.
title: Yerel Makine Güvenlik Duvarı | Microsoft Docs
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 17a5707c5b4d200b149b818ca321d85d41876146
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105229"
---
# <a name="error-firewall-on-local-machine"></a>Hata: Güvenlik Duvarı Yerel Makinede
Yerel makinede İnternet Bağlantısı Güvenlik Duvarı'Visual Studio, uzaktan hata ayıklamaya izin verecek şekilde ayarlanmaz. Varsayılan taşıma ile yönetilen veya yerel uzaktan hata ayıklama için TCP 135 bağlantı noktasının DCOM trafiği için açılması gerekir. Dosya ve yazıcı paylaşımının açılması ve devenv.exe özel durumlar listesine eklenmeleri gerekir. Bazı IPSEC bağlantı noktalarının açılması da gerekebilir.

 Daha fazla bilgi için [bkz. Uzaktan Hata Ayıklama.](../debugger/remote-debugging.md)
