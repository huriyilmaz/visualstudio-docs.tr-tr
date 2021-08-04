---
title: Paralel uygulama hata ayıklaması | Microsoft Docs
description: Visual Studio'de Paralel Görevler ve Paralel Yığınlar pencerelerini kullanarak hata Visual Studio
ms.date: 02/14/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e6adeb4a67272cac90a829069ffc3a65bb7f969
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2021
ms.locfileid: "115094743"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>Kılavuz: Visual Studio'da Paralel Uygulamada Hata Ayıklama (C#, Visual Basic, C++)

Bu kılavuzda paralel bir uygulamada hata **ayıklamak için** Paralel Görevler ve **Paralel** Yığınlar pencerelerini kullanma hakkında bilgi verilmektedir. Bu pencereler, Görev Paralel Kitaplığı [(TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) veya Eşzamanlılık Çalışma Zamanı kullanan kodun çalışma zamanı davranışını anlamanıza ve [doğrulamanıza yardımcı Eşzamanlılık Çalışma Zamanı.](/cpp/parallel/concrt/concurrency-runtime) Bu kılavuz yerleşik kesme noktalarına sahip örnek kod sağlar. Kod bozulduktan sonra izlenecek yol,  Paralel Görevler ve Paralel Yığınlar **pencerelerini kullanarak** incelemeyi gösterir.

 Bu kılavuzda şu görevler öğretildi:

- Tüm iş parçacıklarının çağrı yığınlarını tek bir görünümde görüntüleme.

- Uygulamanıza oluşturulan `System.Threading.Tasks.Task` örneklerin listesini görüntüleme.

- İş parçacıkları yerine gerçek görev çağrı yığınlarını görüntüleme.

- Paralel Görevler ve Paralel **Yığınlar pencerelerinden** **koda** nasıl gidebilirsiniz?

- Pencereler gruplama, yakınlaştırma ve diğer ilgili özellikler aracılığıyla ölçeklendirmeyle nasıl başa çıkabilir?

## <a name="prerequisites"></a>Önkoşullar
 Bu kılavuzda, **Yalnızca kendi kodum** etkinleştirilmiştir (varsayılan olarak daha yeni sürümlerde varsayılan olarak etkindir) Visual Studio. Araçlar menüsünde **Seçenekler'e** **tıklayın,** Hata ayıklama düğümünü **genişletin,** Genel'i seçin ve ardından Yalnızca kendi kodum **etkinleştir (Yalnızca yönetilen) seçeneğini belirleyin.** Bu özelliği ayarlasanız bile bu izlenecek yolu kullanabilirsiniz, ancak sonuçlarınız çizimlerden farklı olabilir.

## <a name="c-sample"></a>C# Örneği
 C# örneğini kullanırsanız, bu kılavuzda Dış Kodun gizli olduğu da varsaylanır. Dış kodun görüntüleniyor olup olmadığını değiştirmek için Çağrı  Yığını penceresinin **Ad** tablosu üst bilgisini sağ tıklatın ve Dış Kodu Göster'i seçin **veya silin.** Bu özelliği ayarlasanız bile bu izlenecek yolu kullanabilirsiniz, ancak sonuçlarınız çizimlerden farklı olabilir.

## <a name="c-sample"></a>C++ Örneği
 C++ örneğini kullanıyorsanız, bu konudaki Dış Kod başvurularını yoksayabilirsiniz. Dış Kod yalnızca C# örneği için geçerlidir.

## <a name="illustrations"></a>Çizimler
 Bu konudaki çizimler C# örneğini çalıştıran dört çekirdekli bir bilgisayara kaydedilmiştir. Bu izlenecek yolu tamamlamak için başka yapılandırmalar da kullanabilirsiniz, ancak çizimler bilgisayarınızda görüntülenenlerden farklı olabilir.

## <a name="creating-the-sample-project"></a>Örnek Project
 Bu kılavuzda yer alan örnek kod, hiçbir şey yapacak bir uygulama değildir. Burada amaç, paralel uygulamada hata ayıklamak için araç pencerelerini kullanmayı anlamaktır.

#### <a name="to-create-the-sample-project"></a>Örnek projeyi oluşturmak için

1. Yeni Visual Studio ve yeni bir proje oluşturun.

   ::: moniker range=">=vs-2019"

   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

   Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından, **Dil listesinden C#**, **C++** **Visual Basic** seçin ve ardından Platform **listesinden Windows'yi** seçin.

   Dil ve platform filtrelerini uygulayan  .NET Core veya C++ için Konsol Uygulaması'na ve ardından Sonraki 'yi **seçin.**

   > [!NOTE]
   > Doğru şablonu görmüyorsanız Araçlar Araçları ve Özellikleri Al... 'a  >  **gidin ve** bu işlem Visual Studio Yükleyicisi. **.NET Core platformlar arası geliştirme veya** **C++** ile masaüstü geliştirme iş yükünü ve ardından Değiştir'i **seçin.**

   Yeni **projenizi yapılandır penceresine** bir ad yazın veya varsayılan adı Project **kullanın.** Ardından, **varsa,** **Sonraki'yi veya** Oluştur'ı seçin.

   .NET Core için önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   ::: moniker-end
   ::: moniker range="vs-2017"
   Üst menü çubuğundan Dosya Yeni **dosya'Project.**  >    >   Yeni proje iletişim kutusunun **sol** bölmesinde, aşağıdakini seçin:

   - Bir C# uygulaması için **Visual C#** altında Windows **Desktop'ı** seçin ve orta bölmede Konsol Uygulaması **(.NET Framework) seçin.**
   - Bir Visual Basic için, **Visual Basic** altında Windows **Desktop'ı seçin** ve orta bölmede Konsol Uygulaması **(.NET Framework) seçin.**
   - Bir C++ uygulaması için, **Visual C++** altında Windows Masaüstü'Windows'ı **seçin.** 

   Konsol Uygulaması **(.NET Core)** veya C++ için Konsol Uygulaması  proje şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. **.NET masaüstü geliştirme veya** **C++** ile masaüstü geliştirme iş yükünü ve ardından Değiştir'i **seçin.**

   Ardından bir ad yazın veya varsayılan adı kullanın ve Tamam'a **tıklayın.**

   **Tamam**’ı seçin.
   ::: moniker-end

   Yeni bir konsol projesi görüntülenir. Proje oluşturulduktan sonra bir kaynak dosya görüntülenir.

1. Projesinde .cpp, .cs veya .vb kod dosyasını açın. Boş bir kod dosyası oluşturmak için içeriğini silin.

1. Seçtiğiniz dil için aşağıdaki kodu boş kod dosyasına yapıştırın.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/debugger/cs/s.cs" id="Snippet1":::
   :::code language="cpp" source="../snippets/cpp/VS_Snippets_Misc/debugger/cpp/beta2_native.cpp" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Misc/debugger/vb/module1.vb" id="Snippet1":::

1. **Dosya** menüsünde **Tümünü Kaydet**’e tıklayın.

1. Derleme menüsünde **Çözümü Yeniden** **Oluştur'a tıklayın.**

    (C++ örneğinde) için dört çağrı olduğunu fark edersiniz. Bu nedenle kesme noktaları eklemek zorunda değildir; yalnızca uygulamayı çalıştırmanın hata ayıklayıcıda dört kez kesmeye neden `Debugger.Break` `DebugBreak` olur.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Paralel Yığınlar Penceresini Kullanma: İş Parçacıkları Görünümü
 **Hata ayıkla** menüsünde **Hata Ayıklamayı Başlat**’a tıklayın. İlk kesme noktası'nın isabetini bekleyin.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Tek bir iş parçacığının çağrı yığınını görüntülemek için

1. Hata Ayıklama **menüsünde, Hata** Ayıkla'nın **üzerine Windows** ve ardından İş Parçacıkları'ya **tıklayın.** İş Parçacıkları **penceresini** iş parçacıklarının alt Visual Studio.

2. Hata **Ayıkla menüsünde,** Hata Ayıkla'Windows üzerine **gelin** ve ardından Çağrı **Yığını'Windows'a tıklayın.** Çağrı **Yığını penceresini alttaki** Visual Studio.

3. İş Parçacıkları penceresinde bir iş **parçacığına çift** tıklar ve bunu geçerli hale sürükleyin. Geçerli iş parçacıklarının sarı bir oku vardır. Geçerli iş parçacığını değiştirdiğimiz zaman, çağrı yığını Çağrı Yığını **penceresinde** görüntülenir.

#### <a name="to-examine-the-parallel-stacks-window"></a>Paralel Yığınlar penceresini incelemek için

1. Hata Ayıklama **menüsünde,** Hata Ayıkla'nın **üzerine Windows** Paralel **Yığınlar'a tıklayın.** Sol üst **köşedeki** kutuda İş Parçacıkları'nın seçili olduğundan emin olun.

     Paralel **Yığınlar penceresini kullanarak** aynı anda birden çok çağrı yığınını tek bir görünümde görüntüebilirsiniz. Aşağıdaki çizimde Çağrı **Yığını penceresinin** üzerindeki Paralel **Yığınlar penceresi gösterilir.**

     ![Paralel Yığınlar penceresinde iş parçacıkları görünümü](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     Ana iş parçacığının çağrı yığını bir kutuda görünür ve diğer dört iş parçacığı için çağrı yığınları başka bir kutuda gruplanır. Yığın çerçeveleri aynı yöntem bağlamlarını paylaştığı için dört iş parçacığı birlikte gruplanır; Başka bir ifadeyle, bunlar aynı yöntemlerdedir: `A` , `B` ve `C` . Aynı kutuyu paylaşırken iş parçacığı kimliklerini ve adlarını görüntülemek için üst bilgisi ( 4 İş Parçacığı) olan kutunun **üzerine gelin.** Geçerli iş parçacığı kalın olarak görüntülenir.

     ![İş parçacığı kimliklerini ve adlarını gösteren araç ipucu](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     Sarı ok, geçerli iş parçacığının etkin yığın çerçevesini gösterir.

     Çağrı Yığını penceresine sağ tıklayarak yığınçerçeveleri (Modül **Adları,** Parametre **Türleri,** Parametre Adları, **Parametre** **Değerleri,** Satır  Numaraları ve **Byte Uzaklıkları)** için ne kadar ayrıntı göster gösterebilirsiniz.

     Bir kutunun çevresindeki mavi vurgu, geçerli iş parçacığının o kutunun bir parçası olduğunu gösterir. Geçerli iş parçacığı, araç ipucundaki kalın yığın çerçevesiyle de gösterilir. İş Parçacıkları penceresinde Ana iş parçacığına çift tıklarsanız, Paralel Yığınlar penceresindeki mavi vurgun uygun şekilde **hareket** ettiğinden görebilirsiniz.

     ![Paralel Yığınlar penceresinde vurgulanan ana iş parçacığı](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Yürütmeyi ikinci kesme noktası kadar sürdürme

1. İkinci kesme noktası isabet edene kadar yürütmeyi devam ettirin, Hata **Ayıkla menüsünde** Devam'a **tıklayın.** Aşağıdaki çizimde ikinci kesme noktası için iş parçacığı ağacı gösterilmiştir.

     ![Birçok dalı gösteren Paralel Yığınlar penceresi](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     İlk kesme noktası, dört iş parçacığının hepsi S.A'dan S.B'ye ve S.C yöntemlerine doğru ilerler. Bu bilgiler Paralel Yığınlar penceresinde **hala görünür** durumdadır, ancak dört iş parçacığı daha fazla ilerledi. Bunlardan biri S.D ve ardından S.E. Bir diğeri S.F, S.G ve S.H.'ye devam etti. Diğer ikisi S.I ve S.J ile devam etti ve bunlardan biri S.K'ye, diğeri de kullanıcı harici koda devam etti.

     İş parçacıklarının iş parçacığı kimliklerini görmek için kutu üst bilgisi **(örneğin, 1** İş Parçacığı veya **2** İş Parçacığı) üzerine gelin. İş parçacığı kimliklerini ve diğer çerçeve ayrıntılarını görmek için yığın çerçevelerinin üzerine gelin. Mavi vurgu geçerli iş parçacığını, sarı ok ise geçerli iş parçacığının etkin yığın çerçevesini gösterir.

     Belirteci iş parçacıkları simgesi (ara çizgiler), eşzamanlı olmayan iş parçacıklarının etkin yığın çerçevelerini gösterir. **Çağrı yığını** penceresinde, kareleri değiştirmek için S. B öğesine çift tıklayın. **Paralel Yığınlar** penceresi, bir yeşil eğri ok simgesi kullanarak geçerli iş parçacığının geçerli yığın çerçevesini gösterir.

     **Iş parçacıkları** penceresinde iş parçacıkları arasında geçiş yapın ve **Paralel Yığınlar** penceresindeki görünümün güncelleştirildiğini gözlemleyin.

     **Paralel Yığınlar** penceresindeki kısayol menüsünü kullanarak başka bir iş parçacığına ya da başka bir iş parçacığının başka bir çerçevesine geçiş yapabilirsiniz. Örneğin, S. J öğesine sağ tıklayın, **çerçeveye geç**' in üzerine gelin ve ardından bir komuta tıklayın.

     ![Yürütmenin paralel yığınları yolu](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     S. C öğesine sağ tıklayın ve **çerçeveye geçiş** yapmak için üzerine gelin. Komutlardan biri, geçerli iş parçacığının yığın çerçevesini gösteren bir onay işaretine sahiptir. Aynı iş parçacığının bu çerçevesine geçebilirsiniz (yalnızca yeşil ok değişir) veya diğer iş parçacığına geçiş yapabilirsiniz (mavi vurgu de değişir). Aşağıdaki çizimde alt menü gösterilmektedir.

     ![J geçerli olduğunda C üzerinde 2 seçenek içeren yığınlar menüsü](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")

     Bir yöntem bağlamı yalnızca bir yığın çerçevesiyle ilişkilendirildiğinde, Box üst bilgisi **1 Iş parçacığı** görüntüler ve çift tıklayarak buna geçiş yapabilirsiniz. Kendisiyle ilişkilendirilmiş 1 ' den fazla çerçeve içeren bir yöntem bağlamına çift tıklarsanız, menü otomatik olarak açılır. Yöntem bağlamlarının üzerine geldiğinizde, sağdaki siyah üçgeni görürsünüz. Bu üçgene tıkladığınızda kısayol menüsü de görüntülenir.

     Çok sayıda iş parçacığına sahip büyük uygulamalar için, yalnızca bir iş parçacığı alt kümesine odaklanmak isteyebilirsiniz. **Paralel Yığınlar** penceresi, yalnızca bayraklı iş parçacıkları için çağrı yığınlarını görüntüleyebilir. İş parçacıklarını işaretlemek için, bir iş parçacığının kısayol menüsünü veya ilk hücresini kullanın.

     Araç çubuğunda, liste kutusunun yanındaki **yalnızca bayraklı** ' i göster düğmesine tıklayın.

     ![Paralel Yığınlar penceresi ve araç ipucu](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")

     Şimdi, yalnızca bayraklı iş parçacığı **Paralel Yığınlar** penceresinde görünür.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Yürütmeyi üçüncü kesme noktasına kadar sürdürmeyi sağlamak için

1. Üçüncü kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın.

     Birden çok iş parçacığı aynı yöntemde olduğunda, ancak yöntem çağrı yığınının başlangıcında olmadığında, yöntem farklı kutular halinde görünür. Geçerli kesme noktasına bir örnek, içinde üç iş parçacığı bulunan ve üç kutuda görünen S. L olur. S.L. çift tıklayın

     ![Paralel Yığınlar penceresindeki yürütme yolu](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")

     Burada ne göründüğünü görebilmeniz için S. L ' nin diğer iki kutuda kalın olduğuna dikkat edin. Hangi çerçevelerin S. L ' ye ve hangi çerçevelere çağrı olduğunu görmek isterseniz, araç çubuğundaki **Yöntem görünümünü aç** düğmesine tıklayın. Aşağıdaki çizimde, **Paralel Yığınlar** penceresinin Yöntem görünümü gösterilmektedir.

     ![Paralel Yığınlar penceresinde Yöntem görünümü](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")

     Diyagramın seçili yöntemi nasıl özetettiğini ve görünümün ortasında kendi kutusuna konumlandırdığını unutmayın. Kasalar ve arayanlar üst ve alt üzerinde görünür. Bu moddan çıkmak için **Yöntem görünümünü değiştirme** düğmesine tekrar tıklayın.

     **Paralel Yığınlar** penceresinin kısayol menüsünde aşağıdaki diğer öğeler de bulunur.

    - **Onaltılık ekran** , ondalık ve onaltılık arasındaki araç ipuçlarında bulunan sayılara geçiş yapar.

    - **sembol Ayarlar** ilgili iletişim kutularını açın.

    - **Iş parçacıklarını kaynakta göster** , kaynak kodunuzda iş parçacıklarının konumunu gösteren kaynak kodunuzda iş parçacığı işaretlerinin görüntülenmesini değiştirir.

    - **Dış kod göster** , Kullanıcı kodunda olmasalar bile tüm kareleri görüntüler. Diyagramın ek çerçevelere uyum sağlayacak şekilde genişletmelerini görmek için bunu deneyin (bunlar için semboller olmadığından soluk olabilir).

2. **Paralel Yığınlar** penceresinde, araç çubuğundaki **geçerli yığın çerçevesine Otomatik Kaydır** düğmesinin açık olduğundan emin olun.

     Büyük diyagramlarınız olduğunda ve sonraki kesme noktasına adımlarınızda, görünümün geçerli iş parçacığının etkin yığın çerçevesine otomatik olarak kaymasını isteyebilirsiniz; diğer bir deyişle, önce kesme noktasına isabet eden iş parçacığı.

3. Devam etmeden önce, **Paralel Yığınlar** penceresinde, sola ve tamamen tüm şekilde kaydırma yapın.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Yürütmenin dördüncü kesme noktasına kadar sürdürülmesi için

1. Dördüncü kesme noktasına ulaşılana kadar yürütmeyi sürdürmek için, **hata ayıklama** menüsünde **devam**' a tıklayın.

     Görünümün nasıl yerleştiğine dikkat edin. İş **parçacıkları** penceresinde iş parçacıklarını değiştirin veya çağrı yığını penceresinde yığın çerçevelerini değiştirin ve görünümün her zaman doğru çerçeveye nasıl **kaydırılacağını** fark edin. **Geçerli araç çerçevesi seçeneğine otomatik kaydırmayı** devre dışı bırakın ve farkı görüntüleyin.

     **Kuşbakışı görünümü** **Paralel Yığınlar** penceresinde büyük diyagramlarla de yardımcı olur. Varsayılan olarak, **kuşbakışı görünümü** açık olur. Ancak, aşağıdaki çizimde gösterildiği gibi pencerenin sağ alt köşesindeki kaydırma çubukları arasındaki düğmeye tıklayarak bunu değiştirebilirsiniz.

     ![&#45;, Paralel Yığınlar penceresinde kuş bakışı görünümü](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     Kuşbakışı görünümünde, çizimi hızla kaydırmak için dikdörtgeni taşıyabilirsiniz.

     Diyagramı herhangi bir yöne taşımanın bir başka yolu da diyagramın boş bir alanına tıklamanız ve istediğiniz yere sürüklemektir.

     Diyagramı yakınlaştırmak ve uzaklaştırmak için fare tekerleğini taşırken CTRL tuşuna basın ve basılı tutun. Alternatif olarak, araç çubuğundaki Yakınlaştır düğmesine tıklayın ve ardından Yakınlaştırma aracını kullanın.

     Ayrıca, **Araçlar** menüsüne tıklayıp **Seçenekler**' e tıklayarak ve ardından **hata ayıklama** düğümü altındaki seçeneği seçerek veya temizleyerek yığınları aşağıdan yukarıya doğru bir şekilde görüntüleyebilirsiniz.

2. Devam etmeden önce, **hata** ayıklama menüsünde, yürütmeyi sonlandırmak Için **hata ayıklamayı Durdur** ' a tıklayın.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Paralel Işler penceresini ve Paralel Yığınlar penceresinin görevler görünümünü kullanma
 Devam etmeden önce önceki yordamları tamamlamanızı öneririz.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>İlk kesme noktasına ulaşılana kadar uygulamayı yeniden başlatmak için

1. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' a tıklayın ve ilk kesme noktasının isabet gelmesini bekleyin.

2. **hata ayıkla** menüsünde, **Windows** ' nin üzerine gelin ve ardından **iş parçacıkları**' ne tıklayın. **Iş parçacıkları** penceresini Visual Studio altına yerleştirin.

3. **hata ayıkla** menüsünde, **Windows** ' nin üzerine gelin ve **çağrı yığını**' na tıklayın. **Çağrı yığını** penceresini Visual Studio altına yerleştirin.

4. Geçerli hale getirmek için **Iş parçacıkları** penceresinde bir iş parçacığına çift tıklayın. Geçerli iş parçacıklarında sarı ok vardır. Geçerli iş parçacığını değiştirdiğinizde diğer pencereler güncelleştirilir. Daha sonra, görevleri inceleyeceğiz.

5. **hata ayıkla** menüsünde, **Windows**' nin üzerine gelin ve ardından **görevler**' e tıklayın. Aşağıdaki çizimde **Görevler** penceresi gösterilmektedir.

     ![Görevler penceresinde dört çalışan görev](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Çalışan her görev için, aynı adlı özellik tarafından döndürülen KIMLIĞINI okuyabilir, onu çalıştıran iş parçacığının KIMLIĞINI ve adını, konumunu (bunun üzerinde tüm çağrı yığınına sahip bir araç ipucu görüntüler) görebilirsiniz. Ayrıca, **görev** sütununun altında göreve geçirilen yöntemi görebilirsiniz; diğer bir deyişle, başlangıç noktası.

     Herhangi bir sütunu sıralayabilirsiniz. Sıralamayı ve yönü gösteren sıralama glifine dikkat edin. Sütunları sola veya sağa sürükleyerek da sıralayabilirsiniz.

     Sarı ok geçerli görevi gösterir. Bir görevi çift tıklayarak veya kısayol menüsünü kullanarak görev geçirebilirsiniz. Görevleri değiştirdiğinizde, temel alınan iş parçacığı geçerli olur ve diğer pencereler güncelleştirilir.

     Bir görevden diğerine el ile geçiş yaptığınızda sarı ok geçer, ancak beyaz ok, hata ayıklayıcının kesintiye neden olan görevi gösterir.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>İkinci kesme noktasına kadar yürütmeyi sürdürmesini sağlamak için

1. İkinci kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın.

     Daha önce, **durum** sütunu tüm görevleri etkin olarak gösterdi, ancak bundan sonra görevlerden ikisi engellenmiştir. Görevler [birçok farklı nedenden dolayı](/dotnet/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism)engellenebilir. **Durum** sütununda, neden engellendiğini öğrenmek için bekleyen bir görevin üzerine gelin. Örneğin, aşağıdaki çizimde, 1. görev 4 ' te bekliyor.

     ![Görevler penceresinde iki bekleyen görev](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     Görev 4 ' te, görev 2 ' ye atanan iş parçacığına ait bir izleyiciyi bekliyor. (Üst bilgi satırına sağ tıklayıp **sütunlar**  >  ' ı seçin. 2. görev iş parçacığı atama değerini görüntülemek için **Iş parçacığı ataması** .

     ![Görevler penceresinde bekleyen görev ve araç ipucu](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     **Görevler** penceresinin ilk sütunundaki bayrağa tıklayarak bir görevi işaretleyebilirsiniz.

     Aynı hata ayıklama oturumunda farklı kesme noktaları arasındaki görevleri izlemek veya **Paralel Yığınlar** penceresinde çağrı yığınları gösterilen görevleri filtrelemek için bayrak uygulayabilirsiniz.

     **Paralel Yığınlar** penceresini daha önce kullandığınızda uygulama iş parçacıklarını görüntülerdi. **Paralel Yığınlar** penceresini yeniden görüntüleyin, ancak bu kez uygulama görevlerini görüntüleyin. Sol üstteki kutudan **Görevler** ' i seçerek bunu yapın. Aşağıdaki çizimde görevler görünümü gösterilmektedir.

     ![Paralel Yığınlar penceresinde görevler görünümü](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     Şu anda yürütülmekte olan iş parçacıkları, **Paralel Yığınlar** penceresinin görevler görünümünde gösterilmez. Ayrıca, görevleri yürüten iş parçacıkları için, görevlerle ilgili olan yığın çerçevelerinden bazıları yığının üst ve alt kısmından filtrelenmiş olur.

     Görevler **penceresini** yeniden görüntüleme. Sütun için kısayol menüsünü görmek için herhangi bir sütun başlığına sağ tıklayın.

     Sütun eklemek veya kaldırmak için kısayol menüsünü kullanabilirsiniz. Örneğin, AppDomain sütunu seçilmez; bu nedenle listede görüntülenmez. **Üst'e tıklayın.** Üst **sütun,** dört görevden herhangi biri için değer olmadan görünür.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Yürütmeyi üçüncü kesme noktası kadar sürdürme

1. Yürütmeyi üçüncü kesme noktası isabet edene kadar devam etmek için Hata **Ayıklama menüsünde** Devam'a **tıklayın.**

     5. görev olan yeni bir görev çalışıyor ve görev 4 artık bekliyor. Durum penceresinde bekleme görevinin üzerine gelerek bunun **neden** olduğunu görebilirsiniz. Üst **sütununda,** 4. görevin 5. görevin üst öğesi olduğunu fark vardır.

     Üst-alt ilişkisini daha iyi görselleştirmek için sütun üst bilgisi satırına sağ tıklayın ve ardından Üst Alt **Görünüm'e tıklayın.** Aşağıdaki çizimi görüyor gerekir.

     ![Görevler&#45;üst öğe alt görünümü](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     4. görev ve 5. görevin aynı iş parçacığında (gizli ise İş Parçacığı **Ataması** sütununu göster) çalıştırıldıklara dikkat olun. Bu bilgiler İş Parçacıkları penceresinde **görüntülenmez;** Burada görmek, Görevler penceresinin bir diğer **avantajıdır.** Bunu onaylamak için Paralel **Yığınlar penceresini** açın. Görevler'i görüntüleyeniden **emin olun.** Görevler penceresinde bu görevlere çift tıklayarak 4. ve 5. **görevleri** bulun. Bunu yapmak için Paralel Yığınlar **penceresindeki mavi vurgu** güncelleştirilir. Paralel Yığınlar penceresindeki araç ipucunı tararsanız 4. ve 5. **görevleri de görebilirsiniz.**

     ![Görev görünümü Yığınlar penceresindeki Görev görünümü'i seçin](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     Paralel **Yığınlar penceresinde** S.P'ye sağ tıklayın ve ardından İş Parçacığına **Git'e tıklayın.** Pencere İş Parçacıkları Görünümüne geçiş gösterir ve karşılık gelen çerçeve görünümdedir. Her iki görevi de aynı iş parçacığında görüyorsunuz.

     ![İş parçacıkları görünümünde vurgulanan iş parçacığı](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Bu, İş Parçacıkları penceresine kıyasla **Paralel Yığınlar** penceresindeki Görevler Görünümü'nin bir diğer **avantajıdır.**

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Yürütmeyi dördüncü kesme noktası kadar sürdürme

1. Yürütmeyi üçüncü kesme noktası isabet edene kadar devam etmek için Hata **Ayıklama menüsünde** Devam'a **tıklayın.** Id sütunu **üst bilgisinde** id sütununa göre sıralamak için tıklayın. Aşağıdaki çizimi görüyor gerekir.

     ![Paralel Yığınlar penceresinde dört görev noktası](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     5. görev tamamlandığından artık görüntülenmez. Bilgisayarınızda böyle bir durum yoksa ve kilitlenme gösterilmezse, F11 tuşuna basarak bir **kez adım atabilirsiniz.**

     Görev 3 ve görev 4 artık birbirini bekliyor ve engellendi. Ayrıca, görev 2'nin en küçükleri olan ve artık zamanlanmış olan 5 yeni görev vardır. Zamanlanmış görevler, kodda başlatmış ancak henüz çalıştırmış olan görevlerdir. Bu nedenle Konum **ve** İş **Parçacığı Ataması** sütunları boştur.

     Paralel **Yığınlar penceresini yeniden** görüntüleme. Her kutunun üst bilgisinde iş parçacığı kimliklerini ve adlarını gösteren bir araç ipucu vardır. Paralel Yığınlar penceresinde Görevler **Görünümüne** geçiş. Aşağıdaki çizimde gösterildiği gibi görev kimliğini ve adını ve görevin durumunu görmek için bir üst bilginin üzerine gelin.

     ![Paralel Yığınlar penceresinde üst bilgi araç ipucu](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")

     Görevleri sütuna göre grupabilirsiniz. Görevler **penceresinde Durum** sütunu üst bilgisinde sağ **tıklayın** ve ardından Durum'a göre **Grupla'ya tıklayın.** Aşağıdaki çizimde, **Duruma göre** gruplanmış Görevler penceresi gösterilir.

     ![Görevler penceresinde gruplanmış görevler](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")

     Ayrıca başka bir sütuna göre de gruplandırebilirsiniz. Görevleri gruplamayla, görevlerin bir alt kümesine odaklanabilirsiniz. Daraltılabilir her grubun birlikte gruplara sahip öğelerin sayısı vardır.

     İncelenecek Görevler **penceresinin** son özelliği, bir göreve sağ tıklarken görüntülenen kısayol menüsüdir.

     Kısayol menüsünde görevin durumuna bağlı olarak farklı komutlar görüntülenir. Komutlar **Copy**, Select All , **Hexadecimal Display**, Switch to **Task**, **Freeze Assigned Thread**, Freeze All Threads But **This**, and **Thaw Assigned Thread**, ve Flag komutlarını **içerebilir.** 

     Bir görevin veya görevlerin temel iş parçacığını dondurabilir veya atanan iş parçacığı dışındaki tüm iş parçacıklarını dondurabilirsiniz. Donmuş iş parçacığı, İş **Parçacıkları** penceresinde olduğu gibi Görevler penceresinde **mavi** bir duraklatma *simgesiyle gösterilir.*

## <a name="summary"></a>Özet
 Bu kılavuzda Paralel Görevler ve **Paralel Yığınlar** **hata ayıklayıcısı** pencereleri gösterildi. Çok iş parçacıklı kod kullanan gerçek projelerde bu pencereleri kullanın. C++, C# veya Visual Basic.

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş Parçacıklı Uygulamalarda Hata Ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [Paralel Programlama](/dotnet/standard/parallel-programming/index)
- [Eşzamanlılık Çalışma Zamanı](/cpp/parallel/concrt/concurrency-runtime)
- [Paralel Yığınlar Penceresini Kullanma](../debugger/using-the-parallel-stacks-window.md)
- [Görevleri Penceresini Kullanma](../debugger/using-the-tasks-window.md)
