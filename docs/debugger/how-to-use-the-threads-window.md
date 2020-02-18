---
title: Çok iş parçacıklı bir uygulamada hata ayıklama
description: Visual Studio 'da Iş parçacıkları penceresini ve hata ayıklama konumu araç çubuğunu kullanarak hata ayıkla
ms.date: 02/14/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb7b7850d8d7582110152d248683f89981933215
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416379"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>İzlenecek yol: Iş parçacıkları penceresini kullanarak çok iş parçacıklı birC#uygulamada hata ayıklama C++(, Visual Basic,)

Birçok Visual Studio Kullanıcı arabirimi öğesi çok iş parçacıklı uygulamalarda hata ayıklamanıza yardımcı olur. Bu makalede kod Düzenleyicisi penceresi, **hata ayıklama konumu** araç çubuğu ve **iş parçacıkları** penceresindeki çok iş parçacıklı hata ayıklama özellikleri tanıtılmaktadır. Çok iş parçacıklı [uygulamalarda hata ayıklamaya](../debugger/get-started-debugging-multithreaded-apps.md)yönelik diğer araçlar hakkında daha fazla bilgi için bkz

Bu öğreticiyi tamamlamak yalnızca birkaç dakika sürer ve çok iş parçacıklı uygulamalarda hata ayıklama hakkında temel bilgileri tamamladığınızda tercihinize.

## <a name="create-a-multithreaded-app-project"></a>Çok iş parçacıklı uygulama projesi oluşturma

Bu öğreticide kullanmak üzere aşağıdaki çok iş parçacıklı uygulama projesini oluşturun:

1. Visual Studio 'Yu açın ve yeni bir proje oluşturun.

   ::: moniker range=">=vs-2019"

   Başlangıç penceresi açık değilse **dosya** > **Başlangıç penceresi**' ni seçin.

   Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, dil **C#** listesini **C++** seçin ve ardından platform listesinden **Windows** ' u seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması (.NET Core)** veya için C++ **konsol uygulaması** şablonu ' nu seçin ve ardından **İleri**' yi seçin.

   > [!NOTE]
   > Doğru şablonu görmüyorsanız **Araçlar** ve özellikler al > ' a gidin. Visual Studio yükleyicisi açan **Araçlar ve Özellikler...** ' a gidin. **.Net masaüstü geliştirme** veya iş yükü **ile C++ masaüstü geliştirmeyi** seçin ve ardından **Değiştir**' i seçin.

   **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *MyThreadWalkthroughApp* yazın veya girin. Ardından **Oluştur**' u seçin.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde aşağıdakileri seçin:

   - Bir C# uygulama için, **C#Visual**altında **Windows Masaüstü**' nün ardından orta bölmedeki **konsol uygulaması (.NET Framework)** seçeneğini belirleyin.
   - Bir C++ uygulama için, **C++Visual**altında **Windows Masaüstü**' nün ardından **Windows konsol uygulaması**' nı seçin.

   **Konsol uygulaması (.NET Core)** C++veya için **konsol** uygulaması projesi şablonu görmüyorsanız, Visual Studio Yükleyicisi açan araçlar **ve Özellikler al** > **Araçlar** ' a gidin. **.Net masaüstü geliştirme** veya iş yükü **ile C++ masaüstü geliştirmeyi** seçin ve ardından **Değiştir**' i seçin.

   Ardından, *MyThreadWalkthroughApp* gibi bir ad yazın ve **Tamam**' a tıklayın.

   **Tamam**’ı seçin.
   ::: moniker-end

   Yeni bir konsol projesi görüntülenir. Proje oluşturulduktan sonra bir kaynak dosya görüntülenir. Seçtiğiniz dile bağlı olarak, kaynak dosya *program.cs*, *MyThreadWalkthroughApp. cpp*veya *Module1. vb*olarak adlandırılabilir.

1. Kaynak dosyadaki kodu, çok C# [iş parçacıklı uygulamalarda hata ayıklamayı kullanmaya](../debugger/get-started-debugging-multithreaded-apps.md)başlayın bölümünde veya C++ örnek kodla değiştirin.

1. **Tümünü kaydet** > **Dosya** ' yı seçin.

## <a name="start-debugging"></a>Hata Ayıklamayı Başlat

1. Kaynak kodda aşağıdaki satırları bulun:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Sol cilt paya tıklayarak veya satırı seçip **F9**tuşuna basarak `Console.WriteLine();` satırında bir kesme noktası ayarlayın.

   Kesme noktası, kod satırının yanındaki sol cilt alanında kırmızı bir daire olarak görünür.

1. Hata **ayıklamayı başlatmak** > **Hata Ayıkla** ' yı seçin veya **F5**tuşuna basın.

   Uygulama hata ayıklama modunda başlar ve kesme noktasında duraklatılır.

