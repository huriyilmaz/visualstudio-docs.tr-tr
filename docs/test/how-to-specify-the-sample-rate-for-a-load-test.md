---
title: 'Nasıl yapılır: Yük Testi Çalışma Ayarı için Örnek Hızı Belirtme'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab77354226028397d5875137ed331860a4b32925
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287395"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Nasıl yapılır: bir yük testi çalışma ayarı için örnek hızı belirtme

**Yeni Yük Testi Sihirbazı**yük testinizi oluşturduktan sonra, özellikleri test ihtiyaçlarınızı ve hedeflerinizi karşılayacak şekilde değiştirmek için **Yük Testi Düzenleyicisi** kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Yük Testi Düzenleyicisi**kullanarak, **Özellikler** penceresinde bir çalıştırma ayarının **örnek hızı** özelliğinin değerini düzenleyebilirsiniz. Çalışma ayarları özelliklerinin ve açıklamalarının tüm listesi için bkz. [Yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).

Yük testinizin uzunluğuna bağlı olarak yük testi çalışma ayarı için **örnek hız** özelliği için uygun bir değer seçin. Beş saniyelik varsayılan değer gibi daha küçük bir örnek hız, yük testi sonuçları veritabanında daha fazla alan gerektirir. Daha uzun yük testleri için, örnek hızının artırılması topladığınız veri miktarını azaltır. Daha fazla bilgi için bkz. [nasıl yapılır: bir yük testi çalışma ayarı için örnek hızı belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Örnek ücretler için bazı yönergeler aşağıda verilmiştir:

|Yük testi süresi|Önerilen örnek hızı|
|-|-----------------------------|
|\< 1 saat|5 saniye|
|1-8 saat|15 saniye|
|8-24 saat|30 saniye|
|> 24 saat|60 saniye|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Bir çalışma ayarında performans sayacı örnekleme hızını belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağacında, **çalışma ayarları** klasöründe, örnek hızını belirtmek istediğiniz çalıştırma ayarını seçin.

3. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

     Yük çalıştırma ayarlarının kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. **Örnek hızı** özelliğinde, yük testinin performans sayacı verilerini toplayacağı sıklığı gösteren bir zaman değeri girin.

5. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet** ' i seçin. Daha sonra yeni **örnek hızı** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
