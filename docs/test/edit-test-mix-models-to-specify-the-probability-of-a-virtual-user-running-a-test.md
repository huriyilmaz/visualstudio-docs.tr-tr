---
title: Metin Karışımı Modellerini Düzenleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 62c817a2df6c56f70ab2217292feeb545cf66c85
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593219"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Test çalıştıran sanal bir kullanıcının olasılığını belirtmek için test karışımı modellerini düzenleme

*Test karması modeli,* bir yükleme testi senaryosunda belirli bir testi çalıştıran sanal bir kullanıcının olasılığını belirtir. Bu, yükü daha gerçekçi bir şekilde simüle etmenizi sağlar. Uygulamalarınızda tek bir iş akışına sahip olmak yerine, son kullanıcıların uygulamalarınızla nasıl etkileşimde bulunduğuna daha yakın bir yaklaşım olan birkaç iş akışına sahip olabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>Test mix model seçenekleri

Yük testi senaryonuz için aşağıdaki test karışımı model seçeneklerinden birini belirtebilirsiniz:

- **Toplam test sayısına göre:** Sanal bir kullanıcı bir test yinelemesi başlattığında hangi web performansının veya birim testinin çalıştırılüster belirler. Yükleme testinin sonunda, belirli bir testin kaç kez çalıştırıldığı atanan test dağılımıyla eşleşir. Test karını bir IIS günlüğündeki veya üretim verilerindeki işlem yüzdelerine dayandırıyorken bu test karışımı modelini kullanın.

- **Sanal kullanıcı sayısına göre:** Belirli bir web performansını veya birim testini çalıştıracak sanal kullanıcıların yüzdesini belirler. Yükleme testinin herhangi bir noktasında, belirli bir testi çalıştıran kullanıcı sayısı atanan dağıtımla eşleşir. Test karını belirli bir testi çalıştıran kullanıcıların yüzdeye dayarken bu test karışımı modelini kullanın.

- **Kullanıcı hızına göre:** Yükleme testi boyunca, her web performans testi veya birim testi, kullanıcı başına saat başına belirli sayıda kez çalıştırılır. Sanal kullanıcıların yükleme testi boyunca testi belirli bir hızda çalıştırmasını istediğinizde bu test karışımı modelini kullanın.

- **Sıralı sıraya göre:** Her sanal kullanıcı, testlerin senaryoda tanımlandığı sırada web performansını veya birim testlerini çalıştırZ. Sanal kullanıcı, yükleme testi tamamlanana kadar bu sırada testler boyunca bisiklet sürmeye devam ediyor.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testiniz için test karışımını belirtme:** Bir yük testi oluşturduğunuzda, **Yeni Yük Testi Sihirbazı'ndaki**yük testi için ayarları belirtirsiniz. Yeni **Yük Testi Sihirbazı'nda,** ilk senaryoya eklemek için varolan web ve birim testlerini seçersiniz. Senaryoya testler ekledikten sonra, senaryo için test karışımını belirtirsiniz.<br /><br /> Yük testi yaptığınız bir web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını daha doğru tahmin etmek için yük modelleme seçeneklerini kullanırsınız. Doğru bir yük modeline dayanmayan bir yük testi yanıltıcı sonuçlar oluşturabileceğinden bunu yapmak önemlidir.|-   [Bir web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını taklit etmek](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Test karışımı modelini düzenleme:** Yük Testi Düzenleyicisi'ni kullanarak test karışımı modellerinden **Load Test Editor**birini kullanmak için bir yük testi senaryosunu değiştirebilirsiniz.||
|**Kullanıcı tempolu test karışımı modeli için tempo gecikmesi yapılandırın:** Yük testi senaryonuz Kullanıcı hızı **test karışımı modelini**kullanacak şekilde yapılandırılırsa, dağıtım Pacing Delay yapılandırmasını nasıl istediğinizi belirtebilirsiniz.|-   [Nasıl yapılır: Kullanıcı hızı testi karışımı modelini kullanırken pacing gecikmesine dağıtım uygulayın](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Senaryoda test karışımı modelini değiştirme

**Yeni Yük Testi Sihirbazı'nı**kullanarak yük testinizi oluşturduktan sonra, test gereksinimlerinizi ve hedeflerinize ulaşmak için senaryo özelliklerini değiştirmek için Yük Testi Düzenleyicisi'ni kullanabilirsiniz. **Load Test Editor**

> [!NOTE]
> Yük ayarları özelliklerinin ve açıklamalarının tam listesi [için, Yük testi senaryo özelliklerine](../test/load-test-scenario-properties.md)bakın.

Yük **Testi**Düzenleyicisi'ni kullanarak, **Özellikler** penceresindetest **Mix Type** özelliğini düzenleyerek bir yük testi senaryosundaki test karışımı modelini değiştirebilirsiniz.

### <a name="to-change-the-test-mix-model"></a>Test karışımı modelini değiştirmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağacının *Senaryolar* klasöründe, en fazla test yinelemesayısını belirtmek istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     Senaryonun kategorileri ve özellikleri görüntülenir.

4. Test **Mix Type** özelliğinde, elips düğmesini seçin ( **...**).

     **Test Mix'i Edit iletişim** kutusu görüntülenir.

5. **Test mix modeli** altında açılır listeyi seçin ve senaryo için kullanmak istediğiniz test karışımı modelini seçin.

6. (İsteğe bağlı) **Ekle,** **Kaldır** ve **Dağıt** düğmelerini ve dağıtım kaydırıcılarını kullanarak test karışımını değiştirin. Daha fazla bilgi için, [yük testi senaryosuna hangi testlerin dahil edilelir belirtilmek için test karmasını düzenleme'ye](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)bakın.

7. (İsteğe bağlı) Onay kutularını kullanarak ve istenen testleri seçerek bir web performansı ve birim testi belirleyin. Daha fazla bilgi için, [bir web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını taklit etme bölümüne](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)bakın.

8. **Tamam'ı**seçin.

     **Özellikler** penceresi, **Test Mix Type** özelliği için yeni test karışımı modelini görüntüler.

9. Özelliği değiştirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra yeni **Test Mix Type** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını edin](../test/edit-load-test-scenarios.md)
- [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md)
