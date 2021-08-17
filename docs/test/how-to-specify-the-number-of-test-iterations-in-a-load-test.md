---
title: Yük testi çalıştırma ayarında yineleme sayısını belirtme
description: Bir yük testinin tüm senaryolarında tüm web performansı ve birim testlerinde çalıştıracak yineleme sayısını belirtmek için Yük Testi Düzenleyicisi.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 3af6b33cb2c611023790f3f70ac4446ac6f99a36
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092468"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Nasıllı: Yük testi çalıştırma ayarında test yinelemelerinin sayısını belirtme

Yük testini New Yük Testi Sihirbazı ile **oluşturdukktan** sonra, Yük Testi Düzenleyicisi özelliklerini test **Yük Testi Düzenleyicisi** hedeflerinizi karşılayacak şekilde değiştirmek için kullanabilirsiniz. Daha fazla bilgi için [bkz. Adım adım kılavuz: Yük testi oluşturma ve çalıştırma.](../test/walkthrough-create-and-run-a-load-test.md)

Yük Testi Düzenleyicisi **kullanarak,** Özellikler penceresinde bir çalıştırma ayarları değerinin **Test** Yinelemeleri özelliğini **düzenleyebilirsiniz.** **Test Yinelemeleri** özelliği, Yük Testi Düzenleyicisi kullanarak bir yük testinin tüm senaryolarında tüm web performansı ve birim testlerinde çalıştıracak **yineleme sayısını belirtir.**

> [!NOTE]
> Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi için [bkz. Test çalıştırması ayarları özelliklerini yükleme.](../test/load-test-run-settings-properties.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Bir çalıştırma ayarında test yinelemesi sayısını belirtmek için

1. Yük testi açın.

     Yükleme **Yük Testi Düzenleyicisi** ve yük testi ağacını görüntüler.

2. Yük testi ağacının Farklı Çalıştır **Ayarlar** bir çalıştırma ayarı seçin.

3. Görünüm **menüsünde,** yük **çalıştırması ayarının** kategorilerini ve özelliklerini görüntülemek için Özellikler Penceresi'ne tıklayın.

4. Test **Yinelemelerini Kullan özelliğini** True olarak **ayarlayın.**

5. Test **Yinelemeleri özelliğinde,** yük testi sırasında çalıştıracak test yinelemelerinin sayısını belirten bir sayı girin.

6. Özelliği değiştirmeyi bitirdikten sonra Dosya menüsünde **Kaydet'i** seçin.  Daha sonra yeni Test Yinelemeleri değerini kullanarak **yük testini çalıştırebilirsiniz.**

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
