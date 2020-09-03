---
title: Yük testi senaryoları
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593245"
---
# <a name="edit-load-test-scenarios"></a>Yük testi senaryolarını Düzenle

Yük testi *senaryosu* , yük modelini, test karışımını, tarayıcı karışımını ve ağ karışımını belirtir. Senaryolar, karmaşık, gerçekçi iş yüklerinin benzetimini yapmak için testler yapılandırmanıza olanak sağladığından önemlidir.

Örneğin, çok sayıda bağlantı hızından ve farklı tarayıcılar kullanarak gelen yüzlerce eşzamanlı müşteri tarafından kullanılan bir Internet ön ucuna sahip bir e-ticaret sitesini test edebilirsiniz. Aynı sitede, ürünleri güncelleştirmek ve istatistikleri görüntülemek için dahili çalışanlar tarafından kullanılan bir yönetim işlevi de bulunabilir. Bu iç kullanıcılar genellikle aynı tarayıcıyı ve yüksek hızlı bir LAN bağlantısını kullanarak siteye erişir. Farklı senaryolarda bu iki farklı Kullanıcı grubunun özelliklerini kapsüllemek isteyeceksiniz. Her senaryo, bir sanal kullanıcı türü içerebilir. Bu durumda, sanal müşterileri temsil eden bir yük testi senaryosu ve bir Web sitesinin sanal iç kullanıcılarını temsil eden başka bir senaryo yapılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>Senaryo bileşenleri

Bir yük testi oluşturduğunuzda belirttiğiniz ilk yapılandırma seçenekleri ve ayarları, **Yük Testi Düzenleyicisi**daha sonra değiştirilebilir. Ayrıca, bir yük testine yeni senaryolar, çalıştırma ayarları ve sayaç kümeleri ekleyebilirsiniz.

![Yük testi senaryoları](../test/media/loadtesteditinscenarios.png)

Senaryolar aşağıdaki bileşenleri içerir:

|Süre|Tanım|
|-|-|
|Tarayıcı karışımı|Sanal kullanıcıların çeşitli web tarayıcıları aracılığıyla bir Web sitesine erişmesini taklit eder.|
|Yük kalıbı|Yük testi sırasında etkin olan sanal kullanıcı sayısını ve yeni kullanıcıların başlatılma hızını belirtir. Örneğin: adım, sabit ve amaç tabanlı.|
|Test karışımı modeli|Bir yük testi senaryosunda belirli bir testi çalıştıran sanal kullanıcı olasılığını belirtir. Örneğin: TestA çalıştırmak için %20 fırsat ve TestB çalıştırmak için %80 şans. Test karışımı modeli, belirli bir senaryo için testinizin hedeflerini yansıtmalıdır.|
|Test karışımı|Test karışımı, senaryoyu oluşturan Web performansı ve birim testlerinin seçiminden ve bu testlerin dağıtımına göre belirlenir.|
|Ağ karışımı|Sanal kullanıcıların bir Web sitesine çeşitli ağ bağlantılarıyla erişmesini taklit eder. Ağ karışımı, LAN, kablolu modem ve diğer seçenekleri içeren seçenekler sunar.|

