---
title: 'Nasıl yapılır: rapor görünümlerinde gürültü azaltılması yapılandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5871473eaba749833714d6382beb487702ebe02d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64830989"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Nasıl yapılır: Rapor Görünümlerinde Gürültü Azaltmayı Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Performans raporları, çağrı ağacı görünümünde ve ayırma görünümünde sunulan veri miktarını sınırlayarak gürültü azaltma için yapılandırılabilir. Gürültü azaltma kullanarak performans sorunları daha belirgin bir şekilde yapılır. Bu, performans raporlarını analiz ettiğinizde yararlı olur.  
  
 Gürültü azaltma yapılandırma seçenekleri aşağıdaki ayarları içerir:  
  
- **Kırpma** Bir rapor analiz edildiğinde, görünüm, aşağıdaki kırpma yordamında açıklandığı gibi, yapılandırdığınız değer ve eşik ayarlarına denk gelen işlevleri atacaktır. Varsayılan olarak, kırpma etkindir.  
  
- **Katlama** Katlamayı etkinleştirirseniz, yapılandırdığınız ayarları karşılayan bir yoldaki birbirini izleyen işlevler, aşağıdaki katlama yordamında açıklandığı gibi birleştirilir. Varsayılan olarak katlama varsayılan olarak etkindir.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>Bir performans raporu için kırpmayı yapılandırmak için  
  
1. Oluşturulan raporda bir çağrı ağacı görünümü veya ayırma görünümü görüntülendiğinde, **Geliştirici** menüsünde **Profil Oluşturucu** ' ya ve ardından **gürültü azaltma seçenekleri**' ne tıklayın.  
  
     **Gürültü azaltma** iletişim kutusu görüntülenir.  
  
2. Kırpmayı etkinleştirmek için şu adımları izleyin:  
  
    1. **Kırpmayı etkinleştir**' i seçin. Bu varsayılan ayardır.  
  
        > [!NOTE]
        > Gürültü azaltma etkinleştirilirse, raporda bir bilgi çubuğu görüntülenir. Daha fazla bilgi için bkz. [çağrı ağacı görünümü](../profiling/call-tree-view.md) ve [ayırma görünümü](../profiling/dotnet-memory-allocations-view.md).  
  
    2. **Değer açılan listesini** kullanarak değer ayarını yapılandırın ve uygulanabilir ayarı seçin.  
  
    3. **Eşik** metin kutusuna bir yüzde değeri yazarak istenen eşik ayarını yapılandırın.  
  
    4. Oluşturulan raporda gürültü azaltma uyarısını etkinleştirmek için, **gürültü azaltma etkinleştirildiğinde uyarı görüntüle**' yi seçin. Bu varsayılan ayardır.  
  
3. Kırpmayı devre dışı bırakmak için **Kırpmayı etkinleştir**' i temizleyin.  
  
4. **Tamam**’a tıklayın.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>Performans raporu için katlamayı yapılandırmak için  
  
1. **Geliştirici** menüsünde, **Profil Oluşturucu** ' ya ve ardından **gürültü azaltma seçenekleri**' ne tıklayın.  
  
     **Gürültü azaltma** iletişim kutusu görüntülenir.  
  
2. Katlamayı etkinleştirmek için şu adımları izleyin:  
  
    1. **Katlamayı etkinleştir**' i seçin. Bu varsayılan ayardır.  
  
        > [!NOTE]
        > Gürültü azaltma etkinleştirilirse, raporda bir bilgi çubuğu görüntülenir. Daha fazla bilgi için bkz. [çağrı ağacı görünümü](../profiling/call-tree-view.md) ve [ayırma görünümü](../profiling/dotnet-memory-allocations-view.md).  
  
    2. **Değer açılan listesini** kullanarak değer ayarını yapılandırın ve uygulanabilir ayarı seçin.  
  
    3. **Eşik** metin kutusuna bir yüzde değeri yazarak istenen eşik ayarını yapılandırın.  
  
    4. Oluşturulan raporda gürültü azaltma uyarısını etkinleştirmek için, **gürültü azaltma etkinleştirildiğinde uyarı görüntüle**' yi seçin. Bu varsayılan ayardır.  
  
3. Katlamayı devre dışı bırakmak için **katlama özelliğini**temizleyin.  
  
4. **Tamam**’a tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans araçları rapor görünümlerini özelleştirme](../profiling/customizing-performance-tools-report-views.md)   
 [Nasıl yapılır: Izleme 'den kısa Işlevler hariç tutma veya dahil etme](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Çağrı ağacı görünümü](../profiling/call-tree-view.md)   
 [Ayırmalar Görünümü](../profiling/dotnet-memory-allocations-view.md)
