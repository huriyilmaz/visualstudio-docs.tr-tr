---
title: Yük testi oluşturma ve çalıştırma
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
ms.openlocfilehash: 780485a4d42cad574cddaaa5a9ae51a65a1a9b7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093630"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Walkthrough: Birim testleri içeren bir yük testi oluşturma ve çalıştırma

Bu izlenme de birim testleri içeren bir yük testi oluşturun.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bu iz, Visual Studio Enterprise'ı kullanarak bir yük testi oluşturup çalıştırmada size yol alar. Yük testi, web performans testleri ve birim testlerinden oluşan bir kapsayıcıdır. Yeni Yük Testi **Sihirbazı**ile yük testleri oluşturursunuz.

Yük testi, istenen yük simülasyonu oluşturmak için değiştirilebilen birçok çalışma zamanı özelliğini de ortaya çıkarır. Bu izbarada, yük testine birim testleri eklemek için **Yeni Yük Testi Sihirbazı'nı** kullanırsınız.

Bu izlenecek yolda, aşağıdaki görevleri tamamlayacaktır:

- Birim testleri kullanan bir yük testi oluşturun.

- Bazı yük testi ayarlarını değiştirin.

- Bir yük testi çalıştırın.

- [Walkthrough:](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) Create through'daki adımları gerçekleştirin: Bazı birim testleri içeren bir web performansı ve yük testi projesi içeren basit bir C# sınıfı kitaplığı oluşturmak için yönetilen kod için birim testleri oluşturma ve çalıştırma.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Yeni Yük Testi Sihirbazı'nı kullanarak birim testleri içeren bir yük testi oluşturma

### <a name="to-start-the-new-load-test-wizard"></a>Yeni Yük Testi Sihirbazı'nı başlatmak için

