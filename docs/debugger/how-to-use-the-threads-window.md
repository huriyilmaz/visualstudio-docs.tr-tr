---
title: Çok iş parçacıklı bir uygulamada hata ayıklama
description: Visual Studio 'teki Iş parçacıkları penceresini ve hata ayıklama konumu araç çubuğunu kullanarak hata ayıklayın
ms.date: 02/14/2020
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5fad593bc6ab559b540f96eaeac5721c588ba7ff
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635392"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>İzlenecek yol: Iş parçacıkları penceresini kullanarak çok iş parçacıklı bir uygulamada hata ayıklama (C#, Visual Basic, C++)

birçok Visual Studio kullanıcı arabirimi öğesi çok iş parçacıklı uygulamalarda hata ayıklamanıza yardımcı olur. Bu makalede kod Düzenleyicisi penceresi, **hata ayıklama konumu** araç çubuğu ve **iş parçacıkları** penceresindeki çok iş parçacıklı hata ayıklama özellikleri tanıtılmaktadır. Çok iş parçacıklı [uygulamalarda hata ayıklamaya](../debugger/get-started-debugging-multithreaded-apps.md)yönelik diğer araçlar hakkında daha fazla bilgi için bkz

Bu öğreticiyi tamamlamak yalnızca birkaç dakika sürer ve çok iş parçacıklı uygulamalarda hata ayıklama hakkında temel bilgileri tamamladığınızda tercihinize.

## <a name="create-a-multithreaded-app-project"></a>Çok iş parçacıklı uygulama projesi oluşturma

Bu öğreticide kullanmak üzere aşağıdaki çok iş parçacıklı uygulama projesini oluşturun:

1. Visual Studio açın ve yeni bir proje oluşturun.

   ::: moniker range=">=vs-2019"

   Başlangıç penceresi açık değilse **Dosya** > **Başlangıç penceresi**' ni seçin.

   Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. ardından, dil listesinden **C#** veya **C++** öğesini seçin ve ardından Platform listesinden **Windows** öğesini seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra .NET Core veya C++ için **konsol uygulamasını** seçin ve ardından **İleri**' yi seçin.

   > [!NOTE]
   > doğru şablonu görmüyorsanız **araçlar**  >  **ve özellikler al..**. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. **.NET Core platformlar arası geliştirme** veya C++ iş yükü **ile masaüstü geliştirme** seçeneklerini belirleyin ve ardından **Değiştir**' i seçin.

   **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *MyThreadWalkthroughApp* yazın veya girin. Sonra, **İleri** veya **Oluştur**' u seçin, hangisi kullanılabilir seçeneği vardır.

   .NET Core için, önerilen hedef Framework veya .NET 6 ' ı seçin ve ardından **Oluştur**' u seçin.

   ::: moniker-end
   ::: moniker range="vs-2017"
   üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin. **Yeni proje** iletişim kutusunun sol bölmesinde aşağıdakileri seçin:

   - c# uygulaması için, **Visual C#** altında, **masaüstü Windows**' yi seçin ve ardından ortadaki bölmede **konsol uygulaması ' nı (.NET Framework)** seçin.
   - C++ uygulaması için, **Visual C++** altında masaüstü ' ne **Windows** ve ardından **Windows konsol uygulaması**' nı seçin.

   **konsol uygulamasını (.NET Framework)** görmüyorsanız veya C++ için **konsol uygulama** projesi şablonu ' na **gidin araçlar**  >  **ve özellikler al..**. ' a giderek Visual Studio Yükleyicisi açılır. C++ iş yüküyle **.net masaüstü geliştirme** veya **masaüstü geliştirme** seçeneklerini belirleyin ve ardından **Değiştir**' i seçin.

   Ardından, *MyThreadWalkthroughApp* gibi bir ad yazın ve **Tamam**' a tıklayın.

   **Tamam**’ı seçin.
   ::: moniker-end

   Yeni bir konsol projesi görüntülenir. Proje oluşturulduktan sonra bir kaynak dosya görüntülenir. Seçtiğiniz dile bağlı olarak, kaynak dosya *program. cs*, *MyThreadWalkthroughApp. cpp* veya *Module1. vb* olarak adlandırılır.

1. Kaynak dosyadaki kodu, çok [iş parçacıklı uygulamalarda hata ayıklamayı kullanmaya](../debugger/get-started-debugging-multithreaded-apps.md)başlamak Için C# veya C++ örnek kodu ile değiştirin.

1. **Dosya**  >  **Tümünü Kaydet**' i seçin.

## <a name="start-debugging"></a>Hata ayıklamayı Başlat

1. Kaynak kodda aşağıdaki satırları bulun:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. `Console.WriteLine();`Sol cilt paya tıklayarak veya satırı seçip **F9** tuşuna basarak satırda bir kesme noktası ayarlayın.

   Kesme noktası, kod satırının yanındaki sol cilt alanında kırmızı bir daire olarak görünür.

