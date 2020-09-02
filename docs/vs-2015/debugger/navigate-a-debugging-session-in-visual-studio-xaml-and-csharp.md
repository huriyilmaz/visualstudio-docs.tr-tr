---
title: Hata ayıklama oturumunda gezinme (XAML ve C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 1da33203-333f-4a05-b4e2-8d407c497233
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5b8d24f01f7882e8c760918119a03a1c489c727
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156744"
---
# <a name="navigate-a-debugging-session-in-visual-studio-xaml-and-c"></a>Visual Studio’da (Xaml ve C#) bir hata ayıklama oturumunda gezinme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hızlı başlangıç, Visual Studio hata ayıklama oturumlarına nasıl gidebileceğinizi ve bir oturumdaki program durumunun nasıl görüntüleneceğini ve değiştirileceğini gösterir.

 Bu hızlı başlangıç, Visual Studio ve Visual Studio hata ayıklama oturumunda gezinme hakkında daha fazla bilgi edinmek isteyen geliştiriciler için Visual Studio ile hata ayıklamaya yeni olan geliştiricilere yöneliktir. Hata ayıklamanın bir resmini kendi kendine öğretmez. Örnek koddaki yöntemler yalnızca, bu konuda açıklanan hata ayıklama yordamlarını göstermek için tasarlanmıştır. Yöntemler uygulama veya işlev tasarımının en iyi yöntemlerini kullanmaz. Aslında, yöntemlerin ve uygulamanın kendisinin her şeyi hiç bir şey yapmadığınızı hızlı bir şekilde keşfedeceksiniz.

 Bu hızlı başlangıç 'nin bölümleri mümkün olduğunca bağımsız olacak şekilde tasarlandı, bu sayede zaten bildiğiniz bilgileri içeren herhangi bir bölümü atlayabilirsiniz. Örnek uygulama oluşturmanız da gerekmez; Ancak, bunu öneriyoruz ve işlemi mümkün olduğunca kolay hale sunuyoruz.

 **Hata ayıklayıcı klavye kısayolları.** Visual Studio hata ayıklayıcısı gezintisi hem fare hem de klavye için iyileştirilmiştir. Bu konudaki adımların birçoğu, parantez içinde klavye hızlandırıcıyı veya kısayol tuşunu içerir. Örneğin, (klavye: F5) F5 tuşunu yazmanın başladığı veya hata ayıklayıcının yürütülmesine devam ettiğini gösterir.

## <a name="in-this-topic"></a>Bu konuda
 Şunları yapmayı öğrenebilirsiniz:

- [Örnek uygulamayı oluşturma](#BKMK_CreateTheApplication)

- [Ayarlama ve bir kesme noktasına çalıştırma, bir yönteme adımla ve program verilerini İnceleme](#BKMK_StepInto)

- [Yönteme adımla, aşırı ve dışı Yöntemler](#BKMK_StepIntoOverOut)

- [Koşullu kesme noktası ayarlayın, imlece çalıştırın ve bir değişkeni görselleştirin](#BKMK_ConditionCursorVisualize)

- [Düzenle ve devam et, özel durumdan kurtar](#BKMK_EditContinueRecoverExceptions)

## <a name="create-the-sample-app"></a><a name="BKMK_CreateTheApplication"></a> Örnek uygulamayı oluşturma
 Hata ayıklama kod ile ilgilidir, bu nedenle örnek uygulama yalnızca bir hata ayıklama oturumunun nasıl çalıştığını ve program durumunu inceleme ve değiştirme hakkında bilgi oluşturabileceğiniz bir kaynak dosyası oluşturmak için Windows Mağazası uygulamasının çerçevesini kullanır. Çağırabileceğiniz tüm kodlar ana sayfanın oluşturucusundan çağrılır; hiçbir denetim eklenmez ve hiçbir olay işlenmiyor.

 **Varsayılan bir C# Windows Mağazası uygulaması oluşturun.** Visual Studio'yu açın. Giriş sayfasında, **Yeni proje** bağlantısı ' nı seçin. Yeni proje iletişim kutusunda, **yüklü** listesinde **Visual C#** ' yi seçin ve ardından **Windows Mağazası**' nı seçin. Proje şablonları listesinde **uygulama**' yı seçin. Visual Studio yeni bir çözüm ve proje oluşturur ve MainPage. xaml Tasarımcısı ve XAML kod düzenleyicisini görüntüler.

 **MainPage.xaml.cs kaynak dosyasını açın.** XAML düzenleyicisinde herhangi bir yere sağ tıklayın ve **kodu görüntüle**' yi seçin. MainPage.xaml.cs arka plan kod dosyası görüntülenir. Dosyasında, oluşturucunun yalnızca bir yöntem `MainPage()` listelendiğini unutmayın.

 **MainPage oluşturucusunu örnek kodla değiştirin.** MainPage () yöntemini silin. Şu bağlantıyı izleyin: [hata ayıklayıcı gezinti örnek kodu (XAML ve C#)](../debugger/debugger-navigation-sample-code-xaml-and-csharp.md)ve ardından C# bölümünde listelenen kodu panoya kopyalayın. (Bu hızlı başlangıç sayfasına dönmek için tarayıcıda veya yardım görüntüleyicisinde **geri** 'yi seçin.) Visual Studio düzenleyicisinde, kodu `partial class MainPage` bloğa yapıştırın. Dosyayı kaydetmek için CTRL + s 'yi seçin.

 Artık bu konudaki örneklerle birlikte takip edebilirsiniz.

## <a name="set-and-run-to-a-breakpoint-step-into-a-method-and-examine-program-data"></a><a name="BKMK_StepInto"></a> Ayarlama ve bir kesme noktasına çalıştırma, bir yönteme adımla ve program verilerini İnceleme
 Hata ayıklama oturumu başlatabilmeniz için en yaygın **Yöntem hata ayıklama menüsünden** **hata ayıklamayı Başlat** ' ı (klavye: F5) seçkullanmaktır. Yürütme başlar ve kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, bir özel durum oluşur veya uygulama sonlanır.

 Hata ayıklayıcıda yürütme askıya alındığında, fareyi değişkenin üzerine getirerek bir veri ipucunda etkin bir değişkenin değerini görüntüleyebilirsiniz. Ayrıca, etkin değişkenlerin ve geçerli değerlerinin listesini görmek için Yereller ve oto pencerelerini de açabilirsiniz. Bir izleme penceresine bir veya daha fazla değişken eklemek, uygulama yürütmeye devam ettiğinden değişkenlerin değerine odaklanmanızı sağlar.

 Uygulamanın yürütülmesini askıya aldıktan sonra (hata ayıklayıcıya bölünmesi olarak da bilinir), program kodunun geri kalanının yürütülme şeklini kontrol edersiniz. Bir yöntem çağrısından yönteme geçerek satıra göre devam edebilir veya çağrılan bir yöntemi tek bir adımda yürütebilirsiniz. Bu yordamlara uygulama aracılığıyla atlama adı verilir. Ayrıca, uygulamanın standart yürütmesini, ayarlamış olduğunuz bir sonraki kesme noktasına veya imlecinizi yerleştirdiğiniz çizgiye da sürdürebilirsiniz. Hata ayıklama oturumunu dilediğiniz zaman durdurabilirsiniz. Hata ayıklayıcı, gerekli temizleme işlemlerini gerçekleştirmek ve yürütmeden çıkmak için tasarlanmıştır.

### <a name="example-1"></a>Örnek 1
 Bu örnekte, MainPage.xaml.cs dosyasının MainPage oluşturucusunda bir kesme noktası ayarlarsınız, ilk yönteme adımlayın, değişken değerlerini görüntüleyin ve sonra hata ayıklamayı durdurun.

 **Bir kesme noktası ayarlayın.** MainPage oluşturucusundaki bildiriminde bir kesme noktası ayarlayın `methodTrack = "Main Page";` . Kaynak kodu düzenleyicisinin gölgeli Cilt payının (klavye: imleci satıra konumlandırın ve F9 tuşuna basın) satırını seçin.

 ![Adımla](../debugger/media/dbg-basics-stepinto.png "DBG_Basics_StepInto")

 Kesme noktası simgesi cilt payı içinde görünür.

 **Kesme noktasına çalıştırın.** **Hata Ayıkla menüsündeki hata** **ayıklamayı Başlat** seçeneğini belirleyerek hata ayıklama oturumunu başlatın (klavye: F5).

 Uygulama yürütülmeye başlar ve kesme noktasını ayarladığınız deyimden hemen önce yürütmeyi askıya alır. Cilt Paydaki geçerli çizgi simgesi konumunuzu tanımlar ve geçerli ifade vurgulanır.

 ![Kesme noktası ayarlama](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")

 Artık uygulamanın yürütülmesini denetlemektir ve program deyimlerine adım adım ilerleyecek şekilde program durumunu inceleyebilirsiniz.

 **Yöntemine adımlayın.** **Hata Ayıkla** menüsünde, **Step** (klavye: F11) öğesini seçin.

 ![Geçerli satır](../debugger/media/dbg-basics-currentline.png "DBG_Basics_CurrentLine")

 Hata ayıklayıcının, example1 yöntemine yapılan bir çağrı olan sonraki satıra taşındığını unutmayın. Yeniden adımla öğesini seçin. Hata ayıklayıcı, example1 yönteminin giriş noktasına gider. Bu, yöntemin çağrı yığınına yüklendiğini ve yerel değişkenler için belleğin ayrıldığını gösterir.

 Bir kod satırına adım adım hata ayıklayıcı aşağıdaki eylemlerden birini gerçekleştirir:

- Sonraki ifade çözümünüzdeki bir işleve bir çağrı değilse, hata ayıklayıcı deyimyi yürütür, sonraki ifadeye gider ve sonra yürütmeyi askıya alır.

- İfade, çözümünüzde bir işleve yapılan çağrıdır, hata ayıklayıcı çağrılan işlevin giriş noktasına gider ve yürütmeyi askıya alır.

  Çıkış noktasına ulaşıncaya kadar example1 deyimlerinin içine ilermeye devam edin. Hata ayıklayıcı, yönteminin kapanış küme ayracını vurgular.

  **Veri ipuçlarında değişken değerlerini inceleyin.** Fareyi bir değişken adının üzerine getirdiğinizde, değişkenin adı, değeri ve türü bir veri ipucunda görüntülenir.

  ![Hata ayıklayıcı veri İpucu](../debugger/media/dbg-basics-datatip.png "DBG_Basics_DataTip")

  Fareyi değişkenin üzerine getirin `a` . Ad, değer ve veri türünü aklınızda yazın. Fareyi değişkenin üzerine getirin `methodTrack` . Yeniden, ad, değer ve veri türünü de dikkate alın.

  **Yereller penceresindeki değişken değerlerini inceleyin.** **Hata Ayıkla** menüsünde **Windows**' un üzerine gelin ve ardından **Yereller**' i seçin. (Klavye: alt + 4).

  ![Yerel öğeler penceresi](../debugger/media/dbg-basics-localswindow.png "DBG_Basics_LocalsWindow")

  Yereller penceresi, işlevin parametrelerinin ve değişkenlerinin ağaç görünümüdür. Bir nesne değişkeninin özellikleri nesnenin kendisinin alt düğümlerdir. `this`Değişken, nesnenin kendisini temsil eden her nesne yönteminde gizli bir parametredir. Bu durumda, MainPage sınıfını temsil eder. , `methodTrack` MainPage sınıfının bir üyesi olduğundan, değeri ve veri türü altında bir satırda listelenir `this` . `this`Bilgileri görüntülemek için düğümünü genişletin `methodTrack` .

  **MethodTrack değişkeni için bir izleme ekleyin.** `methodWatch`Bu hızlı başlangıç boyunca bu değişken, örneklerde çağrılan yöntemleri göstermek için kullanılır. Değişkenin değerini görüntülemeyi kolaylaştırmak için, bunu bir Gözcü penceresine ekleyin. Yereller penceresinde değişken adına sağ tıklayın ve ardından **Gözcü Ekle**' yi seçin.

  ![Gözcü penceresi](../debugger/media/dbg-basics-watchwindow.png "DBG_Basics_WatchWindow")

  Bir izleme penceresinde birden çok değişkeni izleyebilirsiniz. Yerel öğeler ve veri ipucu pencerelerinde bulunan değerler gibi izlenen değişkenlerin değerleri, her yürütme askıya alındığında güncelleştirilir. Ayrıca kod düzenleyicisinden izleme penceresine değişkenler ekleyebilirsiniz. İzlenecek değişkeni seçin, sağ tıklayın ve ardından **Gözcü Ekle**' yi seçin.

## <a name="step-into-over-and-out-of-methods"></a><a name="BKMK_StepIntoOverOut"></a> Yönteme adımla, aşırı ve dışı Yöntemler
 Bir üst yöntem tarafından çağrılan bir yönteme adımlamayı sağlamak için, bir yöntem üzerinde adımlamak alt yöntemini yürütür ve sonra üst devam eden çağıran yöntemde yürütmeyi askıya alır. Yöntemin çalışma biçimini öğrenirsiniz ve yürütmesinin Araştırdığınız sorunu etkilemediğinden emin olmak için bir yöntem üzerinde ileredebilirsiniz.

 Yöntem çağrısı içermeyen bir kod satırı üzerinde Adımlama, çizgiyi satıra adımlamayı tıpkı yürütür.

 Bir alt yöntemin dışına atlama yöntemi yürütmeye devam eder ve ardından Yöntem çağırma yöntemine döndüğünde yürütmeyi askıya alır. İşlevin geri kalanının önemli olmadığını belirlediğinizde uzun bir işlevin dışına ilerlemeyebilirsiniz.

 İşlev üzerinde hem atlama hem de atlama işlevi yürütün.

 ![Yönteme adımla, aşırı ve dışı Yöntemler](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a>Örnek 2
 Bu örnekte, yöntemlerin içine ve dışına adımlayın.

 **MainPage oluşturucusunda example2 yöntemini çağırın.** MainPage oluşturucusunu düzenleyin ve aşağıdaki satırı `methodTrack = String.Empty;` ile değiştirin `Example2();` .

 ![Demo yönteminden example2 metodunu çağırın](../debugger/media/dbg-basics-callexample2.png "DBG_Basics_CallExample2")

 **Kesme noktasına çalıştırın.** **Hata Ayıkla menüsündeki hata** **ayıklamayı Başlat** seçeneğini belirleyerek hata ayıklama oturumunu başlatın (klavye: F5). Hata ayıklayıcı, kesme noktasında yürütmeyi askıya alır.

 **Kod satırının üzerinde adımla.** **Hata Ayıkla** menüsünde, **Atla** ' yı (klavye: F10) seçin. Hata ayıklayıcı, ifadeyi `methodTrack = "MainPage";` ifadeye adımla aynı şekilde yürütür.

 **Example2 ve Example2_A içine adımlayın.** Örnek 2 yöntemine adım adım eklemek için F11 tuşuna basın. Satıra ulaşana kadar example2 deyimlerine adımla devam edin `int x = Example2_A();` . Sonra, Example2_A giriş noktasına gitmek için bu satıra adımlayın. Example2 'e dönene kadar Example2_A her bir ifadeye adımla devam edin.

 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")

 **Bir işlevin üzerinde adımla.** Example2 'deki sonraki satırın `int y = Example2_A();` temelde önceki satırla aynı olduğunu unutmayın. Bu satırın üzerinde güvenle ileredebilirsiniz. Example2_A sürdürme of example2 ' den bu ikinci çağrıya gitmek için F10 tuşunu seçin. Bu yöntemin üzerine geçmek için F10 ' i seçin. `methodTrack`Dizesinin Example2_A yönteminin iki kez yürütüldüğünü unutmayın. Ayrıca, hata ayıklayıcının hemen bir sonraki satıra taşındığını fark edeceksiniz. Example2 devam eden noktada yürütmeyi askıya almaz.

 **İşlevin dışına adımla.** Example2_B yöntemine adım adım eklemek için F11 tuşuna basın. Example2_B Example2_A çok farklı değildir. Yöntemin dışına geçmek için **hata ayıklama** menüsünde **Step Out** (klavye: Shift + F11) seçeneğini belirleyin. `methodTrack`Değişkenin Example2_B yürütüldüğünü ve hata ayıklayıcının example2 devam eden noktaya döndürüldüğünü gösterir.

 **Hata ayıklamayı durdurun.** Hata Ayıkla menüsünde, hata ayıklamayı Durdur ' u seçin (klavye: SHIFT + F5). Bu, hata ayıklama oturumunuzu sonlandırır.

## <a name="set-a-conditional-breakpoint-run-to-the-cursor-and-visualize-a-variable"></a><a name="BKMK_ConditionCursorVisualize"></a> Koşullu kesme noktası ayarlayın, imlece çalıştırın ve bir değişkeni görselleştirin
 Koşullu kesme noktası, hata ayıklayıcının yürütmeyi askıya almasına neden olan bir koşulu belirtir. Koşul, doğru veya yanlış olarak değerlendirilebilen herhangi bir kod ifadesiyle belirtilir. Örneğin, yalnızca bir değişken belirli bir değere ulaştığında sık çağrılan bir yöntemde program durumunu incelemek için koşullu bir kesme noktası kullanabilirsiniz.

 İmlece çalıştırmak, tek seferlik kesme noktası ayarlamaya benzer. Yürütme askıya alındığında, kaynakta bir satırı seçebilir ve seçilen satıra ulaşılana kadar yürütmeyi sürdürebilirsiniz. Örneğin, bir yöntem içindeki bir döngüyle karşılaşabilirsiniz ve döngüdeki kodun doğru şekilde gerçekleştirilmesini belirleyebilirsiniz. Döngünün her tekrarında atlama yerine, döngü yürütüldükten sonra konumlandırılmış olan imlece çalıştırabilirsiniz.

 Bazen, veri ipucu veya değişken penceresinin satırında bir değişken değeri görüntülemek zordur. Hata ayıklayıcı, kaydırılabilir bir penceredeki değerin biçimli bir görünümünü sunan bir metin görselleştiricisi içinde dizeler, HTML ve XML görüntüleyebilir.

### <a name="example-3"></a>Örnek 3
 Bu örnekte, bir döngünün belirli bir yinelemesine bölmek için koşullu bir kesme noktası ayarlayın ve ardından döngüden sonra konumlandırılmış olan imlece çalıştırın. Ayrıca bir değişkenin değerini bir metin Görselleştirici içinde görüntüleyebilirsiniz.

 **MainPage oluşturucusunda Example3 yöntemini çağırın.** MainPage oluşturucusunu düzenleyin ve satır ile takip eden çizgiyi değiştirin `methodTrack = String.Empty;` `Example3();` .

 ![Demo yönteminden Example3 çağrısı yapın](../debugger/media/dbg-basics-callexample3.png "DBG_Basics_CallExample3")

 **Kesme noktasına çalıştırın.** **Hata Ayıkla menüsündeki hata** **ayıklamayı Başlat** seçeneğini belirleyerek hata ayıklama oturumunu başlatın (klavye: F5). Hata ayıklayıcı, ana sayfa yöntemindeki kesme noktasında yürütmeyi askıya alır.

 **Example3 metoduna adımla.** Example3 yönteminin giriş noktasına gitmek için **hata ayıklama** menüsünde (klavye: F11) **içine adımla** öğesini seçin. Bloğun bir veya iki döngüsü tekrarlanana kadar yönteme adımla devam edin `for` . Tüm 1000 yinelemeleriyle ilgili olarak size uzun bir süre geçtiğine göz atın.

 **Koşullu kesme noktası ayarlayın.** Kod penceresinin sol cilt payından satıra sağ tıklayın `x += i;` ve sonra **koşul**' ı seçin. **Koşul** onay kutusunu seçin ve `i == 500;` metin kutusuna yazın. **True** seçeneğini belirleyin ve **Tamam**' ı seçin. Kesme noktası, döngünün 500. yinelemesinde değeri denetlemenizi sağlar `for` .

 ![Kesme noktası koşulu iletişim kutusu](../debugger/media/dbg-basics-breakpointcondition.png "DBG_Basics_BreakpointCondition")

 Koşullu kesme noktası simgesini beyaz çarpı ile tanımlayabilirsiniz.

 ![Koşullu kesme noktası](../debugger/media/dbg-basics-conditionalbreakpoint.png "DBG_Basics_ConditionalBreakpoint")

 **Kesme noktasına çalıştırın.** Hata Ayıkla menüsünde devam ' ı (klavye: F5) seçin. Yereller penceresinde, geçerli değerinin 500 olduğunu doğrulayın `i` . Değişkenin `s` tek satır olarak temsil edileceğini ve pencereden çok daha uzun olduğunu unutmayın.

 **Görsel bir dize değişkeni.** Öğesinin **değer** sütununda büyüteç simgesine tıklayın `s` .

 Metin görselleştiricisi penceresi görünür ve dizenin değeri çok satırlı bir dize olarak sunulur.

 **İmleci imlece çalıştırın.** Satıra sağ tıklayın `methodTrack += "->Example3";` ve ardından **Imlece Çalıştır** ' ı seçin (klavye: imleci satıra taşı; CTRL + F10). Hata ayıklayıcı döngü yinelemelerini tamamlar ve sonra işlemi satırdaki yürütmeyi askıya alır.

 **Hata ayıklamayı durdurun.** Hata Ayıkla menüsünde, hata ayıklamayı Durdur ' u seçin (klavye: SHIFT + F5). Bu, hata ayıklama oturumunuzu sonlandırır.

## <a name="edit-and-continue-recover-from-an-exception"></a><a name="BKMK_EditContinueRecoverExceptions"></a> Düzenle ve devam et, özel durumdan kurtar
 Bazı durumlarda, Visual Studio hata ayıklayıcısında kod yazdığınızda, değişkenlerin değerini ve hatta Logics deyimlerini değiştirme fırsatına sahip olursunuz. Bu işlev Düzenle ve devam et olarak adlandırılır.

 Düzenle ve devam et özellikle bir özel durumla kesme yaptığınızda yararlı olabilir. Özel durumdan kaçınmak için uzun ve ilgili bir yordamda hata ayıklamayı durdurup yeniden başlatmak yerine, özel durumu ortaya çıkar ve ardından sorunlu değişkeni veya ifadeyi değiştirin ve ardından bir özel durum oluşturmayan geçerli hata ayıklama oturumuna devam edebilirsiniz.

 Çok çeşitli durumlarda Düzenle ve devam et özelliğini kullanabilseniz de, koşullar programlama diline, program yığınının geçerli durumuna ve hata ayıklayıcının işlemi bozmadan durum değiştirme özelliğine bağlı olduğundan, düzenleme ve devam etmeyi desteklemeyen belirli koşullar belirtilmelidir. Bir düzenleme değişikliğinin desteklenip desteklenmediğini belirlemenin en iyi yolu, yalnızca deneyin. hata ayıklayıcı, değişikliğin desteklenmediğini hemen bilmenize olanak sağlar.

### <a name="example-4"></a>Örnek 4
 Bu örnekte, hata ayıklayıcıyı bir özel durumla çalıştırın, özel durumu geri sarın ve yöntemin mantığını düzeltin ve sonra yöntemi yürütmeye devam edebilmeniz için bir değişkenin değerini değiştirirsiniz.

 **MainPage oluşturucusunda example4 yöntemini çağırın.** MainPage () oluşturucusunu düzenleyin ve satır ile takip eden çizgiyi değiştirin `methodTrack = String.Empty;` `Example4();` .

 ![Demo yönteminden example4 çağrısı yapın](../debugger/media/dbg-basics-callexample4.png "DBG_Basics_CallExample4")

 **Özel duruma çalıştırın.** **Hata Ayıkla menüsündeki hata** **ayıklamayı Başlat** seçeneğini belirleyerek hata ayıklama oturumunu başlatın (klavye: F5). Yürütmeyi yeniden başlatmak için F5 tuşuna basın. Hata ayıklayıcı, Example4 yönteminin özel durumunda yürütmeyi askıya alır ve bir özel durum iletişim kutusu görüntüler.

 ![Özel durum iletişim kutusu](../debugger/media/dbg-basics-exceptiondlg.png "DBG_Basics_ExceptionDlg")

 **Program mantığını değiştirin.** Hatanın koşulda olması açıktır `if` : değeri `x` 0 ' dan sonra değil, sıfıra eşit değilse, değeri değiştirilmelidir `x` `x` . Metodun mantığını onarmak için **Kes** ' i seçin. Satırı düzenlemeye çalıştığınızda başka bir iletişim kutusu görüntülenir.

 ![Düzenle ve devam et iletişim kutusu](../debugger/media/dbg-basics-editandcontinuedlg.png "DBG_Basics_EditAndContinueDlg")

 **Düzenle** ' yi seçin ve sonra satırı `if (x != 0)` olarak değiştirin `if (x == 0)` . Hata ayıklayıcı, kaynak dosyanın program mantığındaki değişiklikleri devam ettirir.

 **Değişken değerini değiştirin.** Değerini `x` bir veri ipucunda veya Locals penceresinde inceleyin. Hala 0 (sıfır). Özgün özel duruma neden olan bir ifadeyi yürütmeye çalışırsanız, yalnızca yeniden oluşturulur. Değerini değiştirebilirsiniz `x` . Yereller penceresinde **x** satırının **değer** sütununa çift tıklayın. Değeri 0 ' dan 1 ' e değiştirin.

 ![Locals penceresinde bir değer düzenleme](../debugger/media/dbg-basics-editandcontinuefix.png "DBG_Basics_EditAndContinueFix")

 Daha önce bir özel durum oluşturan ifadeye geçmek istediğiniz F11 tuşuna basın. Satırın hata olmadan yürütüldüğünü unutmayın. F11 tuşunu yeniden seçin.

 **Hata ayıklamayı durdurun.** **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur** ' u seçin (klavye: SHIFT + F5). Bu, hata ayıklama oturumunuzu sonlandırır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Hata ayıklama oturumu başlatma (vb, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) [Windows Mağazası için askıya alma, geri alma ve arka plan olaylarını tetikleme)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [Visual Studio 'da hata ayıklama uygulamaları](../debugger/debug-store-apps-in-visual-studio.md)
