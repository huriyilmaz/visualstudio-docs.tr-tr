---
title: Yük testi için Adım Rampa Süresi
description: Özellikler penceresi Adım Rampa Süresi özelliğini ayarlamayı öğrenin. Adım Rampa Süresi özelliği yalnızca bir adım yük düzeniyle birlikte kullanılır.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 3cce2cecbebd6e215f5eb249fa7e999b404ccbc5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726731"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Nasıl yapılır: adım yükleme deseninin Adım Rampa Süresi özelliğini belirtme

**Yeni Yük Testi Sihirbazı** yük testinizi oluşturduktan sonra, test ihtiyaçlarını ve hedeflerinizi karşılamak üzere senaryolar özelliklerini değiştirmek için **Yük Testi Düzenleyicisi** kullanabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testi senaryosu özelliklerinin tam listesi ve açıklamaları için bkz. [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md).

**Adım Rampa Süresi** özelliği **Özellikler** penceresinde ayarlanır. **Yük Testi Düzenleyicisi** yük testi senaryosu özelliklerini düzenleyebilirsiniz.

**Adım Rampa Süresi** özelliği yalnızca bir adım yük düzeniyle birlikte kullanılır. Daha fazla bilgi için bkz. [Sanal Kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Bir adım yük şekli, yük testi çalışırken, kullanıcı yükü arttıkça performansın nasıl değişeceğini görebileceğiniz şekilde sunucu veya sunuculardaki yükü artırmak için kullanılır. Örneğin, kullanıcı yükü 2.000 kullanıcılara artarak sunucu veya sunucularınızın nasıl çalıştığını görmek için, aşağıdaki özelliklerle bir adım yük düzeniyle birlikte 10 saatlik bir yük testi çalıştırabilirsiniz:

- İlk Kullanıcı sayısı: 100

- En fazla kullanıcı sayısı: 2000

- Adım süresi (saniye): 1800

- Adım Rampa Süresi (saniye): 20

- Adım kullanıcı sayısı: 100

Bu ayarlar, 100, 200, 300, 2.000 kullanıcılara kadar olan Kullanıcı yüklerine 30 dakika (1800 saniye) boyunca çalışan yük testine sahiptir.

> [!NOTE]
> **Adım Rampa Süresi** özelliği, **Yeni Yük Testi Sihirbazı** seçim için kullanılamayan bu özelliklerden yalnızca biridir.

**Adım Rampa Süresi** özelliği bir adımdan bir sonrakine (örneğin, 100 ' den 200 ' e kadar) kadar artışın hemen yerine aşamalı olmasını sağlar. Örnekte, kullanıcı yükü 20 saniyelik bir süre (saniyede 5 Kullanıcı artışı) üzerinden 100 ' dan 200 kullanıcıya yükseltilir.

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Adım yükleme deseninin Adım Rampa Süresi özelliğini düzenlemek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **senaryoları** klasöründe, için Adım Rampa süresini belirtmek istediğiniz senaryo düğümünü açın.

3. **Adım yük deseninin** düğümünü seçin.

    > [!NOTE]
    > Senaryonun yük deseninin bir adım yük düzeniyle olması gerekir. Değilse, yük modelinde Şu anda senaryoyla ilişkili olan yük deseninin türü görüntülenir. Daha fazla bilgi için bkz. [Sanal Kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

     Senaryonun kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

5. Adım **Kullanıcı sayısı** özelliği tarafından belirtilen kullanıcıları aşamalı olarak eklemek için her adımda alınan saniyeler için bir sayı girerek **Adım Rampa Süresi** özelliğinin değerini ayarlayın.

6. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet** ' i seçin. Daha sonra yeni **Adım Rampa Süresi** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını Düzenle](../test/edit-load-test-scenarios.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
- [Sanal Kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
