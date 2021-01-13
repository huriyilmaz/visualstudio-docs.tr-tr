---
title: Kanalları Paralel Yığınlar penceresinde görüntüleme | Microsoft Docs
description: Çoklu iş parçacıklı uygulamalarda hata ayıklamaya yardımcı olması için paralel yığınları kullanın. Tüm iş parçacıkları ve görev merkezli çağrı yığını bilgileri için yığın bilgilerini görüntüleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55a004e65a39f4a2b7bbf972cec36d689bf88d97
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150177"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>Paralel Yığınlar penceresinde iş parçacıklarını ve görevleri görüntüleme (C#, Visual Basic, C++)

**Paralel Yığınlar** penceresi, çok iş parçacıklı uygulamalarda hata ayıklamak için faydalıdır. Çeşitli görünümlere sahiptir:

- [Iş parçacıkları görünümü](#threads-view) uygulamadaki tüm iş parçacıkları için çağrı yığını bilgilerini gösterir. Bu iş parçacıklarında iş parçacıkları ve yığın çerçeveleri arasında gezinebilirsiniz.

- [Görevler Görünümü](#tasks-view) görev merkezli çağrı yığını bilgilerini gösterir.
  - Yönetilen kodda, **Görevler** görünümü nesnelerin çağrı yığınlarını gösterir <xref:System.Threading.Tasks.Task?displayProperty=fullName> .
  - Yerel kodda, **Görevler** görünümü [görev gruplarının](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [paralel algoritmaların](/cpp/parallel/concrt/parallel-algorithms), [zaman uyumsuz aracıların](/cpp/parallel/concrt/asynchronous-agents)ve [hafif görevlerin](/cpp/parallel/concrt/task-scheduler-concurrency-runtime)çağrı yığınlarını gösterir.

- [Yöntem görünümü](#method-view) seçili bir yöntemde çağrı yığınını özetler.

## <a name="use-the-parallel-stacks-window"></a>Paralel Yığınlar penceresini kullanma

**Paralel Yığınlar** penceresini açmak için bir hata ayıklama oturumunda olması gerekir.   >  **Windows**  >  **paralel yığınları** Hata Ayıkla ' yı seçin.

### <a name="toolbar-controls"></a>Araç çubuğu denetimleri

**Paralel Yığınlar** penceresi aşağıdaki araç çubuğu denetimlerine sahiptir:

![Paralel Yığınlar penceresinde araç çubuğu](../debugger/media/parallel_stackstoolbar.png "Paralel Yığınlar araç çubuğu")

|Simge|Denetim|Description|
|-|-|-|
|![İş parçacıkları/görevler açılan kutusu](media/parallel_toolbar1.png "İş parçacıkları/görevler açılan kutusu")|**Iş parçacıkları** / **Görevler** açılan kutusu|Görünümü iş parçacıklarının çağrı yığınları ve görev yığınları arasında geçirir. Daha fazla bilgi için bkz. [Görevler Görünümü](#tasks-view) ve [iş parçacıkları görünümü](#threads-view).|
|![Yalnızca bayraklı simgeyi göster](media/parallel_toolbar2.png "Yalnızca bayraklı simgeyi göster")|Yalnızca bayraklı göster|Yalnızca **GPU Iş parçacıkları** penceresi ve **paralel izleme** penceresi gibi diğer hata ayıklayıcı pencerelerinin bayrak eklenmiş iş parçacıkları için çağrı yığınlarını gösterir.|
|![Değiştirme yöntemi görünümü simgesi](media/parallel_toolbar3.png "Değiştirme yöntemi görünümü simgesi")|**Yöntem görünümünü** değiştirme|Çağrı yığını görünümleri ve **Yöntem görünümü** arasında geçiş yapar. Daha fazla bilgi için bkz. [Yöntem görünümü](#method-view).|
|![Geçerli simgeye Otomatik Kaydır](media/parallel_toolbar4.png "Geçerli simgeye Otomatik Kaydır")|Geçerli yığın çerçevesine Otomatik Kaydır|Grafiği geçerli yığın çerçevesinin görünümü olacak şekilde oto kaydır. Bu özellik, geçerli yığın çerçevesini diğer pencerelerin veya büyük grafiklerde yeni bir kesme noktasına vurdığınızda yararlı olur.|
|![Yakınlaştır simgesini değiştirme](media/parallel_toolbar5.png "Yakınlaştır simgesini değiştirme")|Yakınlaştırma denetimini değiştirme|Pencerenin sol tarafındaki Yakınlaştırma denetimini gösterir veya gizler. <br /><br />Yakınlaştırma denetiminin görünürlüğüne bakılmaksızın, **CTRL** tuşuna basarak ve fare tekerleğini açıp veya **CTRL** + **+ SHIFT** tuşlarına basarak yakınlaştırarak yakınlaştırabilirsiniz + **+**  +  + **-** . |

### <a name="stack-frame-icons"></a>Yığın çerçevesi simgeleri
Aşağıdaki simgeler, tüm görünümlerde etkin ve geçerli yığın çerçeveleri hakkında bilgi sağlar:

|Simge|Description|
|-|-|
|![Sarı ok](media/icon_parallelyellowarrow.gif)|Geçerli iş parçacığının geçerli konumunu (etkin yığın çerçevesi) gösterir.|
|![İş parçacıkları simgesi](media/icon_parallelthreads.gif)|Geçerli olmayan bir iş parçacığının geçerli konumunu (etkin yığın çerçevesi) gösterir.|
|![Yeşil ok](media/icon_parallelgreenarrow.gif)|Geçerli yığın çerçevesini gösterir (geçerli hata ayıklayıcı bağlamı). Yöntem adı göründüğü her yerde kalın.|

### <a name="context-menu-items"></a>Bağlam menüsü öğeleri
Aşağıdaki kısayol menü öğeleri, **Iş parçacıkları** görünümü veya **Görevler** görünümündeki bir yönteme sağ tıkladığınızda kullanılabilir. Son altı öğe, [çağrı yığını penceresindeki](how-to-use-the-call-stack-window.md)ile aynıdır.

![Paralel Yığınlar penceresinde kısayol menüsü](../debugger/media/parallel_contmenu.png "Paralel Yığınlar penceresinde kısayol menüsü")

|Menü öğesi|Description|
|-|-|
|**Bayrak**|Seçili öğeyi bayraklar.|
|**İşaretsiz**|Seçili öğenin bayraklarını kaldır.|
|**Amazsınız**|Seçili öğeyi dondurur.|
|**Çözme**|Seçili öğeyi Thaw.|
|**Çerçeveye geçiş yap**|**Çağrı yığını** penceresindeki ilgili menü komutuyla aynı. Ancak, **Paralel Yığınlar** penceresinde bir yöntem birkaç çerçevede olabilir. Bu öğenin alt menüsünde istediğiniz çerçeveyi seçebilirsiniz. Yığın çerçevelerinden biri geçerli iş parçacığı içindeyse, alt menüde bu çerçeve varsayılan olarak seçilidir.|
|**Göreve git** veya **iş parçacığına git**|**Görev** veya **iş parçacığı** görünümüne geçiş yapar ve aynı yığın çerçevesini vurgulanmasını sağlar.|
|**Kaynak koduna git**|Kaynak kodu penceresinde ilgili konuma gider. |
|**Ayrıştırılmış koda git**|**Ayrıştırma** penceresindeki ilgili konuma gider.|
|**Dış kodu göster**|Dış kodu gösterir veya gizler.|
|**Onaltılı ekran**|Ondalık ve onaltılık görüntü arasında geçiş yapar.|
|**Kaynakta Iş parçacıklarını göster**|Kaynak kodu penceresinde iş parçacığının konumunu bayraklar. |
|**Sembol Yükleme Bilgisi**|**Sembol yükleme bilgileri** iletişim kutusunu açar.|
|**Sembol ayarları**|**Sembol ayarları** iletişim kutusunu açar. |

## <a name="threads-view"></a>İş parçacıkları görünümü

**Iş parçacıkları** görünümünde, geçerli iş parçacığının yığın çerçevesi ve çağrı yolu mavi renkle vurgulanır. İş parçacığının geçerli konumu Sarı oka göre gösterilir.

Geçerli yığın çerçevesini değiştirmek için farklı bir yönteme çift tıklayın. Bu işlem, seçtiğiniz yöntemin geçerli iş parçacığının veya başka bir iş parçacığının parçası olmasına bağlı olarak geçerli iş parçacığını de geçebilir.

**Iş parçacıkları** görünüm grafiği pencereye sığmayacak kadar büyükse, pencerede bir **kuşbakışı görünümü** denetimi görünür. Grafiğin farklı bölümlerine gitmek için denetimdeki çerçeveyi taşıyabilirsiniz.

Aşağıdaki çizimde, ana bilgisayardan yönetilen ve yerel kod geçişine giden bir iş parçacığı gösterilmektedir. Geçerli yöntemde altı iş parçacığı bulunur. Birisi Thread. Sleep 'e devam eder ve başka bir konsol. WriteLine ve daha sonra SyncTextWriter. WriteLine ile devam eder.

 ![Paralel Yığınlar penceresinde iş parçacıkları görünümü](../debugger/media/parallel_stack1.png "Paralel Yığınlar penceresinde iş parçacıkları görünümü")

Aşağıdaki tabloda, **Iş parçacıkları** görünümünün ana özellikleri açıklanmaktadır:

|Çıkma|Öğe adı|Açıklama|
|-|-|-|
|1|Çağrı yığını segmenti veya düğümü|Bir veya daha fazla iş parçacığı için bir dizi yöntem içerir. Çerçevede bağlantılı ok çizgileri yoksa çerçeve iş parçacıklarının tüm çağrı yolunu gösterir.|
|2|Mavi vurgu|Geçerli iş parçacığının çağrı yolunu gösterir.|
|3|Ok çizgileri|İş parçacığı (ler) için tüm çağrı yolunu oluşturmak üzere düğümleri bağlayın.|
|4|Düğüm üstbilgisi|Düğüm için işlem ve iş parçacığı sayısını gösterir.|
|5|Yöntem|Aynı yöntemde bir veya daha fazla yığın çerçevesini temsil eder.|
|6|Metodun araç ipucu|Bir yöntemin üzerine geldiğinizde görünür. **Iş parçacıkları** görünümünde, araç ipucu tüm iş parçacıklarını, **iş parçacıkları** penceresine benzer bir tabloda gösterir. |

## <a name="tasks-view"></a>Görevler görünümü
Uygulamanızda <xref:System.Threading.Tasks.Task?displayProperty=fullName> paralellik sağlamak için nesneler (yönetilen kod) veya `task_handle` nesneler (yerel kod) kullanılıyorsa, **Görevler** görünümü ' ne yararlanabilirsiniz. **Görevler** görünümü iş parçacıkları yerine görevlerin çağrı yığınlarını gösterir.

**Görevler** görünümü:

- Görevleri çalıştırmayan iş parçacıklarının çağrı yığınları gösterilmez.
- Görevleri çalıştıran iş parçacıklarının çağrı yığınları, görevler için en ilgili kareleri göstermek üzere en üstte ve altta görsel olarak kırpılmakta.
- Birden çok görev bir iş parçacığında olduğunda, bu görevlerin çağrı yığınları ayrı düğümlerde gösterilir.

Tüm çağrı yığınını görmek için, yığın çerçevesine sağ tıklayıp **Iş parçacığına git**' i seçerek **iş parçacıkları** görünümüne geri dönün.

Aşağıdaki çizimde en üstteki **Iş parçacığı** görünümü ve en altta karşılık gelen **Görevler** görünümü gösterilmektedir.

![İş parçacıkları ve görevler görünümleri](../debugger/media/parallel_threads-tasks.png "İş parçacıkları ve görevler görünümleri")

Ek bilgiler içeren bir araç ipucu göstermek için bir yöntemin üzerine gelin. **Görevler** görünümünde, araç ipucu görevler penceresine benzer bir tablodaki **tüm görevleri gösterir** .

Aşağıdaki görüntüde, en üstteki **Iş parçacıkları** görünümündeki bir yöntemin araç ipucu ve en altta karşılık gelen **Görevler** görünümü gösterilmektedir.

![İş parçacıkları ve görevler araç ipuçları](../debugger/media/parallel_threads-tasks-tooltips.png "İş parçacıkları ve görevler araç ipuçları")

## <a name="method-view"></a>Yöntem görünümü
Herhangi bir **Iş parçacığı** görünümü veya **Görevler** görünümünden, araç çubuğunda **geçiş yöntemi görünümü** simgesini seçerek geçerli yöntemde grafiği özetleyebilirsiniz. **Yöntem görünümü** , ya da çağıran ya da geçerli yöntem tarafından çağrılan tüm iş parçacıklarında tüm yöntemleri gösterir. Aşağıdaki çizimde, sol taraftaki ve doğrudan **Yöntem görünümündeki** **iş parçacıkları** görünümünde aynı bilgilerin nasıl göründüğü gösterilmektedir.

![İş parçacıkları görünümü ve Yöntem görünümü](../debugger/media/parallel_methodview.png "İş parçacıkları görünümü ve Yöntem görünümü")

Yeni bir yığın çerçevesine geçiş yaparsanız, bu yöntemi geçerli yöntem ve **Yöntem görünümü** , yeni yöntemin tüm çağıranlarını ve erimlerini gösterir. Bu yöntem, yöntemin çağrı yığınlarında görünüp görünmediğini bağlı olarak görünümde bazı iş parçacıklarının görünmesine veya görünmemesine neden olabilir. Çağrı yığını görünümüne dönmek için, **Yöntem görünümü** araç çubuğu simgesini yeniden seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Çok iş parçacıklı bir uygulamada hata ayıklamaya başlayın](../debugger/get-started-debugging-multithreaded-apps.md)
- [İzlenecek yol: Paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)
- [Paralel programlama](/dotnet/standard/parallel-programming/index)
- [Görevler penceresini kullanma](../debugger/using-the-tasks-window.md)
- [Görev sınıfı](../extensibility/debugger/task-class-internal-members.md)