1. Kesme modundayken, **Windows** > **Iş parçacıkları** > **Hata Ayıkla** ' yı seçerek **iş parçacıkları** penceresini açın. **Iş parçacıklarını** ve diğer hata ayıklama pencerelerini açmak veya görmek için bir hata ayıklama oturumunda olmanız gerekir.

## <a name="examine-thread-markers"></a>İş parçacığı işaretçilerini İncele

1. Kaynak kodda `Console.WriteLine();` satırını bulun.

   1. **Iş parçacıkları** penceresinde sağ tıklayın ve menüden kaynak ![bölümünde](../debugger/media/dbg-multithreaded-show-threads.png "Threadişaretleyici") iş **parçacıklarını göster ' i seçin.**

   Kaynak kodu satırının yanındaki cilt payı artık *iş parçacığı işaretçisi* simgesi ![iş parçacığı işaretleyicisi](../debugger/media/dbg-thread-marker.png "İş parçacığı Işaretçisi")görüntülüyor. İş parçacığı işaretçisi, bir iş parçacığı bu konuma durdurulduğunu gösterir. Konumda birden fazla durdurulmuş iş parçacığı varsa, ![birden çok iş](../debugger/media/dbg-multithreaded-show-threads.png "çoklu iş parçacıkları") parçacığı simgesi görüntülenir.

1. İşaretçi iş parçacığı işaret gelin. Durdurulan iş parçacığı veya iş parçacıkları için ad ve iş parçacığı KIMLIĞI numarasını gösteren bir veri Ipucu görünür. İş parçacığı adları `<No Name>`olabilir.

   >[!TIP]
   >İsimsiz iş parçacıklarını belirlemenize yardımcı olmak için bunları **Iş parçacıkları** penceresinde yeniden adlandırabilirsiniz. İş parçacığına sağ tıklayıp **Yeniden Adlandır**' ı seçin.

1. Kısayol menüsünde kullanılabilir seçenekleri görmek için kaynak kodundaki iş parçacığı işaretine sağ tıklayın.

## <a name="flag-and-unflag-threads"></a>İş parçacıklarını bayrakla işaretleme ve işareti geri alma

Özel dikkat etmek istediğiniz iş parçacıklarını izlemek için iş parçacıklarına bayrak atayabilirsiniz.

Kaynak kodu düzenleyicisinden veya **Iş parçacıkları** penceresinden iş parçacıklarını bayrak ve işaretini kaldır. **Hata ayıklama konumu** veya **iş parçacıkları** penceresi araç çubuklarından yalnızca bayraklı iş parçacıklarını mı yoksa tüm iş parçacıklarını mı görüntüleneceğini seçin. Herhangi bir konumdan yapılan seçimler tüm konumları etkiler.

### <a name="flag-and-unflag-threads-in-source-code"></a>Kaynak kodundaki iş parçacıklarını işaretle ve işaretini kaldır

1. Hata ayıklama **konumu > ** **görüntüle** > **araç** çubuğunu seçin **.** Ayrıca araç çubuğu alanına sağ tıklayıp **hata ayıklama konumu**' nu seçebilirsiniz.

1. **Hata ayıklama konumu** araç çubuğunda üç alan vardır **: işlem**, **iş parçacığı**ve **yığın çerçevesi**. **Iş parçacığı** listesini açılır ve kaç iş parçacığı olduğunu Note. **Iş parçacığı** listesinde, yürütülmekte olan iş parçacığı bir **>** simgesiyle işaretlenir.

1. Kaynak kodu penceresinde, cilt payında bir iş parçacığı işaretleyici simgesinin üzerine gelin ve veri Ipucunda bayrak simgesini (veya boş bayrak simgelerinden birini) seçin. Bayrak simgesi kırmızıya döner.

   Ayrıca, bir iş parçacığı işaretleyici simgesine sağ tıklayıp **bayrak**' ın üzerine gelin ve kısayol menüsünden bayrak eklenecek bir iş parçacığı seçebilirsiniz.

1. **Hata ayıklama konumu** araç çubuğunda, **iş parçacığı** alanının sağında **yalnızca bayraklı Iş parçacıklarını göster** simgesi ![bayraklı iş parçacıklarını göster](../debugger/media/dbg-threads-show-flagged.png "Bayraklı Iş parçacıklarını göster")' i seçin. Bir veya daha fazla iş parçacığı işaretlenmediği takdirde simgenin gri renkte olması önerilir.

   Araç çubuğundaki **Iş parçacığı** açılır listesinde yalnızca bayraklı iş parçacığı görüntülenir. Tüm iş parçacıklarını yeniden göstermek için, **yalnızca bayraklı Iş parçacıklarını göster** simgesini yeniden seçin.

   >[!TIP]
   >Bazı iş parçacıklarını işaretledikten sonra imlecinizi kod düzenleyicisine yerleştirebilir, sağ tıklayıp **bayraklı Iş parçacıklarını Imlece Çalıştır**' ı seçebilirsiniz. İşaretlenen tüm iş parçacıklarının ulaşabileceği kodu seçtiğinizden emin olun. **Bayraklı Iş parçacıklarını Imlece Çalıştır** , seçilen kod satırında iş parçacıklarını duraklatıp, [iş parçacıklarını dondurarak ve thanerek](#bkmk_freeze)yürütme sırasını denetlemeyi kolaylaştırır.

