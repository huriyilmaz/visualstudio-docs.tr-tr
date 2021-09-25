---
title: Hata ayıklayıcıya ilk bakış
description: Kullanmaya başlayın hata ayıklayıcısını kullanarak Visual Studio ayıklama
ms.custom: ''
ms.date: 09/23/2021
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: afb737484fef3df525596e66159b2d206dc08880
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427362"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Visual Studio Debugger'a bakın

Bu konu başlığında, uygulama tarafından sağlanan hata ayıklayıcı Visual Studio. Bu Visual Studio, uygulamanıza hata ayıklarken *genellikle* uygulamayı hata ayıklayıcı eklenmiş şekilde (hata ayıklayıcı modunda) çalıştırabilirsiniz. Bunu yaparken hata ayıklayıcı, kodunuzun çalışırken ne yaptığını görmek için birçok yol sağlar. Kodunuzu adım adım inceleyebilirsiniz ve değişkenlerde depolanan değerlere göz atabilir, değerlerin ne zaman değişerek değişmesini görmek için değişkenler üzerinde izlemeler ayar biliyor ve kodunuzun yürütme yolunu inceleyebilirsiniz. İlk kez kodda hata ayıklamayı denediyseniz, bu konuya başlamadan önce yeni başlayanlar için [hata](../debugger/debugging-absolute-beginners.md) ayıklama konusunu okumak istiyor olabilirsiniz.

Burada açıklanan özellikler C#, C++, Visual Basic, JavaScript ve Visual Studio tarafından desteklenen diğer diller (not alınanlar dışında) için geçerlidir.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

Kesme noktaları, kod satırı veya çalışma zamanında ayrıntılı olarak incelemek istediğiniz kod bölümünü biliyorken yararlı bir özelliktir. Koşullu kesme noktaları ve işlev kesme noktaları gibi farklı kesme noktası türleri hakkında daha fazla bilgi için [bkz. Kesme noktaları kullanma.](../debugger/using-breakpoints.md)

Hata ayıklamak için, uygulama sürecine eklenen hata ayıklayıcı ile uygulamanıza başlamanız gerekir. **F5** (**Hata > Hata Ayıklamayı** Başlat ) bunu yapmak için en yaygın yol. Ancak, şu anda uygulama kodunuzu incelemek için herhangi bir kesme noktası ayarlamayabilirsiniz, bu nedenle önce bunu yapacağız ve sonra hata ayıklamaya başlayacağız. Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

Kod düzenleyicisinde açık bir dosyanız varsa, bir kod satırın sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın.

![Kesme Noktası Ayarlama](../debugger/media/dbg-tour-set-a-breakpoint.gif "Kesme noktası ayarlama")