Senaryo, **Yük Testi Düzenleyicisi**kullanarak düzenleyebileceğiniz diğer birçok özelliğe sahiptir. Daha fazla bilgi için bkz. [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md).

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Senaryonuza yapay insan etkileşimi duraklamaları ekleyin:** Düşünme süreleri, insanların bir Web sitesi ile etkileşimler arasında beklemesine neden olan insan davranışlarının benzetimini yapmak için kullanılır. Bir Web performans testindeki istekler arasında ve bir yük testi senaryosunda test yinelemeleri arasında düşünme süreleri oluşur. Bir yük testinde düşünme sürelerinin kullanılması, daha doğru yük benzetimleri oluşturmak için yararlı olabilir.|-   [Web sitesi insan etkileşimi gecikmelerini benzetmek için düşünme zamanlarını düzenleme](../test/edit-think-times-in-load-test-scenarios.md)|
|**Senaryonuza yönelik sanal kullanıcı sayısını belirtin:** Yük testi özelliklerini, benzetimli Kullanıcı yükünün yük testi sırasında nasıl ayarlanacağını belirtmek için yapılandırabilirsiniz. Üç yerleşik yük düzeni alırsınız: sabit, adım ve hedef tabanlı. Yük modelini seçer ve özellikleri yük testi hedefleriniz için uygun düzeyler olarak ayarlayabilirsiniz.|-   [Sanal Kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Senaryoda test çalıştıran bir Sanal Kullanıcı olasılığını yapılandırın:** Yük testi senaryosunda belirli bir testi çalıştıran bir sanal kullanıcının olasılığını belirten test karışımını kullanabilirsiniz. Bu, yükün daha gerçekçi bir şekilde benzetimini yapmanızı sağlar. Uygulamalarınız aracılığıyla yalnızca bir iş akışına sahip olmak yerine, son kullanıcıların uygulamalarınızla nasıl etkileşime gireceğini daha yakından yaklaşarak birkaç iş akışınız olabilir.|-   [Metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Yük testi senaryosundan bir Web performans veya birim testi ekleme veya kaldırma:** Bir senaryoda yük testi 'nden bir Web performans veya birim testi ekleyebilir veya kaldırabilirsiniz. Bir yük testi, her biri bir veya daha fazla Web performans veya birim testi içeren bir veya daha fazla senaryo içerir.|-   [Test karışımını düzenle](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Senaryonuz için istenen ağ karışımını yapılandırın:** Ağ karışımını kullanarak, bir yük testi senaryosunda ağ yükünün daha gerçekçi bir şekilde benzetimini yapabilirsiniz. Yük, tek bir ağ türü yerine farklı ağ türleri karışımı kullanılarak oluşturulur. Son kullanıcıların uygulamalarınızla nasıl etkileşime gireceğini daha yakından bir şekilde oluşturursunuz. Ağ karışımı modeli söz konusu senaryonun amaçlarını yansıtmalıdır.|-   [Sanal ağ türlerini belirtin](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Senaryonuz için uygun Web tarayıcısı karışımını seçin:** Tarayıcı karışımını kullanarak, bir yük testi senaryosunda Web yükünün benzetimini daha gerçekçi bir şekilde gerçekleştirebilirsiniz. Yükleme tek bir tarayıcı yerine heterojen tarayıcıların bir karışımı kullanılarak oluşturulur. Uygulamalarınızla birlikte kullanılacak tarayıcıların daha yakından bir kısmını oluşturursunuz.|-   [Web tarayıcıları türlerini belirtin](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Senaryonuz için test yineleme ayarlarını yapılandırın:** Yük Testi Düzenleyicisi ve Özellikler penceresi kullanarak test yineleme ayarlarını yapılandırmak için bir yük testi senaryosunu düzenleyebilirsiniz. Varsayılan olarak, bir senaryo en fazla test yinelemesi olmadan ayarlanır. İsteğe bağlı olarak, senaryoda en fazla yineleme sayısını ve bunların arasında ne kadar duraklatılacağını yapılandırabilirsiniz.|-   [Senaryolar için test yinelemeleri yapılandırma](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Senaryonuz için gecikme ayarlarını yapılandırın:** **Yük Testi Düzenleyicisi** ve **Özellikler** penceresini kullanarak, bir yük testinde senaryo başlatmadan önce bir gecikme belirtebilirsiniz. Başka bir senaryonun tükettiği öğeleri oluşturmaya başlamak için bir senaryoya ihtiyaç duyuyorsanız, **gecikme başlangıç zamanı** özelliğini kullanmak isteyebileceğiniz bir örnektir. Üretim senaryosunun bazı verileri doldurmasına olanak tanımak için tüketim senaryosunu erteleyebilirsiniz.|-   [Configureng senaryo başlangıç gecikmeleri](../test/configure-scenario-start-delays.md)|
|**Yük testi senaryosunda kullanılacak uzak makineleri belirtin:** Yük testi oluşturduktan sonra, hangi test aracılarını dahil etmek istediğinizi belirtmek için yük testi senaryonuzun özelliklerini düzenleyebilirsiniz. Daha fazla bilgi için bkz. [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md).|-   [Nasıl yapılır: kullanılacak test aracılarını belirtme](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testlerini Düzenle](../test/edit-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
