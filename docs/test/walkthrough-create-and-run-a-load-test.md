---
title: Yük testi oluşturma ve çalıştırma
description: Birim testleri içeren bir yük testi oluşturmayı öğrenin. Visual Studio Enterprise kullanarak yük testleri oluşturup çalıştırın.
ms.custom: SEO-VS-2020
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bdcd96e8fc87a7627689af1c67a81b69b2ecee72
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598269"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>İzlenecek yol: birim testlerini içeren bir yük testi oluşturma ve çalıştırma

Bu izlenecek yolda, birim testlerini içeren bir yük testi oluşturursunuz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bu izlenecek yol, Visual Studio Enterprise kullanarak bir yük testi oluşturma ve çalıştırma adımlarında size yol göstermiştir. Yük testi, Web performans testlerinin ve birim testlerinin bir kapsayıcısıdır. **Yeni Yük Testi Sihirbazı** yük testleri oluşturursunuz.

Yük testi, istenen yük simülasyonu oluşturmak için değiştirilebilen birçok çalışma zamanı özelliği de sunar. Bu izlenecek yolda, bir yük testine birim testleri eklemek için **yeni Yük Testi Sihirbazı** kullanırsınız.

Bu kılavuzda, aşağıdaki görevleri tamamlayacaksınız:

- Birim testlerini kullanan bir yük testi oluşturun.

- Bazı yük testi ayarlarını değiştirin.

- Bir yük testi çalıştırın.

- [Izlenecek yol: yönetilen kod için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) , bir Web performansı ve yük testi projesi içeren basit bir C# sınıf kitaplığı oluşturmak için bu adımları uygulayın.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Yeni Yük Testi Sihirbazı kullanarak birim testleri içeren bir yük testi oluşturma

### <a name="to-start-the-new-load-test-wizard"></a>Yeni Yük Testi Sihirbazı başlatmak için

1. [Yük testi projesi oluşturma](../test/quickstart-create-a-load-test-project.md)bölümünde açıklanan **Web performans ve yük testi araçları** bileşenini yüklediğinizden emin olun.

1. [Izlenecek yol: yönetilen kod için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)bölümünde oluşturduğunuz banka çözümünü açın.

1. **Çözüm Gezgini**' de, banka çözümü düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

     **Yeni Proje Ekle** iletişim kutusu görüntülenir.

1. **Yeni Proje Ekle** iletişim kutusunda, **Visual C#** ' yi genişletin ve **Test**' i seçin. Şablonlar listesinden **Web performansı ve yük testi projesi** ' ni seçin ve **ad** alanına yazın `BankLoadTest` . **Tamam ' ı** seçin.

     BankLoadTest web performans ve yük testi projesi çözüme eklenir.

1. Yeni BankLoadTest web performans ve yük testi projesi için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yük testi**' ni seçin.

1. **Yeni Yük Testi Sihirbazı** başlar.

1. **Yeni Yük Testi Sihirbazı** **hoş geldiniz** sayfası ilk sayfasıdır.

1. **İleri**’yi seçin.

### <a name="to-edit-settings-for-load-test-scenario"></a>Yük testi senaryosuna yönelik ayarları düzenlemek için

1. **Yük testi senaryosu için bir ad girin** metin kutusuna **ScenarioSample** yazın.

     *Senaryo* , gruplandırma mekanizmasıdır. Test kümesinden ve bu testleri yük altında çalıştırmaya yönelik özelliklerden oluşur.

2. **Zaman profilini göz önünde** bulundurun `Use normal distribution centered on recorded think times` . Düşünme süreleri, bir kullanıcının sonraki sayfaya geçmeden önce bir Web sayfasını ele aldığı süreyi temsil eder.

1. İşiniz bittiğinde **İleri ' yi** seçin.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Test senaryosu için yük düzen ayarını düzenlemek için

1. **Adım yükle**' yi seçin.

    > [!NOTE]
    > İki tür yük düzeni arasından seçim yapabilirsiniz: sabit ve adım. Her tür, yük testinde kendi işlevine sahiptir, ancak bu izlenecek yol için **adım yükle**' yi seçin.

2. **Başlangıç Kullanıcı sayısını** 10 Kullanıcı olarak ayarlayın.

