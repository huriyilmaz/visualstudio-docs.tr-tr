---
title: 'Nasıl yapılır: Yük Testi Çalışma Ayarı için Örnek Hızı Belirtme'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63b6b9479347b076b7bd9e350e80e4bfa2a36d69
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594831"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Nasıl yapilir: Yük testi çalıştırma ayarı için örnek oranını belirtin

**Yeni Yük Testi Sihirbazı**ile yük testinizi oluşturduktan sonra, test ihtiyaçlarınızı ve hedeflerinizi karşılamak için özellikleri değiştirmek için Yük Testi Düzenleyicisi'ni kullanabilirsiniz. **Load Test Editor**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yük **Testi**Düzenleyicisi'ni kullanarak, **Özellikler** penceresinde bir çalışma ayarının **Örnek Hızı** özelliğinin değerini ayarlayabilirsiniz. Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi [için, Yükle testi çalıştırma ayarları özelliklerine](../test/load-test-run-settings-properties.md)bakın.

Yük testinizin uzunluğuna bağlı olarak yük testi ayarı için **Örnek Oran** özelliği için uygun bir değer seçin. Beş saniyenin varsayılan değeri gibi daha küçük bir örneklem hızı, yük testi sonuçları veritabanında daha fazla alan gerektirir. Daha uzun yük testleri için, örnek lem oranını artırmak topladığınız veri miktarını azaltır. Daha fazla bilgi için [bkz: Yük testi çalıştırma ayarı için örnek oranını belirtin.](../test/how-to-specify-the-sample-rate-for-a-load-test.md)

Örnek oranlar için bazı yönergeler aşağıda verilmiştir:

|Yük Testi Süresi|Önerilen Örnek Oran|
|-|-----------------------------|
|\<1 Saat|5 saniye|
|1 - 8 Saat arası|15 saniye|
|8 - 24 Saat|30 saniye|
|> 24 Saat|60 saniye|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Çalışma ortamında performans sayacı örnekleme oranını belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağacında, **Ayarlar'ı Çalıştır** klasöründe, örnek oranını belirtmek istediğiniz çalışma ayarını seçin.

3. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     Yük çalıştırma ayarının kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. Örnek **Hızı** özelliğine, yük testinin performans sayacı verilerini toplama sıklığını gösteren bir zaman değeri girin.

5. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra yeni **Örnek Oran** değerini kullanarak yük testi nizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md)
