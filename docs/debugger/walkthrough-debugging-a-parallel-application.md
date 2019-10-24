---
title: Paralel uygulamada hata ayıklama | Microsoft Docs
description: Visual Studio 'da paralel görevler ve Paralel Yığınlar penceresi kullanarak hata ayıklama
ms.date: 03/22/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2213da69561e8868c158a3b2cbcaa8efc6adfaf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728590"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>İzlenecek yol: Visual Studio 'da paralel uygulamada hata ayıklamaC#(, Visual Basic C++,)

Bu izlenecek yol, paralel bir uygulamada hata ayıklamak için paralel **Görevler** ve **Paralel Yığınlar** pencerelerinin nasıl kullanılacağını gösterir. Bu pencereler, [görev paralel kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) veya [Eşzamanlılık çalışma zamanı](/cpp/parallel/concrt/concurrency-runtime)kullanan kodun çalışma zamanı davranışını anlamanıza ve doğrulamanıza yardımcı olur. Bu izlenecek yol, yerleşik kesme noktaları içeren örnek kod sağlar. Kod kesildikten sonra, izlenecek yol **paralel görevlerin** ve **Paralel Yığınlar** pencerelerinin nasıl kullanılacağını gösterir.

 Bu izlenecek yol, şu görevleri öğretir:

- Tüm iş parçacıklarının çağrı yığınlarını tek bir görünümde görüntüleme.

- Uygulamanızda oluşturulan `System.Threading.Tasks.Task` örneklerinin listesini görüntüleme.

- İş parçacıkları yerine görevlerin gerçek çağrı yığınlarını görüntüleme.

- **Paralel görevler** ve **Paralel Yığınlar** pencerelerinin koduna gitme.

