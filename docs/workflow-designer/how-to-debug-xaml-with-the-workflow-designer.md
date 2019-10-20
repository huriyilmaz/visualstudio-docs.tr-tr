---
title: 'İş Akışı Tasarımcısı: XAML hatalarını ayıklama'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 5a7b686db2f8c6818d7a76a5e5188715665b3a87
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650348"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Nasıl yapılır: İş Akışı Tasarımcısı ile XAML hatalarını ayıklama

İş akışları XAML bakımından tanımlanmıştır. İş akışının Kullanıcı arabirimi temsili, iş akışını tanımlayan XAML ağacının üzerine kurulmuştur. Hata ayıklama deneyimi İş Akışı Tasarımcısı hata ayıklama iş akışlarıyla benzerdir. Örneğin, XAML hatalarını ayıklarken, Yereller, izle ve iş parçacıkları Windows İş Akışı Tasarımcısı hata ayıklamayla aynı şekilde çalışır. Ayrıca, XAML hata ayıklaması sırasında çağrı yığını görünümü, iş akışı için yürütme akışının satır tabanlı hiyerarşik görünümüdür.

> [!NOTE]
> Bir iş akışı için XAML, etkinliklerle aynı derlemede bulunuyorsa, sınıf adlarının derleme kısmı dahil edilmez. Sınıf (etkinlik) adlarının bu kısmı olmadan XAML çalışma zamanında yüklenemez. Ana projeyle aynı ad alanında etkinlik tanımlamanız önerilmez; Aksi takdirde, XAML, tasarımcıda düzenlendikten sonra el ile düzenlenmelidir.

## <a name="to-debug-workflow-xaml"></a>Workflow XAML hatalarını ayıklamak için

1. Visual Studio 'da bir iş akışı veya etkinlik projesi açın.

2. [Nasıl yapılır: Iş akışlarında kesme noktalarını ayarlama](../workflow-designer/how-to-set-breakpoints-in-workflows.md)bölümünde açıklandığı gibi, hata ayıklamak istediğiniz etkinlik veya etkinliklerde bir kesme noktası ayarlayın.

3. İş akışı tanımınızı içeren. xaml dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin. Tasarım görünümünde, kesme noktasını ayarladığınız etkinliğin XAML öğesi bildirimiyle aynı satırda görüntülenen bir kesme noktası görürsünüz.

4. Hata [ayıklama iş akışlarında](debugging-workflows-with-the-workflow-designer.md)açıklandığı şekilde hata ayıklayıcıyı çağırın.

5. Kod yürütme, kesme noktalarınızın birine ulaştığında, bu kesme noktasıyla ilişkili XAML öğesi vurgulanacaktır. Sonraki kesme noktasına geçmek için **F10** veya **F11** tuşunu kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: İş Akışlarında Kesme Noktası Ayarlama](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Hata ayıklama iş akışları](debugging-workflows-with-the-workflow-designer.md)