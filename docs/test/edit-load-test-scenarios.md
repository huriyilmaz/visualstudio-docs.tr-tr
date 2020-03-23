---
title: Yük Testi Senaryoları
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8fa323d275628fe580763709884552754acfba81
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593245"
---
# <a name="edit-load-test-scenarios"></a>Yük testi senaryolarını edin

Yük testi *senaryosu* yük deseni, test karışımı, tarayıcı karışımı ve ağ karışımını belirtir. Karmaşık, gerçekçi iş yüklerini simüle etmek için testleri yapılandırmanızı sağladığından senaryolar önemlidir.

Örneğin, birçok bağlantı hızı üzerinden gelen ve farklı tarayıcılar kullanan yüzlerce eşzamanlı müşteri tarafından kullanılan bir Internet ön ucuna sahip bir e-ticaret sitesini sınanıyor olabilirsiniz. Aynı site, ürünleri güncelleştirmek ve istatistikleri görüntülemek için dahili çalışanlar tarafından kullanılan bir yönetim işlevine de sahip olabilir. Bu dahili kullanıcılar genellikle aynı tarayıcı ve yüksek hızlı LAN bağlantısı kullanarak siteye erişir. Bu iki farklı kullanıcı grubu özelliğini farklı senaryolarda özetlemek isteyebilirsiniz. Her senaryo sanal bir kullanıcı türü içerebilir. Bu durumda, sanal müşterileri temsil etmek için bir yük testi senaryosu yapılabilir ve bir web sitesinin sanal iç kullanıcılarını temsil etmek için başka bir senaryo yapılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>Senaryo bileşenleri

Yük testi oluştururken belirttiğiniz ilk yapılandırma seçenekleri ve ayarları daha sonra **Yük Testi Düzenleyicisi'nde**değiştirilebilir. Ayrıca, yükleme testine yeni senaryolar, çalışma ayarları ve sayaç kümeleri de ekleyebilirsiniz.

![Yük Testi Senaryoları](../test/media/loadtesteditinscenarios.png)

Senaryolar aşağıdaki bileşenleri içerir:

|Sözleşme Dönemi|Tanım|
|-|-|
|Tarayıcı Karışımı|Sanal kullanıcıların bir web sitesine çeşitli web tarayıcıları aracılığıyla erişmelerini simüle eder.|
|Yük Deseni|Yükleme testi sırasında etkin olan sanal kullanıcı sayısını ve yeni kullanıcıların başlama hızını belirtir. Örneğin: adım, sabit ve hedef tabanlı.|
|Test Mix Modeli|Bir yük testi senaryosunda belirli bir testi çalıştıran sanal bir kullanıcıolasılığını belirtir. Örneğin: TestA'yı çalıştırmak için %20 şans ve TestB'yi çalıştırma şansı %80'dir. Test karması modeli, belirli bir senaryo için testinizin hedeflerini yansıtmalıdır.|
|Test Karışımı|Test karışımı, senaryoyu oluşturan web performansı ve birim testlerinin seçimi ve bu testlerin dağılımıdır.|
|Ağ Karışımı|Sanal kullanıcıların bir web sitesine çeşitli ağ bağlantıları aracılığıyla erişmelerini simüle eder. Network Mix, LAN, kablo modem ve diğer seçenekleri içeren seçenekler sunar.|

