---
title: Kullanım görünümü | Microsoft Docs
description: Kullanım görünümünün, geçerli işlem tarafından kullanılan CPU, GPU ve diğer sistem kaynaklarıyla ilgili bilgileri görüntüleyeceğini öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 943b1c5647be78b796e9eb386aeb54d33adadd1a3d146c39a2880024cf3e91bd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410182"
---
# <a name="utilization-view"></a>Kullanım görünümü
**Kullanım görünümü** , geçerli işlem tarafından kullanılan CPU, GPU ve diğer sistem kaynaklarıyla ilgili bilgileri görüntüler (   >  eşzamanlılık Görselleştiriciyi başlatmak için **eşzamanlılık görselleştirmesini** Çözümle ' yi seçin). Analiz edilen işlem, boşta işlem, sistem işlemi ve zaman içinde sistemde çalışan diğer işlemlere göre ortalama temel kullanımı gösterir. Belirli bir zamanda etkin olan belirli bir çekirdeği göstermez. Örneğin, belirli bir süre boyunca her biri yüzde 50 kapasiteye iki çekirdek çalışıyorsa, bu görünüm kullanılan bir mantıksal çekirdeği gösterir. Görünüm, profil oluşturma süresi kısa saat dilimlerine bölünerek oluşturulur. Her segment için grafik, bu Aralık süresince mantıksal çekirdekler üzerinde yürütülen işlem iş parçacıklarının ortalama sayısını çizer.

 ![CPU kullanımı görünümü](../profiling/media/vsts_ppacpuutil.png "VSTS_PPAcpuUtil")

 Grafik, saat (x ekseninde) ve hedef işlem, boşta işlem ve sistem işlemi tarafından kullanılan ortalama mantıksal çekirdekleri gösterir. (Boş işlem boştaki çekirdekleri gösterir. sistem işlemi, başka işlemler adına iş gerçekleştirebilen Windows bir işlemdir.) Kalan tüm çekirdekleri kullanım için sistem hesabında çalışan kalan süreçler.

 Mantıksal çekirdek sayısı y ekseninde gösterilir. Windows, donanımda çok sayıda çoklu iş parçacıklı desteğini mantıksal çekirdek olarak (örneğin, hiper iş parçacığı) değerlendirir. Bu nedenle, çekirdek başına iki donanım iş parçacığını destekleyen dört çekirdekli bir işlemciye sahip bir sistem, sekiz mantıksal çekirdekli bir sistem olarak görünür. Bu, çekirdek görünümü için de geçerlidir. Daha fazla bilgi için bkz. [çekirdek görünümü](../profiling/cores-view.md).

 GPU etkinlik grafiği zaman içinde kullanımdaki DirectX altyapısının sayısını gösterir.  Bir altyapı, bir DMA paketi işişişişişişdir.  Grafik, belirli DirectX altyapısını (örneğin, 3B altyapısı, video altyapısı ve diğerleri) göstermez.

## <a name="purpose"></a>Amaç
 Eşzamanlılık görselleştiricisi kullandığınızda performans araştırmaları için başlangıç noktası olarak kullanım görünümü önerilir. Zaman içinde bir uygulamadaki eşzamanlılık derecesindeki bir genel bakış sağladığından, performansı ayarlama veya paralelleştirme gerektiren bölgeleri hızlı bir şekilde tanımlamak için kullanabilirsiniz.

 Performans ayarı ile ilgileniyorsanız, beklentilerinizi karşılamayan davranışı belirlemeye çalışıyor olabilirsiniz. Ayrıca, mantıksal CPU çekirdekleri için düşük düzeyde kullanımı olan bölgelerin varlığını ve nedenini de arıyor olabilirsiniz. CPU ve GPU arasındaki kullanım düzenlerini de arıyor olabilirsiniz.

 Bir uygulamayı paralel hale getirme konusunda ilgileniyorsanız, büyük olasılıkla, CPU ile bağlantılı veya CPU 'YU kullanmıyordaki alanların CPU ile bağlantılı alan veya alan olduğunu bakıyorsunuzdur.

 CPU ile bağlantılı alanların yeşili. Grafik, uygulama seri ise kullanılan bir çekirdeği gösterir.

 CPU 'YU kullanmıyorsanız gri olan bölgeler. Bunlar, uygulamanın boşta olduğu noktaları temsil edebilir veya diğer CPU bağlantılı çalışmalarla örtüşerek paralellik olanakları sağlayan g/ç 'yi engelliyor.

 İlgilendiğiniz bir davranış bulduğunuzda, bu bölgeyi seçerek yakınlaştırabilirsiniz. ' İ yakınlaştırdıktan sonra daha ayrıntılı analiz için Iş parçacıkları görünümüne veya çekirdek görünümüne geçiş yapabilirsiniz.

 gpu 'yu C++ AMP veya DirectX kullanarak kullanıyorsanız, kullanımdaki gpu altyapısının sayısını veya gpu 'nun beklenmedik bir şekilde boşta olduğu bölgeleri tanımlamayı düşünebilirsiniz.

## <a name="zoom"></a>Zoom
 CPU kullanımı grafiğini veya GPU etkinlik grafiğini yakınlaştırmak için bir bölüm seçin ya da grafiğin üzerindeki yakınlaştırma kaydırıcı aracını kullanın. Diğer görünümlere geçiş yaparken yakınlaştırma ayarı devam ettirir. Yeniden yakınlaştırmak için yakınlaştırma kaydırıcı aracını kullanın. Ayrıca, **CTRL** kaydırma kullanarak da yakınlaştırma yapabilirsiniz + .

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)
- [Çekirdekler görünümü](../profiling/cores-view.md)