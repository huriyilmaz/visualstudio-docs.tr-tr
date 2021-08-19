---
title: Office çözümleri için olay günlüğü
description: Çalışma zamanı tarafından yakalanan özel durum iletilerini Windows için olay görüntüleyiciyi nasıl kullanabileceğiniz Office için Visual Studio Araçları öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047094"
---
# <a name="event-logging-for-office-solutions"></a>Office çözümleri için olay günlüğü
  Çözüm yükleme veya kaldırma işlemi Windows tarafından yakalanan özel durum iletilerini görmek için olay görüntüleyicisini Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kullanabilirsiniz. Yükleme ve dağıtım sorunlarını çözmek için olay günlükleyiciden bu iletileri kullanabilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="read-the-event-log"></a>Olay Günlüğünü okuma
 Verileri **Olay Görüntüleyicisi** ve görmek istediğiniz olayları filtrele.

### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Windows Server 2003 ve Windows XP'de Olay Günlüğünü okumak için

1. Bu Denetim Masası Yönetimsel **Araçlar'a açın.**

2. başlangıç **Olay Görüntüleyicisi.**

3. Olay günlükleri listesinde Uygulama'ya **tıklayın.**

4. Görünüm menüsünde **Filtre'ye** **tıklayın.**

5. Olay kaynağı listesinde **4.0 VSTO seçin.** 

6. Yükleme olayları için Olay Kimliği **kutusuna** **4096 yazın.**

7. Filtrelenmiş **görünümü** görmek için Tamam'a tıklayın.

### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Windows 7, Windows Vista ve Windows Server 2008'de Olay Günlüğünü okumak için

1. Bu Denetim Masası Yönetimsel **Araçlar'a açın.**

2. başlangıç **Olay Görüntüleyicisi.**

3. Günlükler **Windows genişletin.**

4. Olay günlükleri listesinde Uygulama'ya **tıklayın.**

5. Eylem menüsünde **Geçerli** Günlüğü **Filtrele'ye tıklayın.**

6. Olay kaynağı listesinde **4.0 VSTO seçin.** 

7. Yükleme olayları için Olay Kimliği **kutusuna** **4096 yazın.**

8. Filtrelenmiş **görünümü** görmek için Tamam'a tıklayın.

   Olay görüntüleyicisi aşağıdaki bilgileri içerir:

- Çözüm için dağıtım bildiriminin konumu.

- Hatanın veya özel durumun nedenini açıklayan bir ileti.

  Bu özel durum iletileri, güvenilmeyen sertifika, güvenilmeyen belge konumu veya geçersiz dağıtım bildirimi gibi bir yükleme sorununun nedenini belirlemenize yardımcı olabilir.

  Bir Office çözümü kaldırıldıktan sonra, özel durum iletileri olay günlüğünde kalır.

  Özel durum iletilerini bir çözüm Office göstermek veya günlüğe [](../vsto/debugging-office-projects.md) Office için bkz. Office projelerinde hata ayıklama ve Office [ayıklama.](../vsto/debugging-office-projects.md)

### <a name="localization"></a>Yerelleştirme
 Özel durum iletinin dili, çalışma zamanı Office için Visual Studio Araçları belirlenir. Örneğin, son kullanıcı bilgisayarda Japonca dil paketi yüklüyse, özel durum iletisi Japonca'daki olay günlüğüne yazılır.

## <a name="disable-the-event-logger"></a>Olay günlükleyicisini devre dışı bırakma
 Varsayılan olarak, çözümlerini yükledikten veya kaldırdığınız zaman olay günlük Office etkinleştirilir. Olay günlükçlerini devre dışı bırakmak için ortam değişken VSTO_EVENTLOGDISABLED "1" (bir) olarak ayarlarsınız.

### <a name="to-disable-the-event-log"></a>Olay Günlüğünü devre dışı bırakmak için

1. Bu Denetim Masası Sistem'i **açın.**

2. Gelişmiş sekmesinde **Ortam** **Değişkenleri'ne tıklayın.**

3. Sistem değişkenleri **bölmesinde Yeni'ye** **tıklayın.**

4. Yeni **Sistem Değişkeni iletişim** kutusunda Değişken **VSTO_EVENTLOGDISABLED** **yazın.**

5. Değişken **değeri kutusuna** **1 yazın.**

6. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [Çözüm Office sorunlarını giderme](../vsto/troubleshooting-office-solution-deployment.md)
