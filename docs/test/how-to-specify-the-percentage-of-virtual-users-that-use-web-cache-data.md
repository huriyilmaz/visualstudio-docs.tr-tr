---
title: 'Yük testi: Web önbelleği verilerini kullanarak Sanal Kullanıcı yüzdesini ayarla'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a31ea50cdedbeb825d03de38a89200b6e8e5200
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287408"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Nasıl yapılır: Web önbelleği verilerini kullanan sanal kullanıcıların yüzdesini belirtme

**Yeni Yük Testi Sihirbazı**yük testinizi oluşturduktan sonra, **Yük Testi Düzenleyicisi**kullanarak test ihtiyaçlarını ve hedeflerinizi karşılamak için senaryolar özelliklerini değiştirebilirsiniz. Yük testi senaryosu özelliklerinin tam listesi ve açıklamaları için bkz. [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Yeni kullanıcılar özelliğinin yüzdesi** **Özellikler** penceresinde ayarlanır. **Yük Testi Düzenleyicisi**yük testi senaryosu özelliklerini düzenleyebilirsiniz.

**Yeni kullanıcılar özelliğinin yüzdesi** , yük testinin bir Web tarayıcısı tarafından gerçekleştirilecek önbelleğe alma işlemini taklit etme yöntemini etkiler. Varsayılan olarak, **yeni kullanıcılar özelliğinin yüzdesi** %0 olarak ayarlanır. **Yeni kullanıcılar özelliğinin yüzdesi** %100 olarak ayarlanırsa, bir yük testinde her Web performans testi çalıştırması, önceki ziyaretlerden tarayıcı önbelleğinde Web sitesinden hiçbir içerik bulunmayan Web sitesine ilk Kullanıcı gibi davranır. Bu nedenle, görüntü gibi tüm bağımlı istekler de dahil olmak üzere Web testinde yapılan tüm istekler indirilir.

> [!NOTE]
> Aynı önbelleklenebilir kaynak bir Web testinde birden çok kez istenildiğinde, istekler indirilmez.

Görüntü ve diğer önbelleklenebilir içerikler yerel olarak önbelleğe alınmış çok sayıda dönüş kullanıcısı olan bir Web sitesine yük testi yapıyorsanız, **yeni kullanıcılar özelliğinin yüzdesi** için %100 ayarı, gerçek dünya kullanımında gerçekleşenden daha fazla indirme isteği oluşturacaktır. Bu durumda, Web sitenizin ilk Kullanıcı kullanıcılarından gelen ziyaretlerin yüzdesini tahmin etmeniz ve **Yeni Kullanıcı özelliğinin yüzdesini** uygun şekilde ayarlamanız gerekir.

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>Bir senaryoya yönelik yeni Kullanıcı yüzdesini belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **senaryolar** klasöründe, Yeni Kullanıcı yüzdesi değerini değiştirmek istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. Yeni Kullanıcı yüzdesi için bir sayı girerek **yeni kullanıcılar** özelliğinin değerini ayarlayın.

5. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet** ' i seçin. Daha sonra yeni **Kullanıcı yüzdesi** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını Düzenle](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
- [Sanal Kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
