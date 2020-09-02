---
title: 'Nasıl yapılır: Iş parçacıkları penceresini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da41524fcb231ea399dbbd2a2904afd935e5c4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824253"
---
# <a name="how-to-use-the-threads-window"></a>Nasıl Yapılır: İş Parçacıkları Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Iş parçacıkları** penceresinde, hata ayıklaması yaptığınız uygulamada iş parçacıklarını inceleyebilir ve bunlarla çalışabilirsiniz.  
  
 **Iş parçacıkları** penceresi, her satırın uygulamanızdaki bir iş parçacığını temsil ettiği bir tablo içerir. Varsayılan olarak, tabloda uygulamanızdaki tüm iş parçacıkları listelenir, ancak listeyi yalnızca ilgilendiğiniz iş parçacıklarını gösterecek şekilde filtreleyebilirsiniz. Her sütun farklı türde bilgiler içerir. Ayrıca, bazı sütunları gizleyebilirsiniz. Tüm sütunları görüntülediğinizde, soldan sağa aşağıdaki bilgiler görüntülenir:  
  
- Özel dikkat etmek istediğiniz bir iş parçacığını işaretleyecek bayrak sütunu. Bir iş parçacığını işaretleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bayrak Ekle ve Iş parçacıklarını kaldır](../debugger/how-to-flag-and-unflag-threads.md).  
  
- Sarı okun etkin bir iş parçacığını gösterdiği etkin iş parçacığı sütunu. Bir okun ana hattı, yürütmenin hata ayıklayıcıya bölünmesinin gerçekleştiği iş parçacığını gösterir.  
  
- Her bir iş parçacığının kimlik numarasını içeren **ID** sütunu.  
  
- Yönetilen iş parçacıkları için yönetilen kimlik numaralarını içeren **YÖNETILEN kimlik** sütunu.  
  
- İş parçacıklarını Kullanıcı arabirimi iş parçacıkları, uzak yordam çağrısı işleyicileri veya çalışan iş parçacıkları olarak kategorilere ayırır **Kategori** sütunu. Özel bir kategori, uygulamanın ana iş parçacığını tanımlar.  
  
- Her bir iş parçacığını ada göre (veya olarak) tanımlayan **ad** sütunu \<No Name> .  
  
- İş parçacığının nerede çalıştığını gösteren **konum** sütunu. Bu konumu, iş parçacığının tam çağrı yığınını göstermek için genişletebilirsiniz.  
  
- Sistemin her bir iş parçacığına atadığı önceliği veya önceliği içeren **Öncelik** sütunu.  
  
- Genellikle gizlenen gelişmiş bir sütun olan **benzeşim maskesi** sütunu. Bu sütunda her iş parçacığının işlemci benzeşim maskesi gösterilmektedir. Çok işlemcili bir sistemde, benzeşim maskesi bir iş parçacığının hangi işlemcilerde çalıştırılabileceğini belirler.  
  
- Askıya alınma sayısı içeren, **askıya alınan Count** sütunu. Bu sayı bir iş parçacığının çalıştırılıp çalıştırılamayacağını belirler. Askıya alınan sayım hakkında açıklama için, bu konunun devamındaki "Iş parçacıklarını dondurma ve Thakelebek" bölümüne bakın.  
  
- Her bir iş parçacığının ait olduğu işlemi içeren **Işlem adı** sütunu. Bu sütun, birden çok işlemde hata ayıklarken yararlı olabilir, ancak genellikle gizlidir.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Çalışma parçacıkları penceresini kesme modunda veya çalıştırma modunda görüntüleme  
  
- **Hata Ayıkla** menüsünde **Windows**' un üzerine gelin ve ardından **iş parçacıkları**' na tıklayın.  
  
### <a name="to-display-or-hide-a-column"></a>Bir sütunu göstermek veya gizlemek için  
  
- **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda, **sütunlar**' a tıklayın, ardından göstermek veya gizlemek istediğiniz sütunun adını seçin veya temizleyin.  
  
