---
title: 'Nasıl yapılır: örnekleme olaylarını seçme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 017414bdbf8e0e1a3a664782aab1ea44bda030c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64779148"
---
# <a name="how-to-choose-sampling-events"></a>Nasıl Yapılır: Örnekleme Olayları Seçme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil Oluşturma Araçları, varsayılan olarak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] profili oluşturulmuş işlem tarafından kullanılan işlemci döngüsü sayısı olarak belirtilen bir aralıkta performans verilerini toplar. Bir aralıktaki varsayılan döngü sayısı 10.000.000 ' dir ve 1 GH bir bilgisayarda yaklaşık 0,01 saniyedir. Bir aralıktaki döngü sayısını değiştirebilir ve örnek olayı değiştirebilirsiniz. Aşağıdaki örnek olaylar mevcuttur:  
  
- Saat döngüleri-CPU ile bağlantılı sorunlar için.  
  
- Sayfa hataları-bellekle ilgili sorunlar için.  
  
- Sistem çağrıları-g/ç ile ilgili sorunlar için.  
  
- Performans sayacı-düşük düzeydeki performans sorunları için CPU sayaçları.  
  
> [!IMPORTANT]
> Örnekleme yöntemini kullanarak .NET bellek verileri (ayırmalar veya nesne yaşam süreleri veya her ikisi de) topluyorsanız, Kullanıcı tarafından belirtilen tüm örnekleme olayları yok sayılır ve uygun bellek ayırmaları veya çöp toplama olayları ya da her ikisi de veri toplamak için kullanılır.  
  
### <a name="to-select-a-sample-event"></a>Örnek bir olay seçmek için  
  
1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
2. **Özellik sayfalarında** **örnekleme** özelliklerine tıklayın.  
  
3. **Örnek olay** açılan listesinden, uygulamanızı profili eklemek için kullanmak istediğiniz örnek olayı seçin.  
  
    > [!NOTE]
    > **Kullanılabilir performans sayaçları** yalnızca **örnek olay** açılan listesinden **performans sayacı** ' nı seçtiğinizde etkinleştirilir.  
  
4. **Performans sayacı**' nı seçerseniz, **kullanılabilir performans sayaçları** ağaç görünümü denetiminden belirli bir CPU sayacı seçin.  
  
    - **Taşınabilir olaylar** düğümündeki sayaçlar tüm işlemci türlerinde kullanılabilir.  
  
    - **Platform olayları** düğümündeki sayaçlar, geçerli bilgisayardaki işlemciye özeldir ve diğer işlemci türlerinde kullanılamayabilir.  
  
5. Örnek bir olay seçtiğinizde, **örnekleme aralığı** metin kutusunda varsayılan bir örnekleme aralığı değeri görüntülenir. Gerekirse, metin kutusuna istediğiniz değeri girebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Nasıl yapılır: koleksiyon yöntemleri seçme](../profiling/how-to-choose-collection-methods.md)   
 [CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)   
 [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)   
 [Komut Satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)
