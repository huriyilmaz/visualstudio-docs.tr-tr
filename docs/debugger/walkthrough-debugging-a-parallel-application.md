---
title: Paralel uygulamada hata ayıklama | Microsoft Docs
description: Visual Studio içinde paralel görevler ve Paralel Yığınlar penceresi kullanarak hata ayıklayın
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9e42a6640c2709ccabf7ca2c6a9987e29f31d095
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635964"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>izlenecek yol: Visual Studio paralel uygulamada hata ayıklama (C#, Visual Basic, C++)

Bu izlenecek yol, paralel bir uygulamada hata ayıklamak için paralel **Görevler** ve **Paralel Yığınlar** pencerelerinin nasıl kullanılacağını gösterir. Bu pencereler, [görev paralel kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) veya [Eşzamanlılık çalışma zamanı](/cpp/parallel/concrt/concurrency-runtime)kullanan kodun çalışma zamanı davranışını anlamanıza ve doğrulamanıza yardımcı olur. Bu izlenecek yol, yerleşik kesme noktaları içeren örnek kod sağlar. Kod kesildikten sonra, izlenecek yol **paralel görevlerin** ve **Paralel Yığınlar** pencerelerinin nasıl kullanılacağını gösterir.

 Bu izlenecek yol, şu görevleri öğretir:

- Tüm iş parçacıklarının çağrı yığınlarını tek bir görünümde görüntüleme.

- `System.Threading.Tasks.Task`Uygulamanızda oluşturulan örneklerin listesini görüntüleme.

- İş parçacıkları yerine görevlerin gerçek çağrı yığınlarını görüntüleme.

- **Paralel görevler** ve **Paralel Yığınlar** pencerelerinin koduna gitme.

- Windows Cope 'un gruplandırma, yakınlaştırma ve diğer ilgili özelliklerle nasıl ölçeklendirilmesi.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yol **yalnızca kendi kodum** etkinleştirildiğini varsayar (Visual Studio daha yeni sürümlerinde varsayılan olarak etkindir). **Araçlar** menüsünde **Seçenekler**' e tıklayın, **hata ayıklama** düğümünü genişletin, **genel**' i seçin ve ardından yalnızca kendi kodum etkinleştir ' i seçin **(yalnızca yönetilen)**. Bu özelliği görmüyorsanız, bu yönergeyi kullanmaya devam edebilirsiniz, ancak sonuçlarınız çizimlerden farklı olabilir.

## <a name="c-sample"></a>C# örneği
 C# örneğini kullanıyorsanız bu izlenecek yol, dış kodun gizli olduğunu de varsayar. Dış kodun görüntülenip görüntülenmediğini değiştirmek için **çağrı yığını** penceresinin **ad** tablo başlığına sağ tıklayın ve ardından **dış kodu göster**' i seçin veya temizleyin. Bu özelliği görmüyorsanız, bu yönergeyi kullanmaya devam edebilirsiniz, ancak sonuçlarınız çizimlerden farklı olabilir.

## <a name="c-sample"></a>C++ örneği
 C++ örneğini kullanırsanız, bu konudaki dış koda yönelik başvuruları yoksayabilirsiniz. Dış kod yalnızca C# örneği için geçerlidir.

## <a name="illustrations"></a>Çizimler
 Bu konudaki çizimler, C# örneğini çalıştıran dört çekirdekli bir bilgisayara kaydedilir. Bu yönergeyi tamamlamak için diğer konfigürasyonları da kullanabilirsiniz, ancak çizimler bilgisayarınızda görüntülendiklerden farklı olabilir.

## <a name="creating-the-sample-project"></a>Örnek Project oluşturma
 Bu izlenecek yolda örnek kod hiçbir şey olmayan bir uygulama içindir. Amaç, bir paralel uygulamada hata ayıklamak için araç pencerelerinin nasıl kullanılacağını öğrenmektir.

