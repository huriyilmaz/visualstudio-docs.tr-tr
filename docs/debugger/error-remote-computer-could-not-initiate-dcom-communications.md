---
title: Hata-uzak bilgisayar DCOM iletişimini başlatamadı | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a1f5216953adc1b257e432b1e4f1eb4d041b836
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460710"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Hata: Uzak bilgisayar DCOM iletişimini başlatamadı
Uzak makine yerel makineyle iletişime kalkışmaya çalışırken bir DCOM hatası oluştu. Yerel makine,

 Visual Studio 'Yu çalıştırma. Bu hata, birkaç nedenden dolayı oluşabilir:

- Yerel makinede bir güvenlik duvarı etkin.

- Uzak makineden yerel makineye Windows kimlik doğrulaması çalışmıyor.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Yerel makinede Windows Güvenlik Duvarı etkinse, güvenlik duvarının yerel hata ayıklama için nasıl yapılandırılacağı hakkında yönergeler için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md) .

2. Uzak sunucudan yerel makinede bir dosya paylaşımından açmaya çalışırken Windows kimlik doğrulamasını test edin.

3. Windows kimlik doğrulamasını geri yüklemek için her iki makineyi yeniden başlatmayı deneyin. Kerberos hataları için yerel ve uzak makinelerdeki olay günlüklerini inceleyin ve bilinen sorunlar için etki alanı yöneticilerine başvurun.

## <a name="see-also"></a>Ayrıca bkz.
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)