- Windows Cope 'un gruplandırma, yakınlaştırma ve diğer ilgili özelliklerle nasıl ölçeklendirilmesi.

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yol **yalnızca kendi kodum** etkinleştirildiğini varsayar (Visual Studio 'nun daha yeni sürümlerinde varsayılan olarak etkindir). **Araçlar** menüsünde **Seçenekler**' e tıklayın, **hata ayıklama** düğümünü genişletin, **genel**' i seçin ve ardından yalnızca kendi kodum etkinleştir ' i seçin **(yalnızca yönetilen)** . Bu özelliği görmüyorsanız, bu yönergeyi kullanmaya devam edebilirsiniz, ancak sonuçlarınız çizimlerden farklı olabilir.

## <a name="c-sample"></a>C#Örnekli
 C# Örneği kullanırsanız, bu Izlenecek yol dış kodun gizli olduğunu de varsayar. Dış kodun görüntülenip görüntülenmediğini değiştirmek için **çağrı yığını** penceresinin **ad** tablo başlığına sağ tıklayın ve ardından **dış kodu göster**' i seçin veya temizleyin. Bu özelliği görmüyorsanız, bu yönergeyi kullanmaya devam edebilirsiniz, ancak sonuçlarınız çizimlerden farklı olabilir.

## <a name="c-sample"></a>C++Örnekli
 C++ Örneği kullanırsanız, bu konudaki dış koda yönelik başvuruları yoksayabilirsiniz. Dış kod yalnızca C# örnek için geçerlidir.

## <a name="illustrations"></a>İllü
 Bu konudaki çizimler C# örneği çalıştıran bir dört çekirdekli bilgisayara kaydedilir. Bu yönergeyi tamamlamak için diğer konfigürasyonları da kullanabilirsiniz, ancak çizimler bilgisayarınızda görüntülendiklerden farklı olabilir.

## <a name="creating-the-sample-project"></a>Örnek proje oluşturma
 Bu izlenecek yolda örnek kod hiçbir şey olmayan bir uygulama içindir. Amaç, bir paralel uygulamada hata ayıklamak için araç pencerelerinin nasıl kullanılacağını öğrenmektir.

#### <a name="to-create-the-sample-project"></a>Örnek proje oluşturmak için

1. Visual Studio 'Yu açın ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **konsol** (veya **c++** ) yazın, **Şablonlar**' ı seçin ve ardından:

    - Ya C# da Visual Basic için, C# veya Visual Basic için **Yeni konsol uygulaması (.NET Framework) projesi oluştur** ' u seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    - İçin C++ **Yeni konsol uygulaması projesi oluştur** ' u seçin C++. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.

    Ardından, bir ad yazın veya varsayılan adı kullanın ve **Oluştur**' a tıklayın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **dosya**  > **Yeni**  > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde aşağıdakileri seçin:

    - Bir C# uygulama için, **C#Visual**altında **Windows Masaüstü**' nün ardından orta bölmedeki **konsol uygulaması (.NET Framework)** seçeneğini belirleyin.
    - Visual Basic bir uygulama için, **Visual Basic**altında **Windows Masaüstü**' ne ve ardından orta bölmedeki konsol uygulaması ' nı **(.NET Framework)** seçin.
    - Bir C++ uygulama için, **C++Visual**altında **Windows Masaüstü**' nün ardından **Windows konsol uygulaması**' nı seçin.

    Ardından, bir ad yazın veya varsayılan adı kullanın ve **Tamam**' a tıklayın.
    ::: moniker-end

    **Konsol uygulaması** proje şablonunu görmüyorsanız **Araçlar** ve Özellikler al  >  ' a gidin ve Visual Studio yükleyicisi açan**Araçlar ve Özellikler...** ' a gidin. **.Net masaüstü geliştirme** veya iş yükü **ile C++ masaüstü geliştirmeyi** seçin ve ardından **Değiştir**' i seçin.

1. Projedeki. cpp,. cs veya. vb kod dosyasını açın. Boş bir kod dosyası oluşturmak için içeriğini silin.

1. Seçtiğiniz dil için aşağıdaki kodu boş kod dosyasına yapıştırın.

   [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
   [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
   [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]

1. **Dosya** menüsünde **Tümünü Kaydet**' e tıklayın.

1. **Derle** menüsünde **çözümü yeniden derle**' ye tıklayın.

    @No__t_0 ( C++ örnekteki `DebugBreak`) için dört çağrı olduğuna dikkat edin, bu nedenle kesme noktaları eklemeniz gerekmez; uygulamayı çalıştırmak, uygulamanın hata ayıklayıcıda en fazla dört kez kesilmesine neden olur.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Paralel Yığınlar penceresini kullanma: Iş parçacıkları görünümü
 **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' a tıklayın. İlk kesme noktasının isabet gelmesini bekleyin.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Tek bir iş parçacığının çağrı yığınını görüntülemek için

1. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve ardından **iş parçacıkları**' na tıklayın. Visual Studio 'nun alt kısmındaki **Iş parçacıkları** penceresini yerleştir.

2. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve ardından **çağrı yığını**' na tıklayın. **Çağrı yığını** penceresini alt Visual Studio 'ya yerleştirin.

3. Geçerli hale getirmek için **Iş parçacıkları** penceresinde bir iş parçacığına çift tıklayın. Geçerli iş parçacıklarında sarı bir ok var. Geçerli iş parçacığını değiştirdiğinizde çağrı yığını **çağrı yığını** penceresinde görüntülenir.

#### <a name="to-examine-the-parallel-stacks-window"></a>Paralel Yığınlar penceresini incelemek için

1. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve **Paralel Yığınlar**' ı tıklatın. **Iş parçacıklarının** sol üst köşedeki kutuda seçili olduğundan emin olun.

     **Paralel Yığınlar** penceresini kullanarak, aynı anda birden fazla çağrı yığınını tek bir görünümde görüntüleyebilirsiniz. Aşağıdaki çizimde, **çağrı yığını** penceresinin üstündeki **Paralel Yığınlar** penceresi gösterilmektedir.

     ![Paralel Yığınlar penceresinde iş parçacıkları görünümü](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     Ana iş parçacığının çağrı yığını bir kutu içinde görünür ve diğer dört iş parçacığı için çağrı yığınları başka bir kutu içinde gruplandırılır. Yığın çerçeveleri aynı yöntem bağlamlarını paylaştığı için dört iş parçacığı birlikte gruplandırılır; diğer bir deyişle, bunlar aynı yöntemlere sahiptir: `A`, `B` ve `C`. Aynı kutuyu paylaşan iş parçacıklarının iş parçacığı kimliklerini ve adlarını görüntülemek için üst bilgiyle (**4 Iş parçacığı**) kutunun üzerine gelin. Geçerli iş parçacığı kalın olarak görüntülenir.

     ![İş parçacığı kimliklerini ve adlarını gösteren araç ipucu](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     Sarı ok, geçerli iş parçacığının etkin yığın çerçevesini gösterir.

     **Çağrı yığınına** sağ tıklayarak yığın çerçeveleri (**modül adları**, **parametre türleri**, **parametre adları**, **parametre değerleri**, **satır numaraları** ve **bayt uzaklıkları**) için ne kadar ayrıntı gösterileceğini belirleyebilirsiniz penceresine.

     Bir kutu etrafında mavi bir vurgu, geçerli iş parçacığının o kutunun bir parçası olduğunu gösterir. Geçerli iş parçacığı araç ipucunda kalın yığın çerçevesiyle da belirtilir. Iş parçacıkları penceresinde ana iş parçacığına çift tıklarsanız, **Paralel Yığınlar** penceresindeki mavi vurgunun uygun şekilde taşındığını gözlemleyebilirsiniz.

     ![Paralel Yığınlar penceresinde vurgulanan ana iş parçacığı](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>İkinci kesme noktasına kadar yürütmeyi sürdürmesini sağlamak için

1. İkinci kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın. Aşağıdaki çizimde, ikinci kesme noktasında iş parçacığı ağacı gösterilmektedir.

     ![Birçok dalı gösteren Paralel Yığınlar penceresi](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     İlk kesme noktasında, hepsi S. A ile s. B-S. C yöntemlerine giden dört iş parçacığı. Bu bilgiler, **Paralel Yığınlar** penceresinde görünmeye devam eder, ancak dört iş parçacığının ilerlemedi daha fazla olması gerekir. Bunlardan biri, S. D ve sonra G.D. . F, S. G ve S.H. ile devam eden başka bir Diğer iki kişi de S. I ve S. J ile devam etti ve bunlardan biri, diğer kullanıcı harici kod ile devam etti.

     İş parçacıklarının iş parçacığı kimliklerini görmek için, örneğin **1 Iş parçacığı** veya **2 iş**parçacığı üzerinde, Box üstbilgisinin üzerine gelin. İş parçacığı kimliklerini ve diğer çerçeve ayrıntılarını görmek için yığın çerçevelerinin üzerine gelin. Mavi vurgu geçerli iş parçacığını gösterir ve sarı ok geçerli iş parçacığının etkin yığın çerçevesini gösterir.

     Kumaş iş parçacıkları simgesi (birbirine bağlı çizgiler), geçerli olmayan iş parçacıklarının etkin yığın çerçevelerini gösterir. **Çağrı yığını** penceresinde, kareleri değiştirmek için S. B öğesine çift tıklayın. **Paralel Yığınlar** penceresi, bir yeşil eğri ok simgesi kullanarak geçerli iş parçacığının geçerli yığın çerçevesini gösterir.

     **Iş parçacıkları** penceresinde iş parçacıkları arasında geçiş yapın ve **Paralel Yığınlar** penceresindeki görünümün güncelleştirildiğini gözlemleyin.

     **Paralel Yığınlar** penceresindeki kısayol menüsünü kullanarak başka bir iş parçacığına ya da başka bir iş parçacığının başka bir çerçevesine geçiş yapabilirsiniz. Örneğin, S. J öğesine sağ tıklayın, **çerçeveye geç**' in üzerine gelin ve ardından bir komuta tıklayın.

     ![Yürütmenin paralel yığınları yolu](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     S. C öğesine sağ tıklayın ve **çerçeveye geçiş**yapmak için üzerine gelin. Komutlardan biri, geçerli iş parçacığının yığın çerçevesini gösteren bir onay işaretine sahiptir. Aynı iş parçacığının bu çerçevesine geçebilirsiniz (yalnızca yeşil ok değişir) veya diğer iş parçacığına geçiş yapabilirsiniz (mavi vurgu de değişir). Aşağıdaki çizimde alt menü gösterilmektedir.

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

    - **Sembol ayarları** ilgili iletişim kutularını açın.

    - **Iş parçacıklarını kaynakta göster** , kaynak kodunuzda iş parçacıklarının konumunu gösteren kaynak kodunuzda iş parçacığı işaretlerinin görüntülenmesini değiştirir.

    - **Dış kod göster** , Kullanıcı kodunda olmasalar bile tüm kareleri görüntüler. Diyagramın ek çerçevelere uyum sağlayacak şekilde genişletmelerini görmek için bunu deneyin (bunlar için semboller olmadığından soluk olabilir).

2. **Paralel Yığınlar** penceresinde, araç çubuğundaki **geçerli yığın çerçevesine Otomatik Kaydır** düğmesinin açık olduğundan emin olun.

     Büyük diyagramlarınız olduğunda ve sonraki kesme noktasına adımlarınızda, görünümün geçerli iş parçacığının etkin yığın çerçevesine otomatik olarak kaymasını isteyebilirsiniz; diğer bir deyişle, önce kesme noktasına isabet eden iş parçacığı.

3. Devam etmeden önce, **Paralel Yığınlar** penceresinde, sola ve tamamen tüm şekilde kaydırma yapın.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Yürütmenin dördüncü kesme noktasına kadar sürdürülmesi için

1. Dördüncü kesme noktasına ulaşılana kadar yürütmeyi sürdürmek için, **hata ayıklama** menüsünde **devam**' a tıklayın.

     Görünümün nasıl yerleştiğine dikkat edin. İş **parçacıkları** penceresinde iş parçacıklarını değiştirin veya çağrı yığını penceresinde yığın çerçevelerini değiştirin ve görünümün her zaman doğru çerçeveye nasıl **kaydırılacağını** fark edin. **Geçerli araç çerçevesi seçeneğine otomatik kaydırmayı** devre dışı bırakın ve farkı görüntüleyin.

     **Kuşbakışı görünümü** **Paralel Yığınlar** penceresinde büyük diyagramlarla de yardımcı olur. Varsayılan olarak, **kuşbakışı görünümü** açık olur. Ancak, aşağıdaki çizimde gösterildiği gibi pencerenin sağ alt köşesindeki kaydırma çubukları arasındaki düğmeye tıklayarak bunu değiştirebilirsiniz.

     ![&#45;Paralel Yığınlar penceresinde kuşbakışı görünümü](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     Kuşbakışı görünümünde, çizimi hızla kaydırmak için dikdörtgeni taşıyabilirsiniz.

     Diyagramı herhangi bir yöne taşımanın bir başka yolu da diyagramın boş bir alanına tıklamanız ve istediğiniz yere sürüklemektir.

     Diyagramı yakınlaştırmak ve uzaklaştırmak için fare tekerleğini taşırken CTRL tuşuna basın ve basılı tutun. Alternatif olarak, araç çubuğundaki Yakınlaştır düğmesine tıklayın ve ardından Yakınlaştırma aracını kullanın.

     Ayrıca, **Araçlar** menüsüne tıklayıp **Seçenekler**' e tıklayarak ve ardından **hata ayıklama** düğümü altındaki seçeneği seçerek veya temizleyerek yığınları aşağıdan yukarıya doğru bir şekilde görüntüleyebilirsiniz.

2. Devam etmeden önce, **hata** ayıklama menüsünde, yürütmeyi sonlandırmak Için **hata ayıklamayı Durdur** ' a tıklayın.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Paralel Işler penceresini ve Paralel Yığınlar penceresinin görevler görünümünü kullanma
 Devam etmeden önce önceki yordamları tamamlamanızı öneririz.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>İlk kesme noktasına ulaşılana kadar uygulamayı yeniden başlatmak için

1. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' a tıklayın ve ilk kesme noktasının isabet gelmesini bekleyin.

2. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve ardından **iş parçacıkları**' na tıklayın. Visual Studio 'nun alt kısmındaki **Iş parçacıkları** penceresini yerleştir.

3. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve **çağrı yığını**' na tıklayın. **Çağrı yığını** penceresini alt Visual Studio 'ya yerleştirin.

4. Geçerli hale gelmesini sağlamak için **Iş parçacıkları** penceresinde bir iş parçacığına çift tıklayın. Geçerli iş parçacıklarında sarı ok vardır. Geçerli iş parçacığını değiştirdiğinizde diğer pencereler güncelleştirilir. Daha sonra, görevleri inceleyeceğiz.

5. **Hata Ayıkla** menüsünde **Windows**' un üzerine gelin ve ardından **Görevler**' e tıklayın. Aşağıdaki çizimde **Görevler** penceresi gösterilmektedir.

     ![Görevler penceresinde dört çalışan görev](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Çalışan her görev için, aynı adlı özellik tarafından döndürülen KIMLIĞINI okuyabilir, onu çalıştıran iş parçacığının KIMLIĞINI ve adını, konumunu (bunun üzerinde tüm çağrı yığınına sahip bir araç ipucu görüntüler) görebilirsiniz. Ayrıca, **görev** sütununun altında göreve geçirilen yöntemi görebilirsiniz; diğer bir deyişle, başlangıç noktası.

     Herhangi bir sütunu sıralayabilirsiniz. Sıralamayı ve yönü gösteren sıralama glifine dikkat edin. Sütunları sola veya sağa sürükleyerek da sıralayabilirsiniz.

     Sarı ok geçerli görevi gösterir. Bir görevi çift tıklayarak veya kısayol menüsünü kullanarak görev geçirebilirsiniz. Görevleri değiştirdiğinizde, temel alınan iş parçacığı geçerli olur ve diğer pencereler güncelleştirilir.

     Bir görevden diğerine el ile geçiş yaptığınızda sarı ok geçer, ancak beyaz ok, hata ayıklayıcının kesintiye neden olan görevi gösterir.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>İkinci kesme noktasına kadar yürütmeyi sürdürmesini sağlamak için

1. İkinci kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın.

     Daha önce, **durum** sütunu tüm görevleri etkin olarak gösterdi, ancak bundan sonra görevlerden ikisi engellenmiştir. Görevler birçok farklı nedenden dolayı engellenebilir. **Durum** sütununda, neden engellendiğini öğrenmek için bekleyen bir görevin üzerine gelin. Örneğin, aşağıdaki çizimde, 1. görev 4 ' te bekliyor.

     ![Görevler penceresinde iki bekleyen görev](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     Görev 4 ' te, görev 2 ' ye atanan iş parçacığına ait bir izleyiciyi bekliyor. (Başlık satırına sağ tıklayın ve görev 2 ' de iş parçacığı atama değerini görüntülemek için**Iş parçacığı ataması**  >  **sütunları** seçin.

     ![Görevler penceresinde bekleyen görev ve araç ipucu](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     **Görevler** penceresinin ilk sütunundaki bayrağa tıklayarak bir görevi işaretleyebilirsiniz.

     Aynı hata ayıklama oturumunda farklı kesme noktaları arasındaki görevleri izlemek veya **Paralel Yığınlar** penceresinde çağrı yığınları gösterilen görevleri filtrelemek için bayrak uygulayabilirsiniz.

     **Paralel Yığınlar** penceresini daha önce kullandığınızda uygulama iş parçacıklarını görüntülerdi. **Paralel Yığınlar** penceresini yeniden görüntüleyin, ancak bu kez uygulama görevlerini görüntüleyin. Sol üstteki kutudan **Görevler** ' i seçerek bunu yapın. Aşağıdaki çizimde görevler görünümü gösterilmektedir.

     ![Paralel Yığınlar penceresinde görevler görünümü](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     Şu anda yürütülmekte olan iş parçacıkları, **Paralel Yığınlar** penceresinin görevler görünümünde gösterilmez. Ayrıca, görevleri çalıştıran iş parçacıkları için, görevlerle ilgili olmayan yığın çerçevelerinden bazıları yığının üst ve alt kısmından filtrelenmiştir.

     **Görevler** penceresini yeniden görüntüleyin. Sütunun kısayol menüsünü görmek için herhangi bir sütun başlığına sağ tıklayın.

     Sütun eklemek veya kaldırmak için kısayol menüsünü kullanabilirsiniz. Örneğin, AppDomain sütunu seçili değildir; Bu nedenle, listede gösterilmez. **Üst öğeye**tıklayın. **Üst** sütun dört görevlerden herhangi biri için değer olmadan görüntülenir.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Yürütmeyi üçüncü kesme noktasına kadar sürdürmeyi sağlamak için

1. Üçüncü kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın.

     Yeni bir görev, görev 5, artık çalışıyor ve görev 4 artık bekliyor. **Durum** penceresindeki bekleme görevinin üzerine gelip gelmediğini görebilirsiniz. **Üst** sütunda, görev 4 ' ün görev 5 ' in üst öğesi olduğunu fark edersiniz.

     Üst-alt ilişkisini daha iyi görselleştirmek için, sütun üst bilgisi satırına sağ tıklayın ve sonra **üst alt öğe görünümü**' ne tıklayın. Aşağıdaki çizimi görmeniz gerekir.

     ![Görevler&#45;penceresinde üst alt öğe görünümü](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     Görev 4 ve görev 5 ' in aynı iş parçacığında çalıştığını (gizliyse **Iş parçacığı atama** sütununu göster) unutmayın. Bu bilgiler, **Iş parçacıkları** penceresinde gösterilmez; **Görevler** penceresinin başka bir avantajı burada görüntülenir. Bunu doğrulamak için, **Paralel Yığınlar** penceresini görüntüleyin. **Görevleri**görüntülemekte olduğunuzdan emin olun. **Görevler penceresinde bunlara** çift tıklayarak 4 ve 5. görevleri bulun. Bunu yaptığınızda, **Paralel Yığınlar** penceresinde mavi vurgu güncellenir. **Paralel Yığınlar** penceresinde araç ipuçlarını tarayarak 4 ve 5. görevleri de bulabilirsiniz.

     ![Paralel Yığınlar penceresinde görev görünümü](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     **Paralel Yığınlar** penceresinde, S. P öğesine sağ tıklayın ve ardından **iş parçacığına git ' e**tıklayın. Pencere, Iş parçacıkları görünümüne geçer ve ilgili çerçeve görünümüdür. Aynı iş parçacığında her iki görevi de görebilirsiniz.

     ![İş parçacıkları görünümünde vurgulanan iş parçacığı](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Bu, **Iş parçacıkları** penceresi Ile karşılaştırıldığında **Paralel Yığınlar** penceresindeki görevler görünümü ' ne ait başka bir avantajdır.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Yürütmenin dördüncü kesme noktasına kadar sürdürülmesi için

1. Üçüncü kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın. Kimliğe göre sıralamak için **kimlik** sütun başlığına tıklayın. Aşağıdaki çizimi görmeniz gerekir.

     ![Paralel Yığınlar penceresinde dört görev durumu](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     5\. görev tamamlandığı için artık görüntülenmiyor. Bu durum bilgisayarınızda değilse ve kilitlenme gösterilmezse, **F11**tuşuna basarak bir kez adım adım.

     Görev 3 ve görev 4 artık birbirini bekliyor ve engelleniyor. 2\. görevin alt öğesi olan ve şimdi zamanlanmış 5 yeni görev da vardır. Zamanlanan görevler, kodda başlatılmış ancak henüz çalıştırılmayan görevlerdir. Bu nedenle, **konum** ve **iş parçacığı atama** sütunları boştur.

     **Paralel Yığınlar** penceresini yeniden görüntüleyin. Her kutunun üst bilgisinde, iş parçacığı kimliklerini ve adlarını gösteren bir araç ipucu vardır. **Paralel Yığınlar** penceresinde görevler görünümü ' ne geçin. Aşağıdaki çizimde gösterildiği gibi, görev KIMLIĞI ve adını ve görevin durumunu görmek için bir üstbilginin üzerine gelin.

     ![Paralel Yığınlar penceresindeki üstbilgi araç ipucu](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")

     Görevleri sütuna göre gruplandırabilirsiniz. **Görevler** penceresinde, **durum** sütun başlığına sağ tıklayın ve ardından **duruma göre Gruplandır**' a tıklayın. Aşağıdaki çizim **Görevler** penceresini duruma göre gruplanmış olarak gösterir.

     ![Görevler penceresinde gruplanmış görevler](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")

     Ayrıca, başka bir sütuna göre gruplandırabilirsiniz. Görevleri gruplandırarak, bir görev alt kümesine odaklanırsınız. Her daraltılabilir Grup, birlikte gruplanmış öğelerin sayısına sahiptir.

     Görüntülenecek **Görevler** penceresinin son özelliği, bir göreve sağ tıkladığınızda görüntülenen kısayol menüsü olur.

     Kısayol menüsü, görevin durumuna bağlı olarak farklı komutları görüntüler. Bu komutlar **kopyalama**, **Tümünü seçme**, **onaltılık görüntü**, **görev değiştirme**, **atanan Iş parçacığını**dondurma, **tüm iş parçacıklarını dondurma, ancak bu**atama ve **bayrağı** **çözme**içerebilir.

     Bir görevin veya görevlerin temel alınan iş parçacığını dondurabilir veya atanmış olanı hariç tüm iş parçacıklarını dondurabilirsiniz. Dondurulmuş bir iş parçacığı, bir mavi *duraklatma* simgesiyle **iş parçacıkları** penceresinde olduğu gibi **Görevler** penceresinde temsil edilir.

## <a name="summary"></a>Özet
 Bu izlenecek yol, **paralel görevler** ve **Paralel Yığınlar** hata ayıklayıcısı pencerelerini göstermiştir. Bu pencereleri, çok iş parçacıklı kod kullanan gerçek projeler üzerinde kullanın. C++, C#Veya Visual Basic yazılmış paralel kodu inceleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Çoklu Iş parçacıklı uygulamalarda hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [Paralel Programlama](/dotnet/standard/parallel-programming/index)
- [Eşzamanlılık Çalışma Zamanı](/cpp/parallel/concrt/concurrency-runtime)
- [Paralel Yığınlar Penceresini Kullanma](../debugger/using-the-parallel-stacks-window.md)
- [Görevleri Penceresini Kullanma](../debugger/using-the-tasks-window.md)