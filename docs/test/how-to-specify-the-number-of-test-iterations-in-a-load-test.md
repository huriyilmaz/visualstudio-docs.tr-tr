---
title: Yük testi çalıştırma ayarında test yinelemelerinin sayısını belirtin
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 446da348c1a947e6c59b8ad60d9bd0799d0d4322
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588947"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Nasıl yapilir: Yük testi çalıştırma ayarında test yinelemelerinin sayısını belirtin

**Yeni Yük Testi Sihirbazı**ile yük testinizi oluşturduktan sonra, test gereksinimlerinizi ve hedeflerinize ulaşmak için senaryo özelliklerini değiştirmek için Yük Testi Düzenleyicisi'ni kullanabilirsiniz. **Load Test Editor** Daha fazla bilgi için [Bkz. Walkthrough: Bir yük testi oluşturun ve çalıştırın.](../test/walkthrough-create-and-run-a-load-test.md)

Yük **Testi**Düzenleyicisi'ni kullanarak, **Özellikler** penceresinde çalışan ayarlar değerinin **Test Yinelemeleri** özelliğini değiştirebilirsiniz. **Test Yinelemeleri** özelliği, Yük Testi Düzenleyicisi'ni kullanarak bir yük testindeki tüm senaryolarda tüm web **Load Test Editor**performansında ve birim testlerinde çalışacak yineleme sayısını belirtir.

> [!NOTE]
> Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi [için, Yükle testi çalıştırma ayarları özelliklerine](../test/load-test-run-settings-properties.md)bakın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Çalışma ayarındaki test yinelemelerinin sayısını belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görünür ve yük testi ağacını görüntüler.

2. Yük testi ağacında, **Ayarlar'ı Çalıştır** klasöründe bir çalışma ayarı seçin.

3. **Görünüm** menüsünde, yük çalıştırma ayarının kategorilerini ve özelliklerini görüntülemek için **Özellikler Penceresi'ni** seçin.

4. Kullanım **Testi Yinelemeler** özelliğini **True**olarak ayarlayın.

5. Test **Yinelemeleri** özelliğine, yük testi sırasında çalışacak test yinelemelerinin sayısını gösteren bir sayı girin.

6. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra yeni **Test Yinelemeler** değerini kullanarak yük testi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md)
