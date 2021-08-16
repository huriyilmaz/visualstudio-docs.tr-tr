---
description: Uzak makine yerel makineyle iletişime kalkışmaya çalışırken bir DCOM hatası oluştu.
title: Uzak bilgisayar DCOM iletişimini başlatamadı | Microsoft Docs
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
ms.openlocfilehash: 3c316b87f35186b58b58ae0b8db93edeee3c4a56ab903847ec95187ffb4491a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404484"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Hata: Uzak bilgisayar DCOM iletişimini başlatamadı
Uzak makine yerel makineyle iletişime kalkışmaya çalışırken bir DCOM hatası oluştu. Yerel makine,

 Visual Studio çalışıyor. Bu hata, birkaç nedenden dolayı oluşabilir:

- Yerel makinede bir güvenlik duvarı etkin.

- uzak makineden yerel makineye Windows kimlik doğrulaması çalışmıyor.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. yerel makinede Windows güvenlik duvarı etkinse, güvenlik duvarının yerel hata ayıklama için nasıl yapılandırılacağı hakkında yönergeler için bkz. [uzaktan hata ayıklama](../debugger/remote-debugging.md) .

2. uzak sunucudan yerel makinede bir dosya paylaşımından açmaya çalışan Windows kimlik doğrulamasını Test edin.

3. Windows kimlik doğrulamasını geri yüklemek için her iki makineyi yeniden başlatmayı deneyin. Kerberos hataları için yerel ve uzak makinelerdeki olay günlüklerini inceleyin ve bilinen sorunlar için etki alanı yöneticilerine başvurun.

## <a name="see-also"></a>Ayrıca bkz.
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
