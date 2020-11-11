---
title: 'İş Akışı Tasarımcısı: XAML hatalarını ayıklama'
description: İş akışlarının XAML açısından nasıl tanımlandığını ve İş Akışı Tasarımcısı XAML hata ayıklamanın nasıl yapılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 24540a6e7a2f99f35edf6018355583b5f9230e1a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437937"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Nasıl Yapılır: İş Akışı Tasarımcısı ile XAML Hatalarını Ayıklama

İş akışları XAML bakımından tanımlanmıştır. İş akışının Kullanıcı arabirimi temsili, iş akışını tanımlayan XAML ağacının üzerine kurulmuştur. Hata ayıklama deneyimi İş Akışı Tasarımcısı hata ayıklama iş akışlarıyla benzerdir. Örneğin, XAML hatalarını ayıklarken, Yereller, izle ve iş parçacıkları Windows İş Akışı Tasarımcısı hata ayıklamayla aynı şekilde çalışır. Ayrıca, XAML hata ayıklaması sırasında çağrı yığını görünümü, iş akışı için yürütme akışının satır tabanlı hiyerarşik görünümüdür.

> [!NOTE]
> Bir iş akışı için XAML, etkinliklerle aynı derlemede bulunuyorsa, sınıf adlarının derleme kısmı dahil edilmez. Sınıf (etkinlik) adlarının bu kısmı olmadan XAML çalışma zamanında yüklenemez. Ana projeyle aynı ad alanında etkinlik tanımlamanız önerilmez; Aksi takdirde, XAML, tasarımcıda düzenlendikten sonra el ile düzenlenmelidir.

## <a name="to-debug-workflow-xaml"></a>Workflow XAML hatalarını ayıklamak için

1. Visual Studio 'da bir iş akışı veya etkinlik projesi açın.

2. [Nasıl yapılır: Iş akışlarında kesme noktalarını ayarlama](../workflow-designer/how-to-set-breakpoints-in-workflows.md)bölümünde açıklandığı gibi, hata ayıklamak istediğiniz etkinlik veya etkinliklerde bir kesme noktası ayarlayın.

3. İş akışı tanımınızı içeren. xaml dosyasına sağ tıklayın ve **kodu görüntüle** ' yi seçin. Tasarım görünümünde, kesme noktasını ayarladığınız etkinliğin XAML öğesi bildirimiyle aynı satırda görüntülenen bir kesme noktası görürsünüz.

4. Hata [ayıklama iş akışlarında](debugging-workflows-with-the-workflow-designer.md)açıklandığı şekilde hata ayıklayıcıyı çağırın.

5. Kod yürütme, kesme noktalarınızın birine ulaştığında, bu kesme noktasıyla ilişkili XAML öğesi vurgulanacaktır. Sonraki kesme noktasına geçmek için **F10** veya **F11** tuşunu kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: İş Akışlarında Kesme Noktası Ayarlama](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [İş akışları hata ayıklama](debugging-workflows-with-the-workflow-designer.md)
