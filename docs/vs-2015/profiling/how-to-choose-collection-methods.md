---
title: 'Nasıl yapılır: koleksiyon yöntemlerini seçme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ff14ce88f2032b998214ed11310a15550321dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199801"
---
# <a name="how-to-choose-collection-methods"></a>Nasıl yapılır: Koleksiyon Metotları Seçme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Profil oluşturma araçları, performans verilerini toplamak için üç yöntemi destekler: örnekleme, izleme ve eşzamanlılık. .NET bellek ayırma ve yaşam süresi verilerini toplamak için örnekleme veya izleme yöntemini de kullanabilirsiniz.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Uygulamanız için en uygun koleksiyon yöntemini belirtmek üzere performans oturumu **yöntemi** özelliğini kullanabilirsiniz. Bir performans oturumunun Özellik sayfalarından, Performans Gezgini veya performans sihirbazından koleksiyon yöntemini ayarlayabilirsiniz. Komut satırı araçları kullanıyorsanız daha fazla bilgi için bkz. [komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md) .  
  
## <a name="performance-wizard"></a>Performans Sihirbazı  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Performans sihirbazını kullanarak bir koleksiyon yöntemi seçmek için  
  
- Sihirbazın ilk sayfasında, aşağıdaki seçeneklerden birini seçin:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**CPU örnekleme**|İlk analizler ve CPU kullanımı sorunlarını analiz etmek için yararlı olan uygulama istatistiklerini toplar.|  
|**Yapısı**|Odaklanmış analizler ve giriş/çıkış performans sorunlarını analiz etmek için yararlı olan ayrıntılı zamanlama verilerini toplar.|  
|**.NET bellek ayırma**|[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Örnekleme profil oluşturma yöntemini kullanarak bellek ayırma verilerini toplar.|  
|**Eşzamanlılık**|Sayısal kaynak çekişmesini verilerini toplar.|  
  
## <a name="performance-explorer"></a>Performans Gezgini  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>Performans Gezgini kullanarak bir koleksiyon yöntemi seçmek için  
  
1. **Performans Gezgini** araç çubuğunda, **Yöntem** açılır listesinin yanındaki oka tıklayın.  
  
2. Tercih ettiğiniz koleksiyon yöntemine tıklayın.  
  
## <a name="performance-session-property-pages"></a>Performans oturumu Özellik sayfaları  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Performans oturumu özelliklerini kullanarak örnekleme veya izleme yöntemini seçmek için  
  
1. **Performans Gezgini**' de, performans oturumu ' nu seçin.  
  
     Bir performans oturumu dosya adının. psess uzantısı vardır.  
  
2. Performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
3. **Özellik sayfalarında**, **genel**' e tıklayın.  
  
4. Tercih ettiğiniz koleksiyon yöntemine tıklayın.  
  
    - Örnekleme verilerini toplarken kullanılabilir diğer seçenekler hakkında daha fazla bilgi için bkz. [örnekleme kullanarak performans Istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
    - Örnekleme verilerini toplarken kullanılabilir diğer seçenekler hakkında daha fazla bilgi için bkz. [Izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Performans oturumu özelliklerini kullanarak .NET bellek verileri toplamayı seçmek için  
  
1. **Performans Gezgini**' de, performans oturumu ' nu seçin.  
  
     Bir performans oturumu dosya adının. psess uzantısı vardır.  
  
2. Performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
3. **Özellik sayfalarında**, **genel**' e tıklayın.  
  
4. **Örnekleme** veya **izleme**' ye tıklayın.  
  
5. Nesne ayırmalarının boyutunu ve sayısını toplamak için **.NET nesne ayırma bilgilerini topla** ' ya tıklayın [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
6. Seçim Ayrıca, nesne belleğinin geri alındığı çöp toplama nesilleri hakkında veri toplamak için **.NET nesne yaşam süresi bilgilerini toplayın** .  
  
     .NET bellek verileri topladığınızda kullanılabilen diğer seçenekler hakkında bilgi için bkz. [.net bellek ayırma ve ömür verileri toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Performans oturumu özelliklerini kullanarak eşzamanlılık veri toplamayı seçme  
  
1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
2. **Özellik sayfalarında**, **genel**' e tıklayın.  
  
3. **Eşzamanlılık**' e tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)   
 [Performans oturumu özellikleri](../profiling/performance-session-properties.md)
