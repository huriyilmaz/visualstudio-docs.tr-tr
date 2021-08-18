---
title: Yük testi çalıştırma ayarı için örnek hızı belirtme
description: Çalışma zamanlarını kullanarak bir çalıştırma ayarı için Örnek Oranı'Özellikler penceresi düzenlemeyi Yük Testi Düzenleyicisi.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 2e397dec54a29f3a660c4cc91d21094a99986e5a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135604"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Nasıllı: Yük testi çalıştırma ayarı için örnek hızı belirtme

New Yük Testi Sihirbazı ile yük testi **oluşturduk** Yük Testi Düzenleyicisi özelliklerini test **Yük Testi Düzenleyicisi** hedeflerinizi karşılayacak şekilde değiştirebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

komut **Yük Testi Düzenleyicisi** kullanarak, Özellikler penceresinde bir çalıştırma ayarının **Sample Rate** özelliğinin değerini **düzenleyebilirsiniz.** Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi için [bkz. Test çalıştırması ayarları özelliklerini yükleme.](../test/load-test-run-settings-properties.md)

Yük testi çalıştırma **ayarının Örnek Hızı** özelliği için yük testinizin uzunluğuna göre uygun bir değer seçin. Varsayılan beş saniyelik değer gibi daha küçük bir örnek oranı, yük testi sonuçları veritabanında daha fazla alan gerektirir. Daha uzun yük testleri için örnek oranının artırılması, toplayan veri miktarını azaltır. Daha fazla bilgi için, [bkz. How to: Specify the sample rate for a load test run setting](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Örnek hızlar için bazı yönergeler şu şekildedir:

|Yük Testi Süresi|Önerilen Örnek Oranı|
|-|-----------------------------|
|\< 1 Saat|5 saniye|
|1 - 8 Saat|15 saniye|
|8 - 24 Saat|30 saniye|
|> 24 Saat|60 saniye|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Bir çalıştırma ayarında performans sayacı örnekleme oranını belirtmek için

1. Yük testi açın.

     Yük Testi Düzenleyicisi  görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağacında, Çalıştırma Ayarlar **klasöründe,** örnek oranını belirtmek istediğiniz çalıştırma ayarını seçin.

3. Görünüm menüsünde **Özellikler** **Penceresi'ne tıklayın.**

     Yük çalıştırma ayarının kategorileri ve özellikleri Özellikler **penceresinde** görüntülenir.

4. Örnek **Hızı özelliğinde** yük testinin performans sayacı verilerini toplama sıklığını belirten bir zaman değeri girin.

5. Özelliği değiştirmeyi bitirdikten sonra Dosya menüsünde **Kaydet'i** seçin.  Daha sonra yeni Örnek Hızı değerini kullanarak yük **testini çalıştırarak.**

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
