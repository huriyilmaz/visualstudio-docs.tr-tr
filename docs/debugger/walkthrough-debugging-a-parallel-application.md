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
ms.openlocfilehash: 4663892ef011841ed401331009c2d8f05b63814a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627789"
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

   .NET Core için, önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.

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

     Kumaş iş parçacıkları simgesi (birbirine bağlı çizgiler), geçerli olmayan iş parçacıklarının etkin yığın çerçevelerini gösterir. Çağrı Yığını **penceresinde, çerçeveleri** değiştirmek için S.B'ye çift tıklayın. Paralel **Yığınlar penceresi,** yeşil bir eğri ok simgesi kullanarak geçerli iş parçacığının geçerli yığın çerçevesini gösterir.

     İş Parçacıkları **penceresinde** iş parçacıkları arasında geçiş yapmak ve Paralel Yığınlar penceresindeki **görünümün güncelleştirilmiş** olduğunu gözlemlemek.

     Paralel Yığınlar penceresindeki kısayol menüsünü kullanarak başka bir iş parçacığına veya başka bir iş parçacığının **çerçevesine geçebilirsiniz.** Örneğin, S.J'ye sağ tıklayın, Çerçeveye **Geçiş'in üzerine gelin** ve ardından bir komuta tıklayın.

     ![Paralel Yığınlar Yürütme Yolu](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     S.C'ye sağ tıklayın ve Çerçeveye **Geçiş'in üzerine gelin.** Komutlardan biri, geçerli iş parçacığının yığın çerçevesini gösteren bir onay işaretine sahip. Aynı iş parçacığının bu çerçevesine geçiş (yalnızca yeşil ok hareket eder) veya diğer iş parçacığına geçebilirsiniz (mavi vurgu da hareket eder). Aşağıdaki çizimde alt menüsü gösterilmiştir.

     ![J geçerliyken C'de 2 seçeneğin yer alan yığınlar menüsü](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")

     Bir yöntem bağlamı yalnızca bir yığın çerçevesiyle ilişkili olduğunda, kutu üst bilgisi **1** İş Parçacığı görüntüler ve çift tıklayarak buna geçebilirsiniz. İlişkili 1'den fazla çerçeveye sahip bir yöntem bağlamına çift tıklarsanız menü otomatik olarak açılır. Yöntem bağlamların üzerine gelindiğinde sağ uçta siyah üçgene dikkat edin. Bu üçgene tıklarken kısayol menüsü de görüntülenir.

     Çok sayıda iş parçacığına sahip büyük uygulamalar için yalnızca bir iş parçacığı alt kümesine odaklanmak istiyor olabilir. Paralel **Yığınlar penceresi** yalnızca bayraklı iş parçacıkları için çağrı yığınlarını görüntüler. İş parçacıklarını bayrakla bayrak olarak kullanmak için kısayol menüsünü veya bir iş parçacığının ilk hücreyi kullanın.

     Araç çubuğunda, liste kutusunun **yanındaki Yalnızca Bayraklı** Göster düğmesine tıklayın.

     ![Paralel Yığınlar penceresi ve araç ipucu](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")

     Şimdi, Paralel Yığınlar penceresinde yalnızca **bayraklı iş parçacığı** gösterilir.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Yürütmeyi üçüncü kesme noktası kadar sürdürme

1. Yürütmeyi üçüncü kesme noktası isabet edene kadar devam etmek için Hata **Ayıklama menüsünde** Devam'a **tıklayın.**

     Birden çok iş parçacığı aynı yöntemde olduğunda ancak yöntem çağrı yığınının başında yer alemese de yöntem farklı kutularda görünür. Geçerli kesme noktası örneği, içinde üç iş parçacığı bulunan ve üç kutu içinde görünen S.L'tir. S.L.'ye çift tıklayın.

     ![Paralel Yığınlar penceresinde yürütme yolu](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")

     Diğer iki kutu içinde S.L'nin kalın olduğunu ve başka bir yerde görüntülendiğinden bunu gördüğünüze dikkat olun. S.L'ye çağrılan kareleri ve çağıran çerçeveleri görmek için araç çubuğundaki Yöntem Görünümünü **Değiştir** düğmesine tıklayın. Aşağıdaki çizimde Paralel Yığınlar **penceresinin yöntem görünümü gösterilmiştir.**

     ![Paralel Yığınlar penceresinde yöntem görünümü](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")

     Diyagramın seçili yöntemin üzerine nasıl özetlenene ve görünümün ortasındaki kendi kutusuna nasıl konumlatır? Çağrıyı yapanlar ve çağıranlar üst ve altta görünür. Bu **moddan ayrılmak için Yöntem** Görünümünü Değiştir düğmesine yeniden tıklayın.

     Paralel Yığınlar **penceresinin kısayol menüsünde** aşağıdaki diğer öğeler de vardır.

    - **Onaltılık Görüntü,** araç ipucunda yer alan sayıları ondalık ve onaltılık arasında geçişler.

    - **Sembol Ayarlar** ilgili iletişim kutularını açın.

    - **Kaynakta İş** Parçacıklarını Göster, kaynak kodundaki iş parçacıklarının konumunu gösteren kaynak kodundaki iş parçacığı işaretçilerinin imleçlerini gösterir.

    - **Dış Kodu Göster,** kullanıcı kodunda yer alan tüm kareleri görüntüler. Diyagramın ek karelere uyum sağlayacak şekilde genişleyebildisini deneyin (bu çerçeveler için sembollere sahip olmadığınız için soluk olabilir).

2. Paralel **Yığınlar penceresinde,** araç çubuğundaki Geçerli Yığın **Çerçevesine Otomatik** Kaydırma düğmesinin açık olduğundan emin olun.

     Büyük diyagramlarınız olduğunda ve sonraki kesme noktası adımlarını atlarken, görünümün geçerli iş parçacığının etkin yığın çerçevesine otomatik olarak kaydırması istebilirsiniz; diğer bir ifadeyle, önce kesme noktasıyla isabet alan iş parçacığı.

3. Devam etmek için Paralel **Yığınlar** penceresinde sola ve aşağı doğru kaydırın.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Yürütmeyi dördüncü kesme noktası kadar sürdürme

1. Dördüncü kesme noktası isabet edene kadar yürütmeyi devam ettirin, Hata **Ayıkla menüsünde** Devam'a **tıklayın.**

     Görünümün otomatik olarak nasıl yerinde kaydına dikkat edersiniz. İş Parçacıkları penceresindeki **iş** parçacıklarını  veya Çağrı Yığını penceresinde yığın çerçevelerini değiştirme ve görünümün her zaman doğru çerçeveye nasıl otomatik olarak kaydına dikkat edin. Otomatik **Kaydırmayı Geçerli Araç Çerçevesine Kaydır seçeneğini** kapatın ve farkı görüntüden seçin.

     **Bird's Eye View,** Paralel Yığınlar penceresindeki büyük **diyagramlarda da yardımcı** olur. Varsayılan olarak **Bird'in Göz Görünümü** açıktır. Ancak, aşağıdaki çizimde gösterildiği gibi pencerenin sağ alt köşesindeki kaydırma çubukları arasındaki düğmeye tıklayarak bu düğmeyi değiştirebilirsiniz.

     ![Paralel Yığınlar penceresinde&#45;kuş görünümü](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     Kuş bakış görünümünde dikdörtgeni hareket ettirarak diyagramın etrafında hızlıca kaydırma yapabilirsiniz.

     Diyagramı herhangi bir yönde taşımanın bir diğer yolu da diyagramın boş bir alanına tıklamak ve istediğiniz yere sürüklemektir.

     Diyagramı yakınlaştırıp uzaklaştırmak için fare tekerleğini hareket ettirirken CTRL tuşunu basılı tutun. Alternatif olarak, araç çubuğundaki Yakınlaştır düğmesine tıklayın ve ardından Yakınlaştırma aracını kullanın.

     Ayrıca, Araçlar menüsüne, Seçenekler'e tıklayarak ve ardından Hata ayıklama  düğümü altındaki seçeneği seçerek veya temizleerek yığınları alttan yukarıya değil, yukarı yönlü **olarak görüntüebilirsiniz.**

2. Devam etmek için Hata Ayıklama **menüsünde, yürütmeyi** durdurmak için **Hata Ayıklamayı Durdur'a** tıklayın.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Paralel Görevler Penceresini ve Paralel Yığınlar penceresinin Görevler Görünümünü Kullanma
 Devam etmek için önceki yordamları tamamlamanız önerilir.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>İlk kesme noktası isabet olana kadar uygulamayı yeniden başlatmak için

1. Hata Ayıklama **menüsünde Hata** Ayıklamayı **Başlat'a** tıklayın ve ilk kesme noktası'nın isabetini bekleyin.

2. Hata Ayıklama **menüsünde,** Hata Ayıkla'nın **üzerine Windows** ve ardından İş Parçacıkları'ya **tıklayın.** İş Parçacıkları **penceresini** iş parçacıklarının en Visual Studio.

3. Hata Ayıklama **menüsünde Hata** Ayıkla'nın **üzerine Windows** **Yığını'Windows'a tıklayın.** Çağrı **Yığını penceresinin** alt kısmında Visual Studio.

4. İş Parçacıkları penceresinde bir iş **parçacığına çift** tıklar ve bunu geçerli hale sürükleyin. Geçerli iş parçacıkları sarı oka sahip. Geçerli iş parçacığını değiştirdiğinde, diğer pencereler güncelleştirilir. Ardından, görevleri inceleyeziz.

5. Hata **Ayıkla menüsünde,** öğesinin üzerine **Windows** görevler'e **tıklayın.** Aşağıdaki çizimde Görevler **penceresi gösterilir.**

     ![Görevler penceresinde çalışan dört görev](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Çalışan her Görev için, aynı adlandırılmış özellik, onu çalıştıran iş parçacığının kimliği ve adı, konumu (çağrı yığınının tamamının bulunduğu bir araç ipucu görüntüleyen araç ipucu üzerine gelin) tarafından döndürülen kimliğini okuyabilirsiniz. Ayrıca, **Görev sütunu** altında, göreve geçirilen yöntemi de görebilir; başka bir deyişle, başlangıç noktası.

     Herhangi bir sütunu sıralayebilirsiniz. Sıralama sütununu ve yönünü gösteren sıralama işaretine dikkatin. Sütunları sola veya sağa sürükleyerek de yeniden sıralayabilirsiniz.

     Sarı ok, geçerli görevi gösterir. Bir göreve çift tıklayarak veya kısayol menüsünü kullanarak görevleri değiştirebilirsiniz. Görevleri değiştirdiğinde, temel iş parçacığı geçerli hale gelir ve diğer pencereler güncelleştirilir.

     Bir görevden diğerine el ile geçiş yapmak için sarı ok hareket eder, ancak beyaz ok yine de hata ayıklayıcının bozmasına neden olan görevi gösterir.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Yürütmeyi ikinci kesme noktası kadar sürdürme

1. İkinci kesme noktası isabet edene kadar yürütmeyi devam ettirin, Hata **Ayıkla menüsünde** Devam'a **tıklayın.**

     Daha önce **Durum sütununda** tüm görevler Etkin olarak gösterilese de, şimdi iki görev Engellendi. Görevler birçok farklı nedenle [engellenmiş olabilir.](/dotnet/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism) Durum **sütununda,** neden engellenmiş olduğunu öğrenmek için bekleyen görevin üzerine gelin. Örneğin, aşağıdaki çizimde, görev 3 görev 4'te bekliyor.

     ![Görevler penceresinde iki bekleyen görev](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     Görev 4, sırasıyla, görev 2'ye atanmış iş parçacığının sahip olduğu bir izleyiciyi bekliyor. (Üst bilgi satırına sağ tıklayın ve Sütunlar'ı **seçin**  >  **Görev 2** için iş parçacığı atama değerini görüntülemek için İş Parçacığı Ataması).

     ![Görevler penceresinde bekleyen görev ve araç ipucu](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     Görevler penceresinin ilk sütunundaki bayrağına tıklayarak bir görevi **bayrakla görüntüebilirsiniz.**

     Aynı hata ayıklama oturumunda farklı kesme noktaları arasındaki görevleri izlemek veya çağrı yığınları Paralel Yığınlar penceresinde gösterilen görevleri filtrelemek için flagging **kullanabilirsiniz.**

     Paralel Yığınlar **penceresini daha önce** kullandık, uygulama iş parçacıklarını görüntülemıştık. Paralel **Yığınlar penceresini yeniden** görüntüleme, ancak bu kez uygulama görevlerini görüntüleme. Sol üstteki kutuda **Görevler'i** seçerek bunu gerçekleştirin. Aşağıdaki çizimde Görevler Görünümü gösterilmiştir.

     ![Paralel Yığınlar penceresinde görevler görünümü](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     Şu anda görevleri yürütmeyen iş parçacıkları, Paralel Yığınlar penceresinin **Görevler Görünümü'ne gösterilmez.** Ayrıca, görevleri yürüten iş parçacıkları için, görevlerle ilgili olan yığın çerçevelerinden bazıları yığının üst ve alt kısmından filtrelenmiş olur.

     Görevler **penceresini** yeniden görüntüleme. Sütun için kısayol menüsünü görmek için herhangi bir sütun başlığına sağ tıklayın.

     Sütun eklemek veya kaldırmak için kısayol menüsünü kullanabilirsiniz. Örneğin, AppDomain sütunu seçilmez; bu nedenle listede görüntülenmez. **Üst'e tıklayın.** Üst **sütun,** dört görevden herhangi biri için değer olmadan görünür.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Yürütmeyi üçüncü kesme noktası kadar sürdürme

1. Yürütmeyi üçüncü kesme noktası isabet edene kadar devam etmek için Hata **Ayıklama menüsünde** Devam'a **tıklayın.**

     5. görev olan yeni bir görev çalışıyor ve görev 4 artık bekliyor. Durum penceresinde bekleme görevinin üzerine gelerek bunun **neden** olduğunu görebilirsiniz. Üst **sütununda,** 4. görevin 5. görevin üst öğesi olduğunu fark vardır.

     Üst-alt ilişkisini daha iyi görselleştirmek için sütun üst bilgisi satırına sağ tıklayın ve ardından Üst Alt **Görünüm'e tıklayın.** Aşağıdaki çizimi görüyor gerekir.

     ![Görevler&#45;üst öğe alt görünümü](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     4. görev ve 5. görevin aynı iş parçacığında (gizli ise İş Parçacığı **Ataması** sütununu göster) çalıştırıldıklara dikkat olun. Bu bilgiler İş Parçacıkları penceresinde **görüntülenmez;** Burada görmek, Görevler penceresinin bir diğer **avantajıdır.** Bunu onaylamak için Paralel **Yığınlar penceresini** açın. Görevler'i görüntüleyeniden **emin olun.** Görevler penceresinde bu görevlere çift tıklayarak 4. ve 5. **görevleri** bulun. Bunu yapmak için Paralel Yığınlar **penceresindeki mavi vurgu** güncelleştirilir. Paralel Yığınlar penceresinde araç ipucu taramasını kullanarak da 4. ve 5. **görevleri görebilirsiniz.**

     ![Görev görünümü Yığınlar penceresindeki bağlantı](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     Paralel **Yığınlar penceresinde** S.P'ye sağ tıklayın ve ardından İş Parçacığına **Git'e tıklayın.** Pencere İş Parçacıkları Görünümüne geçiş gösterir ve karşılık gelen çerçeve görünümdedir. Her iki görevi de aynı iş parçacığında görüyorsunuz.

     ![İş parçacıkları görünümünde vurgulanan iş parçacığı](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Bu, İş Parçacıkları penceresine kıyasla **Paralel Yığınlar** penceresindeki Görevler Görünümü'nin bir diğer **avantajıdır.**

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Yürütmeyi dördüncü kesme noktası kadar sürdürme

1. Yürütmeyi üçüncü kesme noktası isabet edene kadar devam etmek için Hata **Ayıklama menüsünde** Devam'a **tıklayın.** Id sütunu **üst bilgisinde** id sütununa göre sıralamak için tıklayın. Aşağıdaki çizimi görüyor gerekir.

     ![Paralel Yığınlar penceresinde dört görev durumları](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     5. görev tamamlandığından artık görüntülenmez. Bilgisayarınızda böyle bir durum yoksa ve kilitlenme gösterilmezse, F11 tuşuna basarak bir **kez adım atabilirsiniz.**

     Görev 3 ve görev 4 artık birbirini bekliyor ve engellendi. Ayrıca 2. görevin en küçükleri olan ve şimdi zamanlanmış olan 5 yeni görev de vardır. Zamanlanmış görevler, kodda başlatmış ancak henüz çalıştırmış olan görevlerdir. Bu nedenle Konum **ve** İş **Parçacığı Ataması** sütunları boştur.

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
