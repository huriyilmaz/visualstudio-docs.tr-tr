---
title: Metin karışımı modellerini düzenleniyor
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8ce54af89164b1a71c7328d04635c8735eec1b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288656"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Testi çalıştıran bir Sanal Kullanıcı olasılığını belirtmek için test karışımı modellerini düzenleyin

*Test karışımı modeli* , bir yük testi senaryosunda belirli bir testi çalıştıran sanal kullanıcı olasılığını belirtir. Bu, yükün daha gerçekçi bir şekilde benzetimini yapmanızı sağlar. Uygulamalarınız aracılığıyla yalnızca bir iş akışına sahip olmak yerine, son kullanıcıların uygulamalarınızla nasıl etkileşime gireceğini daha yakından yaklaşarak birkaç iş akışınız olabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>Test karışımı modeli seçenekleri

Yük testi senaryonuz için aşağıdaki test karışımı modeli seçeneklerinden birini belirtebilirsiniz:

- **Toplam test sayısına göre:** Bir sanal kullanıcı bir test yinelemesi başlattığında hangi Web performansının veya birim testinin çalıştırılacağını belirler. Yük testinin sonunda, belirli bir testin çalıştırıldığı zamanların sayısı atanan test dağılımı ile eşleşir. Test karışımını bir IIS günlüğünde veya üretim verilerinde işlem yüzdeleri temelinde dayandırdığınızda bu test karışımı modelini kullanın.

- **Sanal kullanıcı sayısına göre:** Belirli bir Web performans veya birim testini çalıştıracak sanal kullanıcıların yüzdesini belirler. Yük testinin herhangi bir noktasında, belirli bir testi çalıştıran kullanıcıların sayısı atanan dağıtımla eşleşir. Test karışımını belirli bir testi çalıştıran kullanıcıların yüzdesine dayandırdığınızda bu test karışımı modelini kullanın.

- **Kullanıcı adımına göre:** Yük testi sırasında, her Web performans testi veya birim testi, Kullanıcı başına saat başına belirtilen sayıda kez çalıştırılır. Sanal kullanıcıların testi yük testi boyunca belirli bir hızda çalıştırmasını istediğinizde, bu test karışımı modelini kullanın.

- **Sıralı sıraya göre:** Her sanal kullanıcı, Web performansını veya birim testlerini, testlerin senaryoda belirlenen sırada çalıştırır. Sanal Kullanıcı, yük testi tamamlanana kadar bu sırada testlerin ilerlemeye devam eder.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testiniz için test karışımını belirtme:** Bir yük testi oluşturduğunuzda, **yeni Yük Testi Sihirbazı**yük testinin ayarlarını belirtirsiniz. **Yeni Yük Testi Sihirbazı**, başlangıç senaryosuna eklemek için var olan Web ve birim testlerini seçersiniz. Senaryoya testler ekledikten sonra senaryo için test karışımını belirlersiniz.<br /><br /> Yük-test ettiğiniz bir Web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını daha doğru tahmin etmek için yük modelleme seçeneklerini kullanın. Doğru yük modelini temel alan bir yük testi yanıltıcı sonuçlar üretebildiğinden bunun olması önemlidir.|-   [Bir Web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını benzetir](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Test karışımı modelini düzenleyin:** Yük testi senaryosunu, **Yük Testi Düzenleyicisi**kullanarak test karışımı modellerinden birini kullanacak şekilde değiştirebilirsiniz.||
|**Kullanıcı tarafından ilerleyebileceğiniz test karışımı modeli için ilerleme gecikmesini yapılandırın:** Yük testi senaryonuz, **temel aldığı Kullanıcı hızı test karışımı modelini**kullanacak şekilde yapılandırıldıysa, dağıtım hız gecikmesini nasıl yapılandırmak istediğinizi belirtebilirsiniz.|-   [Nasıl yapılır: Kullanıcı hız testi karışımı modeli kullanırken İlerleme Gecikmesine Dağıtım uygulama](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Bir senaryoda test karışımı modelini değiştirme

**Yeni Yük Testi Sihirbazı**kullanarak yük testinizi oluşturduktan sonra, test ihtiyaçlarını ve hedeflerinizi karşılamak üzere senaryolar özelliklerini değiştirmek için **Yük Testi Düzenleyicisi** kullanabilirsiniz.

> [!NOTE]
> Yükleme ayarları özelliklerinin ve açıklamalarının tüm listesi için bkz. [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md).

**Yük Testi Düzenleyicisi**kullanarak, bir yük testi senaryosunda test karışımı modelini, **Özellikler** penceresindeki **Test karışımı türü** özelliğini düzenleyerek değiştirebilirsiniz.

### <a name="to-change-the-test-mix-model"></a>Test karışımı modelini değiştirmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağacının *senaryolar* klasöründe, en fazla test yinelemesi sayısını belirtmek istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

     Senaryonun kategorileri ve özellikleri görüntülenir.

4. **Test karışımı türü** özelliğinde üç nokta düğmesini ( **...**) seçin.

     **Test karışımını düzenle** iletişim kutusu görüntülenir.

5. **Test karışımı modeli** ' nin altındaki açılan listeyi seçin ve senaryo için kullanmak istediğiniz test karışımı modelini seçin.

6. Seçim **Ekle**, **Kaldır** ve **Dağıt** düğmelerini ve dağıtım kaydırıcılarını kullanarak test karışımını değiştirin. Daha fazla bilgi için bkz. [Yük testi senaryosuna hangi testlerin ekleneceğini belirlemek için test karışımını düzenleme](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7. Seçim Onay kutularını kullanarak ve istenen testleri seçerek başlatılacak veya sona erdirmek için bir Web performansı ve birim testi belirtin. Daha fazla bilgi için bkz. [bir Web sitesinin veya uygulamanın beklenen gerçek dünya kullanımını öykünme](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8. **Tamam ' ı**seçin.

     **Özellikler** penceresi, **Test karışımı türü** özelliği için yeni test karışımı modelini görüntüler.

9. Özelliği değiştirdikten sonra **Dosya** menüsünde **Kaydet** ' i seçin. Ardından, yeni **Test karışımı türü** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını Düzenle](../test/edit-load-test-scenarios.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
