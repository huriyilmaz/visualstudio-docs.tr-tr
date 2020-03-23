---
title: Yük testi için Pacing Delay'a Dağıtım Uygula
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 953c1ac4cb6e0f87d2a36080cc751ea26f66d63e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114496"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Nasıl yapılır: Kullanıcı hızı testi karışımı modeli için pacing gecikmesine dağıtım uygulayın

**Yeni Yük Testi Sihirbazı'nı**kullanarak yük testinizi oluşturduktan sonra, test gereksinimlerinizi ve hedeflerinizi karşılamak için senaryonun özelliklerini değiştirmek için Yük Testi Düzenleyicisini kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Pacing Delay özelliğine Uygula Dağıtımı,** **Özellikler** penceresi kullanılarak ayarlanır. Yük testi senaryo özellikleri Yük Testi Düzenleyicisi kullanılarak değiştirilir.

> [!NOTE]
> **Pacing Delay özelliğine Uygula Dağıtımı,** yalnızca *yük testi karışımı* kullanıcı hızına göre yapılandırılırsa geçerlidir. Daha fazla bilgi için, test [çalıştıran sanal bir kullanıcının olasılığını belirtmek için metin karışımı modellerini edit'e](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)bakın.

**Pacing Delay'a Dağıtım Uygula** değeri doğru veya yanlış olarak ayarlanabilir:

- **True**: Senaryo, **Test Mix** iletişim kutusundaki **Kullanıcı Başına Saat Başına Testler** sütunundaki değere göre belirtilen normal istatistiksel dağılım gecikmelerini uygular. Daha fazla bilgi için, test [çalıştıran sanal bir kullanıcının olasılığını belirtmek için metin karışımı modellerini edit'e](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)bakın.

     Örneğin, test kümesi için Test Mix'i **düzenleme** iletişim kutusunda saat **başına kullanıcı başına testler** insaatini varsayalım. **Pacing Delay özelliğine Dağıtım Uygula** **True**olarak ayarlanırsa, testler arasındaki bekleme süresine normal bir istatistiksel dağılım uygulanır. Testler yine de saatte iki test çalıştıracaktır, ancak aralarında mutlaka 30 dakika gecikme olmayacaktır. İlk test dört dakika sonra, ikinci test ise 45 dakika sonra çalıştırılabilir.

- **False**: Testleri **Test Mix** iletişim kutusunda Ki Saat **Başına Kullanıcı Başına Testler** sütununda değer için belirlediğiniz hızda çalışır. Daha fazla bilgi için, test [çalıştıran sanal bir kullanıcının olasılığını belirtmek için metin karışımı modellerini edit'e](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)bakın.

     Örneğin, test kümesi için Test Mix'i **düzenleme** iletişim kutusunda saat **başına kullanıcı başına testler** insaatini varsayalım. **Pacing Delay özelliğine Uygula Dağıtımı** **False**olarak ayarlanmışsa, testleriniz çalışırken hiçbir serbestlik vermiyorsunuz. Test her 30 dakikada bir çalışır. Bu, saatte iki test yürütmenizi sağlar.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Bir senaryo için Pacing Delay özellik ayarına Dağıtım Uygula'yı belirtmek için

1. Bir yük testi açın.

   **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağacının **Senaryolar** klasöründe, pacing dağılımı uygulamak istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

   Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. **Pacing Delay'a Dağıtım Uygula'nın**özellik değerinde, **Doğru** veya **Yanlış'ı**seçin.

5. **Dosya** > **Kaydet'i**seçin. Artık yük testinizi yeni **Pacing Delay değerine Uygula Dağıtımı** ile çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını edin](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md)
