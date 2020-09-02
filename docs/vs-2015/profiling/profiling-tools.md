---
title: Profil Oluşturma Araçları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bcb230532da4a0b84ea0102d86534c28afe35558
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686187"
---
# <a name="profiling-tools"></a>Profil Araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil oluşturma ve tanılama araçları, bellek ve CPU kullanımına ilişkin sorunları ve uygulama düzeyindeki diğer sorunları tanılamanıza yardımcı olur. Bu araçlarla, hata ayıklayıcıda uygulamanızı çalıştırdığınız zaman içindeki verileri (değişken değerleri, işlev çağrıları ve olaylar gibi) biriktirişebilmeniz gerekir. Kodunuzun yürütülmesi sırasında uygulamanızın durumunu farklı noktalara bakabilirsiniz.  
  
 Proje türü için hangi araçların kullanılabildiğini görmek için en alttaki özete göz atın (örneğin, Masaüstü, UWP, ASP.NET).  
  
 Hata ayıklama oturumunuz sırasında araçları kullanmak için **hata ayıklama/Windows/tanılama araçları göster** ' i kullanarak veya odaklanmış bir performans analizi yapmak Için **hata ayıklama/performans profili Oluşturucu..** . ' yı kullanarak profil oluşturma araçlarına erişebilirsiniz.  Farklı yaklaşımlar hakkında daha fazla bilgi için bkz. [profil oluşturma araçları hata ayıklayıcı ile veya olmadan çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md) .  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 Bu yayına yönelik yeni özellikler hakkında bilgi edinmek için [profil oluşturma araçları](../profiling/what-s-new-in-profiling-tools.md) yenilikleri inceleyin.  
  
 Aşağıdaki bölümlerde, Visual Studio 'da bulunan farklı performans araçları açıklanır.  
  
## <a name="memory-usage"></a>Bellek Kullanımı  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 **Bellek kullanımı** aracı ile hata ayıklarken bellek sızıntılarını ve verimsiz belleği bulun. Araç, yönetilen ve yerel bellek yığınının anlık görüntülerini almanızı sağlar. Bu aracı masaüstü uygulamaları, Windows Universal Apps ve ASP.NET uygulamaları ile birlikte kullanabilirsiniz. **Bellek kullanımı** Aracı, hata ayıklarken (**Hata Ayıkla/Windows/göster tanılama araçları**) veya hata ayıklayıcı dışında (hata ayıklama/**performans profil oluşturucu...**) **Tanılama araçları** penceresinden çalıştırılabilir. Daha fazla bilgi için bkz. [hata ayıklama olmadan](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0) [bellek kullanımı](../profiling/memory-usage.md) ve bellek kullanımı.  
  
## <a name="cpu-usage"></a>CPU Kullanımı  
 ![Diagcpusküçük](../profiling/media/diagcpusmall.png "Diagcpusküçük")  
  
 **CPU kullanımı** Aracı, CPU 'nun C++, C#/vb ve JavaScript kodu yürütme zamanının nerede harcamaya yönelik olduğunu gösterir.  Bu aracı hem masaüstü hem de Windows Evrensel uygulamalarıyla, ayrıca Azure App Services uygulamalarıyla birlikte kullanabilirsiniz. **CPU kullanımı** Aracı, hata ayıklarken (**Hata Ayıkla/Windows/göster tanılama araçları**) veya hata ayıklayıcı dışında (hata ayıklama/**performans profil oluşturucu...**) **Tanılama araçları** penceresinden çalıştırılabilir. Daha fazla bilgi için bkz. [CPU kullanımı](../profiling/cpu-usage.md) .  
  
## <a name="performance-explorer"></a>Performans Gezgini  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 **Performans Gezgini** (**hata ayıklama/profil oluşturucu/performans Gezgini**), **CPU örnekleme**, **Izleme**, **.net bellek ayırma**ve **kaynak çekişmesi**gibi birçok farklı araç kullanmanıza olanak sağlar. Masaüstü uygulamaları ve ASP.NET uygulamaları ile Performans Gezgini araçları kullanabilirsiniz, ancak Windows Evrensel uygulamaları için kullanamazsınız. Daha fazla bilgi için bkz. [Performans Gezgini](../profiling/performance-explorer.md).  
  
## <a name="gpu-usage"></a>GPU Kullanımı  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Direct3D uygulamanızın üst düzey donanım kullanımını daha iyi anlamak için [GPU kullanımı](../debugger/gpu-usage.md) aracını kullanın. Bu aracı hem masaüstü hem de Windows Evrensel uygulamalarıyla kullanabilirsiniz, ancak ASP.NET uygulamaları için kullanamazsınız. Hata ayıklarken (hata**Ayıkla/göster tanılama araçları**) veya hata ayıklayıcı dışında (hata ayıklama/**performans profil oluşturucu...**), **GPU kullanım** aracı **Tanılama araçları** penceresinden çalıştırılabilir.  
  
