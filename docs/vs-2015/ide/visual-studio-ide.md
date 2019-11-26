---
title: Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3780e0ee5cf6bffb1a749b17d868445fbda38b13
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296922"
---
# <a name="visual-studio-ide"></a>Visual Studio IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015 için kullanıcı Arabirimi tasarımı aracılığıyla planlama aşamasında den yazılım oluşturma, kodlama, test etme, hata ayıklama, kod kalitesini ve performansını analiz araçları, müşterileri ve kullanım telemetri toplama dağıtma paketidir. Bu araçlar, birlikte mümkün olan tüm Visual Studio tümleşik geliştirme ortamı (IDE üzerinden) sunulan olarak sorunsuz bir şekilde çalışmak üzere tasarlanmıştır.

Visual Studio, birçok türde uygulamalar, güç kurumlar ve veri merkezlerine büyük ve karmaşık sistemleri için basit mağazası uygulamaları ve mobil istemciler için oyunlar oluşturmak için kullanabilirsiniz. Oluşturabilirsiniz:

- Uygulama ve yalnızca Windows üzerinde çalışan oyunlar de Android ve iOS.

- ASP.NET, JQuery, AngularJS ve diğer popüler çerçeveleri dayalı Web siteleri ve web hizmetleri.

- Uygulamalar için Platform ve cihazlarda Azure, Office, Sharepoint, Hololens, Kinect ve nesnelerin interneti, yalnızca birkaç örnek adı için farklı.

- Oyunlar ve Xbox dahil olmak üzere, DirectX kullanarak Windows cihazları, çeşitli grafik kullanımı yoğun uygulamalar.

Varsayılan olarak Visual Studio için destek sağlar C#, C ve C++, JavaScript, F#ve Visual Basic. Visual Studio çalışır ve [Unity için Visual Studio Araçları](../cross-platform/visual-studio-tools-for-unity.md) uzantısı aracılığıyla Unity gibi üçüncü taraf uygulamalarla Apache Cordova ve [Apache Cordova için Visual Studio Araçları](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42)aracılığıyla iyi tümleşir. Visual Studio kendinize özel görevleri gerçekleştirmek özel araçlar oluşturarak genişletebilirsiniz.

Daha önce Visual Studio 'Yu kullanmadıysanız, Visual Studio öğreticileri ve yönergelerden [yararlanmamız](../ide/get-started-developing-with-visual-studio.md) sayesinde Başlarken hakkında temel bilgileri öğrenin.

Visual Studio 2015 ' deki yeni özellikler hakkında daha fazla bilgi edinmek istiyorsanız bkz. [Visual studio 2015 ' deki](../what-s-new-in-visual-studio-2015.md)yenilikler.

## <a name="visual-studio-setup"></a>Visual Studio Kurulumu
 Visual Studio 'nun hangi sürümünün [Visual Studio sürümlerinde](https://visualstudio.microsoft.com/vs/)sizin için uygun olduğunu bulabilirsiniz.

 Visual Studio 2015 ' i [Visual Studio indirmelerden](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx)indirerek yükleyebilirsiniz. Yükleme işlemi hakkında daha fazla bilgi edinmek istiyorsanız bkz. [Visual Studio 2015 yükleme](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>IDE temelleri
 Aşağıdaki görüntüde bir Proje Aç ile Visual Studio IDE gösterir ve proje dosyaları içinde gezinmek için Çözüm Gezgini penceresinde ve gezinme kaynağı için Takım Gezgini penceresi denetim ve iş öğesi izleme. Anılmaktadır başlık çubuğunda özellikleri aşağıda daha ayrıntılı olarak açıklanmıştır.

 ![Visual Studio IDE](../ide/media/visualstudioide.png "VisualStudioIDE")

