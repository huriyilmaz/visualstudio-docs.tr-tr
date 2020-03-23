---
title: Yük testi için Özel Sayaç Setleri Ekle
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7438f657af2ba40fbda5afefbd8a12cc56a2a4c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114874"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Nasıl yapilir: Yük Testi Düzenleyicisi'ni kullanarak özel sayaç kümeleri ekleme

**Yeni Yük Testi Sihirbazı**ile bir yük testi oluşturduğunuzda, bir başlangıç sayaç kümesi eklersiniz. Bunlar, yük testiniz için önceden tanımlanmış sayaç kümeleri sunar.

> [!NOTE]
> Yük testleriniz uzak makinelere dağıtılırsa, denetleyici ve aracı sayaçları denetleyici ve aracı sayAcı kümelerine eşlenir. Yük testinizde uzak makineleri kullanma hakkında daha fazla bilgi için [test denetleyicileri ve test ajanlarına](configure-test-agents-and-controllers-for-load-tests.md)bakın.

Yük Testi Düzenleyicisi'nde sayaçlarınızı yönetirsiniz. **Load Test Editor** Teste zaten eklenen sayaç kümeleri, yük testinin **Sayaç Kümeleri** düğümünde görünür. Bir Yük testi oluşturduktan sonra, buna yeni özel sayaç kümeleri ekleyebilirsiniz.

![Özel Sayaç Seti](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Yük Testi'ne özel sayaç kümesi eklemek için

1. Bir yük testi açın.

2. Sayaç **Kümeleri** düğümlerini genişletin. Yük testine eklenen tüm sayaç kümeleri görülebilir.

3. **Sayaç Kümeleri** düğümüne sağ tıklayın ve **Özel Sayaç Seti Ekle'yi**seçin.

    > [!NOTE]
    > Sayaç kümesine **Custom1**gibi varsayılan bir ad verilir. **Özellikler** penceresini kullanarak adı değiştirebilirsiniz. **Özellikler** penceresini görüntülemek için **F4** tuşuna basın.

4. Özel sayaç setinize sayaç eklemek için yeni sayaç kümesini sağ tıklatın ve ardından **Sayaç Ekle'yi**seçin. Sayaç ekleme hakkında daha fazla bilgi için [bkz: Sayaç kümelerine sayaç ekleme.](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)

    > [!NOTE]
    > Varolan bir sayaç kümesini sağ tıklatıp, kopyala öğesini seçip ardından onu sayaç kümeleri düğümüne yapıştırarak da özel sayaç kümesi eklemek mümkündür. Kopyalanan ancak gerekli olmayan ek sayaçlar silinebilir. **Özellikler** penceresini kullanarak yeni sayaç kümesinin adını değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testindeki bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