### <a name="to-switch-the-active-thread"></a>Etkin iş parçacığını değiştirmek için  
  
- Aşağıdaki adımlardan birini gerçekleştirin:  
  
  - Herhangi bir iş parçacığına çift tıklayın.  

  - Bir iş parçacığına sağ tıklayıp **Iş parçacığına geç ' e**tıklayın.  

    Yeni etkin iş parçacığının yanında sarı ok görünür. Bir okun gri ana hattı, yürütmenin hata ayıklayıcıya bölünmesinin gerçekleştiği iş parçacığını tanımlar.  
  
## <a name="grouping-and-sorting-threads"></a>Iş parçacıklarını gruplandırma ve sıralama  
 İş parçacıklarını gruplandırdığınızda her grup için tabloda bir başlık görünür. Başlık, "çalışan Iş parçacığı" veya "bayrak edilmemiş Iş parçacıkları" gibi bir grup açıklaması ve bir ağaç denetimi içerir. Her bir grubun üye iş parçacıkları grup başlığının altında görünür. Bir grup için üye iş parçacıklarını gizlemek istiyorsanız, ağaç denetimini grubunu daraltmak için kullanabilirsiniz.  
  
 Gruplandırma sıralamaya göre öncelikli olduğundan, iş parçacıklarını kategoriye göre gruplandırabilir, örneğin, bunları her bir kategorinin içindeki KIMLIĞE göre sıralayabilirsiniz.  
  
#### <a name="to-sort-threads"></a>İş parçacıklarını sıralamak için  
  
1. **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda herhangi bir sütunun en üstünde bulunan düğmeye tıklayın.  
  
     İş parçacıkları artık bu sütundaki değerlere göre sıralanır.  
  
2. Sıralama düzenini tersine çevirmek istiyorsanız, tekrar aynı düğmeye tıklayın.  
  
     Listenin en üstünde görünen iş parçacıkları artık altta görünür.  
  
#### <a name="to-group-threads"></a>İş parçacıklarını gruplandırmak için  
  
- **Iş parçacıkları** penceresi araç çubuğunda **Gruplandırma ölçütü** listesine tıklayın ve sonra iş parçacıklarını gruplamak istediğiniz ölçütlere tıklayın.  
  
#### <a name="to-sort-threads-within-groups"></a>Grupları içindeki iş parçacıklarını sıralamak için  
  
1. **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda, **Gruplandır** listesine tıklayın ve sonra iş parçacıklarını gruplamak istediğiniz ölçütlere tıklayın.  
  
2. **Iş parçacıkları** penceresinde herhangi bir sütunun en üstünde bulunan düğmeye tıklayın.  
  
     İş parçacıkları artık bu sütundaki değerlere göre sıralanır.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Tüm grupları genişletmek veya daraltmak için  
  
- **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda **grupları Genişlet** veya **grupları Daralt**' ı tıklatın.  
  
## <a name="searching-for-specific-threads"></a>Belirli Iş parçacıkları aranıyor  
 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]' De, belirtilen bir dizeyle eşleşen iş parçacıkları için arama yapabilirsiniz. **İş parçacıkları penceresinde iş** parçacıkları aradığınızda, pencerede herhangi bir sütunda arama dizesiyle eşleşen tüm iş parçacıkları görüntülenir. Bu bilgiler, **konum** sütununda çağrı yığınının en üstünde görünen iş parçacığı konumunu içerir. Ancak, varsayılan olarak, tam çağrı yığını aranmaz.  
  
#### <a name="to-search-for-specific-threads"></a>Belirli iş parçacıklarını aramak için  
  
- **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda, **arama** kutusuna gidin ve şunlardan birini yapın:  
  
  - Bir arama dizesi yazın ve ENTER tuşuna basın.  

    \- veya  

  - **Arama** kutusunun yanındaki aşağı açılan listeye tıklayın ve önceki aramadan bir arama dizesi seçin.  
  
