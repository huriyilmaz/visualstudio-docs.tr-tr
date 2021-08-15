---
title: Görevler penceresini kullanma | Microsoft Docs
description: Görevler eşzamanlı olarak çalışabilen zaman uyumsuz işlemlerdir. Aynı iş parçacığında birden çok görev çalıştırılabilir. Görevi ve WinJS. Promise nesne bilgilerini görüntülemek için görevleri kullanın.
ms.custom: SEO-VS-2020
ms.date: 03/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: cfbb3faef7fa097114f66eafe8ea224c04d431b5019516f67e03bfa3947ad5c0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419266"
---
# <a name="using-the-tasks-window-c-visual-basic-c"></a>Görevler penceresini kullanma (C#, Visual Basic, C++)

**Görevler** penceresi, **iş parçacıkları** penceresine benzer, ancak <xref:System.Threading.Tasks.Task?displayProperty=fullName> her iş parçacığı yerine, [task_handle](/cpp/parallel/concrt/reference/task-group-class)veya [WinJS. Promise](/previous-versions/windows/apps/br211867(v=win.10)) nesneleri hakkında bilgi gösterir. İş parçacıkları gibi görevler, eşzamanlı olarak çalışabilecek zaman uyumsuz işlemleri temsil eder; Ancak, aynı iş parçacığında birden çok görev çalıştırılabilir.

Yönetilen  kodda, nesnelerle çalışırken <xref:System.Threading.Tasks.Task?displayProperty=fullName> veya **await** ve **Async** anahtar sözcükleriyle (VisualBasic içinde **await** ve **Async** ) görevler penceresini kullanabilirsiniz. Yönetilen koddaki görevler hakkında daha fazla bilgi için bkz.  [paralel programlama](/dotnet/standard/parallel-programming/index).

Yerel kodda [görev grupları](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [paralel algoritmalar](/cpp/parallel/concrt/parallel-algorithms), [zaman uyumsuz aracılar](/cpp/parallel/concrt/asynchronous-agents)ve [hafif görevlerle](/cpp/parallel/concrt/task-scheduler-concurrency-runtime)çalışırken **Görevler** penceresini kullanabilirsiniz. Yerel koddaki görevler hakkında daha fazla bilgi için bkz. [Eşzamanlılık çalışma zamanı](/cpp/parallel/concrt/concurrency-runtime).

JavaScript 'te, taahhüt kodu ile çalışırken görevler penceresini kullanabilirsiniz `.then` . Daha fazla bilgi için bkz. [JavaScript 'Te zaman uyumsuz programlama (UWP uygulamaları)](/previous-versions/windows/apps/hh700330(v=win.10)) .

Hata ayıklayıcıya her kesme yaptığınızda **Görevler** penceresini kullanabilirsiniz. **hata ayıkla** menüsünde **Windows** ' a ve ardından **görevler**' e tıklayarak erişebilirsiniz. Aşağıdaki çizimde **Görevler** penceresi varsayılan modunda gösterilmektedir.

