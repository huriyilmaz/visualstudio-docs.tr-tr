---
title: Hata Ayıklayıcıdaki iş parçacıklarını görüntüle | Microsoft Docs
description: İş parçacıklarını incelemek ve denetlemek için Iş parçacıklarını kullanın. İş parçacıklarını gruplandırabilir, sıralayabilir, düzenleyebilir, dondurabilir ve arayabilir, sütunları seçebilir ve çağrı yığınlarını görüntüleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd11e722886b77e9faaace768cc30a74c759903f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884214"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>Iş parçacıkları penceresini kullanarak Visual Studio hata ayıklayıcısındaki iş parçacıklarını görüntüleme (C#, Visual Basic, C++)
**Iş parçacıkları** penceresinde, hata ayıklaması yaptığınız uygulamadaki iş parçacıklarını inceleyebilir ve bunlarla çalışabilirsiniz. **Iş parçacıkları** penceresini kullanma hakkında adım adım yönergeler için bkz. [Izlenecek yol: iş parçacıkları penceresini kullanarak hata ayıklama](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>İş Parçacıkları penceresini kullanma
 **Iş parçacıkları** penceresi, her satırın uygulamanızda ayrı bir iş parçacığını açıkladığı bir tablo içerir. Varsayılan olarak, tabloda uygulamanızdaki tüm iş parçacıkları listelenir, ancak listeyi yalnızca ilgilendiğiniz iş parçacıklarını gösterecek şekilde filtreleyebilirsiniz. Her sütunda farklı türde bilgiler açıklanmaktadır. Ayrıca, bazı sütunları gizleyebilirsiniz. Tüm sütunları görüntülediğinizde, soldan sağa aşağıdaki sütunlar görüntülenir:

- **Bayrak**: Bu etiketsiz sütunda, özel dikkat etmek istediğiniz bir iş parçacığını işaretleyebilirsiniz. Bir iş parçacığını işaretleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bayrak Ekle ve iş parçacıklarını kaldır](../debugger/how-to-flag-and-unflag-threads.md).

- **Geçerli iş parçacığı**: Bu etiketlenmemiş sütunda, sarı ok geçerli iş parçacığını gösterir. Ok ana hattı geçerli olmayan bir iş parçacığının geçerli hata ayıklayıcı bağlamını gösterir.

- **ID**: her bir iş parçacığının kimlik numarasını görüntüler.

- **YÖNETILEN kimlik**: yönetilen iş parçacıkları için yönetilen tanımlama numaralarını görüntüler.

- **Kategori**: Kullanıcı arabirimi iş parçacıkları, uzak yordam çağrısı işleyicileri veya çalışan iş parçacıkları olarak iş parçacıklarının kategorisini görüntüler. Özel bir kategori, uygulamanın ana iş parçacığını tanımlar.

- **Ad**: her bir iş parçacığını ada göre veya olarak tanımlar \<No Name> .

- **Konum**: iş parçacığının nerede çalıştığını gösterir. Bu konumu, iş parçacığının tam çağrı yığınını göstermek için genişletebilirsiniz.

- **Öncelik**: sistemin her bir iş parçacığına atadığı önceliği veya önceliği görüntüleyen Gelişmiş bir sütun (varsayılan olarak gizlidir).

- **Benzeşim maskesi**: her bir iş parçacığının işlemci benzeşim maskesini gösteren gelişmiş bir sütun (varsayılan olarak gizlidir). Çok işlemcili bir sistemde, benzeşim maskesi bir iş parçacığının hangi işlemcilerde çalıştırılabileceğini belirler.

