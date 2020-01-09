---
title: Bir yük testi için çalıştırma ayarları ekleme
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584510"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Nasıl yapılır: bir yük testine ek çalışma ayarları ekleme

Çalıştırma ayarları yük testinin çeşitli diğer ayarları belirleyin. Bunlar, test sonuçları koleksiyon ayrıntı düzeyi ve test çalıştığında toplanan sayaç kümeleri süresini içerir. Oluşturun ve her bir yük testi için birden çok çalışma ayarlarını depolamak ve ardından test çalıştırması sırasında kullanmak için belirli bir ayar seçin. İlk çalıştırma ayarı kullanarak yük testi oluşturduğunuzda, yük testinize eklenir **Yeni Yük Testi Sihirbazı**.

Yük testi farklı koşullar altında çalıştırabilmeniz için daha fazla yük testinize farklı özellik ayarları ile çalışma ayarları ekleyebilirsiniz. Örneğin, yeni bir test ayarı ekleyin ve farklı bir örnek hızı kullanabilir veya bir uzun çalıştırma süresi belirtin. Ayar etkin olarak işaretleyerek kullanmaya çalıştığı belirtmeniz gerekir ve yalnızca bir çalışma ayarı teker teker kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>Başka bir çalıştırma ayarı eklemek için

1. Bir yük testi açın.

2. (İsteğe bağlı) Genişletin **çalıştırma ayarları** klasör.

3. Sağ **çalıştırma ayarları** klasörü ve select **çalıştırma ayarları Ekle**.

     Yeni bir çalışma ayarı eklenir **çalıştırma ayarları** klasör.

4. Üzerinde **görünümü** menüsünde seçin **Özellikler penceresi**.

     **Özellikleri** seçili çalışma ayarı için özelliklerle penceresi görüntülenir.

5. İçinde **özellikleri** penceresinde metin kutusunu kullanın **adı** ayar bir adı çalıştırılmasına vermek özelliği çalışma ayarı amacı tanımlar (örneğin, **Çalıştır ayarını: beş dakika çalıştırma** ).

6. Kullanım **özellikleri** çalıştırma ayarlarını değiştirmek için penceresi. Örneğin, çalışma süresini **00:05:00** testiniz için beş dakika çalıştırılacak.

    > [!NOTE]
    > Çalıştırma ayarları özellikleri ve açıklamalarının tam listesi için bkz: [yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).

     Eklenen çalıştırın ayarını etkin olarak kullanmak istediğiniz artık belirtebilirsiniz. Daha fazla bilgi için [nasıl yapılır: çalışma ayarları yük testi için etkin seçmek](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Sayaç kümelerini ve eşik kurallarını bilgisayarlar için bir yük testi içinde belirtin.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
