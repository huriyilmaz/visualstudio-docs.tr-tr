---
title: Yük testi için Eşik Kuralı ekleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d1389df0c307ad6ec65575fc7934e622928a0ca1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591638"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Nasıl?

Yük testlerinde eşik kuralları, performans sayacı değerini sabit bir değer veya başka bir performans sayacı değeriyle karşılaştırır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Eşik kuralı eklemek için

1. Bir yük testi açın.

2. Yük Testi Düzenleyicisi'nde **Sayaç Kümeleri** düğümlerini genişletin.

3. Sayaç Kümelerinden birinde **Sayaç Kategorilerinden** birini genişletin. Örneğin, **LoadTest:Scenario'u**seçebilirsiniz. Düğümü genişletin.

4. **LoadTest:Scenario**altında sayaçlardan birini sağ tıklatın, örneğin, **Kullanıcı Yükü**, LoadTest altında. **Eşik Kuralı Ekle'yi**seçin.

     **Eşik Kuralı Ekle** iletişim kutusu görüntülenir.

5. İki tür kural arasından seçim yapabilirsiniz: **Sabiti Karşılaştır** ve **Sayacı Karşılaştır.** Uygun türü seçin ve değerleri ayarlayın.

    > [!NOTE]
    > Bir eşiği aşmanın bir sorun olduğunu belirtmek için **True** özelliğinin üzerinde mi yoksa bir eşiğin altına düşmenin sorun olduğunu belirtmek için **False'a** **ayarlayın.**

## <a name="see-also"></a>Ayrıca bkz.

- [Eşik kuralı ihlallerini analiz edin](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Yük testindeki bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
