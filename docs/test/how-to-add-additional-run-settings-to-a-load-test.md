---
title: Yük Testine Çalıştırma Ayarları Ekleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adcb50d2c6800c5ce64ab2b7cf16ce9d2a25aaaa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584510"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Nasıl yapılır: Yük testine ek çalışma ayarları ekleme

Yük testinin çalışma ayarları çeşitli diğer ayarları belirler. Bunlar, testin süresini, sonuç toplama ayrıntı düzeyini ve test çalıştığında toplanan sayaç kümelerini içerir. Her yük testi için birden çok çalıştırma ayarı oluşturabilir ve depolayabilir ve testi çalıştırdığınızda kullanmak üzere belirli bir ayar seçebilirsiniz. **Yeni Yük Testi Sihirbazı'nı**kullanarak yük testinizi oluştururken ilk çalıştırma ayarı yük testinize eklenir.

Farklı koşullar altında yük testini çalıştırabilmeniz için farklı özellik ayarlarıyla yük testinize daha fazla çalıştırma ayarı ekleyebilirsiniz. Örneğin, yeni bir test ayarı ekleyebilir ve farklı bir örnek hızı kullanabilir veya daha uzun bir çalışma süresi belirtebilirsiniz. Aynı anda yalnızca bir çalıştırma ayarı kullanabilirsiniz ve etkin olarak işaretleyerek hangi çalışma ayarını kullanacağınızı belirtmeniz gerekir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>Başka bir çalıştırma ayarı eklemek için

1. Bir yük testi açın.

2. (İsteğe bağlı) Çalışma **Ayarları** klasörünü genişletin.

3. Ayarlar'ı **Çalıştır** klasörüne sağ tıklayın ve **Çalıştır Ayarları Ekle'yi**seçin.

     **Çalışma Ayarları** klasörüne yeni bir çalışma ayarı eklenir.

4. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     **Özellikler** penceresi, seçili çalıştırma ayarı özellikleriyle görüntülenir.

5. **Özellikler** penceresinde, yeni çalıştırma ayarı için **Ad** özelliğinin metin kutusunu kullanarak çalıştırma ayarının amacını açıklayan bir ad verin (örneğin, **Çalıştır Ayarı: Beş dakikalık çalışma).**

6. Çalışma ayarlarını değiştirmek için **Özellikler** penceresini kullanın. Örneğin, testinizi beş dakika çalıştırmak için çalışma süresini **00:05:00** olarak değiştirin.

    > [!NOTE]
    > Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi [için, Yükle testi çalıştırma ayarları özelliklerine](../test/load-test-run-settings-properties.md)bakın.

     Artık eklenen çalıştırma ayarını etkin olarak ayarlayarak kullanmak istediğinizi belirtebilirsiniz. Daha fazla bilgi için [bkz: Yük testi için etkin çalışma ayarını seçin.](../test/how-to-select-the-active-run-setting-for-a-load-test.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testindeki bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