1. Şu anda yürütülmekte olan iş parçacığının bayraklı veya işaretlenmeyen durumunu değiştirmek için, **yalnızca bayraklı Iş parçacıklarını göster** düğmesinin solunda bulunan **geçerli Iş parçacığı bayrak durumu** araç çubuğu düğmesini seçerek tek bayrak ' i seçin. Geçerli iş parçacığına bayrak eklemek, yalnızca bayraklı iş parçacıkları gösterilirken geçerli iş parçacığını bulmak için yararlıdır.

1. Bir iş parçacığının bayrağını kaldırmak için kaynak kodundaki iş parçacığı işaretçisinin üzerine gelin ve kırmızı bayrak simgesini seçerek temizleyin veya iş parçacığı işaretine sağ tıklayıp **bayrağı kaldır**' ı seçin.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Iş parçacıkları penceresindeki bayrakları işaretle ve Kaldır

**Iş parçacıkları** penceresinde, bayraklı iş parçacıklarının yanında kırmızı bayrak simgeleri vardır ve gösterilirse bayraklı iş parçacıkları boş simgelere sahiptir.

![İş parçacıkları penceresi](../debugger/media/dbg-threads-window.png "İş parçacıkları penceresi")

Geçerli durumuna bağlı olarak, iş parçacığı durumunu bayraklı veya bayraklı olarak değiştirmek için bir bayrak simgesi seçin.

Ayrıca, kısayol menüsünden bir satıra sağ tıklayıp **bayrak**, bayrağı **Kaldır**veya **tüm iş parçacıklarını işaretini kaldır** ' ı seçebilirsiniz.

**Iş parçacıkları** penceresi araç çubuğu aynı zamanda **yalnızca bayraklı iş parçacıklarını göster** düğmesine sahiptir, bu iki bayrak simgelerinden biri olan righthand. **Hata ayıklama konumu** araç çubuğundaki düğmeyle aynı şekilde çalışacaktır ve iki düğme de her iki konumdaki görüntüyü denetler.

### <a name="other-threads-window-features"></a>Diğer Iş parçacıkları penceresi özellikleri

**Iş parçacıkları** penceresinde, herhangi bir sütunun üst bilgisini seçerek iş parçacıklarını bu sütuna göre sıralayın. Sıralama düzenini tersine çevirmek için yeniden seçin. Tüm iş parçacıkları gösteriyorsa, bayrak simgesi sütunu seçildiğinde iş parçacıkları bayraklı veya işaretlenmeyen duruma göre sıralanır.

**Iş parçacıkları** penceresinin (üst bilgi içermeyen) Ikinci sütunu **geçerli iş parçacığı** sütunudur. Bu sütundaki sarı ok, geçerli yürütme noktasını işaretler.

**Konum** sütununda her bir iş parçacığının kaynak kodunda nerede göründüğü gösterilmektedir. Bu iş parçacığı için kısmi bir çağrı yığını göstermek için **konum** girişinin yanındaki Genişlet okunu veya girdinin üzerine gelin.

>[!TIP]
>İş parçacıkları için çağrı yığınlarının grafik görünümü için [Paralel Yığınlar](../debugger/using-the-parallel-stacks-window.md) penceresini kullanın. Pencereyi açmak için hata ayıklama sırasında **hata ayıkla**> **Windows** > **Paralel Yığınlar**' ı seçin.

**Tüm Iş parçacıklarının** **bayrak**, **Unflag**ve Unflag öğelerine ek olarak, **iş parçacığı** pencere öğeleri için sağ tıklama bağlam menüsü:

