---
title: Yük testi için adım yükleme deseninin Adım Rampa Süresi
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a40f7ce4aacfdc03b5e05becbfc83439945f7e8a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588921"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Nasıl yapılır: adım yükleme deseninin Adım Rampa Süresi özelliğini belirtme

İle yükleme testinizi oluşturduktan sonra **Yeni Yük Testi Sihirbazı**, kullanabileceğiniz **Yük Testi Düzenleyicisi** test ihtiyaçlarınızı ve hedeflerinizi karşılayacak şekilde değiştirmek için. Daha fazla bilgi için [izlenecek yol: bir yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testi senaryosu özelliklerini ve açıklamalarının tam listesi için bkz [yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md).

**Adım Rampa Süresi** özelliği **Özellikler** penceresinde ayarlanır. Yük testi senaryosu özelliklerini Düzenle **Yük Testi Düzenleyicisi**.

**Adım Rampa Süresi** özelliği yalnızca bir adım yük düzeniyle birlikte kullanılır. Daha fazla bilgi için [düzenleme yük desen modeli sanal kullanıcı etkinliği](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Bir adım yük şekli, yük testi çalışırken, kullanıcı yükü arttıkça performansın nasıl değişeceğini görebileceğiniz şekilde sunucu veya sunuculardaki yükü artırmak için kullanılır. Örneğin, kullanıcı yükü 2.000 kullanıcılara artarak sunucu veya sunucularınızın nasıl çalıştığını görmek için, aşağıdaki özelliklerle bir adım yük düzeniyle birlikte 10 saatlik bir yük testi çalıştırabilirsiniz:

- İlk Kullanıcı sayısı: 100

- En fazla kullanıcı sayısı: 2000

- Adım süresi (saniye): 1800

- Adım Rampa Süresi (saniye): 20

- Adım kullanıcı sayısı: 100

Bu ayarlar, 100, 200, 300, 2.000 kullanıcılara kadar olan Kullanıcı yüklerine 30 dakika (1800 saniye) boyunca çalışan yük testine sahiptir.

> [!NOTE]
> **Adım Rampa Süresi** özelliği, **Yeni Yük Testi Sihirbazı**seçim için kullanılamayan bu özelliklerden yalnızca biridir.

**Adım Rampa Süresi** özelliği bir adımdan bir sonrakine (örneğin, 100 ' den 200 ' e kadar) kadar artışın hemen yerine aşamalı olmasını sağlar. Örnekte, kullanıcı yükü 20 saniyelik bir süre (saniyede 5 Kullanıcı artışı) üzerinden 100 ' dan 200 kullanıcıya yükseltilir.

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Adım yükleme deseninin Adım Rampa Süresi özelliğini düzenlemek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görünür. Yük testi ağacında görüntülenir.

2. Yük testi ağaçları **senaryoları** klasöründe, için Adım Rampa süresini belirtmek istediğiniz senaryo düğümünü açın.

3. **Adım yük deseninin** düğümünü seçin.

    > [!NOTE]
    > Senaryonun yük deseninin bir adım yük düzeniyle olması gerekir. Değilse, yük modelinde Şu anda senaryoyla ilişkili olan yük deseninin türü görüntülenir. Daha fazla bilgi için [düzenleme yük desen modeli sanal kullanıcı etkinliği](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4. Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

     Senaryonun kategoriler ve özellikler görüntülenir **özellikleri** penceresi.

5. Adım **Kullanıcı sayısı** özelliği tarafından belirtilen kullanıcıları aşamalı olarak eklemek için her adımda alınan saniyeler için bir sayı girerek **Adım Rampa Süresi** özelliğinin değerini ayarlayın.

6. Özelliği değiştirmeyi bitirdikten sonra seçin **Kaydet** üzerinde **dosya** menüsü. Daha sonra yeni **Adım Rampa Süresi** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
- [Model sanal kullanıcı etkinlikleri için yük desenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
