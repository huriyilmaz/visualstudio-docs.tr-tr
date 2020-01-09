---
title: Yük testi çalıştırma ayarında test yinelemesi sayısını belirtin
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588947"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Nasıl yapılır: bir yük testi çalışma ayarı içinde test yineleme sayısını belirtme

İle yükleme testinizi oluşturduktan sonra **Yeni Yük Testi Sihirbazı**, kullanabileceğiniz **Yük Testi Düzenleyicisi** test ihtiyaçlarınızı ve hedeflerinizi karşılayacak şekilde değiştirmek için. Daha fazla bilgi için [izlenecek yol: bir yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md).

Kullanarak **Yük Testi Düzenleyicisi**, düzenleyebileceğiniz **Test Yinelemeleri** çalıştırma ayarları değer özelliğini **özellikleri** penceresi. **Test Yinelemeleri** özelliği, tüm web başarım ve birim testleri tüm senaryolarda kullanarak bir yük testi çalıştırmak için yineleme sayısını belirtir **Yük Testi Düzenleyicisi**.

> [!NOTE]
> Çalıştırma ayarları özellikleri ve açıklamalarının tam listesi için bkz: [yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Bir çalışma ayarında test yineleme sayısını belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görünür ve yük testi ağacında görüntüler.

2. Ağaç, yük test **çalıştırma ayarları** klasör, bir çalışma ayarı seçin.

3. Üzerinde **görünümü** menüsünde **Özellikler penceresi** yük ayarın kategoriler ve Özellikler çalışma görüntülemek için.

4. Ayarlama **Test Yinelemeleri Kullan** özelliğini **True**.

5. İçinde **Test Yinelemeleri** özelliği, yük testi sırasında çalıştırılacak test yineleme sayısını gösteren bir sayı girin.

6. Özelliği değiştirmeyi bitirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Daha sonra yeni kullanarak yük testlerini çalıştırabilirsiniz **Test Yinelemeleri** değeri.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
