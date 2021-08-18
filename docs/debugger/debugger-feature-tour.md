---
title: Hata ayıklayıcıya ilk bakış
description: Kullanmaya başlayın hata ayıklayıcısını kullanarak Visual Studio ayıklama
ms.custom: ''
ms.date: 07/26/2021
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0a857fc74fe76703361d260062c447f139cedc61
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134188"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Visual Studio Debugger'a bakın

Bu konu başlığında, uygulama tarafından sağlanan hata ayıklayıcı Visual Studio. Bu Visual Studio, uygulamanıza hata ayıklarken *genellikle* uygulamayı hata ayıklayıcı eklenmiş (hata ayıklayıcı modunda) ile çalıştırabilirsiniz. Bunu yaparken hata ayıklayıcı, kodunuzun çalışırken ne yaptığını görmek için birçok yol sağlar. Kodunuzu adım adım inceleyebilirsiniz ve değişkenlerde depolanan değerlere göz atabilir, değerlerin ne zaman değişerek değişmesini görmek için değişkenler üzerinde izlemeler ayar biliyor ve kodunuzun yürütme yolunu inceleyebilirsiniz. İlk kez kodda hata ayıklamayı denediyseniz, bu konuya başlamadan önce yeni başlayanlar için [hata](../debugger/debugging-absolute-beginners.md) ayıklama konusunu okumak istiyor olabilirsiniz.

Burada açıklanan özellikler C#, C++, Visual Basic, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (not alınanlar dışında).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

Hata ayıklamak için, uygulama sürecine eklenen hata ayıklayıcı ile uygulamanıza başlamanız gerekir. **F5** (**Hata > Hata Ayıklamayı** Başlat ) bunu yapmak için en yaygın yol. Ancak, şu anda uygulama kodunuzu incelemek için herhangi bir kesme noktası ayarlamayabilirsiniz, bu nedenle önce bunu yapacağız ve sonra hata ayıklamaya başlayacağız. Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

Kod düzenleyicisinde açık bir dosyanız varsa, bir kod satırın sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın.

![Kesme Noktası Ayarlama](../debugger/media/dbg-tour-set-a-breakpoint.gif "Kesme noktası ayarlama")

