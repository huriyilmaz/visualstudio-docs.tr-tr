---
title: Çok iş parçacıklı uygulamalarda hata | Microsoft Docs
description: Çok iş parçacıklı uygulamalarda hata ayıklama Visual Studio. Çok iş parçacıklı uygulamalarda hata ayıklama hakkında araçları ve diğer makaleleri gözden geçirme.
ms.custom: SEO-VS-2020
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6a3c3b20117061f06d7f5e65e1cd9ec4fbd0b814
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105407"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Çok iş parçacıklı uygulamalarda hata ayıklama Visual Studio
İş parçacığı, işletim sisteminin işlemciye zaman izni vermek için bir yönergeler dizisidir. İşletim sisteminde çalışan her işlem en az bir iş parçacığına sahiptir. Birden fazla iş parçacığına sahip işlemler çok iş parçacıklı olarak çağrılır.

Birden çok işlemciye, çok çekirdekli işlemcilere veya hiper iş parçacığı işlemeye sahip bilgisayarlar birkaç eşzamanlı iş parçacığı çalıştırabilirsiniz. Birçok iş parçacığını kullanarak paralel işleme program performansını önemli ölçüde geliştirebilir, ancak birçok iş parçacığını takip ediyorsanız hata ayıklamayı da zorlaştırabilirsiniz.

Çoklu iş parçacığı, yeni türlerde olası hatalara neden olabilir. Örneğin, iki veya daha fazla iş parçacığının aynı kaynağa erişmesi gerekir, ancak aynı anda yalnızca bir iş parçacığı kaynağa güvenli bir şekilde erişebilirsiniz. Kaynağa herhangi bir anda yalnızca bir iş parçacığının erişirken emin olmak için karşılıklı dışlamanın bir biçimi gereklidir. Karşılıklı dışlama yanlış uygulanırsa, herhangi bir iş *parçacığının yürütülecek* bir kilitlenme koşulu oluşturabilir. Kilitlenmeler genellikle hata ayıklamak için zor bir sorundur.

## <a name="tools-for-debugging-multithreaded-apps"></a>Çok iş parçacıklı uygulamalarda hata ayıklama araçları

Visual Studio çok iş parçacıklı uygulamalarda hata ayıklamada kullanmak için farklı araçlar sağlar.

- İş parçacıklarında hata ayıklama için birincil  araçlar İş Parçacıkları penceresi, kaynak pencerelerde iş parçacığı işaretçileri, **Paralel** Yığınlar penceresi, **Paralel** İzleme penceresi ve Hata Ayıklama Konumu araç çubuğu'larıdır.  İş Parçacıkları penceresi ve **Hata Ayıklama** Konumu araç çubuğu **hakkında bilgi** edinmek için bkz. Kılavuz: İş Parçacıkları penceresini kullanarak [hata ayıklama.](../debugger/how-to-use-the-threads-window.md) Paralel Yığınlar ve Paralel İzleme  **pencerelerini** kullanmayı öğrenmek için bkz. Kullanmaya başlayın uygulamanın hata [ayıklamasını düzeltme.](../debugger/get-started-debugging-multithreaded-apps.md) Her iki konu da iş parçacığı işaretçilerini kullanmayı gösterir.

