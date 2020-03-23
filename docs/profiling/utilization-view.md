---
title: Kullanım Görünümü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 926c67261f91aa8787d9be4a33dadbd3a890c568
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62823536"
---
# <a name="utilization-view"></a>Kullanım görünümü
**Kullanım görünümü,** geçerli işlem tarafından kullanılan CPU, GPU ve diğer sistem kaynakları hakkındaki bilgileri görüntüler (eşzamanlılık görselleştiricisini başlatmak için**Eşzamanlılık Görselleştiricisini** **Çözümle'yi** > seçin). Analiz edilen işlem, Boşta işlemi, Sistem işlemi ve zaman içinde sistemde çalışan diğer işlemler tarafından ortalama çekirdek kullanımını gösterir. Herhangi bir zamanda hangi çekirdeğin etkin olduğunu göstermez. Örneğin, iki çekirdeğin her biri belirli bir süre için yüzde 50 kapasiteyle çalışıyorsa, bu görünüm kullanılan bir mantıksal çekirdeği gösterir. Görünüm, profil oluşturma süresini kısa zaman dilimlerine bölerek oluşturulur. Her kesim için grafik, bu aralık sırasında mantıksal çekirdeklerde çalıştırılabilen ortalama işlem iş parçacığı sayısını çizer.

 ![CPU Kullanım Görünümü](../profiling/media/vsts_ppacpuutil.png "VSTS_PPAcpuUtil")

 Grafik, zaman (x ekseninde) ve hedef işlem, Boşta işlemi ve Sistem işlemi tarafından kullanılan ortalama mantıksal çekirdekleri gösterir. (Boşta işlemi boşta çekirdekleri gösterir. Sistem işlemi, Windows'ta diğer işlemler adına iş yapabilen bir işlemdir.) Sistemde çalışan kalan işlemler, kalan çekirdeklerin kullanımını hesaba katar.

 Mantıksal çekirdek sayısı y ekseninde gösterilir. Windows, donanımdaki eşzamanlı çoklu iş parçacığı desteğini mantıksal çekirdek (örneğin, Hyper-Threading) olarak ele verir. Bu nedenle, çekirdek başına iki donanım iş parçacığı destekleyen dört çekirdekli işlemci olan bir sistem sekiz mantıksal çekirdekli bir sistem olarak görünür. Bu, Cores görünümü için de geçerlidir. Daha fazla bilgi için [Çekirdekgörünümü'ne](../profiling/cores-view.md)bakın.

 GPU Etkinlik grafiği, zaman içinde kullanılan DirectX motorlarının sayısını gösterir.  Bir DMA paketini işliyorsa bir motor kullanılıyor.  Grafik belirli DirectX motoru (örneğin, 3D Engine, Video Engine ve diğerleri) göstermez.

## <a name="purpose"></a>Amaç
 EşzamanlıLık Görselleştiricisini kullandığınızda performans araştırmaları için başlangıç noktası olarak Kullanım Görünümü'nu öneririz. Bir uygulamanın zaman içinde eşzamanlılık derecesine genel bir bakış sağladığından, bunu performans ayarlaması veya paralelleştirme gerektiren alanları hızla tanımlamak için kullanabilirsiniz.

 Performans atonlamasıyla ilgileniyorsanız, beklentilerinizi karşılamayan davranışları belirlemeye çalışıyor olabilirsiniz. Ayrıca, mantıksal CPU çekirdeklerinin düşük kullanımı olan bölgelerin varlığını ve nedenini de arıyor olabilirsiniz. Ayrıca CPU ve GPU arasında kullanım desenleri arıyor olabilirsiniz.

 Bir uygulamayı paralelleştirmek le ilgileniyorsanız, büyük olasılıkla CPU'ya bağlı yürütme alanlarını veya CPU'yu kullanmadığınız alanları arıyorsunuzdur.

 CPU'ya bağlı alanlar yeşildir. Grafik, uygulama seri ise kullanılan bir çekirdek gösterir.

 CPU'yu kullanmadığınız alanlar gridir. Bunlar, uygulamanın boşta olduğu veya diğer CPU'ya bağlı çalışmayla çakışarak paralellik için fırsatlar sağlayan engelleme G/Ç'yi gerçekleştirdiği noktaları temsil edebilir.

 İlgi nizi çeken bir davranış bulduğunuzda, bu bölgeyi seçerek o bölgeyi yakınlaştırabilirsiniz. Yakınlaştırdıktan sonra, daha ayrıntılı analiz için İş Parçacıkları Görünümü'ne veya Çekirdek Görünümü'ne geçebilirsiniz.

 C++ AMP veya DirectX kullanarak GPU kullanıyorsanız, kullanımdaki GPU motorlarının sayısını veya GPU'nun beklenmedik bir şekilde boşta olduğu alanları belirlemek ilginizi çekebilir.

## <a name="zoom"></a>Zoom
 CPU Kullanım grafiğini veya GPU Etkinlik grafiğini yakınlaştırmak için bir bölüm seçin veya grafiğin üzerindeki yakınlaştırma kaydırıcısını kullanın. Diğer görünümlere geçerken yakınlaştırma ayarı devam eder. Yeniden uzaklaştırmak için yakınlaştırma kaydırıcısı aracını kullanın. **Ctrl**+**kaydırma**özelliğini kullanarak da yakınlaştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)
- [Çekirdek görünümü](../profiling/cores-view.md)