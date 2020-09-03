---
title: Hata-DCOM iletişimi başlatılamıyor | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccd8b30fcba11d89e11227861c4582ff67f3a7e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460032"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Hata: DCOM iletişimi başlatılamıyor
Yerel makine uzak makineyle iletişime kalkışmaya çalışırken bir DCOM hatası oluştu. Bunun nedeni uzak sunucudaki bir güvenlik duvarının veya uzak makinedeki Windows kimlik doğrulamasının bozuk olması nedeniyle oluşur.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Uzak makinede Windows Güvenlik Duvarı etkinse, güvenlik duvarının yerel hata ayıklama için nasıl yapılandırılacağı hakkında yönergeler için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md) .

- Windows kimlik doğrulamasını geri yüklemek için her iki makineyi yeniden başlatmayı deneyin. Kerberos hataları için yerel ve uzak makinelerdeki olay günlüklerini inceleyin ve bilinen sorunlar için etki alanı yöneticilerine başvurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)