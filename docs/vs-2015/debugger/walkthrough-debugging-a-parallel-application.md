---
title: 'İzlenecek yol: paralel uygulamada hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad496bb55bae8d9e08035408059e454430ab4e39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705543"
---
# <a name="walkthrough-debugging-a-parallel-application"></a>İzlenecek Yol: Paralel Uygulamada Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, paralel bir uygulamada hata ayıklamak için paralel **Görevler** ve **Paralel Yığınlar** pencerelerinin nasıl kullanılacağını gösterir. Bu pencereler, [görev paralel kitaplığı (TPL)](https://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23) veya [Eşzamanlılık çalışma zamanı](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)kullanan kodun çalışma zamanı davranışını anlamanıza ve doğrulamanıza yardımcı olur. Bu izlenecek yol, yerleşik kesme noktaları içeren örnek kod sağlar. Kod kesildikten sonra, izlenecek yol **paralel görevlerin** ve **Paralel Yığınlar** pencerelerinin nasıl kullanılacağını gösterir.  
  
 Bu izlenecek yol, şu görevleri öğretir:  
  
- Tüm iş parçacıklarının çağrı yığınlarını tek bir görünümde görüntüleme.  
  
- `System.Threading.Tasks.Task`Uygulamanızda oluşturulan örneklerin listesini görüntüleme.  
  
- İş parçacıkları yerine görevlerin gerçek çağrı yığınlarını görüntüleme.  
  
- **Paralel görevler** ve **Paralel Yığınlar** pencerelerinin koduna gitme.  
  
- Windows Cope 'un gruplandırma, yakınlaştırma ve diğer ilgili özelliklerle nasıl ölçeklendirilmesi.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Bu izlenecek yol **yalnızca kendi kodum** etkinleştirildiğini varsayar. **Araçlar** menüsünde **Seçenekler**' e tıklayın, **hata ayıklama** düğümünü genişletin, **genel**' i seçin ve ardından yalnızca kendi kodum etkinleştir ' i seçin **(yalnızca yönetilen)**. Bu özelliği görmüyorsanız, bu yönergeyi kullanmaya devam edebilirsiniz, ancak sonuçlarınız çizimlerden farklı olabilir.  
  
## <a name="c-sample"></a>C# örneği  
 C# örneğini kullanıyorsanız bu izlenecek yol, dış kodun gizli olduğunu de varsayar. Dış kodun görüntülenip görüntülenmediğini değiştirmek için **çağrı yığını** penceresinin **ad** tablo başlığına sağ tıklayın ve ardından **dış kodu göster**' i seçin veya temizleyin. Bu özelliği görmüyorsanız, bu yönergeyi kullanmaya devam edebilirsiniz, ancak sonuçlarınız çizimlerden farklı olabilir.  
  
## <a name="c-sample"></a>C++ örneği  
 C++ örneğini kullanırsanız, bu konudaki dış koda yönelik başvuruları yoksayabilirsiniz. Dış kod yalnızca C# örneği için geçerlidir.  
  
## <a name="illustrations"></a>Çizimler  
 Bu konudaki çizimler, C# örneğini çalıştıran dört çekirdekli bir bilgisayara kaydedilir. Bu yönergeyi tamamlamak için diğer konfigürasyonları da kullanabilirsiniz, ancak çizimler bilgisayarınızda görüntülendiklerden farklı olabilir.  
  
## <a name="creating-the-sample-project"></a>Örnek proje oluşturma  
 Bu izlenecek yolda örnek kod hiçbir şey olmayan bir uygulama içindir. Amaç, bir paralel uygulamada hata ayıklamak için araç pencerelerinin nasıl kullanılacağını öğrenmektir.  
  
#### <a name="to-create-the-sample-project"></a>Örnek proje oluşturmak için  
  
1. Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.  
  
2. **Yüklü şablonlar** bölmesinde, Visual C#, Visual Basic veya Visual C++ seçeneklerinden birini belirleyin. Yönetilen diller için [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] çerçeve kutusunda görüntülendiğinden emin olun.  
  
3. **Konsol uygulaması** ' nı seçin ve ardından **Tamam**' a tıklayın. Varsayılan olan hata ayıklama yapılandırmasında kalır.  
  
