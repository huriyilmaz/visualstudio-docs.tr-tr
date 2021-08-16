---
title: Çok iş parçacıklı uygulamada hata ayıklama
description: İş Parçacıkları penceresini ve Hata Ayıklama Konumu araç çubuğunu kullanarak hata Visual Studio
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
ms.openlocfilehash: 2f4783f4a9d34d267c78ddf08309f2a140b4769b5ce1bc2ac5d86ea7aa68fd7b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378702"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Kılavuz: İş Parçacıkları penceresini kullanarak çok iş parçacıklı bir uygulamada hata ayıklama (C#, Visual Basic, C++)

Birden Visual Studio kullanıcı arabirimi öğeleri, çok iş parçacıklı uygulamalarda hata ayıklamanıza yardımcı olur. Bu makalede kod düzenleyicisi penceresinde, Hata Ayıklama Konumu araç çubuğunda ve İş Parçacıkları penceresinde çok iş **parçacıklı** hata ayıklama **özellikleri tanıtıldı.** Çok iş parçacıklı uygulamalarda hata ayıklamaya ilişkin diğer araçlar hakkında daha fazla bilgi için [bkz. Kullanmaya başlayın uygulamalarda hata ayıklama.](../debugger/get-started-debugging-multithreaded-apps.md)

Bu öğreticiyi tamamlamak yalnızca birkaç dakika sürer ve çok iş parçacıklı uygulamalarda hata ayıklamanın temellerini size bilgi sağlar.

## <a name="create-a-multithreaded-app-project"></a>Çok iş parçacıklı uygulama projesi oluşturma

Bu öğreticide kullanmak üzere aşağıdaki çok iş parçacıklı uygulama projesini oluşturun:

1. Yeni Visual Studio ve yeni bir proje oluşturun.

   ::: moniker range=">=vs-2019"

   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

   Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından Dil **listesinden C#** **veya C++** seçin ve ardından Platform **listesinden Windows'yi** seçin. 

   Dil ve platform filtrelerini uyguladikten  sonra .NET Core veya C++ için Konsol Uygulaması'na ve ardından Sonraki 'yi **seçin.**

   > [!NOTE]
   > Doğru şablonu görmüyorsanız Araçlar Araçları ve Özellikleri Al... 'a  >  **gidin ve** bu işlem Visual Studio Yükleyicisi. **.NET Core platformlar arası geliştirme veya** **C++** ile masaüstü geliştirme iş yükünü ve ardından Değiştir'i **seçin.**

   Yeni **projenizi yapılandır penceresine** *MyThreadWalkthroughApp yazın* **veya Project** girin. Ardından, **varsa,** **Sonraki'yi veya** Oluştur'ı seçin.

   .NET Core için önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   ::: moniker-end
   ::: moniker range="vs-2017"
   Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni proje iletişim kutusunun **sol** bölmesinde, aşağıdakini seçin:

   - Bir C# uygulaması için **Visual C#** altında Windows **Desktop'ı** seçin ve orta bölmede Konsol Uygulaması **(.NET Framework) seçin.**
   - Bir C++ uygulaması için, **Visual C++** altında Windows **Masaüstü'ne** tıklayın ve ardından Konsol **Uygulaması'Windows seçin.**

   Konsol Uygulaması **(.NET Framework)** veya C++ için Konsol Uygulaması proje şablonunu  görmüyorsanız Araçlar Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. **.NET masaüstü geliştirme veya** **C++** ile masaüstü geliştirme iş yükünü ve ardından Değiştir'i **seçin.**

   Ardından *MyThreadWalkthroughApp gibi bir ad yazın ve Tamam'a* **tıklayın.**

   **Tamam**’ı seçin.
   ::: moniker-end

   Yeni bir konsol projesi görüntülenir. Proje oluşturulduktan sonra bir kaynak dosya görüntülenir. Seçtiğiniz dile bağlı olarak, kaynak dosya *Program.cs*, *MyThreadWalkthroughApp.cpp* veya *Module1.vb olarak çağrılmalıdır.*