### <a name="signing-in"></a>Oturum açma
 Visual Studio'yu ilk kez başlattığınızda, Microsoft hesabınızı veya iş kullanarak oturum açın ya da Okul hesabı. İmzalı birden çok cihazda gibi pencere düzenlerini, ayarlarınızı eşitlemek ve Azure abonelikleri ve Visual Studio Team Services gibi gerekebilir hizmetleri otomatik olarak bağlamak sağlar. Abonelik tabanlı bir lisansınız varsa, lisans belirteci güncel kalması için düzenli olarak Visual Studio'ya oturum gerekecektir. Bir ürün anahtarı lisansınız varsa, oturum açmasına gerek yoktur, ancak bunu yaparsanız bu nedenle Visual Studio Team Services hesaplarınızı Azure veya Office 365, Salesforce.com ile bağlanmak daha kullanışlı kolaylaştırır. Daha fazla bilgi için bkz. [Visual Studio 'Da oturum açma](../ide/signing-in-to-visual-studio.md).

 Birden çok Visual Studio Team Services hesapları, Azure hesapları veya MSDN aboneliği varsa, tek bir oturum açma ile tüm hesaplarınızda bunları ve kaynak ve hizmetlere bağlayabilirsiniz. Daha fazla bilgi için bkz. [birden çok kullanıcı hesabıyla çalışma](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Güncel kalma
 Bildirim simgesine sağ üst kısmındaki başlık çubuğunda ne zaman Visual Studio için güncelleştirmeler kullanılabilir veya ilgili tüm bileşenlerin yüklü olduğunu söyler. Kapat veya bu bildirimlere işlem seçebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio bildirimleri](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Öğeleri bulma ve Yardım alma
 Aşağıda gösterilen [Hızlı başlatma](../ide/reference/quick-launch-environment-options-dialog-box.md) penceresi, klavye kısayolunu veya menü konumunu bilmiyorsanız Visual Studio komutları, araçları, özellikleri, vb. bulmanın hızlı bir yoludur. Aradığınız ne yazmanız yeterlidir ve Hızlı Başlat, bir bağlantı için size sunar.

 ![' Yeni proje ' için hızlı başlatma sonuçları](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

 MSDN teknik belgeler için Microsoft web sitesi olur; MSDN bu sayfada şu anda okumakta olduğunuz! Visual Studio 'da **F1** ' e basarak etkin pencere için MSDN yardım sayfasına gidebilirsiniz. Ayrıca, geçerli giriş işareti konumunda API veya anahtar sözcüğü için MSDN yardım sayfasına gitmek üzere kod düzenleyicisinde **F1** 'e de gidebilirsiniz. Örneğin, bir C# dosyada, giriş işaretini bir `System.String` bildiriminin sonuna veya sonuna yerleştirin ve <xref:System.String>MSDN yardım sayfasına gitmek için **F1** tuşuna basın.

### <a name="giving-feedback"></a>Geri bildirim
 Dilediğiniz zaman bize geri bildirim Visual Studio sağlamak kolay bir işlemdir. **Hızlı Başlat** ' ın yanındaki başlık çubuğunda bulunan geri bildirim simgesine ve ardından **sorun bildir** veya **öneri sağlama**' ya tıklayın. Visual Studio 'nun yayın öncesi sürümlerinde **Bu ürüne** yönelik bir ücret de vardır. Bu açıklamalar arayın ve bunları ürünü iyileştirmek için kullanırız. Daha fazla bilgi için bkz. [bizimle Iletişim kurun](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>IDE’yi kişiselleştirme
 Pencere düzenini geliştirme stilinize uyacak şekilde özelleştirebilirsiniz. Yerleştirme, float veya herhangi bir zamanda herhangi bir pencereyi gizle ve düzenleyici tam ekran modunda da çalıştırabilirsiniz. Oluşturun ve yalnızca belirli bağlamlarda için gereksinim duyduğunuz pencerelerini Göster birden çok özel pencere düzenlerini kaydedin. Örneğin, Kod düzenleyicisinde gördüğünüz tüm böylece bir tam ekran düzeni oluşturabilirsiniz. Ve hata ayıklama ve ekip işlemleri alan farklı düzenler oluşturabilirsiniz. Daha fazla bilgi için bkz. [pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md).

 Visual Studio'yu diğer birçok şekilde özelleştirin ve zorlanmazsa ayarlarınızı birden fazla makinede çalışır. Daha fazla bilgi için bkz. [IDE’yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

 Neredeyse her şey için klavye kısayolları vardır ve de özelleştirebilirsiniz. Yeni kısayol oluşturmak için hızlı klavye iletişim kutusunu açmak için Başlat "Klavye" yazın. Burada, seçenekleri hakkında daha fazla bilgiye ihtiyacınız varsa, MSDN yardım sayfasına gitmek için F1 tuşuna basabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'Da varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Visual Studio Team Services ve Team Foundation Server'a bağlanma
 Visual Studio Team Services (VSTS) barındırma yazılım projeler ve takımlar etkinleştirme işbirliği için bulut tabanlı bir hizmettir. VSTS, Scrum ve CMMI Çevik Geliştirme yöntemleri yanı sıra, hem Git hem de Team Foundation kaynak denetimi sistemlerini destekler. Team Foundation sürüm denetimi (TFVC) izlemek için bir tek, merkezi sunucu deposu ve sürüm dosyalarını kullanır. Yerel değişiklikler her zaman diğer geliştiricilerin son değişiklikleri nereden merkez sunucuya iade edilir. Team Foundation Server (TFS) 2015, Visual Studio uygulama yaşam döngüsü yönetimi hub ' dir. Tek bir çözüm kullanarak katılmak için geliştirme işlemine dahil olan herkes sağlar. TFS, heterojen takımlara ve projelere, çok yönetimi için avantajlıdır.

 Ağınızda bir Team Foundation Server veya Visual Studio Team Services hesabı varsa, için Takım Gezgini penceresi bağlanın. Bu pencereden içine veya dışına kaynak denetimi kodunu kontrol edin, çalışma öğelerini yönetmek, derlemeler ve erişim takım odaları ve çalışma alanları başlatın. **Hızlı Başlat** ' dan veya ana menüdeki Takım Gezgini **Takım Gezgini Görünüm &#124;**  ' den veya **takımdan &#124; bağlantıları Yönet**' den açabilirsiniz.  Visual Studio Team Services hakkında daha fazla bilgi için bkz. [www.VisualStudio.com](https://www.visualstudio.com/). Team Foundation Server hakkında daha fazla bilgi için bkz. [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 Aşağıdaki görüntüde, VSTS'de barındırılan bir çözüm için Takım Gezgini bölmesinde gösterilmektedir:

 ![Visual Studio Takım Gezgini](../ide/media/vs2015-teamexplorer.png "VS2015_TeamExplorer")

## <a name="creating-solutions-and-projects"></a>Çözümler ve projeler oluşturma
 Tek tek kod dosyalarına gözatabilmeniz için Visual Studio 'Yu kullanabilirsiniz, ancak daha yaygın olarak bir *projede*çalışmanız gerekir. Visual Studio projesi, dosyalar ve uygulamalar (örneğin, bir .exe, DLL veya appx) için tek bir ikili yürütülebilir dosyasına derlenir kaynakları koleksiyonudur. Olmayan ASP.NET Web siteleri için herhangi bir yürütülebilir dosya oluşturulur ve projeyi görüntüler ve yalnızca HTML, JavaScript dosyaları içerir. Bazen birden çok ikili dosyaları veya yakından ilgili Web siteleri oluşturmanız gerekebilir, Visual Studio çözüm, birden çok proje veya Web siteleri içerebilir kavramını sahip olacaktır. Bir proje oluşturduğunuzda, aslında bir proje içinde-çözüm oluşturuyorsanız ve gerekirse daha fazla projeler bu çözüme daha sonra ekleyebilirsiniz. Örneğin, bir DLL projesi varsa, .exe projesinde yükleyen ve DLL kullanan bir çözüme ekleyebilirsiniz.

 *Proje şablonu* , belirli bir tür uygulamayı oluşturmak için hızlı bir şekilde ayarlamış olduğunuz bir önceden doldurulmuş kod dosyaları ve yapılandırma ayarları koleksiyonudur. Visual Studio aralarından seçim yapabileceğiniz birçok proje şablonları bulunur ve varsayılan şablonlarından hiçbiri işinize yaramazsa kendi oluşturabilirsiniz. Bir şablonla bir projesi oluşturduktan sonra sağlanan dosyaları veya eklediğiniz yeni dosyalar da, kendi kod yazmaya başlayabilirsiniz. Daha fazla bilgi için bkz. [çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md). ASP.NET uygulamaları için kullanılabilir proje şablonları ile yeni proje iletişim aşağıda gösterilmiştir.

 ![Visual Studio yeni proje Iletişim kutusu](../ide/media/vs2015-newprojectdialog.png "VS2015_NewProjectDialog")

## <a name="designing-the-user-interface"></a>Kullanıcı arabirimi tasarlama
 Bir tasarımcı, bir kullanıcı arabirimi, kod yazmaya gerek kalmadan oluşturmanıza olanak sağlayan sezgisel bir araçtır. Liste kutuları, takvimler ve düğmeler gibi kullanıcı arabirimi denetimlerini [araç](../ide/reference/toolbox.md) kutusu penceresinden pencere veya iletişim kutusunu temsil eden bir tasarım yüzeyine sürükleyebilirsiniz. Yeniden boyutlandırma ve herhangi bir kod yazmadan öğelerini yeniden düzenleyebilir. Tasarımcılar, bir kullanıcı arabirimi olan herhangi bir proje türü için dahil edilir.

 Projenizin bir XAML tabanlı kullanıcı arabirimi varsa varsayılan Tasarımcısı, Visual Studio ile sorunsuz çalışır bir Gelişmiş grafik aracı olan Visual Studio için Blend olur.

 ![Yüzeylerini](../ide/media/b5-artboard.png "b5_artboard")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Tasarım görünümü** Belgenizin görsel tasarımını görüntüler. Bu görünümde, çizime veya tasarım yüzeyinde nesneleri değiştirebilirsiniz.|
|![](../designers/media/b1-2.png "B1_2")|**Içerik Haritası** Seçilen bir nesne için şablon düzenlemesi modu, stil oluşturma modu ve nesne düzenlemesi kapsamı arasında hızlıca geçiş yapın.|
|![](../designers/media/b1-3.png "B1_3")|**Yakınlaştır** Tasarım yüzeyinde tasarım yüzeyini veya nesneleri yakınlaştırmak için kullanın.|
|![](../designers/media/b1-4.png "B1_4")|**Tasarım yüzeyi denetimleri** Yapışma seçeneklerini ayarlamak için bu denetimleri kullanın (**yaslama kılavuzunu göster**, **kılavuz çizgilerine yasla** ve **yama çizgilerine yaslamayı aç veya kapat**). Yaslamayı birbiriyle en fazla veya eşit aralıklı satırları tasarım yüzeyinde nesneleri hizalama için kullanışlıdır.|
|![](../designers/media/b1-5.png "B1_5")|**Kod Düzenleyicisi** XAML, C# C++ veya Visual Basic kodunuzu kod düzenleyicisinde el ile düzenleyin.|

 Daha fazla bilgi için bkz. [Visual Studio 'DA xaml tasarlama ve Visual Studio için Blend](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Gezinme, yazma ve kod anlama
 Geliştirici misiniz, düzenleyici penceresinde zamanınızın çoğunu burada büyük olasılıkla geçirir olur. Visual Studio için düzenleyicileri içerir C#, C++, Visual Basic, JavaScript, XML, HTML, CSS ve F#, üçüncü taraflar için birçok başka dile eklenti Düzenleyicileri (ve derleyiciler) sunar.

 **&#124; Dosya Aç &#124; dosya** ' ya tıklayarak metin düzenleyicisinde tek tek dosyaları düzenleyebilirsiniz. Açık bir proje dosyalarını düzenlemek için Çözüm Gezgini'ndeki dosya adını tıklayın. Kod renklendirilmiş ve Hızlı Başlat "Renk" yazarak renk düzenini kişiselleştirebilirsiniz. Aynı anda çok fazla metin düzenleyicisi sekmeli penceresi açık olabilir. Her pencere bağımsız olarak bölebilirsiniz. Metin Düzenleyici tam ekran modunda da çalıştırabilirsiniz.

 ![Kod düzenleyicisinde, Mesconsoleapp. cpp](../ide/media/c-ide-editorlinenumberswordwrapon.png "C++ IDE_EditorLineNumbersWordWrapOn")

 Metin düzenleyici, yüksek oranda (olmasını istiyorsanız) ile birçok üretkenlik yardımcı daha iyi daha hızlı kod yazmanızı etkileşimlidir. Dile göre farklı özellikler ve özelliklerini aç veya kapat için bunlardan (türü "Düzenleyicisinde" Hızlı Başlat) herhangi birini kullanmak zorunda değilsiniz: ortak üretkenlik özelliklerinden bazıları şunlardır:

1. Yeniden [düzenleme](../ide/refactoring-in-visual-studio.md) , değişkenlerin akıllı yeniden adlandırılması, seçilen kod satırlarının ayrı bir işleve taşınması, kodun başka konumlara taşınması, redsıralaması işlev parametreleri ve daha fazlası gibi işlemleri içerir.

2. *IntelliSense* , kodunuzun içindeki tür bilgilerini doğrudan düzenleyicide görüntüleyen ve bazı durumlarda sizin için küçük bir kod yazmak için kullanılan bir dizi popüler özellik için şemsiye bir terimdir. Bu temel belgeleri satır içi ayrı Yardım penceresinde tür bilgileri aramak zorunda kalmaktan kurtarır düzenleyicisinde gibidir. IntelliSense özellikleri dile göre değişiklik gösterir. Daha fazla bilgi için bkz [. C# Visual IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Visual Basic özel IntelliSense](../ide/visual-basic-specific-intellisense.md). Aşağıdaki çizimde, iş yerinde bazı IntelliSense özelliklerini gösterir:

    ![Visual Studio üye listesi](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

3. **Dalgalı çizgiler** , siz yazarken kodunuzda gerçek zamanlı olarak hata veya olası sorunlar olduğunu bildirir. Bu, derleme veya çalışma zamanı sırasında hatanın bulunmasını beklemeden onları hemen düzeltmenize olanak sağlar. Dalgalı çizgi gelin, hatayla ilgili ek bilgileri görürsünüz. Bir ampul, önerileri nasıl hatayı düzeltmek sol kenar boşluğunda de görünebilir. Daha fazla bilgi için bkz. [hafif bulbs ile hızlı eylemler gerçekleştirme](../ide/perform-quick-actions-with-light-bulbs.md).

    ![Fare üzerine gelindiğinde ampul](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

4. [Yer işaretleri](../ide/setting-bookmarks-in-code.md) , üzerinde etkin olarak çalıştığınız dosyalardaki belirli satırlara hızlı bir şekilde gezinmenizi sağlar.

5. Çağrı [hiyerarşisi](../ide/reference/call-hierarchy.md) penceresi, çağıran yöntemleri göstermek için metin düzenleyici bağlam menüsünde çağrılabilir ve giriş işareti altında yöntemi tarafından çağrılır.

6. **Kod lens** , kodunuzun, bağlantılı hataların, iş öğelerinizin, kod incelemelerinizin ve birim testlerinin, tüm Düzenleyiciden çıkmadan başvuruları ve değişiklikleri bulmanıza olanak sağlar. Daha fazla bilgi için bkz. [kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md).

7. **Tanıma göz atma** penceresinde geçerli bağlamınızdan uzaklaşmadan bir yöntem veya tür tanımı satır içi gösterilir. Bu pencereyi şimdi XAML için çok çalışır.

8. **Tanıma Git** bağlam menüsü seçeneği sizi doğrudan işlevin veya nesnenin tanımlandığı yere götürür. Başka gezinme komutları da Düzenleyicisi'nde sağ tıklayarak kullanılabilir.

9. [Nesne tarayıcısı](https://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470), ilgili bir araç, içerdikleri türleri ve bu türlerin hangi yöntem ve özellikleri içerdiğini görmek için sisteminizde .net veya Windows çalışma zamanı derlemelerini incelemenizi sağlar.

     ![System. Timer öğesini gösteren obect tarayıcısı](../ide/media/objectbrowser.png "ObjectBrowser")

   Düzen menüsü ve Görünüm menüsü öğelerin çoğu Kod Düzenleyicisi'nde şekilde ilgilidir. Düzenleyici hakkında daha fazla bilgi için bkz. [kod yazma](../ide/writing-code-in-the-code-and-text-editor.md) ve [kodunuzu düzenleme](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Derleme ve kod oluşturma

Bir proje oluşturmak için kaynak kodu derleyin ve yürütülebilir dosyayı oluşturmak için gerekli tüm adımları gerçekleştirmek anlamına gelir. Farklı dillerde farklı bir derleme işlem var ve normal Web siteleri hiçbir derleme yok. Proje türü ne olursa olsun, da yapı menüsündeki şu komutları standart konumudur. Derleme ve tek bir tuş vuruşu ile kodunuzu çalıştırmak için F5 tuşuna basın. Her derleyici IDE ile tamamen yapılandırılabilirdir. Derleme araç mı programınızda, simgeler ve kesme noktaları ve tek hata ayıklayıcı veya bir yayın yapısı Adımlama, ne, sonuçta müşterilere sağlayacak olan desteklemek üzere etkinleştirilmiş ek hata denetimi ile hata ayıklama sürümünü oluşturmak belirtmenize olanak sağlar. Bir proje özelliği sayfasında daha fazla derleme ve diğer birçok ayarlarını yapılandırabilirsiniz. Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve Özellikler'i seçin. Bu gibi durumlarda, yapılar da komut satırından çalıştırabilirsiniz.

Bir hata veya başarı iletileri de dahil olmak üzere, derleme çıktısı **Çıkış** penceresinde görüntülenir. **Hata listesi** , derleme hatalarıyla ilgili ayrıntılı bilgileri gösterir.

## <a name="debugging-your-code"></a>Kodunuzun hatalarını ayıklama
 Visual Studio'nun durumu resim hata ayıklayıcı yerel projenizde, Android veya Windows Phone yönelik olanlar gibi bir öykünücü veya uzak bir cihazda çalışan kodda hata ayıklamak sağlar. Aynı anda bir deyim kod adım adım ve belirtilen bir koşul true olduğunda, yalnızca isabet kesme noktalarını ayarlayabilir, Git ve çok iş parçacıklı uygulamalar aracılığıyla geçebilirsiniz gibi değişkenleri denetleyin. Kodunuzun bağlamı bırakmak zorunda kalmazsınız tüm kod düzenleyicisinde kendisini yapılandırılabilir.

 ![Kesme noktası ayarları Özeti penceresi](../ide/media/dbg-breakpoints-peekwindow.png "DBG_Breakpoints_PeekWindow")

 Hata ayıklayıcı kendisini görüntülemek ve yerel değişkenler, çağrı yığını ve diğer yönleri çalışma zamanı ortamı sağlayan birden çok windows sahiptir. Bu pencereleri **hata ayıklama** menüsünde bulabilirsiniz.

 [Komut penceresi](../ide/reference/immediate-window.md) bir ifadeyi yazıp sonucunu hemen görmenizi sağlar.

 [IntelliTrace](https://msdn.microsoft.com/629e9660-c59a-446b-8c30-290059158f61) penceresi, çalışan bir .net programındaki her yöntem çağrısını ve diğer olayları kaydeder ve bir sorunun nereden kaynaklandığını hızlı bir şekilde bulmanıza yardımcı olabilir.

 Daha fazla bilgi için bkz. [Visual Studio 'Da hata ayıklama](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Kodunuzu test etme
 Visual Studio birim testi çerçevesi için yönetilen kodu (.NET) ve bir yerel C++ içerir. Testleri, birim oluşturmak için testlerinizi yazın ve ardından bunları Test Gezgini penceresinden çalıştırın sadece bir Test projesi çözümünüze ekleyin. Daha fazla bilgi için bkz. [birim testi kodunuz](../test/unit-test-your-code.md).

 ![Birim test Gezgini](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

## <a name="analyzing-code-quality-and-performance"></a>Kod kalitesini ve performansını analiz etme
 Visual Studio statik ve çalışma zamanı analizi için güçlü araçlar içerir. Statik analiz araçları tasarımı, Genelleştirme, birlikte çalışabilirlik, performans, güvenlik ve diğer kategorilerden olası hataları belirlemenize yardımcı olur. Performans testi veya profil oluşturma, ölçme, programınızın nasıl çalıştığını içerir. Bu araçlara **Çözümle** menüsünden erişirsiniz. Daha fazla bilgi için bkz. [Visual Studio Ile kaliteyi artırma tanılama araçları](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Bulut hizmetlerine ve veritabanlarına bağlanma
 Visual Studio 'daki [Sunucu Gezgini](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) penceresinde, SQL Server örnekleri, Azure, Salesforce.com, Office 365 ve Web siteleri dahil olmak üzere kişiselleştirme hesabınızla (oturum açtığınız) yönetilen tüm hesaplara ait kaynaklar gösterilir.

 ![Sunucu Gezgini](../ide/media/vs2015-serverexplorer3.png "vs2015_ServerExplorer3")

 Visual Studio, veritabanlarını oluşturmanızı, hatalarını ayıklamanızı, bakımını ve yeniden düzenleme işlemlerini sağlayan [Microsoft SQL Server veri araçları](https://msdn.microsoft.com/data/tools.aspx) (SSDT) içerir. Bir veritabanı projesiyle veya doğrudan ile bir bağlı veritabanı örneği veya kapalı-şirket içinde çalışabilir.

 Visual Studio'da SQL Server Nesne Gezgini veritabanı nesnelerini SQL Server Management Studio'ya benzer bir görünümünü sunar. SQL Server Nesne Gezgini tablo verilerini düzenleme, Şema karşılaştırma ve doğru SQL Server Nesne Gezgini bağlam menülerini kullanarak sorgular yürütme light vergileri veritabanı yönetimi ve tasarım işler yapmasını sağlar. SSDT, ayrıca özel proje türleri ve SQL Server 2012 Analysis Services ve Reporting Services (önceki adıyla Business Intelligence Development Studio da bilinir) tümleştirme hizmetlerini iş zekası (BI) çözüm geliştirmeye yönelik araçlar içerir.

 ![SQL Server Nesne Gezgini](../ide/media/vs2015-sqlobjectexplorer.png "vs2015_SQLObjectExplorer")

## <a name="deploying-your-finished-application"></a>Tamamlanmış uygulamanızı dağıtma
 Uygulamanızı müşterilere dağıtmaya hazır olduğunda, Visual Studio için Windows Store, bir SharePoint sitesine veya InstallShield veya Windows Installer teknolojileriyle dağıtıyorsanız olup olmadığını, bunu yapmak için araçlar sağlar. Bu, tüm IDE erişilebilir. Daha fazla bilgi için bkz. [uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Mimari ve Modelleme Araçları (yalnızca Kurumsal)
 Tasarım ve uygulama modeli için Visual Studio mimari ve Modelleme Araçları'nı kullanabilirsiniz. Bu araçlar, kodun yapısını, davranış ve ilişkileri görselleştirmek için yardımcı olur. Geliştirme sürecinizin bir parçası olarak farklı uygulama yaşam döngüsü boyunca ayrıntı düzeylerinde modeller oluşturabilirsiniz. Gereksinimler, görevler, test çalışmalarını, hataları ve Team Foundation Server çalışma öğeleri ve geliştirme planınızı model öğelerini bağlantılandırarak Modellerinizi ile ilişkili diğer iş izleyebilirsiniz. Daha fazla bilgi için bkz. [uygulamanızı tasarlama ve modelleme](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Visual Studio SDK ile Visual Studio'yu genişletme
 Visual Studio genişletilebilir bir platformdur. Visual Studio IDE ile tümleşen bir özel aracı uzantısıdır. Üçüncü taraf uzantıları ekleyin veya kendinizinkini oluşturun. Daha fazla bilgi için bkz. [Visual Studio uzantıları geliştirme](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 [Visual Studio Kullanıcı deneyimi yönergeleri](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) , Visual Studio için uzantı yazma konusunda önemli bir başvurudur. Yeni özelliğinizi olmanızı sağlayacak diğer etkileşim desenleri Visual Studio ile sorunsuz şekilde tümleştirin ve bu platforma özgü yönergeleri iletişim tasarımı, yazı tiplerini, renkleri, simgeler, ortak denetimleri hakkında bilgi içerir.

## <a name="in-this-guide"></a>Bu kılavuzda

|||
|-|-|
|[Kullanıcı Hesapları ve Güncelleştirmeler](../ide/user-accounts-and-updates.md)|[IDE’yi Kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)|
|[Nasıl Yapılır: IDE'de Gezinme](../ide/how-to-move-around-in-the-visual-studio-ide.md)|[Visual Studio ile Geliştirmeye Başlama](../ide/get-started-developing-with-visual-studio.md)|
|[Visual Studio Uzantıları’nı bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)|[Çözümler ve Projeler](../ide/solutions-and-projects-in-visual-studio.md)|
|[Kod Yazma](../ide/writing-code-in-the-code-and-text-editor.md)|[Visual Studio’da hata ayıklama](../debugger/debugging-in-visual-studio.md)|
|[Profil Araçları](../profiling/profiling-tools.md)|[Kod Kalitesini Geliştirme](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|
|[Kullanıcı Arabirimleri Tasarlama](../designers/designing-user-interfaces.md)|[Mimariyi Çözümleme ve Mimarinin Modelini Oluşturma](../modeling/analyze-and-model-your-architecture.md)|
|[Derleme ve Oluşturma](../ide/compiling-and-building-in-visual-studio.md)|[Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma](../deployment/deploying-applications-services-and-components.md)|
|[Visual Studio IDE 64 Bit Desteği](../ide/visual-studio-ide-64-bit-support.md)|[Security](../ide/security-in-visual-studio.md)|
|[Visual Studio Örnekleri](../ide/visual-studio-samples.md)|[Microsoft Yardım Görüntüleyicisi](../ide/microsoft-help-viewer.md)|
|[Uygulamaları Genelleştirme ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)|[Kullanıcı arabirimi başvurusu](../ide/reference/general-user-interface-elements-visual-studio.md)|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio 2015 yükleniyor](../install/install-visual-studio-2015.md)
- [Kodunuzu düzenleniyor](https://www.visualstudio.com/features/ide-vs)
- [Visual Studio 2015’teki Yenilikler](../what-s-new-in-visual-studio-2015.md)
- [Visual Studio Projelerini Taşıma, Geçirme ve Yükseltme](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
- [Bizimle İletişime Geçin](../ide/talk-to-us.md)