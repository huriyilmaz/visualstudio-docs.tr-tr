---
title: Hata ayıklayıcıya ilk bakış
description: Visual Studio hata ayıklama sını kullanarak uygulamaları hata ayıklama ya da hata ayıklama kullanmaya başlayın
ms.custom: ''
ms.date: 04/08/2019
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93973322c40ca62396414317c2ad8875e9b94854
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77578948"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Visual Studio Debugger ilk bakış

Bu konu Visual Studio tarafından sağlanan hata ayıklama araçlarını tanıtır. Visual Studio bağlamında, *uygulamanızı hata ayıklama*yaptığınızda, genellikle uygulamayı hata ayıklama ekli (yani hata ayıklama modunda) çalıştırdığınız anlamına gelir. Bunu yaptığınızda, hata ayıklayıcı, kodunuzu çalışırken ne yaptığını görmek için birçok yol sağlar. Kodunuzu gözden geçirebilir ve değişkenlerde depolanan değerlere bakabilirsiniz, değerler ne zaman değiştiğini görmek için değişkenler üzerinde saatler ayarlayabilir, kodunuzu yürütme yolunu inceleyebilirsiniz, ve diğerleri. Bu kod hata ayıklama denedim ilk kez ise, bu konu geçmeden önce [mutlak yeni başlayanlar için Hata Ayıklama](../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

Burada açıklanan özellikler C#, C++, Visual Basic, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (not edilendurumlar hariç).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Bir kesme noktası ayarlayın ve hata ayıklamayı başlatın

Hata ayıklama için uygulamanızı uygulama işlemine bağlı hata ayıklama ile başlatmanız gerekir. **F5** **(Hata Ayıklama > Başlat Hata Ayıklama**) bunu yapmanın en yaygın yoludur. Ancak, şu anda uygulama kodunuzu incelemek için herhangi bir kesme noktası ayarlamamış olabilirsiniz, bu nedenle bunu önce yapacağız ve sonra hata ayıklamaya başlayacağız. Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio'nun çalışan kodunuzu nerede askıya alması gerektiğini gösterir, böylece değişkenlerin değerlerine veya belleğin davranışına veya bir kod dalının çalıştırılıp çalıştırılmayacağına göz atabilirsiniz.

Kod düzenleyicisinde açık bir dosyanız varsa, kod satırının solundaki kenar boşluğuna tıklayarak bir kesme noktası ayarlayabilirsiniz.

![Bir Kesme Noktası Ayarlama](../debugger/media/dbg-tour-set-a-breakpoint.gif "Kesme noktası ayarlama")

**Hata** **Ayıklama (Hata Ayıklama > Hata Ayıklama**başlat) veya Hata **Ayıklama** Başlat düğmesine basın Hata Ayıklama Araç Çubuğu'nda Hata ![Ayıklama](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklama'yı Başlatma") başlatın ve hata ayıklayıcı karşılaştığı ilk kesme noktasına çalışır. Uygulama henüz çalışmıyorsa, F5 hata ayıklamayı başlatır ve ilk kesme noktasında durur.

Kesme noktaları, kod satırını veya ayrıntılı olarak incelemek istediğiniz kod bölümünü bildiğinizde yararlı bir özelliktir.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a>Adım komutlarını kullanarak hata ayıklayıcıda kodda gezinme

Uygulama kodunuzu daha hızlı gezinmeyi sağladıkları için çoğu komut için klavye kısayollarını sağlarız. (Menü komutları gibi eşdeğer komutlar parantez içinde gösterilir.)

Uygulamanızı hata ayıklama ekli olarak başlatmak için **F11** **(Hata Ayıklama > Adım Adım)** tuşuna basın. F11, **Step Into** komutudur ve uygulama yürütmeyi bir er seferde bir ekibe iletir. Uygulamayı F11 ile başlattığınızda, hata ayıklama yürütülen ilk deyimde kırılır.

![F11 Adım Adım](../debugger/media/dbg-tour-f11.png "F11 Adım Adım")

Sarı ok, hata ayıklamanın duraklatılmış olduğu ve aynı noktada uygulama yürütmesini de askıya alan deyimi temsil eder (bu bildirim henüz yürütülmedi).

F11, yürütme akışını en ayrıntılı olarak incelemek için iyi bir yoldur. (Kod üzerinden daha hızlı hareket etmek için, size diğer bazı seçenekleri de gösteririz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan kodu atlar (daha fazla ayrıntı istiyorsanız, [Bkz. Just My Code).](../debugger/just-my-code.md)

>[!NOTE]
> Yönetilen kodda, özelliklerin ve işleçlerin (varsayılan davranış) üzerine otomatik olarak bastığınızda bilgilendirilmek isteyip istemediğiniz soran bir iletişim kutusu görürsünüz. Ayarı daha sonra değiştirmek isterseniz, **Hata Ayıklama**altında **Araçlar > Seçenekleri** menüsünde özellikleri ve **işleçler** ayarı üzerinden adım devre dışı.

## <a name="step-over-code-to-skip-functions"></a>Işlevleri atlamak için kodun üzerine geçme

İşlev veya yöntem çağrısı olan bir kod satırında olduğunuzda, **F11 yerine F10** **(Hata Ayıklama > Adımı)** tuşuna basabilirsiniz.

F10, hata ayıklayıcıyı uygulama kodunuzdaki işlevlere veya yöntemlere adım atmadan ilerler (kod hala yürütülür). F10 tuşuna basarak, ilgilenmediğiniz kodu atlayabilirsiniz. Bu şekilde, daha fazla ilgilendiğiniz koda hızla ulaşabilirsiniz.

## <a name="step-into-a-property"></a>Bir özelliğe adım atma

Daha önce de belirtildiği gibi, varsayılan olarak hata ayıklama yönetilen özellikleri ve alanları atlar, ancak **Adım Belirli** komutu bu davranışı geçersiz kılmak için izin verir.

Bir özellik veya alana sağ tıklayın ve **Belirli Adım'ı**seçin, ardından kullanılabilir seçeneklerden birini seçin.

![Belirli adım](../debugger/media/dbg-tour-step-into-specific.png "Belirli Bir Adım")

Bu örnekte, **Step Into Specific** bizi `Path.set`' için koda

![Belirli adım](../debugger/media/dbg-tour-step-into-specific-2.png "Belirli Bir Adım")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Fareyi kullanarak kodunuzun bir noktasına hızlı bir şekilde koş

Hata ayıklayıcıdayken, soltarafta **Çalıştır'dan** Tıklat'a kadar bir kod satırının üzerinde gezin (Yürütmeyi buraya çalıştırın) düğmesi ![görünür.](../debugger/media/dbg-tour-run-to-click.png "RunToClick")

![Tıklanan Satıra Kadar Çalıştır](../debugger/media/dbg-tour-run-to-click-2.png "Tıklanan Satıra Kadar Çalıştır")

> [!NOTE]
> **Tıklatmak Için Çalıştır** (Yürütmeyi buraya çalıştır) [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]butonundan başlayarak kullanılabilir.

**Tıklatmak için Çalıştır** (Yürütmeyi buraya çalıştır) düğmesini tıklatın. Hata ayıklayıcı tıklattığınız kod satırına ilerler.

Bu düğmeyi kullanmak geçici bir kesme noktası ayarlamaya benzer. Bu komut, uygulama kodunun görünür bir bölgesinde hızlı bir şekilde dolaşmak için de kullanışlıdır. Herhangi bir açık dosyada **Tıklatmak için Çalıştır'ı** kullanabilirsiniz.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Hata ayıklamayı geçerli işlevden çıkarma

Bazen hata ayıklama oturumunuza devam etmek, ancak hata ayıklamayı geçerli işlev boyunca ilerletebilirsiniz.

**Shift + F11** tuşuna basın (veya **Hata Ayıklama > Adım Dışarı**).

Bu komut, geçerli işlev dönene kadar uygulama yürütmesini devam ettirer (ve hata ayıklamayı ilerler).

## <a name="run-to-cursor"></a>İmlecile çalıştır

Hata **Ayıklama** yı durdur un kırmızı düğmeye basarak hata ayıklamayı durdurun ![Hata Ayıklama'yı durdurun](../debugger/media/dbg-tour-stop-debugging.png "Hata Ayıklamayı Durdur") veya**F5'i** **Kaydırın.** + 

Uygulamanızdaki bir kod satırına sağ tıklayın ve **İmlere Çalıştır'ı**seçin. Bu komut hata ayıklamayı başlatır ve geçerli kod satırında geçici bir kesme noktası ayarlar.

![İmlec'e Çalıştır](../debugger/media/dbg-tour-run-to-cursor.png "İmlec'e Çalıştır")

Kesme noktaları ayarladıysanız, hata ayıklama çarptırdığı ilk kesme noktasında duraklar.

**İmlec'e Çalıştır'ı**seçtiğiniz kod satırına ulaşana kadar **F5** tuşuna basın.

Bu komut, kodu düzenlerken ve hızlı bir şekilde geçici bir kesme noktası ayarlamak ve hata ayıklayıcıyı aynı anda başlatmak istediğinizde yararlıdır.

> [!NOTE]
> Hata ayıklama sırasında **Çağrı Yığını** penceresinde **Imleç için Çalıştır'ı** kullanabilirsiniz.

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızla yeniden başlatın

Hata Ayıklama Araç Çubuğu'ndaki **(Ctrl + Shift +F5)** **Uygulamayı Yeniden** ![Başlat](../debugger/media/dbg-tour-restart.png "Uygulamayı Yeniden Başlat") düğmesini tıklatın.

**Yeniden Başlat**tuşuna bastığınızda, uygulamayı durdurmak ve hata ayıklamayı yeniden başlatmak karşı zaman kazandırır. Hata ayıklayıcı, yürütme kodu tarafından vurulan ilk kesme noktasında duraklar.

Hata ayıklayıcıyı durdurmak ve kod düzenleyicisine geri dönmek istiyorsanız, **Yeniden Başlat**yerine kırmızı stop ![Hata Ayıklamayı Durdur](../debugger/media/dbg-tour-stop-debugging.png "Hata Ayıklamayı Durdur") düğmesine basabilirsiniz.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Kodunuzu edin ve hata ayıklama devam (C#, VB, C++, XAML)

Visual Studio tarafından desteklenen çoğu dilde, hata ayıklama oturumunun ortasında kodunuzu düzenleme yapabilir ve hata ayıklama devam edebilirsiniz. Bu özelliği kullanmak için hata ayıklayıcıda duraklarken imlecinizle kodunuzu tıklatın, düzeltmeler yapın ve hata ayıklama devam etmek için **F5**, **F10**veya **F11** tuşuna basın.

![Hata ayıklamayı ve hata ayıklamayı yapmaya devam etme](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Özelliği kullanma ve özellik sınırlamaları hakkında daha fazla bilgi için [bkz.](../debugger/edit-and-continue.md)

Hata ayıklama oturumu sırasında XAML kodunu değiştirmek için [bkz.](../xaml-tools/xaml-hot-reload.md)

## <a name="inspect-variables-with-data-tips"></a>Değişkenleri veri ipuçlarıyla inceleyin

Artık yolunuzu biraz bildiğinize göre, hata ayıklama ile uygulama durumunuzu (değişkenleri) incelemeye başlamak için iyi bir fırsatınız olur. Değişkenleri incelemenize olanak tanıyan özellikler hata ayıklamanın en yararlı özelliklerinden bazılarıdır ve bunu yapmanın farklı yolları vardır. Genellikle, bir sorunu hata ayıklamaya çalıştığınızda, değişkenlerin belirli bir uygulama durumunda olmasını beklediğiniz değerleri depolayıp depolamadığını bulmaya çalışırsınız.

Hata ayıklamada duraklatılırken, fareyle birlikte bir nesnenin üzerine gezinir ve varsayılan özellik `market 031.jpg` değerini görürsünüz (bu örnekte, dosya adı varsayılan özellik değeridir).

![Veri İpucunu Görüntüleme](../debugger/media/dbg-tour-data-tips.gif "Veri ipucunu görüntüleme")

Tüm özelliklerini (bu örnekteki `FullPath` özellik gibi) görmek için nesneyi genişletin.

Genellikle, hata ayıklama, nesnelerüzerinde özellik değerlerini denetlemek için hızlı bir yol istiyorum ve veri ipuçları bunu yapmak için iyi bir yoldur.

> [!TIP]
> Desteklenen dillerin çoğunda, hata ayıklama oturumunun ortasında kodu değiştirebilirsiniz. Daha fazla bilgi için [bkz.](../debugger/edit-and-continue.md)

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otomatik ve Yerel pencerelerle değişkenleri inceleyin

Hata ayıklama sırasında, kod düzenleyicisinin altındaki **Otomatikler** penceresine bakın.

![Otomatik Pencere](../debugger/media/dbg-tour-autos-window.png "Otomatik değişkenler penceresi")

Otomatik **Ler** penceresinde, değişkenleri geçerli değerleri ve türüyle birlikte görürsünüz. **Otomatik ler** penceresi, geçerli satırda veya önceki satırda kullanılan tüm değişkenleri gösterir (C++'da, pencere önceki üç kod satırındaki değişkenleri gösterir. Dillere özgü davranış için belgeleri denetleyin).

> [!NOTE]
> JavaScript'te **Yerel ler** penceresi desteklenir, ancak **Otomatik ler** penceresi desteklenmez.

Sonra, Yerel **pencereye** bak. **Yerel ler** penceresi, şu anda kapsamda olan değişkenleri gösterir.

![Yerel Pencere](../debugger/media/dbg-tour-locals-window.png "Yerel öğeler penceresi")

Bu örnekte, `this` nesne ve `f` nesne kapsamdadır. Daha fazla bilgi için, [Bkz. Otomatik ve Yerel Windows'daki Değişkenleri İncele.](../debugger/autos-and-locals-windows.md)

## <a name="set-a-watch"></a>Bir saat ayarlama

İzlemek istediğiniz bir değişkeni (veya ifadeyi) belirtmek için **İzleme** penceresini kullanabilirsiniz.

Hata ayıklama sırasında bir nesneye sağ tıklayın ve **İzle Ekle'yi**seçin.

![İzleme Penceresi](../debugger/media/dbg-tour-watch-window.png "Gözcü penceresi")

Bu örnekte, `f` nesne üzerinde bir saat seti var ve hata ayıklama ile hareket ettikçe değerinin değiştiğini görebilirsiniz. Diğer değişken pencerelerden farklı olarak, **Watch** pencereleri her zaman izlediğiniz değişkenleri gösterir (kapsam dışında olduklarında gri renktedirler).

Daha fazla bilgi için bkz: [Watch ve QuickWatch Windows'u kullanarak Bir İzleme Ayarla](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Arama yığınını inceleme

Hata ayıklama sırasında **Arama Yığını** penceresini tıklatın, bu da varsayılan olarak sağ alt bölmede açılır.

![Çağrı Yığınını İncele](../debugger/media/dbg-tour-call-stack.png "Arama yığınını inceleme")

**Çağrı Yığını** penceresi, yöntemlerin ve işlevlerin çağrılma sırasını gösterir. Üst satır geçerli işlevi (bu örnekteki `Update` yöntem) gösterir. İkinci `Path.set` satır, `Update` özellikten çağrıldıve benzeri gösterir. Arama yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yoldur.

> [!NOTE]
> **Arama Yığını** penceresi Eclipse gibi bazı IDA'larda Hata Ayıklama perspektifine benzer.

Kaynak kodu na bakmak için bir kod satırına çift tıklayabilirsiniz ve bu da hata ayıklayıcı tarafından denetlenen geçerli kapsamı değiştirir. Bu hata ayıklama ilerlemez.

Başka şeyler yapmak için **Yığın Çağır** penceresinden sağ tıklatma menülerini de kullanabilirsiniz. Örneğin, kesme noktalarını belirli işlevlere ekleyebilir, **Uygulamanızı Çalıştır imlecini**kullanarak yeniden başlatabilir ve kaynak kodu incelemeye gidebilirsiniz. [Bkz. Nasıl: Çağrı Yığınını İnceleyin.](../debugger/how-to-use-the-call-stack-window.md)

## <a name="examine-an-exception"></a><a name="exception"></a>Bir özel durum inceleme

Uygulamanız bir özel durum attığında, hata ayıklayıcı sizi özel durum atan kod satırına götürür.

![Özel Durum Yardımcısı](../debugger/media/dbg-tour-exception-helper.png "Özel Durum Yardımcısı")

Bu örnekte, **Özel Durum** Yardımcısı `System.Argument` size bir özel durum ve yolun yasal bir form olmadığını belirten bir hata iletisi gösterir. Yani, hatanın bir yöntem veya işlev bağımsız değişkeninde oluştuğunu biliyoruz.

Bu örnekte, `DirectoryInfo` çağrı `value` değişkende depolanan boş dize üzerinde hata verdi.

Özel Durum Yardımcısı hata ayıklama yardımcı olabilecek harika bir özelliktir. Ayrıca hata ayrıntılarını görüntüleme ve Özel Durum Yardımcısı'ndan saat ekleme gibi şeyler de yapabilirsiniz. Veya gerekirse, belirli bir özel durum atma koşullarını değiştirebilirsiniz. Kodunuzdaki özel durumları nasıl işlerek hakkında daha fazla bilgi için Hata [Ayıklama teknikleri ve araçlarına](../debugger/write-better-code-with-visual-studio.md)bakın.

> [!NOTE]
> Özel Durum Yardımcısı, 'den [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]başlayarak Özel Durum Yardımcısı'nın yerini aldı.

Bu özel durum türünü nasıl işleyeceğinize ilişkin daha fazla seçenek görmek için **Özel Durum Ayarları** düğümünü genişletin, ancak bu tur için hiçbir şeyi değiştirmeniz gerekmez!

## <a name="configure-debugging"></a>Hata ayıklamayı yapılandırma

Projenizi [Hata Ayıklama veya Sürüm yapılandırması](../debugger/how-to-set-debug-and-release-configurations.md)olarak yapılandırmak, hata ayıklama için proje özelliklerini yapılandırmak veya hata ayıklama için [genel ayarları](../debugger/how-to-specify-debugger-settings.md) yapılandırmak üzere yapılandırabilirsiniz. Buna ek olarak, hata ayıklayıcıyı [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) özniteliği veya C/C++, [NatVis çerçevesi](create-custom-views-of-native-objects.md)gibi özellikleri kullanarak özel bilgileri görüntülemek üzere yapılandırabilirsiniz.

Hata ayıklama özellikleri her proje türüne özgüdür. Örneğin, başlattığınızda uygulamaya geçmek için bir bağımsız değişken belirtebilirsiniz. Çözüm Gezgini'nde projeyi sağ tıklatarak ve **Özellikler'i**seçerek projeye özel özelliklere erişebilirsiniz. Hata ayıklama özellikleri genellikle belirli proje türüne bağlı olarak **Yapı** veya **Hata Ayıklama** sekmesinde görünür.

![Proje özellikleri](../debugger/media/dbg-tour-project-properties.png "Proje özellikleri")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Azure Uygulama Hizmeti'nde uygulamaları ASP.NET canlı hata ayıklama

**Anlık Görüntü Hata Ayıklayıcı,** yürütmek istediğiniz kod çalıştırıldığında üretim içi uygulamalarınızın anlık görüntüsünü alır. Hata ayıklayıcıya anlık görüntü almasını söylemek için, kodunuzda anlık noktalar ve günlük noktaları ayarlarsınız. Hata ayıklama, üretim uygulamanızın trafiğini etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Anlık Görüntü Hata Ayıklama, üretim ortamlarında oluşan sorunları çözmek için gereken süreyi önemli ölçüde azaltmanıza yardımcı olabilir.

![Anlık görüntü hata ayıklama başlatın](../debugger/media/snapshot-launch.png "Anlık görüntü hata ayıklama başlatın")

Anlık görüntü koleksiyonu, Azure Uygulama Hizmeti'nde çalışan ASP.NET uygulamalar için kullanılabilir. ASP.NET uygulamaları .NET Framework 4.6.1 veya sonraki saatlerde çalışıyor olmalı ve ASP.NET Core uygulamaları .NET Core 2.0 veya daha sonra Windows'ta çalışıyor olmalıdır.

Daha fazla bilgi için [Bkz. Anlık Görüntü Hata Ayıklama'yı kullanarak uygulama ASP.NET Hata Ayıklama'](../debugger/debug-live-azure-applications.md)ya bakın.

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>IntelliTrace adım geri (Visual Studio Enterprise) ile anlık görüntüleri görüntüleyin

**IntelliTrace adım geri** otomatik olarak her kesme noktası ve hata ayıklama adım olay uygulamanızın bir anlık alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenizi ve uygulamanın durumunu geçmişte olduğu gibi görüntülemenizi sağlar. IntelliTrace adım geri önceki uygulama durumunu görmek istediğinizde zaman kazandırabilir, ancak hata ayıklama yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemiyorum.

Hata Ayıklama araç çubuğundaki **Geri Adım** ve **İleri Adım** düğmelerini kullanarak anlık görüntüleri gezebilir ve görüntüleyebilirsiniz. Bu düğmeler, **Tanılama Araçları** penceresindeki **Olaylar** sekmesinde görünen olaylarda gezinir.

![İleri adım ve İleri Düğmeler](../debugger/media/intellitrace-step-back-icons-description.png  "İleri adım ve İleri düğmeleri")

Daha fazla bilgi [için, IntelliTrace sayfasını kullanarak önceki uygulama durumlarını incele'ye](../debugger/view-historical-application-state.md) bakın.

## <a name="debug-performance-issues"></a>Hata ayıklama performans sorunları

Uygulamanız çok yavaş çalışıyorsa veya çok fazla bellek kullanıyorsa, uygulamanızı profil oluşturma araçlarıyla erkenden test etmeniz gerekebilir. CPU Kullanım aracı ve Memory Analyzer gibi profil oluşturma araçları hakkında daha fazla bilgi için [profil oluşturma araçlarına ilk bakışta](../profiling/profiling-feature-tour.md)bakın.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, birçok hata ayıklayıcı özelliğine hızlıca göz attınız. Kesme noktaları gibi bu özelliklerden birine daha ayrıntılı bir bakış isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Kesme noktalarını kullanmayı öğrenin](../debugger/using-breakpoints.md)