1. Kaynak dosyada yer alan kodu çok iş parçacıklı uygulamalarda hata ayıklamak için [kullanılan C# Kullanmaya başlayın C++ örnek koduyla değiştirin.](../debugger/get-started-debugging-multithreaded-apps.md)

1. Dosya **Kaydet'i**  >  **seçin.**

## <a name="start-debugging"></a>Hata ayıklamayı başlatma

1. Kaynak kodunda aşağıdaki satırları bulun:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Sol oluk içinde tıklayarak veya satırı seçerek ve F9 tuşuna basarak `Console.WriteLine();` satırda bir kesme **noktası ayarlayın.**

   Kesme noktası, kod çizgisinin yanında sol oluk içinde kırmızı bir daire olarak görünür.

1. Hata **AyıklamaYı Başlat**  >  **Hata Ayıklama'yi seçin** veya **F5 tuşuna basın.**

   Uygulama hata ayıklama modunda başlar ve kesme noktası sırasında duraklatılır.

1. Kesme modundayken, İş  Parçacıklarında Hata Ayıkla'ya **Windows**  >    >  **açın.** İş Parçacıkları ve diğer hata ayıklama pencerelerini açmak veya görmek için **bir hata ayıklama** oturumunda olmak gerekir.

## <a name="examine-thread-markers"></a>İş parçacığı işaretçilerini inceleme

1. Kaynak kodunda, satırı `Console.WriteLine();` bulun.

   1. İş Parçacıkları penceresine sağ **tıklayın** ve menüden **kaynakta İş** Parçacıklarını ![Kaynakta Göster'i](../debugger/media/dbg-multithreaded-show-threads.png "Threadişaretleyici") seçin.

   Kaynak kod çizgisinin yanındaki oluk artık iş parçacığı işaretçisi simgesini *İş Parçacığı* İşaretçisi ![olarak görüntüler.](../debugger/media/dbg-thread-marker.png "İş parçacığı Işaretçisi") İş parçacığı işaretçisi, bir iş parçacığının bu konumda durdurulmuş olduğunu gösterir. Konumda birden fazla durdurulmuş iş parçacığı varsa birden çok ![iş parçacığı](../debugger/media/dbg-multithreaded-show-threads.png "birden çok iş parçacığı") simgesi görünür.

1. İşaretçiyi iş parçacığı işaretçisinin üzerine gelin. Durdurulan iş parçacığının veya iş parçacıklarının adını ve iş parçacığı kimliği numarasını gösteren bir DataTip görüntülenir. İş parçacığı adları `<No Name>` olabilir.

   >[!TIP]
   >Adsız iş parçacıklarını tanımlamaya yardımcı olmak için bunları İş Parçacıkları penceresinde yeniden **adlandırabilirsiniz.** İş parçacığına sağ tıklayın ve Yeniden Adlandır'ı **seçin.**

1. Kısayol menüsündeki kullanılabilir seçenekleri görmek için kaynak kodda iş parçacığı işaretçiye sağ tıklayın.

## <a name="flag-and-unflag-threads"></a>İş parçacıklarını bayrakla işaretleme ve işareti geri alma

Özellikle dikkat etmek istediğiniz iş parçacıklarını izlemek için iş parçacıklarını bayrakla izleyebilirsiniz.

İş parçacıklarını kaynak kod düzenleyicisinden veya İş Parçacıkları penceresinden bayrağını **açın.** Hata Ayıklama Konumu veya İş Parçacıkları pencere araç  çubuklarından yalnızca bayraklı iş parçacıklarını mı yoksa tüm iş **parçacıklarını mı** görüntüleyebilirsiniz? Herhangi bir konumdan yapılan seçimler tüm konumları etkiler.

### <a name="flag-and-unflag-threads-in-source-code"></a>Kaynak kodda iş parçacıklarını bayrakla bayrakla asma ve iş parçacıklarını geri alama

1. Görünüm Araç **Çubukları Hata Ayıklama Konumu'nu** **seçerek**  >  **Hata Ayıklama Konumu** araç çubuğunu  >  **açın.** Araç çubuğu alanına sağ tıklar ve Hata Ayıklama **Konumu'nu da seçersiniz.**

1. Hata **Ayıklama Konumu araç çubuğunda** üç alan vardır: **İşlem,** **İş Parçacığı** ve **Yığın Çerçevesi.** İş parçacığı **listesini aşağı** bırakın ve kaç iş parçacığı olduğunu not ekleyin. İş **Parçacığı listesinde,** yürütülen iş parçacığı bir sembolle **>** işaretlenir.

1. Kaynak kodu penceresinde, boşlukta bir iş parçacığı işaretçisi simgesinin üzerine gelin ve DataTip'te bayrak simgesini (veya boş bayrak simgelerinden birini) seçin. Bayrak simgesi kırmızıya döner.

   Ayrıca, bir iş parçacığı işaretçisi simgesine sağ tıklar, Bayrağı'nın üzerine gelin ve kısayol menüsünden bayrak eklemek için bir iş parçacığı seçebilirsiniz. 

1. Hata Ayıklama **Konumu araç çubuğunda,** İş **Parçacığı** ![](../debugger/media/dbg-threads-show-flagged.png "Bayraklı Iş parçacıklarını göster")alanı sağ üst köşesindeki Yalnızca Bayraklı İş Parçacıklarını Göster simgesini Bayraklı İş Parçacıklarını Göster **'i** seçin. Bir veya daha fazla iş parçacığı işaretlenmediği sürece simge gri renkte görünür.

   Artık araç çubuğundaki İş Parçacığı açılan **listesinde yalnızca bayraklı** iş parçacığı görünür. Tüm iş parçacıklarını yeniden göstermek için Yalnızca **Bayraklı İş Parçacıklarını Göster simgesini yeniden** seçin.

   >[!TIP]
   >Bazı iş parçacıklarını işaretledikten sonra imlecinizi kod düzenleyicisine yerleştirerek sağ tıklar ve Bayraklı İş Parçacıklarını İmleç olarak **çalıştır'ı seçin.** Bayrakla işaretlenmiş tüm iş parçacıklarının ulaşacak kodu seçmeyi tercih emin olun. **Bayraklı İş Parçacıklarını İmleç'e** Çalıştır seçeneği, seçilen kod satırı üzerinde iş parçacıklarını duraklatarak iş parçacıklarını dondurarak ve çözülerek yürütme [sıralarını denetlemeyi kolaylaştırır.](#bkmk_freeze)

1. O anda yürütülen iş parçacığının bayraklı veya bayraksız durumunu  değiştirmek için, Yalnızca Bayraklı İş Parçacıklarını Göster düğmesinin sol tarafından bulunan Geçerli İş Parçacığı Bayraklı Durum araç çubuğunu değiştir düğmesini **seçin.** Geçerli iş parçacığını bayrakla göstermek, yalnızca bayraklı iş parçacıkları gösteriliyorken geçerli iş parçacığını bulmak için kullanışlıdır.

1. Bir iş parçacığının bayrağını silmek için, kaynak kodda iş parçacığı işaretçisi üzerine gelin ve kırmızı bayrak simgesini seçerek iş parçacığı işaretçisini silin veya iş parçacığı işaretçisini sağ tıklatın ve **Bayrağını Geri Ekle'yi seçin.**

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>İş Parçacıkları penceresinde iş parçacıklarını bayrakla açma ve açma

İş Parçacıkları **penceresinde,** bayraklı iş parçacıklarının yanında kırmızı bayrak simgeleri, gösteriliyorsa, dalgalanmamış iş parçacıklarının ise boş simgeleri vardır.

![İş Parçacıkları Penceresi](../debugger/media/dbg-threads-window.png "İş parçacıkları penceresi")

İş parçacığı durumunu geçerli durumuna bağlı olarak bayraklı veya bayraksız olarak değiştirmek için bir bayrak simgesi seçin.

Ayrıca, bir satıra sağ tıklar ve kısayol **menüsünden** Bayrak , BayrağıNı **Kaldır** veya Tüm İş **Parçacıklarını** Bayrağını Kaldır'ı seçebilirsiniz.

İş **Parçacıkları** penceresi araç çubuğunda **ayrıca, iki bayrak simgesi** arasında sağ tarafta bulunan Bayraklı İş Parçacıklarını Yalnızca Göster düğmesi de vardır. Hata Ayıklama Konumu araç çubuğundaki düğmeyle **aynı şekilde** çalışır ve her iki düğmeden biri her iki konumda da ekranı kontrol eder.

### <a name="other-threads-window-features"></a>Diğer İş Parçacıkları penceresi özellikleri

İş Parçacıkları **penceresinde,** iş parçacıklarını bu sütuna göre sıralamak için herhangi bir sütunun üst bilgilerini seçin. Sıralama sıralamayı ters çevirmek için yeniden seçin. Tüm iş parçacıkları gösteriliyorsa, bayrak simgesi sütununu seçmek iş parçacıklarını bayraklı veya bayraksız durumlara göre sıralar.

İş Parçacıkları penceresinin **ikinci sütunu** (üst bilgi yok) Geçerli İş **Parçacığı sütunu** olur. Bu sütundaki sarı ok, geçerli yürütme noktasını işaretler.

Konum **sütunu,** her iş parçacığının kaynak kodda nerede görüntülendiğinde gösterir. Konum girişinin yanındaki genişletme **okunu** seçin veya girişin üzerine gelerek bu iş parçacığı için kısmi bir çağrı yığınını gösterebilirsiniz.

>[!TIP]
>İş parçacıkları için çağrı yığınlarının grafik görünümü için Paralel [Yığınlar penceresini](../debugger/using-the-parallel-stacks-window.md) kullanın. Hata ayıklama sırasında pencereyi açmak için Paralel Yığınlarda **hata** >  **Windows**  >  **seçin.**

Bayrak ,  **Bayrağını Kaldır** ve Tüm **İş** Parçacıklarını Bayrakla Kaldır'a ek olarak, İş Parçacığı pencere öğeleri için sağ tıklama **bağlam** menüsünde şunları içerir:

- İş **Parçacıklarını Kaynakta Göster** düğmesi.
- **İş Parçacıkları penceresindeki** İş Parçacığı Kimliklerini ondalıktan onaltılık biçime değiştirir. 
- [Yürütmeyi hemen](#switch-to-another-thread)bu iş parçacığına devreden İş Parçacığına Geçiş.
- **yeniden** adlandırarak iş parçacığı adını değiştirebilirsiniz.
- [Freeze ve Thaw](#bkmk_freeze) komutları.

## <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> İş parçacığı yürütmeyi dondurma ve çözme

İş parçacıklarının iş gerçekleştirdiği sırayı denetlemek için iş parçacıklarını dondurabilir ve çözme ya da askıya alabilir ve devam ettirebilirsiniz. İş parçacıklarını dondurma ve çözme, Kilitlenmeler ve yarış koşulları gibi eşzamanlılık sorunlarını çözmenize yardımcı olabilir.

> [!TIP]
> Aynı zamanda yaygın bir hata ayıklama senaryosu olan diğer iş parçacıklarını dondurmadan tek bir iş parçacığını izlemek için bkz. çok [iş parçacıklı uygulamalarda hata ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**İş parçacıklarını dondurmak ve çözmek için:**

1. **Iş parçacıkları** penceresinde herhangi bir iş parçacığına sağ tıklayın ve ardından **dondurma**' yı seçin. **Geçerli Iş parçacığı** sütununda bir **duraklatma** simgesi, iş parçacığının dondurulmuş olduğunu gösterir.

1. **Iş parçacıkları** penceresi araç çubuğunda **sütunlar** ' ı seçin ve **ardından askıya alınan Sayısı sütununu göstermek** için **askıda kalmış sayısı** ' nı seçin. Dondurulmuş iş parçacığı için askıda olan sayı değeri **1**' dir.

1. Dondurulmuş iş parçacığına sağ tıklayın ve çöz ' ü **seçin.**

   **Duraklat** simgesi kaybolur ve **askıya alınan sayı** değeri **0** olarak değişir.

## <a name="switch-to-another-thread"></a>Başka bir iş parçacığına geç

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
