---
title: 'Nasıl yapılır: Windows sayaç verilerini toplama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9743fa7defbbf3321636d2ba4799454713a647db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64836781"
---
# <a name="how-to-collect-windows-counter-data"></a>Nasıl yapılır: Windows Sayaç Verileri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows sayaçları, profil oluşturma sırasında ayarlanan aralıklarda toplanabilecek sistem performans sayaçlarıdır. Profil Oluşturma Araçları raporun Işaretler görünümünde, bir satır her koleksiyon aralığı için **otomatik işaret** olarak etiketlenir. Satırda, bu aralıkta performans sayacı değerlerini tanımlayan sütunlar bulunur. Çözümlemeyi iki belirli işaret arasındaki bir zaman dilimi ile sınırlamak için, işaretleri seçin, sağ tıklayın ve ardından **Filter By**  ->   kısayol menüsünde**işaretlere** göre filtrele ' yi seçin.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-collect-windows-counter-data"></a>Windows sayaç verilerini toplamak için  
  
1. Performans Gezgini, Windows sayaçlarını yapılandırmak istediğiniz oturuma sağ tıklayın ve **Özellikler**' i seçin.  
  
2. **Özellik sayfalarında** **Windows sayaçları**' na tıklayın.  
  
3. **Windows sayaçlarını topla** onay kutusunu seçin.  
  
4. **Koleksiyon aralığı (msecs)** metin kutusuna bir zaman aralığı yazın.  
  
5. **Sayaç kategorisi** açılan listesinden bir kategori seçin.  
  
6. **Örnek** açılır listesinden bir örnek seçin.  
  
7. Uygulamanızı profillerinizi oluştururken kullanmak istediğiniz sayaçları seçin.  
  
8. Uygula ' ya tıklayın **.**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Performans oturumu özellikleri](../profiling/performance-session-properties.md)   
 [CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)
