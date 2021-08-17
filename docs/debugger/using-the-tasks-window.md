---
title: Görevler Penceresi penceresini | Microsoft Docs
description: Görevler eş zamanlı olarak çalıştırabilirsiniz zaman uyumsuz işlemlerdir. Aynı iş parçacığında birden çok görev çalışması gerçekleştirebilir. Görev ve WinJS.Promise nesne bilgilerini görüntülemek için Görevler'i kullanın.
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
# <a name="using-the-tasks-window-c-visual-basic-c"></a>Görevler Penceresini Kullanma (C#, Visual Basic, C++)

Görevler **penceresi** İş Parçacıkları  penceresine benzer ancak her iş parçacığı yerine <xref:System.Threading.Tasks.Task?displayProperty=fullName> , [task_handle](/cpp/parallel/concrt/reference/task-group-class)veya [WinJS.Promise](/previous-versions/windows/apps/br211867(v=win.10)) nesneleriyle ilgili bilgileri gösterir. İş parçacıkları gibi görevler de eşzamanlı olarak çalıştırıla zaman uyumsuz işlemleri temsil ediyor; ancak, aynı iş parçacığında birden çok görev çalışmasına neden olabilir.

Yönetilen kodda, nesnelerle  veya await ve async anahtar sözcükleriyle <xref:System.Threading.Tasks.Task?displayProperty=fullName> (VisualBasic'te **Await** ve **Async)**  birlikteyken Görevler penceresini kullanabilirsiniz.  Yönetilen kodda görevler hakkında daha fazla bilgi için bkz. [Paralel Programlama.](/dotnet/standard/parallel-programming/index)

Yerel kodda görev [grupları,](/cpp/parallel/concrt/task-parallelism-concurrency-runtime)paralel algoritmalar, zaman [](/cpp/parallel/concrt/parallel-algorithms)uyumsuz aracılar [ve](/cpp/parallel/concrt/asynchronous-agents)basit görevler ile birlikte  çalışabilirsiniz. [](/cpp/parallel/concrt/task-scheduler-concurrency-runtime) Yerel kodda görevler hakkında daha fazla bilgi için bkz. [Eşzamanlılık Çalışma Zamanı.](/cpp/parallel/concrt/concurrency-runtime)

Promise koduyla çalışırken JavaScript'te Görevler penceresini `.then` kullanabilirsiniz. Daha [fazla bilgi için bkz. JavaScript'te zaman](/previous-versions/windows/apps/hh700330(v=win.10)) uyumsuz programlama (UWP uygulamaları).

Hata **ayıklayıcısına her** girebilirsiniz. Hata Ayıkla menüsünden Hata **Ayıkla'ya** ve **Windows'ye** tıklayarak **erişebilirsiniz.** Aşağıdaki çizimde Görevler **penceresi** varsayılan modunda gösterilir.

