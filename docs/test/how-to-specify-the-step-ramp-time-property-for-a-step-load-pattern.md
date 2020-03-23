---
title: Yük testi için Adım Yük Deseni için Adım Rampası Süresi
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a40f7ce4aacfdc03b5e05becbfc83439945f7e8a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588921"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Nasıl yapılı: Adım yükleme deseni için adım rampası zaman özelliğini belirtin

**Yeni Yük Testi Sihirbazı**ile yük testinizi oluşturduktan sonra, test gereksinimlerinizi ve hedeflerinize ulaşmak için senaryo özelliklerini değiştirmek için Yük Testi Düzenleyicisi'ni kullanabilirsiniz. **Load Test Editor** Daha fazla bilgi için [Bkz. Walkthrough: Bir yük testi oluşturun ve çalıştırın.](../test/walkthrough-create-and-run-a-load-test.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testi senaryo özelliklerinin ve açıklamalarının tam listesi için [bkz.](../test/load-test-scenario-properties.md)

**Step Rampası Saati** özelliği **Özellikler** penceresinde ayarlanır. Yük Testi Düzenleyicisi'nde **Load Test Editor**yük testi senaryo özelliklerini edin.

**Step Rampası Süresi** özelliği yalnızca bir adım yük deseni yle kullanılır. Daha fazla bilgi [için, sanal kullanıcı etkinliklerini modellemek için yük desenlerini düzenle'ye](../test/edit-load-patterns-to-model-virtual-user-activities.md)bakın.

Kullanıcı yükü arttıkça performansın nasıl değiştiğini görebilmeniz için yük testi çalışırken sunucu veya sunuculardaki yükü artırmak için bir adım yük deseni kullanılır. Örneğin, kullanıcı yükü 2.000 kullanıcıya artarken sunucunuzun veya sunucularınızın nasıl performans gösterdiğini görmek için, aşağıdaki özelliklere sahip bir adım yük deseni kullanarak 10 saatlik bir yükleme testi çalıştırabilirsiniz:

- İlk Kullanıcı Sayısı: 100

- Maksimum Kullanıcı Sayısı: 2000

- Adım Süresi (saniye): 1800

- Adım Rampası Süresi (saniye): 20

- Adım Kullanıcı Sayısı: 100

Bu ayarlar, 100, 200, 300 ve 2.000 kullanıcıya kadar olan kullanıcı yüklerinden 30 dakika (1800 saniye) boyunca çalışan yük testine sahiptir.

> [!NOTE]
> **Adım Rampası Süresi** özelliği, Yeni Yük Testi Sihirbazı'nda **New Load Test Wizard**seçilemeyen bu özelliklerden yalnızca biridir.

**Step Ramp Time** özelliği, bir adımdan diğerine (örneğin 100'den 200 kullanıcıya) artışın hemen değil kademeli olmasını sağlar. Örnekte, kullanıcı yükü 20 saniyelik bir süre içinde 100 kullanıcıdan 200 kullanıcıya yükseltilse (saniyede 5 kullanıcı artışı).

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Adım yükleme deseni için adım rampası zaman özelliğini düzenlemek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **Senaryolar** klasöründe, adım rampası süresini belirtmek istediğiniz senaryo düğümünü açın.

3. Adım **Yük Deseni** düğümünü seçin.

    > [!NOTE]
    > Senaryo için yük deseni bir adım yük deseni olmalıdır. Değilse, yük deseni şu anda senaryoyla ilişkili olan yük deseni türünü görüntüler. Daha fazla bilgi [için, sanal kullanıcı etkinliklerini modellemek için yük desenlerini düzenle'ye](../test/edit-load-patterns-to-model-virtual-user-activities.md)bakın.

4. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

5. **Adım Kullanıcı Sayısı** özelliği tarafından belirtilen kullanıcıları kademeli olarak eklemek için her adımda alınan saniyeler için bir sayı girerek Step Ramp **Time** özelliğinin değerini ayarlayın.

6. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra yeni **Step RampA Süresi** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını edin](../test/edit-load-test-scenarios.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md)
- [Sanal kullanıcı etkinliklerini modellemek için yük modellerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