#### <a name="to-create-the-sample-project"></a>Örnek proje oluşturmak için

1. Visual Studio açın ve yeni bir proje oluşturun.

   ::: moniker range=">=vs-2019"

   Başlangıç penceresi açık değilse **Dosya** > **Başlangıç penceresi**' ni seçin.

   Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. ardından, dil listesinden **C#**, **C++** veya **Visual Basic** seçin ve ardından Platform listesinden **Windows** öğesini seçin.

   Dil ve platform filtrelerini uyguladıktan sonra .NET Core veya C++ **konsol uygulamasını** seçin ve ardından **İleri**' yi seçin.

   > [!NOTE]
   > doğru şablonu görmüyorsanız **araçlar**  >  **ve özellikler al..**. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. **.NET Core platformlar arası geliştirme** veya C++ iş yükü **ile masaüstü geliştirme** seçeneklerini belirleyin ve ardından **Değiştir**' i seçin.

   **yeni projeyi yapılandırın** penceresinde bir ad yazın veya **Project ad** kutusunda varsayılan adı kullanın. Sonra, **İleri** veya **Oluştur**' u seçin, hangisi kullanılabilir seçeneği vardır.

   .NET Core için, önerilen hedef Framework veya .NET 6 ' ı seçin ve ardından **Oluştur**' u seçin.

   ::: moniker-end
   ::: moniker range="vs-2017"
   üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin. **Yeni proje** iletişim kutusunun sol bölmesinde aşağıdakileri seçin:

   - c# uygulaması için, **Visual C#** altında, **masaüstü Windows**' yi seçin ve ardından ortadaki bölmede **konsol uygulaması ' nı (.NET Framework)** seçin.
   - Visual Basic bir uygulama için, **Visual Basic** altında **masaüstü Windows**' yı seçin ve ardından orta bölmedeki **konsol uygulaması (.NET Framework)** seçeneğini belirleyin.
   - C++ uygulaması için, **Visual C++** altında masaüstü ' ne **Windows** ve ardından **Windows konsol uygulaması**' nı seçin.

   **konsol uygulamasını (.net Core)** görmüyorsanız veya C++ için **konsol uygulaması** proje şablonu ' na **gidin araçlar**  >  **ve özellikler al..**. ' a giderek Visual Studio Yükleyicisi açılır. C++ iş yüküyle **.net masaüstü geliştirme** veya **masaüstü geliştirme** seçeneklerini belirleyin ve ardından **Değiştir**' i seçin.

   Ardından, bir ad yazın veya varsayılan adı kullanın ve **Tamam**' a tıklayın.

   **Tamam**’ı seçin.
   ::: moniker-end

   Yeni bir konsol projesi görüntülenir. Proje oluşturulduktan sonra bir kaynak dosya görüntülenir.

1. Projedeki. cpp,. cs veya. vb kod dosyasını açın. Boş bir kod dosyası oluşturmak için içeriğini silin.

1. Seçtiğiniz dil için aşağıdaki kodu boş kod dosyasına yapıştırın.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/debugger/cs/s.cs" id="Snippet1":::
   :::code language="cpp" source="../snippets/cpp/VS_Snippets_Misc/debugger/cpp/beta2_native.cpp" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Misc/debugger/vb/module1.vb" id="Snippet1":::

1. **Dosya** menüsünde **Tümünü Kaydet**’e tıklayın.

1. **Derle** menüsünde **çözümü yeniden derle**' ye tıklayın.

    İçin dört çağrı olduğunu unutmayın `Debugger.Break` ( `DebugBreak` C++ örneğinde), bu nedenle kesme noktaları eklemeniz gerekmez; uygulamayı çalıştırmak, hata ayıklayıcıda en fazla dört kez kesintiye neden olur.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Paralel Yığınlar penceresini kullanma: Iş parçacıkları görünümü
 **Hata ayıkla** menüsünde **Hata Ayıklamayı Başlat**’a tıklayın. İlk kesme noktasının isabet gelmesini bekleyin.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Tek bir iş parçacığının çağrı yığınını görüntülemek için