![Görevler penceresi](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> Yönetilen kodda, görevin durumu. <xref:System.Threading.Tasks.Task> [oluşturuldu](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus. waitingforactivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>)veya [TaskStatus. waitingtorun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) , yönetilen iş parçacıkları bir uyku veya JOIN durumunda olduğunda **Görevler** penceresinde görüntülenmeyebilir.

## <a name="tasks-column-information"></a>Görevler sütun bilgileri

**Görevler** penceresindeki sütunlar aşağıdaki bilgileri gösterir.

|Sütun adı|Açıklama|
|-----------------|-----------------|
|**Larına**|Hangi görevlerin işaretlenip işaretlenmediğini gösterir ve bir görevi işaretlemenizi veya bayrak kaldırmanızı sağlar.|
|**Simgeler**|Sarı ok geçerli görevi gösterir. Geçerli görev, geçerli iş parçacığında en üstteki görevdir.<br /><br /> Beyaz ok, son görevi, yani hata ayıklayıcı çağrıldığında geçerli olan olanı gösterir.<br /><br /> Duraklat simgesi, Kullanıcı tarafından dondurulmuş olan bir görevi gösterir. Listede sağ tıklayarak bir görevi dondurabilir ve çöz ' ü seçebilirsiniz.|
|**ID**|Görevin sistem tarafından sağlanmış numarası. Yerel kodda, bu görevin adresidir.|
|**Durum**|Görevin geçerli durumu (zamanlanan, etkin, engellenen, kilitlenen, bekleyen veya tamamlanmış). Zamanlanmış bir görev henüz çalıştırılmayan ve bu nedenle çağrı yığınına, atanan iş parçacığına veya ilgili bilgilere sahip değildir.<br /><br /> Etkin bir görev, hata ayıklayıcıda kesmeden önce kodu yürüten bir görevdir.<br /><br /> Bekleyen veya engellenen bir görev, bir olayın bildirilebilmesi, yayınlanacak bir kilit ya da başka bir görevin bitmesi beklediği için engellenmiş bir görevdir.<br /><br /> Kilitlenen bir görev, iş parçacığı başka bir iş parçacığıyla kilitlenmiş bekleyen bir görevdir.<br /><br /> Blok hakkında daha fazla bilgi görmek için, kilitlenen veya bekleyen bir görevin **durum** hücresinin üzerine gelin. **Uyarı:**  **Görevler** penceresi, yalnızca bekleme zinciri çapraz geçişi (WCT) tarafından desteklenen bir eşitleme temel alanı kullanan engellenen bir görev için kilitlenme bildirir. Örneğin, <xref:System.Threading.Tasks.Task> WCT kullanan kilitli olmayan bir nesne için, hata ayıklayıcı **bekleyen kilitli** olarak raporlar. WCT kullanmayan Eşzamanlılık Çalışma Zamanı tarafından yönetilen kilitli olmayan bir görev için, hata ayıklayıcı rapor **bekliyor**. WCT hakkında daha fazla bilgi için bkz. [zincir geçişini bekleme](/windows/desktop/Debug/wait-chain-traversal).|
|**Başlangıç Zamanı**|Görevin etkin hale geldiğinden geçen süre.|
|**Süre**|Görevin etkin olduğu saniye sayısı.|
|**Tamamlanma Zamanı**|Görevin tamamlandığı zaman.|
|**Konum**|Görevin çağrı yığınında geçerli konum. Görevin tüm çağrı yığınını görmek için bu hücrenin üzerine gelin. Zamanlanan görevlerin bu sütunda bir değeri yok.|
|**Görev**|İlk yöntem ve oluşturulduğunda göreve geçirilen bağımsız değişkenler.|
|**AsyncState**|Yönetilen kod için görev durumu. Bu sütun varsayılan olarak gizlidir. Bu sütunu göstermek için, sütun başlıklarından biri için bağlam menüsünü açın. **Sütunları**, **AsyncState** öğesini seçin.|
|**Parent**|Bu görevi oluşturan görevin KIMLIĞI. Bu boşsa, görevin üst öğesi yok. Bu yalnızca yönetilen programlar için geçerlidir.|
|**İş parçacığı ataması**|Görevin üzerinde çalıştığı iş parçacığının KIMLIĞI ve adı.|
|**AppDomain**|Yönetilen kod için görevin yürütüldüğü uygulama etki alanı.|
|**task_group**|Yerel kod için, görevi planladığı [task_group](/cpp/parallel/concrt/reference/task-group-class) nesnesinin adresi. Zaman uyumsuz aracılar ve hafif görevler için bu sütun 0 olarak ayarlanır.|
|**İşleme**|Görevin üzerinde çalıştığı işlemin KIMLIĞI.|

 Bir sütun başlığına sağ tıklayıp istediğiniz sütunları seçerek görünüme sütun ekleyebilirsiniz. (Seçimleri temizleyerek sütunları kaldırın.) Sütunları sola veya sağa sürükleyerek da sıralayabilirsiniz. Sütun kısayol menüsü aşağıdaki çizimde gösterilmiştir.

 ![Görevler penceresinde kısayol Görünüm menüsü](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Görevleri sıralama
 Görevleri sütun ölçütlerine göre sıralamak için sütun başlığına tıklayın. Örneğin, **kimlik** sütunu başlığına tıklayarak GÖREVLERI görev kimliği: 1, 2, 3, 4, 5 vb. olarak sıralayabilirsiniz. Sıralama düzenini tersine çevirmek için sütun başlığına tekrar tıklayın. Geçerli sıralama sütunu ve sıralama düzeni, sütundaki bir okla belirtilir.

## <a name="grouping-tasks"></a>Görevleri gruplandırma
 Görevleri liste görünümündeki herhangi bir sütuna göre gruplandırabilirsiniz. Örneğin, **durum** sütunu başlığına sağ tıklayıp ardından **grupla**' ya tıklayarak  >  **[*durum*]** seçeneğine tıkladığınızda, aynı duruma sahip tüm görevleri gruplayabilirsiniz. Örneğin, neden engellendikleri konusunda odaklanabilmeniz için görevleri beklediğinizi hızlıca görebilirsiniz. Ayrıca, hata ayıklama oturumu sırasında ilgilenmeyen bir grubu daraltabilirsiniz. Aynı şekilde, diğer sütunlara göre gruplandırabilirsiniz. Grup üst bilgisinin yanındaki düğmeye tıklanarak, bir grup (yok) belirlenemez. Aşağıdaki çizimde, **Görevler** penceresi gruplanmış modda gösterilmektedir.

 ![Görevler penceresinde gruplanmış mod](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Üst alt öğe görünümü
 (Bu görünüm yalnızca yönetilen kod için kullanılabilir.) **Durum** sütunu başlığına sağ tıklayıp, üst öğeye **göre Gruplandır**  >  ' a tıklayarak, görev listesini her alt görevin üst öğesi altında görüntülenebilen veya gizlenen bir alt düğüm olduğu hiyerarşik bir görünüm olarak değiştirebilirsiniz.

## <a name="flagging-tasks"></a>Görevleri bayrak atama
 Görev listesi öğesini seçip bağlam menüsünden **bayrak atanmış Iş parçacığı** öğesini seçerek veya ilk sütundaki bayrak simgesine tıklayarak iş parçacığına bir görevin çalıştığı görevi işaretleyebilirsiniz. Birkaç görevi işaretlemeniz halinde bayrak sütunu üzerinde sıralama yapabilirsiniz. böylece, yalnızca bunlara odaklanabilmeniz için bayraklı tüm görevleri en üste getirebilirsiniz. Yalnızca işaretlenen görevleri görüntülemek için **Paralel Yığınlar** penceresini de kullanabilirsiniz. Bu, hata ayıklama için ilgilendiğiniz görevleri filtrelemenizi sağlar. Bayraklar hata ayıklama oturumları arasında kalıcı değildir.

## <a name="freezing-and-thawing-tasks"></a>Donma ve Çözülen Görevler
 Görev listesi öğesini sağ tıklar ve ardından Atanan İş Parçacığını Dondur'a tıklayarak bir görevin üzerinde çalıştırdığı **iş parçacığını dondurabilirsiniz.** (Bir görev zaten donmuşsa, komut **Thaw Atanmış İş Parçacığı'dır.)** Bir iş parçacığını dondurduktan sonra kodda adım adım ilerlerken bu iş parçacığı yürütülmez. Tüm **İş Parçacıklarını Dondur ama Bu** Bir komutu, görev listesi öğesini yürüten iş parçacığı dışındaki tüm iş parçacıklarını donduruyor.

 Aşağıdaki çizimde her görev için diğer menü öğeleri gösterilmiştir.

 ![Görevler penceresindeki kısayol iş parçacığı menüsü](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Etkin Görevi veya Çerçeveyi Değiştirme

Göreve **Geç komutu** geçerli görevi etkin görev yapar. Çerçeveye **Geçiş Komutu** seçili yığın çerçevesini etkin yığın çerçevesi yapar. Hata ayıklayıcısı bağlamı geçerli göreve veya seçilen yığın çerçevesine geçişler.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [Paralel Programlama](/dotnet/standard/parallel-programming/index)
- [Eşzamanlılık Çalışma Zamanı](/cpp/parallel/concrt/concurrency-runtime)
- [Paralel Yığınlar Penceresini Kullanma](../debugger/using-the-parallel-stacks-window.md)
- [İzlenecek Yol: Paralel Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)