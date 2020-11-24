---
title: Yük testi için bir eşik kuralı ekleme
description: Bir performans sayacı değerini sabit bir değerle veya başka bir performans sayacı değeriyle karşılaştıran yük testlerinde eşik kuralları hakkında bilgi edinin.
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
manager: jillfra
ms.openlocfilehash: efd601862de60c38991de5eb901de5b55605540a
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440226"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Nasıl yapılır: Yük Testi Düzenleyicisini kullanarak bir eşik kuralı ekleme

Yük testlerinde eşik kuralları bir performans sayacı değerini sabit bir değerle veya başka bir performans sayacı değeriyle karşılaştırır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Eşik kuralı eklemek için

1. Bir yük testi açın.

2. Yük Testi Düzenleyicisi, **sayaç kümeleri** düğümünü genişletin.

3. Sayaç kümelerinden birindeki **sayaç kategorilerinden** birini genişletin. Örneğin, **LoadTest: Scenario** öğesini seçebilirsiniz. Düğümünü genişletin.

4. Sayaçlarından birine sağ tıklayın, örneğin, **LoadTest: Scenario** altında **Kullanıcı yükü**. **Eşik kuralı ekle**' yi seçin.

     **Eşik kuralı ekle** iletişim kutusu görüntülenir.

5. İki tür kural arasından seçim yapabilirsiniz: **sabiti Karşılaştır** ve **sayacı Karşılaştır**. Uygun türü seçin ve değerleri ayarlayın.

    > [!NOTE]
    > Bir eşiğin bir sorun olduğunu veya eşiğin altına düşülecek bir sorun olduğunu **göstermek için,** özelliği **true** olarak ayarlandıysa **uyarıyı** ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Eşik Kuralı İhlallerini Çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
