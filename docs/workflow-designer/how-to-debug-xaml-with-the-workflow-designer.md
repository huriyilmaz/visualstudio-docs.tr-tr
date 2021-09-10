---
title: "İş Akışı Tasarımcısı: XAML'de Hata Ayıklama"
description: İş akışlarının XAML açısından nasıl tanımlandığı ve XAML'de hata ayıklamanın nasıl İş Akışı Tasarımcısı.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- uwp
ms.openlocfilehash: 721ee723c6f7d0e28c4d7da376233641a580d21d
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963745"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Nasıl Yapılır: İş Akışı Tasarımcısı ile XAML Hatalarını Ayıklama

İş akışları XAML açısından tanımlanır. İş akışının kullanıcı arabirimi gösterimi, iş akışını tanımlayan XAML ağacının üzerine inşa edilmiştir. Hata ayıklama deneyimi, iş akışlarında hata ayıklamaya benzer İş Akışı Tasarımcısı. Örneğin, XAML'de hata ayıklarken yereller, izleme ve iş parçacıkları pencereleri hata ayıklamada olduğu gibi İş Akışı Tasarımcısı çalışır. Ayrıca, XAML hata ayıklaması sırasında çağrı yığını görünümü, iş akışı için yürütme akışının satır tabanlı hiyerarşik bir görünümü olur.

> [!NOTE]
> Bir iş akışının XAML'i etkinliklerle aynı derlemede bulunuyorsa, sınıf adlarının derleme kısmı dahil değildir. Sınıf (etkinlik) adlarının bu bölümü olmadan, XAML çalışma zamanında yüklenemiyor. Ana projeyle aynı ad alanı içinde etkinlikler tanımlamak önerilmez; aksi takdirde, tasarımcıda düzenlendikten sonra XAML el ile düzenlenemez.

## <a name="to-debug-workflow-xaml"></a>İş akışı XAML'de hata ayıklamak için

1. Bir iş akışı veya etkinlik projesini Visual Studio.

2. Hata ayıklamak istediğiniz etkinlik veya etkinliklerde nasıl kullanılır: İş Akışlarında Kesme Noktaları Ayarlama konusunda [açıklandığı gibi bir kesme noktası ayarlayın.](../workflow-designer/how-to-set-breakpoints-in-workflows.md)

3. İş akışı tanımınızı içeren .xaml dosyasına sağ tıklayın ve Kodu **Görüntüle'yi seçin.** Tasarım görünümünde kesme noktası ayar etkinliğinin XAML öğesi bildirimiyle aynı satırda bir kesme noktası görüntülenir.

4. İş akışlarında hata ayıklama konusunda açıklandığı gibi [hata ayıklayıcısını çağırma.](debugging-workflows-with-the-workflow-designer.md)

5. Kod yürütme kesme noktalarından biri ile ulaştığında, bu kesme noktasıyla ilişkili XAML öğesi vurgulanır. Bir sonraki kesme noktası için **F10** veya **F11 anahtarını** kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: İş Akışlarında Kesme Noktası Ayarlama](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [İş akışları hata ayıklama](debugging-workflows-with-the-workflow-designer.md)
