---
description: Uzak makine yerel makineyle iletişim kurmaya çalıştığı zaman bir DCOM hatası oluştu.
title: Uzak bilgisayar DCOM iletişimlerini | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
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
ms.openlocfilehash: 8a5141560aefaf31337ffc82eee1bfa0f413d43c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058653"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Hata: Uzak bilgisayar DCOM iletişimini başlatamadı
Uzak makine yerel makineyle iletişim kurmaya çalıştığı zaman bir DCOM hatası oluştu. Yerel makine şu makinedir:

 çalıştırma Visual Studio. Bu hata çeşitli nedenlerle oluşabilir:

- Yerel makinede bir güvenlik duvarı etkindir.

- Windows makineden yerel makineye kimlik doğrulaması çalışmıyor.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Yerel makinede Güvenlik Duvarı Windows varsa, güvenlik duvarını yerel [hata](../debugger/remote-debugging.md) ayıklama için yapılandırma hakkında yönergeler için bkz. Uzaktan Hata Ayıklama.

2. Uzak Windows makinede bir dosya paylaşımı açmayı deneyerek kimlik doğrulamasını test etmek.

3. Bu kimlik Windows geri yüklemek için her iki makineyi de yeniden başlatmayı deneyin. Kerberos hataları için yerel ve uzak makinelerde olay günlüklerini inceler ve bilinen sorunlar için etki alanı yöneticilerine başvurun.

## <a name="see-also"></a>Ayrıca bkz.
 [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
