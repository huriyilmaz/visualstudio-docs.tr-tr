---
title: Yük Testi Senaryoları
description: Karmaşık ve gerçekçi iş yüklerinin benzetimini yapmak için testleri yapılandırmaya olanak sağlayan yük testi senaryolarını düzenlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 1b269b0563c82a97fcbf17c7b920a9433e1c1692
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123131"
---
# <a name="edit-load-test-scenarios"></a>Yük testi senaryolarını düzenleme

Yük testi *senaryosu yük* desenini, test karışımını, tarayıcı karışımını ve ağ karışımını belirtir. Karmaşık ve gerçekçi iş yüklerinin benzetimini yapmak için testleri yapılandırmanız olanaklı olduğundan senaryolar önemlidir.

Örneğin, birçok bağlantı hızı üzerinden gelen ve farklı tarayıcılar kullanan yüzlerce eşzamanlı müşteri tarafından kullanılan İnternet ön uçlarına sahip bir e-ticaret sitesini test ediyor olabilirsiniz. Aynı sitede ayrıca iç çalışanlar tarafından ürünleri güncelleştirmek ve istatistikleri görüntülemek için kullanılan bir yönetim işlevi de olabilir. Bu iç kullanıcılar genellikle aynı tarayıcıyı ve yüksek hızlı LAN bağlantısını kullanarak siteye erişer. Bu iki farklı kullanıcı gruplarının özelliklerini farklı senaryolarda kapsüllemek iyi olur. Her senaryo bir sanal kullanıcı türü içerebilir. Bu durumda, sanal müşterileri temsil eden bir yük testi senaryosu, bir web sitesinin sanal iç kullanıcılarını temsil etmek için başka bir senaryo da kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>Senaryo bileşenleri

Yük testi oluşturma sırasında belirttiğiniz tüm ilk yapılandırma seçenekleri ve ayarları, daha sonra yükleme **Yük Testi Düzenleyicisi.** Ayrıca yük testinde yeni senaryolar ekleyebilir, ayarları ve sayaç kümelerini çalıştırabilirsiniz.

![Yük Testi Senaryoları](../test/media/loadtesteditinscenarios.png)

Senaryolar aşağıdaki bileşenleri içerir:

|Süre|Tanım|
|-|-|
|Tarayıcı Karışımı|Sanal kullanıcıların bir web sitesine çeşitli web tarayıcıları üzerinden erişmesini simüle etmiştir.|
|Yük Düzeni|Yük testi sırasında etkin olan sanal kullanıcı sayısını ve yeni kullanıcıların başlama oranını belirtir. Örneğin: adım, sabit ve hedef tabanlı.|
|Test Karışımı Modeli|Bir yük testi senaryosunda belirli bir testi çalıştıran bir sanal kullanıcının olasılığını belirtir. Örneğin: TestA'yı çalıştırma şansı %20 ve TestB'i çalıştırma %80 şans. Test karışımı modeli, belirli bir senaryo için test amacını yansıtmalı.|
|Test Karışımı|Test karışımı, senaryoyu oluşturan web performansı ve birim testlerinin seçimi ve bu testlerin dağılımıdır.|
|Ağ Karışımı|Sanal kullanıcıların çeşitli ağ bağlantıları aracılığıyla bir web sitesine erişmelerini simüle eder. Ağ Karışımı LAN, kablo modem ve diğer seçenekleri içeren seçenekler sunar.|

