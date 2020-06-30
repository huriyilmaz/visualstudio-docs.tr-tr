---
title: Paralel Yığınlar penceresini kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e89125c8e1dea25ab02fe64c21b8166e9d65194a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542226"
---
# <a name="using-the-parallel-stacks-window"></a>Paralel Yığınlar Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çoklu iş parçacıklı uygulamalarda hata ayıklarken **Paralel Yığınlar** penceresi faydalıdır. **Iş parçacıkları görünümü** uygulamanızdaki tüm iş parçacıkları için çağrı yığını bilgilerini gösterir. Bu iş parçacıklarında iş parçacıkları ve yığın çerçeveleri arasında gezinmenize imkan tanır. Yönetilen kodda, **Görevler Görünümü** nesnelerin çağrı yığınlarını gösterir <xref:System.Threading.Tasks.Task?displayProperty=fullName> . Yerel kodda, **Görevler Görünümü** [görev gruplarının](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [paralel algoritmaların](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [zaman uyumsuz aracıların](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)ve [hafif görevlerin](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90)çağrı yığınlarını gösterir.  
  
## <a name="threads-view"></a>İş Parçacıkları Görünümü  
 Aşağıdaki çizimde ana öğesinden A 'ya ve sonra da bazı harici koda giden bir iş parçacığı gösterilmektedir. Bir dış koddan daha sonra bir diğer iş parçacığı başlatılır, ancak B ile devam eden iş parçacıklarından biri ve sonra bazı harici kodlar ve diğer iş parçacığı C ve daha sonra bazı AnonymousMethod ile devam eder.  
  
 ![Paralel Yığınlar penceresinde iş parçacıkları görünümü](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 Çizimde, geçerli iş parçacığının çağrı yolu mavi renkle vurgulanır ve etkin yığın çerçevesi sarı oka göre belirlenir. **Paralel Yığınlar** penceresinde farklı bir yöntem seçerek geçerli yığın çerçevesini değiştirebilirsiniz. Bu, seçtiğiniz yöntemin geçerli iş parçacığının veya başka bir iş parçacığının parçası olmasına bağlı olarak, geçerli iş parçacığını değiştirmeye da neden olabilir. Aşağıdaki tabloda, çizimde gösterildiği gibi **Paralel Yığınlar** penceresinin ana özellikleri açıklanmaktadır.  
  
|Belirtme çizgisi harfi|Öğe Adı|Description|  
|--------------------|------------------|-----------------|  
|A|Çağrı yığını segmenti veya düğümü|Bir veya daha fazla iş parçacığı için bir dizi yöntem bağlamı içerir. Düğüme bağlı ok çizgileri yoksa, iş parçacıklarının tüm çağrı yolunu temsil eder.|  
|B|Mavi vurgu|Geçerli iş parçacığının çağrı yolunu gösterir.|  
|C|Ok çizgileri|İş parçacığı (ler) için tüm çağrı yolunu oluşturmak üzere düğümleri bağlayın.|  
|D|Düğüm üstbilgisindeki araç ipucu|Çağrı yolu bu düğümü paylaşan her iş parçacığının KIMLIĞINI ve Kullanıcı tanımlı adını gösterir.|  
|E|Yöntem bağlamı|Aynı yöntemde bir veya daha fazla yığın çerçevesini temsil eder.|  
|F|Yöntem bağlamında araç ipucu|Iş parçacıkları görünümünde, bir tablodaki tüm iş parçacıklarını **Iş parçacıkları** penceresine benzer şekilde gösterir. Görev görünümünde, **paralel görevler** penceresine benzer şekilde bir tablodaki tüm görevleri gösterir.|  
  
 Ayrıca Paralel Yığınlar penceresi, Graph pencereye sığmayacak kadar büyük olduğunda ana bölmedeki bir **kuşbakışı görünümü** simgesini gösterir. Penceredeki tüm grafiği görmek için simgeye tıklayabilirsiniz.  
  
## <a name="method-context-icons"></a>Yöntem bağlamı simgeleri  
 Aşağıdaki tabloda, etkin ve geçerli yığın çerçeveleri hakkında bilgi sağlayan simgeler açıklanmaktadır:  
  
|Simge|Description|  
|-|-|
|![Paralel Yığınlar sarı ok](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Yöntem bağlamının geçerli iş parçacığının etkin yığın çerçevesini içerdiğini belirtir.|  
|![Paralel Yığınlar Iş parçacıkları simgesi](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|Yöntem bağlamının geçerli olmayan bir iş parçacığının etkin yığın çerçevesini içerdiğini belirtir.|  
|![Paralel Yığınlar yeşil ok](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Yöntem bağlamının geçerli yığın çerçevesini içerdiğini belirtir. Bu yöntem adı, göründüğü tüm düğümlerde kalın olur.|  
  
## <a name="toolbar-controls"></a>Araç çubuğu denetimleri  
 Aşağıdaki çizim ve tablo, Paralel Yığınlar araç çubuğunda bulunan denetimleri anlatmaktadır.  
  
 ![Paralel Yığınlar penceresinde araç çubuğu](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|Belirtme çizgisi harfi|Denetim|Description|  
|--------------------|-------------|-----------------|  
|A|İş parçacıkları/görevler açılan kutusu|Görünümü iş parçacıklarının çağrı yığınları ve görev yığınları arasında geçirir. Daha fazla bilgi için bkz. görevler görünümü ve Iş parçacıkları görünümü.|  
|B|Yalnızca bayraklı göster|Yalnızca diğer hata ayıklama pencerelerinin (örneğin, **GPU Iş parçacıkları** penceresi ve **paralel izleme** penceresi) işaretlenen iş parçacıkları için çağrı yığınlarını gösterir.|  
|C|Yöntem görünümünü değiştirme|Yığın görünümü ve Yöntem görünümü arasında geçiş yapar. Daha fazla bilgi için bkz. Yöntem görünümü.|  
|D|Geçerli yığın çerçevesine Otomatik Kaydır|Diyagramı geçerli yığın çerçevesinin görünümü olacak şekilde oto kaydır. Bu özellik, geçerli yığın çerçevesini diğer pencerelerin değiştirirken veya büyük diyagramlarda yeni bir kesme noktasına vurdığınızda yararlıdır.|  
|E|Yakınlaştırma denetimini değiştirme|Yakınlaştırma denetimini gösterir veya gizler. Ayrıca, yakınlaştırma denetiminin görünürlüğüne veya yakınlaştırmak için CTRL **+ SHIFT + ' +** ' tuşlarını kullanarak, **yakınlaştırmak için CTRL** tuşuna basarak ve fare tekerleğini açıp kapatabilirsiniz. **CTRL + F8** tuşlarına basmak ekrana sığacak şekilde yakınlaşacaktır.|  
  
### <a name="context-menu-items"></a>Bağlam menüsü öğeleri  
 Aşağıdaki çizim ve tablo, Iş parçacıkları görünümü veya Görevler görünümünde bir yöntem bağlamına sağ tıkladığınızda kullanılabilen kısayol menü öğelerini anlatmaktadır. Son altı öğe doğrudan çağrı yığını penceresinden ödünç alınır ve yeni bir davranış sunmaz.  
  
 ![Paralel Yığınlar penceresinde kısayol menüsü](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|Menü Öğesi|Description|  
|---------------|-----------------|  
|Bayrak|Seçili öğeyi bayraklar.|  
|İşaretsiz|Seçili öğenin bayraklarını kaldır.|  
|Amazsınız|Seçili öğeyi dondurur.|  
|Çözme|Seçili öğeyi Thaw.|  
|Göreve git (Iş parçacığı)|Araç çubuğundaki Birleşik giriş kutusuyla aynı işlevi gerçekleştirir, ancak aynı yığın çerçevesini vurgulatutar.|  
|Kaynak koduna git|Kullanıcının sağ tıkladığını yığın çerçevesine karşılık gelen kaynak kodundaki konuma gider.|  
|Çerçeveye geçiş yap|Çağrı yığını penceresinde karşılık gelen menü komutuyla aynı. Ancak, paralel yığınlarla birden çok çerçeve bir yöntem bağlamına karşılık gelebilir. Bu nedenle, menü öğesi, her biri belirli bir yığın çerçevesini temsil eden alt menülere sahiptir. Yığın çerçevelerinden biri geçerli iş parçacığından geliyorsa, bu yığın çerçevesine karşılık gelen menü seçilidir.|  
|Ayrıştırılmış koda git|Kullanıcının sağ tıkladığını yığın çerçevesine karşılık gelen ayrıştırma penceresindeki konuma gider.|  
|Dış kodu göster|Dış kodu gösterir veya gizler.|  
|Onaltılı ekran|Ondalık ve onaltılık görüntü arasında geçiş yapar.|  
|Sembol Yükleme Bilgisi|İlgili iletişim kutusunu görüntüler.|  
|Sembol ayarları|İlgili iletişim kutusunu görüntüler.|  
  
## <a name="tasks-view"></a>Görevler görünümü  
 Uygulamanız, <xref:System.Threading.Tasks.Task?displayProperty=fullName> paralellik sağlamak için nesneleri (yönetilen kod) veya `task_handle` nesneleri (yerel kod) kullanıyorsa, *Görevler görünümüne*geçmek için Paralel Yığınlar penceresi araç çubuğundaki Birleşik giriş kutusunu kullanabilirsiniz. Görevler Görünümü iş parçacıkları yerine görevlerin çağrı yığınlarını gösterir. Görevler görünümü Iş parçacıkları görünümünden aşağıda gösterildiği gibi farklıdır:  
  
- Görevleri çalıştırmayan iş parçacıklarının çağrı yığınları gösterilmez.  
  
- Görevleri çalıştıran iş parçacıklarının çağrı yığınları, görevlerle ilgili en ilgili kareleri göstermek için en üstte ve en altta görsel olarak kırpılmakta.  
  
- Bir iş parçacığında birden çok görev olduğunda, bu görevlerin çağrı yığınları ayrı düğümlere bölünür.  
  
  Aşağıdaki çizimde, solda ve ilgili Iş parçacıkları görünümündeki Paralel Yığınlar görevler görünümü gösterilmektedir.  
  
  ![Paralel Yığınlar penceresinde görevler görünümü](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
  Tüm çağrı yığınını görmek için, bir yığın çerçevesine sağ tıklayıp sonra **Iş parçacığına git**' e tıklayarak Iş parçacıkları görünümüne geri geçmeniz yeterlidir.  
  
  Önceki tabloda açıklandığı gibi, bir yöntem bağlamının üzerine gelindiğinde, ek bilgi görebilirsiniz. Aşağıdaki görüntüde, Iş parçacıkları görünümü ve görevler görünümü için araç ipucunda bulunan bilgiler gösterilmektedir.  
  
  ![Paralel Yığınlar penceresinde araç ipuçları](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Yöntem görünümü  
 Herhangi bir Iş parçacığı görünümü veya görevler görünümünden, araç çubuğundaki Yöntem görünümü simgesine tıklayarak grafiği geçerli yöntemde Özet olarak ekleyebilirsiniz. Yöntem görünümü, ya da çağıran ya da geçerli yöntem tarafından çağrılan tüm iş parçacıklarında tüm yöntemleri gösterir. Aşağıdaki çizimde bir Iş parçacığı görünümü ve ayrıca aynı bilgilerin Yöntem görünümünde nasıl göründüğü gösterilmektedir.  
  
 ![Paralel Yığınlar penceresinde Yöntem görünümü](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 Yeni bir yığın çerçevesine geçerek, bu yöntemi geçerli yöntemi yapar ve yeni yöntem için pencerenin tüm çağıranları ve calkaları göstermesini sağlar. Bu yöntem, yöntemin çağrı yığınlarında görünüp görünmediğini bağlı olarak görünümde bazı iş parçacıklarının görünmesine veya görünmemesine neden olabilir. Yığın görünümüne dönmek için, yöntem görünümü araç çubuğu düğmesine tekrar tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Hata ayıklayıcı temelleri](../debugger/debugger-basics.md)   
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Paralel programlama](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Görevler penceresini kullanma](../debugger/using-the-tasks-window.md)   
 [İzlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Task Sınıfı](../extensibility/debugger/task-class-internal-members.md)
