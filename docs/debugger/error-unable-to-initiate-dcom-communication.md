---
description: Yerel makine uzak makineyle iletişim kurmaya çalıştığı zaman bir DCOM hatası oluştu.
title: DCOM iletişim | Microsoft Docs
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
ms.openlocfilehash: 5890fc9772e3645aca16893ab8b9c3b3d3af7d31
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074357"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Hata: DCOM iletişimi başlatılamıyor
Yerel makine uzak makineyle iletişim kurmaya çalıştığı zaman bir DCOM hatası oluştu. Bu, uzak sunucuda bir güvenlik duvarı veya uzak makinede Windows güvenlik duvarının bozuk durumdan kaynaklandı.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Uzak makinede Güvenlik Duvarı Windows varsa, güvenlik duvarını yerel [hata](../debugger/remote-debugging.md) ayıklama için yapılandırma yönergeleri için bkz. Uzaktan Hata Ayıklama.

- Bu kimlik Windows geri yüklemek için her iki makineyi de yeniden başlatmayı deneyin. Kerberos hataları için yerel ve uzak makinelerde olay günlüklerini inceler ve bilinen sorunlar için etki alanı yöneticilerine başvurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