- Görev Paralel  Kitaplığı [(TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) veya [Eşzamanlılık Çalışma Zamanı](/cpp/parallel/concrt/concurrency-runtime/)kullanan kodlar için, hata ayıklama  için birincil araçlar  Paralel Yığınlar penceresi, Paralel İzleme penceresi ve JavaScript'i de destekleyen Görevler penceresidir. Çalışmaya başlama için bkz. [Adım adım: Paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md) ve Adım adım kılavuz: Bir uygulamanın C++ AMP [ayıklama.](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)

- GPU'da iş parçacıklarında hata ayıklama için birincil araç GPU İş **Parçacıkları penceresidir.** Bkz. [Nasıl: GPU İş Parçacıkları penceresini kullanma.](../debugger/how-to-use-the-gpu-threads-window.md)

- İşlemler için birincil araçlar İşleme Ekle **iletişim** kutusu, **İşlemler penceresi ve** Hata Ayıklama Konumu araç **çubuğu'larıdır.**

Visual Studio, çok iş parçacıklı uygulamalarda hata ayıklarken yararlı olan güçlü kesme noktaları ve izleme noktaları da sağlar. Kesme noktaları tek tek iş parçacıklarına yer etmek için kesme noktası koşullarını ve filtrelerini kullanın. İzleme noktaları, kilitlenmeler gibi sorunları çalışmak için programınızı kesmeden yürütmeyi izlemenizi sağlar. Daha fazla bilgi için [bkz. Kesme noktası eylemleri ve izleme noktaları.](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)

Kullanıcı arabirimine sahip çok iş parçacıklı bir uygulamada hata ayıklamak özellikle zor olabilir. Uygulamayı ikinci bir bilgisayarda çalıştırmayı ve uzaktan hata ayıklamayı kullanmayı düşünebilirsiniz. Daha fazla bilgi için [bkz. Uzaktan hata ayıklama.](../debugger/remote-debugging.md)

## <a name="articles-about-debugging-multithreaded-apps"></a>Çok iş parçacıklı uygulamalarda hata ayıklama hakkında makaleler

 [Kullanmaya başlayın iş parçacıklı uygulamada hata ayıklama](../debugger/get-started-debugging-multithreaded-apps.md)

Paralel Yığınlar penceresindeki ve Paralel İzleme penceresindeki özellikleri vurgulayan iş parçacığı **hata** ayıklama **özellikleri turu.**

 [İş parçacıklarında ve işlemlerde hata ayıklama araçları](../debugger/debug-threads-and-processes.md)

İş parçacıklarında ve işlemlerde hata ayıklamaya yardımcı olan araçların özelliklerini listeler.

 [Birden çok işlemde hata ayıklama](../debugger/debug-multiple-processes.md)

Birden çok işlemde hata ayıklamayı açıklar.

 [Adım adım kılavuz: İş Parçacıkları penceresini kullanarak hata ayıklama.](../debugger/how-to-use-the-threads-window.md)

İş Parçacıkları penceresinin ve Hata Ayıklama Konumu **araç** çubuğunun **kullanımını gösteren izlenecek** yol.

 [İzlenecek yol: Paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)

Paralel Yığınlar ve Görevler pencerelerini **kullanmayı gösteren** **izlenecek yol.**

 [Nasıl yapılır: Hata ayıklarken başka bir iş parçacığına geçme](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Hata ayıklama bağlamını başka bir iş parçacığına değiştirmenin çeşitli yolları.

 [Nasıl yapılır: İş parçacıklarını bayrakla işaretleme ve işareti geri alma](../debugger/how-to-flag-and-unflag-threads.md)

Hata ayıklama sırasında özellikle dikkat etmek istediğiniz iş parçacıklarını işaretleme veya işaretleme.

 [Nasıl yapılanlar: Yüksek performanslı kümede hata ayıklama](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Yüksek performanslı bir kümede çalışan bir uygulamada hata ayıklama teknikleri.

 [Yerel kod iş parçacıklarında hata ayıklama ipuçları](../debugger/tips-for-debugging-threads-in-native-code.md)

Yerel iş parçacıklarında hata ayıklamak için kullanışlı olan basit teknikler.

 [Nasıl ayarlanır: Yerel kodda iş parçacığı adı ayarlama](../debugger/how-to-set-a-thread-name-in-native-code.md)

İş parçacığınıza İş Parçacıkları penceresinde görüntüley istediğiniz **bir ad** girin.

 [Nasıl ayarlanır: Yönetilen kodda iş parçacığı adı ayarlama](../debugger/how-to-set-a-thread-name-in-managed-code.md)

İş parçacığınıza İş Parçacıkları penceresinde görüntüley istediğiniz **bir ad** girin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kesme noktalarını kullanma](../debugger/using-breakpoints.md)
- [İş Parçacığı Oluşturma](/dotnet/standard/threading/index)
- [Bileşenlerde çoklu iş parçacığı](/previous-versions/3es4b6yy(v=vs.140))
- [Eski kod için çoklu iş parçacığı desteği](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [İş parçacıklarında ve işlemlerde hata ayıklama](../debugger/debug-threads-and-processes.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)