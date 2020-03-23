---
title: Kötü-Behaved Multithreaded Uygulamalar için Ortak Desenler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aec033266ccb2a6e6dcd0342669b7c31082488a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62788931"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Hatalı davranan çok iş parçacıklı uygulamalar için ortak desenler

Eşzamanlılık Görselleştiricisi, geliştiricilerin çok iş parçacığı yla dolu bir uygulamanın davranışını görselleştirmelerine yardımcı olur. Bu araç, kötü davranan çok iş parçacığı uygulamaları için ortak desenler bir galeri içerir. Galeri, her desentarafından temsil edilen davranışın açıklamasıyla birlikte, araç aracılığıyla ortaya çıkarılan tipik ve tanınabilir görsel desenler, bu davranışın olası sonucunu ve bunu çözmek için en yaygın yaklaşımı içerir.

## <a name="lock-contention-and-serialized-execution"></a>Kilit çekişmesi ve serileştirilmiş yürütme

![Seri leştirilmiş yürütmeyle sonuçlanan kilit çekişmesi](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")

Bazen paralelleştirilmiş bir uygulama, birkaç iş parçacığı na ve bilgisayarda yeterli sayıda mantıksal çekirdek olmasına rağmen seri olarak yürütmeye devam eder. İlk belirti kötü multithreaded performans, belki de biraz daha yavaş bir seri uygulama daha. İş Parçacıkları Görünümü'nde, paralel çalışan birden çok iş parçacığı görmezsiniz; bunun yerine, yalnızca bir iş parçacığı herhangi bir zamanda yürütülen olduğunu görürsünüz. Bu noktada, iş parçacığında bir eşitleme kesimini tıklattığınızda, engellenen iş parçacığı (arama yığınını engelleme) için bir çağrı yığını ve engelleme koşulunu kaldıran iş parçacığı (arama yığınını kaldırma) görebilirsiniz. Ayrıca, engellemeyi kaldırma çağrı yığını çözümlediğiniz işlemde oluşursa, Iş Parçacığına Hazır bağlayıcı görüntülenir. Bu noktadan itibaren, serileştirmenin nedenini daha da araştırmak için arama yığınlarını engelleme ve engellemeyi kaldırma dan kodunuza gidebilirsiniz.

Aşağıdaki resimde gösterildiği gibi, Eşzamanlılık Görselleştiricisi de cpu kullanım görünümünde bu belirti ortaya çıkarabilir, burada, birden fazla iş parçacığı varlığına rağmen, uygulama yalnızca bir mantıksal çekirdek tüketir.

Daha fazla bilgi için, "Sorun bölümü ile başlatın" MSDN Dergisi makale [Konu Performansı - Kaynak Çekişme Concurrency Profilleme Visual Studio 2010](https://msdn.microsoft.com/magazine/ff714587.aspx)bakın.

![Kilit Çekişmesi](../profiling/media/lockcontention_2.png "LockContention_2")

## <a name="uneven-workload-distribution"></a>Düzensiz iş yükü dağılımı

![Düzensiz iş yükü](../profiling/media/unevenworkload_1.png "UnevenWorkLoad_1")

Bir uygulamada birkaç paralel iş parçacığı arasında düzensiz bir çalışma dağılımı oluştuğunda, önceki resimde gösterildiği gibi, her iş parçacığı çalışmasını tamamlarken tipik bir merdiven adımı deseni görüntülenir. Eşzamanlı Görselleştirici en sık her eşzamanlı iş parçacığı için çok yakın başlangıç zamanlarını gösterir. Ancak, bu iş parçacıkları genellikle aynı anda sona ermek yerine düzensiz bir şekilde sona erer. Bu desen, bir grup paralel iş parçacığı arasında düzensiz bir çalışma dağılımını gösterir ve bu da performansın düşmesine neden olabilir. Böyle bir soruna en iyi yaklaşım, çalışmanın paralel iş parçacıkları arasında bölündüğü algoritmayı yeniden değerlendirmektir.

Aşağıdaki resimde gösterildiği gibi, Eşzamanlılık Görselleştiricisi de CPU Kullanımı Görünümü'nde bu belirti ortaya çıkarabilir CPU kullanımı nda kademeli bir adım aşağı olarak.

![Düzensiz iş yükü](../profiling/media/unevenworkload_2.png "UnevenWorkload_2")

## <a name="oversubscription"></a>Oversubscription

![Oversubscription](../profiling/media/oversubscription.png "Oversubscription")

Aşırı abonelik durumunda, bir işlemdeki etkin iş parçacığı sayısı sistemdeki kullanılabilir mantıksal çekirdek sayısından daha büyüktür. Önceki resimde, tüm etkin iş parçacıklarında önemli preemption bantlama ile oversubscription sonuçlarını gösterir. Buna ek olarak, gösterge preemption (bu örnekte yüzde 84) harcanan zaman büyük bir yüzdesi gösterir. Bu, işlemin sistemden mantıksal çekirdek sayısından daha fazla eşzamanlı iş parçacığı yürütmesini istediğini gösterebilir. Ancak, bu, sistemdeki diğer işlemlerin bu işlem için kullanılabilir olduğu varsayılan kaynakları kullandığını da gösterebilir.

Bu sorunu değerlendirirken aşağıdakileri göz önünde bulundurmanız gerekir:

- Genel sistem aşırı abone olabilir. Sistemdeki diğer işlemlerin iş parçacığınızı önceden gözden geçirebileceğini göz önünde bulundurun. İş parçacıkları görünümünde bir önalım kesimi üzerinde duraklattığınızda, bir araç ucu iş parçacığı ve iş parçacığı preempted işlemi tanımlar. Bu işlem, işlemin izinden alındı tüm zaman boyunca yürütülen mutlaka biri değildir, ancak işleminize karşı preemption basınç oluşturulan hakkında bir ipucu sağlar.

- İşleminizin bu çalışma aşamasında yürütülmesi için uygun iş parçacığı sayısını nasıl belirlediğini değerlendirin. İşleminiz doğrudan etkin paralel iş parçacığı sayısını hesaplarsa, bu algoritmayı sistemdeki kullanılabilir mantıksal çekirdek sayısını daha iyi hesaba katmak için değiştirmeyi düşünün. Eşzamanlılık Çalışma Zamanı, Görev Paralel Kitaplığı veya PLINQ kullanıyorsanız, bu kitaplıklar iş parçacığı sayısını hesaplama işini gerçekleştirir.

## <a name="inefficient-io"></a>Verimsiz G/Ç

![Verimsiz Ben&#47;O](../profiling/media/inefficient_io.png "Inefficient_IO")

G/Ç'nin aşırı kullanımı veya kötüye kullanımı, uygulamalardaki verimsizliklerin yaygın bir nedenidir. Önceki çizimi göz önünde bulundurun. Görünür Zaman Çizelgesi Profili, görünür iş parçacığı süresinin yüzde 44'ünün G/Ç tarafından tüketildiğini gösterir. Zaman çizelgesi, profilli uygulamanın Sık sık G/Ç tarafından engellendiğini gösteren büyük miktarda G/Ç gösterir. G/Ç türleri ve programınızın engellendiği yerle ilgili ayrıntıları görmek için sorunlu bölgeleri yakınlaştırın, Görünür Zaman Çizelgesi Profilini inceleyin ve ardından geçerli arama yığınlarını görmek için belirli bir G/Ç bloğunu tıklatın.

## <a name="lock-convoys"></a>Konvoyları kilitleyin

![Konvoyları kilitleyin](../profiling/media/lock_convoys.png "Lock_Convoys")

Kilit konvoyları, uygulama ilk gelen, ilk hizmet sırasına göre kilitler aldığında ve kilitteki varış oranı edinme oranından daha yüksek olduğunda oluşur. Bu iki koşulun birleşimi, kilidin yedeklemeye başlaması için isteklere neden olur. Bu sorunla mücadele etmenin bir yolu, "haksız" kilitleri veya kilitsiz durumlarda bunları bulmak için ilk iş parçacığına erişim sağlayan kilitleri kullanmaktır. Önceki resimde bu konvoy davranışı gösterilmektedir. Sorunu çözmek için, eşitleme nesneleri için çekişmeyi azaltmayı deneyin ve haksız kilitleri kullanmayı deneyin.

## <a name="see-also"></a>Ayrıca bkz.

[İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)