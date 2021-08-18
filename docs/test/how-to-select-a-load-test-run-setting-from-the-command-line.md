---
title: Komut satırına yük testi çalıştırma ayarlarını ayarlama
description: Yük testi, yük testinin çalışma yolunu etkileyen özellikler olan çalıştırma ayarlarını içerebilir. Çalıştırma ayarlarını komut satırına yükleme hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: c0e7b0e8bd4b7295bb3fca586b3931115f88652d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033206"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Nasıllı: Komut satırdan kullanmak üzere bir yük testi çalıştırma ayarı seçme

Yük testi, yük *testinin* çalışma yolunu etkileyen özellikler olan çalıştırma ayarlarını içerebilir. Çalıştırma ayarları, Özellikler penceresindeki kategorilere **göre** düzenlenmiştir. Bir yük testi çalıştır olduğunda, şu anda etkin olarak ayarlanmış çalıştırma ayarını kullanır.

Yük testinde yalnızca bir çalıştırma ayarı varsa, bu her zaman etkin düğüm olur. Yük testinde birden çok çalıştırma ayarı düğümü varsa, komut satırdan bir yük testi çalıştırarak kullanmak istediğiniz düğümü seçebilirsiniz. Bkz. [Nasıl kullanılır: Yük testinde ek çalıştırma ayarları ekleme.](../test/how-to-add-additional-run-settings-to-a-load-test.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-change-the-run-setting-from-the-command-line"></a>Komut satırı çalıştırma ayarını değiştirmek için

1. Bağlam parametresi stratejisini kullanmak için komut satırına göre farklı çalıştırma ayarları kullanmak için aşağıdaki komutu kullanın:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2. mstest kullanarak yük testini çalıştırın:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Nasıl kullanılır: Yük testinde ek çalıştırma ayarları ekleme](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Nasıllı: Yük testi için etkin çalıştırma ayarını seçme](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
