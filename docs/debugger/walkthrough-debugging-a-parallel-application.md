---
title: Paralel uygulamada hata ayıklama | Microsoft Docs
description: Paralel Görevler ve Paralel Yığınlar pencerelerinin Visual Studio kullanarak hata ayıklama
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9079fc17da9f89ceae61cbd7d4f086f1db133cf
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416431"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>İzlenecek yol: Visual Studio 'da paralel uygulamada hata ayıklamaC#(, Visual Basic C++,)

Bu izlenecek yol, paralel bir uygulamada hata ayıklamak için paralel **Görevler** ve **Paralel Yığınlar** pencerelerinin nasıl kullanılacağını gösterir. Bu pencereler, [görev paralel kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) veya [Eşzamanlılık çalışma zamanı](/cpp/parallel/concrt/concurrency-runtime)kullanan kodun çalışma zamanı davranışını anlamanıza ve doğrulamanıza yardımcı olur. Bu izlenecek yol, yerleşik kesme noktaları olan örnek kodu sağlıyor. Kod kesildikten sonra, izlenecek yol **paralel görevlerin** ve **Paralel Yığınlar** pencerelerinin nasıl kullanılacağını gösterir.

 Bu izlenecek yol bu görevleri öğretir:

- Nasıl tüm iş parçacığı çağrı yığınlarını tek bir görünümde görüntülenir.

- Uygulamanızda oluşturulan `System.Threading.Tasks.Task` örneklerinin listesini görüntüleme.

- Görev iş parçacıkları yerine gerçek çağrı yığınlarını görüntülemek nasıl.

- **Paralel görevler** ve **Paralel Yığınlar** pencerelerinin koduna gitme.

