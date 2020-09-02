---
title: 'İzlenecek yol: çok Iş parçacıklı uygulamada hata ayıklama | Microsoft Docs'
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
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ce391523a256bcb195deccf0c14868b5eae707
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683089"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>İzlenecek Yol: Çok İş Parçacıklı Uygulamada Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] çok iş parçacıklı uygulamalarda hata ayıklamayı kolaylaştırmak için geliştirilmiş bir **Iş parçacığı** penceresi ve diğer kullanıcı arabirimi geliştirmeleri sağlar. Bu izlenecek yol yalnızca birkaç dakika sürer, ancak bunu tamamlamak çok iş parçacıklı uygulamalarda hata ayıklamaya yönelik yeni arabirim özellikleri hakkında bilgi sağlar.  
  
 Bu yönergeyi başlamak için çok iş parçacıklı bir uygulama projesine ihtiyacınız vardır. Bu projeyi oluşturmak için burada listelenen adımları izleyin.  
  
#### <a name="to-create-the-walkthrough-project"></a>İzlenecek yol projesi oluşturmak için  
  
1. **Dosya** menüsünde, **Yeni** ' yi seçin ve ardından **Proje**' ye tıklayın.  
  
     **Yeni Proje** iletişim kutusu görünür.  
  
2. **Proje türü**kutusunda, tercih ettiğiniz dile tıklayın: **Visual Basic**, **Visual C#** veya **Visual C++**.  
  
3. **Şablonlar** kutusunda **konsol uygulaması** veya **clr konsol uygulaması**' nı seçin.  
  
4. **Ad** kutusuna MyThreadWalkthroughApp adını yazın.  
  
5. **Tamam**’a tıklayın.  
  
     Yeni bir konsol projesi görüntülenir. Proje oluşturulduğunda, bir kaynak dosya görüntülenir. Seçtiğiniz dile bağlı olarak, kaynak dosyaya Module1. vb, Program.cs veya MyThreadWalkthroughApp. cpp adı verilir  
  
