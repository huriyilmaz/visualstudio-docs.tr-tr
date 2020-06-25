---
title: Yük testine çalışma ayarları ekleme
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2f62b3e9797e411138590fc15b0fe872920d203
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288461"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Nasıl yapılır: yük testine ek çalışma ayarları ekleme

Yük testinin çalışma ayarları, diğer birçok ayarı tespit. Bunlar testin süresini, sonuç koleksiyonu ayrıntısı düzeyini ve test çalışırken toplanan sayaç kümelerini içerir. Her bir yük testi için birden fazla çalışma ayarı oluşturup depolayabilmeniz ve sonra testi çalıştırdığınızda kullanılacak belirli bir ayarı seçmeniz gerekir. **Yeni Yük Testi Sihirbazı**kullanarak yük testinizi oluşturduğunuzda, yük testinize bir başlangıç çalıştırması ayarı eklenir.

Yük testini farklı koşullarda çalıştırabilmeniz için, farklı özellik ayarlarıyla yük testinize daha fazla çalışma ayarı ekleyebilirsiniz. Örneğin, yeni bir test ayarı ekleyebilir ve farklı bir örnek hızı kullanabilir ya da daha uzun çalışma süresi belirtebilirsiniz. Tek seferde yalnızca bir çalıştırma ayarı kullanabilir ve onu etkin olarak işaretleyerek kullanılacak çalıştırma ayarını belirtmeniz gerekir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>Başka bir çalışma ayarı eklemek için

1. Bir yük testi açın.

2. Seçim **Çalışma ayarları** klasörünü genişletin.

3. **Çalışma ayarları** klasörüne sağ tıklayın ve **çalıştırma ayarları ekle**' yi seçin.

     **Çalışma ayarları** klasörüne yeni bir çalışma ayarı eklenir.

4. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

     **Özellikler** penceresi, seçilen çalışma ayarının özellikleriyle birlikte görüntülenir.

5. **Özellikler** penceresinde, **ad** özelliği için metin kutusunu kullanın. yeni çalıştırma ayarına, çalışma ayarının amacını açıklayan bir ad verin (örneğin, **çalıştırma ayarı: beş dakikalık çalıştırma**).

6. Çalıştırma ayarlarını değiştirmek için **Özellikler** penceresini kullanın. Örneğin, testinizi beş dakikada çalıştırmak için çalıştırma süresini **00:05:00** olarak değiştirin.

    > [!NOTE]
    > Çalışma ayarları özelliklerinin tam listesi ve açıklamaları için bkz. [Yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).

     Artık, eklenen çalışma ayarını etkin olarak ayarlayarak kullanmak istediğinizi belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yük testi için etkin çalışma ayarını seçme](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
