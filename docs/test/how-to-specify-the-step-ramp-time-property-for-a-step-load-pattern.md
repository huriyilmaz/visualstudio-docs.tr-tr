---
title: Yük testi için adımlı rampa süresi
description: Kümede Step Ramp Time özelliğini ayarlamayı Özellikler penceresi. Step Ramp Time özelliği yalnızca bir adım yükleme düzeni ile kullanılır.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092455"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Nasıl olur: Adım yükleme deseni için adım rampası zaman özelliğini belirtme

Yük testini New Yük Testi Sihirbazı ile **oluşturdukktan** sonra, Yük Testi Düzenleyicisi özelliklerini test **Yük Testi Düzenleyicisi** hedeflerinizi karşılayacak şekilde değiştirmek için kullanabilirsiniz. Daha fazla bilgi için [bkz. Adım adım kılavuz: Yük testi oluşturma ve çalıştırma.](../test/walkthrough-create-and-run-a-load-test.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testi senaryosu özelliklerinin ve açıklamalarının tam listesi için bkz. [Yük testi senaryosu özellikleri.](../test/load-test-scenario-properties.md)

Step **Ramp Time** özelliği Özellikler penceresinde **ayarlanır.** Yük testi senaryosu özelliklerini **Yük Testi Düzenleyicisi.**

Step **Ramp Time özelliği** yalnızca bir adım yükleme düzeni ile kullanılır. Daha fazla bilgi için [bkz. Sanal kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme.](../test/edit-load-patterns-to-model-virtual-user-activities.md)

Kullanıcı yükü arttıkça performansın nasıl değişiklik gösterir olduğunu görmek için yük testi çalıştırtıkça sunucu veya sunucu üzerindeki yükü artırmak için bir adım yükleme düzeni kullanılır. Örneğin, kullanıcı yükü 2.000 kullanıcıya artarak sunucu veya sunucularının nasıl performans sergileyeli olduğunu görmek için, aşağıdaki özelliklere sahip bir adım yükleme düzeni kullanarak 10 saatlik bir yük testi çalıştırabilirsiniz:

- İlk Kullanıcı Sayısı: 100

- En Fazla Kullanıcı Sayısı: 2000

- Adım Süresi (saniye): 1800

- Step Ramp Time (saniye): 20

- Adım Kullanıcı Sayısı: 100

Bu ayarlar, 2.000 kullanıcıya kadar 100, 200, 300 kullanıcı yükünde 30 dakika (1800 saniye) çalışan yük testini içerir.

> [!NOTE]
> Step **Ramp Time** özelliği, New Yük Testi Sihirbazı . 

**Step Ramp Time özelliği,** bir adımdan sonrakine (örneğin 100 kullanıcıdan 200 kullanıcıya) kadar olan artışın hemen değil kademeli olarak artmasına olanak sağlar. Örnekte, kullanıcı yükü 20 saniyelik bir süre boyunca 100 kullanıcıdan 200 kullanıcıya (her saniye 5 kullanıcı artışı) artırılabilir.

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Adım yükleme deseninin adım rampası zaman özelliğini düzenlemek için

1. Yük testi açın.

     Yük Testi Düzenleyicisi  görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **Senaryolar** klasöründe, adım rampası zamanını belirtmek istediğiniz senaryo düğümünü açın.

3. Adım Yükleme **Düzeni düğümünü** seçin.

    > [!NOTE]
    > Senaryo için yük deseni, adımlı bir yük düzenine sahip olması gerekir. Yüklenmezse, yük düzeni şu anda senaryoyla ilişkilendirilmiş olan yük deseni türünü görüntüler. Daha fazla bilgi için [bkz. Sanal kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme.](../test/edit-load-patterns-to-model-virtual-user-activities.md)

4. Görünüm menüsünde **Özellikler** **Penceresi'ne tıklayın.**

     Senaryonun kategorileri ve özellikleri Özellikler **penceresinde** görüntülenir.

5. Adım Kullanıcı Sayısı **özelliği tarafından** belirtilen kullanıcıları kademeli olarak eklemek üzere her adımda geçen saniye sayısı için bir sayı girerek Step **Ramp Time özelliğinin değerini** ayarlayın.

6. Özelliği değiştirmeyi bitirdikten sonra Dosya menüsünde **Kaydet'i** seçin.  Daha sonra yeni Step Ramp Time değerini kullanarak yük **testini çalıştırabilirsiniz.**

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
- [Sanal kullanıcı etkinliklerini modellemek için yük desenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md)