1. **Hata**  >  **ayıklamayı Başlat hata** Ayıkla ' yı seçin veya **F5** tuşuna basın.

   Uygulama hata ayıklama modunda başlar ve kesme noktasında duraklatılır.

1. kesme modundayken, **hata ayıklama**   >  **Windows**  >  **iş parçacıkları**' nı seçerek iş parçacıkları penceresini açın. **Iş parçacıklarını** ve diğer hata ayıklama pencerelerini açmak veya görmek için bir hata ayıklama oturumunda olmanız gerekir.

## <a name="examine-thread-markers"></a>İş parçacığı işaretçilerini İncele

1. Kaynak kodunda `Console.WriteLine();` satırı bulun.

   1. **Iş parçacıkları** penceresinde sağ tıklayın ve menüden kaynak ![bölümünde](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") iş **parçacıklarını göster ' i seçin.**

   Kaynak kodu satırının yanındaki cilt payı artık *iş parçacığı işaretçisi* simgesi ![iş parçacığı işaretleyicisi](../debugger/media/dbg-thread-marker.png "İş Parçacığı İşaretçisi")görüntülüyor. İş parçacığı işaretçisi, bu konumda bir iş parçacığının durdurulduğunu gösterir. Konumda birden fazla durdurulmuş iş parçacığı varsa, ![birden çok iş](../debugger/media/dbg-multithreaded-show-threads.png "birden çok iş parçacığı") parçacığı simgesi görüntülenir.

1. İşaretçiyi iş parçacığı işaretçisinin üzerine getirin. Durdurulan iş parçacığı veya iş parçacıkları için ad ve iş parçacığı KIMLIĞI numarasını gösteren bir veri Ipucu görünür. İş parçacığı adları olabilir `<No Name>` .

   >[!TIP]
   >İsimsiz iş parçacıklarını belirlemenize yardımcı olmak için bunları **Iş parçacıkları** penceresinde yeniden adlandırabilirsiniz. İş parçacığına sağ tıklayıp **Yeniden Adlandır**' ı seçin.

1. Kısayol menüsünde kullanılabilir seçenekleri görmek için kaynak kodundaki iş parçacığı işaretine sağ tıklayın.

## <a name="flag-and-unflag-threads"></a>İş parçacıklarını bayrakla işaretleme ve işareti geri alma

Özel dikkat etmek istediğiniz iş parçacıklarını izlemek için iş parçacıklarına bayrak atayabilirsiniz.

Kaynak kodu düzenleyicisinden veya **Iş parçacıkları** penceresinden iş parçacıklarını bayrak ve işaretini kaldır. **Hata ayıklama konumu** veya **iş parçacıkları** penceresi araç çubuklarından yalnızca bayraklı iş parçacıklarını mı yoksa tüm iş parçacıklarını mı görüntüleneceğini seçin. Herhangi bir konumdan yapılan seçimler tüm konumları etkiler.

### <a name="flag-and-unflag-threads-in-source-code"></a>Kaynak kodundaki iş parçacıklarını işaretle ve işaretini kaldır

1.    >  **Araç çubukları**  >  **hata ayıklama konumunu** göster ' i seçerek hata ayıklama konumu araç çubuğunu açın. Ayrıca araç çubuğu alanına sağ tıklayıp **hata ayıklama konumu**' nu seçebilirsiniz.

1. **Hata ayıklama konumu** araç çubuğunda üç alan vardır **: işlem**, **iş parçacığı** ve **yığın çerçevesi**. **Iş parçacığı** listesini açılır ve kaç iş parçacığı olduğunu Note. **Iş parçacığı** listesinde, yürütülmekte olan iş parçacığı bir sembol tarafından işaretlenir **>** .

1. Kaynak kodu penceresinde, cilt payında bir iş parçacığı işaretleyici simgesinin üzerine gelin ve veri Ipucunda bayrak simgesini (veya boş bayrak simgelerinden birini) seçin. Bayrak simgesi kırmızıya döner.

   Ayrıca, bir iş parçacığı işaretleyici simgesine sağ tıklayıp **bayrak**' ın üzerine gelin ve kısayol menüsünden bayrak eklenecek bir iş parçacığı seçebilirsiniz.

1. **Hata ayıklama konumu** araç çubuğunda, **iş parçacığı** alanının sağında **yalnızca bayraklı Iş parçacıklarını göster** simgesi ![bayraklı iş parçacıklarını göster](../debugger/media/dbg-threads-show-flagged.png "Bayraklı İş Parçacıklarını Göster")' i seçin. Bir veya daha fazla iş parçacığı işaretlenmediği takdirde simgenin gri renkte olması önerilir.

   Araç çubuğundaki **Iş parçacığı** açılır listesinde yalnızca bayraklı iş parçacığı görüntülenir. Tüm iş parçacıklarını yeniden göstermek için, **yalnızca bayraklı Iş parçacıklarını göster** simgesini yeniden seçin.

   >[!TIP]
   >Bazı iş parçacıklarını işaretledikten sonra imlecinizi kod düzenleyicisine yerleştirebilir, sağ tıklayıp **bayraklı Iş parçacıklarını Imlece Çalıştır**' ı seçebilirsiniz. İşaretlenen tüm iş parçacıklarının ulaşabileceği kodu seçtiğinizden emin olun. **Bayraklı Iş parçacıklarını Imlece Çalıştır** , seçilen kod satırında iş parçacıklarını duraklatıp, [iş parçacıklarını dondurarak ve thanerek](#bkmk_freeze)yürütme sırasını denetlemeyi kolaylaştırır.

1. Şu anda yürütülmekte olan iş parçacığının bayraklı veya işaretlenmeyen durumunu değiştirmek için, **yalnızca bayraklı Iş parçacıklarını göster** düğmesinin solunda bulunan **geçerli Iş parçacığı bayrak durumu** araç çubuğu düğmesini seçerek tek bayrak ' i seçin. Geçerli iş parçacığına bayrak eklemek, yalnızca bayraklı iş parçacıkları gösterilirken geçerli iş parçacığını bulmak için yararlıdır.

1. Bir iş parçacığının bayrağını kaldırmak için kaynak kodundaki iş parçacığı işaretçisinin üzerine gelin ve kırmızı bayrak simgesini seçerek temizleyin veya iş parçacığı işaretine sağ tıklayıp **bayrağı kaldır**' ı seçin.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Iş parçacıkları penceresindeki bayrakları işaretle ve Kaldır

**Iş parçacıkları** penceresinde, bayraklı iş parçacıklarının yanında kırmızı bayrak simgeleri vardır ve gösterilirse bayraklı iş parçacıkları boş simgelere sahiptir.

![İş parçacıkları penceresi](../debugger/media/dbg-threads-window.png "İş Parçacıkları Penceresi")

Geçerli durumuna bağlı olarak, iş parçacığı durumunu bayraklı veya bayraklı olarak değiştirmek için bir bayrak simgesi seçin.

Ayrıca, kısayol menüsünden bir satıra sağ tıklayıp **bayrak**, bayrağı **Kaldır** veya **tüm iş parçacıklarını işaretini kaldır** ' ı seçebilirsiniz.

**Iş parçacıkları** penceresi araç çubuğunda Ayrıca, iki bayrak simgelerinden oluşan, **yalnızca bayrak eklenmiş bir iş parçacığı göster** düğmesi bulunur. **Hata ayıklama konumu** araç çubuğundaki düğmeyle aynı şekilde çalışacaktır ve iki düğme de her iki konumdaki görüntüyü denetler.

### <a name="other-threads-window-features"></a>Diğer Iş parçacıkları penceresi özellikleri

**Iş parçacıkları** penceresinde, herhangi bir sütunun üst bilgisini seçerek iş parçacıklarını bu sütuna göre sıralayın. Sıralama düzenini tersine çevirmek için yeniden seçin. Tüm iş parçacıkları gösteriyorsa, bayrak simgesi sütunu seçildiğinde iş parçacıkları bayraklı veya işaretlenmeyen duruma göre sıralanır.

**Iş parçacıkları** penceresinin (üst bilgi içermeyen) Ikinci sütunu **geçerli iş parçacığı** sütunudur. Bu sütundaki sarı ok, geçerli yürütme noktasını işaretler.

**Konum** sütununda her bir iş parçacığının kaynak kodunda nerede göründüğü gösterilmektedir. Bu iş parçacığı için kısmi bir çağrı yığını göstermek için **konum** girişinin yanındaki Genişlet okunu veya girdinin üzerine gelin.

>[!TIP]
>İş parçacıkları için çağrı yığınlarının grafik görünümü için [Paralel Yığınlar](../debugger/using-the-parallel-stacks-window.md) penceresini kullanın. pencereyi açmak için hata ayıklama sırasında  >    >  **paralel yığınlar** Windows hata ayıkla ' yı seçin.

**Tüm Iş parçacıklarının** **bayrak**, **Unflag** ve Unflag öğelerine ek olarak, **iş parçacığı** pencere öğeleri için sağ tıklama bağlam menüsü:

- **Kaynak olarak Iş parçacıklarını göster** düğmesi.
- İş **parçacıkları** penceresindeki **iş parçacığı kimliklerini** ondalığa onaltılık biçime değiştiren **onaltılık görüntü**.
- Çalışmayı hemen ilgili iş parçacığına geçirir [Iş parçacığına geçin](#switch-to-another-thread).
- İş parçacığı adını değiştirmenize olanak sağlayan **yeniden adlandırma**.
- Komutları [dondurma ve çözme](#bkmk_freeze) .

## <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> İş parçacığı yürütmeyi dondurma ve çözme

İş parçacıklarının çalışma sırasına göre denetim altına almak için iş parçacıklarını dondurabilir, çözdürabilir veya iş parçacıklarını askıya alabilir ve devam ettirin. Donma ve çözülen iş parçacıkları kilitlenmeler ve yarış koşulları gibi eşzamanlılık sorunlarını çözmenize yardımcı olabilir.

> [!TIP]
> Yaygın bir hata ayıklama senaryosu olan diğer iş parçacıklarını dondurmadan tek bir iş parçacığını takip etmek için [bkz. çoklu](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread)iş parçacığı Kullanmaya başlayın hata ayıklama.

**İş parçacıklarını dondurmak ve dondurmak için:**

1. İş Parçacıkları **penceresinde herhangi** bir iş parçacığına sağ tıklayın ve Ardından Dondur'u **seçin.** Geçerli **İş** Parçacığı sütunundaki **Duraklat simgesi,** iş parçacığının donmuş olduğunu gösterir.

1. İş **Parçacıkları penceresi** araç çubuğunda **Sütunlar'ı** seçin ve ardından **Askıya Alınan Sayı** sütununu görüntülemek için **Askıya Alınan Sayı'ya** tıklayın. Donmuş iş parçacığı için askıya alınan sayı değeri **1'tir.**

1. Donmuş iş parçacığına sağ tıklayın ve **Thaw öğesini seçin.**

   Duraklat **simgesi** kaybolur ve Askıya Alınan **Sayı değeri** **0 olarak değişir.**

## <a name="switch-to-another-thread"></a>Başka bir iş parçacığına geçme

Başka bir iş **parçacığına geçiş yapmaya çalışırken** Uygulamanın kesme modunda olduğunu görebilirsiniz. Bu pencere, iş parçacığının geçerli hata ayıklayıcısı tarafından görüntülen herhangi bir koda sahip olmadığını belirtir. Örneğin, yönetilen kodda hata ayıklayabilirsiniz, ancak iş parçacığı yerel koddur. Pencere, sorunu çözmek için öneriler sunar.

**Başka bir iş parçacığına geçmek için:**

1. İş **Parçacıkları** penceresinde geçerli iş parçacığı kimliğini (Geçerli İş Parçacığı sütununda sarı ok bulunan iş **parçacığı) not** etmek için kullanın. Uygulamanıza devam etmek için bu iş parçacığına geri dönmek gerekir.

1. Farklı bir iş parçacığına sağ tıklayın ve bağlam **menüsünden İş Parçacığına** Geç'i seçin.

1. İş Parçacıkları penceresinde sarı ok konumunun değiştiğini **görebilirsiniz.** Özgün geçerli iş parçacığı işaretçisi de ana hat olarak kalır.

   Kod kaynağı düzenleyicisinde iş parçacığı işaretçisinde araç ipucuna ve Hata Ayıklama Konumu araç **çubuğundaki İş** Parçacığı açılan **menüsündeki listeye** bakın. Geçerli iş parçacığının da burada değiştiğini gözlemlemek.

1. Hata Ayıklama **Konumu araç çubuğunda** İş Parçacığı listesinden farklı bir iş **parçacığı** seçin. Geçerli iş parçacığının diğer iki konumda da değiştiklerini unutmayın.

1. Kaynak kod düzenleyicisinde, bir iş parçacığı işaretçisini sağ tıklatın, İş Parçacığına Geç'in **işaretine gelin** ve listeden başka bir iş parçacığı seçin. Geçerli iş parçacığının üç konumda da değiştiklerini gözlemlemek.

Kaynak kodda iş parçacığı işaretçisi ile, yalnızca o konumda durdurulmuş iş parçacıklarına geçebilirsiniz. İş Parçacıkları penceresini **ve** Hata Ayıklama **Konumu araç çubuğunu** kullanarak herhangi bir iş parçacığına geçebilirsiniz.

Artık çok iş parçacıklı uygulamalarda hata ayıklamanın temellerini öğrendiniz. İş Parçacıkları penceresini, Hata Ayıklama Konumu araç çubuğundaki İş Parçacığı listesini  veya kaynak  kod düzenleyicisinde iş parçacığı işaretçilerini kullanarak iş parçacıklarını gözlemleyebilirsiniz, işaretlerini ayıklar, dondurabilir ve çözülebilirsiniz. 

## <a name="see-also"></a>Ayrıca bkz.
- [Çok iş parçacıklı uygulamaların hatalarını ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Nasıl yapılır: Hata ayıklarken başka bir iş parçacığına geçme](../debugger/how-to-switch-to-another-thread-while-debugging.md)
