---
title: "Nasıl yapılır: İş Akışı Tasarımcısı XAML 'de hata ayıklama | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a696123551c24fd0d14fecde67826cf14f88826f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668644"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Nasıl Yapılır: İş Akışı Tasarımcısı ile XAML Hatalarını Ayıklama
İş akışları XAML bakımından tanımlanmıştır. İş akışının Kullanıcı arabirimi temsili, iş akışını tanımlayan XAML ağacının üzerine kurulmuştur. Hata ayıklama deneyimi, içindeki iş akışlarının hata ayıklamasına benzer [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Örneğin, XAML hatalarını ayıklarken, Yereller, izle ve iş parçacıkları Windows [!INCLUDE[wfd2](../includes/wfd2-md.md)] hata ayıklamayla aynı şekilde çalışır. Ayrıca, XAML hata ayıklaması sırasında çağrı yığını görünümü, iş akışı için yürütme akışının satır tabanlı hiyerarşik görünümüdür.

> [!NOTE]
> Bir iş akışı için XAML, etkinliklerle aynı derlemede bulunuyorsa, sınıf adlarının derleme kısmı dahil edilmez. Sınıf (etkinlik) adlarının bu kısmı olmadan XAML çalışma zamanında yüklenemez. Ana projeyle aynı ad alanında etkinlik tanımlamanız önerilmez; Aksi takdirde, XAML, tasarımcıda düzenlendikten sonra el ile düzenlenmelidir.

### <a name="to-debug-workflow-xaml"></a>Workflow XAML hatalarını ayıklamak için

1. İçinde bir iş akışı veya etkinlik projesi açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

2. [Nasıl yapılır: Iş akışlarında kesme noktalarını ayarlama](../workflow-designer/how-to-set-breakpoints-in-workflows.md)bölümünde açıklandığı gibi, hata ayıklamak istediğiniz etkinlik veya etkinliklerde bir kesme noktası ayarlayın.

3. İş akışı tanımınızı içeren. xaml dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin. Tasarım görünümünde, kesme noktasını ayarladığınız etkinliğin XAML öğesi bildirimiyle aynı satırda görüntülenen bir kesme noktası görürsünüz.

4. [Nasıl yapılır: Iş akışı hata ayıklayıcısını çağırma](../workflow-designer/how-to-invoke-the-workflow-debugger.md)bölümünde açıklandığı gibi hata ayıklayıcıyı çağırın.

5. Kod yürütme, kesme noktalarınızın birine ulaştığında, bu kesme noktasıyla ilişkili XAML öğesi vurgulanacaktır. Sonraki kesme noktasına geçmek için **F10** veya **F11** tuşunu kullanın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: Iş akışlarında kesme noktaları ayarlama](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [nasıl yapılır: Iş akışı hata ayıklayıcıyı çağırma](../workflow-designer/how-to-invoke-the-workflow-debugger.md)