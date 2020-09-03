---
title: Çok İş Parçacıklı Uygulamalarda Hata Ayıklama
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cb43c9a32f3dfd0a6383d466f7cd283acf0ab3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691274"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Visual Studio'da Çok İş Parçacıklı Uygulamalarda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İş parçacığı, işletim sisteminin işlemci zamanını ayıran yönergelerin bir dizisidir. İşletim sisteminde çalışan her işlem en az bir iş parçacığından oluşur. Birden fazla iş parçacığına sahip işlemlere çok iş parçacığı denir.

 Birden çok işlemcili bilgisayarlar, çok çekirdekli işlemciler veya hiper iş parçacığı oluşturma işlemlerinde aynı anda birden çok iş parçacığı çalıştırılabilir. Birden çok iş parçacığının paralel işlemesi program performansını önemli ölçüde iyileştirebilir, ancak birden çok iş parçacığını izleme gereksinimini sunduğundan hata ayıklamayı daha da zor hale getirir.

 Ayrıca, çoklu iş parçacığı bazı olası hata türlerini tanıtır. Genellikle, örneğin, iki veya daha fazla iş parçacığının aynı kaynağa erişmesi gerekir, ancak aynı anda yalnızca bir iş parçacığı güvenli bir şekilde kaynağa erişebilir. Tek seferde kaynağa yalnızca bir iş parçacığının eriştiğinden emin olmak için bazı karşılıklı dışlama biçimi gereklidir. Karşılıklı dışlama yanlış gerçekleştirilirse, iş parçacığının yürütülemediği bir *kilitlenme* koşulu oluşturabilir. Kilitlenmeler, hata ayıklama için özellikle bir sorun olabilir.

 Visual Studio bir **Iş parçacığı** penceresi, bir GPU iş parçacıkları penceresi, paralel izleme penceresi ve çok iş parçacıklı hata ayıklamayı daha kolay hale getirir. İş parçacığı oluşturma özellikleri hakkında bilgi almanın en iyi yolu, izlenecek yolları kullanmaktır. [Izlenecek yol: çok Iş parçacıklı uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-multithreaded-application.md) ve [izlenecek yol: C++ amp uygulamasında hata ayıklama](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 Visual Studio, çok iş parçacıklı uygulamalarda hata ayıklarken yararlı olabilecek güçlü kesme noktaları ve izleme noktaları da sağlar. Kesme noktalarını her bir iş parçacığına yerleştirmek için kesme noktası filtrelerini kullanabilirsiniz. Bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md)

 Kullanıcı arabirimine sahip çok iş parçacıklı bir uygulamada hata ayıklamak özellikle zor olabilir. Bu durumda, uygulamayı ikinci bir bilgisayarda çalıştırmayı ve uzaktan hata ayıklamayı kullanmayı düşünebilirsiniz. Bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>Bu Bölümde
 [Hata ayıklama Iş parçacıkları ve süreçler](../debugger/debug-threads-and-processes.md) İş parçacıklarının ve işlemlerin hata ayıklamasına ilişkin temel bilgileri açıklar.

 [Birden çok Işlemde hata ayıklama](../debugger/debug-multiple-processes.md) Birden çok işlemde hata ayıklama işleminin nasıl yapılacağını açıklar.

 [Nasıl yapılır: Iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-threads-window.md) **Iş parçacıkları** penceresi ile iş parçacıkları hata ayıklama için yararlı yordamlar.

 [Nasıl yapılır: hata ayıklarken başka bir Iş parçacığına geçme](../debugger/how-to-switch-to-another-thread-while-debugging.md) Hata ayıklama bağlamını başka bir iş parçacığına geçirmek için üç yol.

 [Nasıl yapılır: Iş parçacıklarını işaretleme ve Işaretini kaldırma](../debugger/how-to-flag-and-unflag-threads.md) Hata ayıklama sırasında özel dikkat sağlamak istediğiniz iş parçacıklarını işaretleyin veya bayrak ekleyin.

 [Nasıl yapılır: yerel kodda Iş parçacığı adı ayarlama](../debugger/how-to-set-a-thread-name-in-native-code.md) İş parçacığına, **Iş parçacıkları** penceresinde görüntülediğiniz bir ad verin.

 [Nasıl yapılır: yönetilen kodda Iş parçacığı adı ayarlama](../debugger/how-to-set-a-thread-name-in-managed-code.md) İş parçacığına, **Iş parçacıkları** penceresinde görüntülediğiniz bir ad verin.

 [Izlenecek yol: çok Iş parçacıklı bir uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-multithreaded-application.md).
İş parçacığı hata ayıklama özelliklerinin Kılavuzlu turu, özelliklerin nasıl yapılacağını vurgulaması [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] .

 [Nasıl yapılır: yüksek performanslı kümede hata ayıklama](../debugger/how-to-debug-on-a-high-performance-cluster.md) Yüksek performanslı kümede çalışan bir uygulamada hata ayıklama teknikleri.

 [Yerel koddaki Iş parçacıkları hata ayıklama ipuçları](../debugger/tips-for-debugging-threads-in-native-code.md) Yerel iş parçacıkları için hata ayıklama yararlı olabilecek basit teknikler.

 [Görevler penceresini kullanma](../debugger/using-the-tasks-window.md) Tüm yönetilen veya yerel görev nesnelerinin durumlarını ve diğer yararlı bilgilerini içeren bir listesini gösterir.

 [Paralel Yığınlar penceresini kullanma](../debugger/using-the-parallel-stacks-window.md) Tek bir görünümdeki birden çok iş parçacığının (veya görev) çağrı yığınlarını gösterir ve ayrıca iş parçacıkları (veya görevler) arasında ortak olan yığın segmentlerini birleştirir.

 [Izlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md) Paralel görevler ve Paralel Yığınlar pencerelerinin nasıl kullanılacağını gösteren izlenecek yol.

 [Nasıl yapılır: paralel Izleme penceresini kullanma](../debugger/how-to-use-the-parallel-watch-window.md) Birden çok iş parçacığı üzerinde değerleri ve ifadeleri inceleyin.

 [Nasıl yapılır: GPU Iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-gpu-threads-window.md) Hata ayıklama sırasında GPU üzerinde çalışan iş parçacıklarını inceleyin ve bunlarla çalışın.

## <a name="related-sections"></a>İlgili Bölümler

[Kesme Noktalarını Kullanma](../debugger/using-breakpoints.md)
- Tek bir iş parçacığına bir kesme noktası yerleştirmek istediğinizde kesme noktası filtrelerini kullanın.

- İzleme noktaları, programınızı koparmadan yürütmeyi izlemenizi sağlar. Bu, kilitlenmeler gibi sorunları yeniden birleştirme için yararlı olabilir.

  [Iş parçacığı](https://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) oluşturma [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Örnek kod dahil, programlamada iş parçacığı kavramları.

  [Bileşenlerde çoklu Iş parçacığı](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) Bileşenlerinde çoklu iş parçacığı kullanımı [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

  [Eski kod Için çoklu Iş parçacığı desteği (Visual C++)](https://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) MFC kullanarak C++ programcıları için iş parçacığı oluşturma kavramları ve örnek kod.

## <a name="see-also"></a>Ayrıca Bkz.
 [Hata ayıklama Iş parçacıkları ve süreçler](../debugger/debug-threads-and-processes.md) [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