- **Kaynak olarak Iş parçacıklarını göster** düğmesi.
- İş **parçacıkları** penceresindeki **iş parçacığı kimliklerini**ondalığa onaltılık biçime değiştiren **onaltılık görüntü**.
- Çalışmayı hemen ilgili iş parçacığına geçirir [Iş parçacığına geçin](#switch-to-another-thread).
- İş parçacığı adını değiştirmenize olanak sağlayan **yeniden adlandırma**.
- Komutları [dondurma ve çözme](#bkmk_freeze) .

## <a name="bkmk_freeze"></a>İş parçacığı yürütmeyi dondurma ve çözme

İş parçacıklarının iş gerçekleştirdiği sırayı denetlemek için iş parçacıklarını dondurabilir ve çözme ya da askıya alabilir ve devam ettirebilirsiniz. İş parçacıklarını dondurma ve çözme, Kilitlenmeler ve yarış koşulları gibi eşzamanlılık sorunlarını çözmenize yardımcı olabilir.

> [!TIP]
> Aynı zamanda yaygın bir hata ayıklama senaryosu olan diğer iş parçacıklarını dondurmadan tek bir iş parçacığını izlemek için bkz. çok [iş parçacıklı uygulamalarda hata ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**İş parçacıklarını dondurmak ve çözmek için:**

1. **Iş parçacıkları** penceresinde herhangi bir iş parçacığına sağ tıklayın ve ardından **dondurma**' yı seçin. **Geçerli Iş parçacığı** sütununda bir **duraklatma** simgesi, iş parçacığının dondurulmuş olduğunu gösterir.

1. **Iş parçacıkları** penceresi araç çubuğunda **sütunlar** ' ı seçin ve **ardından askıya alınan Sayısı sütununu göstermek** için **askıda kalmış sayısı** ' nı seçin. Dondurulmuş iş parçacığı için askıda olan sayı değeri **1**' dir.

1. Dondurulmuş iş parçacığına sağ tıklayın ve çöz ' ü **seçin.**

   **Duraklat** simgesi kaybolur ve **askıya alınan sayı** değeri **0**olarak değişir.

## <a name="switch-to-another-thread"></a>Başka bir iş parçacığına geçiş

Başka bir iş parçacığına geçiş yapmayı denediğinizde **, uygulamanın kesme modu penceresinde olduğunu** görebilirsiniz. Bu pencere, iş parçacığının geçerli hata ayıklayıcının görüntüleyeceği herhangi bir kodu olmadığını söyler. Örneğin, yönetilen kodda hata ayıklaması yapabilirsiniz, ancak iş parçacığı yerel koddur. Pencere, sorunu çözmeye yönelik öneriler sunar.

**Başka bir iş parçacığına geçmek için:**

1. **Iş parçacıkları** penceresinde, geçerli iş **parçacığı** sütununda Sarı oka sahip iş parçacığı olan geçerli iş parçacığı kimliğini bir yere getirin. Uygulamanıza devam etmek için bu iş parçacığına geri dönmek isteyeceksiniz.

1. Farklı bir iş parçacığına sağ tıklayın ve bağlam menüsünden **Iş parçacığına geç** ' i seçin.

1. Sarı ok konumunun **Iş parçacıkları** penceresinde değiştiğini gözlemleyin. Özgün geçerli iş parçacığı işaretleyicisi Ayrıca, bir ana hat olarak kalır.

   Kod kaynağı düzenleyicisindeki iş parçacığı işaretçisinin araç ipucuna ve **hata ayıklama konumu** araç çubuğunda **iş parçacığı** açılan listesinde bakın. Geçerli iş parçacığının da orada değiştiğini gözlemleyin.

1. **Hata ayıklama konumu** araç çubuğunda, **iş parçacığı** listesinden farklı bir iş parçacığı seçin. Geçerli iş parçacığının diğer iki konumda da değiştiği unutulmamalıdır.

1. Kaynak kodu düzenleyicisinde bir iş parçacığı işaretine sağ tıklayın, **Iş parçacığına geç**' in üzerine gelin ve listeden başka bir iş parçacığı seçin. Geçerli iş parçacığının her üç konumda da değiştiğini gözlemleyin.

Kaynak kodundaki iş parçacığı işaretleyicisi ile yalnızca o konumda durdurulan iş parçacıkları için geçiş yapabilirsiniz. **Iş parçacıkları** penceresini ve **hata ayıklama konumu** araç çubuğunu kullanarak herhangi bir iş parçacığına geçiş yapabilirsiniz.

Artık çok iş parçacıklı uygulamalarda hata ayıklama hakkında temel bilgileri öğrendiniz. **İş parçacıkları penceresini,** **hata ayıklama konumu** araç çubuğundaki **iş parçacığı** listesini veya kaynak kodu düzenleyicisindeki iş parçacığı işaretçilerini kullanarak iş parçacıklarını gözlemleyerek, bayrakla kaldırarak ve dondurabilirsiniz

## <a name="see-also"></a>Ayrıca bkz.
- [Çok iş parçacıklı uygulamaların hatalarını ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Nasıl yapılır: Hata ayıklarken başka bir iş parçacığına geçme](../debugger/how-to-switch-to-another-thread-while-debugging.md)
