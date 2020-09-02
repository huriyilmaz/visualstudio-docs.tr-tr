---
title: Görevler penceresini kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 267a04e0d717bde311423aae7f35fba07ca6f39b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684033"
---
# <a name="using-the-tasks-window"></a>Görevleri Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Görevler** penceresi, **iş parçacıkları** penceresine benzer, ancak <xref:System.Threading.Tasks.Task?displayProperty=fullName> her iş parçacığı yerine, [task_handle](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7)veya [WinJS. Promise](https://msdn.microsoft.com/library/windows/apps/br211867.aspx) nesneleri hakkında bilgi gösterir. İş parçacıkları gibi görevler, eşzamanlı olarak çalışabilecek zaman uyumsuz işlemleri temsil eder; Ancak, aynı iş parçacığında birden çok görev çalıştırılabilir. Daha fazla bilgi için bkz. [JavaScript 'Te zaman uyumsuz programlama (Windows Mağazası uygulamaları)](https://msdn.microsoft.com/library/windows/apps/hh700330.aspx) .  
  
 Yönetilen **Tasks** kodda, nesnelerle çalışırken <xref:System.Threading.Tasks.Task?displayProperty=fullName> veya **await** ve **Async** anahtar sözcükleriyle (VisualBasic içinde**await** ve **Async** ) görevler penceresini kullanabilirsiniz. Yönetilen koddaki görevler hakkında daha fazla bilgi için bkz.  [paralel programlama](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d).  
  
 Yerel kodda [görev grupları](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [paralel algoritmalar](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [zaman uyumsuz aracılar](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)ve [hafif görevlerle](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90)çalışırken **Görevler** penceresini kullanabilirsiniz. Yerel koddaki görevler hakkında daha fazla bilgi için bkz. [Eşzamanlılık çalışma zamanı](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c).  
  
 JavaScript 'te, taahhüt ile çalışırken görevler penceresini kullanabilirsiniz. daha sonra kodu.  
  
 Hata ayıklayıcıya her kesme yaptığınızda **Görevler** penceresini kullanabilirsiniz. **Hata Ayıkla** menüsünde **Windows** ' a ve ardından **Görevler**' e tıklayarak erişebilirsiniz. Aşağıdaki çizimde **Görevler** penceresi varsayılan modunda gösterilmektedir.  
  
 ![Paralel Görevler penceresi](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
> Yönetilen kodda, <xref:System.Threading.Tasks.Task> durumu <xref:System.Threading.Tasks.TaskStatus> , <xref:System.Threading.Tasks.TaskStatus> veya, <xref:System.Threading.Tasks.TaskStatus> yönetilen iş parçacıkları bir uyku ya da JOIN durumunda olduğunda Görevler penceresinde görüntülenmeyebilir.  
  
## <a name="tasks-column-information"></a>Görevler sütun bilgileri  
 **Görevler** penceresindeki sütunlar aşağıdaki bilgileri gösterir.  
  
|Sütun adı|Description|  
|-----------------|-----------------|  
|**Larına**|Hangi görevlerin işaretlenip işaretlenmediğini gösterir ve bir görevi işaretlemenizi veya bayrak kaldırmanızı sağlar.|  
|**Simgeler**|Sarı ok geçerli görevi gösterir. Geçerli görev, geçerli iş parçacığında en üstteki görevdir.<br /><br /> Beyaz ok, son görevi, yani hata ayıklayıcı çağrıldığında geçerli olan olanı gösterir.<br /><br /> Duraklat simgesi, Kullanıcı tarafından dondurulmuş olan bir görevi gösterir. Listede sağ tıklayarak bir görevi dondurabilir ve çöz ' ü seçebilirsiniz.|  
|**ID**|Görevin sistem tarafından sağlanmış numarası. Yerel kodda, bu görevin adresidir.|  
|**Durum**|Görevin geçerli durumu (zamanlanan, etkin, kilitli, bekleniyor veya tamamlandı). Zamanlanmış bir görev henüz çalıştırılmayan ve bu nedenle çağrı yığınına, atanan iş parçacığına veya ilgili bilgilere sahip değildir.<br /><br /> Etkin bir görev, hata ayıklayıcıda kesmeden önce kodu yürüten bir görevdir.<br /><br /> Bekleyen bir görev, bir olayın bildirilebilmesi, yayınlanacak bir kilit ya da başka bir görevin bitmesi beklediği için engellenmiş bir görevdir.<br /><br /> Kilitlenen bir görev, iş parçacığı başka bir iş parçacığıyla kilitlenmiş bekleyen bir görevdir.<br /><br /> Blok hakkında daha fazla bilgi görmek için kilitlenen veya bekleyen bir görevin **durum** hücresinin üzerine gelin. **Uyarı:**  **Görevler** penceresi, yalnızca bekleme zinciri çapraz geçişi (WCT) tarafından desteklenen bir eşitleme temel alanı kullanan engellenen bir görev için kilitlenme bildirir. Örneğin, <xref:System.Threading.Tasks.Task> WCT kullanan, kilitli olmayan bir nesne için, hata ayıklayıcı **bekliyor-** kilitlendi ' ı raporlar. WCT kullanmayan Eşzamanlılık Çalışma Zamanı tarafından yönetilen kilitli olmayan bir görev için, hata ayıklayıcı rapor **bekliyor**. WCT hakkında daha fazla bilgi için bkz. [zincir geçişini bekleme](https://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Başlangıç Zamanı**|Görevin etkin hale geldiğinden geçen süre.|  
|**Süre**|Görevin etkin olduğu saniye sayısı.|  
|**Tamamlanma Zamanı**|Görevin tamamlandığı zaman.|  
|**Konum**|Görevin çağrı yığınında geçerli konum. Görevin tüm çağrı yığınını görmek için bu hücrenin üzerine gelin. Zamanlanan görevlerin bu sütunda bir değeri yok.|  
|**Görev**|İlk yöntem ve oluşturulduğunda göreve geçirilen bağımsız değişkenler.|  
|**Parent**|Bu görevi oluşturan görevin KIMLIĞI. Bu boşsa, görevin üst öğesi yok. Bu yalnızca yönetilen programlar için geçerlidir.|  
|**İş parçacığı ataması**|Görevin üzerinde çalıştığı iş parçacığının KIMLIĞI ve adı.|  
|**Dönüş durumu**|Görevin tamamlandığı durum. Döndürülen durum değerleri **başarılı**, **Iptal edildi**ve **hata**.|  
|**AppDomain**|Yönetilen kod için görevin yürütüldüğü uygulama etki alanı.|  
|**task_group**|Yerel kod için, görevi planladığı [task_group](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) nesnesinin adresi. Zaman uyumsuz aracılar ve hafif görevler için bu sütun 0 olarak ayarlanır.|  
|İşleme|Görevin üzerinde çalıştığı işlemin KIMLIĞI.|  
|Zaman uyumsuz durum|Yönetilen kod için görev durumu. Bu sütun varsayılan olarak gizlidir. Bu sütunu göstermek için, sütun başlıklarından biri için bağlam menüsünü açın. **Sütunları**, **AsyncState**öğesini seçin.|  
  
 Bir sütun başlığına sağ tıklayıp istediğiniz sütunları seçerek görünüme sütun ekleyebilirsiniz. (Seçimleri temizleyerek sütunları kaldırın.) Sütunları sola veya sağa sürükleyerek da sıralayabilirsiniz. Sütun kısayol menüsü aşağıdaki çizimde gösterilmiştir.  
  
 ![Paralel Görevler penceresinde kısayol Görünüm menüsü](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Görevleri sıralama  
 Görevleri sütun ölçütlerine göre sıralamak için sütun başlığına tıklayın. Örneğin, **kimlik** sütunu başlığına tıklayarak GÖREVLERI görev kimliği: 1, 2, 3, 4, 5 vb. olarak sıralayabilirsiniz. Sıralama düzenini tersine çevirmek için sütun başlığına tekrar tıklayın. Geçerli sıralama sütunu ve sıralama düzeni, sütundaki bir okla belirtilir.  
  
## <a name="grouping-tasks"></a>Görevleri gruplandırma  
 Görevleri liste görünümündeki herhangi bir sütuna göre gruplandırabilirsiniz. Örneğin, **durum** sütunu başlığına sağ tıklayıp ardından **duruma göre Gruplandır**' a tıkladığınızda, aynı duruma sahip tüm görevleri gruplandırabilirsiniz. Örneğin, neden engellendikleri konusunda odaklanabilmeniz için bekleyen görevleri hızla görebilirsiniz. Ayrıca, hata ayıklama oturumu sırasında ilgilenmeyen bir grubu daraltabilirsiniz. Aynı şekilde, diğer sütunlara göre gruplandırabilirsiniz. Grup üst bilgisinin yanındaki düğmeye tıklanarak, bir grup (yok) belirlenemez. Aşağıdaki çizimde, **Görevler** penceresi gruplanmış modda gösterilmektedir.  
  
 ![Paralel Görevler penceresinde gruplanmış mod](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Üst alt öğe görünümü  
 (Bu görünüm yalnızca yönetilen kod için kullanılabilir.) Bir sütun başlığına sağ tıklayıp **üst alt öğe görünümü**' ne tıklayarak, görev listesini her alt görevin üst öğesi altında görüntülenebilen veya gizlenebilen bir alt düğüm olduğu hiyerarşik bir görünüm olarak değiştirebilirsiniz. Aşağıdaki çizimde, üst-alt görünümündeki görevler gösterilmektedir.  
  
 ![Paralel Görevler penceresinde üst&#45;alt öğe görünümü](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Görevleri bayrak atama  
 Görev listesi öğesini seçip bağlam menüsünden **bayrak** ' i seçerek veya ilk sütundaki bayrak simgesine tıklayarak iş parçacığına bir görevin çalıştığı görevi işaretleyebilirsiniz. Birkaç görevi işaretlemeniz halinde bayrak sütunu üzerinde sıralama yapabilirsiniz. böylece, yalnızca bunlara odaklanabilmeniz için bayraklı tüm görevleri en üste getirebilirsiniz. Yalnızca işaretlenen görevleri görüntülemek için **Paralel Yığınlar** penceresini de kullanabilirsiniz. Bu, hata ayıklama için ilgilendiğiniz görevleri filtrelemenizi sağlar. Bayraklar hata ayıklama oturumları arasında kalıcı değildir.  
  
## <a name="freezing-and-thawing-tasks"></a>Görevleri donduruyor ve Thakelebek  
 Görev listesi öğesine sağ tıklayıp **atanan Iş parçacığını dondur**' a tıklayarak bir görevin çalıştığı iş parçacığını dondurabilirsiniz. (Bir görev zaten dondurulmuşsa, komut **atanan Iş parçacığını çözme**işlemi olur.) Bir iş parçacığını dondurduktan sonra, geçerli kesme noktasından sonra koddan ilerledikten sonra bu iş parçacığı yürütülmez. **Tüm Iş parçacıklarını dondur, ancak bu** komut, görev listesi öğesini yürüten öğe dışındaki tüm iş parçacıklarını dondurur.  
  
 Aşağıdaki çizim her bir görev için diğer menü öğelerini gösterir.  
  
 ![Paralel Görevler penceresinde kısayol iş parçacığı menüsü](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı temelleri](../debugger/debugger-basics.md)   
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Paralel programlama](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Eşzamanlılık Çalışma Zamanı](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Paralel Yığınlar penceresini kullanma](../debugger/using-the-parallel-stacks-window.md)   
 [İzlenecek Yol: Paralel Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)
