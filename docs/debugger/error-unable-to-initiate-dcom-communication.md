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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1cbb59dc2da38274efd77ae5c8cd1efc69f7c55d8cf86cb55fe06f96bdd2b852
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419786"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Hata: DCOM iletişimi başlatılamıyor
Yerel makine uzak makineyle iletişime kalkışmaya çalışırken bir DCOM hatası oluştu. bunun nedeni uzak sunucuda bir güvenlik duvarı veya uzak makinede bozuk Windows kimlik doğrulaması olur.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- uzak makinede Windows güvenlik duvarı etkinse, güvenlik duvarının yerel hata ayıklama için nasıl yapılandırılacağı hakkında yönergeler için bkz. [uzaktan hata ayıklama](../debugger/remote-debugging.md) .

- Windows kimlik doğrulamasını geri yüklemek için her iki makineyi yeniden başlatmayı deneyin. Kerberos hataları için yerel ve uzak makinelerdeki olay günlüklerini inceleyin ve bilinen sorunlar için etki alanı yöneticilerine başvurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