## <a name="application-timeline"></a>Uygulama Zaman Çizelgesi  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 [Uygulama zaman çizelgesi](../profiling/application-timeline.md) Aracı, kaynak tüketiminin ayrıntılı bir görünümünü sağlayarak XAML uygulamalarının performansının artırılmasına yardımcı olur. **Uygulama zaman çizelgesi** masaüstü ve Windows Evrensel uygulamalarıyla birlikte kullanabilirsiniz, ancak ASP.NET uygulamaları kullanamazsınız. **Uygulama zaman çizelgesi** aracı **Tanılama araçları** penceresinden çalıştırılabilir (**hata ayıklama/performans profili Oluşturucu...**).  
  
## <a name="perftips"></a>PerfTips  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Hata ayıklayıcı, bir kesme noktası veya Adımlama işleminde yürütmeyi durdurduktan sonra, kesme ve önceki kesme noktası arasındaki geçen süre, düzenleyici penceresinde bir ipucu olarak görüntülenir. Bu [PerfTips](../profiling/perftips.md) , hata ayıklarken uygulamanızın performansını izlemenize ve çözümlemenize yardımcı olur. **PerfTips** for Desktop, Windows Universal ve ASP.net Apps bölümüne bakabilirsiniz.  
  
## <a name="javascript-memory"></a>JavaScript Belleği  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 [JavaScript bellek](../profiling/javascript-memory.md) Aracı, uygulamanızdaki her bir işlevin giriş ve çıkış bölümünde zamanlama bilgilerini toplayarak kodunuzda performansla ilgili sorunları ölçmenize, değerlendirmenize ve hedeflemenizi sağlar. Bu aracı Windows Evrensel HTML uygulamalarıyla birlikte kullanabilirsiniz. **JavaScript Işlev zamanlama** aracı **Tanılama araçları** penceresinden çalıştırılabilir (**hata ayıklama/performans profili Oluşturucu...**).  
  
## <a name="html-ui-responsiveness"></a>HTML UI yanıtlama hızı  
 ![Diabir Mlyanıt](../profiling/media/diaghtmlresp.png "Diabir Mlyanıt")  
  
 [HTML UI yanıtlama hızı](../profiling/html-ui-responsiveness.md) Aracı, uygulamalarınızda daha az sıklıkta yanıt verme, yavaş yükleme süresi ve görsel güncelleştirmeler gibi performans sorunlarını yalıtmanıza yardımcı olur. Bu aracı Windows Evrensel HTML uygulamalarıyla birlikte kullanabilirsiniz. **HTML UI yanıtlama hızı** Aracı, **Tanılama araçları** penceresinden çalıştırılabilir (**hata ayıklama/performans profili Oluşturucu...**).  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![Diagıntellitrace](../profiling/media/diagintellitrace.png "Diagıntellitrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) belirli olayları kaydetmenizi, hata ayıklayıcı olayları ve işlev çağrıları sırasında **Yereller** penceresindeki verileri incelemenizi ve yeniden oluşturulması zor olan hataların hatalarını ayıklamanıza olanak tanır.  IntelliTrace öncelikle bir hata ayıklama aracıdır, ancak performans araştırmaları için kullanılabilecek bilgiler de sağlar. Bu aracı, Masaüstü, Windows Universal ve ASP.NET C# uygulamalarıyla yalnızca Visual Studio Enterprise kullanabilirsiniz. Hata ayıklarken **Tanılama araçları** penceresinde IntelliTrace 'i bulabilirsiniz (**hata ayıklama/Windows/göster tanılama araçları**).  
  
## <a name="profiling-in-production"></a>Üretimde profil oluşturma  
 Üretimde profil oluşturmak için önerilen yaklaşım, bir CPU profili toplamak için [vsperf.exekullanarak komut satırından ](../profiling/using-the-profiling-tools-from-the-command-line.md) profildir. Azure App Service uzak profil oluşturma desteği için [Sunucu Gezgini veya kudu portalı](https://azure.microsoft.com/blog/remote-profiling-support-in-azure-app-service/)aracılığıyla profil oluşturabilirsiniz.  
  
## <a name="which-tool-should-i-use"></a>Hangi aracı kullanmalıyım?  
 Aşağıda, Visual Studio tekliflerinin farklı araçları ve bunları kullanabileceğiniz farklı proje türlerini listeleyen bir tablo verilmiştir:  
  
|Performans aracı|Windows masaüstü|Windows Evrensel/mağaza|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[Bellek Kullanımı](../profiling/memory-usage.md)|evet|evet|hayır|  
|[CPU Kullanımı](../profiling/cpu-usage.md)|evet|evet|Yalnızca Azure App Service|  
|[GPU Kullanımı](../debugger/gpu-usage.md)|evet|evet|hayır|  
|[Uygulama Zaman Çizelgesi](../profiling/application-timeline.md)|evet|evet|hayır|  
|[PerfTips](../profiling/perftips.md)|evet|XAML için Evet, HTML için Hayır|hayır|  
|[Performans Gezgini](../profiling/performance-explorer.md)|evet|hayır|evet|  
|[IntelliTrace](../debugger/intellitrace.md)|Yalnızca .NET Enterprise|Yalnızca .NET Enterprise|Yalnızca .NET Enterprise|  
|[HTML kullanıcı arabirimi yanıt hızı](../profiling/html-ui-responsiveness.md)|hayır|HTML için Evet, XAML için Hayır|hayır|  
|[JavaScript Belleği](../profiling/javascript-memory.md)|hayır|HTML için Evet, XAML için Hayır|hayır|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
