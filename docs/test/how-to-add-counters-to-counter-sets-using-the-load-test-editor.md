---
title: Yük testi için Sayaçları Sayaçları Sayaçlar Ekleme
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594347"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Nasıl yapilir: Yük Testi Düzenleyicisi'ni kullanarak sayaç kümelerine sayaç ekleme

**Yük Testi Sihirbazı**ile bir yük testi oluşturduğunuzda, bir başlangıç sayaç kümesi eklersiniz. Bunlar, yük testiniz için önceden tanımlanmış sayaç kümeleri sunar. Daha fazla bilgi için [bkz.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testleriniz uzak makinelere dağıtılırsa, denetleyici ve aracı sayaçları denetleyici ve aracı sayAcı kümelerine eşlenir. Yük testinizde uzak makinelerin nasıl kullanılacağı hakkında daha fazla bilgi için test [denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)hakkında bilgi alın.

Yük Testi Düzenleyicisi'nde sayaçlarınızı yönetirsiniz. **Load Test Editor** Teste zaten eklenen sayaç kümeleri, yük testinin **Sayaç Kümeleri** düğümünde görünür. Bir yük testi oluşturduktan sonra, varolan sayaç kümelerine yeni sayaçlar ekleyebilirsiniz.

## <a name="to-add-counters-to-a-counter-set"></a>Sayaç kümesine sayaç eklemek için

1. Bir yük testi açın.

2. Sayaç **Kümeleri** düğümlerini genişletin. Yük testine eklenen tüm sayaç kümeleri görülebilir.

    > [!NOTE]
    > Yük testi hiyerarşisi ağacı da **Çalıştır Ayarları** düğüm içerir. Bu düğüm, tüm bilgisayarları ve bu bilgisayarlara eşlenen sayaç kümelerini gösteren **Sayaç Kümesi Eşlemeler** düğümlerini içerir.

3. Varolan sayaç kümesini sağ tıklatın ve ardından **Sayaç Ekle'yi**seçin.

     **Performans Sayaçları Seç** iletişim kutusu görüntülenir.

4. **Bilgisayar** açılır açılan açılan kutusuna, eşlemek istediğiniz bilgisayarın adını yazın. Alternatif olarak, açılır listedeki bilgisayarlardan birini seçin.

    > [!NOTE]
    > Sayaç kümelerinin performans verileri toplanmadan önce bilgisayara eşlemesi gerektiğinden, performans verilerini toplayacak bir bilgisayar belirtmeniz gerekir.

5. Performans veri sayaçları kategorilerini filtrelemek için bir **Performans kategorisi** seçin. Performans sayaçlarını seçmek için iki veri sütunu görürsünüz.

    > [!NOTE]
    > Bazı sayaç kategorileri, bir örnek de seçmeniz gerekir. Örneğin, bir SQL sayacı seçerseniz, hedef bilgisayarda birden fazla SQL örneği yüklü olabileceğinden bir SQL örneği seçmeniz gerekir.

6. Özel sayaç setinize eklemek için bir sayaç ve örnek seçin.

     \-veya -

     Kullanılabilir tüm sayaçları seçmek için **Tüm sayaçlar** radyo düğmesini seçin.

7. **Tamam'ı**seçin.

    > [!NOTE]
    > Ayrıca, varolan bir sayaç veya sayaç kategorisi seçerek, kopya seçerek ve sonra farklı bir sayaç kümesi düğümüne yapıştırarak sayaç kümesine sayaç eklemek de mümkündür. Kopyalanan ancak gerekli olmayan ekstra sayaçlar silinebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testindeki bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
