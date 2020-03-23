---
title: 'Nasıl Kullanılır: Windows Karşı Veri Toplama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c85187fd54d61fdf40956c8aee3c0a222d95a313
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776325"
---
# <a name="how-to-collect-windows-counter-data"></a>Nasıl kullanılır: Windows karşı veri toplama

Windows Sayaçları, profil oluşturma sırasında belirli aralıklarla toplanabilen sistem performans sayaçlarıdır. Profil Oluşturma Araçları raporunun İşaretler görünümünde, bir satır her toplama aralığı için **AutoMark** olarak etiketlenir. Satır, bu aralıktaki performans sayacı değerlerini açıklayan sütunlar içerir. Çözümlemeni iki belirli işaret arasında bir süreyle sınırlamak için işaretleri seçin, sağ tıklatın ve ardından kısayol menüsünden > **İşaretlere** **Göre Filtrele'yi**seçin.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

## <a name="to-collect-windows-counter-data"></a>Windows sayacı verilerini toplamak için

1. Performans Gezgini'nde, Windows sayaçlarını yapılandırmak istediğiniz oturuma sağ tıklayın ve **Özellikler'i**seçin.

2. Özellik **Sayfalarında,** **Windows Sayaçları'nı**tıklatın.

3. Windows **Sayaçlarını Topla** onay kutusunu seçin.

4. Toplama **aralığı (msecs)** metin kutusuna bir zaman aralığı yazın.

5. **Sayaç Kategorisi** açılır listesinden bir kategori seçin.

6. **Örnek** açılır listesinden bir örnek seçin.

7. Uygulamanızın profilini yaparken kullanmak istediğiniz sayaçları seçin.

8. **Uygula'yı tıklatın.**

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını](../profiling/configuring-performance-sessions.md)
yapılandırma[Performans oturumu özellikleri](../profiling/performance-session-properties.md)
[CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)