- Seçim Aramanıza tam çağrı yığınını eklemek için **arama yığını ara**' yı seçin.  
  
## <a name="freezing-and-thawing-threads"></a>Iş parçacıklarını dondurma ve çözülmüş  
 Bir iş parçacığını dondurursanız, kaynaklar kullanılabilir olsa bile, sistem iş parçacığının yürütülmesini başlatmaz.  
  
 Yerel kodda, Windows işlevlerini çağırarak veya, `SuspendThread` `ResumeThread` [CWinThread:: SuspendThread](https://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) ve [CWinThread:: ResumeThread](https://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5)işlevlerini çağırarak iş parçacıklarını askıya alabilir veya sürdürebilirsiniz. `SuspendThread`Veya `ResumeThread` öğesini çağırırsanız, **iş parçacıkları** penceresinde görüntülenen *askıya alınmış sayımı*değiştirirsiniz. Ancak, yerel bir iş parçacığını dondurursanız ya da çözme yaparsanız, askıya alınma sayısını değiştirmeyin. Yerel kodda, bir iş parçacığı thaçar ve askıya alınmış sıfır sayısına sahip olmadığı takdirde yürütülemez.  
  
 Yönetilen kodda, bir iş parçacığını dondurmak veya thanmek, askıya alınma sayısını değiştirir. Yönetilen kodda, dondurulmuş bir iş parçacığının askıda sayısı 1 ' dir. Yerel kodda, dondurulmuş bir iş parçacığı bir çağrı tarafından askıya alınmamışsa, askıya alınan 0 sayısına sahiptir `SuspendThread` .  
  
> [!NOTE]
> Yerel koddan yönetilen koda yapılan bir çağrıda hata ayıkladığınızda, yönetilen kod, kendisini çağıran yerel kodla aynı fiziksel iş parçacığında çalışır. Yerel iş parçacığını askıya almak veya dondurmak, yönetilen kodu da dondurur.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Bir iş parçacığının yürütülmesini dondurmak veya çözme  
  
- **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda, parçacıkları veya **çözme iş**parçacıklarını **Dondur** ' ı tıklatın.  
  
     Bu eylem yalnızca **Iş parçacıkları** penceresinde seçili olan iş parçacıklarını etkiler.  
  
## <a name="displaying-flagged-threads"></a>Bayraklı Iş parçacıklarını görüntüleme  
 Özel dikkat sağlamak istediğiniz bir iş parçacığını, **Iş parçacıkları** penceresinde bir simge ile işaretleyerek işaretleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bayrak ve bayrak kaldırma Iş parçacıkları](../debugger/how-to-flag-and-unflag-threads.md). Iş parçacıkları penceresinde, tüm iş parçacıklarını veya yalnızca bayraklı iş parçacıklarını görüntülemeyi tercih edebilirsiniz.  
  
#### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını göstermek için  
  
- **Iş parçacıkları** penceresinin sol üst köşesindeki bayrak düğmesini seçin.  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>Iş parçacığı çağrı yığınlarını görüntüleme ve çerçeveler arasında geçiş yapma  
 Çok iş parçacıklı bir programda, her iş parçacığının kendi çağrı yığını vardır. **Iş parçacıkları** penceresi, bu yığınları görüntülemek için kullanışlı bir yol sağlar.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Bir iş parçacığının çağrı yığınını görüntülemek için  
  
- **Konum** sütununda, iş parçacığı konumunun yanındaki ters üçgeni tıklatın.  
  
     Konum, iş parçacığının çağrı yığınını gösterecek şekilde genişler.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Tüm iş parçacıklarının çağrı yığınlarını görüntülemek veya daraltmak için  
  
- **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda, **çağrı yığınlarını Genişlet** veya **çağrı yığınlarını Daralt**' ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [İzlenecek Yol: Çok İş Parçacıklı Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-multithreaded-application.md)
