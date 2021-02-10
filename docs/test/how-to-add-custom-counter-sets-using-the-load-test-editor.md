---
title: Yük testi için özel sayaç kümeleri ekleme
description: Yük Testi Sihirbazı bir yük testi oluşturduğunuzda, bir ilk sayaç kümesi eklersiniz. Yük Testi Düzenleyicisi kullanarak özel sayaç kümeleri eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ce34a4e30c9d612bd37afb61c354b7a4b5df7aed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966935"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Nasıl yapılır: Yük Testi Düzenleyicisi kullanarak özel sayaç kümeleri ekleme

**Yeni Yük Testi Sihirbazı** bir yük testi oluşturduğunuzda, ilk sayaç kümesini eklersiniz. Bunlar, yük testiniz için önceden tanımlanmış sayaç kümeleri kümesi sunar.

> [!NOTE]
> Yük testleriniz uzak makineler arasında dağıtılmışsa, denetleyici ve aracı sayaçları denetleyici ve aracı sayaç kümelerine eşlenir. Yük testinizde uzak makineleri kullanma hakkında daha fazla bilgi için bkz. [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md).

Sayaçlarınızı **Yük Testi Düzenleyicisi** yönetirsiniz. Teste zaten eklenmiş olan sayaç kümeleri, yük testinin **sayaç kümeleri** düğümünde görünür. Yük testi oluşturduktan sonra, buna yeni özel sayaç kümeleri ekleyebilirsiniz.

![Özel sayaç kümesi](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Bir yük testine özel sayaç kümesi eklemek için

1. Bir yük testi açın.

2. **Sayaç kümeleri** düğümünü genişletin. Yük testine eklenmiş olan tüm sayaç kümeleri görünür.

3. **Sayaç kümeleri** düğümüne sağ tıklayın ve **Özel sayaç kümesi Ekle**' yi seçin.

    > [!NOTE]
    > Sayaç kümesine **Özel1** gibi varsayılan bir ad verilir. **Özellikler** penceresini kullanarak adı değiştirebilirsiniz. **Özellikler** penceresini göstermek için **F4** tuşuna basın.

4. Özel sayaç kümesine sayaç eklemek için, yeni sayaç kümesine sağ tıklayın ve ardından **Sayaç Ekle**' yi seçin. Sayaçların nasıl ekleneceği hakkında daha fazla bilgi için bkz. [nasıl yapılır: sayaç kümelerine sayaç ekleme](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Varolan bir sayaç kümesini sağ tıklatıp, kopyala öğesini seçip ardından onu sayaç kümeleri düğümüne yapıştırarak da özel sayaç kümesi eklemek mümkündür. Kopyalanmış, ancak gerekli olmayan ek sayaçlar silinebilir. Yeni sayaç kümesinin adını **Özellikler** penceresini kullanarak değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