**F5** (**Hata Ayıkla >** Hata Ayıklamayı  Başlat ) ![](../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat") veya Hata Ayıklama Araç Çubuğunda Hata Ayıklamayı Başlat düğmesine basın ve hata ayıklayıcı karşılaştığı ilk kesme noktası için çalışır. Uygulama henüz çalışmıyorsa F5 hata ayıklayıcıyı başlatır ve ilk kesme noktası üzerinde durur.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a> Adım komutlarını kullanarak hata ayıklayıcıda kodda gezinme

Çoğu komut için klavye kısayolları sağlarsınız çünkü bunlar uygulama kodunda gezinmeyi daha hızlı halelar. (Menü komutları gibi eşdeğer komutlar parantez içinde gösterilir.) Adım komutlarını kullanma hakkında daha fazla bilgi için [bkz. Hata ayıklayıcısında kodda gezinme.](../debugger/navigating-through-code-with-the-debugger.md)

Uygulamanıza hata ayıklayıcı eklenmiş olarak başlatmak için **F11** ' e ( Hata Ayıkla **> Adımla) tuşuna basın.** F11, **Adımla komutudır** ve uygulama yürütmeyi tek tek bir deyimle ilerleter. Uygulamayı F11 ile başlarken, hata ayıklayıcı yürütülen ilk deyimde hata ayıklayıcıyı kırar.

![F11 Içine Adımla](../debugger/media/dbg-tour-f11.png "F11 step INTO")

Sarı ok, aynı noktada uygulama yürütmeyi de askıya alan (bu deyim henüz yürütülmedi) hata ayıklayıcının duraklatılmış olduğu deyimi temsil eder.

F11, yürütme akışını en ayrıntılı şekilde incelemek için iyi bir yol sağlar. (Kodda daha hızlı hareket etmek için size başka seçenekler de gösteriyoruz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan kodu atlar (daha fazla ayrıntı için bkz. [Yalnızca kendi kodum).](../debugger/just-my-code.md)

>[!NOTE]
> Yönetilen kodda, özellikler ve işleçler (varsayılan davranış) üzerinden otomatik olarak adım atarak size bildirilecek olup olmadığını soran bir iletişim kutusu görüntülenir. Ayarı daha sonra değiştirmek için,  Hata Ayıklama'nın altındaki Araçlar ve Seçenekler menüsünde özellikler ve işleçler > **devre** **dışı ekleyebilirsiniz.**

## <a name="step-over-code-to-skip-functions"></a>İşlevleri atlamak için kodun üzerinden adım atla

İşlev veya yöntem çağrısı olan bir kod satırı üzerindeyken, **F11 yerine F10** ( Hata Ayıklama >**Adım** At ) tuşuna basabilirsiniz.

F10, uygulama kodundaki işlevlere veya yöntemlere adımlamadan hata ayıklayıcıyı ilerletmektedir (kod yürütülmektedir). F10 tuşuna basarak, ilgilenmeyebilirsiniz kodu atlayabilirsiniz. Bu şekilde, daha çok ilgilendiğin koda hızlıca varabilirsiniz. Adım komutlarını kullanma hakkında daha fazla bilgi için [bkz. Hata ayıklayıcısında kodda gezinme.](../debugger/navigating-through-code-with-the-debugger.md)

## <a name="step-into-a-property"></a>Bir özelliğin içine adımla

Daha önce belirtildiği gibi, hata ayıklayıcı varsayılan olarak yönetilen özellikleri ve alanları atlar, ancak **Belirli** Bir Adıma Atla komutu bu davranışı geçersiz kılmaya olanak sağlar.

Bir özellik veya alana sağ tıklayın ve Belirli Bir Alana **Adımla'yı** seçin ve ardından kullanılabilir seçeneklerden birini belirleyin.

![Kod satırı Visual Studio Hata Ayıklayıcısı'nın ekran görüntüsü. Bağlam menüsünde Belirli Bir Adımla seçilidir ve Path.set yöntemi seçilidir.](../debugger/media/dbg-tour-step-into-specific.png)

Bu örnekte, **Step Into Specific** koduna bizi `Path.set` alır.

![Path.set Visual Studio gösteren Hata Ayıklayıcısı'nın ekran görüntüsü. Küme işlevini çevreleyen küme ayraçları sarı renkle vurgulanır.](../debugger/media/dbg-tour-step-into-specific-2.png)

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Fareyi kullanarak kodunda hızla bir noktaya kadar çalıştırma

Tıklayarak **Çalıştır düğmesini kullanmak,** geçici bir kesme noktası ayarlamaya benzer. Bu komut, uygulama kodunun görünür bir bölgesi içinde hızlıca dolaşma için de kullanışlıdır. Herhangi bir açık **dosyaya tıklamak için** Çalıştır'ı kullanabilirsiniz. Bu özellik ve benzer gezinti özellikleri hakkında daha fazla bilgi için [bkz. Kodunda belirli bir konuma çalıştırma.](../debugger/navigating-through-code-with-the-debugger.md#run-to-a-specific-location-or-function)

Hata ayıklayıcıdayken, TıklanırKen Çalıştır **(Yürütmeyi** buraya kadar çalıştır) düğmesine kadar bir kod çizgisinin üzerine gelin. Hata Ayıklayıcısı'nın Visual Studio ![ düğmesi. Düğme, yürütmenin düğmenin yerleştiril olduğu satıra kadar çalışması gerektiğini gösterir.](../debugger/media/dbg-tour-run-to-click.png) sol tarafta görünür.

![Update işlevine yapılan Visual Studio sol tarafta görünen Tıklamaya Çalıştır düğmesini gösteren Hata Ayıklayıcısı'nın ekran görüntüsü.](../debugger/media/dbg-tour-run-to-click-2.png)

> [!NOTE]
> **Tıklarken Çalıştır** (Yürütmeyi buraya kadar çalıştır) düğmesi'den başlayarak [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] kullanılabilir.

**Tıklarken Çalıştır** (Yürütmeyi buraya kadar çalıştır) düğmesine tıklayın. Hata ayıklayıcısı, tıklamış olduğu kod satırına ilerler.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Hata ayıklayıcıyı geçerli işlevden dışarı ilerletin

Bazen hata ayıklama oturuma devam etmek ancak hata ayıklayıcıyı geçerli işlev boyunca ilerletebilirsiniz.

**Shift + F11 tuşlarına** basın (veya **> Adım Atarak) hata ayıkla'ya basın.**

Bu komut, geçerli işlev geri dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerleter).

## <a name="run-to-cursor"></a>İmleç için çalıştır

Kodu düzenlerken (hata ayıklayıcıda duraklatılmış yerine), uygulamanıza bir kod satırına sağ tıklayın ve Imleçte Çalıştır'ı **seçin** (veya **Ctrl'den** **F10'a basın).** Bu komut hata ayıklamayı başlatır ve geçerli kod satırı üzerinde geçici bir kesme noktası ayarlar. Bu özellik ve benzer gezinti özellikleri hakkında daha fazla bilgi için [bkz. Kodunda belirli bir konuma çalıştırma.](../debugger/navigating-through-code-with-the-debugger.md#run-to-a-specific-location-or-function)

![İmleç'e Çalıştır](../debugger/media/dbg-tour-run-to-cursor.png "Imlece kadar Çalıştır")

Kesme noktaları ayarladısanız, hata ayıklayıcı ilk kesme noktası üzerinde duraklar.

**İmleçte** Çalıştır'ın seçili olduğu kod satırına ulaşana kadar F5 **tuşuna basın.**

Bu komut, kodu düzenlerken ve hızlı bir şekilde geçici bir kesme noktası ayarlamak ve hata ayıklayıcıyı aynı anda başlatmak istediğiniz zaman kullanışlıdır.

> [!NOTE]
> Hata ayıklarken **Çağrı Yığını penceresinde** **Imleçte** Çalıştır'ı kullanabilirsiniz.

## <a name="restart-your-app-quickly"></a>Hızlı bir şekilde uygulamayı yeniden başlatın

Hata Ayıklama Araç **Çubuğunda** ![Uygulamayı](../debugger/media/dbg-tour-restart.png "Uygulamayı yeniden Başlat") Yeniden Başlat düğmesine tıklayın (veya **Ctrl + Shift + F5 tuşlarına basın).**

Yeniden **Başlat'a bassanız,** uygulamayı durdurmak ve hata ayıklayıcıyı yeniden başlatmak yerine zamandan tasarruf sağlar. Hata ayıklayıcısı, kod yürüterek isabet alan ilk kesme noktası üzerinde duraklatılır.

Hata ayıklayıcıyı durdurmak ve kod düzenleyicisine geri dönmek istemiyorsanız Yeniden ![](../debugger/media/dbg-tour-stop-debugging.png "Hata ayıklamayı Durdur") Başlat yerine Hata Ayıklamayı Durdur düğmesine **basabilirsiniz.**

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Kodunuzu düzenleyin ve hata ayıklamaya devam edin (C#, VB, C++, XAML)

Visual Studio desteklenen çoğu dilde, hata ayıklama oturumunun ortasında kodunuzu düzenleyebilir ve hata ayıklamaya devam edersiniz. Bu özelliği kullanmak için hata ayıklayıcıda duraklatılmış durumdayken imlecinizi kullanarak kodunuzla tıklayın, düzenlemeler yapmak ve hata ayıklamaya devam etmek için **F5**, **F10** veya **F11'e** basın. Bu özelliği kullanma ve özellik sınırlamaları hakkında daha fazla bilgi için bkz. [Düzenle ve Devam Edin.](../debugger/edit-and-continue.md)

![Düzenleme ve hata ayıklamaya devam](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Hata ayıklama oturumu sırasında XAML kodunu değiştirmek için bkz. XAML kodunu kullanarak [XAML kodu yazma ve hata XAML Çalışırken Yeniden Yükleme.](../xaml-tools/xaml-hot-reload.md)

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçlarıyla değişkenleri inceleme

Artık biraz bilginiz olduğu için hata ayıklayıcı ile uygulama durumunu (değişkenleri) incelemeye başlamak için iyi bir fırsata sahipsiniz. Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en kullanışlı özelliklerinden bazılarıdır ve bunu yapmak için farklı yollar vardır. Genellikle bir sorunda hata ayıklamaya çalışırken değişkenlerin, belirli bir uygulama durumuna sahip olmasını beklediğiniz değerleri depolayarak depolamaya çalışmaya çalıştığınız olur. Veri ipuçlarını kullanma hakkında ayrıntılı bilgi için [bkz. Veri ipuçlarında veri değerlerini görüntüleme.](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)

Hata ayıklayıcıda duraklatılmış durumdayken fareyle bir nesnenin üzerine gelin ve varsayılan özellik değerini (bu örnekte dosya adı varsayılan özellik `market 031.jpg` değeridir) görüyorsunuz.

![Veri İpucu Görüntüleme](../debugger/media/dbg-tour-data-tips.gif "Veri ipucunu görüntüleme")

Tüm özelliklerini (bu örnekteki özelliği gibi) görmek `FullPath` için nesnesini genişletin.

Hata ayıklama sırasında genellikle nesnelerdeki özellik değerlerini denetlemenin hızlı bir yolunu bulmak ve veri ipuçları bunu yapmak için iyi bir yol olabilir.

> [!TIP]
> Desteklenen dillerin çoğunda, hata ayıklama oturumunun ortasında kodu düzenleyebilirsiniz. Daha fazla bilgi için bkz. [Düzenle ve Devam Edin.](../debugger/edit-and-continue.md)

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otomatikler ve Yereller pencereleriyle değişkenleri inceleme

Otomatikler **penceresinde** değişkenlerin yanı sıra geçerli değerlerini ve bunların türünü de görebilirsiniz. **Otomatikler** penceresinde, geçerli satırda veya önceki satırda kullanılan tüm değişkenler gösterilir (C++ içinde pencere, önceki üç kod satırındaki değişkenleri gösterir. Dile özgü davranış için belgeleri inceleyin). Bu pencereleri kullanma hakkında daha fazla bilgi için [Bkz. Otomatikler ve Yereller pencerelerinde değişkenleri inceleme.](../debugger/autos-and-locals-windows.md)

Hata ayıklama sırasında kod **düzenleyicisinin en** altındaki Otomatikler penceresine bakın.

![Otomatikler Penceresi](../debugger/media/dbg-tour-autos-window.png "Otomatik değişkenler penceresi")

> [!NOTE]
> JavaScript 'te, **Yereller** penceresi desteklenir, ancak **oto** penceresi desteklenmez.

Sonra, **Yereller** penceresine bakın. **Yereller** penceresi, şu anda kapsamda olan değişkenleri gösterir.

![Yereller penceresi](../debugger/media/dbg-tour-locals-window.png "Yerel öğeler penceresi")

Bu örnekte, `this` nesnesi ve nesnesi `f` kapsamdadır. Daha fazla bilgi için bkz. [oto ve yereller Windows değişkenleri İnceleme](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>İzleme ayarlama

Bir gözü tutmak istediğiniz bir değişken (veya bir ifade) belirtmek için bir **Gözcü** penceresi kullanabilirsiniz. Ayrıntılı bilgi için bkz. [izleme ve hızlı izleme Windows kullanarak Izleme ayarlama](../debugger/watch-and-quickwatch-windows.md).

Hata ayıklarken, bir nesneye sağ tıklayın ve **Gözcü Ekle**' yi seçin.

![Gözcü penceresi](../debugger/media/dbg-tour-watch-window.png "Gözcü penceresi")

Bu örnekte, nesnesinde bir izleme kümesi vardır `f` ve hata ayıklayıcıda geçiş yaparken değer değişikliğini görebilirsiniz. Diğer değişken pencerelerinin aksine, **Watch** Windows her zaman izlemekte olduğunuz değişkenleri gösterir (kapsam dışında gri renkte bulunur).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleyin

Çağrı yığını penceresi, yöntemlerin ve işlevlerin hangi sırada **çağrılacağını** gösterir. Üstteki satırda geçerli işlev ( `Update` Bu örnekteki yöntem) gösterilir. İkinci satır, `Update` `Path.set` özelliğinden çağrılan ve bu şekilde devam eden gösterir. Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yoldur. Ayrıntılı bilgi için bkz. [nasıl yapılır: çağrı yığınını İnceleme](../debugger/how-to-use-the-call-stack-window.md).

> [!NOTE]
> **Çağrı yığını** penceresi, tutulma gibi bazı NDES 'Teki hata ayıklama perspektifine benzer.

Hata ayıklarken **çağrı yığını** penceresine, varsayılan olarak sağ alt bölmede da açık ' a tıklayın.

![Çağrı yığınını inceleyin](../debugger/media/dbg-tour-call-stack.png "Çağrı yığınını inceleyin")

Bir kod satırına çift tıklayarak bu kaynak koda bakabilir ve ayrıca hata ayıklayıcı tarafından incelenen geçerli kapsamı da değiştirebilirsiniz. Bu, hata ayıklayıcıyı ilerlemez.

Ayrıca, **çağrı yığını** penceresindeki diğer işlemleri yapmak için sağ tıklama menülerini de kullanabilirsiniz. Örneğin, belirli işlevlere kesme noktaları ekleyebilirsiniz, uygulamayı **Imlece Çalıştır**' ı kullanarak yeniden başlatabilir ve kaynak kodunu inceleyebilirsiniz.

## <a name="inspect-an-exception"></a><a name="exception"></a> Özel durum İnceleme

Uygulamanız bir özel durum oluşturduğunda, hata ayıklayıcı sizi özel durumu oluşturan kod satırına götürür. Ayrıntılı bilgi için bkz. [özel durum yardımcısını kullanarak özel durum İnceleme](../debugger/exception-helper.md).

![Özel durum Yardımcısı](../debugger/media/dbg-tour-exception-helper.png "Özel durum Yardımcısı")

Bu örnekte, **özel durum Yardımcısı** size bir `System.Argument` özel durum ve yolun geçerli bir form olmadığını belirten bir hata iletisi gösterir. Bu nedenle, bir yöntem veya işlev bağımsız değişkeninde oluşan hatayı biliyoruz.

Bu örnekte, çağrı, `DirectoryInfo` değişkende depolanan boş dizede hata verdi `value` .

Özel durum Yardımcısı, hata ayıklamanıza yardımcı olabilecek harika bir özelliktir. Hata ayrıntılarını görüntüle ve özel durum Yardımcısı 'ndan bir izleme ekleme gibi işlemler de yapabilirsiniz. Ya da gerekirse, belirli bir özel durumu oluşturma koşullarını değiştirebilirsiniz. Kodunuzda özel durumların nasıl işleneceği hakkında daha fazla bilgi için bkz. [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md).

bu özel durum türünün nasıl işleneceği hakkında daha fazla seçenek görmek için **özel durum Ayarlar** düğümünü genişletin, ancak bu tur için herhangi bir şeyi değiştirmeniz gerekmez!

## <a name="configure-debugging"></a>Hata ayıklamayı yapılandırma

Projenizi hata ayıklama [veya sürüm yapılandırması](../debugger/how-to-set-debug-and-release-configurations.md)olarak derlemek, hata ayıklama için proje özelliklerini yapılandırmak veya hata ayıklama için [genel ayarları](../debugger/how-to-specify-debugger-settings.md) yapılandırmak üzere yapılandırabilirsiniz. Buna ek olarak, hata ayıklayıcıyı, [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) özniteliği gibi özellikleri kullanarak özel bilgileri görüntüleyecek şekilde veya C/C++, [Natvis çerçevesi](create-custom-views-of-native-objects.md)için de yapılandırabilirsiniz.

Hata ayıklama özellikleri her proje türüne özeldir. Örneğin, uygulamayı başlattığınızda uygulamaya geçirilecek bir bağımsız değişken belirtebilirsiniz. Projeye özgü özelliklere Çözüm Gezgini ' de projeye sağ tıklayıp **Özellikler**' i seçerek erişebilirsiniz. Hata ayıklama özellikleri, belirli proje türüne bağlı olarak genellikle **derleme** veya **hata ayıklama** sekmesinde görüntülenir.

![Project özellikleri](../debugger/media/dbg-tour-project-properties.png "Proje özellikleri")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Azure App Service içindeki canlı ASP.NET uygulamalarda hata ayıkla

**Snapshot Debugger** , yürütirken ilgilendiğiniz kodun yürütüldüğü üretim içi uygulamalarınızın anlık görüntüsünü alır. Hata ayıklayıcıya bir anlık görüntü almasını söylemek için kodunuzda anlık görüntü noktaları ve günlüğe kaydetme noktaları ayarlarsınız. Hata ayıklayıcı, üretim uygulamanızın trafiğini etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için geçen süreyi önemli ölçüde düşürmeye yardımcı olabilir.

![Snapshot Debugger 'ı başlatın](../debugger/media/snapshot-launch.png "Snapshot Debugger 'ı başlatın")

anlık görüntü koleksiyonu, Azure App Service çalıştıran ASP.NET uygulamalar için kullanılabilir. ASP.NET uygulamalar .NET Framework 4.6.1 veya sonraki bir sürümde çalışmalıdır ve ASP.NET Core uygulamaların Windows üzerinde .net Core 2,0 veya üzeri sürümlerde çalışıyor olması gerekir.

daha fazla bilgi için bkz. [Snapshot Debugger kullanarak canlı ASP.NET uygulamalarda hata ayıklama](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>IntelliTrace adım geri (Visual Studio Enterprise) ile anlık görüntüleri görüntüleme

**IntelliTrace adım geri** alma, her kesme noktası ve hata ayıklayıcı adım olayında uygulamanızın bir anlık görüntüsünü otomatik olarak alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenize ve uygulamanın geçmişte olduğu gibi durumunu görüntülemenize imkan tanır. IntelliTrace adım geri dönüş, önceki uygulama durumunu görmek istediğinizde, ancak hata ayıklamayı yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemediğinizde size zaman kazandırabilir.

Hata ayıklama araç çubuğundaki **geri** ve **adım ileri** düğmelerini kullanarak anlık görüntülerle gezinerek görüntüleyebilirsiniz. Bu düğmeler **Tanılama araçları** penceresindeki **Olaylar** sekmesinde görüntülenen olaylara gider.

![Geri adımla ve Ilet düğmeleri](../debugger/media/intellitrace-step-back-icons-description.png  "Geri adımla ve Ilet düğmeleri")

Daha fazla bilgi için bkz. [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md) sayfası.

## <a name="debug-performance-issues"></a>Hata ayıklama performans sorunları

Uygulamanız çok yavaş çalışırsa veya çok fazla bellek kullanıyorsa, uygulamanızı önce profil oluşturma araçlarıyla test etmeniz gerekebilir. CPU kullanımı aracı ve bellek Çözümleyicisi gibi profil oluşturma araçları hakkında daha fazla bilgi için bkz. [profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide birçok hata ayıklayıcı özelliğine hızlı bir bakış sunuyoruz. Kesme noktaları gibi bu özelliklerden birine daha ayrıntılı bir bakış istemeniz gerekebilir.

> [!div class="nextstepaction"]
> [Kesme noktaları kullanmayı öğrenin](../debugger/using-breakpoints.md)
