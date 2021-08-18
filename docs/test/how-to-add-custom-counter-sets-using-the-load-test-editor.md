---
title: Yük testi için Özel Sayaç Kümeleri ekleme
description: Yük Testi Sihirbazı ile bir yük testi oluşturdukta, ilk sayaçlar kümesi eklersiniz. Yük Testi Düzenleyicisi kullanarak özel sayaç kümeleri Yük Testi Düzenleyicisi.
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
ms.technology: vs-ide-test
ms.openlocfilehash: 5980dc94d4be706730c9d9e053e907e6b6267424
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092572"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Nasıl Yük Testi Düzenleyicisi

New Yük Testi Sihirbazı ile bir **yük testi** oluşturdukta, ilk sayaç kümesi eklersiniz. Bunlar, yük testi için önceden tanımlanmış sayaç kümeleri kümesi sağlar.

> [!NOTE]
> Yük testlerinizi uzak makinelere dağıtıyorsanız, denetleyici ve aracı sayaçları denetleyici ve aracı sayaç kümeleri ile eşlenmiş olur. Yük testinde uzak makineleri kullanma hakkında daha fazla bilgi için bkz. [Test denetleyicileri ve test aracıları.](configure-test-agents-and-controllers-for-load-tests.md)

Sayaçlarınızı **Yük Testi Düzenleyicisi.** Teste zaten eklenmiş olan sayaç kümeleri, yük **testinin Sayaç Kümeleri** düğümünde görünür. Yük testi oluşturdukktan sonra, buna yeni özel sayaç kümeleri eklemek için kullanabilirsiniz.

![Özel Sayaç Kümesi](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Yük Testi'ne özel sayaç kümesi eklemek için

1. Yük testi açın.

2. Sayaç Kümeleri **düğümünü** genişletin. Yük testine eklenmiş olan tüm sayaç kümeleri görünür durumdadır.

3. Sayaç Kümeleri düğümüne **sağ tıklayın ve** Özel Sayaç Kümesi **Ekle'yi seçin.**

    > [!NOTE]
    > Sayaç kümesine Custom1 gibi bir varsayılan **ad verilir.** Özellikler penceresini kullanarak adı **değiştirebilirsiniz.** Özellikler penceresini görüntülemek için **F4** **tuşuna** basın.

4. Özel sayaç kümenize sayaç eklemek için yeni sayaç kümesine sağ tıklayın ve Sayaç **Ekle'yi seçin.** Sayaç ekleme hakkında daha fazla bilgi için [bkz. Nasıl: Sayaç kümelere sayaç ekleme.](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)

    > [!NOTE]
    > Varolan bir sayaç kümesini sağ tıklatıp, kopyala öğesini seçip ardından onu sayaç kümeleri düğümüne yapıştırarak da özel sayaç kümesi eklemek mümkündür. Kopyalanan ancak gerekli olan ek sayaçlar silinebilir. Özellikler penceresini kullanarak yeni sayaç kümesi adını **değiştirebilirsiniz.**

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
