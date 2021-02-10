---
title: Yük testi senaryolarında kullanılacak test aracılarını belirtme
description: Yük Testi Düzenleyicisi Özellikler penceresi aracıları kullanılacak şekilde ayarlayarak bir senaryoda kullanılacak aracıları belirtmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 0fc1aeb6eed9bf3697d1658a98d00bdfdab42660
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936216"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Nasıl yapılır: yük testi senaryolarında kullanılacak test aracılarını belirtme

**Yeni Yük Testi Sihirbazı** kullanarak yük testinizi oluşturduktan sonra, test ihtiyaçlarını ve hedeflerinizi karşılamak üzere senaryolar özelliklerini değiştirmek için **Yük Testi Düzenleyicisi** kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testi senaryosu özelliklerinin tam listesi ve açıklamaları için bkz. [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md).

Aracılar, **Özellikler** penceresinde **aracıları kullanacak şekilde** değiştirmek için **Yük Testi Düzenleyicisi** kullanılarak belirtilir.

Yük testini uzaktan çalıştırmak için denetleyiciler ve aracılar kullanıyorsanız senaryonuzu kullanmasını istediğiniz aracıları belirtebilirsiniz. Örneğin, performans eğilimlerini analiz ettiğinizde tutarlılığı korumanız için belirli bir aracı kümesi belirtmek isteyebilirsiniz. Ayrıca, aracılar coğrafi olarak dağıtılabilir ve bu sayede çalıştırdıkları betikler ve aracının nerede bulunduğu arasında bir benzeşim bulunur.

> [!TIP]
> Uzak siteye fiziksel olarak bir aracı koymak yerine, yavaş ağa öykünmek için Ağ öykünmesinin kullanılması başka bir seçenektir. Daha fazla bilgi için bkz. [sanal ağ türlerini belirtme](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Daha fazla bilgi için bkz.  [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md).

Diğer bir nedenden dolayı, aracıların bazıları belirli bir senaryo için gerekli olan bir yazılım, ancak bunların tümüne yüklenmemiş olabilir.

Test ayarlarındaki rolleri kullanarak belirli bir test çalıştırması için aracı seçimini kontrol edebilirsiniz. Daha fazla bilgi için bkz.  [test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md).

Bir test aracısı makinesinde yüzde 75 ' den fazla CPU kullanımı varsa veya kullanılabilir fiziksel belleğin yüzde 10 ' dan az olması halinde, aracı makinenin yük testinizde performans sorunu olmadığından emin olmak için yük testinize daha fazla aracı ekleyin.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Bir senaryo için kullanılacak aracıları belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **senaryolar** klasöründe, kullanılacak aracıları belirtmek istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. **Aracıların kullanması için** metin kutusunda, senaryonun çalıştırılacağı aracıların listesini yazın.

     Aracıların virgülle ayrılması gerekir, örneğin "**Agent1, agent2, Agent3**". Özelliği boş bırakmak, senaryonun kullanılabilir tüm aracıları kullanması gerektiğini belirtir.

    > [!NOTE]
    > Özelliği **Kullanılacak Aracılar** yerel çalıştırmalar için yok sayılır. Uzaktan çalıştırmalar için, **aracılarda** belirtilen aracıların hiçbiri kullanılabilir değilse, senaryodaki testler çalışmaz.

5. Özelliği değiştirdikten sonra **Dosya** menüsünde **Kaydet** ' i seçin. Daha sonra, değer **kullanmak için yeni aracıları** kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını Düzenle](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
