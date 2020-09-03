---
title: Yük testi için bir Web sitesinin gerçek dünya kullanımına öykünüşme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18e22cd151d8013a50e34a01757069dde9574e79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75589610"
---
# <a name="test-mix-models-overview"></a>Test karışımı modellerine genel bakış

Yük modelleme seçeneklerini, yük testi yaptığınız bir Web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını daha doğru tahmin etmek için kullanabilirsiniz. Doğru yük modelini temel alan bir yük testi yanıltıcı sonuçlar üretebildiğinden bunun olması önemlidir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Test karışımı modeli iyileştirmeleri

Yük Testi Düzenleyicisi veya test karışımı modeli sihirbazını kullanarak, bir yük testi senaryosu için aşağıdaki test karışımı türlerini belirtebilirsiniz. Daha fazla bilgi için bkz. [bir senaryoda test karışımı modelini değiştirme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Yük testi senaryonuz için aşağıdaki test karışımı modeli seçeneklerinden birini belirtebilirsiniz:

- **Toplam test sayısına göre:** Bir sanal kullanıcı bir test yinelemesi başlattığında hangi Web performansının veya birim testinin çalıştırılacağını belirler. Yük testinin sonunda, belirli bir test çalıştırmasının atanan test dağıtımını eşleştirme sayısı. Test karışımını bir IIS günlüğünde veya üretim verilerinde işlem yüzdeleri temelinde dayandırdığınızda bu test karışımı modelini kullanın. Daha fazla bilgi için bkz. [Testleri temel alan yüzde](#BasedOnTestsStarted).

- **Sanal kullanıcı sayısına göre:** Belirli bir Web performans veya birim testini çalıştıracak sanal kullanıcıların yüzdesini belirler. Yük testinin herhangi bir noktasında, belirli bir testi çalıştıran kullanıcıların sayısı atanan dağıtımla eşleşir. Test karışımını belirli bir testi çalıştıran kullanıcıların yüzdesine dayandırdığınızda, bu test karışımı modelini kullanın. Daha fazla bilgi için bkz. [sanal kullanıcılara göre yüzde](#PercentageBasedonVirtualUsers).

- **Kullanıcı adımına göre:** Yük testi sırasında, her Web performans testi veya birim testi, Kullanıcı başına saat başına belirtilen sayıda kez çalıştırılır. Sanal kullanıcıların testi yük testi boyunca belirli bir hızda çalıştırmasını istediğinizde, bu test karışımı modelini kullanın. Daha fazla bilgi için bkz. [hız testi karışımı](#PacingTestMix).

    > [!TIP]
    > Ne zaman **yüzde test karışımı** seçtiğinizde ve **sanal kullanıcılara göre yüzdeyi**ne zaman seçersiniz? Bu iki seçenek arasındaki fark, Test karışımındaki bazı testlerin diğer testlerden çok daha uzun süreli olduğu durumlarda önemlidir. Bu durumda, büyük olasılıkla **sanal kullanıcılara göre yüzdeyi**seçmelisiniz. Bu seçim, çok fazla kullanıcının uzun süreli testler çalıştıracağına ilişkin olasılık artışının arttığı bir test çalıştırmasının önlenmesine yardımcı olur. Ancak, testlerin hepsi benzer süreler içeriyorsa, **yüzde test karışımını**daha güvenli bir şekilde seçebilirsiniz.

- **Sıralı sıraya göre:** Her sanal kullanıcı, Web performansını veya birim testlerini, testlerin senaryoda belirlenen sırada çalıştırır. Sanal Kullanıcı, yük testi tamamlanana kadar bu sırada testlerin ilerlemeye devam eder. Daha fazla bilgi için bkz. [sıralı sıra](#SequentialOrder).

### <a name="percentage-based-on-tests-started"></a><a name="BasedOnTestsStarted"></a> Başlatılan testleri temel alan yüzde

Karışımdaki her bir test için, testin çalıştırılacak sonraki test olarak ne sıklıkta seçili olacağını belirleyen bir yüzde belirtebilirsiniz. Örneğin, aşağıdaki yüzde değerlerini üç teste atayabilirsiniz:

- TestA (%50)

- TestB (%35)

- TestC (%15)

Bu ayarı kullanırsanız, başlangıç için sonraki test atanan yüzdeleri temel alır. Bunu, her bir testi çalıştıran sanal kullanıcı sayısını hesaba katmadan yapabilirsiniz.

### <a name="percentage-based-on-virtual-users"></a><a name="PercentageBasedonVirtualUsers"></a> Sanal kullanıcılara göre yüzde
Bu test karışımı modeli, belirli bir testi çalıştıracak sanal kullanıcıların yüzdesini belirler. Bu test karışımı modelini kullanırsanız, başlangıç için sonraki test yalnızca atanan yüzdeleri değil, o anda belirli bir testi çalıştıran sanal kullanıcıların yüzdesini temel alır. Yük testinin herhangi bir noktasında, belirli bir testi çalıştıran kullanıcıların sayısı, atanan dağıtımla mümkün olduğunca yakından eşleşir.

### <a name="pacing-test-mix"></a><a name="PacingTestMix"></a> Hız testi karışımı

Bir hız testi karışımı belirtirseniz, Test karışımındaki her bir test için her bir sanal kullanıcı için bir test yürütmesi oranı ayarlarsınız. Her test için, bu oran, Sanal Kullanıcı başına saat başına çalıştırılan testler olarak ifade edilir. Örneğin, aşağıdaki hız testi karışımını aşağıdaki testlere atayabilirsiniz:

- TestA: Kullanıcı başına saat başına 4 test

- TestB: Kullanıcı başına saat başına 2 test

- TestC: Kullanıcı başına saat başına 0,125 test

Hız testi karışımı modelini kullanırsanız, yük testi çalışma zamanı altyapısı, testlerin başlatıldığı gerçek oranın belirtilen orandan küçük ya da buna eşit olmasını garanti eder. Testler, atanan sayının tamamlanması için çok uzun süre çalışıyorsa bir hata döndürülür.

**Test yinelemeleri ayarı arasındaki düşünme süresi** , bir hız testi karışımı kullandığınızda uygulanmaz.

#### <a name="apply-distribution-to-pacing-delay"></a>İlerleme Gecikmesine Dağıtım Uygula
Yük testi senaryosunda, **Adımlama Gecikmesine Dağıtım Uygula** özelliği true veya false olarak ayarlanabilir:

- **Doğru**: senaryo, **test karışımını düzenle** Iletişim kutusunda **saat başına Kullanıcı başına testler** sütunundaki değer tarafından belirtilen tipik istatistiksel dağıtım gecikmelerini uygular. Daha fazla bilgi için bkz. [test çalıştıran bir Sanal Kullanıcı olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Örneğin, test kümesinin saat başına 2 Kullanıcı olarak ayarlanması için **test karışımını düzenle** Iletişim kutusunda **saat başına Kullanıcı başına** test olduğunu varsayalım. **Ilerleme Gecikmesine Dağıtım Uygula** özelliği **true**olarak ayarlanırsa, testler arasındaki bekleme süresine tipik istatistiksel bir dağıtım uygulanır. Sınamalar saat başına 2 test çalıştırmaya devam eder, ancak aralarında 30 dakika olması gerekmez. İlk test 4 dakika sonra ve ikinci test 45 dakika sonra çalışabilir.

- **Yanlış**: testler, **test karışımını düzenle** Iletişim kutusunda **saat başına Kullanıcı başına testler** sütunundaki değer için belirttiğiniz belirli hızda çalışır. Daha fazla bilgi için bkz. [test çalıştıran bir Sanal Kullanıcı olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Örneğin, test kümesinin saat başına 2 Kullanıcı olarak ayarlanması için **test karışımını düzenle** Iletişim kutusunda **saat başına Kullanıcı başına** test olduğunu varsayalım. **Adımlama Gecikmesine Dağıtım Uygula** özelliği **yanlış**olarak ayarlanırsa, Testleriniz çalışırken temel olarak hiçbir zaman bir yöntem verirsiniz. Test her 30 dakikada bir çalışacaktır. Bu, saat başına 2 test yürütmenizi sağlar.

  Daha fazla bilgi için, bkz. [nasıl yapılır: Kullanıcı hız testi karışımı modeli kullanırken Adım Gecikmesine Dağıtım uygulama](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

### <a name="sequential-order"></a><a name="SequentialOrder"></a> Sıralı sıra
Sıralı test sırası seçeneğinin temelinde seçilmesi, her bir sanal kullanıcının senaryodaki tüm testleri testlerin tanımlandığı sırada çalıştırmasını sağlar.

## <a name="test-iterations-property"></a>Test Yinelemeleri özelliği
Çalışma ayarları özelliklerinde, Test Yinelemeleri özelliği için bir değer belirtebilirsiniz. Bu değer, bir yük testinde çalıştırılacak test yinelemesi sayısıdır. Belirtilen test yinelemesi sayısı başlatıldıktan sonra, yük profillerinin herhangi birinin ayarlarına rağmen ek test yinelemeleri başlatılmaz. Belirtilen test yinelemeleri sayısı tamamlandığında, yük testi sona erer. Daha fazla bilgi için, bkz. [nasıl yapılır: bir çalışma ayarında test yinelemesi sayısını belirtme](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Testleri başlatma ve sonlandırma
Her bir sanal kullanıcının yük testi oturumunun başlangıcında ve sonunda çalıştırılacak testleri seçebilirsiniz. Daha fazla bilgi için bkz. [test çalıştıran bir Sanal Kullanıcı olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

- **Testi başlatın**. Bu test, Test karışımındaki testlerin herhangi biri çalıştırılmadan önce her bir sanal kullanıcı tarafından çalıştırılır.

- **Testi Sonlandır**. Bu test, belirli bir sanal kullanıcı için tüm testler çalıştırıldıktan sonra çalıştırılır.

  Başlatma testi ve sonlandırma testi hakkında aşağıdakilere göz önünde olun:

- Yük testi süresini yineleme sayısı yerine zamana göre belirtebilirsiniz. Bu durumda, yük testi çalıştırma süresi tamamlandığında, sonlandırma testi çalıştırılmaz.

- Başlatma testi bir birim testi veya bir Web performans testi ise, başlatma testinin tamamlanmasından sonraki TestContext veya WebTestContext içerisinde, nesnesi durumu kaydedilir. Daha sonra test karışımında testlerin yinelemeleri için başlangıç bağlamı olarak kullanılacaktır.

- Yeni kullanıcılar, yeni kullanıcıların senaryo özelliği yüzdesi bölümünde tanımlandığı gibi, her zaman başlatma testini, test karışımından bir testin bir yinelemesini ve sonlandırma testini yürütür.

## <a name="see-also"></a>Ayrıca bkz.

- [Test çalıştıran bir Sanal Kullanıcı olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Sanal Kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Yük testi senaryosuna hangi testlerin ekleneceğini belirlemek için test karışımını düzenleyin](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
- [Bir senaryoda test karışımı modelini değiştirme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
