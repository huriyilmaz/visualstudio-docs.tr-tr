---
title: Çok iş parçacıklı uygulamalarda hata ayıklama | Microsoft Docs
description: Visual Studio 'da çok iş parçacıklı uygulamalarda hata ayıklayın. Çoklu iş parçacıklı uygulamalarda hata ayıklama hakkında araçları ve diğer makaleleri gözden geçirin.
ms.custom: SEO-VS-2020, seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fed6580219964ab71f5a5010060c1af193375df
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727144"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Visual Studio 'da çok iş parçacıklı uygulamalarda hata ayıklama
İş parçacığı, işletim sisteminin işlemci zamanı verdiği bir yönergeler dizisidir. İşletim sisteminde çalışan her işlem en az bir iş parçacığından oluşur. Birden fazla iş parçacığına sahip işlemlere çok iş parçacığı denir.

Birden çok işlemcili bilgisayarlar, çok çekirdekli işlemciler veya hiper iş parçacığı oluşturma işlemlerinde birkaç eşzamanlı iş parçacığı çalıştırılabilir. Birçok iş parçacığı kullanan paralel işleme, program performansını önemli ölçüde iyileştirebilir, ancak birçok iş parçacığını izlemekte olduğunuz için hata ayıklamayı daha da zor hale gelebilir.

Çoklu iş parçacığı oluşturma, olası hataların yeni türlerini ortaya çıkarabilir. Örneğin, iki veya daha fazla iş parçacığının aynı kaynağa erişmesi gerekebilir, ancak aynı anda yalnızca bir iş parçacığı kaynağa güvenli bir şekilde erişebilir. Belirli bir zamanda kaynağa yalnızca bir iş parçacığının eriştiğinden emin olmak için bazı karşılıklı dışlama biçimi gereklidir. Karşılıklı dışlama yanlış uygulanırsa, iş parçacığı yürütülemeyecek bir *kilitlenme* koşulu oluşturabilir. Kilitlenmeler genellikle hata ayıklamada zor bir sorundur.

## <a name="tools-for-debugging-multithreaded-apps"></a>Çok iş parçacıklı uygulamalarda hata ayıklama araçları

Visual Studio, çok iş parçacıklı uygulamalarda hata ayıklamada kullanmak için farklı araçlar sağlar.

- İş parçacıkları için, hata ayıklama iş parçacıklarının birincil araçları **Iş parçacıkları** penceresidir, kaynak pencerelerin iş parçacığı Işaretçileri, **Paralel Yığınlar** penceresi, **paralel Izleme** penceresi ve **hata ayıklama konumu** araç çubuğudur. **Iş parçacıkları** penceresi ve **hata ayıklama konumu** araç çubuğu hakkında bilgi edinmek Için bkz. [izlenecek yol: Iş parçacıkları penceresini kullanarak hata ayıklama](../debugger/how-to-use-the-threads-window.md) **Paralel yığınları** ve **paralel izleme** pencerelerini nasıl kullanacağınızı öğrenmek için bkz. çok [iş parçacıklı bir uygulamada hata ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md). Her iki konuda de iş parçacığı işaretlerinin nasıl kullanılacağı gösterilmektedir.

- [Görev paralel kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) veya [Eşzamanlılık çalışma zamanı](/cpp/parallel/concrt/concurrency-runtime/)kullanan kod için, hata ayıklama Için birincil Araçlar **Paralel Yığınlar** penceresi, **paralel izleme** penceresi ve ayrıca JavaScript 'i de destekleyen **Görevler** penceresidir. Başlamak için bkz. [Izlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md) ve [izlenecek yol: C++ amp uygulamasında hata ayıklama](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application).

- GPU 'daki iş parçacıkları hata ayıklaması için, birincil araç **GPU Iş parçacıkları** penceresidir. Bkz. [nasıl yapılır: GPU Iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-gpu-threads-window.md).

- İşlemler için, birincil Araçlar **Işleme İliştir** iletişim kutusu, **Işlemler** penceresi ve **hata ayıklama konumu** araç çubuğudur.

