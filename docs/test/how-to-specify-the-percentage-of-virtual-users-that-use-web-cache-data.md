---
title: 'Yük testi: Web önbelleği verilerini kullanarak sanal kullanıcı yüzdesi ayarlama'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cac3368d0f03c268e086cc8636f1175a15effdd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113366"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Nasıl kullanılır: Web önbelleği verilerini kullanan sanal kullanıcıların yüzdesini belirtin

**Yeni Yük Testi Sihirbazı**ile yük testinizi oluşturduktan sonra, Yük Testi Düzenleyicisi'ni kullanarak test ihtiyaçlarınızı ve hedeflerinizi karşılayacak senaryo özelliklerini değiştirebilirsiniz. **Load Test Editor** Yük testi senaryo özelliklerinin ve açıklamalarının tam listesi için [bkz.](../test/load-test-scenario-properties.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Yeni Kullanıcıların Özelliğinin Yüzdesi** **Özellikler** penceresinde ayarlanır. Yük Testi Düzenleyicisi'nde **Load Test Editor**yük testi senaryo özelliklerini edin.

**Yeni Kullanıcıların Özelliğiyüzdesi,** yük testinin bir web tarayıcısı tarafından gerçekleştirilecek önbelleğe alma şeklini etkiler. Varsayılan olarak, **yeni Kullanıcıların özelliğiyüzdesi** %0 olarak ayarlanır. **Yeni Kullanıcılar özelliğinin yüzdesi** değeri %100 olarak ayarlanmışsa, bir yük testinde çalıştırılabilen her web performans testi, önceki ziyaretlerden tarayıcı önbelleğinde web sitesinden herhangi bir içeriğe sahip olmayan web sitesine ilk kez kullanıcı olarak kabul edilir. Böylece, resimler gibi tüm bağımlı istekler de dahil olmak üzere web testindeki tüm istekler indirilir.

> [!NOTE]
> Aynı önbelleğe uygun kaynak bir web testinde birden fazla kez istendiğinde, istekler karşıdan yüklenmez.

Yerel olarak önbelleğe alınmış görüntülere ve diğer önbelleğe getirilebilir içeriğe sahip önemli sayıda iade kullanıcısı olan bir web sitesini yük testine tabi yoruyorsanız, **yeni Kullanıcıların özelliğinin yüzdesi** için %100'lük bir ayar gerçek dünya kullanımında oluşacak olandan daha fazla indirme isteği oluşturur. Bu durumda, web sitenize yapılan ziyaretlerin yüzdesini tahmin etmeli ve web sitesini ilk kez kullananlardan gelen ziyaretlerin yüzdesini buna göre **yeni Kullanıcılar özelliğine** göre ayarlamalısınız.

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>Bir senaryo için yeni kullanıcıların yüzdesini belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **Senaryolar** klasöründe, yeni kullanıcı yüzdesi değerini değiştirmek istediğiniz senaryo düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. Yeni kullanıcıların yüzdesi için bir sayı girerek **Yeni Kullanıcılar özelliğinin yüzdesi** değerini ayarlayın.

5. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra yeni Yeni Kullanıcı **Yüzdesi** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını edin](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md)
- [Sanal kullanıcı etkinliklerini modellemek için yük modellerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