- **Askıya alınan sayı**: askıya alınan sayıyı görüntüleyen Gelişmiş bir sütun (varsayılan olarak gizlidir). Bu sayı bir iş parçacığının çalıştırılıp çalıştırılamayacağını belirler. Askıya alınan sayımlar hakkında daha fazla bilgi için bkz. [iş parçacıklarını dondurma ve çözme](#freeze-and-thaw-threads).

- **Işlem adı**: her bir iş parçacığının ait olduğu işlemi görüntüleyen Gelişmiş bir sütun (varsayılan olarak gizlidir). Bu sütundaki veriler, birçok işlem hata ayıklaması yaparken yararlı olabilir.

- **Işlem kimliği**: her bir iş parçacığının ait olduğu işlem kimliğini görüntüleyen Gelişmiş bir sütun (varsayılan olarak gizlidir).

- **Aktarım niteleyicisi**: hata ayıklayıcının bağlı olduğu makineyi benzersiz olarak tanımlayan gelişmiş bir sütun (varsayılan olarak gizlidir).

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Çalışma parçacıkları penceresini kesme modunda veya çalıştırma modunda görüntüleme

- Visual Studio hata ayıklama modundayken **hata ayıklama** menüsünü seçin, **Windows**' un üzerine gelin ve **iş parçacıkları**' nı seçin.

### <a name="to-display-or-hide-a-column"></a>Bir sütunu göstermek veya gizlemek için

- **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda **sütunlar**' ı seçin. Ardından, göstermek veya gizlemek istediğiniz sütunun adını seçin veya temizleyin.

## <a name="display-flagged-threads"></a>Bayraklı iş parçacıklarını görüntüle
 Özel dikkat sağlamak istediğiniz bir iş parçacığını, **Iş parçacıkları** penceresinde bir simge ile işaretleyerek işaretleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bayrak ve bayrak kaldırma iş parçacıkları](../debugger/how-to-flag-and-unflag-threads.md). **Iş parçacıkları** penceresinde, tüm iş parçacıklarını veya yalnızca bayraklı iş parçacıklarını görüntülemeyi tercih edebilirsiniz.

### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını göstermek için

- Yalnızca **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda **bayraklı iş parçacıklarını göster** ' i seçin. (Soluk ise, önce bazı iş parçacıklarını bayrakla ayarlamanız gerekecektir.)

## <a name="freeze-and-thaw-threads"></a>İş parçacıklarını dondurma ve çözme
 Bir iş parçacığını dondurursanız, kaynaklar kullanılabilir olsa bile, sistem iş parçacığının yürütülmesini başlatılmaz.

 Yerel kodda, Windows işlevlerini ve çağırarak iş parçacıklarını askıya alabilir veya sürdürebilirsiniz `SuspendThread` `ResumeThread` . Ya da, [CWinThread:: SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) ve [CWinThread:: ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread)MFC işlevlerini çağırın. `SuspendThread`Veya `ResumeThread` öğesini çağırırsanız, **iş parçacıkları** penceresinde gösterilen *askıya alınan sayım* değiştirilir. Yerel bir iş parçacığını dondurursanız veya kaldırırsanız, askıda olan sayı değişmez. Bir iş parçacığı, thaçar ve askıya alınmış sıfır sayısına sahip olmadığı müddetçe yerel kodda yürütülemez.

 Yönetilen kodda, bir iş parçacığını dondurma veya çözme sırasında askıda bekleyen sayı değişir. Yönetilen koddaki bir iş parçacığını dondurursanız, askıya alınma sayısı 1 ' dir. Yerel koddaki bir iş parçacığını dondurursanız, çağrıyı kullanmadığınız takdirde, askıya alınma sayısı 0 olur `SuspendThread` .

> [!NOTE]
> Yerel koddan yönetilen koda yapılan bir çağrıda hata ayıkladığınızda, yönetilen kod, kendisini çağıran yerel kodla aynı fiziksel iş parçacığında çalışır. Yerel iş parçacığını askıya almak veya dondurmak, yönetilen kodu da dondurur.

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Bir iş parçacığının yürütülmesini dondurmak veya çözme

- **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda, **iş parçacıklarını dondur** veya **çözme iş** parçacıklarını seçin.

     Bu eylem yalnızca **Iş parçacıkları** penceresinde seçili olan iş parçacıklarını etkiler.

### <a name="switch-to-another-thread"></a>Başka bir iş parçacığına geç

Sarı ok geçerli iş parçacığını (ve yürütme işaretçisinin konumunu) gösterir. Küme kuyruğu olan yeşil ok, geçerli olmayan bir iş parçacığının geçerli hata ayıklayıcı bağlamına sahip olduğunu gösterir.

#### <a name="to-switch-to-another-thread"></a>Başka bir iş parçacığına geçiş yapmak için

- Aşağıdaki adımlardan birini izleyin:

  - Herhangi bir iş parçacığına çift tıklayın.

  - Bir iş parçacığına sağ tıklayıp **Iş parçacığına geç**' i seçin.