1. [Yük testi projesi oluştur'da](../test/quickstart-create-a-load-test-project.md)açıklanan Web performansı ve yük test **araçları** bileşenini yüklediğinizden emin olun.

1. Walkthrough'da oluşturduğunuz Banka çözümünü [açın: Yönetilen kod için birim testleri oluşturma ve çalıştırma.](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

1. **Çözüm Gezgini'nde,** Banka çözüm düğümü için kısayol menüsünü açın, **Ekle'yi**seçin ve ardından **Yeni Proje'yi**seçin.

     **Yeni Proje Ekle** iletişim kutusu görüntülenir.

1. Yeni **Proje Ekle** iletişim kutusunda **Visual C#** seçeneğini genişletin ve **Test'i**seçin. Şablonlar **listesinden, Web Performansı ve Yük Testi Projesi'ni** `BankLoadTest`seçin ve **Ad** alanında . **Tamam'ı**seçin.

     BankLoadTest web performansı ve yük testi projesi çözüme eklenir.

1. Yeni BankLoadTest web performansı ve yük testi projesi için kısayol menüsünü açın, **Ekle'yi**seçin ve ardından **Yük Testi'ni**seçin.

1. **Yeni Yük Testi Sihirbazı** başlar.

1. **Yeni Yük Testi Sihirbazı'nın** Hoş **Geldiniz** sayfası ilk sayfadır.

1. **İleri**’yi seçin.

### <a name="to-edit-settings-for-load-test-scenario"></a>Yük testi senaryosu için ayarları yeniden yüklemek için

1. Yükleme testi senaryosu metin **kutusunun adını girin'de** **ScenarioSample**yazın.

     *Senaryo* bir gruplandırma mekanizmasıdır. Bir dizi testten ve bu testleri yük altında çalıştırmak için özelliklerden oluşur.

2. Zaman **Profilini Ayarla Think** ' e `Use normal distribution centered on recorded think times`. Düşünme süreleri, bir kullanıcının bir sonraki sayfaya geçmeden önce bir web sayfasını düşüneceği zamanı temsil eder.

1. Bittiğinde **İleri'yi** seçin.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Test senaryosu için yük deseni ayarını düzenlemek için

1. **Adım yüklemesini**seçin.

    > [!NOTE]
    > Sabit ve adım olmak gibi iki tür yük deseni arasından seçim yapabilirsiniz. Her tür yük testi kendi işlevi vardır, ancak bu iznin amaçları için **Adım yük**seçin.

2. **Başlat kullanıcı sayısını** 10 kullanıcıya ayarlayın.

3. **Adım süresini** 10 saniyeye ayarlayın.

4. **Adım kullanıcı sayısını** 10 kullanıcı/adım olarak ayarlayın.

5. **Maksimum kullanıcı sayısını** 100 kullanıcıya ayarlayın.

6. **İleri**’yi seçin.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Senaryo için test karışımı modelini seçmek için

1. Test **karışımı nasıl modellenmelidir**altında, **testin toplam sayısına göre**seçin.

2. **İleri**’yi seçin.

### <a name="to-add-unit-tests-to-the-scenario"></a>Senaryoya birim testleri eklemek için

1. Bir sonraki **adım, bir yük testi senaryosuna test eklemek ve test karışımını**düzenlemektir.

2. Testleri seçmek için **Ekle'yi** seçin.

3. Web performansı ve yük testi projesindeki tüm web performans testlerini ve birim testlerini listeleyen **Kullanılabilir Testler** bölmesinde listelenen **CreditTest** birim testlerini seçin.

4. **Seçili Testler** bölmesine **CreditTest** birim testini eklemek için oku seçin.

5. **DebitTest** ve **FreezeAccountTest** birim testleri için 3 ve 4 adımlarını yineleyin.

6. Üç birim testini eklemeyi tamamladığınızda **Tamam'ı**seçin.

     Size test karışımı ile sunulur.

7. Test dağıtımını ayarlamak için **CreditTest** için **Dağıtım** altında kaydırıcıyı biraz sağa taşıyın. Diğer kaydırıcıların otomatik olarak sola hareket ettiğine dikkat edin, böylece dağılım %100'de kalır.

8. **İleri**’yi seçin.

### <a name="to-select-network-mix-for-test-scenario"></a>Test senaryosu için ağ karışımını seçmek için

1. Ağ bant genişliği karışımına eklemek için LAN bağlantı türünü seçin.

     Daha fazla ağ türü ekleyebilirsiniz. Test dağıtımını ve ağırlığını ayarlamak için kaydırıcıları kullanın.

2. **İleri**’yi seçin.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Yük testi çalışması sırasında sayaç kümeleriyle izlenecek bilgisayarları belirtmek için

1. **İleri**’yi seçin.

     Sayaç kümeleri hakkında daha fazla bilgi için [bkz.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)

### <a name="to-edit-run-setting-for-load-test"></a>Yük testi için çalışma ayarını ayarlamak için

1. Yük testi nizi test *etmek* için Test **Süresini Doldur'u** seçin ve ardından **Çalışma Süresini** 2 dakikaya ayarlayın.

     Yük testlerinizi oluşturduğunuzda, kısa, hafif bir yük testi çalıştırarak her şeyin doğru şekilde yapılandırıldığı ve beklendiği gibi çalıştığını doğrulamak iyi bir uygulamadır. Bu işlem *duman testi*olarak bilinir.

2. **Son**’u seçin. **Yük testiniz Load Test Editor'da**açılır.

## <a name="run-the-load-test"></a>Yük testini çalıştırın
 Yük testini oluşturduktan sonra, banka uygulamanızın yük simülasyonuna nasıl yanıt veriş olduğunu görüntülemek için çalıştırın. Bir yük testi çalışırken, **Yük Testi Çözümleyicisi** penceresini görürsünüz.

### <a name="to-run-the-load-test"></a>Yük testini çalıştırmak için

1. **Load Test Editor'da**açık olan Load testi yle araç çubuğundaki yeşil **Test düğmesini** seçin. Yük testiniz devam etmeye başlar.

2. Test simülasyonunuzun herhangi bir eşiği aşması durumunda, bir eşik ihlalini belirtmek için ağaç denetim düğümlerinde simgeler görünür. Hatalar kırmızı daire kaplaması var, uyarılar sarı üçgen bindirme var. Eşiğe aşan bir sayaç bulabilir ve simgeyi grafiğe sürükleyerek grafiği çizebilirsiniz. Test çalışırken bunu yapabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryosuna hangi testlerin dahil edilemesini belirtmek için test karışımını düzenleme](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Sanal ağ türlerini belirtin](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Yük testi senaryolarını edin](../test/edit-load-test-scenarios.md)
- [Sanal kullanıcı etkinliklerini modellemek için yük modellerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Test çalıştıran sanal bir kullanıcının olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
