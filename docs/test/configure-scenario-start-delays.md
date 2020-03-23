---
title: Yük testi için Senaryo Başlangıç Gecikmelerini Yapılandırma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f962306462538717df694d3bc47719fe31b1e1fe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76111483"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Yük testlerinde senaryo başlangıç gecikmelerini yapılandırma

Yük Testi Düzenleyicisi ve **Özellikler** penceresini kullanarak bir yük testinde senaryo başlamadan önce bir gecikme belirtin.

Örneğin, başka bir senaryonun tükettiği öğeleri üretmeye başlamak için bir senaryoya ihtiyacınız **varsa, Gecikme Başlangıç Saati** özelliğini kullanmak isteyebilirsiniz. Üreten senaryonun bazı verileri doldurmasını sağlamak için tüketen senaryoyu geciktirebilirsiniz.

Başka bir örnek, yalnızca günün belirli bir saatinde çalıştırılabilen bir senaryonuz olabilir. Yani, bunu simüle etmek için senaryonun başlangıcını geciktirmek istiyorsunuz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Senaryonun gecikme başlangıç saatini belirtin

**Özellikler** penceresindeki **Gecikme Başlangıç Saati** özelliğini değiştirmek için Yük Testi Düzenleyicisi'ni kullanarak yük testinde senaryo başlamadan önce bir gecikme belirtebilirsiniz.

> [!NOTE]
> Yük testi senaryo özelliklerinin ve açıklamalarının tam listesi için [bkz.](../test/load-test-scenario-properties.md)

**Gecikme Başlangıç Saati** özelliğini kullanmak isteyebileceğin bir örnek, başka bir senaryonun tükettiği öğeleri üretmeye başlamak için bir senaryoya ihtiyaç duyduğunuz durumdur. Üreten senaryonun bazı verileri doldurmasını sağlamak için tüketen senaryoyu geciktirebilirsiniz.

Başka bir örnek, yalnızca günün belirli bir saatinde çalıştırılabilen bir senaryonuz olabilir. Bu nedenle, bunu simüle etmek için senaryonun başlangıcını geciktirmek istiyorsunuz.

> [!NOTE]
> Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi [için, Yükle testi senaryo özelliklerine](../test/load-test-scenario-properties.md)bakın.

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Bir senaryonun gecikme başlangıç saatini belirtmek için

1. Bir yük testi açın.

     Yük Testi Düzenleyicisi görüntülenir. Yük testi ağacı görüntülenir.

2. Yükleme testi ağaçları **Senaryolar** klasöründe, gecikme başlangıç saatini belirtmek istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. **Gecikme Başlangıç Saati** özelliğinin metin kutusuna, yük testi çalıştırıldığında senaryoyu başlatmadan önce yükleme testi başladıktan sonra bekleme süresini gösteren bir zaman değeri yazın.

    > [!NOTE]
    > Senaryo için **Isınma sırasında Devre Dışı Bırak** özelliğinin değeri **True**olarak ayarlanırsa, ısınma döneminden sonra Gecikme **Başlangıç Zamanı** özellikleri zaman değeri uygulanır. **Isınma sırasında Devre Dışı** Kaldır senaryosu özelliğini kullanarak Hangi senaryoların ısınmaya dahil edildiğini kontrol edebilirsiniz.

5. Özelliği değiştirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra yeni **Gecikme Başlangıç Saati** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Isınma döneminde bir senaryonun çalışıp çalıştırmadığını etkinleştirme ve devre dışı

**Isınma Sırasında Devre Dışı Bırak** özelliği **Özellikler** penceresi kullanılarak ayarlanır. Düzenleme yük testi senaryo özellikleri Yük Testi Düzenleyicisi tarafından ayarlanır.

**Isınma Sırasında Devre Dışı Devre özelliği,** **Gecikme Başlangıç Saati** özelliğinde belirtilen ısınma döneminde senaryonun çalışıp çalışmaması gerektiğini belirtmek için kullanılır. Daha fazla bilgi için önceki yordamı gözden [geçirin Bir senaryonun gecikme başlangıç saatini belirtin.](#specify-the-delay-start-time-of-a-scenario)

> [!NOTE]
> Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi [için, Yükle testi senaryo özelliklerine](../test/load-test-scenario-properties.md)bakın.

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Bir senaryo için ısınma süresini etkinleştirmek veya devre dışı kılabilir

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **Senaryolar** klasöründe, ısınma davranışını değiştirmek istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

     **Isınma Sırasında Devre Dışı Bırak** özelliğinde **True** veya False'u **seçin.**

4. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra ısınma sırasında yeni **Devre Dışı Kaldır** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Yük testleri için test aracılarını ve test denetleyicilerini yapılandırın](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md)
