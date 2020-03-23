---
title: Komut satırından yük testi çalıştırma ayarlarını ayarlama
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 760cf18062e607e9f9039c6cc5f4adf409134cb5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588999"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Nasıl seçilir: Komut satırından kullanılacak bir yük testi çalıştırma ayarı seçin

Yük testi, yük testinin çalışma şeklini etkileyen özellikler olan *çalıştırma ayarlarını*içerebilir. Çalıştırma ayarları **Özellikler** penceresindeki kategorilere göre düzenlenir. Bir yük testi çalıştırıldığında, şu anda etkin olarak ayarlanmış çalıştırma ayarını kullanır.

Yük testiniz yalnızca bir çalıştırma ayarı içeriyorsa, her zaman etkin düğümdür. Yük testinizde birden çok çalışma ayarı düğümü varsa, komut satırından bir yük testi çalıştırdığınızda kullanılacak olanını seçebilirsiniz. [Bkz. Nasıl Yapılır: Yük testine ek çalıştırma ayarları ekleyin.](../test/how-to-add-additional-run-settings-to-a-load-test.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-change-the-run-setting-from-the-command-line"></a>Komut satırından çalıştırma ayarını değiştirmek için

1. Bağlam parametre stratejisinden yararlanmak için komut satırından farklı çalışma ayarlarını kullanmak istiyorsanız, aşağıdaki komutu kullanın:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2. Mstest kullanarak yük testini çalıştırın:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testindeki bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Nasıl yapılır: Yük testine ek çalışma ayarları ekleme](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Nasıl seçilir: Yük testi için etkin çalışma ayarını seçin](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
