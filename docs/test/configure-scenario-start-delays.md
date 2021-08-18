---
title: Yük testi için Senaryo Başlatma Gecikmelerini Yapılandırma
description: Yük testinde senaryo başlamadan önce gecikme belirtmeyi öğrenmek için Yük Testi Düzenleyicisi ve Özellikler penceresi.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: c918d2479c27b068fd155ddaea78241019f22ca6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092689"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Yük testlerinde senaryo başlatma gecikmelerini yapılandırma

Yük testinde senaryo başlamadan önce, Yük Testi Düzenleyicisi ve Özellikler penceresini **kullanarak bir gecikme belirtin.**

Örneğin, başka bir senaryonun  tükettiği öğeleri üretmeye başlamak için bir senaryoya ihtiyacınız varsa Gecikme Başlangıç Zamanı özelliğini kullanmak iyi olabilir. Üretim senaryosunun bazı verileri doldurmak için tüketen senaryoyu geciktirebilirsiniz.

Bir diğer örnek de yalnızca günün belirli bir zamanında çalıştıracak bir senaryoya sahip olabileceğinizdir. Bu nedenle, bunun simülasyonunu yapmak için senaryonun başlangıcını geciktirmek istiyor uz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Bir senaryonun gecikme başlangıç saati belirtme

Özellikler penceresindeki Gecikme Başlangıç Zamanı özelliğini değiştirmek için Yük Testi Düzenleyicisi kullanarak yük testinde  bir senaryo başlamadan önce bir **gecikme belirtebilirsiniz.**

> [!NOTE]
> Yük testi senaryosu özelliklerinin ve açıklamalarının tam listesi için bkz. [Yük testi senaryosu özellikleri.](../test/load-test-scenario-properties.md)

Gecikme Başlangıç Zamanı özelliğini kullanmak istemeniz  gereken örneklerden biri, başka bir senaryonun tükettiği öğeleri üretmeye başlamak için bir senaryoya ihtiyacınız olduğudur. Üretim senaryosunun bazı verileri doldurmak için tüketen senaryoyu geciktirebilirsiniz.

Bir diğer örnek de yalnızca günün belirli bir zamanında çalıştıracak bir senaryoya sahip olabileceğinizdir. Bu nedenle, bunun benzetimini yapmak için senaryonun başlangıcını geciktirmek istiyor.

> [!NOTE]
> Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi için bkz. [Test senaryosu özelliklerini yükleme.](../test/load-test-scenario-properties.md)

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Bir senaryo için gecikme başlangıç saati belirtmek için

1. Yük testi açın.

     Yük Testi Düzenleyicisi görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **Senaryolar** klasöründe, gecikme başlangıç saati belirtmek istediğiniz senaryo düğümünü seçin.

3. Görünüm menüsünde **Özellikler** **Penceresi'ne tıklayın.**

     Senaryonun kategorileri ve özellikleri Özellikler **penceresinde** görüntülenir.

4. Gecikme Başlangıç Zamanı  özelliğinin metin kutusuna, yük testi çalıştırılana kadar senaryoyu başlatmadan önce yük testi başladıktan sonra bekleyeceği zamanı belirten bir saat değeri yazın.

    > [!NOTE]
    > Senaryonun Isınma **Sırasında** Devre Dışı Bırak özelliğinin değeri  **True** olarak ayarlanırsa, gecikme başlangıç saati özellikleri zaman değeri, sıcaktan sonra uygulanır. Isınma sırasında devre dışı bırak senaryo özelliğini kullanarak hangi senaryoların isınma **dahil olduğunu** kontrol etmek için kullanılabilirsiniz.

5. Özelliği değiştirdikten sonra Dosya **menüsünde Kaydet'i** seçin.  Daha sonra yeni Gecikme Başlangıç Zamanı değerini kullanarak yük **testini çalıştırabilirsiniz.**

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Isınma dönemi boyunca bir senaryonun çalıştırıp çalıştırılamayacaklarını etkinleştirme ve devre dışı bırakma

**Isınma Sırasında Devre** Dışı Bırak özelliği, Özellikler penceresi **kullanılarak** ayarlanır. Yük testi senaryosu özelliklerini düzenleme özelliği, Yük Testi Düzenleyicisi.

**Isınma Sırasında Devre** Dışı Bırak özelliği, senaryonun Gecikme Başlangıç Zamanı özelliğinde belirtilen sıcak dönem boyunca çalıştırıp çalıştırmayacaklarını belirtmek **için** kullanılır. Daha fazla bilgi için bir senaryonun gecikme [başlangıç saati belirtme önceki yordamını gözden geçirebilirsiniz.](#specify-the-delay-start-time-of-a-scenario)

> [!NOTE]
> Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi için bkz. [Test senaryosu özelliklerini yükleme.](../test/load-test-scenario-properties.md)

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Bir senaryo için isınma dönemini etkinleştirmek veya devre dışı bırakmak için

1. Yük testi açın.

     Yük Testi Düzenleyicisi  görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **Senaryolar** klasöründe, için ısınma davranışını değiştirmek istediğiniz senaryo düğümünü seçin.

3. Görünüm menüsünde **Özellikler** **Penceresi'ne tıklayın.**

     Senaryonun kategorileri ve özellikleri Özellikler **penceresinde** görüntülenir.

     **Isınma Sırasında Devre Dışı Bırak** özelliğinde **True** veya False'ı **seçin.**

4. Özelliği değiştirmeyi bitirdikten sonra Dosya menüsünde **Kaydet'i** seçin.  Daha sonra, yeni Isınma Sırasında Devre Dışı Bırak değerini **kullanarak yük testini çalıştırarak.**

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Yük testleri için test aracılarını ve test denetleyicilerini yapılandırma](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
