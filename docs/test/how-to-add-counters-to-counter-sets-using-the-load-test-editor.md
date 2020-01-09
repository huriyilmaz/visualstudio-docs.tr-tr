---
title: Yük testi için sayaç kümelerine sayaç ekleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b83d9c3624a4a268bfeba8a02b224fb9813ad7d1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594347"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Nasıl yapılır: Yük Testi Düzenleyicisi kullanarak sayaç kümelerine sayaç ekleme

**Yük Testi Sihirbazı**bir yük testi oluşturduğunuzda, bir ilk sayaç kümesi eklersiniz. Bu, Yük testiniz için ön tanımlı sayaç kümeleri kümesini sunar. Daha fazla bilgi için [sayaç kümelerini ve eşik kurallarını bilgisayarlar için bir yük testinde belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testlerinizi Uzak makinelerde dağıtılmışsa, denetleyici ve aracı sayaçları denetleyicisi ve aracısı için eşlenen sayaç kümeleri. Uzak makinede yük testinizde kullanma hakkında daha fazla bilgi için bkz. [Test denetleyicileri ve test aracılarını](configure-test-agents-and-controllers-for-load-tests.md).

Sayaçlarınızı yönettiğiniz **Yük Testi Düzenleyicisi**. Test zaten eklenmiş olan sayaç kümeleri görülebilir **sayaç kümeleri** düğümü yük testi. Yük testi oluşturduktan sonra, mevcut sayaç kümelerine yeni sayaçlar ekleyebilirsiniz.

## <a name="to-add-counters-to-a-counter-set"></a>Sayaç kümesine sayaç eklemek için

1. Bir yük testi açın.

2. Genişletin **sayaç kümeleri** düğümü. Yük testi için eklenmiş olan tüm sayaç kümeleri tarafından görülebilir.

    > [!NOTE]
    > Yük testi hiyerarşisi ağacı, **çalışma ayarları** düğümünü de içerir. Bu düğüm, bu bilgisayarlarla eşlenen tüm bilgisayarları ve sayaç kümelerini gösteren **sayaç kümesi eşlemeleri** düğümünü içerir.

3. Var olan bir sayaç kümesine sağ tıklayın ve ardından **Sayaç Ekle**' yi seçin.

     **Performans sayaçlarını Seç** iletişim kutusu görüntülenir.

4. **Bilgisayar** açılan kutusu açılan kutusuna, eşlemek istediğiniz bilgisayarın adını yazın. Alternatif olarak, açılan listeden bilgisayarlardan birini seçin.

    > [!NOTE]
    > Performans verileri toplanmadan önce sayaç kümelerinin bir bilgisayara eşlenmesi gerektiğinden, performans verilerinin toplanacağı bir bilgisayar belirtmeniz gerekir.

5. Performans veri sayacı kategorilerini filtrelemek için bir **Performans kategorisi** seçin. Performans sayaçlarını seçmek için iki veri sütunu görürsünüz.

    > [!NOTE]
    > Bazı sayaç kategorileri aynı zamanda bir örnek seçmenizi gerektirir. Örneğin, bir SQL sayacı seçerseniz, hedef bilgisayarda birden fazla SQL örneği yüklü olabileceğinden bir SQL örneği seçmelisiniz.

6. Özel sayaç kümesine eklemek için bir sayaç ve örnek seçin.

     \- veya -

     Tüm kullanılabilir sayaçları seçmek için **Tüm sayaçlar** radyo düğmesini seçin.

7. **Tamam**’ı seçin.

    > [!NOTE]
    > Ayrıca, var olan bir sayacı veya sayaç kategorisini seçip Kopyala ' yı seçip farklı bir sayaç kümesi düğümüne yapıştırarak sayaç kümesine sayaçlar eklemek mümkündür. Kopyalanmış, ancak gerekli olmayan ek sayaçlar silinebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Sayaç kümelerini ve eşik kurallarını bilgisayarlar için bir yük testi içinde belirtin.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
