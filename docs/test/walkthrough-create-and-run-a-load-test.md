---
title: Yük testi oluşturma ve çalıştırma
description: Birim testleri içeren bir yük testi oluşturma hakkında bilgi. Yük testleri oluşturmak ve çalıştırmak için Visual Studio Enterprise.
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
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: c42c6a98ab9b453131af383b5b39a1c12ed9e895
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038324"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Adım adım kılavuz: Birim testleri içeren bir yük testi oluşturma ve çalıştırma

Bu kılavuzda birim testlerini içeren bir yük testi oluşturabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bu kılavuzda, yük testi oluşturma ve çalıştırma adımları, Visual Studio Enterprise. Yük testi, web performansı testlerinin ve birim testlerinin bir kapsayıcısıdır. Yük testlerini New Yük Testi Sihirbazı **.**

Yük testi, istenen yük benzetimini oluşturmak için değiştirilebiliyor birçok çalışma zamanı özelliği de gösterir. Bu kılavuzda, bir yük **testini Yük Testi Sihirbazı** için New Yük Testi Sihirbazı'yi kullanırsiniz.

Bu kılavuzda aşağıdaki görevleri tamamlayabilirsiniz:

- Birim testlerini kullanan bir yük testi oluşturun.

- Yük testi ayarlarından bazılarını değiştirin.

- Yük testi çalıştırma.

- Kılavuz: Yönetilen [](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) kod için birim testleri oluşturma ve çalıştırma makalesinde yer alan adımları gerçekleştirerek içinde bazı birim testleri içeren web performansı ve yük testi projesi içeren basit bir C# sınıf kitaplığı oluşturun.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>New Yük Testi Sihirbazı kullanarak birim testleri içeren bir yük testi Yük Testi Sihirbazı

### <a name="to-start-the-new-load-test-wizard"></a>Yeni Yük Testi Sihirbazı

1. Yük testi projesi oluşturma konusunda açıklanan **Web performansı ve yük testi araçları** bileşenini [yüklemiş olduğundan emin olun.](../test/quickstart-create-a-load-test-project.md)