4. Projedeki. cpp,. cs veya. vb kod dosyasını açın. Boş bir kod dosyası oluşturmak için içeriğini silin.  
  
5. Seçtiğiniz dil için aşağıdaki kodu boş kod dosyasına yapıştırın.  
  
   [!code-cpp[Debugger#1](../snippets/cpp/VS_Snippets_Misc/debugger/cpp/beta2_native.cpp#1)]
   [!code-csharp[Debugger#1](../snippets/csharp/VS_Snippets_Misc/debugger/cs/s.cs#1)]
   [!code-vb[Debugger#1](../snippets/visualbasic/VS_Snippets_Misc/debugger/vb/module1.vb#1)]  
  
6. **Dosya** menüsünde **Tümünü Kaydet**’e tıklayın.  
  
7. **Derle** menüsünde **çözümü yeniden derle**' ye tıklayın.  
  
    İçin dört çağrı olduğunu unutmayın `Debugger.Break` ( `DebugBreak` C++ örneğinde), bu nedenle kesme noktaları eklemeniz gerekmez; uygulamayı çalıştırmak, hata ayıklayıcıda en fazla dört kez kesintiye neden olur.  
  
## <a name="using-the-parallel-stacks-window-threads-view"></a>Paralel Yığınlar penceresini kullanma: Iş parçacıkları görünümü  
 **Hata ayıkla** menüsünde **Hata Ayıklamayı Başlat**’a tıklayın. İlk kesme noktasının isabet gelmesini bekleyin.  
  
#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Tek bir iş parçacığının çağrı yığınını görüntülemek için  
  
1. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve ardından **iş parçacıkları**' na tıklayın. Visual Studio 'nun alt kısmındaki **Iş parçacıkları** penceresini yerleştir.  
  
2. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve ardından **çağrı yığını**' na tıklayın. **Çağrı yığını** penceresini alt Visual Studio 'ya yerleştirin.  
  
3. Geçerli hale getirmek için **Iş parçacıkları** penceresinde bir iş parçacığına çift tıklayın. Geçerli iş parçacıklarında sarı bir ok var. Geçerli iş parçacığını değiştirdiğinizde çağrı yığını **çağrı yığını** penceresinde görüntülenir.  
  
#### <a name="to-examine-the-parallel-stacks-window"></a>Paralel Yığınlar penceresini incelemek için  
  
1. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve **Paralel Yığınlar**' ı tıklatın. **Iş parçacıklarının** sol üst köşedeki kutuda seçili olduğundan emin olun.  
  
     **Paralel Yığınlar** penceresini kullanarak, aynı anda birden fazla çağrı yığınını tek bir görünümde görüntüleyebilirsiniz. Aşağıdaki çizimde, **çağrı yığını** penceresinin üstündeki **Paralel Yığınlar** penceresi gösterilmektedir.  
  
     ![Paralel Yığınlar penceresinde iş parçacıkları görünümü](../debugger/media/pdb-walkthrough-1.png "PDB_Walkthrough_1")  
  
     Ana iş parçacığının çağrı yığını bir kutu içinde görünür ve diğer dört iş parçacığı için çağrı yığınları başka bir kutu içinde gruplandırılır. Yığın çerçeveleri aynı yöntem bağlamlarını paylaştığı için dört iş parçacığı birlikte gruplandırılır; diğer bir deyişle, bu yöntemler aynı yöntemlerde: `A` , `B` ve `C` . Aynı kutuyu paylaşan iş parçacıklarının iş parçacığı kimliklerini ve adlarını görüntülemek için üstbilginin üzerine gelin (**4 Iş parçacığı**). Aşağıdaki çizimde gösterildiği gibi geçerli iş parçacığı kalın olarak görüntülenir.  
  
     ![İş parçacığı kimliklerini ve adlarını gösteren araç ipucu](../debugger/media/pdb-walkthrough-1a.png "PDB_Walkthrough_1A")  
  
     Sarı ok, geçerli iş parçacığının etkin yığın çerçevesini gösterir. Daha fazla bilgi edinmek için üzerine gelin  
  
     ![Etkin yığın çerçevesindeki araç ipucu](../debugger/media/pdb-walkthrough-1b.png "PDB_Walkthrough_1B")  
  
     **Çağrı yığını** penceresine sağ tıklayarak yığın çerçeveleri (**modül adları**, **parametre türleri**, **parametre adları**, **parametre değerleri**, **satır numaraları** ve **bayt uzaklıkları**) için ne kadar ayrıntı gösterileceğini belirleyebilirsiniz.  
  
     Bir kutu etrafında mavi bir vurgu, geçerli iş parçacığının o kutunun bir parçası olduğunu gösterir. Geçerli iş parçacığı araç ipucunda kalın yığın çerçevesiyle da belirtilir. Iş parçacıkları penceresinde ana iş parçacığına çift tıklarsanız, **Paralel Yığınlar** penceresindeki mavi vurgunun uygun şekilde taşındığını gözlemleyebilirsiniz.  
  
     ![Paralel Yığınlar penceresinde vurgulanan ana iş parçacığı](../debugger/media/pdb-walkthrough-1c.png "PDB_Walkthrough_1C")  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>İkinci kesme noktasına kadar yürütmeyi sürdürmesini sağlamak için  
  
1. İkinci kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın. Aşağıdaki çizimde, ikinci kesme noktasında iş parçacığı ağacı gösterilmektedir.  
  
     ![Birçok dalı gösteren Paralel Yığınlar penceresi](../debugger/media/pdb-walkthrough-2.png "PDB_Walkthrough_2")  
  
     İlk kesme noktasında, hepsi S. A ile s. B-S. C yöntemlerine giden dört iş parçacığı. Bu bilgiler, **Paralel Yığınlar** penceresinde görünmeye devam eder, ancak dört iş parçacığının ilerlemedi daha fazla olması gerekir. Bunlardan biri, S. D ve sonra G.D. . F, S. G ve S.H. ile devam eden başka bir Diğer iki kişi de S. I ve S. J ile devam etti ve bunlardan biri, diğer kullanıcı harici kod ile devam etti.  
  
     İş parçacıklarının iş parçacığı kimliklerini görmek için, örneğin **1 Iş parçacığı** veya **2 iş**parçacığı üzerinde, Box üstbilgisinin üzerine gelin. İş parçacığı kimliklerini ve diğer çerçeve ayrıntılarını görmek için yığın çerçevelerinin üzerine gelin. Mavi vurgu geçerli iş parçacığını gösterir ve sarı ok geçerli iş parçacığının etkin yığın çerçevesini gösterir.  
  
     Kumaş iş parçacıkları simgesi (mavi ve kırmızı waalı çizgiler), geçerli olmayan iş parçacıklarının etkin yığın çerçevelerini gösterir. **Çağrı yığını** penceresinde, kareleri değiştirmek için S. B öğesine çift tıklayın. **Paralel Yığınlar** penceresi, bir yeşil eğri ok simgesi kullanarak geçerli iş parçacığının geçerli yığın çerçevesini gösterir.  
  
     **Iş parçacıkları** penceresinde iş parçacıkları arasında geçiş yapın ve **Paralel Yığınlar** penceresindeki görünümün güncelleştirildiğini gözlemleyin.  
  
     **Paralel Yığınlar** penceresindeki kısayol menüsünü kullanarak başka bir iş parçacığına ya da başka bir iş parçacığının başka bir çerçevesine geçiş yapabilirsiniz. Örneğin, S. J öğesine sağ tıklayın, **çerçeveye geç**' in üzerine gelin ve ardından bir komuta tıklayın.  
  
     ![Yürütmenin paralel yığınları yolu](../debugger/media/pdb-walkthrough-2b.png "PDB_Walkthrough_2B")  
  
     S. C öğesine sağ tıklayın ve **çerçeveye geçiş**yapmak için üzerine gelin. Komutlardan biri, geçerli iş parçacığının yığın çerçevesini gösteren bir onay işaretine sahiptir. Aynı iş parçacığının bu çerçevesine geçebilirsiniz (yalnızca yeşil ok değişir) veya diğer iş parçacığına geçiş yapabilirsiniz (mavi vurgu de değişir). Aşağıdaki çizimde alt menü gösterilmektedir.  
  
     ![J geçerli olduğunda C üzerinde 2 seçenek içeren yığınlar menüsü](../debugger/media/pdb-walkthrough-3.png "PDB_Walkthrough_3")  
  
     Bir yöntem bağlamı yalnızca bir yığın çerçevesiyle ilişkilendirildiğinde, Box üst bilgisi **1 Iş parçacığı** görüntüler ve çift tıklayarak buna geçiş yapabilirsiniz. Kendisiyle ilişkilendirilmiş 1 ' den fazla çerçeve içeren bir yöntem bağlamına çift tıklarsanız, menü otomatik olarak açılır. Yöntem bağlamlarının üzerine geldiğinizde, sağdaki siyah üçgeni görürsünüz. Bu üçgene tıkladığınızda kısayol menüsü de görüntülenir.  
  
     Çok sayıda iş parçacığına sahip büyük uygulamalar için, yalnızca bir iş parçacığı alt kümesine odaklanmak isteyebilirsiniz. **Paralel Yığınlar** penceresi, yalnızca bayraklı iş parçacıkları için çağrı yığınlarını görüntüleyebilir. Araç çubuğunda, liste kutusunun yanındaki **yalnızca bayraklı** ' i göster düğmesine tıklayın.  
  
     ![Boş Paralel Yığınlar penceresi ve araç ipucu](../debugger/media/pdb-walkthrough-3a.png "PDB_Walkthrough_3A")  
  
     Sonra, **Iş parçacıkları** penceresinde, çağrı yığınlarının **Paralel Yığınlar** penceresinde nasıl göründüğünü görmek için iş parçacıklarını tek tek bayrakla işaretle. İş parçacıklarını işaretlemek için, bir iş parçacığının kısayol menüsünü veya ilk hücresini kullanın. Tüm iş parçacıklarını göstermek için **yalnızca bayraklı** araç çubuğunu göster düğmesine tıklayın.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Yürütmeyi üçüncü kesme noktasına kadar sürdürmeyi sağlamak için  
  
1. Üçüncü kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın.  
  
    Birden çok iş parçacığı aynı yöntemde olduğunda, ancak yöntem çağrı yığınının başlangıcında olmadığında, yöntem farklı kutular halinde görünür. Geçerli kesme noktasına bir örnek, içinde üç iş parçacığı bulunan ve üç kutuda görünen S. L olur. S.L. çift tıklayın  
  
    ![Paralel Yığınlar penceresindeki yürütme yolu](../debugger/media/pdb-walkthrough-3b.png "PDB_Walkthrough_3B")  
  
    Burada ne göründüğünü görebilmeniz için S. L ' nin diğer iki kutuda kalın olduğuna dikkat edin. Hangi çerçevelerin S. L ' ye ve hangi çerçevelere çağrı olduğunu görmek isterseniz, araç çubuğundaki **Yöntem görünümünü aç** düğmesine tıklayın. Aşağıdaki çizimde, **Paralel Yığınlar** penceresinin Yöntem görünümü gösterilmektedir.  
  
    ![Paralel Yığınlar penceresinde Yöntem görünümü](../debugger/media/pdw-walkthrough-4.png "PDW_Walkthrough_4")  
  
    Diyagramın seçili yöntemi nasıl özetettiğini ve görünümün ortasında kendi kutusuna konumlandırdığını unutmayın. Kasalar ve arayanlar üst ve alt üzerinde görünür. Bu moddan çıkmak için **Yöntem görünümünü değiştirme** düğmesine tekrar tıklayın.  
  
    **Paralel Yığınlar** penceresinin kısayol menüsünde aşağıdaki diğer öğeler de bulunur.  
  
   - **Onaltılık ekran** , ondalık ve onaltılık arasındaki araç ipuçlarında bulunan sayılara geçiş yapar.  
  
   - **Sembol yükleme bilgileri** ve **sembol ayarları** ilgili iletişim kutularını açar.  
  
   - **Kaynak kodu ' na gidin** ve **ayrıştırılmış derleme ' ya giderek** seçili yönteme gidin.  
  
   - **Dış kod göster** , Kullanıcı kodunda olmasalar bile tüm kareleri görüntüler. Diyagramın ek çerçevelere uyum sağlayacak şekilde genişletmelerini görmek için bunu deneyin (bunlar için semboller olmadığından soluk olabilir).  
  
     Büyük diyagramlarınız olduğunda ve sonraki kesme noktasına adımlarınızda, görünümün geçerli iş parçacığının etkin yığın çerçevesine otomatik olarak kaymasını isteyebilirsiniz; diğer bir deyişle, önce kesme noktasına isabet eden iş parçacığı. **Paralel Yığınlar** penceresinde, araç çubuğundaki **geçerli yığın çerçevesine Otomatik Kaydır** düğmesinin açık olduğundan emin olun.  
  
     ![Paralel Yığınlar penceresinde oto kaydırma](../debugger/media/pdb-walkthrough-4a.png "PDB_Walkthrough_4A")  
  
2. Devam etmeden önce, **Paralel Yığınlar** penceresinde, sola ve tamamen tüm şekilde kaydırma yapın.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Yürütmenin dördüncü kesme noktasına kadar sürdürülmesi için  
  
1. Dördüncü kesme noktasına ulaşılana kadar yürütmeyi sürdürmek için, **hata ayıklama** menüsünde **devam**' a tıklayın.  
  
     Görünümün nasıl yerleştiğine dikkat edin. İş **parçacıkları** penceresinde iş parçacıklarını değiştirin veya çağrı yığını penceresinde yığın çerçevelerini değiştirin ve görünümün her zaman doğru çerçeveye nasıl **kaydırılacağını** fark edin. **Geçerli araç çerçevesi seçeneğine otomatik kaydırmayı** devre dışı bırakın ve farkı görüntüleyin.  
  
     **Kuşbakışı görünümü** **Paralel Yığınlar** penceresinde büyük diyagramlarla de yardımcı olur. Aşağıdaki çizimde gösterildiği gibi pencerenin sağ alt köşesindeki kaydırma çubukları arasındaki düğmeye tıklayarak **kuşbakışı görünümünü** görebilirsiniz.  
  
     ![&#45;, Paralel Yığınlar penceresinde kuş bakışı görünümü](../debugger/media/pdb-walkthrough-5.png "PDB_Walkthrough_5")  
  
     Dikdörtgeni, diyagram etrafında hızlıca kaydırmak için taşıyabilirsiniz.  
  
     Diyagramı herhangi bir yöne taşımanın bir başka yolu da diyagramın boş bir alanına tıklamanız ve istediğiniz yere sürüklemektir.  
  
     Diyagramı yakınlaştırmak ve uzaklaştırmak için fare tekerleğini taşırken CTRL tuşuna basın ve basılı tutun. Alternatif olarak, araç çubuğundaki Yakınlaştır düğmesine tıklayın ve ardından Yakınlaştırma aracını kullanın.  
  
     ![Paralel Yığınlar penceresinde yakınlaştırılmış yığınlar](../debugger/media/pdb-walkthrough-5a.png "PDB_Walkthrough_5A")  
  
     Ayrıca, **Araçlar** menüsüne tıklayıp **Seçenekler**' e tıklayarak ve ardından **hata ayıklama** düğümü altındaki seçeneği seçerek veya temizleyerek yığınları aşağıdan yukarıya doğru bir şekilde görüntüleyebilirsiniz.  
  
2. Devam etmeden önce, **hata** ayıklama menüsünde, yürütmeyi sonlandırmak Için **hata ayıklamayı Durdur** ' a tıklayın.  
  
## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Paralel Işler penceresini ve Paralel Yığınlar penceresinin görevler görünümünü kullanma  
 Devam etmeden önce önceki yordamları tamamlamanızı öneririz.  
  
#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>İlk kesme noktasına ulaşılana kadar uygulamayı yeniden başlatmak için  
  
1. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' a tıklayın ve ilk kesme noktasının isabet gelmesini bekleyin.  
  
2. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve ardından **iş parçacıkları**' na tıklayın. Visual Studio 'nun alt kısmındaki **Iş parçacıkları** penceresini yerleştir.  
  
3. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve **çağrı yığını**' na tıklayın. **Çağrı yığını** penceresini alt Visual Studio 'ya yerleştirin.  
  
4. Geçerli hale gelmesini sağlamak için **Iş parçacıkları** penceresinde bir iş parçacığına çift tıklayın. Geçerli iş parçacıklarında sarı ok vardır. Geçerli iş parçacığını değiştirdiğinizde diğer pencereler güncelleştirilir. Daha sonra, görevleri inceleyeceğiz.  
  
5. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve **paralel görevler**' e tıklayın. Aşağıdaki çizimde **paralel görevler** penceresi gösterilmektedir.  
  
     ![Paralel Görevler penceresinde dört çalışan görev](../debugger/media/pdw-walkthrough-6.png "PDW_Walkthrough_6")  
  
     Çalışan her görev için, aynı adlı özellik tarafından döndürülen KIMLIĞINI okuyabilir, onu çalıştıran iş parçacığının KIMLIĞINI ve adını, konumunu (bunun üzerinde tüm çağrı yığınına sahip bir araç ipucu görüntüler) görebilirsiniz. Ayrıca, **görev** sütununun altında göreve geçirilen yöntemi görebilirsiniz; diğer bir deyişle, başlangıç noktası.  
  
     Herhangi bir sütunu sıralayabilirsiniz. Sıralamayı ve yönü gösteren sıralama glifine dikkat edin. Sütunları sola veya sağa sürükleyerek da sıralayabilirsiniz.  
  
     Sarı ok geçerli görevi gösterir. Bir görevi çift tıklayarak veya kısayol menüsünü kullanarak görev geçirebilirsiniz. Görevleri değiştirdiğinizde, temel alınan iş parçacığı geçerli olur ve diğer pencereler güncelleştirilir.  
  
     Bir görevden diğerine el ile geçiş yaptığınızda sarı ok geçer, ancak beyaz ok, hata ayıklayıcının kesintiye neden olan görevi gösterir.  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>İkinci kesme noktasına kadar yürütmeyi sürdürmesini sağlamak için  
  
1. İkinci kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın.  
  
     Daha önce, **durum** sütunu tüm görevleri çalışıyor olarak gösterdi, ancak bundan sonra görevlerden ikisi bekliyor. Görevler birçok farklı nedenden dolayı engellenebilir. **Durum** sütununda, neden engellendiğini öğrenmek için bekleyen bir görevin üzerine gelin. Örneğin, aşağıdaki çizimde, 1. görev 4 ' te bekliyor.  
  
     ![Paralel Görevler penceresinde iki bekleyen görev](../debugger/media/pdb-walkthrough-7.png "PDB_Walkthrough_7")  
  
     Görev 4 ' te, görev 2 ' ye atanan iş parçacığına ait bir izleyiciyi bekliyor.  
  
     ![Görevler penceresinde bekleyen görev ve araç ipucu](../debugger/media/pdb-walkthrough-7a.png "PDB_Walkthrough_7A")  
  
     **Paralel görevler** penceresinin ilk sütunundaki bayrağa tıklayarak bir görevi işaretleyebilirsiniz.  
  
     Aynı hata ayıklama oturumunda farklı kesme noktaları arasındaki görevleri izlemek veya **Paralel Yığınlar** penceresinde çağrı yığınları gösterilen görevleri filtrelemek için bayrak uygulayabilirsiniz.  
  
     **Paralel Yığınlar** penceresini daha önce kullandığınızda uygulama iş parçacıklarını görüntülerdi. **Paralel Yığınlar** penceresini yeniden görüntüleyin, ancak bu kez uygulama görevlerini görüntüleyin. Sol üstteki kutudan **Görevler** ' i seçerek bunu yapın. Aşağıdaki çizimde görevler görünümü gösterilmektedir.  
  
     ![Paralel Yığınlar penceresinde iş parçacıkları görünümü](../debugger/media/pdb-walkthrough-8.png "PDB_Walkthrough_8")  
  
     Şu anda yürütülmekte olan iş parçacıkları, **Paralel Yığınlar** penceresinin görevler görünümünde gösterilmez. Ayrıca, görevleri çalıştıran iş parçacıkları için, görevlerle ilgili olmayan yığın çerçevelerinden bazıları yığının üst ve alt kısmından filtrelenmiştir.  
  
     **Paralel görevler** penceresini yeniden görüntüleyin. Sütunun kısayol menüsünü görmek için herhangi bir sütun başlığına sağ tıklayın.  
  
     ![Paralel Görevler penceresinde kısayol Görünüm menüsü](../debugger/media/pdb-walkthrough-8a.png "PDB_Walkthrough_8A")  
  
     Sütun eklemek veya kaldırmak için kısayol menüsünü kullanabilirsiniz. Örneğin, AppDomain sütunu seçili değildir; Bu nedenle, listede gösterilmez. **Üst öğeye**tıklayın. **Üst** sütun dört görevlerden herhangi biri için değer olmadan görüntülenir.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Yürütmeyi üçüncü kesme noktasına kadar sürdürmeyi sağlamak için  
  
1. Üçüncü kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın.  
  
     Yeni bir görev, görev 5, artık çalışıyor ve görev 4 artık bekliyor. **Durum** penceresindeki bekleme görevinin üzerine gelip gelmediğini görebilirsiniz. **Üst** sütunda, görev 4 ' ün görev 5 ' in üst öğesi olduğunu fark edersiniz.  
  
     Üst-alt ilişkisini daha iyi görselleştirmek için **üst** sütun başlığına sağ tıklayın ve ardından **üst alt öğe görünümü**' ne tıklayın. Aşağıdaki çizimi görmeniz gerekir.  
  
     ![Paralel Görevler penceresinde üst&#45;alt öğe görünümü](../debugger/media/pdb-walkthrough-9.png "PDB_Walkthrough_9")  
  
     Görev 4 ve görev 5 ' in aynı iş parçacığında çalıştığını unutmayın. Bu bilgiler, **Iş parçacıkları** penceresinde gösterilmez; **paralel görevler** penceresinin başka bir avantajı burada görüyor. Bunu doğrulamak için, **Paralel Yığınlar** penceresini görüntüleyin. **Görevleri**görüntülemekte olduğunuzdan emin olun. **Paralel görevler** penceresinde bunlara çift tıklayarak 4 ve 5. görevleri bulun. Bunu yaptığınızda, **Paralel Yığınlar** penceresinde mavi vurgu güncellenir. **Paralel Yığınlar** penceresinde araç ipuçlarını tarayarak 4 ve 5. görevleri de bulabilirsiniz.  
  
     ![Paralel Yığınlar penceresinde görev görünümü](../debugger/media/pdb-walkthrough-9a.png "PDB_Walkthrough_9A")  
  
     **Paralel Yığınlar** penceresinde, S. P öğesine sağ tıklayın ve ardından **iş parçacığına git ' e**tıklayın. Pencere, Iş parçacıkları görünümüne geçer ve ilgili çerçeve görünümüdür. Aynı iş parçacığında her iki görevi de görebilirsiniz.  
  
     ![İş parçacıkları görünümünde vurgulanan iş parçacığı](../debugger/media/pdb-walkthrough-9b.png "PDB_Walkthrough_9B")  
  
     Bu, **Iş parçacıkları** penceresi Ile karşılaştırıldığında **Paralel Yığınlar** penceresindeki görevler görünümü ' ne ait başka bir avantajdır.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Yürütmenin dördüncü kesme noktasına kadar sürdürülmesi için  
  
1. Üçüncü kesme noktasına isabet edene kadar yürütmeyi sürdürmek için, **Hata Ayıkla** menüsünde **devam**' a tıklayın. Kimliğe göre sıralamak için **kimlik** sütun başlığına tıklayın. Aşağıdaki çizimi görmeniz gerekir.  
  
     ![Paralel Yığınlar penceresinde dört görev durumu](../debugger/media/pdb-walkthrough-10.png "PDB_Walkthrough_10")  
  
     5. görev tamamlandığı için artık görüntülenmiyor. Bu durum bilgisayarınızda değilse ve kilitlenme gösterilmezse, F11 tuşuna basarak bir kez adım adım.  
  
     Görev 3 ve görev 4 artık birbirini bekliyor ve kilitlenmişti. 2. görevin alt öğesi olan ve şimdi zamanlanmış 5 yeni görev da vardır. Zamanlanan görevler, kodda başlatılmış ancak henüz çalıştırılmayan görevlerdir. Bu nedenle, **konum** ve **iş parçacığı atama** sütunları boştur.  
  
     **Paralel Yığınlar** penceresini yeniden görüntüleyin. Her kutunun üst bilgisinde, iş parçacığı kimliklerini ve adlarını gösteren bir araç ipucu vardır. **Paralel Yığınlar** penceresinde görevler görünümü ' ne geçin. Aşağıdaki çizimde gösterildiği gibi, görev KIMLIĞI ve adını ve görevin durumunu görmek için bir üstbilginin üzerine gelin.  
  
     ![Paralel Yığınlar penceresindeki üstbilgi araç ipucu](../debugger/media/pdb-walkthrough-11.png "PDB_Walkthrough_11")  
  
     Görevleri sütuna göre gruplandırabilirsiniz. **Paralel görevler** penceresinde, **durum** sütun başlığına sağ tıklayın ve ardından **duruma göre Gruplandır**' a tıklayın. Aşağıdaki çizim **paralel görevler** penceresini duruma göre gruplanmış olarak gösterir.  
  
     ![Paralel Görevler penceresinde gruplanmış görevler](../debugger/media/pdb-walkthrough-12.png "PDB_Walkthrough_12")  
  
     Ayrıca, başka bir sütuna göre gruplandırabilirsiniz. Görevleri gruplandırarak, bir görev alt kümesine odaklanırsınız. Her daraltılabilir Grup, birlikte gruplanmış öğelerin sayısına sahiptir. Ayrıca, **daraltma** düğmesinin sağındaki **bayrak** düğmesine tıklayarak gruptaki tüm öğeleri hızlıca işaretleyebilirsiniz.  
  
     ![Paralel Yığınlar penceresinde gruplanmış yığınlar](../debugger/media/pdb-walkthrough-12a.png "PDB_Walkthrough_12A")  
  
     İncelemek için **paralel görevler** penceresinin son özelliği, bir göreve sağ tıkladığınızda görüntülenen kısayol menüsü olur.  
  
     ![Paralel Görevler penceresinde kısayol menüsü](../debugger/media/pdb-walkthrough-12b.png "PDB_Walkthrough_12B")  
  
     Kısayol menüsü, görevin durumuna bağlı olarak farklı komutları görüntüler. Bu komutlar **kopyalama**, **Tümünü seçme**, **onaltılık görüntü**, **görev değiştirme**, **atanan Iş parçacığını**dondurma, **tüm iş parçacıklarını dondurma, ancak bu**atama ve **bayrağı** **çözme**içerebilir.  
  
     Bir görevin veya görevlerin temel alınan iş parçacığını dondurabilir veya atanmış olanı hariç tüm iş parçacıklarını dondurabilirsiniz. Dondurulmuş bir iş parçacığı, bir mavi *duraklatma* simgesiyle **iş parçacıkları** penceresinde olduğu gibi **paralel görevler** penceresinde temsil edilir.  
  
## <a name="summary"></a>Özet  
 Bu izlenecek yol, **paralel görevler** ve **Paralel Yığınlar** hata ayıklayıcısı pencerelerini göstermiştir. Bu pencereleri, çok iş parçacıklı kod kullanan gerçek projeler üzerinde kullanın. C++, C# veya Visual Basic yazılmış paralel kodu inceleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çoklu Iş parçacıklı uygulamalarda hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Hata ayıklayıcı temelleri](../debugger/debugger-basics.md)   
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Paralel programlama](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Eşzamanlılık Çalışma Zamanı](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Paralel Yığınlar penceresini kullanma](../debugger/using-the-parallel-stacks-window.md)   
 [Görevleri Penceresini Kullanma](../debugger/using-the-tasks-window.md)