6. Kaynak dosyada görüntülenen kodu silin ve bunu, [Iş parçacığı oluşturma ve Başlangıç zamanında veri geçirme](https://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d)konusunun "Iş parçacığı oluşturma" bölümünde görüntülenen örnek kodla değiştirin.  
  
7. **Dosya** menüsünde **Tümünü Kaydet**’e tıklayın.  
  
#### <a name="to-begin-the-walkthrough"></a>İzlenecek yolu kullanmaya başlamak için  
  
- Kaynak penceresinde aşağıdaki kodu arayın:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```csharp  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### <a name="to-start-debugging"></a>Hata ayıklamayı başlatmak için  
  
1. Deyime sağ tıklayın `Console.WriteLine` , **kesme** noktası ' nın üzerine gelin ve ardından **kesme noktası Ekle**' ye tıklayın.  
  
     Kaynak pencerenin sol tarafındaki cilt alanında kırmızı bir top görüntülenir. Bu, bir kesme noktasının artık bu konumda ayarlandığını gösterir.  
  
2. **Hata ayıkla** menüsünde **Hata Ayıklamayı Başlat**’a tıklayın.  
  
     Hata ayıklama başlar, konsol uygulamanız çalışmaya başlar ve sonra kesme noktasında durmaktadır.  
  
3. Konsol uygulama penceresi bu noktada odağa sahipse, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] odağı öğesine döndürmek için pencereye tıklayın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
4. Kaynak penceresinde, aşağıdaki kodu içeren satırı bulun:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```csharp  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
1. 
  
#### <a name="to-discover-the-thread-marker"></a>İş parçacığı işaretçisini bulma  
  
1. **Iş parçacıkları** penceresinde sağ tıklayın ve sonra **Iş parçacıklarını kaynakta göster**' e tıklayın.  
  
2. Pencerenin sol tarafındaki cilt paya bakın. Bu satırda, iki kumaş iş parçacığına benzer bir simge görürsünüz. Bir iş parçacığı kırmızı ve diğeri mavi. İş parçacığı işaretçisi, bu konumda bir iş parçacığının durdurulduğunu gösterir. Büyük olasılıkla, iş parçacığı bu konumda durdurulmuş.  
  
3. İşaretçiyi iş parçacığı işaretçisinin üzerine getirin. Görüntülenen bir veri Ipucu. Veri Ipucu, her durdurulan iş parçacığı için ad ve iş parçacığı KIMLIĞI numarası size bildirir. Bu durumda, adı muhtemelen olan yalnızca bir iş parçacığı vardır `<noname>` .  
  
4. İş parçacığı işaretine sağ tıklayın. Kısayol menüsündeki seçeneklere göz önünde edin.  
  
   Bu simge bir *iş parçacığı işaretleyicisi*:  
  
   ![İş parçacığı Işaretçisi](../debugger/media/threadmarker.gif "Threadişaretleyici")  
  
## <a name="flagging-and-unflagging-threads"></a>Iş parçacıklarının işaretlemesini ve Işaretini kaldırma  
 İçinde [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] , özel dikkat sağlamak istediğiniz iş parçacıklarını Bayrakla işaretleyebilirsiniz. İş parçacıkları için bayrak eklemek, önemli iş parçacıklarını izlemenin ve ilgilendiğiniz iş parçacıklarını yoksaymanın iyi bir yoludur.  
  
#### <a name="to-flag-threads"></a>İş parçacıklarını işaretlemek için  
  
1. **Görünüm** menüsünde, **araç çubukları**' nın üzerine gelin.  
  
     **Hata ayıklama konumu** araç çubuğunun seçili olduğundan emin olun.  
  
2. **Hata ayıklama konumu** araç çubuğuna gidin ve **iş parçacığı** listesine tıklayın.  
  
    > [!NOTE]
    > Bu araç çubuğunu üç belirgin listeye göre tanıyabilir: **işlem**, **Iş parçacığı**ve **yığın çerçevesi**.  
  
3. Listede kaç iş parçacığı göründüğünü unutmayın.  
  
4. Kaynak penceresine geri dönün ve **Iş parçacığı** işaretine tekrar sağ tıklayın.  
  
5. Kısayol menüsünde, **bayrak**' ın üzerine gelin ve ardından iş parçacığı adı ve kimlik numarası ' na tıklayın.  
  
6. **Hata ayıklama konumu** araç çubuğuna geri dönün ve **iş parçacığı** listesine tekrar tıklayın.  
  
     Artık listede yalnızca bayraklı iş parçacığı görüntülenir. **Iş parçacığı** listesinin hemen sağındaki bayrak düğmesi. Düğme üzerindeki bayrak simgesi daha önce soluk. Artık kesintisiz, parlak kırmızı.  
  
7. İşaretçiyi bayrak simgesinin üzerine getirin.  
  
     Açılır pencere görüntülenir. Bu açılır pencere, **Iş parçacığı** listesinin hangi modda olduğunu söyler: **yalnızca bayraklı iş parçacıklarını göster**.  
  
8. **Tüm Iş parçacıkları modunu göstermek** üzere geri dönmek için bayrak düğmesine tıklayın.  
  
9. **Iş parçacığı** listesine yeniden tıklayın ve artık tüm iş parçacıklarını yeniden görebildiğinizi doğrulayın.  
  
10. **Yalnızca bayraklı Iş parçacıklarını göstermek**üzere geri dönmek için bayrak düğmesine tıklayın.  
  
11. **Hata Ayıkla** menüsünde **Windows** ' un üzerine gelin ve ardından **iş parçacıkları**' na tıklayın.  
  
     **Iş parçacıkları** penceresi görüntülenir. Bir iş parçacığında kendisine bağlı belirgin bayrak simgesi vardır.  
  
12. Kaynak penceresinde iş parçacığı işaretine yeniden sağ tıklayın.  
  
     Artık kısayol menüsünde hangi seçeneklerin kullanılabilir olduğuna dikkat edin. **Bayrak**yerine **artık bayrak işaretini görürsünüz.** **Unflag**tıklamayın.  
  
13. İş parçacıklarının işaretini kaldırma hakkında sonraki yordama gidin.  
  
#### <a name="to-unflag-threads"></a>İş parçacıklarının bayrağını kaldırmak için  
  
1. **Iş parçacıkları** penceresinde, bayraklı iş parçacığına karşılık gelen satıra sağ tıklayın.  
  
     Kısayol menüsü görüntülenir. **Bayrak kaldırmak** ve **tümünün**işaretini kaldırmak seçeneklere sahiptir.  
  
2. İş parçacığının bayrağını kaldırmak için, **bayrağı kaldır**' ı tıklatın.  
  
3. Kırmızı bayrak simgesine tıklayın.  
  
4. **Hata ayıklama konumu** araç çubuğuna tekrar bakın. Bayrak düğmesi bir daha soluk. Bayrak eklenmiş olan iş parçacığının işaretini kaldırunlar. Bayraklı iş parçacığı olmadığından, araç çubuğu **Tüm Iş parçacıkları modunu göstermeye** geri gitti. **Iş parçacığı** listesine tıklayın ve tüm iş parçacıklarını görebildiğinizi doğrulayın.  
  
5. **Iş parçacıkları** penceresine geri dönün ve bilgi sütunlarını inceleyin.  
  
     Her sütunun üst kısmında, çoğu düğme sütunu tanımlayan başlıklar vardır. Ancak, sol taraftaki ilk sütunda başlık yoktur. Bunun yerine, bir bayrağın ana hattı olan bir simge vardır. İş parçacığı listesinin her satırında aynı ana hat olduğunu fark edeceksiniz. Ana hat, iş parçacığının işaretlenmediği anlamına gelir.  
  
6. İkinci ve üçüncü, listenin en altında bulunan iki iş parçacığı için bayrak anahatlara tıklayın.  
  
     Bayrak simgeleri boş anahatlar yerine düz kırmızı olur.  
  
7. Bayrak sütununun en üstündeki düğmeye tıklayın.  
  
     Düğmeye tıkladığınızda iş parçacığı listesinin sırası değişti. İş parçacığı listesi artık üstteki bayraklı iş parçacıkları ile sıralanır.  
  
8. Yine, bayrak sütununun en üstündeki düğmeye tıklayın.  
  
     Sıralama düzeni yeniden değiştirildi.  
  
## <a name="more-about-the-threads-window"></a>Iş parçacıkları penceresi hakkında daha fazla bilgi  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Iş parçacıkları penceresi hakkında daha fazla bilgi edinmek için  
  
1. **Iş parçacıkları** penceresinde, sol taraftaki üçüncü sütunu inceleyin. Bu sütunun en üstündeki düğme **kimlik**diyor.  
  
2. **Kimlik**' e tıklayın.  
  
     İş parçacığı listesi artık iş parçacığı KIMLIĞI numarasına göre sıralanır.  
  
3. Listedeki herhangi bir iş parçacığına sağ tıklayın. Kısayol menüsünde **onaltılık görüntü**' e tıklayın.  
  
     İş parçacığı KIMLIK numaralarının biçimi değiştirildi.  
  
4. Fare işaretçisini listedeki herhangi bir iş parçacığının üzerine getirin.  
  
     Bir kopan gecikmeden sonra bir veri Ipucu belirir. İş parçacığı için kısmi bir çağrı yığını gösterir.  
  
5. Sol taraftaki **Kategori**etiketli dördüncü sütuna bakın. İş parçacıkları kategoriler halinde sınıflandırılır.  
  
     Bir işlemde oluşturulan ilk iş parçacığı ana iş parçacığı olarak adlandırılır. İş parçacığı listesinde bulun.  
  
6. Ana iş parçacığına sağ tıklayıp **Iş parçacığına geç ' e**tıklayın.  
  
     Bir uyarı iletişim kutusu görüntülenir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Ana iş parçacığı için kaynak kodu göstermeyeceğini söyler.  
  
     **Tamam**’a tıklayın.  
  
7. **Çağrı yığını** penceresine ve **hata ayıklama konumu** araç çubuğuna bakın.  
  
     **Çağrı yığını** penceresinin içeriği değişti.  
  
## <a name="switching-the-active-thread"></a>Etkin Iş parçacığını değiştirme  
  
#### <a name="to-switch-threads"></a>İş parçacıklarını değiştirmek için  
  
1. **Iş parçacıkları** penceresinde, sol taraftaki ikinci sütunu inceleyin. Bu sütunun en üstündeki düğme metin veya simge içermiyor. Bu sütun **etkin Iş parçacığı** sütunudur.  
  
2. **Etkin Iş parçacığı** sütununa bakın ve bir iş parçacığının Sarı oka sahip olduğuna dikkat edin. Bu, *etkin iş parçacığı göstergesidir*.  
  
3. Etkin iş parçacığı göstergesinin bulunduğu iş parçacığı KIMLIĞI numarasını bir yere unutmayın. Etkin iş parçacığı göstergesini başka bir iş parçacığına taşıyacaksınız, ancak işiniz bittiğinde geri koymanız gerekir.  
  
4. Başka bir iş parçacığına sağ tıklayıp **Iş parçacığına geç ' e**tıklayın.  
  
5. Kaynak penceredeki **çağrı yığını** penceresine bakın. İçerik değiştirildi.  
  
6. **Hata ayıklama konumu** araç çubuğuna bakın. Etkin iş parçacığı aynı şekilde değiştirildi.  
  
7. **Hata ayıklama konumu** araç çubuğuna gidin. **Iş parçacığı** kutusuna tıklayın ve açılan listeden farklı bir iş parçacığı seçin.  
  
8. **Iş parçacıkları** penceresine bakın. Etkin iş parçacığı göstergesi değişti.  
  
9. Kaynak penceresinde bir iş parçacığı işaretine sağ tıklayın. Kısayol menüsünde, **Değiştir** ' in üzerine gelin ve bir iş parçacığı adı/kimlik numarası ' na tıklayın.  
  
     Etkin iş parçacığını değiştirmenin üç yolunu gördünüz: **Iş parçacıkları** penceresini, **hata ayıklama konumu** araç çubuğundaki **iş parçacığı** kutusunu ve kaynak penceredeki iş parçacığı göstergesini kullanarak.  
  
     İş parçacığı göstergesi ile yalnızca belirli bir konumda durdurulmuş olan iş parçacıklarıyla geçiş yapabilirsiniz. **Iş parçacıkları** penceresini ve **hata ayıklama konumu** araç çubuğunu kullanarak herhangi bir iş parçacığına geçiş yapabilirsiniz.  
  
## <a name="freezing-and-thawing-thread-execution"></a>İş parçacığı yürütmeyi donduruyor ve thakelebek  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>İş parçacıklarını dondurmak ve çözmek için  
  
1. **Iş parçacıkları** penceresinde herhangi bir iş parçacığına sağ tıklayın ve ardından **dondurma**' ya tıklayın.  
  
2. Etkin iş parçacığı sütununa bakın. Dikey çubukların çifti artık burada görünür. Bu iki mavi çubuk, iş parçacığının dondurulmuş olduğunu gösterir.  
  
3. **Askıda kalma** sütununa bakın. İş parçacığının askıya alma sayısı artık 1 ' dir.  
  
4. Dondurulmuş iş parçacığına sağ tıklayın ve ardından **çözme**' ye tıklayın.  
  
     Etkin iş parçacığı sütunu ve **askıya alma** sütunu değişikliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Nasıl yapılır: hata ayıklarken başka bir Iş parçacığına geçme](../debugger/how-to-switch-to-another-thread-while-debugging.md)
