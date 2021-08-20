---
title: Metin Karışımı Modellerini Düzenleme
description: Test karışımı modelinin, son kullanıcıların uygulamalarınız ile nasıl etkileşime geçmeleri hakkında daha yakından bilgi veren çeşitli iş akışlarına sahip olmak için nasıl olanaklı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 6bf9001d07a56d521283bcd5e9c6b7774437df48
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140017"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Testi çalıştıran bir sanal kullanıcının olasılığını belirtmek için test karışımı modellerini düzenleme

Test *karışımı modeli,* bir yük testi senaryosunda belirli bir testi çalıştıran bir sanal kullanıcının olasılığını belirtir. Bu, yükün benzetimini daha gerçekçi bir şekilde uygulamana olanak sağlar. Uygulamalarınız arasında yalnızca bir iş akışı olması yerine, son kullanıcıların uygulamalarınız ile nasıl etkileşim kurduğuna daha yakın bir tahmin olan birkaç iş akışınız olabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>Test karışımı modeli seçenekleri

Yük testi senaryo için aşağıdaki test karışımı modeli seçeneklerine birini belirtebilirsiniz:

- **Toplam test sayısına göre:** Sanal kullanıcı bir test yinelemesi başlatırken hangi web performansının veya birim testinin çalıştırılı olduğunu belirler. Yük testinin sonunda, belirli bir testin çalıştırdığı sayı atanan test dağıtımıyla eşler. Test karışımını IIS günlüğünde veya üretim verisinde işlem yüzdelerini kullanıyorken bu test karışımı modelini kullanın.

- **Sanal kullanıcı sayısına göre:** Belirli bir web performansını veya birim testini çalıştıracak sanal kullanıcıların yüzdesini belirler. Yük testinin herhangi bir noktasında, belirli bir testi çalıştıran kullanıcı sayısı atanan dağıtımla eştir. Test karışımını belirli bir testi çalıştıran kullanıcıların yüzdesine bağlıyken bu test karışımı modelini kullanın.

- **Kullanıcı hızına göre:** Yük testi boyunca, her web performans testi veya birim testi, kullanıcı başına saat başına belirtilen sayıda çalıştırtır. Sanal kullanıcıların yük testi boyunca belirli bir hızda test çalıştırmalarını istediğiniz durumlarda bu test karışımı modelini kullanın.

- **Sıralı sıralamaya göre:** Her sanal kullanıcı, testlerin senaryoda tanımlandığı sırada web performansını veya birim testlerini çalıştırır. Sanal kullanıcı, yük testi tamamlayana kadar testlerde bu sırayla devam eder.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testin test karışımını belirtme:** Bir yük testi oluşturdukta, Yük testi için ayarları New **Yük Testi Sihirbazı.** Yeni **uygulama Yük Testi Sihirbazı,** ilk senaryoya eklemek için mevcut web ve birim testlerini seçersiniz. Senaryoya testleri ekledikten sonra, senaryo için test karışımını belirtirsiniz.<br /><br /> Yük test etmekte olduğunu bir web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını daha doğru tahmin etmek için yük modelleme seçeneklerini kullanırız. Doğru bir yük modelini temel alan bir yük testi yanıltıcı sonuçlar oluşturayana kadar bunu yapmak önemlidir.|-   [Bir web sitesinin veya uygulamanın beklenen gerçek dünya kullanımına öykün](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Test karışımı modelini düzenleyin:** Bir yük testi senaryosunu, test karışımı modellerinden birini kullanmak için **Yük Testi Düzenleyicisi.**||
|**Kullanıcı hızına sahip bir test karışımı modeli için ilerleme gecikmesi yapılandırma:** Yük testi senaryonuz Kullanıcı hızı test karışımı modeline göre'yi kullanmak üzere **yapılandırılmışsa,** dağıtım Hızı Gecikmesi'nin nasıl yapılandırılmasını istediğiniz belirtesiniz.|-   [Nasıl yapılır: Kullanıcı hızı test karışımı modeli kullanırken ilerleme gecikmesine dağıtım uygulama](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Bir senaryoda test karışımı modelini değiştirme

Yük testini New Yük Testi Sihirbazı kullanarak **oluşturdukta,** senaryo özelliklerini test **Yük Testi Düzenleyicisi** hedeflerinizi karşılayacak şekilde değiştirmek için Yük Testi Düzenleyicisi'ı kullanabilirsiniz.

> [!NOTE]
> Yük ayarları özelliklerinin ve açıklamalarının tam listesi için bkz. [Yük testi senaryosu özellikleri.](../test/load-test-scenario-properties.md)

Yük Testi Düzenleyicisi **kullanarak,** Özellikler penceresindeki **Test** Karışımı Türü özelliğini düzenleyerek bir yük testi senaryosunda test karışımı **modelini değiştirebilirsiniz.**

### <a name="to-change-the-test-mix-model"></a>Test karışımı modelini değiştirmek için

1. Yük testi açın.

     Yük Testi Düzenleyicisi  görüntülenir. Yük testi ağacı görüntülenir.

2. Yük *testi* ağacının Senaryolar klasöründe, en fazla test yinelemesi sayısını belirtmek istediğiniz senaryo düğümünü seçin.

3. Görünüm menüsünde **Özellikler** **Penceresi'ne tıklayın.**

     Senaryonun kategorileri ve özellikleri görüntülenir.

4. Test **Karışımı Türü özelliğinde** üç nokta düğmesini ( **... ) seçin.**

     Test **Karışımını Düzenle** iletişim kutusu görüntülenir.

5. Test karışımı modeli'nin altındaki **açılan listeyi** seçin ve senaryo için kullanmak istediğiniz test karışımı modelini seçin.

6. (İsteğe bağlı) Ekle, Kaldır ve Dağıt **düğmelerini ve** **dağıtım kaydırıcılarını** kullanarak test karışımını değiştirebilirsiniz.  Daha fazla bilgi için [bkz. Bir yük testi senaryosuna](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)hangi testlerin dahil olduğunu belirtmek için test karışımını düzenleme.

7. (İsteğe bağlı) Onay kutularını kullanarak ve istenen testleri seçerek başlatmak veya bitebilmek için bir web performansı ve birim testi belirtin. Daha fazla bilgi için [bkz. Bir web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını öykün.](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)

8. **Tamam'ı seçin.**

     Özellikler **penceresinde** Test Karışımı Türü özelliği için yeni **test karışımı modeli** görüntülenir.

9. Özelliği değiştirdikten sonra Dosya **menüsünde Kaydet'i** seçin.  Daha sonra yeni Test Karışımı Türü değerini kullanarak **yük testini çalıştırarak.**

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
