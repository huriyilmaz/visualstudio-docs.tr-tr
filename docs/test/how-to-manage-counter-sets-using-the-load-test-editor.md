---
title: Yük testi sayıcı setleri
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 224ac14a0d670648f8047a82a8abef0c2b7b2654
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113432"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Nasıl Yapilir: Yük Testi Düzenleyicisi'ni kullanarak sayaç kümelerini yönetme

**Yeni Yük Testi Sihirbazı**ile bir yük testi oluşturduğunuzda, bir başlangıç sayaç kümesi eklersiniz. Bunlar, yük testiniz için önceden tanımlanmış sayaç kümeleri sunar.

> [!NOTE]
> Yük testleriniz uzak makinelere dağıtılırsa, denetleyici ve aracı sayaçları denetleyici ve aracı sayAcı kümelerine eşlenir. Yük testinizde uzak makinelerin nasıl kullanılacağı hakkında daha fazla bilgi için test [denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)hakkında bilgi alın.

Sayaç kümelerini yönetmek, performans verileri toplamak istediğiniz bilgisayar kümesini seçmeyi ve her bir bilgisayardan toplanacak bir sayaç kümeleri kümesi atamayı içerir. Yük Testi Düzenleyicisi'nde sayaçlarınızı yönetirsiniz. **Load Test Editor**

![Sayaç Setlerini Yönetme](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Sayaç kümelerini yönetmek için

1. Bir yük testi açın.

2. Sayaç **Kümelerini Yönet** düğmesini seçin.

     – veya –

     Yük testi ağacında **Sayaç Kümeleri** klasörünü sağ tıklatın ve **Sayaç Kümelerini Yönet'i**seçin.

     **Sayaç Kümelerini Yönet** iletişim kutusu görüntülenir.

3. (İsteğe bağlı) **Seçili bilgisayarlarda ve sayaç kümelerinde aşağıdaki çalışma ayarları listesi kutusunun altına eklenecektir,** farklı bir çalışma ayarı seçin.

    > [!NOTE]
    > Bu, yalnızca yük testinizde birden fazla çalıştırma ayarınız varsa geçerlidir.

4. (İsteğe bağlı) İzlenecek yeni bir bilgisayar eklemek için **Bilgisayar Ekle'yi** seçin. Bir ad için isteceksiniz. Bir bilgisayarın adını yazın ve yeni girişin altında düğümler göreceksiniz. Örneğin **ASP.NET**, **IIS**, **SQL**, ve diğerleri. Seçmek istediğiniz düğümlerin önündeki onay kutularını seçin. Yeni sayaçlar Önizleme **seçimleri** bölmesinde görünür.

5. (İsteğe bağlı) Bilgisayar **Etiketleri** metin kutusuna, bilgisayarla ilişkilendirmek için bir etiket yazın. Örneğin, "TestMachine12 lab3 içinde".

     Bilgisayar etiketleri, tanınması kolay bir ada sahip bir bilgisayarı tanımlamanıza izin verir.

     Etiketler, Yük Testi Düzenleyicisi'ndeki ağaçtaki **Sayaç Kümesi Eşlemeler** düğümünde görüntülenir. Daha da önemlisi, etiketler Excel raporlarında görüntülenir ve bu da hissedarların bilgisayarın yük testinde ne gibi bir rolü olduğunu belirlemesine yardımcı olur. Örneğin, "Lab2'de Web Server1" veya "Phoenix ofisinde KI SQL Server2". Daha fazla bilgi için, [test karşılaştırmaları veya eğilim çözümlemesi için Rapor yük testleri sonuçlarına](../test/compare-load-test-results.md)bakın.

6. **Tamam'ı**seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testindeki bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
