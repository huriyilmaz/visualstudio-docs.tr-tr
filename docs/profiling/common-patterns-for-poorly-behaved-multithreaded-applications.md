---
title: Kötü iş parçacıklı uygulamalar için ortak desenler
description: Eşzamanlılık görselleştiricisi, çok iş parçacıklı uygulamalar için grafikler ve bir dizi yaygın olarak davranların bir galerisini sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e645af13f52f64664cb4d9539dcd9c3769d9dd08
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039715"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Hatalı davranan çok iş parçacıklı uygulamalar için ortak desenler

Eşzamanlılık görselleştiricisi, geliştiricilerin çok iş parçacıklı bir uygulamanın davranışını görselleştirmesine yardımcı olur. Bu araç, çok iş parçacıklı uygulamalar için hatalı davranan yaygın desenler galerisini içerir. Galeri, araçla birlikte sunulan tipik ve tanınabilir görsel desenleri, her bir desen tarafından temsil edilen davranışın açıklaması, bu davranışın büyük bir sonucu ve bunu çözmek için en yaygın yaklaşım içerir.

## <a name="lock-contention-and-serialized-execution"></a>Kilit çakışması ve serileştirilmiş yürütme

![Seri hale getirilmiş yürütmeye neden olan kilit çakışması](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")

Bazı durumlarda, çok sayıda iş parçacığı olmasına rağmen bilgisayar yeterli sayıda mantıksal çekirdeğe sahip olsa bile, paralel bir uygulama stubbornly bir şekilde yürütülmeye devam eder. İlk belirti, büyük olasılıkla bir seri uygulamadan biraz daha yavaş olan çok iş parçacıklı performanstır. Iş parçacıkları görünümünde paralel olarak çalışan birden çok iş parçacığı görmezsiniz; Bunun yerine, herhangi bir zamanda yalnızca bir iş parçacığının yürütüğünü görürsünüz. Bu noktada, bir iş parçacığında bir eşitleme segmentine tıklarsanız, engellenen iş parçacığı (çağrı yığınını engelleme) ve engelleme koşulunu kaldıran iş parçacığı (çağrı yığınının engellemesini kaldırma) için çağrı yığınını görebilirsiniz. Ayrıca, analiz ettiğiniz işlemde engellemeyi kaldırma çağrı yığını gerçekleşirse, bir Thread-Ready Bağlayıcısı görüntülenir. Bu noktadan sonra, bir serileştirme nedenini daha da araştırmak için engelleme ve çağrı yığınlarını engellemeyi kaldırma ' dan kodunuza gidebilirsiniz.

Aşağıdaki çizimde gösterildiği gibi eşzamanlılık görselleştiricisi de bu belirtiyi CPU kullanımı görünümünde kullanıma sunabileceğinden, burada birden çok iş parçacığı varlığına rağmen uygulama yalnızca bir mantıksal çekirdek tüketir.

daha fazla bilgi için, Visual Studio 2010 ' de bkz. MSDN Magazine article [iş parçacığı performansı-kaynak çekişmesini oluşturma](/archive/msdn-magazine/2010/june/msdn-magazine-thread-performance-resource-contention-concurrency-profiling-in-visual-studio-2010)konusunun "sorun ile başlayın".

![Kilit çakışması](../profiling/media/lockcontention_2.png "LockContention_2")

## <a name="uneven-workload-distribution"></a>Düzensiz iş yükü dağıtımı

![Eşzamanlılık görselleştiricisi içindeki paralel iş parçacıkları için bir iş yükü grafiğinin ekran görüntüsü. İş parçacıkları, bir merdiven adımı deseninin gösterildiği farklı zamanlarda sona erdir.](../profiling/media/unevenworkload_1.png)

Bir uygulamadaki çeşitli paralel iş parçacıkları arasında düzensiz bir iş dağıtımı gerçekleştiğinde, önceki çizimde gösterildiği gibi, her bir iş parçacığının çalışmasını tamamlarsa, tipik bir merdiven adımı görüntülenir. Eşzamanlılık görselleştiricisi genellikle her bir eşzamanlı iş parçacığı için çok yakın başlangıç zamanlarını gösterir. Ancak, bu iş parçacıkları genellikle aynı anda sona ermek yerine düzensiz bir şekilde sona eriyor. Bu model, bir dizi paralel iş parçacığı arasında düzensiz bir şekilde bir dağıtım olduğunu gösterir. Bu, performansın düşmesine neden olabilir. Bu tür bir soruna en iyi yaklaşım, çalışmanın paralel iş parçacıkları arasında bölündüğü algoritmayı yeniden değerlendirmelidir.

Aşağıdaki çizimde gösterildiği gibi eşzamanlılık görselleştiricisi ayrıca CPU kullanımı görünümünde bu belirtiyi CPU kullanımında aşamalı bir adım olarak kullanıma sunabilir.

![Eşzamanlılık görselleştiricisi içindeki CPU kullanımı görünümünün ekran görüntüsü, CPU kullanımı grafiğinin sonunda bir merdiven adımı deseninin gösterilmesi.](../profiling/media/unevenworkload_2.png)

## <a name="oversubscription"></a>Aşırı abonelik

![Eşzamanlılık görselleştiricisi içindeki tüm etkin iş parçacıkları için bir iş yükü grafiğinin ekran görüntüsü. Bir gösterge, yürütme ve önalım ile harcanan süreyi gösterir.](../profiling/media/oversubscription.png)

Fazla abonelik durumunda, bir işlemdeki etkin iş parçacıklarının sayısı sistemdeki kullanılabilir mantıksal çekirdek sayısından daha büyük. Önceki çizimde, tüm etkin iş parçacıklarında önemli önalım bantlarla fazla abonelik sonuçları gösterilmektedir. Ayrıca, göstergede büyük bir yüzde önalım (Bu örnekte yüzde 84) harcandığını gösterir. Bu, işlemin sisteme, mantıksal çekirdek sayısından daha fazla eşzamanlı iş parçacığı yürütmesini isteyeceğini gösteriyor olabilir. Bununla birlikte, bu durum sistemdeki diğer işlemlerin bu işlem için kullanılabilir kabul edilen kaynakları kullandığını da belirtebilir.

Bu sorunu değerlendirirken şunları göz önünde bulundurmanız gerekir:

- Genel sistem aşırı abone olabilir. Sistem üzerindeki diğer işlemlerin iş parçacıklarınız öncelik verme olabileceğini göz önünde bulundurun. İş parçacıkları görünümünde bir önalım segmentinin üzerinde durakladığınızda, bir araç ipucu iş parçacığını ve iş parçacığını yok eden işlemi belirler. Bu işlem, işleminiz önceden geçersiz hale gelen bir süre boyunca yürütülene gerek kalmaz, ancak işlem için önalım basıncı oluşturma hakkında bir ipucu sağlar.

- İşleminizin bu iş aşamasında yürütülmek üzere uygun iş parçacığı sayısını nasıl belirlediğini değerlendirin. İşleminiz etkin paralel iş parçacığı sayısını doğrudan hesapladığında, sistemdeki kullanılabilir mantıksal çekirdek sayısı için bu algoritmayı daha iyi hesaba göre değiştirmeyi göz önünde bulundurun. Eşzamanlılık Çalışma Zamanı, görev paralel kitaplığı veya PLıNQ ' i kullanırsanız, bu kitaplıklar iş parçacığı sayısını hesaplama işini gerçekleştirir.

## <a name="inefficient-io"></a>Verimsiz g/ç

![Verimsiz&#47;O](../profiling/media/inefficient_io.png "Inefficient_IO")

G/ç 'nin aşırı kullanım veya kötüye kullanımı, verimsizlikleri uygulamalarında yaygın bir nedendir. Önceki çizimi göz önünde bulundurun. Görünür zaman çizelgesi profili, görünen iş parçacığı süresinin yüzde 44 ' unun g/ç tarafından tüketildiğini gösterir. Zaman çizelgesi, profili oluşturulmuş uygulamanın sıklıkla g/ç tarafından engellendiğini gösteren büyük miktarda g/ç 'yi gösterir. Bir g/ç türü ve programınızın engellediği yer hakkındaki ayrıntıları görmek için sorunlu bölgelere yakınlaştırın, görünür zaman çizelgesi profilini inceleyin ve ardından geçerli çağrı yığınlarını görmek için belirli bir g/ç bloğuna tıklayın.

## <a name="lock-convoys"></a>Convoys 'i kilitle

![Convoys 'i kilitle](../profiling/media/lock_convoys.png "Lock_Convoys")

Kilit convoys, uygulama ilk ve ilk kez sunulan bir siparişte kilit elde etdiğinde ve kilit sırasındaki varış hızı, Alım hızından yüksekse oluşur. Bu iki koşulun birleşimi kilit isteklerinin yedeklemeye başlatılmasına neden olur. Bu sorunu çözmek için bir yol, "haksız" kilitleri veya kilitlenmemiş durumlarda ilk iş parçacığına erişim veren kilitleri kullanmaktır. Önceki çizimde bu konvoy davranışı gösterilmektedir. Sorunu çözmek için eşitleme nesnelerinin çekişmesini azaltmayı deneyin ve dengeli olmayan kilitleri kullanmayı deneyin.

## <a name="see-also"></a>Ayrıca bkz.

[İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)