1. **hata ayıkla** menüsünde, **Windows** ' nin üzerine gelin ve ardından **iş parçacıkları**' ne tıklayın. **Iş parçacıkları** penceresini Visual Studio altına yerleştirin.

2. **hata ayıkla** menüsünde, **Windows** ' nin üzerine gelin ve ardından **çağrı yığını**' na tıklayın. **Çağrı yığını** penceresini alt Visual Studio yerleştir.

3. Geçerli hale getirmek için **Iş parçacıkları** penceresinde bir iş parçacığına çift tıklayın. Geçerli iş parçacıklarında sarı bir ok var. Geçerli iş parçacığını değiştirdiğinizde çağrı yığını **çağrı yığını** penceresinde görüntülenir.

#### <a name="to-examine-the-parallel-stacks-window"></a>Paralel Yığınlar penceresini incelemek için

1. **hata ayıkla** menüsünde, **Windows** ' nin üzerine gelin ve **paralel yığınlar**' ı tıklatın. **Iş parçacıklarının** sol üst köşedeki kutuda seçili olduğundan emin olun.

     **Paralel Yığınlar** penceresini kullanarak, aynı anda birden fazla çağrı yığınını tek bir görünümde görüntüleyebilirsiniz. Aşağıdaki çizimde, **çağrı yığını** penceresinin üstündeki **Paralel Yığınlar** penceresi gösterilmektedir.

     ![Paralel Yığınlar penceresinde iş parçacıkları görünümü](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     Ana iş parçacığının çağrı yığını bir kutu içinde görünür ve diğer dört iş parçacığı için çağrı yığınları başka bir kutu içinde gruplandırılır. Yığın çerçeveleri aynı yöntem bağlamlarını paylaştığı için dört iş parçacığı birlikte gruplandırılır; diğer bir deyişle, bu yöntemler aynı yöntemlerde: `A` , `B` ve `C` . Aynı kutuyu paylaşan iş parçacıklarının iş parçacığı kimliklerini ve adlarını görüntülemek için üst bilgiyle (**4 Iş parçacığı**) kutunun üzerine gelin. Geçerli iş parçacığı kalın olarak görüntülenir.

     ![İş parçacığı kimliklerini ve adlarını gösteren araç ipucu](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     Sarı ok, geçerli iş parçacığının etkin yığın çerçevesini gösterir.

     **Çağrı yığını** penceresine sağ tıklayarak yığın çerçeveleri (**modül adları**, **parametre türleri**, **parametre adları**, **parametre değerleri**, **satır numaraları** ve **bayt uzaklıkları**) için ne kadar ayrıntı gösterileceğini belirleyebilirsiniz.

     Bir kutu etrafında mavi bir vurgu, geçerli iş parçacığının o kutunun bir parçası olduğunu gösterir. Geçerli iş parçacığı araç ipucunda kalın yığın çerçevesiyle da belirtilir. Iş parçacıkları penceresinde ana iş parçacığına çift tıklarsanız, **Paralel Yığınlar** penceresindeki mavi vurgunun uygun şekilde taşındığını gözlemleyebilirsiniz.

     ![Paralel Yığınlar penceresinde vurgulanan ana iş parçacığı](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>İkinci kesme noktasına kadar yürütmeyi sürdürmesini sağlamak için

1. İkinci kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın. Aşağıdaki çizimde, ikinci kesme noktasında iş parçacığı ağacı gösterilmektedir.

     ![Birçok dalı gösteren Paralel Yığınlar penceresi](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     İlk kesme noktasında, hepsi S. A ile s. B-S. C yöntemlerine giden dört iş parçacığı. Bu bilgiler, **Paralel Yığınlar** penceresinde görünmeye devam eder, ancak dört iş parçacığının ilerlemedi daha fazla olması gerekir. Bunlardan biri, S. D ve sonra G.D. . F, S. G ve S.H. ile devam eden başka bir Diğer iki kişi de S. I ve S. J ile devam etti ve bunlardan biri, diğer kullanıcı harici kod ile devam etti.

     İş parçacıklarının iş parçacığı kimliklerini görmek için, örneğin **1 Iş parçacığı** veya **2 iş** parçacığı üzerinde, Box üstbilgisinin üzerine gelin. İş parçacığı kimliklerini ve diğer çerçeve ayrıntılarını görmek için yığın çerçevelerinin üzerine gelin. Mavi vurgu geçerli iş parçacığını gösterir ve sarı ok geçerli iş parçacığının etkin yığın çerçevesini gösterir.

     Kumaş iş parçacıkları simgesi (birbirine bağlı çizgiler), geçerli olmayan iş parçacıklarının etkin yığın çerçevelerini gösterir. **Çağrı yığını** penceresinde, kareleri değiştirmek için S. B öğesine çift tıklayın. **Paralel Yığınlar** penceresi, bir yeşil eğri ok simgesi kullanarak geçerli iş parçacığının geçerli yığın çerçevesini gösterir.

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

1. Yürütmeyi üçüncü kesme noktası isabet edene kadar devam etmek için Hata **Ayıkla menüsünde** Devam'a **tıklayın.**

     5. görev olan yeni bir görev çalışıyor ve görev 4 artık bekliyor. Durum penceresinde bekleme görevinin üzerine gelerek bunun **neden** olduğunu görebilirsiniz. Üst **sütununda,** 4. görevin 5. görevin üst öğesi olduğunu fark vardır.

     Üst-alt ilişkisini daha iyi görselleştirmek için sütun üst bilgisi satırına sağ tıklayın ve ardından Üst Alt **Görünüm'e tıklayın.** Aşağıdaki çizimi görüyor gerekir.

     ![Görevler&#45;üst öğe alt görünümü](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     4. görev ve 5. görevin aynı iş parçacığında (gizli ise İş Parçacığı **Ataması** sütununu göster) çalıştırıldıklara dikkat olun. Bu bilgiler İş Parçacıkları penceresinde **görüntülenmez;** Burada görmek, Görevler penceresinin bir diğer **avantajıdır.** Bunu onaylamak için Paralel **Yığınlar penceresini** açın. Görevler'i görüntüleyeniden **emin olun.** Görevler penceresinde bu görevlere çift tıklayarak 4. ve 5. **görevleri** bulun. Bunu yapmak için Paralel Yığınlar **penceresindeki mavi vurgu** güncelleştirilir. Paralel Yığınlar penceresindeki araç ipucunı tararsanız 4. ve 5. **görevleri de görebilirsiniz.**

     ![Görev görünümü Yığınlar penceresindeki bağlantı](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     Paralel **Yığınlar penceresinde** S.P'ye sağ tıklayın ve ardından İş Parçacığına **Git'e tıklayın.** Pencere İş Parçacıkları Görünümüne geçiş gösterir ve karşılık gelen çerçeve görünümdedir. Her iki görevi de aynı iş parçacığında görüyorsunuz.

     ![İş parçacıkları görünümünde vurgulanan iş parçacığı](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Bu, İş Parçacıkları penceresine kıyasla **Paralel Yığınlar** penceresindeki Görevler Görünümü'nin bir diğer **avantajıdır.**

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Yürütmeyi dördüncü kesme noktası kadar sürdürme

1. Yürütmeyi üçüncü kesme noktası isabet edene kadar devam etmek için Hata **Ayıkla menüsünde** Devam'a **tıklayın.** Id sütunu **üst bilgisinde** id sütununa göre sıralamak için tıklayın. Aşağıdaki çizimi görüyor gerekir.

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
