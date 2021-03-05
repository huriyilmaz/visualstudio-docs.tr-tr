---
description: Yerel makine uzak makineyle iletişime kalkışmaya çalışırken bir DCOM hatası oluştu.
title: DCOM iletişimi başlatılamıyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
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
ms.openlocfilehash: e7cf87815f7d6a09242d2b361db904094fcfcdea
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146450"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Hata: DCOM iletişimi başlatılamıyor
Yerel makine uzak makineyle iletişime kalkışmaya çalışırken bir DCOM hatası oluştu. Bunun nedeni uzak sunucudaki bir güvenlik duvarının veya uzak makinedeki Windows kimlik doğrulamasının bozuk olması nedeniyle oluşur.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Uzak makinede Windows Güvenlik Duvarı etkinse, güvenlik duvarının yerel hata ayıklama için nasıl yapılandırılacağı hakkında yönergeler için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md) .

- Windows kimlik doğrulamasını geri yüklemek için her iki makineyi yeniden başlatmayı deneyin. Kerberos hataları için yerel ve uzak makinelerdeki olay günlüklerini inceleyin ve bilinen sorunlar için etki alanı yöneticilerine başvurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
