---
title: Yük Testi Senaryolarında Kullanmak Üzere Test Aracılarını Belirtme
description: Bir senaryoda kullanmak üzere aracıları belirtmeyi öğrenmek için, Aracılar'ın Özellikler penceresi özelliği olarak Yük Testi Düzenleyicisi.
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
ms.technology: vs-ide-test
ms.openlocfilehash: a0a32ade4170bcc2763a019bdf1532af01221393
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075820"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Nasıl kullanılır: Yük testi senaryolarında kullanmak üzere test aracılarını belirtme

Yük testini New Yük Testi Sihirbazı kullanarak **oluşturdukktan** sonra, Yük Testi Düzenleyicisi özelliklerini test **Yük Testi Düzenleyicisi** hedeflerinizi karşılayacak şekilde değiştirmek için kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testi senaryosu özelliklerinin ve açıklamalarının tam listesi için bkz. [Yük testi senaryosu özellikleri.](../test/load-test-scenario-properties.md)

Aracılar, Özellikler penceresinde **aracılar Yük Testi Düzenleyicisi** olarak değiştirmek **için** aracılar kullanılarak **belirtilir.**

Yük testini uzaktan çalıştırmak için denetleyiciler ve aracılar kullanıyorsanız senaryonun kullanmak istediğiniz aracıları belirtebilirsiniz. Örneğin, performans eğilimlerini analiz ederken tutarlılığı korumak için belirli bir aracı kümesi belirtmek istiyor olabilir. Ayrıca aracılar coğrafi olarak dağıtıldığından, çalıştırıldıları betikler ile aracının bulunduğu konum arasında bir benzeşim vardır.

> [!TIP]
> Uzak siteye fiziksel olarak bir aracı koymak yerine, yavaş ağa öykünme için ağ öykünmesi kullanmak başka bir seçenektir. Daha fazla bilgi için [bkz. Sanal ağ türlerini belirtme.](../test/specify-virtual-network-types-in-a-load-test-scenario.md)

Daha fazla bilgi için [bkz. Test denetleyicileri ve test aracıları.](configure-test-agents-and-controllers-for-load-tests.md)

Bir diğer neden de, bazı aracıların üzerinde belirli bir senaryo için gerekli olan yazılımların yüklü olmasıdır.

Test ayarlarında rolleri kullanarak, verilen bir test çalıştırması için aracı seçimini kontrol edebilirsiniz. Daha fazla bilgi için [bkz. Test ayarlarını kullanarak tanılama bilgilerini toplama.](../test/collect-diagnostic-information-using-test-settings.md)

Bir test aracısı makinesi yüzde 75'in üzerinde CPU kullanımına sahipse veya kullanılabilir fiziksel belleğin yüzde 10'undan daha azı varsa, aracı makinesinin yük testinde performans sorununa dönüşmay olduğundan emin olmak için yük testinize daha fazla aracı ekleyin.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Bir senaryo için kullanmak üzere aracıları belirtmek için

1. Yük testi açın.

     Yük Testi Düzenleyicisi  görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **Senaryolar** klasöründe, kullanmak üzere aracıları belirtmek istediğiniz senaryo düğümünü seçin.

3. Görünüm menüsünde **Özellikler** **Penceresi'ne tıklayın.**

     Senaryonun kategorileri ve özellikleri Özellikler **penceresinde** görüntülenir.

4. Agents to Use **özelliğinin metin kutusuna,** senaryonun üzerinde çalıştırılay olduğu aracıların listesini yazın.

     Aracılar virgülle ayrılarak ayrılabilir; örneğin, "**Agent1, Agent2, Agent3**". Özelliğini boş bırakmak, senaryonun tüm kullanılabilir aracıları kullanması gerektiğini belirtir.

    > [!NOTE]
    > Yerel **çalıştırmalar için,** Kullanılacak Aracılar özelliği yoksayılır. Uzak çalıştırmalar için, Kullanmak üzere Aracılar'da belirtilen **aracılardan** hiçbiri mevcutsa, senaryoda testler çalıştırilmez.

5. Özelliği değiştirdikten sonra Dosya **menüsünde Kaydet'i** seçin.  Daha sonra, yeni Aracılar to Use değerini kullanarak **yük testini çalıştırarak.**

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
