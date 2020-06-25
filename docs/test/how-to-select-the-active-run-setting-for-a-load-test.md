---
title: Yük testi için bir çalıştırma ayarı seçin
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8400c5afcb81215078617cca00cef9aa8ce018d6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287551"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Nasıl yapılır: bir yük testi için etkin çalışma ayarını seçme

**Yeni Yük Testi Sihirbazı**yük testinizi oluşturduktan sonra, test ihtiyaçlarını ve hedeflerinizi karşılamak üzere senaryolar özelliklerini değiştirmek için **Yük Testi Düzenleyicisi** kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yük testi, bir yük testinin çalışma biçimini etkileyen özellikler kümesi olan bir veya daha fazla *çalıştırma ayarı* içerebilir. Çalışma ayarları, **Özellikler** penceresindeki kategorilere göre düzenlenir. Bir yük testi çalıştırıldığında, şu anda etkin olarak ayarlanmış olan çalıştırma ayarını kullanır.

> [!NOTE]
> Çalışma ayarları özelliklerinin ve açıklamalarının tüm listesi için bkz. [Yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).

Yük testiniz **çalışma ayarları** klasörü altında yalnızca bir çalıştırma ayarı düğümü içeriyorsa, bu düğüm her zaman etkin düğümdür. Yük testiniz birden çok çalışma ayarları düğümü içeriyorsa, bir yük testi çalıştırdığınızda kullanılacak birini seçebilirsiniz. Bkz. [nasıl yapılır: yük testine ek çalışma ayarları ekleme](../test/how-to-add-additional-run-settings-to-a-load-test.md).

**Yük Testi Düzenleyicisi**, etkin çalıştırma ayarı "[etkin]" son eki tarafından tanımlanır.

## <a name="select-the-active-run-setting"></a>Etkin çalışma ayarını seçin

1. Bir yük testi açın.

2. **Çalışma ayarları** klasörünü genişletin.

3. Etkin düğüm olmasını istediğiniz çalışma ayarları düğümüne sağ tıklayın ve sonra **etkin olarak ayarla**' yı seçin.

     **Yük testi edito**r 'de, etkilenen çalışma ayarı düğümü "[etkin]" sonekiyle güncellenir.

     Seçilen çalıştırma ayarı etkin duruma gelir ve etkin olacak farklı bir çalışma ayarı seçene kadar etkin kalır.

> [!NOTE]
> Adlı bir ortam değişkenini ayarlayarak etkin çalıştırma ayarını geçersiz kılabilirsiniz `Test.UseRunSetting=<run setting name>` . Bu, komut satırından veya bir toplu iş dosyasından bir yük testi çalıştırdığınızda yararlı olur. Bu, yük testinizi açmadan farklı çalışma ayarları seçmenize olanak sağlar.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>Komut satırından kullanılacak çalıştırma ayarını belirtin

Komut satırından bir ortam değişkeni ayarlayarak, yük testinizde varsayılan çalıştırma ayarlarını geçersiz kılabilirsiniz:

**Set test. UseRunSetting = PreProdEnvironment**

Ve testi çalıştırmak için:

**MSTest/testcontainer: LoadTest1. LoadTest**

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Nasıl yapılır: yük testine ek çalışma ayarları ekleme](../test/how-to-add-additional-run-settings-to-a-load-test.md)