1. Adım adım kılavuz: Yönetilen kod için [birim testleri oluşturma ve çalıştırma konusunda oluşturduğunuz Banka çözümünü açın.](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

1. Bu **Çözüm Gezgini,** Banka çözümü düğümünün kısayol menüsünü açın, Ekle'yi **seçin** ve ardından Yeni **oluştur'Project.**

     Yeni **Veri Project** iletişim kutusu görüntülenir.

1. Yeni Dosya **Ekle iletişim Project** Visual C# öğesini genişletin ve **Test'i** **seçin.** Şablon listesinden Web Performansı ve Yük Testi **Project** seçin ve **Ad alanına** `BankLoadTest` yazın. **Tamam'ı seçin.**

     BankLoadTest web performansı ve yük testi projesi çözüme eklenir.

1. Yeni BankLoadTest web performansı ve yük testi projesinin kısayol menüsünü açın, Ekle'yi **ve** ardından Yük **Testi'ni seçin.**

1. Yeni **Yük Testi Sihirbazı** başlar.

1. Yeni **Giriş** sayfasının **Yük Testi Sihirbazı** sayfasıdır.

1. **İleri**’yi seçin.

### <a name="to-edit-settings-for-load-test-scenario"></a>Yük testi senaryosunun ayarlarını düzenlemek için

1. Yük **testi senaryosu için bir ad girin metin kutusuna** **ScenarioSample yazın.**

     Senaryo *bir* gruplama mekanizmasıdır. Bir dizi test ve bu testleri yük altında çalıştırma özellikleri içerir.

2. Time **Profile Think (Zaman Profili Düşünme) olarak** `Use normal distribution centered on recorded think times` ayarlayın. Düşünme süreleri, kullanıcının bir sonraki sayfaya gitmeden önce bir web sayfasını takip etme zamanlarını temsil ediyor.

1. Bitirdikten **sonra** Sonraki'yi seçin.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Test senaryosu için yük düzeni ayarını düzenlemek için

1. Adım **yükleme'yi seçin.**

    > [!NOTE]
    > İki tür yük deseni seçebilirsiniz: sabit ve adım. Her türün yük test etme işlevi vardır, ancak bu izlenecek yol için Adım **yükleme'yi seçin.**

2. Kullanıcı **sayısını başlat'a** 10 kullanıcı ayarlayın.

3. Adım **süresi'i** 10 saniye olarak ayarlayın.

4. Adım **kullanıcı sayısı'na** 10 kullanıcı/adım ayarlayın.

5. En **fazla kullanıcı sayısı'nın** 100 kullanıcı olduğunu ayarlayın.

6. **İleri**’yi seçin.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Senaryo için test karışımı modelini seçmek için

1. Test **karışımının modellenesi nasıl olmalı?** altında Toplam test **sayısına göre öğesini seçin.**

2. **İleri**’yi seçin.

### <a name="to-add-unit-tests-to-the-scenario"></a>Senaryoya birim testleri eklemek için

1. Sonraki adım, bir **yük testi senaryosuna test eklemek ve test karışımını düzenlemektir.**

2. Testleri seçmek **için** Ekle'yi seçin.

3. Kullanılabilir Testler **bölmesinde listelenen CreditTest** birim testlerini seçin. Bu bölmede web performansı ve yük testi projesinde tüm web performansı testleri ve birim testleri listelenir. 

4. Seçilen Testler bölmesine **CreditTest** birim testi eklemek için **oku** seçin.

5. **DebitTest** ve **FreezeAccountTest** birim testleri için 3. ve 4. adımları tekrarlayın.

6. Üç birim testi eklemeyi bitirdikten sonra Tamam'ı **seçin.**

     Size test karışımı sunulmaktadır.

7. Test dağıtımını ayarlamak **için** **CreditTest** için Dağıtım'ın altındaki kaydırıcıyı biraz sağa taşıyın. Dağıtımın %100'de kalması için diğer kaydırıcıların otomatik olarak sola doğru hareket eder.

8. **İleri**’yi seçin.

### <a name="to-select-network-mix-for-test-scenario"></a>Test senaryosu için ağ karışımını seçmek için

1. Ağ bant genişliği karışımına eklemek için LAN bağlantı türünü seçin.

     Daha fazla ağ türü ekebilirsiniz. Kaydırıcıları kullanarak test dağıtımını ve ağırlıklarını ayarlayın.

2. **İleri**’yi seçin.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Yük testi çalıştırması sırasında sayaç kümeleriyle izlenir bilgisayarları belirtmek için

1. **İleri**’yi seçin.

     Sayaç kümeleri hakkında daha fazla bilgi için [bkz. Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)

### <a name="to-edit-run-setting-for-load-test"></a>Yük testi için çalıştırma ayarını düzenlemek için

1. Yük **testi süresini yükle'yi** seçin ve yük **testinde** duman testi yapmak için Çalıştırma Süresi'ne 2 *dakika* ayarlayın.

     Yük testlerinizi derlemek, kısa ve hafif bir yük testi çalıştırarak her şeyin doğru yapılandırıldığından ve beklendiği gibi çalıştırıldığından emin olmak iyi bir uygulamadır. Bu işlem duman testi *olarak bilinir.*

2. **Son**’u seçin. Yük testiniz, **Yük Testi Düzenleyicisi.**

## <a name="run-the-load-test"></a>Yük testini çalıştırma
 Yük testini oluşturduktan sonra, banka uygulamanın yük simülasyonu yanıtını görüntülemek için çalıştırın. Yük testi çalışırken Yük Testi **Çözümleyicisi penceresini** görebilirsiniz.

### <a name="to-run-the-load-test"></a>Yük testini çalıştırmak için

1. komut çubuğunda yük testi açık **Yük Testi Düzenleyicisi** araç çubuğundaki **yeşil Renkli Testi** Çalıştır düğmesini seçin. Yük testi çalışmaya başlar.

2. Test benzetiminiz eşikleri aşarsa ağaç denetim düğümlerde eşik ihlaline işaret etmek için simgeler görünür. Hatalarda kırmızı daire katmanlı, uyarılarda ise sarı üçgen katman vardır. Eşiği aşan bir sayaç bulabilir ve simgeyi grafın üzerine sürükleyerek grafiği grafitebilirsiniz. Test çalışırken bunu da yapabiliriz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryosuna hangi testlerin dahil olduğunu belirtmek için test karışımını düzenleyin](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Sanal ağ türlerini belirtme](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Sanal kullanıcı etkinliklerini modellemek için yük desenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Test çalıştıran bir sanal kullanıcının olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