Visual Studio, çok iş parçacıklı uygulamalarda hata ayıklarken yararlı olabilecek güçlü kesme noktaları ve izleme noktaları da sağlar. Kesme noktalarını bağımsız iş parçacıklarında yerleştirmek için kesme noktası koşullarını ve filtrelerini kullanın. İzleme noktaları, kilitlenme gibi sorunları incelemek için, çalışmanız olmadan programınızın yürütülmesini izlemenizi sağlar. Daha fazla bilgi için bkz. [kesme noktası eylemleri ve izleme noktaları](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Kullanıcı arabirimine sahip çok iş parçacıklı bir uygulamada hata ayıklamak özellikle zor olabilir. Uygulamayı ikinci bir bilgisayarda çalıştırmayı ve uzaktan hata ayıklamayı kullanmayı düşünebilirsiniz. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

## <a name="articles-about-debugging-multithreaded-apps"></a>Çok iş parçacıklı uygulamalarda hata ayıklama hakkında makaleler

 [Çok iş parçacıklı bir uygulamada hata ayıklamaya başlayın](../debugger/get-started-debugging-multithreaded-apps.md)

İş parçacığı hata ayıklama özelliklerinin bir turu, **Paralel Yığınlar** penceresindeki özellikleri ve **paralel izleme** penceresini vurgularken.

 [İş parçacıkları ve işlemlerde hata ayıklama araçları](../debugger/debug-threads-and-processes.md)

İş parçacıkları ve süreçlerinde hata ayıklama araçlarının özelliklerini listeler.

 [Birden çok işlemde hata ayıklama](../debugger/debug-multiple-processes.md)

Birden çok işlemde hata ayıklama işleminin nasıl yapılacağını açıklar.

 [Izlenecek yol: Iş parçacıkları penceresini kullanarak hata ayıklayın](../debugger/how-to-use-the-threads-window.md).

**Iş parçacıkları** penceresi ve **hata ayıklama konumu** araç çubuğunun nasıl kullanılacağını gösteren izlenecek yol.

 [İzlenecek yol: Paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)

**Paralel Yığınlar** ve **Görevler** pencerelerinin nasıl kullanılacağını gösteren izlenecek yol.

 [Nasıl yapılır: Hata ayıklarken başka bir iş parçacığına geçme](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Hata ayıklama bağlamını başka bir iş parçacığına geçirmek için çeşitli yollar.

 [Nasıl yapılır: İş parçacıklarını bayrakla işaretleme ve işareti geri alma](../debugger/how-to-flag-and-unflag-threads.md)

Hata ayıklama sırasında özel dikkat sağlamak istediğiniz iş parçacıklarını işaretleyin veya bayrak ekleyin.

 [Nasıl yapılır: yüksek performanslı kümede hata ayıklama](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Yüksek performanslı kümede çalışan bir uygulamada hata ayıklama teknikleri.

 [Yerel kod iş parçacıklarında hata ayıklama ipuçları](../debugger/tips-for-debugging-threads-in-native-code.md)

Yerel iş parçacıkları için hata ayıklama yararlı olabilecek basit teknikler.

 [Nasıl yapılır: yerel kodda iş parçacığı adı ayarlama](../debugger/how-to-set-a-thread-name-in-native-code.md)

İş parçacığına, **Iş parçacıkları** penceresinde görüntülediğiniz bir ad verin.

 [Nasıl yapılır: yönetilen kodda iş parçacığı adı ayarlama](../debugger/how-to-set-a-thread-name-in-managed-code.md)

İş parçacığına, **Iş parçacıkları** penceresinde görüntülediğiniz bir ad verin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kesme noktalarını kullanma](../debugger/using-breakpoints.md)
- [İş Parçacığı Oluşturma](/dotnet/standard/threading/index)
- [Bileşenlerde çoklu iş parçacığı](/previous-versions/3es4b6yy(v=vs.140))
- [Eski kod için çoklu iş parçacığı desteği](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [İş parçacıklarında ve işlemlerde hata ayıklama](../debugger/debug-threads-and-processes.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)