---
title: Yük Testi için Çalıştır Ayarı seçin
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91ac811c1f55fdb9a662db679ebd2d038ecdd5dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588986"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Nasıl seçilir: Yük testi için etkin çalışma ayarını seçin

**Yeni Yük Testi Sihirbazı**ile yük testinizi oluşturduktan sonra, test gereksinimlerinizi ve hedeflerinize ulaşmak için senaryo özelliklerini değiştirmek için Yük Testi Düzenleyicisi'ni kullanabilirsiniz. **Load Test Editor**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yük testi, yük testinin çalışma şeklini etkileyen bir dizi özellik olan bir veya daha fazla *çalıştırma ayarı* içerebilir. Çalıştırma ayarları **Özellikler** penceresindeki kategorilere göre düzenlenir. Bir yük testi çalıştırıldığında, şu anda etkin olarak ayarlanmış çalıştırma ayarını kullanır.

> [!NOTE]
> Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi [için, Yükle testi çalıştırma ayarları özelliklerine](../test/load-test-run-settings-properties.md)bakın.

Yük **testiniz, Çalışma Ayarları** klasörü altında yalnızca bir çalıştırma ayar düğümü içeriyorsa, bu düğüm her zaman etkin düğümdür. Yük testinizde birden çok çalışma ayarı düğümü varsa, yük testi çalıştırdığınızda kullanılacak olanını seçebilirsiniz. [Bkz. Nasıl Yapılır: Yük Testine Ek Çalıştırma Ayarları Ekleyin.](../test/how-to-add-additional-run-settings-to-a-load-test.md)

Load **Test Editor'da**etkin çalışma ayarı "[Etkin]" soneki yle tanımlanır.

## <a name="select-the-active-run-setting"></a>Etkin çalışma ayarını seçin

1. Bir yük testi açın.

2. Çalışma **Ayarları** klasörünü genişletin.

3. Etkin düğüm olmak istediğiniz çalıştır ayarları düğümüne sağ tıklayın ve ardından **Etkin Olarak Ayarla'yı**seçin.

     Yük **Testi Edito**r'de, etkilenen çalıştır ayar düğümü "[Etkin]" sonekiyle güncelleştirilir.

     Seçili çalıştırma ayarı etkin hale gelir ve etkin olması için farklı bir çalışma ayarı seçene kadar etkin kalır.

> [!NOTE]
> 'li bir ortam değişkeni ayarlayarak etkin `Test.UseRunSetting=<run setting name>`çalışma ayarını geçersiz kılabilirsiniz. Bu, komut satırından veya toplu iş dosyasından bir yük testi çalıştırdığınızda kullanışlıdır. Bu, yük testinizi açmadan farklı çalışma ayarlarını seçmenize olanak tanır.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>Komut satırından kullanılacak çalıştırma ayarını belirtin

Komut satırından bir ortam değişkeni ayarlayarak yük testinizdeki varsayılan çalıştırma ayarlarını geçersiz kılabilirsiniz:

**Set Test.UseRunSetting=PreProdEnvironment**

Ve testi çalıştırmak için:

**mstest /testkonteyneri:loadtest1.loadtest**

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testindeki bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Nasıl yapılır: Yük testine ek çalışma ayarları ekleme](../test/how-to-add-additional-run-settings-to-a-load-test.md)
