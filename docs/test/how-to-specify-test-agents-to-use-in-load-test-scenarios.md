---
title: Yük Testi Senaryolarında Kullanılacak Test Aracılarını Belirtin
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d23d565752d81bff960027090ddaaf88e9d78ed5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588934"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Nasıl kullanılır: Yük testi senaryolarında kullanılacak test aracılarını belirtme

**Yeni Yük Testi Sihirbazı'nı**kullanarak yük testinizi oluşturduktan sonra, test gereksinimlerinizi ve hedeflerinize ulaşmak için senaryo özelliklerini değiştirmek için Yük Testi Düzenleyicisi'ni kullanabilirsiniz. **Load Test Editor**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testi senaryo özelliklerinin ve açıklamalarının tam listesi için [bkz.](../test/load-test-scenario-properties.md)

Aracılar, **Özellikler** penceresindeki özelliği kullanacak **aracıları** değiştirmek için **Yük Testi Düzenleyicisi** kullanılarak belirtilir.

Yük testini uzaktan çalıştırmak için denetleyicileri ve aracıları kullanıyorsanız, senaryonuzun kullanmasını istediğiniz aracıları belirtebilirsiniz. Örneğin, performans eğilimlerini analiz ederken tutarlılığı korumak için belirli bir aracı kümesi belirtmek isteyebilirsiniz. Ayrıca, aracılar coğrafi olarak dağıtılabilir, böylece çalıştırdıkları komut dosyaları ile aracının bulunduğu yer arasında bir benzerlik vardır.

> [!TIP]
> Bir aracıyı uzak siteye fiziksel olarak yerleştirmek yerine, başka bir seçenek de yavaş ağı taklit etmek için ağ öykünme kullanmaktır. Daha fazla bilgi için [bkz.](../test/specify-virtual-network-types-in-a-load-test-scenario.md)

Daha fazla bilgi için test [denetleyicileri ve test aracıları'na](configure-test-agents-and-controllers-for-load-tests.md)bakın.

Başka bir nedeni, bazı, ancak tüm değil, aracılar belirli bir senaryo için gerekli olan yazılım yüklü olabilir.

Test ayarlarındaki rolleri kullanarak belirli bir test çalışması için aracı seçimini denetleyebilirsiniz. Daha fazla bilgi için bkz. [Test ayarlarını kullanarak tanı bilgilerini topla.](../test/collect-diagnostic-information-using-test-settings.md)

Bir test aracısı makinesinde yüzde 75'ten fazla CPU kullanımı varsa veya fiziksel belleğin yüzde 10'undan azı varsa, aracı makinenin yük testinizdeki darboğaz haline getirmediğinden emin olmak için yükleme testinize daha fazla aracı ekleyin.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Bir senaryo için kullanılacak aracıları belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **Senaryolar** klasöründe, kullanılacak aracıları belirtmek istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. Aracıların Kullanım Özelliği için metin **kutusuna,** senaryonun çalıştırılabileceği aracıların listesini yazın.

     Aracılar virgülle ayrılmalıdır, örneğin "**Agent1, Agent2, Agent3**". Özelliği boş bırakmak, senaryonun kullanılabilir tüm aracıları kullanması gerektiğini belirtir.

    > [!NOTE]
    > Özelliği **Kullanacak Aracılar** yerel çalıştırmalar için yoksayılır. Uzaktan çalıştırmalarda, **Kullanılacak Aracılar'da** belirtilen aracıların hiçbiri yoksa, senaryodaki testler çalışmaz.

5. Özelliği değiştirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra yeni **Aracılar kullanmak** değeri kullanarak yük testi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını edin](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md)