## <a name="group-and-sort-threads"></a>İş parçacıklarını gruplandırma ve sıralama
 İş parçacıklarını gruplandırdığınızda her grup için tabloda bir başlık görünür. Başlık, **çalışan Iş parçacığı** veya **bayrak edilmemiş iş parçacıkları** gibi bir grup açıklaması ve bir ağaç denetimi içerir. Her bir grubun üye iş parçacıkları grup başlığının altında görünür. Bir grup için üye iş parçacıklarını gizlemek istiyorsanız, Grup daraltmak için ağaç denetimini kullanın.

 Gruplandırma sıralamaya göre öncelikli olduğundan, iş parçacıklarını kategoriye göre gruplandırabilir, örneğin, bunları her bir kategorinin içindeki KIMLIĞE göre sıralayabilirsiniz.

### <a name="to-sort-threads"></a>İş parçacıklarını sıralamak için

1. **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda herhangi bir sütunun en üstünde bulunan düğmeyi seçin.

     İş parçacıkları artık bu sütundaki değerlere göre sıralanır.

2. Sıralama düzenini tersine çevirmek istiyorsanız, tekrar aynı düğmeyi seçin.

     Listenin en üstünde görünen iş parçacıkları artık altta görünür.

### <a name="to-group-threads"></a>İş parçacıklarını gruplandırmak için

- **Iş parçacıkları** penceresi araç çubuğunda **Gruplandırma ölçütü** listesini seçin ve sonra iş parçacıklarını gruplandırmak istediğiniz ölçütü seçin.

### <a name="to-sort-threads-within-groups"></a>Grupları içindeki iş parçacıklarını sıralamak için

1. **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda, **Gruplandır** listesini seçin ve sonra iş parçacıklarını gruplandırmak istediğiniz ölçütü seçin.

2. **Iş parçacıkları** penceresinde herhangi bir sütunun en üstünde bulunan düğmeyi seçin.

     İş parçacıkları artık bu sütundaki değerlere göre sıralanır.

### <a name="to-expand-or-collapse-all-groups"></a>Tüm grupları genişletmek veya daraltmak için

- **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda **grupları Genişlet** veya **grupları Daralt**' ı seçin.

## <a name="search-for-specific-threads"></a>Belirli iş parçacıklarını arayın
 **Iş parçacıkları** penceresinde belirtilen dizeyle eşleşen iş parçacıkları için arama yapabilirsiniz. İş parçacığı ararken, pencerede herhangi bir sütunda arama dizesiyle eşleşen tüm iş parçacıkları görüntülenir. Bu bilgiler, **konum** sütununda çağrı yığınının en üstünde görünen iş parçacığı konumunu içerir. Varsayılan olarak, tam çağrı yığını aranmaz.

### <a name="to-search-for-specific-threads"></a>Belirli iş parçacıklarını aramak için

1. **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda, **arama** kutusuna gidin ve şunlardan birini yapın:

     - Bir arama dizesi girin ve ardından **ENTER** tuşuna basın.

     \- veya

     - **Arama** kutusunun yanındaki açılan listeyi seçin ve önceki aramadan bir arama dizesi seçin.

2. Seçim Aramanıza tam çağrı yığınını eklemek için **arama yığını ara**' yı seçin.

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>İş parçacığı çağrı yığınlarını görüntüle ve çerçeveler arasında geçiş yap
Çok iş parçacıklı bir programda, her iş parçacığının kendi çağrı yığını vardır. **Iş parçacıkları** penceresi, bu yığınları görüntülemek için kullanışlı bir yol sağlar.

> [!TIP]
> Her iş parçacığının çağrı yığınının görsel temsili için [Paralel Yığınlar](../debugger/get-started-debugging-multithreaded-apps.md) penceresini kullanın.

### <a name="to-view-the-call-stack-of-a-thread"></a>Bir iş parçacığının çağrı yığınını görüntülemek için

- **Konum** sütununda, iş parçacığı konumunun yanındaki ters üçgeni seçin.

     Konum, iş parçacığının çağrı yığınını gösterecek şekilde genişler.

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Tüm iş parçacıklarının çağrı yığınlarını görüntülemek veya daraltmak için

- **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda, **çağrı yığınlarını Genişlet** veya **çağrı yığınlarını Daralt**' ı seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Çok iş parçacıklı uygulamaların hatalarını ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Çok iş parçacıklı uygulamalarda hata ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md)