Bir senaryoda, Yük Testi Düzenleyicisi kullanarak düzenleyemezsiniz diğer **Yük Testi Düzenleyicisi.** Daha fazla bilgi için [bkz. Yük testi senaryosu özellikleri.](../test/load-test-scenario-properties.md)

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Senaryoya yapay insan etkileşimi duraklamaları ekleyin:** Düşünme süreleri, insanların bir web sitesiyle etkileşimler arasında beklemelerini neden olan insan davranışlarının benzetimini yapmak için kullanılır. Bir web performans testinde istekler ile yük testi senaryosunda test yinelemeleri arasında oluşan zamanları düşünün. Yük testinde düşünme sürelerini kullanmak, daha doğru yük simülasyonları oluşturmada yararlı olabilir.|-   [Web sitesi insan etkileşimi gecikmelerinin benzetimini yapmak için düşünme sürelerini düzenleme](../test/edit-think-times-in-load-test-scenarios.md)|
|**Senaryo için sanal kullanıcı sayısını belirtin:** Yük deseni özelliklerini, sanal kullanıcı yükünün bir yük testi sırasında nasıl ayar olduğunu belirtmek için yapılandırabilirsiniz. Sabit, adım ve hedefe dayalı üç yerleşik yük deseni elde edin. Yük desenini seçer ve özellikleri yük testi hedefleriniz için uygun düzeylere ayarlarsiniz.|-   [Sanal kullanıcı etkinliklerini modellemek için yük desenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Senaryoda test çalıştıran bir sanal kullanıcının olasılığını yapılandırma:** Bir yük testi senaryosunda belirli bir testi çalıştıran sanal kullanıcının olasılığını belirten test karışımını kullanabilirsiniz. Bu, yükü daha gerçekçi bir şekilde simüle etmek için size olanak sağlar. Uygulamalarınız arasında yalnızca bir iş akışı olması yerine, son kullanıcıların uygulamalarınız ile nasıl etkileşim kurduğuna daha yakın bir tahmin olan birkaç iş akışınız olabilir.|-   [Metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Yük testi senaryosundan Web performansı veya birim testi ekleme veya kaldırma:** Bir senaryoda yük testinde web performansı veya birim testi ekleyebilir veya kaldırabilirsiniz. Yük testi, her biri bir veya daha fazla web performansı ya da birim testi içeren bir veya daha fazla senaryo içerir.|-   [Test karışımını düzenleme](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Senaryo için istenen ağ karışımını yapılandırma:** Ağ karışımını kullanarak, bir yük testi senaryosunda ağ yükünün simülasyonunu daha gerçekçi bir şekilde sebilirsiniz. Yük, tek bir ağ türü yerine ağ türlerinin heterojen bir karışımı kullanılarak oluşturulur. Son kullanıcıların uygulamalarınız ile nasıl etkileşim kurduğuna daha yakın bir tahmin oluşturabilirsiniz. Ağ karışımı modeli bu senaryonun hedeflerini yansıtmalı.|-   [Sanal ağ türlerini belirtme](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Senaryo için uygun Web tarayıcısı karışımını seçin:** Tarayıcı karışımını kullanarak bir yük testi senaryosunda web yükünün benzetimini daha gerçekçi bir şekilde tamamlayabilirsiniz. Yükleme, tek bir tarayıcı yerine tarayıcıların heterojen bir karışımı kullanılarak oluşturulur. Uygulamalarınız ile kullanılacak tarayıcılar hakkında daha yakın bir tahmin oluşturursanız.|-   [Web tarayıcısı türlerini belirtme](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Senaryo için test yineleme ayarlarını yapılandırma:** Test yineleme ayarlarını yapılandırmak için yük testi senaryosunu düzenlemek için Yük Testi Düzenleyicisi ve Özellikler penceresi. Varsayılan olarak, bir senaryo en fazla test yinelemesi ile ayarlanır. İsteğe bağlı olarak senaryoda en fazla yineleme sayısını ve aralarında ne kadar duraklama olduğunu yapılandırabilir.|-   [Senaryolar için test yinelemelerini yapılandırma](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Senaryo için gecikme ayarlarını yapılandırma:** Yük Testi Düzenleyicisi **ve** Özellikler **penceresini kullanarak,** bir senaryoyu yük testinde başlatmadan önce bir gecikme belirtebilirsiniz. Gecikme Başlangıç Zamanı özelliğini kullanmak  istemeniz gereken durumlara bir örnek, başka bir senaryonun tükettiği öğeleri üretmeye başlamak için bir senaryoya ihtiyacınız olduğudur. Üretim senaryosunun bazı verileri doldurmak için tüketen senaryoyu geciktirebilirsiniz.|-   [Yapılandırma senaryosu başlatma gecikmeleri](../test/configure-scenario-start-delays.md)|
|**Yük testi senaryosunda kullanmak üzere uzak makineleri belirtin:** Bir yük testi oluşturdukktan sonra, hangi test aracılarını dahil etmek istediğinize işaret etmek için yük testi senaryonun özelliklerini düzenleyebilirsiniz. Daha fazla bilgi için [bkz. Test denetleyicileri ve test aracıları.](configure-test-agents-and-controllers-for-load-tests.md)|-   [Nasıl yapılanlar: Kullanmak üzere test aracılarını belirtme](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testlerini düzenleme](../test/edit-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
