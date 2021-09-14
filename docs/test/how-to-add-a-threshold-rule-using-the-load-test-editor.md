---
title: Yük testi için Eşik Kuralı ekleme
description: Bir performans sayacı değerini sabit değerle veya başka bir performans sayacı değeriyle karşılaştıran yük testlerinde eşik kuralları hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: fb6d40558acac6c51f353925b7e8a5b5453f611a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634238"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Nasıl: Yük testi düzenleyicisini kullanarak eşik kuralı ekleme

Yük testlerinde eşik kuralları, performans sayacı değerini sabit değerle veya başka bir performans sayacı değeriyle karşılaştırıldığında.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Eşik kuralı eklemek için

1. Yük testi açın.

2. Aşağıdaki Yük Testi Düzenleyicisi Sayaç Kümeleri **düğümünü** genişletin.

3. Sayaç Kümelerinden **biri için** Sayaç Kategorilerinden birini genişletin. Örneğin, **LoadTest:Scenario öğesini seçin.** Düğümü genişletin.

4. Sayaçlardan birini (örneğin, Kullanıcı Yüklemesi) **LoadTest:Scenario altında sağ tıklayın.**  Eşik **Kuralı Ekle'yi seçin.**

     Eşik **Kuralı Ekle** iletişim kutusu görüntülenir.

5. İki tür kuraldan birini seçebilirsiniz: **Sabiti Karşılaştır ve** **Sayacı Karşılaştır.** Uygun türü seçin ve değerleri ayarlayın.

    > [!NOTE]
    > Eşiği **aşmanın bir sorun** olduğunu belirtmek için Alert If Over özelliğini **True,** eşiğin altına düşmesinin bir sorun olduğunu belirtmek için **False** olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Eşik kuralı ihlallerini analiz etme](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