**F5** (**Hata Ayıklamayı >** Başlat )  veya Hata ![](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") Ayıklama Araç Çubuğunda Hata Ayıklamayı Başlat düğmesine basın ve hata ayıklayıcı karşılaştığı ilk kesme noktası için çalışır. Uygulama henüz çalışmıyorsa F5 hata ayıklayıcıyı başlatır ve ilk kesme noktası üzerinde durur.

Kesme noktaları, kod satırı veya ayrıntılı incelemek istediğiniz kod bölümünü biliyorken yararlı bir özelliktir.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a> Adım komutlarını kullanarak hata ayıklayıcıda kodda gezinme

Çoğu komut için klavye kısayollarını sağlarsınız çünkü bunlar uygulama kodunda gezinmeyi daha hızlı halelar. (Menü komutları gibi eşdeğer komutlar parantez içinde gösterilir.)

Uygulamanıza hata ayıklayıcı eklenmiş olarak başlatmak için **F11** ( Hata Ayıkla **> Adımla) tuşuna basın.** F11, **Adımla komutudır** ve uygulama yürütmeyi tek tek bir deyimle ilerleter. Uygulamayı F11 ile başlarken, hata ayıklayıcı yürütülen ilk deyimde hata ayıklayıcıyı kırar.

![F11 Içine Adımla](../debugger/media/dbg-tour-f11.png "F11 Içine Adımla")

Sarı ok, hata ayıklayıcının duraklatılmış olduğu deyimi temsil eder ve aynı noktada uygulama yürütmeyi de askıya alır (bu deyim henüz yürütülmedi).

F11, yürütme akışını en ayrıntılı şekilde incelemek için iyi bir yol sağlar. (Kodda daha hızlı hareket etmek için size başka seçenekler de gösteriyoruz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan kodu atlar (daha fazla ayrıntı için bkz. [Yalnızca kendi kodum).](../debugger/just-my-code.md)

>[!NOTE]
> Yönetilen kodda, özellikler ve işleçler (varsayılan davranış) üzerinden otomatik olarak adım atarak size bildirilecek olup olmadığını soran bir iletişim kutusu görüntülenir. Ayarı daha sonra değiştirmek için,  Hata Ayıklama'nın altındaki Araçlar ve Seçenekler menüsündeki Özellikler ve işleçler **> atla** ayarını **devre dışı ekleyebilirsiniz.**

## <a name="step-over-code-to-skip-functions"></a>İşlevleri atlamak için kodun üzerinden adım atla

İşlev veya yöntem çağrısı olan bir kod satırı üzerindeyken **F11 yerine F10** ( Hata Ayıklama **> Adım** At ) tuşuna basabilirsiniz.

F10, uygulama kodundaki işlevlere veya yöntemlere adımlamadan hata ayıklayıcıyı ilerletmektedir (kod yürütülmektedir). F10 tuşuna basarak, ilgilenmeyebilirsiniz kodu atlayabilirsiniz. Bu şekilde, daha çok ilgilendiğin koda hızlıca varabilirsiniz.

## <a name="step-into-a-property"></a>Bir özelliğin içine adımla

Daha önce belirtildiği gibi, hata ayıklayıcı varsayılan olarak yönetilen özellikleri ve alanları atlar, ancak **Belirli** Bir Adıma Atla komutu bu davranışı geçersiz kılmaya olanak sağlar.

Bir özellik veya alana sağ tıklayın ve Belirli Bir Alana Adımla'yı seçin ve ardından kullanılabilir seçeneklerden birini belirleyin.

![Kod satırı Visual Studio Hata Ayıklayıcısı'nın ekran görüntüsü. Bağlam menüsünde Belirli Bir Adımla seçilidir ve Path.set yöntemi seçilidir.](../debugger/media/dbg-tour-step-into-specific.png)

Bu örnekte, **Step Into Specific** koduna bizi `Path.set` alır.

![Path.set Visual Studio gösteren Hata Ayıklayıcısı'nın ekran görüntüsü. Küme işlevini çevreleyen küme ayraçları sarı renkle vurgulanır.](../debugger/media/dbg-tour-step-into-specific-2.png)

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Fareyi kullanarak kodunda hızla bir noktaya kadar çalıştırma

Hata ayıklayıcıdayken, Hata Ayıklayıcı'daki  Tıklarken Çalıştır (Yürütmeyi buraya kadar çalıştır) düğmesine kadar bir kod satırı üzerine gelin. Hata Ayıklayıcısı'nın Visual Studio ![ düğmesi. Düğme, yürütmenin düğmenin yerleştiril olduğu satıra kadar çalışması gerektiğini gösterir.](../debugger/media/dbg-tour-run-to-click.png) sol tarafta görünür.

![Update işlevine yapılan Visual Studio sol tarafta görünen Tıklamaya Çalıştır düğmesini gösteren Hata Ayıklayıcısı'nın ekran görüntüsü.](../debugger/media/dbg-tour-run-to-click-2.png)

> [!NOTE]
> **Tıklarken Çalıştır** (Yürütmeyi buraya kadar çalıştır) düğmesi'den başlayarak [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] kullanılabilir.

**Tıklarken Çalıştır** (Yürütmeyi buraya kadar çalıştır) düğmesine tıklayın. Hata ayıklayıcısı, tıklamış olduğu kod satırına ilerler.

Bu düğmeyi kullanmak, geçici bir kesme noktası ayarlamaya benzer. Bu komut, uygulama kodunun görünür bir bölgesi içinde hızlıca dolaşma için de kullanışlıdır. Herhangi bir açık **dosyaya tıklamak için** Çalıştır'ı kullanabilirsiniz.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Hata ayıklayıcıyı geçerli işlevden dışarı ilerletin

Bazen hata ayıklama oturuma devam etmek ancak hata ayıklayıcıyı geçerli işlev boyunca ilerletebilirsiniz.

**Shift + F11 tuşlarına** basın (veya **> AdımLa) tuşlarına basın.**

Bu komut, geçerli işlev geri dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerleter).

## <a name="run-to-cursor"></a>İmleç için çalıştır

Kodu düzenlerken (hata ayıklayıcıda duraklatılmış yerine), uygulamanıza bir kod satırına sağ tıklayın ve Imleçte Çalıştır'ı **seçin** (veya **Ctrl'den** **F10'a basın).** Bu komut hata ayıklamayı başlatır ve geçerli kod satırı üzerinde geçici bir kesme noktası ayarlar.

![İmleç'e Çalıştır](../debugger/media/dbg-tour-run-to-cursor.png "İmleç'e Çalıştır")

Kesme noktaları ayarladısanız, hata ayıklayıcı ilk kesme noktası üzerinde duraklar.

**İmleçte** Çalıştır'ın seçili olduğu kod satırına ulaşana kadar F5 **tuşuna basın.**

Bu komut, kodu düzenlerken ve hızlı bir şekilde geçici bir kesme noktası ayarlamak ve hata ayıklayıcıyı aynı anda başlatmak istediğiniz zaman kullanışlıdır.

> [!NOTE]
> Hata ayıklarken **Çağrı Yığını penceresinde** **Imleçte** Çalıştır'ı kullanabilirsiniz.

## <a name="restart-your-app-quickly"></a>Hızlı bir şekilde uygulamayı yeniden başlatın

Hata Ayıklama Araç **Çubuğunda** ![Uygulamayı Yeniden](../debugger/media/dbg-tour-restart.png "Uygulamayı Yeniden Başlatma") Başlat düğmesine tıklayın (veya **Ctrl + Shift + F5 tuşlarına basın).**

Yeniden **Başlat'a bassanız,** uygulamayı durdurmak ve hata ayıklayıcıyı yeniden başlatmak yerine zamandan tasarruf sağlar. Hata ayıklayıcısı, kod yürüterek isabet alan ilk kesme noktası üzerinde duraklatılır.

Hata ayıklayıcıyı durdurmak ve kod düzenleyicisine geri dönmek istemiyorsanız, ![](../debugger/media/dbg-tour-stop-debugging.png "Hata Ayıklamayı Durdurma") Yeniden Başlat yerine Hata Ayıklamayı Durdur düğmesine **basabilirsiniz.**

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Kodunuzu düzenleyin ve hata ayıklamaya devam edin (C#, VB, C++, XAML)

Uygulama tarafından desteklenen çoğu Visual Studio, hata ayıklama oturumunun ortasında kodunuzu düzenleyebilir ve hata ayıklamaya devam edersiniz. Bu özelliği kullanmak için hata ayıklayıcıda duraklatılmış durumdayken imlecinizi kullanarak kodunuzla tıklayın, düzenlemeler yapmak ve hata ayıklamaya devam etmek için **F5**, **F10** veya **F11'e** basın.

![Düzenleme ve hata ayıklamaya devam](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Özelliği kullanma ve özellik sınırlamaları hakkında daha fazla bilgi için bkz. [Düzenle ve Devam Edin.](../debugger/edit-and-continue.md)

Hata ayıklama oturumu sırasında XAML kodunu değiştirmek için bkz. XAML kodunu kullanarak [XAML kodu yazma ve hata XAML Çalışırken Yeniden Yükleme.](../xaml-tools/xaml-hot-reload.md)

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçlarıyla değişkenleri inceleme

Artık biraz bilginiz olduğu için hata ayıklayıcı ile uygulama durumunu (değişkenleri) incelemeye başlamak için iyi bir fırsata sahipsiniz. Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en kullanışlı özelliklerinden bazılarıdır ve bunu yapmak için farklı yollar vardır. Genellikle bir sorunda hata ayıklamaya çalışırken değişkenlerin, belirli bir uygulama durumuna sahip olmasını beklediğiniz değerleri depolayarak depolamaya çalışmaya çalıştığınız olur.

Hata ayıklayıcıda duraklatılmış durumdayken fareyle bir nesnenin üzerine gelin ve varsayılan özellik değerini (bu örnekte dosya adı varsayılan özellik `market 031.jpg` değeridir) görüyorsunuz.

![Veri İpucu Görüntüleme](../debugger/media/dbg-tour-data-tips.gif "Veri ipucu görüntüleme")

Tüm özelliklerini (bu örnekteki özelliği gibi) görmek `FullPath` için nesnesini genişletin.

Hata ayıklama sırasında genellikle nesnelerdeki özellik değerlerini denetlemenin hızlı bir yolunu bulmak ve veri ipuçları bunu yapmak için iyi bir yol olabilir.

> [!TIP]
> Desteklenen dillerin çoğunda, hata ayıklama oturumunun ortasında kodu düzenleyebilirsiniz. Daha fazla bilgi için bkz. [Düzenle ve Devam Edin.](../debugger/edit-and-continue.md)

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otomatikler ve Yereller pencereleriyle değişkenleri inceleme

Hata ayıklama sırasında, kod **düzenleyicisinin** en altındaki Otomatikler penceresine bakın.

![Otomatikler Penceresi](../debugger/media/dbg-tour-autos-window.png "Otomatik değişkenler penceresi")

Otomatikler **penceresinde** değişkenlerin yanı sıra geçerli değerlerini ve bunların türünü de görebilirsiniz. **Otomatikler** penceresinde geçerli satırda veya önceki satırda kullanılan tüm değişkenler gösterilir (C++ içinde pencere, önceki üç kod satırı içinde değişkenleri gösterir. Dile özgü davranış için belgeleri inceleyin).

> [!NOTE]
> JavaScript'te **Yereller** penceresi desteklene, ancak Otomatikler **penceresi desteklanmaz.**

Ardından Yereller **penceresine** bakın. **YerelLer** penceresinde, şu anda kapsamda olan değişkenler gösterilir.

![YerelLer Penceresi](../debugger/media/dbg-tour-locals-window.png "Yerel öğeler penceresi")

Bu örnekte, `this` nesnesi ve nesnesi `f` kapsamdadır. Daha fazla bilgi için, [bkz. Inspect Variables in the Autos and Locals Windows.](../debugger/autos-and-locals-windows.md)

## <a name="set-a-watch"></a>Saat ayarlama

İzleme penceresi **kullanarak** göz tutmak istediğiniz bir değişken (veya ifade) belirtebilirsiniz.

Hata ayıklama sırasında bir nesneye sağ tıklayın ve İzleme **Ekle'yi seçin.**

![İzleme Penceresi](../debugger/media/dbg-tour-watch-window.png "Gözcü penceresi")

Bu örnekte nesnesinde bir izleme kümesi vardır ve hata ayıklayıcıda ilerlerken `f` değerinin değişmesini sebilirsiniz. Diğer değişken pencerelerinin aksine, **İzle** pencereleri her zaman izlediğiniz değişkenleri gösterir (kapsam dışındayken bunlar gri renkte görünür).

Daha fazla bilgi için [bkz. Watch ve QuickWatch](../debugger/watch-and-quickwatch-windows.md) kullanarak watch Windows

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleme

Hata **ayıklama sırasında,** varsayılan olarak sağ alt bölmede açık olan Çağrı Yığını penceresine tıklayın.

![Çağrı Yığınını Inceleme](../debugger/media/dbg-tour-call-stack.png "Çağrı yığınını inceleme")

Çağrı **Yığını** penceresi, yöntemlerin ve işlevlerin çağrıldığı sırayı gösterir. Üst satır geçerli işlevi (bu `Update` örnekteki yöntemi) gösterir. İkinci satırda `Update` özelliğinden `Path.set` çağrıldı ve bu şekilde devam etti. Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yol sağlar.

> [!NOTE]
> Çağrı **Yığını penceresi,** Eclipse gibi bazı IDE'lerde Hata Ayıklama perspektifi ile benzerdir.

Bir kod satırına çift tıklar ve bu koda göz atabilir ve hata ayıklayıcı tarafından denetlenen geçerli kapsamı da değiştirir. Bu, hata ayıklayıcıyı ilerleten bir işlem değildir.

Başka şeyler yapmak için Çağrı Yığını penceresinden sağ **tıklama** menülerini de kullanabilirsiniz. Örneğin, belirli işlevlere kesme noktaları ekler, İmleçte Çalıştır'ı kullanarak uygulamanızı yeniden başlatabilir ve kaynak kodu incelemeye gidebilirsiniz. Bkz. [Nasıl: Çağrı Yığınını Inceleme.](../debugger/how-to-use-the-call-stack-window.md)

## <a name="examine-an-exception"></a><a name="exception"></a> Özel durumu inceleme

Uygulamanız bir özel durum atarsa, hata ayıklayıcı sizi özel durumu başlatan kod satırına alır.

![Özel Durum Yardımcı](../debugger/media/dbg-tour-exception-helper.png "Özel Durum Yardımcı")

Bu örnekte, Özel **Durum Yardımcısı** size bir özel durum ve yolun yasal bir form olmadığını söyleyen `System.Argument` bir hata iletisi gösterir. Bu nedenle hatanın bir yöntem veya işlev bağımsız değişkende olduğunu biliyoruz.

Bu örnekte çağrısı, `DirectoryInfo` değişkende depolanan boş dizede hata `value` verdi.

Özel Durum Yardımcı, hatalarda hata ayıklamanıza yardımcı olan harika bir özelliktir. Ayrıca hata ayrıntılarını görüntüleme ve Özel Durum Yardımcı'dan izleme ekleme gibi şeyler de ebilirsiniz. Veya gerekirse, belirli bir özel durumu atma koşullarını değiştirebilirsiniz. Kodundaki özel durumları işleme hakkında daha fazla bilgi için bkz. [Hata ayıklama teknikleri ve araçları.](../debugger/write-better-code-with-visual-studio.md)

> [!NOTE]
> Özel Durum Yardımcısı, 'den başlayarak Özel Durum Yardımcısı'nın yerini [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] alacak.

Bu özel **durum Ayarlar** işleme hakkında daha fazla seçenek görmek için Özel durum kümesi düğümünü genişletin, ancak bu tur için hiçbir şeyi değiştirmeniz gerekmeyecek!

## <a name="configure-debugging"></a>Hata ayıklamayı yapılandırma

Projenizi Hata Ayıklama veya Yayın yapılandırması [olarak](../debugger/how-to-set-debug-and-release-configurations.md)derlemek, hata ayıklama için proje özelliklerini yapılandırmak veya hata ayıklama için [genel ayarları](../debugger/how-to-specify-debugger-settings.md) yapılandırmak üzere yapılandırabilirsiniz. Ayrıca hata ayıklayıcıyı [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) özniteliği veya C/C++ için NatVis çerçevesi gibi özellikleri kullanarak özel bilgileri [görüntüleyebilirsiniz.](create-custom-views-of-native-objects.md)

Hata ayıklama özellikleri her proje türüne özeldir. Örneğin, uygulamayı başlatarak uygulamaya geçeceği bir bağımsız değişken belirtebilirsiniz. projesinde projeye sağ tıklar ve Özellikler'i seçerek Çözüm Gezgini özelliklere **erişebilirsiniz.** Hata ayıklama özellikleri genellikle belirli bir **proje** **türüne** bağlı olarak Derleme veya Hata Ayıklama sekmesinde görünür.

![Project özellikleri](../debugger/media/dbg-tour-project-properties.png "Proje özellikleri")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Azure App Service'da canlı ASP.NET hata ayıklama

bu **Snapshot Debugger,** ilgilendiğiniz kod yürütülürken üretim uygulamalarınıza bir anlık görüntü alır. Hata ayıklayıcıya anlık görüntü alma talimatı için kodunda anlık görüntü noktaları ve günlük noktaları ayarlayın. Hata ayıklayıcısı, üretim uygulama trafiğinizi etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Bu Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için gereken zamanı önemli ölçüde azaltmanıza yardımcı olabilir.

![Anlık görüntü hata ayıklayıcısını başlatma](../debugger/media/snapshot-launch.png "Anlık görüntü hata ayıklayıcısını başlatma")

Anlık görüntü koleksiyonu, ASP.NET çalışan uygulamalar için Azure App Service. ASP.NET 4.6.1 veya sonraki bir .NET Framework üzerinde, ASP.NET Core uygulamalarının da ASP.NET Core'de .NET Core 2.0 veya sonraki bir üzerinde Windows.

Daha fazla bilgi için [bkz. ASP.NET kullanarak canlı Snapshot Debugger.](../debugger/debug-live-azure-applications.md)

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>IntelliTrace geri adım atarak anlık görüntüleri görüntüleme (Visual Studio Enterprise)

**IntelliTrace geri adımı,** her kesme noktası ve hata ayıklayıcı adımı olayında otomatik olarak uygulamanın anlık görüntüsünü alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenizin yanı sıra uygulamanın geçmişte olduğu gibi durumunu görüntülemeye olanak sağlar. IntelliTrace geri adımı önceki uygulama durumunu görmek istediğiniz ancak hata ayıklamayı yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemeyebilirsiniz.

Hata Ayıklama araç çubuğundaki Geri Adım ve İleri **Adım** düğmelerini **kullanarak** anlık görüntülerde gezinebilirsiniz ve görüntüleyebilirsiniz. Bu düğmeler, Tanılama Araçları penceresindeki  Olaylar **sekmesinde görünen Tanılama Araçları** gezinebilirsiniz.

![Geri ve İleri Adım Düğmeleri](../debugger/media/intellitrace-step-back-icons-description.png  "Geri ve İleri Adım düğmeleri")

Daha fazla bilgi için [IntelliTrace kullanarak önceki uygulama eyaletlerini inceleme sayfasına](../debugger/view-historical-application-state.md) bakın.

## <a name="debug-performance-issues"></a>Performans sorunlarını ayıklama

Uygulamanız çok yavaş çalışıyorsa veya çok fazla bellek kullanıyorsa, profil oluşturma araçlarıyla erkenden test etmek zorundayabilirsiniz. CPU Kullanımı aracı ve Bellek Çözümleyicisi gibi profil oluşturma araçları hakkında daha fazla bilgi için bkz. Profil oluşturma [araçlarına ilk bakış.](../profiling/profiling-feature-tour.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, birçok hata ayıklayıcı özelliğine hızlı bir bakış edindi. Kesme noktaları gibi bu özelliklerden birini daha ayrıntılı bir şekilde görmek istiyor olabilir.

> [!div class="nextstepaction"]
> [Kesme noktaları kullanmayı öğrenin](../debugger/using-breakpoints.md)
