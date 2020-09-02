---
title: 'Nasıl yapılır: satır düzeyi örnekleme verileri toplama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65890bf31a1257c3a41bc1fd7ed3f732c50eda14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185949"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Nasıl yapılır: Satır Düzeyi Örnekleme Verileri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Satır düzeyinde örnekleme, profil oluşturucunun, yüksek ayrıcalıklı örneklere sahip bir işlev gibi, işlemcinin yoğun bir işlev kodunda nerede bir süre harcadığını belirlemede kullandığı bir işlemdir.  
  
## <a name="overview"></a>Genel Bakış  
 Satır düzeyi örnekleme için, profil oluşturucu program çağrı yığınını belirlenen aralıklarda yönlendirir ve bu sonuçları toplar. Bu sonuçlar, örnek çekilirken işlemcinin hangi talimatları yürüttüğünü gösterir. Dışlamalı örneklerle ilgili toplanan veriler daha sonra kod satırlarını ve yönerge işaretçisini (IP) belirlemek için çözümlenir.  
  
 Satır düzeyi örnekleme, yönetilen ve yerel kod için de kullanılır. Bu verileri görüntüleyen performans raporları, satırlar görünümü ve modüller görünümünü içerir.  
  
 Yerel kod için karakter başlangıç/bitiş bilgileri kullanılamıyor. Çok satırlı deyimler için, satır başlangıç bilgileri yerel kod için kullanılamaz; yalnızca satır sonu bilgileri kullanılabilir.  
  
### <a name="available-data"></a>Kullanılabilir veriler  
 Kullanılabilir satır düzeyi örnekleme verileri aşağıdaki bilgileri içerir:  
  
- İşlev adı.  
  
- İşlev adresi.  
  
- Satır başlangıcı – örneklenmiş kodun satır numarası.  
  
- Satır sonu: bitiş kaynak satır numarası. Tek bir program ifadesinin birden çok kaynak kodu satırını yaydığı durumlar dışında, bu genellikle "satır başlangıcı" verileriyle aynıdır.  
  
- Karakter başlangıcı – toplu Örneğin başlangıç sütunu. Tek bir satır birden çok program deyimi içerdiğinde bu genellikle 0 ' dır.  
  
- Toplu örnek için karakter sonu – bitiş sütunu.  
  
- IP – toplam örneğin alındığı adres (yalnızca IP görünümü).  
  
  **Modüller** görünümünde, bir işlevde satır düzeyi istatistikleri varsa, istatistikler her bir işlevin altına yuvalanır. Bunlara ek olarak, her satırın altında iç içe geçmiş IP düzeyi istatistikler sunulur.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Yönetilen kod için satır düzeyinde örnekleme kapatma  
 Varsayılan olarak, satır düzeyi örnekleme açıktır. Aşağıdakilerden birini yaparak, yönetilen kod için satır düzeyinde veri toplamayı kapatabilirsiniz:  
  
- Profil oluşturmadan önce **VSPerfCLREnv/samplelineoff**yazın. Bu, hem uygulamaları hem de hizmetleri etkiler.  
  
     veya  
  
- Bir uygulamayı başlatırken **VSPerfCmd/LineOff \<other arguments> **yazın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Performans Araçları Verilerini Analiz Etme](../profiling/analyzing-performance-tools-data.md)
