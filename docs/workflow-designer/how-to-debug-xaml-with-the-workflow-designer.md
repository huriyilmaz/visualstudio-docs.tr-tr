---
title: 'İş Akışı Tasarımcısı: XAML hatalarını ayıklama'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 9be7c8da251a9698e0fceba64e3941ba8fbdf803
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817521"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Nasıl Yapılır: İş Akışı Tasarımcısı ile XAML Hatalarını Ayıklama

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
- [İş akışları hata ayıklama](debugging-workflows-with-the-workflow-designer.md)
