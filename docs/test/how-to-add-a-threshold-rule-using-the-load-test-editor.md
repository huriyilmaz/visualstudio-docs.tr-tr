---
title: Yük testi için bir eşik kuralı ekleme
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
ms.openlocfilehash: c6855088c05e03311b5724ba3a0ccf438a43b6a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288487"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Nasıl yapılır: Yük Testi Düzenleyicisini kullanarak bir eşik kuralı ekleme

Yük testlerinde eşik kuralları bir performans sayacı değerini sabit bir değerle veya başka bir performans sayacı değeriyle karşılaştırır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Eşik kuralı eklemek için

1. Bir yük testi açın.

2. Yük Testi Düzenleyicisi, **sayaç kümeleri** düğümünü genişletin.

3. Sayaç kümelerinden birindeki **sayaç kategorilerinden** birini genişletin. Örneğin, **LoadTest: Scenario**öğesini seçebilirsiniz. Düğümünü genişletin.

4. Sayaçlarından birine sağ tıklayın, örneğin, **LoadTest: Scenario**altında **Kullanıcı yükü**. **Eşik kuralı ekle**' yi seçin.

     **Eşik kuralı ekle** iletişim kutusu görüntülenir.

5. İki tür kural arasından seçim yapabilirsiniz: **sabiti Karşılaştır** ve **sayacı Karşılaştır**. Uygun türü seçin ve değerleri ayarlayın.

    > [!NOTE]
    > Bir eşiğin bir sorun olduğunu veya eşiğin altına düşülecek bir sorun olduğunu **göstermek için,** özelliği **true** olarak ayarlandıysa **uyarıyı** ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Eşik Kuralı İhlallerini Çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
