---
title: Windows sayaç verilerini toplama | Microsoft Docs
description: Windows sayaçları, izleme profili oluşturma bölümünde kullanılır. Windows sayaç verilerini nasıl toplayacağınızı ve analizin tek bir koleksiyon aralığıyla nasıl kısıtlanacağını öğrenin.
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3f1e8f38ee9cb63dfe5a79f0b410e957b4cefaf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886216"
---
# <a name="how-to-collect-windows-counter-data"></a>Nasıl yapılır: Windows sayaç verileri toplama

Windows sayaçları, profil oluşturma sırasında ayarlanan aralıklarda toplanabilecek sistem performans sayaçlarıdır. Profil Oluşturma Araçları raporun Işaretler görünümünde, bir satır her koleksiyon aralığı için **otomatik işaret** olarak etiketlenir. Satırda, bu aralıkta performans sayacı değerlerini tanımlayan sütunlar bulunur. Çözümlemeyi iki belirli işaret arasındaki bir zaman dilimi ile sınırlamak için, işaretleri seçin, sağ tıklayın ve ardından   >  kısayol menüsünde **işaretlere** göre filtrele ' yi seçin.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Windows sayaç verilerini toplamak için

1. Performans Gezgini, Windows sayaçlarını yapılandırmak istediğiniz oturuma sağ tıklayın ve **Özellikler**' i seçin.

2. **Özellik sayfalarında** **Windows sayaçları**' na tıklayın.

3. **Windows sayaçlarını topla** onay kutusunu seçin.

4. **Koleksiyon aralığı (msecs)** metin kutusuna bir zaman aralığı yazın.

5. **Sayaç kategorisi** açılan listesinden bir kategori seçin.

6. **Örnek** açılır listesinden bir örnek seçin.

7. Uygulamanızı profillerinizi oluştururken kullanmak istediğiniz sayaçları seçin.

8. Uygula ' ya tıklayın **.**

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Performans oturumu özellikleri](../profiling/performance-session-properties.md) 
 [CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)
