---
title: Yük testi için bir web sitesinin Gerçek Dünya Kullanımını taklit etme
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589610"
---
# <a name="test-mix-models-overview"></a>Test mix modellerine genel bakış

Yük testi yaptığınız bir web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını daha doğru tahmin etmek için yük modelleme seçeneklerini kullanırsınız. Bunu yapmak önemlidir, çünkü doğru bir yük modeline dayanmayan bir yük testi yanıltıcı sonuçlar oluşturabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Test karışımı modeli geliştirmeleri

Yük Testi Düzenleyicisi'ni veya test karışımı modeli sihirbazını kullanarak, yük testi senaryosu için aşağıdaki test karışımı türlerini belirtebilirsiniz. Daha fazla bilgi için bkz: [Bir senaryodaki test karışımı modelini değiştir.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

Yük testi senaryonuz için aşağıdaki test karışımı model seçeneklerinden birini belirtebilirsiniz:

- **Toplam test sayısına göre:** Sanal bir kullanıcı bir test yinelemesi başlattığında hangi web performansının veya birim testinin çalıştırılüster belirler. Yükleme testinin sonunda, belirli bir test çalışmasının atanan test dağılımıyla kaç kez eşleştik. Test karını bir IIS günlüğündeki veya üretim verilerindeki işlem yüzdelerine dayandırıyorken bu test karışımı modelini kullanın. Daha fazla bilgi için, [başlatılan testlere göre Yüzde'ye](#BasedOnTestsStarted)bakın.

- **Sanal kullanıcı sayısına göre:** Belirli bir web performansını veya birim testini çalıştıracak sanal kullanıcıların yüzdesini belirler. Yükleme testinin herhangi bir noktasında, belirli bir testi çalıştıran kullanıcı sayısı atanan dağıtımla eşleşir. Test karını belirli bir testi çalıştıran kullanıcıların yüzdeye dayarken bu test karışımı modelini kullanın. Daha fazla bilgi için [sanal kullanıcılara dayalı Yüzde'ye](#PercentageBasedonVirtualUsers)bakın.

- **Kullanıcı hızına göre:** Yükleme testi boyunca, her web performans testi veya birim testi, kullanıcı başına saat başına belirli sayıda kez çalıştırılır. Sanal kullanıcıların yükleme testi boyunca testi belirli bir hızda çalıştırmasını istediğinizde bu test karışımı modelini kullanın. Daha fazla bilgi için [Pacing test karışımına](#PacingTestMix)bakın.

    > [!TIP]
    > Yüzde test **karışımını** ne zaman ve **sanal kullanıcılara göre Yüzde'yi**ne zaman seçersiniz? Test karışımındaki bazı testler diğer testlere göre çok daha uzun bir süreye sahipolduğunda, bu iki seçenek arasındaki fark önemlidir. Bu durumda, büyük olasılıkla **sanal kullanıcılara göre Yüzde**seçmelisiniz. Bu seçim, çok fazla kullanıcının uzun süreli testler çalıştıracağı olasılığın arttığı bir test çalışmasını önlemeye yardımcı olur. Ancak, testlerin tümü benzer sürelere sahipse, **yüzde test karışımını**daha güvenli bir şekilde seçebilirsiniz.

- **Sıralı sıraya göre:** Her sanal kullanıcı, testlerin senaryoda tanımlandığı sırada web performansını veya birim testlerini çalıştırZ. Sanal kullanıcı, yükleme testi tamamlanana kadar bu sırada testler boyunca bisiklet sürmeye devam ediyor. Daha fazla bilgi için [sıralı sıraya](#SequentialOrder)bakın.

### <a name="percentage-based-on-tests-started"></a><a name="BasedOnTestsStarted"></a>Başlatılan testlere göre yüzde

Karışımdaki her test için, bir sonraki test olarak testin ne sıklıkta seçili olduğunu belirleyen bir yüzde belirtebilirsiniz. Örneğin, aşağıdaki yüzde değerlerini üç teste atayabilirsiniz:

- Testa (%50)

- TestB (%35)

- TestC (%15)

Bu ayarı kullanırsanız, başlatılacak bir sonraki test atanan yüzdeleri temel atanır. Bunu, şu anda her testi çalıştıran sanal kullanıcı sayısını hesaba katmadan yaparsınız.

### <a name="percentage-based-on-virtual-users"></a><a name="PercentageBasedonVirtualUsers"></a>Sanal kullanıcılara dayalı yüzde
Bu test karışımı modeli, belirli bir testi çalıştıracak sanal kullanıcıların yüzdesini belirler. Bu test karışımı modelini kullanırsanız, başlatılacak bir sonraki test yalnızca atanan yüzdelere değil, aynı zamanda belirli bir testi çalıştıran sanal kullanıcıların yüzdesine de dayanır. Yükleme testinin herhangi bir noktasında, belirli bir testi çalıştıran kullanıcı sayısı atanan dağıtımla mümkün olduğunca yakın eşleşir.

### <a name="pacing-test-mix"></a><a name="PacingTestMix"></a>Pacing test karışımı

Bir pacing test karışımı belirtirseniz, test karışımındaki her test için her sanal kullanıcı için bir test yürütme hızı belirlersiniz. Her test için bu oran, sanal kullanıcı başına saat başına çalıştırılan testler olarak ifade edilir. Örneğin, aşağıdaki pacing test karışımını aşağıdaki testlere atayabilirsiniz:

- TestA: Kullanıcı başına saatte 4 test

- TestB: Kullanıcı başına saatte 2 test

- TestC: Kullanıcı başına saat başına 0,125 test

Pacing test mix modelini kullanırsanız, yük testi çalışma zamanı motoru, testlerin başlatıldığu gerçek hızın belirtilen orandan daha az veya eşit olduğunu garanti eder. Atanan sayının tamamlanması için testler çok uzun süre çalıştırılırsa, bir hata döndürülür.

Bir pacing test karışımı kullandığınızda **Test Yinelemeleri Arasındaki Düşünme Süresi** ayarı geçerli değildir.

#### <a name="apply-distribution-to-pacing-delay"></a>Pacing gecikmesine dağıtım uygulayın
Yük testi senaryosunda **Pacing Delay özelliğine Uygula Dağıtımının** değeri doğru veya yanlış olarak ayarlanabilir:

- **True**: Senaryo, **Test Mix'i Düzenleme** iletişim kutusunda, Kullanıcı Başına Saat Başına **Testler** sütunundaki değere göre belirtilen tipik istatistiksel dağılım gecikmelerini uygular. Daha fazla bilgi için, test [çalıştıran sanal bir kullanıcının olasılığını belirtmek için metin karışımı modellerini edit'e](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)bakın.

   Örneğin, test kümesi için Test Mix'i **düzenleme** iletişim kutusunda saat başına 2 kullanıcıya sahip kullanıcı **başına testleriniz** olduğunu varsayalım. **Pacing Delay özelliğine Dağıtım Uygula** **True**olarak ayarlanmışsa, testler arasındaki bekleme süresine tipik bir istatistiksel dağılım uygulanır. Testler hala saatte 2 test çalışır, ancak mutlaka aralarında 30 dakika olmayacaktır. İlk test 4 dakika sonra, ikinci test 45 dakika sonra da devam edebilir.

- **False**: Testler, **Test Mix'i Düzenleme** iletişim kutusundaki Kullanıcı Başına Saat Başına **Testler** sütunundaki değer için belirttiğiniz belirli hızda çalışır. Daha fazla bilgi için, test [çalıştıran sanal bir kullanıcının olasılığını belirtmek için metin karışımı modellerini edit'e](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)bakın.

   Örneğin, test kümesi için Test Mix'i **düzenleme** iletişim kutusunda saat başına 2 kullanıcıya sahip kullanıcı **başına testleriniz** olduğunu varsayalım. **Pacing Delay özelliğine Dağıtım Uygula** özelliği **False**olarak ayarlanmışsa, testleriniz çalıştırıldığında temelde hiçbir serbestlik vermiyorsunuz. Test her 30 dakikada bir çalışır. Bu, saatte 2 test yürütmenizi sağlar.

  Daha fazla bilgi için [bkz: Nasıl yapılır: Kullanıcı hızı testi mix modelini kullanırken pacing gecikmesine dağıtım uygulayın.](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)

### <a name="sequential-order"></a><a name="SequentialOrder"></a>Sıralı sıralı
Sıralı test sırasına göre temel alma seçeneğini seçmek, her sanal kullanıcının senaryodaki tüm testleri testlerin tanımlandığı sırada çalıştırmalarını sağlar.

## <a name="test-iterations-property"></a>Yinelemeleri test edin
Çalışma Ayarları özelliklerinde, Test Yinelemeleri özelliği için bir değer belirtebilirsiniz. Bu değer, bir yük testinde çalıştırılabilmek için test yinelemelerinin sayısıdır. Belirtilen test yineleme sayısı başlatıldıktan sonra, yük profillerinden herhangi birinin ayarlarına rağmen ek test yinelemeleri başlatılacaktır. Belirtilen test yinelemesayısı tamamlandıktan sonra, yük testi sona erer. Daha fazla bilgi için [bkz: Çalışma ortamındatest yinelemelerinin sayısını belirtin.](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)

## <a name="initialize-and-terminate-tests"></a>Testlerin başlatılması ve sonlandırılması
Her sanal kullanıcının yük testi oturumunun başında ve sonunda çalışacak testleri seçebilirsiniz. Daha fazla bilgi için, test [çalıştıran sanal bir kullanıcının olasılığını belirtmek için metin karışımı modellerini edit'e](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)bakın.

- **Önce başlatma testi**. Bu test, test karışımındaki testlerin herhangi biri çalıştırılmadan önce her sanal kullanıcı tarafından çalıştırılır.

- **Testi sonlandır.** Bu test, belirli bir sanal kullanıcı için tüm testler çalıştırıldıktan sonra çalıştırılır.

  Başlatma testi ve sonlandırma testi hakkında lütfen aşağıdakilere dikkat ediniz:

- Yineleme sayısı yerine yük testi süresini zamana göre belirtebilirsiniz. Bu durumda, yükleme testi çalıştırma süresi tamamlandığında, sonlandırma testi çalıştırılmayacaktır.

- Başlatma testi bir birim testi veya web performans testiise, başlatma testi tamamlandıktan sonra nesne TestContext veya WebTestContext durumu kaydedilir. Daha sonra test karışımı testlerin yinelemeler için başlangıç bağlamı olarak kullanılacaktır.

- Yeni Kullanıcılar, senaryo özelliği Yeni Kullanıcıların Yüzdesi'nde tanımlandığı gibi, her zaman başlatma testini, test karışımından bir test yinelemesini ve sonlandırma testini çalıştırır.

## <a name="see-also"></a>Ayrıca bkz.

- [Test çalıştıran sanal bir kullanıcının olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Sanal kullanıcı etkinliklerini modellemek için yük modellerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Yük testi senaryosuna hangi testlerin dahil edilemesini belirtmek için test karışımını düzenleme](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
- [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md)
- [Senaryoda test karışımı modelini değiştirme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
