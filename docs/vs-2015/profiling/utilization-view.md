---
title: Kullanım görünümü | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 238d821795aaa4e9ef0ac06e117316450b46fda4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145361"
---
# <a name="utilization-view"></a>Kullanım Görünümü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Kullanım görünümü** , geçerli işlem tarafından kullanılan CPU, GPU ve diğer sistem kaynaklarıyla ilgili bilgileri görüntüler. Analiz edilen işlem, boşta işlem, sistem işlemi ve zaman içinde sistemde çalışan diğer işlemlere göre ortalama temel kullanımı gösterir. Belirli bir zamanda etkin olan belirli bir çekirdeği göstermez. Örneğin, belirli bir süre boyunca her biri yüzde 50 kapasiteye iki çekirdek çalışıyorsa, bu görünüm kullanılan bir mantıksal çekirdeği gösterir. Görünüm, profil oluşturma süresi kısa saat dilimlerine bölünerek oluşturulur. Her segment için grafik, bu Aralık süresince mantıksal çekirdekler üzerinde yürütülen işlem iş parçacıklarının ortalama sayısını çizer.  
  
 ![CPU kullanımı görünümü](../profiling/media/vsts-ppacpuutil.png "VSTS_PPAcpuUtil")  
  
 Grafik, saat (x ekseninde) ve hedef işlem, boşta işlem ve sistem işlemi tarafından kullanılan ortalama mantıksal çekirdekleri gösterir. (Boş işlem boştaki çekirdekleri gösterir. Sistem işlemi, Windows 'da diğer işlemler adına iş gerçekleştirebilen bir işlemdir.) Kalan tüm çekirdekleri kullanım için sistem hesabında çalışan kalan süreçler.  
  
 Mantıksal çekirdek sayısı y ekseninde gösterilir. Windows, donanım (örneğin, hiper Iş parçacığı) olarak donanımda eşzamanlı çoklu iş parçacıklı desteğe davranır. Bu nedenle, çekirdek başına iki donanım iş parçacığını destekleyen dört çekirdekli bir işlemciye sahip bir sistem, sekiz mantıksal çekirdekli bir sistem olarak görünür. Bu, çekirdek görünümü için de geçerlidir. Daha fazla bilgi için bkz. [çekirdek görünümü](../profiling/cores-view.md).  
  
 GPU etkinlik grafiği zaman içinde kullanımdaki DirectX altyapısının sayısını gösterir.  Bir altyapı, bir DMA paketi işişişişişişdir.  Grafik, belirli DirectX altyapısını (örneğin, 3B altyapısı, video altyapısı ve diğerleri) göstermez.  
  
## <a name="purpose"></a>Amaç  
 Eşzamanlılık görselleştiricisi kullandığınızda performans araştırmaları için başlangıç noktası olarak kullanım görünümü önerilir. Zaman içinde bir uygulamadaki eşzamanlılık derecesindeki bir genel bakış sağladığından, performansı ayarlama veya paralelleştirme gerektiren bölgeleri hızlı bir şekilde tanımlamak için kullanabilirsiniz.  
  
 Performans ayarı ile ilgileniyorsanız, beklentilerinizi karşılamayan davranışı belirlemeye çalışıyor olabilirsiniz. Ayrıca, mantıksal CPU çekirdekleri için düşük düzeyde kullanımı olan bölgelerin varlığını ve nedenini de arıyor olabilirsiniz. CPU ve GPU arasındaki kullanım düzenlerini de arıyor olabilirsiniz.  
  
 Bir uygulamayı paralel hale getirme konusunda ilgileniyorsanız, büyük olasılıkla, CPU ile bağlantılı veya CPU 'YU kullanmıyordaki alanların CPU ile bağlantılı alan veya alan olduğunu bakıyorsunuzdur.  
  
 CPU ile bağlantılı alanların yeşili. Grafik, uygulama seri ise kullanılan bir çekirdeği gösterir.  
  
 CPU 'YU kullanmıyorsanız gri olan bölgeler. Bunlar, uygulamanın boşta olduğu noktaları temsil edebilir veya diğer CPU bağlantılı çalışmalarla örtüşerek paralellik olanakları sağlayan g/ç 'yi engelliyor.  
  
 İlgilendiğiniz bir davranış bulduğunuzda, bu bölgeyi seçerek yakınlaştırabilirsiniz. ' İ yakınlaştırdıktan sonra daha ayrıntılı analiz için Iş parçacıkları görünümüne veya çekirdek görünümüne geçiş yapabilirsiniz.  
  
 GPU 'YU C++ AMP veya DirectX kullanarak kullanıyorsanız, kullanımdaki GPU altyapısının sayısını veya GPU 'nun beklenmedik bir şekilde boşta olduğu bölgeleri tanımlamayı düşünebilirsiniz.  
  
## <a name="zooming"></a>Yakınlaştırma  
 CPU kullanımı grafiğini veya GPU etkinlik grafiğini yakınlaştırmak için bir bölüm seçin ya da grafiğin üzerindeki yakınlaştırma kaydırıcı aracını kullanın. Diğer görünümlere geçiş yaparken yakınlaştırma ayarı devam ettirir. Yeniden yakınlaştırmak için yakınlaştırma kaydırıcı aracını kullanın. Ayrıca CTRL + SCROLL kullanarak da yakınlaştırma yapabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)   
 [Çekirdekler Görünümü](../profiling/cores-view.md)
