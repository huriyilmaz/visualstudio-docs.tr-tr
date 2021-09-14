---
title: Office çözümleri için olay günlüğü
description: Office için Visual Studio Araçları çalışma zamanı tarafından yakalanan özel durum iletilerini görmek için Windows olay görüntüleyicisini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9dedf882fcd149c2eecc04d712df19af980b5c48
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634094"
---
# <a name="event-logging-for-office-solutions"></a>Office çözümleri için olay günlüğü
  Office çözümlerini yüklerken veya kaldırdığınızda tarafından yakalanan özel durum iletilerini görmek için Windows 'deki olay görüntüleyicisini kullanabilirsiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Bu iletileri, yükleme ve dağıtım sorunlarını çözmek için olay günlükçüsü ' nden kullanabilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="read-the-event-log"></a>Olay günlüğünü okuyun
 **Olay Görüntüleyicisi** açın ve görmek istediğiniz olayları filtreleyin.

### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Windows Server 2003 ve Windows XP 'de olay günlüğünü okumak için

1. Denetim Masası 'nda **Yönetimsel Araçlar**' ı açın.

2. **Olay Görüntüleyicisi** başlatın.

3. Olay günlükleri listesinde **uygulama**' yı seçin.

4. **Görünüm** menüsünde **filtre**' ye tıklayın.

5. **olay kaynağı** listesinde **VSTO 4,0**' ı seçin.

6. Yükleme olayları için, **olay kimliği** kutusuna **4096** yazın.

7. Filtrelenmiş görünümü görmek için **Tamam** ' ı tıklatın.

### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Windows 7, Windows Vista ve Windows Server 2008 ' de olay günlüğünü okumak için

1. Denetim Masası 'nda **Yönetimsel Araçlar**' ı açın.

2. **Olay Görüntüleyicisi** başlatın.

3. **Windows günlükleri**' ni genişletin.

4. Olay günlükleri listesinde **uygulama**' yı seçin.

5. **Eylem** menüsünde **geçerli günlüğü filtrele**' ye tıklayın.

6. **olay kaynağı** listesinde **VSTO 4,0**' ı seçin.

7. Yükleme olayları için, **olay kimliği** kutusuna **4096** yazın.

8. Filtrelenmiş görünümü görmek için **Tamam** ' ı tıklatın.

   Olay Görüntüleyicisi aşağıdaki bilgileri içerir:

- Çözüm için dağıtım bildiriminin konumu.

- Hatanın veya özel durumun nedenini açıklayan bir ileti.

  Bu özel durum iletileri, güvenilmeyen bir sertifika, güvenilmeyen belge konumu veya geçersiz bir dağıtım bildirimi gibi yükleme sorununun nedenini belirlemenize yardımcı olabilir.

  bir Office çözümü kaldırıldıktan sonra, özel durum iletileri olay günlüğünde kalır.

  Office bir çözüm çalışırken özel durum iletilerini göstermek veya günlüğe kaydetmek için bkz. [Office projeleri hata ayıklama](../vsto/debugging-office-projects.md) ve [Office projelerinde hata ayıklama](../vsto/debugging-office-projects.md).

### <a name="localization"></a>Yerelleştirme
 özel durum iletisinin dili Office için Visual Studio Araçları çalışma zamanı dili tarafından belirlenir. Örneğin, Son Kullanıcı bilgisayarda Japonca dil paketi yüklüyse, özel durum iletisi, Japonca 'daki olay günlüğüne yazılır.

## <a name="disable-the-event-logger"></a>Olay günlükçüsü 'yi devre dışı bırakma
 varsayılan olarak, Office çözümlerini yüklediğinizde veya kaldırdığınızda olay günlükçüsü etkinleştirilir. VSTO_EVENTLOGDISABLED ortam değişkenini "1" (bir) olarak ayarlayarak olay günlükçüsü 'yi devre dışı bırakabilirsiniz.

### <a name="to-disable-the-event-log"></a>Olay günlüğünü devre dışı bırakmak için

1. Denetim Masası 'nda **sistem**' i açın.

2. **Gelişmiş** sekmesinde, **ortam değişkenleri**' ne tıklayın.

3. **Sistem değişkenleri** bölmesinde **Yeni**' ye tıklayın.

4. **Yeni sistem değişkeni** iletişim kutusunda, **değişken adı** kutusuna **VSTO_EVENTLOGDISABLED** yazın.

5. **Değişken değeri** kutusuna **1** yazın.

6. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office çözüm dağıtımı sorunlarını giderme](../vsto/troubleshooting-office-solution-deployment.md)
