---
title: Yük testi çalıştırma ayarlarını komut satırından ayarla
description: Yük testi, yük testinin çalışma biçimini etkileyen özellikler olan çalıştırma ayarları ' nı içerebilir. Çalıştırma ayarlarını komut satırından yüklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 9cb3cb2fce990eabfd68bd3683418241be3020107de98c6aa55eca8e61011047
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366608"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Nasıl yapılır: komut satırından kullanmak için bir yük testi çalıştırma ayarı seçme

Yük testi, yük testinin çalışma biçimini etkileyen özellikler olan *çalıştırma ayarları*' nı içerebilir. Çalışma ayarları, **Özellikler** penceresindeki kategorilere göre düzenlenir. Bir yük testi çalıştırıldığında, şu anda etkin olarak ayarlanmış olan çalıştırma ayarını kullanır.

Yük testiniz yalnızca bir çalıştırma ayarı içeriyorsa, her zaman etkin düğüm olur. Yük testiniz birden çok çalışma ayarları düğümü içeriyorsa, komut satırından bir yük testi çalıştırdığınızda kullanılacak birini seçebilirsiniz. Bkz. [nasıl yapılır: yük testine ek çalışma ayarları ekleme](../test/how-to-add-additional-run-settings-to-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-change-the-run-setting-from-the-command-line"></a>Komut satırından çalıştırma ayarını değiştirmek için

1. Bağlam parametresi stratejisinden faydalanmak için komut satırından farklı çalışma ayarları kullanmak istiyorsanız aşağıdaki komutu kullanın:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2. MSTest kullanarak yük testini çalıştırın:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Nasıl yapılır: yük testine ek çalışma ayarları ekleme](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Nasıl yapılır: bir yük testi için etkin çalışma ayarını seçme](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