Bir senaryo, Yük Testi Düzenleyicisi'ni **Load Test Editor**kullanarak yükleyebileceğiniz birkaç başka özellime sahiptir. Daha fazla bilgi için, [Yük testi senaryo özelliklerine](../test/load-test-scenario-properties.md)bakın.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Senaryonuza yapay insan etkileşimi duraklamaları ekleyin:** Düşünme süreleri, insanların bir web sitesi yle etkileşimleri arasında beklemelerine neden olan insan davranışlarını simüle etmek için kullanılır. Web performans testindeki istekler ile yük testi senaryosundaki test yinelemeleri arasında düşünme süreleri oluşur. Bir yük testinde düşünme sürelerini kullanmak, daha doğru yük simülasyonları oluşturmada yararlı olabilir.|-   [Web sitesi insan etkileşimi gecikmeleri simüle etmek için düşünmek kez edin](../test/edit-think-times-in-load-test-scenarios.md)|
|**Senaryonuz için sanal kullanıcı sayısını belirtin:** Bir yük testi sırasında benzetilen kullanıcı yükünün nasıl ayarlandığını belirtmek için yük deseni özelliklerini yapılandırabilirsiniz. Üç yerleşik yük desenleri elde elabilirsiniz: sabit, adım ve hedef tabanlı. Yük modelini seçin ve özellikleri yük testi hedefleriniz için uygun düzeylere ayarlayın.|-   [Sanal kullanıcı etkinliklerini modellemek için yük modellerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Senaryoda bir test çalıştıran sanal kullanıcı olasılığını yapılandırın:** Bir yük testi senaryosunda belirli bir testi çalıştıran sanal bir kullanıcıolasılığını belirten test karışımını kullanabilirsiniz. Bu, yükü daha gerçekçi bir şekilde simüle etmenizi sağlar. Uygulamalarınızda tek bir iş akışına sahip olmak yerine, son kullanıcıların uygulamalarınızla nasıl etkileşimde bulunduğuna daha yakın bir yaklaşım olan birkaç iş akışına sahip olabilirsiniz.|-   [Metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Bir Web performansı veya birim testi bir yük testi senaryosundan ekleme veya kaldırma:** Bir senaryoda bir web performansı veya birim testi yük testinden ekleyebilir veya kaldırabilirsiniz. Yük testi, her biri bir veya daha fazla web performansı veya birim testi içeren bir veya daha fazla senaryo içerir.|-   [Test karışımını düzenleme](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Senaryonuz için istenen ağ karışımını yapılandırın:** Ağ karışımını kullanarak, yük testi senaryosunda ağ yükünü daha gerçekçi bir şekilde simüle edebilirsiniz. Yük, tek bir ağ türü yerine ağ türlerinin heterojen bir karışımı kullanılarak oluşturulur. Son kullanıcıların uygulamalarınızla nasıl etkileşimde denecek hakkında daha yakın bir yaklaşım oluşturursunuz. Ağ karması modeli bu senaryonun hedeflerini yansıtmalıdır.|-   [Sanal ağ türlerini belirtin](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Senaryonuz için uygun Web tarayıcısı karışımını seçin:** Tarayıcı karışımını kullanarak, bir yük testi senaryosunda web yükünü daha gerçekçi bir şekilde simüle edebilirsiniz. Yük tek bir tarayıcı yerine tarayıcıların heterojen bir karışımı kullanılarak oluşturulur. Uygulamalarınızda kullanılacak tarayıcıların daha yakın bir tahminini oluşturursunuz.|-   [Web tarayıcısı türlerini belirtin](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Senaryonuz için test yineleme ayarlarını yapılandırın:** Yük Testi Düzenleyicisi ve Özellikler penceresini kullanarak test yineleme ayarlarını yapılandırmak için bir yük testi senaryosunu değiştirebilirsiniz. Varsayılan olarak, bir senaryo en büyük test yinelemeleri ile ayarlanır. İsteğe bağlı olarak, senaryodaki en fazla yineleme sayısını ve aralarında ne kadar zaman zaman duraklatacağınızı görebilirsiniz.|-   [Senaryolar için test yinelemelerini yapılandırma](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Senaryonuz için gecikme ayarlarını yapılandırın:** Yük **Testi Düzenleyicisi** ve **Özellikler** penceresini kullanarak, bir yük testinde senaryobaşlatmadan önce bir gecikme belirtebilirsiniz. **Gecikme Başlangıç Zamanı** özelliğini ne zaman kullanmak isteyebileceğiniz in bir örneği, başka bir senaryonun tükettiği öğeleri üretmeye başlamak için bir senaryoya ihtiyacınız olmasıdır. Üreten senaryonun bazı verileri doldurmasını sağlamak için tüketen senaryoyu geciktirebilirsiniz.|-   [Yapılandırma senaryosu başlatma gecikmeleri](../test/configure-scenario-start-delays.md)|
|**Yük testi senaryosunda kullanılacak uzak makineleri belirtin:** Bir yük testi oluşturduktan sonra, hangi test aracılarını eklemek istediğinizi belirtmek için yük testi senaryonuzun özelliklerini atabilirsiniz. Daha fazla bilgi için test [denetleyicileri ve test aracıları'na](configure-test-agents-and-controllers-for-load-tests.md)bakın.|-   [Nasıl kullanılır: Kullanılacak test aracılarını belirtin](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testlerini edit](../test/edit-load-tests.md)
- [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md)
