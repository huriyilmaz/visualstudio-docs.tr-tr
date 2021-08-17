---
title: Sayaç Windows verilerini toplama | Microsoft Docs
description: Windows sayaçları, ölçüm ölçüm profili oluşturmada kullanılır. Sayaç verilerini Windows ve analizi tek bir toplama aralığıyla kısıtlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bf19e1ac15867069aeec19151cd00258564a3865
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033518"
---
# <a name="how-to-collect-windows-counter-data"></a>Nasıl Windows: Windows toplama

Windows Sayaçlar, profil oluşturma sırasında belirli aralıklarla toplanabilir sistem performans sayaçlarıdır. Rapor raporunun İşaretler görünümünde Profil Oluşturma Araçları aralığı için bir satır **AutoMark** olarak etiketlenmiş. Satır, bu aralıkta performans sayacı değerlerini açıklayan sütunlar içerir. Analizi belirli iki işaret arasındaki bir süreyle kısıtlamak için işaretleri seçin, sağ tıklayın ve kısayol menüsünden İşaretlere Göre  >   Filtrele'yi seçin.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="to-collect-windows-counter-data"></a>Sayaç verilerini Windows için

1. Bu Performans Gezgini, sayaçları yapılandırmak istediğiniz oturuma sağ tıklayın ve Windows'yi **seçin.**

2. Özellik **Sayfaları'Windows** **tıklayın.**

3. Veri **Sayaçlarını Windows onay** kutusunu seçin.

4. Koleksiyon **aralığı (msecs)** metin kutusuna bir zaman aralığı yazın.

5. Sayaç Kategorisi açılan **listesinden bir** kategori seçin.

6. Örnek açılan **listesinden** bir örnek seçin.

7. Uygulama profili oluşturmak için kullanmak istediğiniz sayaçları seçin.

8. **Uygula'ya tıklayın.**

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Performans oturumu özellikleri](../profiling/performance-session-properties.md) 
 [CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)