- Nasıl windows gruplandırma, yakınlaştırma ve diğer ilgili özellikler Ölçekle başa.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yol **yalnızca kendi kodum** etkinleştirildiğini varsayar (Visual Studio 'nun daha yeni sürümlerinde varsayılan olarak etkindir). **Araçlar** menüsünde **Seçenekler**' e tıklayın, **hata ayıklama** düğümünü genişletin, **genel**' i seçin ve ardından yalnızca kendi kodum etkinleştir ' i seçin **(yalnızca yönetilen)** . Bu özelliği ayarlamazsanız, bu izlenecek yolda kullanmaya devam edebilirsiniz, ancak sonuçlarınızı gösterilenlerden farklı olabilir.

## <a name="c-sample"></a>C# örneği
 C# örneği kullanıyorsanız, bu kılavuzda Ayrıca Dış kod gizlidir varsayılır. Dış kodun görüntülenip görüntülenmediğini değiştirmek için **çağrı yığını** penceresinin **ad** tablo başlığına sağ tıklayın ve ardından **dış kodu göster**' i seçin veya temizleyin. Bu özelliği ayarlamazsanız, bu izlenecek yolda kullanmaya devam edebilirsiniz, ancak sonuçlarınızı gösterilenlerden farklı olabilir.

## <a name="c-sample"></a>C++ örnek
 C++ örnek kullanırsanız, bu konudaki dış kod başvurularını yoksayabilirsiniz. Dış kod yalnızca C# örneği için geçerlidir.

## <a name="illustrations"></a>Çizimler
 Bu konudaki resimler, C# örneği çalıştıran bir dört çekirdekli bilgisayarda kaydedilmiş. Bu izlenecek yolu tamamlamak için diğer yapılandırmalar kullanabilirsiniz, ancak çizimler bilgisayarınızda görüntülenen öğesinden farklı olabilir.

## <a name="creating-the-sample-project"></a>Örnek Proje oluşturma
 Bu kılavuzda örnek kod, hiçbir şey yapmaz bir uygulamadır. Yalnızca araç pencereleri paralel uygulamada hata ayıklamak için nasıl kullanılacağını anlamak için hedeftir.

#### <a name="to-create-the-sample-project"></a>Örnek proje oluşturmak için

1. Visual Studio 'Yu açın ve yeni bir proje oluşturun.

   ::: moniker range=">=vs-2019"

   Başlangıç penceresi açık değilse **dosya** > **Başlangıç penceresi**' ni seçin.

   Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Sonra, dil **C#** listesinden **C++** ,, veya **Visual Basic** seçin ve ardından platform listesinden **Windows** ' u seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması (.NET Core)** veya için C++ **konsol uygulaması** şablonu ' nu seçin ve ardından **İleri**' yi seçin.

   > [!NOTE]
   > Doğru şablonu görmüyorsanız **Araçlar** ve özellikler al > ' a gidin. Visual Studio yükleyicisi açan **Araçlar ve Özellikler...** ' a gidin. **.Net masaüstü geliştirme** veya iş yükü **ile C++ masaüstü geliştirmeyi** seçin ve ardından **Değiştir**' i seçin.

   **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusunda bir ad yazın veya varsayılan adı kullanın. Ardından **Oluştur**' u seçin.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde aşağıdakileri seçin:

   - Bir C# uygulama için, **C#Visual**altında **Windows Masaüstü**' nün ardından orta bölmedeki **konsol uygulaması (.NET Framework)** seçeneğini belirleyin.
   - Visual Basic bir uygulama için, **Visual Basic**altında **Windows Masaüstü**' ne ve ardından orta bölmedeki konsol uygulaması ' nı **(.NET Framework)** seçin.
   - Bir C++ uygulama için, **C++Visual**altında **Windows Masaüstü**' nün ardından **Windows konsol uygulaması**' nı seçin.

   **Konsol uygulaması (.NET Core)** C++veya için **konsol** uygulaması projesi şablonu görmüyorsanız, Visual Studio Yükleyicisi açan araçlar **ve Özellikler al** > **Araçlar** ' a gidin. **.Net masaüstü geliştirme** veya iş yükü **ile C++ masaüstü geliştirmeyi** seçin ve ardından **Değiştir**' i seçin.

   Ardından, bir ad yazın veya varsayılan adı kullanın ve **Tamam**' a tıklayın.

   **Tamam**’ı seçin.
   ::: moniker-end

   Yeni bir konsol projesi görüntülenir. Proje oluşturulduktan sonra bir kaynak dosya görüntülenir.

1. Projede .cpp, .cs veya .vb kod dosyasını açın. Boş bir kod dosyası oluşturmak için içeriğini silin.

1. Aşağıdaki kod, seçtiğiniz dilde için boş bir kod dosyasına yapıştırın.

   [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
   [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
   [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]

1. **Dosya** menüsünde **Tümünü Kaydet**' e tıklayın.

1. **Derle** menüsünde **çözümü yeniden derle**' ye tıklayın.

    `Debugger.Break` ( C++ örnekteki`DebugBreak`) için dört çağrı olduğuna dikkat edin, bu nedenle kesme noktaları eklemeniz gerekmez; uygulamayı çalıştırmak, uygulamanın hata ayıklayıcıda en fazla dört kez kesilmesine neden olur.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Kullanarak Paralel Yığınlar penceresi: iş parçacıkları görünümü
 **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' a tıklayın. İlk kesme noktasına isabet tamamlanmasını bekleyin.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Tek bir iş parçacığı çağrı yığınını görüntülemek için

1. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve ardından **iş parçacıkları**' na tıklayın. Visual Studio 'nun alt kısmındaki **Iş parçacıkları** penceresini yerleştir.

2. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve ardından **çağrı yığını**' na tıklayın. **Çağrı yığını** penceresini alt Visual Studio 'ya yerleştirin.

3. Geçerli hale getirmek için **Iş parçacıkları** penceresinde bir iş parçacığına çift tıklayın. Sarı bir ok geçerli iş parçacığı vardır. Geçerli iş parçacığını değiştirdiğinizde çağrı yığını **çağrı yığını** penceresinde görüntülenir.

#### <a name="to-examine-the-parallel-stacks-window"></a>Paralel Yığınlar penceresini incelemek için

1. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve **Paralel Yığınlar**' ı tıklatın. **Iş parçacıklarının** sol üst köşedeki kutuda seçili olduğundan emin olun.

     **Paralel Yığınlar** penceresini kullanarak, aynı anda birden fazla çağrı yığınını tek bir görünümde görüntüleyebilirsiniz. Aşağıdaki çizimde, **çağrı yığını** penceresinin üstündeki **Paralel Yığınlar** penceresi gösterilmektedir.

     ![Paralel Yığınlar penceresinde iş parçacıkları görünümü](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     Ana iş parçacığı çağrı yığınına bir kutuda görünür ve diğer dört iş parçacığı için çağrı yığınlarını başka bir kutuya gruplandırılır. Yığın çerçeveleri aynı yöntem bağlamlarını paylaştığı için dört iş parçacığı birlikte gruplandırılır; diğer bir deyişle, bunlar aynı yöntemlere sahiptir: `A`, `B`ve `C`. Aynı kutuyu paylaşan iş parçacıklarının iş parçacığı kimliklerini ve adlarını görüntülemek için üst bilgiyle (**4 Iş parçacığı**) kutunun üzerine gelin. Geçerli iş parçacığı kalın olarak gösterilir.

     ![İş parçacığı kimliklerini ve adlarını gösteren araç ipucu](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     Sarı ok, geçerli iş parçacığının etkin yığın çerçevesini belirtir.

     **Çağrı yığını** penceresine sağ tıklayarak yığın çerçeveleri (**modül adları**, **parametre türleri**, **parametre adları**, **parametre değerleri**, **satır numaraları** ve **bayt uzaklıkları**) için ne kadar ayrıntı gösterileceğini belirleyebilirsiniz.

     Bir kutu etrafındaki mavi Vurgu, geçerli iş parçacığı kutunun bir parçası olduğunu gösterir. Geçerli iş parçacığı, ayrıca araç ipucunda kalın yığın çerçevesi tarafından belirtilir. Iş parçacıkları penceresinde ana iş parçacığına çift tıklarsanız, **Paralel Yığınlar** penceresindeki mavi vurgunun uygun şekilde taşındığını gözlemleyebilirsiniz.

     ![Paralel Yığınlar penceresinde vurgulanan ana iş parçacığı](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>İkinci kesme noktasına kadar yürütme devam etmek için

1. İkinci kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın. Aşağıdaki resimde ikinci bir kesme noktasında iş parçacığı ağacını gösterir.

     ![Birçok dalı gösteren Paralel Yığınlar penceresi](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     İlk kesme noktasında dört iş parçacığı tüm S.A S.C yöntemlere S.B için oluştu. Bu bilgiler, **Paralel Yığınlar** penceresinde görünmeye devam eder, ancak dört iş parçacığının ilerlemedi daha fazla olması gerekir. S.D ve ardından G.D. bunlardan birinin devamı Başka bir S.F, S.G ve S.H. devamı Diğer iki S.I ve S.J ve orada birinin devamı S.K için gittiği ve diğer dış kullanıcı dışı kod için devam.

     İş parçacıklarının iş parçacığı kimliklerini görmek için, örneğin **1 Iş parçacığı** veya **2 iş**parçacığı üzerinde, Box üstbilgisinin üzerine gelin. İş parçacığı kimlikleri yanı sıra diğer çerçeve ayrıntılarını görmek için yığın çerçevesi gelebilirsiniz. Geçerli iş parçacığı mavi Vurgu gösterir ve geçerli iş parçacığının etkin yığın çerçevesini sarı ok gösterir.

     (Satır interweaved) bez iş parçacığı simgesini çerçevesidir iş parçacığı etkin yığın çerçeveleri gösterir. **Çağrı yığını** penceresinde, kareleri değiştirmek için S. B öğesine çift tıklayın. **Paralel Yığınlar** penceresi, bir yeşil eğri ok simgesi kullanarak geçerli iş parçacığının geçerli yığın çerçevesini gösterir.

     **Iş parçacıkları** penceresinde iş parçacıkları arasında geçiş yapın ve **Paralel Yığınlar** penceresindeki görünümün güncelleştirildiğini gözlemleyin.

     **Paralel Yığınlar** penceresindeki kısayol menüsünü kullanarak başka bir iş parçacığına ya da başka bir iş parçacığının başka bir çerçevesine geçiş yapabilirsiniz. Örneğin, S. J öğesine sağ tıklayın, **çerçeveye geç**' in üzerine gelin ve ardından bir komuta tıklayın.

     ![Yürütmenin paralel yığınları yolu](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     S. C öğesine sağ tıklayın ve **çerçeveye geçiş**yapmak için üzerine gelin. Komutlardan birini geçerli iş parçacığı yığın çerçevesinde belirten bir onay işareti bulunur. (Yalnızca yeşil ok taşınır) aynı iş parçacığının bu çerçeveye geçiş yapabilir veya (Mavi Vurgu, ayrıca taşınır) diğer iş parçacığına geçiş yapabilirsiniz. Aşağıdaki çizim, alt gösterir.

     ![J geçerli olduğunda C üzerinde 2 seçenek içeren yığınlar menüsü](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")

     Bir yöntem bağlamı yalnızca bir yığın çerçevesiyle ilişkilendirildiğinde, Box üst bilgisi **1 Iş parçacığı** görüntüler ve çift tıklayarak buna geçiş yapabilirsiniz. 1'den fazla çerçeve ile ilişkili olan bir yöntemi bağlamı çift tıklayın, ardından menüsü otomatik olarak açılır. Yöntemi bağlamları geldiğinizde sağ siyah üçgeni dikkat edin. Bu üçgen tıklayarak, kısayol menüsünü görüntüler.

     Birçok iş parçacığı olan büyük uygulamalar için yalnızca bir alt kümesi iş parçacıkları üzerinde odaklanmak isteyebilirsiniz. **Paralel Yığınlar** penceresi, yalnızca bayraklı iş parçacıkları için çağrı yığınlarını görüntüleyebilir. İş parçacıklarını için kısayol menüsü veya bir iş parçacığının ilk hücrenin kullanın.

     Araç çubuğunda, liste kutusunun yanındaki **yalnızca bayraklı** ' i göster düğmesine tıklayın.

     ![Paralel Yığınlar penceresi ve araç ipucu](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")

     Şimdi, yalnızca bayraklı iş parçacığı **Paralel Yığınlar** penceresinde görünür.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Üçüncü kesme noktasına kadar yürütme devam etmek için

1. Üçüncü kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın.

     Yöntemi, birden çok iş parçacığı aynı yöntemi olan ancak yöntem çağrı yığınının başında değil, farklı kutusunda görünür. Üç iş parçacığı vardır ve üç kutularında görünen S.L geçerli kesme noktasında örnektir. R. çift tıklayın

     ![Paralel Yığınlar penceresindeki yürütme yolu](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")

     Else göründüğü görebilmeniz için S.L diğer iki kutulara kalın olduğuna dikkat edin. Hangi çerçevelerin S. L ' ye ve hangi çerçevelere çağrı olduğunu görmek isterseniz, araç çubuğundaki **Yöntem görünümünü aç** düğmesine tıklayın. Aşağıdaki çizimde, **Paralel Yığınlar** penceresinin Yöntem görünümü gösterilmektedir.

     ![Paralel Yığınlar penceresinde Yöntem görünümü](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")

     Nasıl diyagramda seçilen metodunda özetlenmiş ve kendi kutusunda görünümün ortasında yerleştirilmiş dikkat edin. Çağıranlar ve çağrılanlar üst ve alt görünür. Bu moddan çıkmak için **Yöntem görünümünü değiştirme** düğmesine tekrar tıklayın.

     **Paralel Yığınlar** penceresinin kısayol menüsünde aşağıdaki diğer öğeler de bulunur.

    - **Onaltılık ekran** , ondalık ve onaltılık arasındaki araç ipuçlarında bulunan sayılara geçiş yapar.

    - **Sembol ayarları** ilgili iletişim kutularını açın.

    - **Iş parçacıklarını kaynakta göster** , kaynak kodunuzda iş parçacıklarının konumunu gösteren kaynak kodunuzda iş parçacığı işaretlerinin görüntülenmesini değiştirir.

    - **Dış kod göster** , Kullanıcı kodunda olmasalar bile tüm kareleri görüntüler. Genişletme (simgeler için erişiminiz yok olduğu için soluk) ek çerçeveler uyum sağlamak için bir diyagram görmeniz için deneyin.

2. **Paralel Yığınlar** penceresinde, araç çubuğundaki **geçerli yığın çerçevesine Otomatik Kaydır** düğmesinin açık olduğundan emin olun.

     Sahip olduğunuz büyük diyagramları ve sonraki kesme noktasına adım, geçerli iş parçacığının etkin yığın çerçevesine otomatik Kaydır görünümüne isteyebilirsiniz; diğer bir deyişle, ilk kesme noktasına isabet iş parçacığı.

3. Devam etmeden önce, **Paralel Yığınlar** penceresinde, sola ve tamamen tüm şekilde kaydırma yapın.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Dördüncü kesme noktasına kadar yürütme devam etmek için

1. Dördüncü kesme noktasına ulaşılana kadar yürütmeyi sürdürmek için, **hata ayıklama** menüsünde **devam**' a tıklayın.

     Bildirim nasıl görünümü autoscrolled içine yerleştir. İş **parçacıkları** penceresinde iş parçacıklarını değiştirin veya çağrı yığını penceresinde yığın çerçevelerini değiştirin ve görünümün her zaman doğru çerçeveye nasıl **kaydırılacağını** fark edin. **Geçerli araç çerçevesi seçeneğine otomatik kaydırmayı** devre dışı bırakın ve farkı görüntüleyin.

     **Kuşbakışı görünümü** **Paralel Yığınlar** penceresinde büyük diyagramlarla de yardımcı olur. Varsayılan olarak, **kuşbakışı görünümü** açık olur. Ancak, bunu arasında kaydırma çubuklarını penceresinin sağ alt köşesindeki düğmeye tıklayarak aşağıdaki çizimde gösterildiği gibi geçiş yapabilirsiniz.

     ![&#45;Paralel Yığınlar penceresinde kuşbakışı görünümü](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     Kuşbakışı göz görünümü'nde, diyagram hızla kaydırmak için dikdörtgen taşıyabilirsiniz.

     Diyagramın herhangi bir yönde taşımak için başka bir yolu, diyagramın boş bir alana tıklayın ve istediğiniz yere sürükleyin oluşturmaktır.

     Diyagramını yakınlaştırma ve uzaklaştırma için basın ve CTRL basılı tutarak fare tekerleğini taşıyın. Alternatif olarak, araç çubuğundaki Yakınlaştır düğmesinin tıklayın ve Yakınlaştırma aracını kullanın.

     Ayrıca, **Araçlar** menüsüne tıklayıp **Seçenekler**' e tıklayarak ve ardından **hata ayıklama** düğümü altındaki seçeneği seçerek veya temizleyerek yığınları aşağıdan yukarıya doğru bir şekilde görüntüleyebilirsiniz.

2. Devam etmeden önce, **hata** ayıklama menüsünde, yürütmeyi sonlandırmak Için **hata ayıklamayı Durdur** ' a tıklayın.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Paralel Görevler penceresi ve Görevler görünümü Paralel Yığınlar penceresini kullanma
 Devam etmeden önce önceki yordamlarını tamamlamanız önerilir.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>İlk kesme noktasına kadar uygulamayı yeniden başlatmasını isabet

1. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' a tıklayın ve ilk kesme noktasının isabet gelmesini bekleyin.

2. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve ardından **iş parçacıkları**' na tıklayın. Visual Studio 'nun alt kısmındaki **Iş parçacıkları** penceresini yerleştir.

3. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve **çağrı yığını**' na tıklayın. **Çağrı yığını** penceresini alt Visual Studio 'ya yerleştirin.

4. Geçerli hale gelmesini sağlamak için **Iş parçacıkları** penceresinde bir iş parçacığına çift tıklayın. Geçerli iş parçacığı, sarı ok vardır. Geçerli iş parçacığı değiştirdiğinizde, diğer windows güncelleştirilir. Ardından, görevleri inceleyeceğiz.

5. **Hata Ayıkla** menüsünde **Windows**' un üzerine gelin ve ardından **Görevler**' e tıklayın. Aşağıdaki çizimde **Görevler** penceresi gösterilmektedir.

     ![Görevler penceresinde dört çalışan görev](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Çalışan her görev için aynı adlı özelliği, kimliği ve konumunu (tüm çağrı yığınına sahip bir araç ipucu görüntüleyen geldiğinizde), çalışan iş parçacığının adı tarafından döndürülen Kimliğini okuyabilir. Ayrıca, **görev** sütununun altında göreve geçirilen yöntemi görebilirsiniz; diğer bir deyişle, başlangıç noktası.

     Herhangi bir sütunu sıralayabilirsiniz. Karakter Sırala yönünü ve sıralama sütunu gösteren dikkat edin. Sütunları sağa veya sola sürükleyerek de yeniden sıralayabilirsiniz.

     Sarı ok geçerli görev gösterir. Görevler, görev çift tıklayarak veya kısayol menüsünü kullanarak geçiş yapabilirsiniz. Görevler arasında geçiş yaptığınızda, temel alınan iş parçacığı geçerli olur ve diğer windows güncelleştirilir.

     El ile bir görevden diğerine geçiş yaptığınızda, sarı ok taşır, ancak beyaz bir ok yine de hata ayıklayıcının neden görev gösterir.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>İkinci kesme noktasına kadar yürütme devam etmek için

1. İkinci kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın.

     Daha önce, **durum** sütunu tüm görevleri etkin olarak gösterdi, ancak bundan sonra görevlerden ikisi engellenmiştir. Görevler, birçok nedenden dolayı engellenebilir. **Durum** sütununda, neden engellendiğini öğrenmek için bekleyen bir görevin üzerine gelin. Örneğin, aşağıdaki çizimde, 3. görev 4. görevde bekliyor.

     ![Görevler penceresinde iki bekleyen görev](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     Görev 4, sırasıyla 2 göreve atanmış iş parçacığı tarafından sahip olunan bir monitörde bekliyor. (Başlık satırına sağ tıklayın ve görev 2 ' de iş parçacığı atama değerini görüntülemek için **Iş parçacığı ataması** > **sütunları** seçin.

     ![Görevler penceresinde bekleyen görev ve araç ipucu](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     **Görevler** penceresinin ilk sütunundaki bayrağa tıklayarak bir görevi işaretleyebilirsiniz.

     Aynı hata ayıklama oturumunda farklı kesme noktaları arasındaki görevleri izlemek veya **Paralel Yığınlar** penceresinde çağrı yığınları gösterilen görevleri filtrelemek için bayrak uygulayabilirsiniz.

     **Paralel Yığınlar** penceresini daha önce kullandığınızda uygulama iş parçacıklarını görüntülerdi. **Paralel Yığınlar** penceresini yeniden görüntüleyin, ancak bu kez uygulama görevlerini görüntüleyin. Sol üstteki kutudan **Görevler** ' i seçerek bunu yapın. Görevler görünümü aşağıda gösterilmiştir.

     ![Paralel Yığınlar penceresinde görevler görünümü](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     Şu anda yürütülmekte olan iş parçacıkları, **Paralel Yığınlar** penceresinin görevler görünümünde gösterilmez. Ayrıca, görevleri yürütme iş parçacığı için bazı görevler ilgili olmayan yığın çerçevelerini yığınının alt ve üst filtre uygulanır.

     **Görevler** penceresini yeniden görüntüleyin. Sütunu için kısayol menüsünü görmek için herhangi bir sütun başlığına sağ tıklayın.

     Sütun ekleme veya kaldırma için kısayol menüsünü kullanabilirsiniz. Örneğin, AppDomain sütun seçilmedi; Bu nedenle, listesinde görüntülenmez. **Üst öğeye**tıklayın. **Üst** sütun dört görevlerden herhangi biri için değer olmadan görüntülenir.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Üçüncü kesme noktasına kadar yürütme devam etmek için

1. Üçüncü kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın.

     Yeni bir görev, görev 5, şu anda çalışıyor ve 4. Görev artık bekliyor. **Durum** penceresindeki bekleme görevinin üzerine gelip gelmediğini görebilirsiniz. **Üst** sütunda, görev 4 ' ün görev 5 ' in üst öğesi olduğunu fark edersiniz.

     Üst-alt ilişkisini daha iyi görselleştirmek için, sütun üst bilgisi satırına sağ tıklayın ve sonra **üst alt öğe görünümü**' ne tıklayın. Aşağıdaki çizim görmeniz gerekir.

     ![Görevler&#45;penceresinde üst alt öğe görünümü](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     Görev 4 ve görev 5 ' in aynı iş parçacığında çalıştığını (gizliyse **Iş parçacığı atama** sütununu göster) unutmayın. Bu bilgiler, **Iş parçacıkları** penceresinde gösterilmez; **Görevler** penceresinin başka bir avantajı burada görüntülenir. Bunu doğrulamak için, **Paralel Yığınlar** penceresini görüntüleyin. **Görevleri**görüntülemekte olduğunuzdan emin olun. **Görevler penceresinde bunlara** çift tıklayarak 4 ve 5. görevleri bulun. Bunu yaptığınızda, **Paralel Yığınlar** penceresinde mavi vurgu güncellenir. **Paralel Yığınlar** penceresinde araç ipuçlarını tarayarak 4 ve 5. görevleri de bulabilirsiniz.

     ![Paralel Yığınlar penceresinde görev görünümü](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     **Paralel Yığınlar** penceresinde, S. P öğesine sağ tıklayın ve ardından **iş parçacığına git ' e**tıklayın. İş Parçacıkları görünümü penceresi geçer ve karşılık gelen bir çerçeve görünür. Her iki görevi aynı iş parçacığında görebilirsiniz.

     ![İş parçacıkları görünümünde vurgulanan iş parçacığı](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Bu, **Iş parçacıkları** penceresi Ile karşılaştırıldığında **Paralel Yığınlar** penceresindeki görevler görünümü ' ne ait başka bir avantajdır.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Dördüncü kesme noktasına kadar yürütme devam etmek için

1. Üçüncü kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın. Kimliğe göre sıralamak için **kimlik** sütun başlığına tıklayın. Aşağıdaki çizim görmeniz gerekir.

     ![Paralel Yığınlar penceresinde dört görev durumu](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     Görev 5 tamamlandığından artık görüntülenmez. Bu durum bilgisayarınızda değilse ve kilitlenme gösterilmezse, **F11**tuşuna basarak bir kez adım adım.

     Görev 3 ve 4. Görev artık birbirleri üzerinde bekleyen ve engellenir. 2\. görev alt ve artık zamanlanmış 5 yeni görevleri de vardır. Zamanlanmış Görevler, kodda başlatıldı ancak henüz çalıştırmadıysanız görevlerdir. Bu nedenle, **konum** ve **iş parçacığı atama** sütunları boştur.

     **Paralel Yığınlar** penceresini yeniden görüntüleyin. Her kutusunun üst bilgisi, iş parçacığı kimlikleri ve adları gösteren bir araç ipucu yok. **Paralel Yığınlar** penceresinde görevler görünümü ' ne geçin. Aşağıdaki çizimde gösterildiği gibi görev kimliği, adı ve görevin durumunu görmek için bir üst bilgisinin üzerinde gelin.

     ![Paralel Yığınlar penceresindeki üstbilgi araç ipucu](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")

     Görevleri sütunu örneğe göre gruplandırabilirsiniz. **Görevler** penceresinde, **durum** sütun başlığına sağ tıklayın ve ardından **duruma göre Gruplandır**' a tıklayın. Aşağıdaki çizim **Görevler** penceresini duruma göre gruplanmış olarak gösterir.

     ![Görevler penceresinde gruplanmış görevler](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")

     Ayrıca, herhangi bir sütuna göre de gruplayabilirsiniz. Gruplandırma görevler tarafından görevlerin bir alt kümesi üzerinde odaklanabilirsiniz. Daraltılabilir her grubu, birlikte gruplanır öğelerinin sayısını sahiptir.

     Görüntülenecek **Görevler** penceresinin son özelliği, bir göreve sağ tıkladığınızda görüntülenen kısayol menüsü olur.

     Kısayol menüsünü görev durumuna bağlı olarak farklı komutları görüntüler. Bu komutlar **kopyalama**, **Tümünü seçme**, **onaltılık görüntü**, **görev değiştirme**, **atanan Iş parçacığını**dondurma, **tüm iş parçacıklarını dondurma, ancak bu**atama ve **bayrağı** **çözme**içerebilir.

     Bir görev veya görevleri temel alınan iş parçacığını Dondur ya da atanan dışındaki tüm iş parçacıklarını dondurma. Dondurulmuş bir iş parçacığı, bir mavi *duraklatma* simgesiyle **iş parçacıkları** penceresinde olduğu gibi **Görevler** penceresinde temsil edilir.

## <a name="summary"></a>Özet
 Bu izlenecek yol, **paralel görevler** ve **Paralel Yığınlar** hata ayıklayıcısı pencerelerini göstermiştir. Bu windows birden çok iş parçacıklı kod kullanan gerçek projelerde kullanın. C++, C# veya Visual Basic içinde yazılan paralel kod inceleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Çoklu Iş parçacıklı uygulamalarda hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [Paralel Programlama](/dotnet/standard/parallel-programming/index)
- [Eşzamanlılık Çalışma Zamanı](/cpp/parallel/concrt/concurrency-runtime)
- [Paralel Yığınlar Penceresini Kullanma](../debugger/using-the-parallel-stacks-window.md)
- [Görevleri Penceresini Kullanma](../debugger/using-the-tasks-window.md)