![Görevler penceresi](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> Yönetilen kodda, yönetilen iş parçacıkları uyku veya birleştirme durumunda olduğunda <xref:System.Threading.Tasks.Task> [TaskStatus.Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus.WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>)  veya [TaskStatus.WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) durumu Görevler penceresinde görüntülenmez.

## <a name="tasks-column-information"></a>Görevler Sütun Bilgileri

Görevler **penceresindeki sütunlar** aşağıdaki bilgileri gösterir.

|Sütun Adı|Açıklama|
|-----------------|-----------------|
|**Bayrak**|Hangi görevlerin işaretli olduğunu gösterir ve bir görevi bayrakla işaretlenmenizi veya işaretlerini geri alamamanizi sağlar.|
|**Simgeler**|Sarı ok, geçerli görevi gösterir. Geçerli görev, geçerli iş parçacığında en üst sırada yer alan görevdir.<br /><br /> Beyaz ok, hata ayıklayıcı çağrıldığında geçerli olan hata ayıklama görevini belirtir.<br /><br /> Duraklatma simgesi, kullanıcı tarafından donmuş bir görevi gösterir. Listede sağ tıklayarak bir görevi dondurabilir ve serbest ekleyebilirsiniz.|
|**ID**|Görev için sistem tarafından sağlanan bir sayı. Yerel kodda bu, görevin adresidir.|
|**Durum**|Görevin geçerli durumu (zamanlanmış, etkin, engellenen, kilitlenmiş, bekleniyor veya tamamlandı). Zamanlanmış görev henüz çalıştırılmış olan bir görevdir ve bu nedenle henüz bir çağrı yığınına, atanmış iş parçacığına veya ilgili bilgilere sahip değildir.<br /><br /> Etkin görev, hata ayıklayıcıda hata ayıklayıcıda hata ayıklamadan önce kod yürüten görevdir.<br /><br /> Bekleyen veya engellenen görev, bir olayın sinyale konmalarını, serbest bırakılamalarını veya bitecek başka bir görevi beklediği için engellenen görevdir.<br /><br /> Kilitlenmeli görev, iş parçacığı başka bir iş parçacığıyla kilitli bekleyen bir görevdir.<br /><br /> Kilitlenme veya **bekleyen** görevin Durum hücresi üzerine gelerek blok hakkında daha fazla bilgi edinebilirsiniz. **Uyarı:**  Görevler **penceresi** kilitlenmeyi yalnızca Bekleme Zinciri Geçişi (WCT) tarafından desteklenen bir eşitleme temel öğe kullanan engellenen bir görev için raporlar. Örneğin, WCT kullanan kilitlenmemiş bir nesne için <xref:System.Threading.Tasks.Task> hata ayıklayıcısı **Awaiting-deadlocked raporlar.** WCT kullanmayan, Eşzamanlılık Çalışma Zamanı tarafından yönetilen kilitlenmeli bir görev için hata ayıklayıcı Bekliyor 'u **raporlar.** WCT hakkında daha fazla bilgi için [bkz. Bekleme Zinciri Geçişi.](/windows/desktop/Debug/wait-chain-traversal)|
|**Başlangıç Zamanı**|Görevin etkin olduğu zaman.|
|**Süre**|Görevin etkin olduğu saniye sayısı.|
|**Tamamlanma Zamanı**|Görevin tamamlanma zamanı.|
|**Konum**|Görevin çağrı yığınındaki geçerli konum. Görevin çağrı yığınının tamamını görmek için bu hücrenin üzerine gelin. Zamanlanmış görevlerin bu sütunda bir değeri yoktur.|
|**Görev**|İlk yöntem ve oluşturulduğunda göreve geçirilen bağımsız değişkenler.|
|**Asyncstate**|Yönetilen kod için görev durumu. Bu sütun varsayılan olarak gizlidir. Bu sütunu görüntülemek için sütun üst bilgilerinden birinin bağlam menüsünü açın. Sütunlar , **AsyncState seçin.**|
|**Parent**|Bu görevi oluşturan görevin kimliği. Bu boşsa, görevin üst öğesi yoktur. Bu yalnızca yönetilen programlar için geçerlidir.|
|**İş Parçacığı Ataması**|Görevin üzerinde çalıştır olduğu iş parçacığının kimliği ve adı.|
|**Appdomain**|Yönetilen kod için, görevin yürütülmektedir uygulama etki alanı.|
|**Task_group**|Yerel kod için, görevi zaman [task_group](/cpp/parallel/concrt/reference/task-group-class) nesnesinin adresi. Zaman uyumsuz aracılar ve basit görevler için bu sütun 0 olarak ayarlanır.|
|**İşleme**|Görevin üzerinde çalıştır olduğu sürecin kimliği.|

 Bir sütun başlığına sağ tıklar ve ardından istediğiniz sütunları seçerek görünüme sütun ekleyebilirsiniz. (Seçimleri temizerek sütunları kaldırın.) Sütunları sola veya sağa sürükleyerek de yeniden sıralayabilirsiniz. Sütun kısayol menüsü aşağıdaki çizimde gösterilmiştir.

 ![Görevler penceresindeki kısayol görünümü menüsü](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Görevleri Sıralama
 Görevleri sütun ölçütlerine göre sıralamak için sütun başlığına tıklayın. Örneğin, KIMLIK sütunu  üst bilgine tıklayarak görevleri 1,2,3,4,5 gibi görev kimliğine göre sıraabilirsiniz. Sıralama sıralamayı ters çevirmek için sütun üst bilgisini yeniden tıklatın. Geçerli sıralama sütunu ve sıralama düzeni, sütundaki bir okla belirtilmiştir.

## <a name="grouping-tasks"></a>Görevleri Gruplama
 Görevleri liste görünümündeki herhangi bir sütuna göre grupabilirsiniz. Örneğin, Durum sütunu üst  bilgisinde sağ tıklar ve ardından  >  **Grupla [*durum*]** seçeneğine tıklayarak, aynı durumu olan tüm görevleri grupabilirsiniz. Örneğin, görevlerin nasıl engellenmiş olduğuna odaklanarak görevlerin nasıl engellenmiş olduğunu hızlıca görebilirsiniz. Ayrıca, hata ayıklama oturumu sırasında ilgini yer alan bir grubu daraltabilirsiniz. Aynı şekilde, diğer sütunlara göre gruplayabilirsiniz. Bir grup, yalnızca grup üst bilgisi yanındaki düğmeye tıklayarak işaretlenmez (işaretlenmez). Aşağıdaki çizimde, **Görevler penceresi** gruplanmış modda gösterilir.

 ![Görevler penceresinde gruplanmış mod](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Üst Alt Görünüm
 (Bu görünüm yalnızca yönetilen kod için kullanılabilir.) Durum sütun başlığına sağ tıklar ve ardından Üst Öğeye Göre Grupla'ya tıklayarak, görev listesini hiyerarşik bir görünüm olarak değiştirebilirsiniz. Bu görünümde her alt görev, üst öğesi altında görüntülenebilir veya gizlenebilir bir alt düğüm   >  olur.

## <a name="flagging-tasks"></a>Flagging Görevleri
 Görev listesi öğesini ve ardından bağlam menüsünden Atanan İş Parçacığına Bayrak  Ekle'yi seçerek veya ilk sütundaki bayrak simgesine tıklayarak görevin üzerinde çalıştırdığı iş parçacığına bayrak ekleyebilirsiniz. Birden fazla görev bayrakla işaretlenirse bayrak sütununa göre sıralanmış olarak işaretlenen tüm görevleri en üst düzeye getirebilirsiniz; böylece yalnızca bu görevlere odaklanabilirsiniz. Paralel Yığınlar penceresini **yalnızca bayraklı** görevleri görüntülemek için de kullanabilirsiniz. Bu, hata ayıklamayla ilgilenmeniz gereken görevleri filtrelemenizi sağlar. Bayraklar hata ayıklama oturumları arasında kalıcı olmaz.

## <a name="freezing-and-thawing-tasks"></a>Donma ve Çözülen Görevler
 Görev listesi öğesini sağ tıklar ve ardından Atanan İş Parçacığını Dondur'a tıklayarak bir görevin üzerinde çalıştırdığı **iş parçacığını dondurabilirsiniz.** (Bir görev zaten donmuşsa, komut **Thaw Atanmış İş Parçacığı 'dır.)** Bir iş parçacığını dondurduktan sonra kodda adım adım ilerlerken bu iş parçacığı yürütülmez. Tüm **İş Parçacıklarını Dondur ama Bu** Bir komutu, görev listesi öğesini yürüten iş parçacığı dışındaki tüm iş parçacıklarını donduruyor.

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