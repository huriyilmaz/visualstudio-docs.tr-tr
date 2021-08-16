---
title: Yük testi için bir web sitesinin gerçek dünya kullanımına öykün
description: Yük test etmekte olduğunu bir web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını daha doğru tahmin etmek için yük modelleme seçeneklerini kullanın.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 74ec63a85657ad91982627a3b717547df07b469e93b33aaf3e2ef99109c78d49
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366738"
---
# <a name="test-mix-models-overview"></a>Test karışımı modellerini genel bakış

Yük test etmekte olduğunu bir web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını daha doğru tahmin etmek için yük modelleme seçeneklerini kullanırız. Doğru bir yük modelini temel alan bir yük testi yanıltıcı sonuçlar oluşturayana kadar bunu yapmak önemlidir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Test karışımı modeli geliştirmeleri

Test Yük Testi Düzenleyicisi veya test karışımı modeli sihirbazını kullanarak, bir yük testi senaryosu için aşağıdaki test karışımı türlerini belirtebilirsiniz. Daha fazla bilgi için [bkz. Bir senaryoda test karışımı modelini değiştirme.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

Yük testi senaryo için aşağıdaki test karışımı modeli seçeneklerine birini belirtebilirsiniz:

- **Toplam test sayısına göre:** Sanal kullanıcı bir test yinelemesi başlatırken hangi web performansının veya birim testinin çalıştırılı olduğunu belirler. Yük testinin sonunda, belirli bir test çalıştırması atanan test dağıtımıyla kaç kez eşlendi? Bir IIS günlüğünde veya üretim verisinde işlem yüzdeleri üzerinde test karışımını kullanıyorken bu test karışımı modelini kullanın. Daha fazla bilgi için [bkz. Başlatan testleri temel alan yüzde.](#BasedOnTestsStarted)

- **Sanal kullanıcı sayısına göre:** Belirli bir web performansını veya birim testini çalıştıracak sanal kullanıcıların yüzdesini belirler. Yük testinin herhangi bir noktasında, belirli bir testi çalıştıran kullanıcı sayısı atanan dağıtımla eştir. Test karışımını belirli bir testi çalıştıran kullanıcıların yüzdesine bağlıyken bu test karışımı modelini kullanın. Daha fazla bilgi için [bkz. Sanal kullanıcıları temel alan yüzde.](#PercentageBasedonVirtualUsers)

- **Kullanıcı hızına göre:** Yük testi boyunca, her web performans testi veya birim testi, kullanıcı başına saat başına belirtilen sayıda çalıştırtır. Sanal kullanıcıların yük testi boyunca belirli bir hızda test çalıştırmalarını istediğiniz durumlarda bu test karışımı modelini kullanın. Daha fazla bilgi için [bkz. Pacing test mix](#PacingTestMix).

    > [!TIP]
    > Yüzde test karışımını **ne zaman ve** sanal kullanıcıları temel alan **Yüzde'yi ne zaman seçersiniz?** Bu iki seçenek arasındaki fark, test karışımında bazı testlerin süresi diğer testlere göre çok daha uzun olduğunda önemlidir. Bu durumda, sanal kullanıcılara göre **yüzde'yi seçmeniz gerekir.** Bu seçim, çok fazla sayıda kullanıcının uzun süreli testler çalıştırma olasılığını artıran bir test çalıştırması önlemeye yardımcı olur. Ancak, testlerin hepsi benzer sürelere sahipse, Daha güvenli bir şekilde Test karışımı **yüzdesi'ne seçebilirsiniz.**

- **Sıralı sıralamaya göre:** Her sanal kullanıcı, testlerin senaryoda tanımlandığı sırada web performansını veya birim testlerini çalıştırır. Sanal kullanıcı, yük testi tamamlayana kadar testlerde bu sırayla devam eder. Daha fazla bilgi için bkz. [Sıralı sıra.](#SequentialOrder)

### <a name="percentage-based-on-tests-started"></a><a name="BasedOnTestsStarted"></a> Başlatan testleri temel alan yüzde

Karmada yer alan her test için, testin çalıştırilecek bir sonraki test olarak ne sıklıkta seçileceklerini belirleyen bir yüzde belirtsiniz. Örneğin, üç teste aşağıdaki yüzde değerlerini at uygun olabilir:

- TestA (%50)

- TestB (%35)

- TestC (%15)

Bu ayarı kullanırsanız, başlatacak bir sonraki test atanan yüzdeleri temel almaktadır. Bunu, şu anda her testi çalıştıran sanal kullanıcı sayısını dikkate almadan yapacaksınız.

### <a name="percentage-based-on-virtual-users"></a><a name="PercentageBasedonVirtualUsers"></a> Sanal kullanıcıları temel alan yüzde
Bu test karışımı modeli, belirli bir testi çalıştıracak sanal kullanıcıların yüzdesini belirler. Bu test karışımı modelini kullanırsanız, başlatacak sonraki test yalnızca atanan yüzdeleri değil, aynı zamanda belirli bir testi çalıştıran sanal kullanıcıların yüzdesini de temel almaktadır. Yük testinin herhangi bir noktasında, belirli bir testi çalıştıran kullanıcı sayısı atanan dağıtımla mümkün olduğunca yakından eştir.

### <a name="pacing-test-mix"></a><a name="PacingTestMix"></a> Test karışımını ilerleme

Bir ilerleme testi karışımı belirtirsiniz, test karışımında her bir test için her sanal kullanıcı için bir test yürütme hızı ayarlayın. Her test için bu hız, sanal kullanıcı başına saat başına çalıştırıla testler olarak ifade edildi. Örneğin, aşağıdaki pacing test karışımını aşağıdaki testlere at uygun şekilde at uygun olabilir:

- TestA: Kullanıcı başına saatte 4 test

- TestB: Kullanıcı başına saat başına 2 test

- TestC: Kullanıcı başına saat başına 0,125 test

Hız testi karışımı modelini kullanırsanız yük testi çalışma zamanı altyapısı, testleri başlatan gerçek hızın belirtilen orandan daha düşük veya ona eşit olduğunu garantiler. Atanan numaranın tamamlanması için testler çok uzun süre çalıştırıldısa bir hata döndürülür.

Test **Yinelemeleri Arasında Düşünme Süresi** ayarı, bir ilerleme testi karışımını kullanıyorsanız geçerli değildir.

#### <a name="apply-distribution-to-pacing-delay"></a>Hızın gecikmesine dağıtım uygulama
Bir yük testi **senaryosunda Dağıtımı Pacing Delay'e** Uygula özelliğinin değeri true veya false olarak ayarlanmış olabilir:

- **Doğru:** Senaryo, Test Karışımını Düzenle iletişim kutusundaki  Kullanıcı Başına Test Sayısı sütunundaki değer tarafından belirtilen tipik istatistiksel dağıtım **gecikmelerini** uygulayacak. Daha fazla bilgi için, [test çalıştıran bir sanal kullanıcının olasılığını belirtmek için bkz. Metin karışımı modellerini düzenleme.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

   Örneğin, test karışımını düzenle **iletişim** kutusunda Test  Karışımını Düzenle iletişim kutusunda Kullanıcı Başına Test Sayısı değerinin saatte 2 kullanıcı olarak ayar olduğunu varsayalım. Hızı **Geciktirme özelliğine Dağıtımı** Uygula özelliği **True** olarak ayarlanırsa, testler arasındaki bekleme süresine tipik bir istatistiksel dağılım uygulanır. Testler yine de saatte 2 test çalıştıracak ancak aralarında 30 dakika olması gerekmez. İlk test 4 dakika sonra, ikinci test ise 45 dakika sonra çalışmasına neden olabilir.

- **Yanlış:** Testler, Test Karışımını Düzenle iletişim kutusundaki  Kullanıcı Başına Test Sayısı sütununda belirtilen değer için belirttiğiniz **hızda** ecek. Daha fazla bilgi için, [test çalıştıran bir sanal kullanıcının olasılığını belirtmek için bkz. Metin karışımı modellerini düzenleme.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

   Örneğin, test karışımını düzenle **iletişim** kutusunda Test  Karışımını Düzenle iletişim kutusunda Kullanıcı Başına Test Sayısı değerinin saatte 2 kullanıcı olarak ayar olduğunu varsayalım. Pacing **Delay'e Dağıtımı** Uygula özelliği **False** olarak ayarlanırsa, testlerinizi çalıştıracaksanız temel olarak hiçbir şey vermiyor olursanız. Test 30 dakikada bir çalıştıracak. Bu, saatte 2 test yürütmeyi sağlar.

  Daha fazla bilgi için, [bkz. How to: Apply distribution to pacing delay when using a user pace test mix model](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

### <a name="sequential-order"></a><a name="SequentialOrder"></a> Sıralı sıra
Sıralı test sırasına göre seçeneğinin belirlenerek her sanal kullanıcı, senaryonun tüm testlerini testlerin tanımlandığı sırayla çalıştıracak.

## <a name="test-iterations-property"></a>Test yinelemeleri özelliği
Run Ayarlar özelliklerinde Test Yinelemeleri özelliği için bir değer belirtebilirsiniz. Bu değer, yük testinde çalıştıracak test yinelemelerinin sayısıdır. Belirtilen sayıda test yinelemesi başlatıldıktan sonra, yük profillerinin herhangi bir ayarına rağmen ek test yinelemeleri başlatilmez. Belirtilen test yinelemelerinin sayısı tamamlandıktan sonra yük testi sona erer. Daha fazla bilgi [için, bkz. How to: Specify the number](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)of test iterations in a run setting .

## <a name="initialize-and-terminate-tests"></a>Testleri başlatma ve sonlandırma
Her sanal kullanıcının yük testi oturumunun başında ve sonunda çalıştıracak testleri seçin. Daha fazla bilgi için, [test çalıştıran bir sanal kullanıcının olasılığını belirtmek için bkz. Metin karışımı modellerini düzenleme.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

- **Testini başlatma.** Bu test, test karışımında testlerden herhangi biri çalıştırılamadan önce her sanal kullanıcı tarafından sınanacak.

- **Testini sonlandır.** Bu test, belirli bir sanal kullanıcı için tüm testler çalıştırktan sonra sınanr.

  Başlatma testi ve sonlandırma testi hakkında aşağıdakilere dikkat edin:

- Yük testi süresini yineleme sayısı yerine zaman olarak belirtebilirsiniz. Bu durumda, yük testi çalıştırma süresi tamamlandığında, sonlandırma testi çalıştırılmaz.

- Başlatma testi bir birim testi veya web performans testi, TestContext veya WebTestContext durumu ise, başlatma testi tamamlandıktan sonra nesne kaydedilir. Ardından test karışımında test yinelemeleri için başlangıç bağlamı olarak kullanılacaktır.

- Yeni Kullanıcılar, Yeni Kullanıcıların Yüzdesi senaryo özelliğinde tanımlandığı gibi her zaman başlatma testini, test karışımından bir testin yinelemesini ve sonlandırma testini yürütün.

## <a name="see-also"></a>Ayrıca bkz.

- [Test çalıştıran bir sanal kullanıcının olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Sanal kullanıcı etkinliklerini modellemek için yük desenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Yük testi senaryosuna hangi testlerin dahil olduğunu belirtmek için test karışımını düzenleyin](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
- [Bir senaryoda test karışımı modelini değiştirme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
