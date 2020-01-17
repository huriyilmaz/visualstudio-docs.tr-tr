---
title: Yük testi için senaryo başlangıç gecikmelerini yapılandırma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f962306462538717df694d3bc47719fe31b1e1fe
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111483"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Yük testlerinde senaryo başlangıç gecikmelerini yapılandırma

Yük Testi Düzenleyicisi ve **Özellikler** penceresini kullanarak bir senaryo yük testinde başlamadan önce bir gecikme belirtin.

Örneğin, başka bir senaryonun tükettiği öğeleri oluşturmaya başlamak için bir senaryoya ihtiyaç duyuyorsanız, **gecikme başlangıç zamanı** özelliğini kullanmak isteyebilirsiniz. Üretim senaryosunun bazı verileri doldurmasına olanak tanımak için tüketim senaryosunu erteleyebilirsiniz.

Başka bir örnek ise yalnızca günün belirli bir saatinde çalışan bir senaryonuz olabilir. Bu nedenle, bunun benzetimini yapmak için senaryonun başlangıcını geciktirmek isteyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Bir senaryonun gecikme başlangıç saatini belirtin

**Özellikler** penceresinde **gecikme başlangıç zamanı** özelliğini değiştirmek için Yük Testi Düzenleyicisi kullanarak bir yük testinde senaryonun başlangıcından önce bir gecikme belirtebilirsiniz.

> [!NOTE]
> Yük testi senaryosu özelliklerini ve açıklamalarının tam listesi için bkz [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

**Gecikme başlangıç zamanını** kullanmak isteyebileceğiniz bir örneğe örnek olarak, başka bir senaryonun tükettiği öğeleri oluşturmaya başlamak için bir senaryoya ihtiyacınız vardır. Üretim senaryosunun bazı verileri doldurmasına olanak tanımak için tüketim senaryosunu erteleyebilirsiniz.

Başka bir örnek ise yalnızca belirli bir saatte çalışan bir senaryonuz olabilir. Bu nedenle, bunun benzetimini yapmak için senaryonun başlangıcını geciktirmek isteyebilirsiniz.

> [!NOTE]
> Çalışma ayarları özelliklerinin tam listesi ve açıklamaları için bkz. [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Bir senaryo için gecikme başlangıç saatini belirtmek için

1. Bir yük testi açın.

     Yük Testi Düzenleyicisi görünür. Yük testi ağacında görüntülenir.

2. Yük testi ağaçları **senaryolar** klasöründe, gecikme başlangıç zamanını belirtmek istediğiniz senaryo düğümünü seçin.

3. Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Kategoriler ve özellikler bu senaryonun görüntülenen **özellikleri** penceresi.

4. **Gecikme başlangıç zamanı** özelliğinin metin kutusunda, yük testi çalıştırıldığında senaryoya başlamadan önce, yük testi başladıktan sonra beklenecek süreyi belirten bir zaman değeri yazın.

    > [!NOTE]
    > Senaryo için **Warmup özelliği sırasında Disable** değeri **true**olarak ayarlanırsa, **gecikme başlangıç zamanı** özellikleri zaman değeri, ısınma süresinden sonra uygulanır. **Warmup senaryo özelliği sırasında devre dışı bırak** ' a tıklayarak hangi senaryoların sıcak bir şekilde ekleneceğini kontrol edebilirsiniz.

5. Özellik değiştirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Daha sonra yeni **gecikme başlangıç saati** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Bir senaryonun ısınma dönemi boyunca çalışıp çalışmadığını etkinleştirin ve devre dışı bırakın

**Warmup sırasında Disable** özelliği **Özellikler** penceresi kullanılarak ayarlanır. Yük testi senaryosu özelliklerini düzenleyerek Yük Testi Düzenleyicisi ayarlanır.

**Warmup sırasında devre dışı bırak** özelliği, senaryonun **gecikme başlangıç zamanı** özelliğinde belirtilen Isınma döneminde çalıştırılıp çalıştırılmayacağını veya çalıştırılmayacağını belirtmek için kullanılır. Daha fazla bilgi için, [bir senaryonun gecikme başlangıç saatini belirten](#specify-the-delay-start-time-of-a-scenario)önceki yordamı gözden geçirin.

> [!NOTE]
> Çalışma ayarları özelliklerinin ve açıklamalarının tamamı bir listesi için bkz. [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Bir senaryonun ısınma dönemini etkinleştirmek veya devre dışı bırakmak için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görünür. Yük testi ağacında görüntülenir.

2. Yük testi ağaçları **senaryolar** klasöründe, ısınma davranışını değiştirmek istediğiniz senaryo düğümünü seçin.

3. Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Senaryonun kategoriler ve özellikler görüntülenir **özellikleri** penceresi.

     **Warmup sırasında devre dışı bırak** özelliğinde, **true** veya **false değerini seçin.**

4. Özelliği değiştirmeyi bitirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Daha sonra, **Warmup değeri sırasında yeni devre dışı bırak** 'ı kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Test aracıları yapılandırmak ve test denetleyicilerini yük testleri için](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