3. **Adım süresini** 10 saniyeye ayarlayın.

4. **Adım kullanıcı sayısını** 10 Kullanıcı/adım olarak ayarlayın.

5. **Maksimum kullanıcı sayısını** 100 Kullanıcı olarak ayarlayın.

6. **İleri**’yi seçin.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Senaryonun test karışımı modelini seçmek için

1. **Test karışımı modellenmesi gereken** altında, **Toplam test sayısına göre**' yi seçin.

2. **İleri**’yi seçin.

### <a name="to-add-unit-tests-to-the-scenario"></a>Senaryoya birim testleri eklemek için

1. Bir sonraki adım, **Yük testi senaryosuna testler eklemek ve test karışımını düzenlemek** için kullanılır.

2. Testleri seçmek için **Ekle** ' yi seçin.

3. Web performansı ve yük testi projesindeki tüm Web performans testlerini ve birim testlerini listeleyen **kullanılabilir testler** bölmesinde listelenen **CreditTest** birim testlerini seçin.

4. **CreditTest** birim testini **Seçili testler** bölmesine eklemek için oku seçin.

5. **DebitTest** ve **FreezeAccountTest** birim testleri için 3 ve 4 numaralı adımları tekrarlayın.

6. Üç birim testini eklemeyi bitirdiğinizde **Tamam**' ı seçin.

     Test karışımı sunulur.

7. Test dağıtımını ayarlamak için kaydırıcıyı **CreditTest** **' ın altında** olacak şekilde sağa taşıyın. Dağıtımın %100 ' de kalması için diğer Kaydırıcıların otomatik olarak sola hareket ettiğini unutmayın.

8. **İleri**’yi seçin.

### <a name="to-select-network-mix-for-test-scenario"></a>Test senaryosu için ağ karışımını seçmek için

1. Ağ bant genişliği karışımına eklenecek LAN bağlantı türünü seçin.

     Daha fazla ağ türü ekleyebilirsiniz. Test dağıtımını ve ağırlığı ayarlamak için kaydırıcıları kullanın.

2. **İleri**’yi seçin.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Yük testi çalışması sırasında sayaç kümeleriyle izlenecek bilgisayarları belirtmek için

1. **İleri**’yi seçin.

     Sayaç kümeleri hakkında daha fazla bilgi için bkz. [bir yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Yük testi için çalışma ayarını düzenlemek için

1. Yük testi **süresi** ' ni seçin ve ardından Yük testinizi *duman test* etmek için **çalışma süresini** 2 dakikaya ayarlayın.

     Yük testlerinizi oluştururken, her şeyin doğru şekilde yapılandırıldığını ve kısa, hafif bir yük testi çalıştırarak beklendiği gibi çalıştığını doğrulamak iyi bir uygulamadır. Bu işlem *duman testi* olarak bilinir.

2. **Son**’u seçin. Yük testiniz **Yük Testi Düzenleyicisi** açılır.

## <a name="run-the-load-test"></a>Yük testini çalıştırma
 Yük testini oluşturduktan sonra, banka uygulamanızın yük benzetimine nasıl yanıt vereceğini görüntülemek için çalıştırın. Yük testi çalışırken, **Yük Testi Çözümleyicisi** penceresini görürsünüz.

### <a name="to-run-the-load-test"></a>Yük testini çalıştırmak için

1. **Yük Testi Düzenleyicisi** bir yük testi açıkken, araç çubuğundaki yeşil **Test Çalıştır** düğmesini seçin. Yük testiniz çalışmaya başlar.

2. Test simülasyonu herhangi bir eşiği aşarsa, bir eşik ihlali göstermek için ağaç denetimi düğümlerinde simgeler görünür. Hataların kırmızı bir daire kaplaması var, uyarılar sarı bir üçgen yer paylaşımına sahiptir. Eşiği aşan bir sayaç bulabilir ve simgeyi grafiğe sürükleyerek grafiğe ekleyebilirsiniz. Test çalışırken bunu yapabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryosuna hangi testlerin ekleneceğini belirlemek için test karışımını düzenleyin](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Sanal ağ türlerini belirtin](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Yük testi senaryolarını Düzenle](../test/edit-load-test-scenarios.md)
- [Sanal Kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Test çalıştıran bir Sanal Kullanıcı olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
