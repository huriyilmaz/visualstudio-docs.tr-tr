---
title: Yük testi için Ilerleme gecikmesine dağıtım uygulayın
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa5d3239e3b096a2018d6ef9c9b3c6666dcd31c3
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288279"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Nasıl yapılır: Kullanıcı hız testi karışımı modeli için İlerleme Gecikmesine Dağıtım uygulama

**Yeni Yük Testi Sihirbazı**kullanarak yük testinizi oluşturduktan sonra, senaryonun özelliklerini test ihtiyaçlarınızı ve hedeflerinizi karşılayacak şekilde değiştirmek için Yük Testi Düzenleyicisi kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Adımlama Gecikmesine Dağıtım Uygula** özelliği **Özellikler** penceresi kullanılarak ayarlanır. Yük testi senaryosu özellikleri Yük Testi Düzenleyicisi kullanılarak değiştirilir.

> [!NOTE]
> **Adımlama Gecikmesine Dağıtım Uygula** özelliği, yalnızca *Yük testi karışımı* Kullanıcı adımına göre yapılandırıldıysa geçerlidir. Daha fazla bilgi için bkz. [test çalıştıran bir Sanal Kullanıcı olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

**Adımlama Gecikmesine Dağıtım Uygula** değeri true veya false olarak ayarlanabilir:

- **Doğru**: senaryo, **test karışımını düzenle** Iletişim kutusunda **saat başına Kullanıcı başına testler** sütununda belirtilen normal istatistiksel dağıtım gecikmelerini uygular. Daha fazla bilgi için bkz. [test çalıştıran bir Sanal Kullanıcı olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Örneğin, test kümesi için test **karışımını düzenle** iletişim kutusunda saat başına iki kullanıcı olarak **saat başına Kullanıcı başına** test olduğunu varsayalım. **Ilerleme Gecikmesine Dağıtım Uygula** özelliği **true**olarak ayarlanırsa, testler arasındaki bekleme süresine normal istatistiksel bir dağıtım uygulanır. Testler, saat başına iki test çalıştırmaya devam eder, ancak aralarında 30 dakikalık bir gecikme olması gerekmez. İlk test dört dakika sonra, ikinci test 45 dakika sonra çalışabilir.

- **Yanlış**: testler, **test karışımını düzenle** Iletişim kutusunda **saat başına Kullanıcı başına testler** sütunundaki değer için belirttiğiniz hızda çalışır. Daha fazla bilgi için bkz. [test çalıştıran bir Sanal Kullanıcı olasılığını belirtmek için metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Örneğin, test kümesi için test **karışımını düzenle** iletişim kutusunda saat başına iki kullanıcı olarak **saat başına Kullanıcı başına** test olduğunu varsayalım. **Adımlama Gecikmesine Dağıtım Uygula** özelliği **false**olarak ayarlandıysa, testleriniz çalıştırıldığında hiçbir zaman yöntemi verirsiniz. Test her 30 dakikada bir çalışacaktır. Bu, saat başına iki test yürütmenizi sağlar.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Bir senaryo için Adımlama Gecikmesine Dağıtım Uygula özellik ayarını belirtmek için

1. Bir yük testi açın.

   **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağacının **senaryolar** klasöründe, hız dağıtımını uygulamak istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

   Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. **Adımlama Gecikmesine Dağıtım Uygula**için özellik değeri ' nde, **doğru** veya **yanlış**' ı seçin.

5. **Dosya**  >  **Kaydet**' i seçin. Artık yük testinizi, yeni bir **adım adım gecikme değerine dağıtım Uygula** değeriyle çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını Düzenle](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
