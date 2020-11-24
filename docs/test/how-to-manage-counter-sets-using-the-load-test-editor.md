---
title: Yük testi sayaç kümeleri
description: Bilgisayarları seçerek ve her bilgisayardan toplanacak sayaç kümelerini atayarak sayaç kümelerini yönetmek için Yük Testi Düzenleyicisi yönetme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
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
ms.openlocfilehash: 15d04d105264d07a1f883c5b67ce57c8590375a8
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440019"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Nasıl yapılır: Yük Testi Düzenleyicisi kullanarak sayaç kümelerini yönetme

**Yeni Yük Testi Sihirbazı** bir yük testi oluşturduğunuzda, ilk sayaç kümesini eklersiniz. Bunlar, yük testiniz için önceden tanımlanmış sayaç kümeleri kümesi sunar.

> [!NOTE]
> Yük testleriniz uzak makineler arasında dağıtılmışsa, denetleyici ve aracı sayaçları denetleyici ve aracı sayaç kümelerine eşlenir. Yük testinizde uzak makinelerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md).

Sayaç kümelerini yönetmek, performans verilerini toplamak istediğiniz bilgisayar kümesini seçmeyi ve her bir bilgisayardan toplanacak bir dizi sayaç kümesi atamayı içerir. Sayaçlarınızı **Yük Testi Düzenleyicisi** yönetirsiniz.

![Sayaç kümelerini yönetme](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Sayaç kümelerini yönetmek için

1. Bir yük testi açın.

2. **Sayaç Kümelerini Yönet** düğmesini seçin.

     veya

     Yük testi ağacındaki **sayaç kümeleri** klasörünü sağ tıklatın ve **Sayaç Kümelerini Yönet**' i seçin.

     **Sayaç Kümelerini Yönet** iletişim kutusu görüntülenir.

3. Seçim **Seçilen bilgisayarlarda ve sayaç kümeleri aşağıdaki çalışma ayarları liste kutusu altına eklenir** , farklı bir çalışma ayarı seçin.

    > [!NOTE]
    > Bu yalnızca yük testinizde birden fazla çalışma ayarınız varsa geçerlidir.

4. Seçim İzlemek üzere yeni bir bilgisayar eklemek için **Bilgisayar Ekle** ' yi seçin. Sizden bir ad girmeniz istenir. Bilgisayarın adını yazın ve yeni girdinin altında düğümleri görürsünüz. Örneğin, **ASP.net**, **IIS**, **SQL** ve diğerleri. Seçmek istediğiniz düğümlerin önündeki onay kutularını seçin. Yeni sayaçlar **Önizleme seçimleri** bölmesinde görünür.

5. Seçim **Bilgisayar etiketleri** metin kutusuna bilgisayarla ilişkilendirilecek bir etiket yazın. Örneğin, "TestMachine12 in lab3".

     Bilgisayar etiketleri, kullanımı kolay bir ada sahip bir bilgisayarı tanımlamanızı sağlar.

     Etiketler, Yük Testi Düzenleyicisi ağaçtaki **sayaç kümesi eşlemeleri** düğümünde görüntülenir. Daha önemli olan Etiketler, paydaşların bilgisayarın yük testinde hangi rolün olduğunu belirlemesine yardımcı olan Excel raporlarında görüntülenir. Örneğin, "Web 'de Sunucu1 lab2" veya "Phoenix ofisinde SQL Sunucu2". Daha fazla bilgi için bkz. [Test karşılaştırmaları veya eğilim analizi Için rapor yükleme testleri sonuçları](../test/compare-load-test-results.md).

6. **Tamam ' ı** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtin](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
