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
ms.openlocfilehash: 52e0b8f87774b11b1750700d5bef19c5423824c4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667138"
---
# <a name="visual-studio-ide"></a>Visual Studio IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015, planlama aşamasından Kullanıcı arabirimi tasarımı, kodlama, test etme, hata ayıklama, kod kalitesini ve performansı çözümleme, müşterilere dağıtma ve kullanım için telemetri toplama araçları aracılığıyla yazılım oluşturmaya yönelik bir araç paketidir. Bu araçlar, birlikte çalışmak üzere tasarlanmıştır ve Visual Studio tümleşik geliştirme ortamı (IDE) aracılığıyla sunulur.

Visual Studio 'Yu kullanarak mobil istemciler için basit mağaza uygulamalarından ve oyunlarından, kuruluşların ve veri merkezlerinden oluşan büyük ve karmaşık sistemlere birçok uygulama türü oluşturabilirsiniz. Şunları oluşturabilirsiniz:

- Yalnızca Windows üzerinde değil, Android ve iOS için de çalışan uygulamalar ve Oyunlar.

- ASP.NET, JQuery, AngularJS ve diğer popüler çerçeveleri temel alan Web siteleri ve Web Hizmetleri.

- Platformlar ve cihazlara yönelik uygulamalar, Azure, Office, SharePoint, Hololens, Kinect ve Nesnelerin İnterneti farklı olarak yalnızca birkaç örnek adı verecek şekilde.

- DirectX kullanarak Xbox gibi çeşitli Windows cihazları için oyunlar ve grafik yoğun uygulamalar.

Visual Studio varsayılan olarak, C ve C# C++, JavaScript, F#ve Visual Basic için destek sağlar. Visual Studio çalışır ve [Unity için Visual Studio Araçları](../cross-platform/visual-studio-tools-for-unity.md) uzantısı aracılığıyla Unity gibi üçüncü taraf uygulamalarla Apache Cordova ve [Apache Cordova için Visual Studio Araçları](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42)aracılığıyla iyi tümleşir. Özelleşmiş görevleri gerçekleştiren özel araçlar oluşturarak Visual Studio 'Yu kendiniz genişletebilirsiniz.

Daha önce Visual Studio 'Yu kullanmadıysanız, Visual Studio öğreticileri ve yönergelerden [yararlanmamız](../ide/get-started-developing-with-visual-studio.md) sayesinde Başlarken hakkında temel bilgileri öğrenin.

Visual Studio 2015 ' deki yeni özellikler hakkında daha fazla bilgi edinmek istiyorsanız bkz. [Visual studio 2015 ' deki](../what-s-new-in-visual-studio-2015.md)yenilikler.

## <a name="visual-studio-setup"></a>Visual Studio Kurulumu
 Visual Studio 'nun hangi sürümünün [Visual Studio sürümlerinde](http://www.visualstudio.com/products/visual-studio-with-msdn-overview-vs)sizin için uygun olduğunu bulabilirsiniz.

 Visual Studio 2015 ' i [Visual Studio indirmelerden](http://www.visualstudio.com/downloads/download-visual-studio-vs.aspx)indirerek yükleyebilirsiniz. Yükleme işlemi hakkında daha fazla bilgi edinmek istiyorsanız bkz. [Visual Studio 2015 yükleme](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>IDE temelleri
 Aşağıdaki görüntüde, açık bir proje olan Visual Studio IDE ve proje dosyalarında gezinmek için Çözüm Gezgini penceresi ve kaynak denetimi ve iş öğesi izleme ile gezinmek için Takım Gezgini penceresi gösterilmektedir. Başlık çubuğundaki özellikler daha ayrıntılı olarak aşağıda açıklanmıştır.

 ![Visual Studio IDE](../ide/media/visualstudioide.png "VisualStudioIDE")

### <a name="signing-in"></a>Oturum açma
 Visual Studio 'Yu ilk kez başlattığınızda, Microsoft hesabı veya iş veya okul hesabınızı kullanarak oturum açabilirsiniz. Oturum açmanız, Windows düzenleri gibi ayarlarınızı birden çok cihazda eşitlemenize ve Azure abonelikleri ve Visual Studio Team Services gibi gereksinim duyduğunuz hizmetlere otomatik olarak bağlanmanızı sağlar. Abonelik tabanlı lisansınız varsa, lisans belirtecinizi yeni tutmak için Visual Studio 'da düzenli olarak oturum açmanız gerekir. Ürün anahtarı lisansınız varsa, oturum açmanız gerekmez, ancak bunu yapmanız, Azure, Office 365, Salesforce.com ile Visual Studio Team Services ve hesaplarınıza bağlanmayı daha kolay hale getirir. Daha fazla bilgi için bkz. [Visual Studio 'Da oturum açma](../ide/signing-in-to-visual-studio.md).

 Birden çok Visual Studio Team Services hesabınız, Azure hesaplarınız veya MSDN abonelikleriniz varsa, tek bir oturum açma işlemiyle bunları bağlayabilir ve tüm hesaplarınızdaki kaynaklara ve hizmetlere erişebilirsiniz. Daha fazla bilgi için bkz. [birden çok kullanıcı hesabıyla çalışma](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Güncel kalın
 Başlık çubuğunun sağ üst köşesindeki bildirim simgesi, Visual Studio veya yüklediğiniz ilgili herhangi bir bileşen için güncelleştirmeler ne zaman kullanılabilir olduğunu söyler. Bu bildirimleri kapatmak veya üzerinde işlem yapmak istediğinizi seçebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio bildirimleri](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Şeyleri bulma ve yardım alma
 Aşağıda gösterilen [Hızlı başlatma](../ide/reference/quick-launch-environment-options-dialog-box.md) penceresi, klavye kısayolunu veya menü konumunu bilmiyorsanız Visual Studio komutları, araçları, özellikleri, vb. bulmanın hızlı bir yoludur. Aradığınızı yazmanız yeterlidir ve hızlı başlatma size bir bağlantı sağlar.

 ![' Yeni proje ' için hızlı başlatma sonuçları](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

 MSDN, teknik belgeler için Microsoft Web sitesidir. Bu sayfayı MSDN 'de Şu anda okuyora sahipsiniz! Visual Studio 'da **F1** ' e basarak etkin pencere için MSDN yardım sayfasına gidebilirsiniz. Ayrıca, geçerli giriş işareti konumunda API veya anahtar sözcüğü için MSDN yardım sayfasına gitmek üzere kod düzenleyicisinde **F1** 'e de gidebilirsiniz. Örneğin, bir C# dosyada, giriş işaretini bir `System.String` bildiriminin sonuna veya sonuna yerleştirin ve <xref:System.String> MSDN yardım sayfasına gitmek için **F1** tuşuna basın.

### <a name="giving-feedback"></a>Geri bildirim verme
 Dilediğiniz zaman Visual Studio ile ilgili geri bildirimde bulunmak çok kolay. **Hızlı Başlat** ' ın yanındaki başlık çubuğunda bulunan geri bildirim simgesine ve ardından **sorun bildir** veya **öneri sağlama**' ya tıklayın. Visual Studio 'nun yayın öncesi sürümlerinde **Bu ürüne** yönelik bir ücret de vardır. Tüm bu açıklamalara göz atacağız ve ürünü geliştirmek için bunları kullanıyoruz. Daha fazla bilgi için bkz. [bizimle Iletişim kurun](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>IDE’yi kişiselleştirme
 Pencere düzenini geliştirme stilinize uyacak şekilde özelleştirebilirsiniz. Dilediğiniz zaman herhangi bir pencereyi sabitleyebilir, kaydırılabilir veya gizleyebilirsiniz ve ayrıca düzenleyiciyi tam ekran modunda çalıştırabilirsiniz. Yalnızca belirli bağlamlar için gereken pencereleri gösteren birden çok özel pencere düzeni oluşturabilir ve kaydedebilirsiniz. Örneğin, tüm gördüğünüz kod Düzenleyicisi olmak üzere tam ekran düzeni oluşturabilirsiniz. Diğer bir deyişle, hata ayıklama ve takım işlemleri için farklı düzenler oluşturabilirsiniz. Daha fazla bilgi için bkz. [pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md).

 Visual Studio 'Yu birçok farklı şekilde özelleştirebilir ve birden çok makine üzerinde çalışmanız durumunda ayarlarınızı dolaşımda bulabilirsiniz. Daha fazla bilgi için bkz. [IDE’yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

 Neredeyse her şey için klavye kısayolları vardır ve bunları da özelleştirebilirsiniz. Yeni kısayollar oluşturmak için hızlı başlatma ' ya "klavye" yazın ve klavye iletişim kutusunu açın. Buradan, seçenekler hakkında daha fazla bilgiye ihtiyacınız varsa, F1 tuşuna basarak MSDN yardım sayfasına gidebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'Da varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Visual Studio Team Services ve Team Foundation Server bağlanma
 Visual Studio Team Services (VSTS), yazılım projelerini barındırmak ve ekiplerde işbirliğini etkinleştirmek için bulut tabanlı bir hizmettir. VSTS hem git hem de Team Foundation kaynak denetimi sistemlerini, hem de Scrum, CMMı ve çevik geliştirme yöntemlerini destekler. Team Foundation Sürüm Denetimi (TFVC), dosyaları izlemek ve sürümde tek bir merkezi sunucu deposu kullanır. Yerel değişiklikler her zaman, diğer geliştiricilerin en son değişiklikleri aldığı merkezi sunucuya iade edilir. Team Foundation Server (TFS) 2015, Visual Studio için uygulama yaşam döngüsü yönetim merkezdir. Geliştirme işlemiyle ilgili herkesin tek bir çözüm kullanarak katılmasını sağlar. TFS, heterojen takımları ve projeleri yönetmek için yararlıdır.

 Ağınızda bir Visual Studio Team Services hesabınız veya bir Team Foundation Server varsa, Takım Gezgini penceresinden bu sunucuya bağlanırsınız. Bu pencereden, kaynak denetimi içine veya dışına kodu denetleyebilir, iş öğelerini yönetebilir, yapıları başlatabilir ve ekip odalarına ve çalışma alanlarına erişebilirsiniz. **Hızlı Başlat** ' dan veya ana menüdeki Takım Gezgini **Takım Gezgini Görünüm &#124;**  ' den veya **takımdan &#124; bağlantıları Yönet**' den açabilirsiniz.  Visual Studio Team Services hakkında daha fazla bilgi için bkz. [www.VisualStudio.com](https://www.visualstudio.com/). Team Foundation Server hakkında daha fazla bilgi için bkz. [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 Aşağıdaki görüntüde VSTS 'de barındırılan bir çözüm için Takım Gezgini bölmesi gösterilmektedir:

 ![Visual Studio Takım Gezgini](../ide/media/vs2015-teamexplorer.png "VS2015_TeamExplorer")

## <a name="creating-solutions-and-projects"></a>Çözümler ve projeler oluşturma
 Tek tek kod dosyalarına gözatabilmeniz için Visual Studio 'Yu kullanabilirsiniz, ancak daha yaygın olarak bir *projede*çalışmanız gerekir. Visual Studio projesi, uygulamalar için tek bir ikili yürütülebilir dosyaya derlenen bir dosya ve kaynak koleksiyonudur (örneğin, bir. exe, DLL veya appx). Non-ASP.NET Web siteleri için çalıştırılabilir üretilmez ve proje yalnızca HTML, JavaScript dosyaları ve görüntüleri içerir. Bazen daha yakından ilgili olan birden çok ikili dosya veya Web sitesi oluşturmanız gerekebileceğinden, Visual Studio birden fazla proje veya Web sitesi içerebilen çözüm kavramını içerir. Bir proje oluşturduğunuzda, gerçekten bir proje çözümü oluşturursunuz ve daha sonra gerekirse bu çözüme daha fazla proje ekleyebilirsiniz. Örneğin, bir DLL projeniz varsa, DLL 'yi yükleyen ve tüketen çözüme bir. exe projesi ekleyebilirsiniz.

 *Proje şablonu* , belirli bir tür uygulamayı oluşturmak için hızlı bir şekilde ayarlamış olduğunuz bir önceden doldurulmuş kod dosyaları ve yapılandırma ayarları koleksiyonudur. Visual Studio, aralarından seçim yapabileceğiniz birçok proje şablonu ile birlikte gelir ve varsayılan şablonların hiçbiri sizin için çalışmazsa, kendi uygulamanızı oluşturabilirsiniz. Şablon içeren bir proje oluşturduktan sonra, bu kodda, belirtilen dosyalarda veya eklediğiniz yeni dosyalarda kendi kodunuzu yazmaya başlayabilirsiniz. Daha fazla bilgi için bkz. [çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md). Aşağıdaki çizimde, ASP.NET uygulamaları için kullanılabilen proje şablonlarıyla yeni proje iletişim kutusu gösterilmektedir.

 ![Visual Studio yeni proje Iletişim kutusu](../ide/media/vs2015-newprojectdialog.png "VS2015_NewProjectDialog")

## <a name="designing-the-user-interface"></a>Kullanıcı arabirimini tasarlama
 Tasarımcı, kod yazmadan bir kullanıcı arabirimi oluşturmanıza olanak sağlayan sezgisel bir araçtır. Liste kutuları, takvimler ve düğmeler gibi kullanıcı arabirimi denetimlerini [araç](../ide/reference/toolbox.md) kutusu penceresinden pencere veya iletişim kutusunu temsil eden bir tasarım yüzeyine sürükleyebilirsiniz. Herhangi bir kod yazmadan öğeleri yeniden boyutlandırabilir ve yeniden düzenleyebilirsiniz. Tasarımcılar, Kullanıcı arabirimine sahip tüm proje türleri için dahil edilmiştir.

 Projenizde XAML tabanlı bir kullanıcı arabirimi varsa, varsayılan Tasarımcı Visual Studio için Blend, Visual Studio ile sorunsuz bir şekilde çalışacak gelişmiş bir grafik aracıdır.

 ![Yüzeylerini](../ide/media/b5-artboard.png "b5_artboard")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Tasarım görünümü** Belgenizin görsel tasarımını görüntüler. Bu görünümde, Tasarım yüzeyinde nesne çizebilir veya nesneleri değiştirebilirsiniz.|
|![](../designers/media/b1-2.png "B1_2")|**Içerik Haritası** Seçilen bir nesne için şablon düzenlemesi modu, stil oluşturma modu ve nesne düzenlemesi kapsamı arasında hızlıca geçiş yapın.|
|![](../designers/media/b1-3.png "B1_3")|**Yakınlaştır** Tasarım yüzeyinde tasarım yüzeyini veya nesneleri yakınlaştırmak için kullanın.|
|![](../designers/media/b1-4.png "B1_4")|**Tasarım yüzeyi denetimleri** Yapışma seçeneklerini ayarlamak için bu denetimleri kullanın (**yaslama kılavuzunu göster**, **kılavuz çizgilerine yasla** ve **yama çizgilerine yaslamayı aç veya kapat**). Yaslama, nesneleri birbirlerine veya tasarım yüzeyinde eşit aralıklı satırlara göre hizalamak için faydalıdır.|
|![](../designers/media/b1-5.png "B1_5")|**Kod Düzenleyicisi** XAML, C# C++ veya Visual Basic kodunuzu kod düzenleyicisinde el ile düzenleyin.|

 Daha fazla bilgi için bkz. [Visual Studio 'DA xaml tasarlama ve Visual Studio için Blend](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Kod yazma, gezinme ve anlama
 Bir geliştiricisiyseniz, en büyük olasılıkla zaman harcamanız gereken düzenleyici pencere olur. Visual Studio C#, diğer birçok dil C++için eklenti Düzenleyicileri (ve derleyiciler) sunan,, Visual Basic F#, JavaScript, XML, HTML, CSS ve ve üçüncü tarafların düzenleyicilerini içerir.

 **&#124; Dosya Aç &#124; dosya** ' ya tıklayarak metin düzenleyicisinde tek tek dosyaları düzenleyebilirsiniz. Açık bir projedeki dosyaları düzenlemek için Çözüm Gezgini dosya adına tıklayın. Kod renklendirilir ve hızlı başlatma bölümünde "renkler" yazarak renk şemasını kişiselleştirebilirsiniz. Aynı anda çok sayıda metin Düzenleyicisi sekmeli pencere açabilirsiniz. Her pencereyi bağımsız olarak ayırabilirsiniz. Ayrıca, metin düzenleyiciyi tam ekran modunda da çalıştırabilirsiniz.

 ![Kod düzenleyicisinde, Mesconsoleapp. cpp](../ide/media/c-ide-editorlinenumberswordwrapon.png "C + + IDE_EditorLineNumbersWordWrapOn")

 Daha iyi kod daha hızlı yazmanıza yardımcı olan çok sayıda üretkenlik özelliği ile metin Düzenleyicisi oldukça etkileşimli (isterseniz istiyorsanız). Özellikler dile göre farklılık gösterir ve bunlardan herhangi birini kullanmanız gerekmez (hızlı başlatma bölümünde "Düzenleyici" yazın) özellikleri açmak veya kapatmak için: bazı yaygın üretkenlik özelliklerinden bazıları şunlardır:

1. Yeniden [düzenleme](../ide/refactoring-in-visual-studio.md) , değişkenlerin akıllı yeniden adlandırılması, seçilen kod satırlarının ayrı bir işleve taşınması, kodun başka konumlara taşınması, redsıralaması işlev parametreleri ve daha fazlası gibi işlemleri içerir.

2. *IntelliSense* , kodunuzun içindeki tür bilgilerini doğrudan düzenleyicide görüntüleyen ve bazı durumlarda sizin için küçük bir kod yazmak için kullanılan bir dizi popüler özellik için şemsiye bir terimdir. Temel belgeleri düzenleyicide satır içi olarak, tür bilgilerini ayrı bir Yardım penceresinde aramak zorunda kalmanızı sağlar. IntelliSense özellikleri dile göre farklılık gösterir. Daha fazla bilgi için bkz [. C# Visual IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Visual Basic özel IntelliSense](../ide/visual-basic-specific-intellisense.md). Aşağıdaki çizimde, bazı IntelliSense özellikleri iş başında gösterilmektedir:

    ![Visual Studio üye listesi](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

3. **Dalgalı çizgiler** , siz yazarken kodunuzda gerçek zamanlı olarak hata veya olası sorunlar olduğunu bildirir. Bu, derleme veya çalışma zamanı sırasında hatanın bulunmasını beklemeden onları hemen düzeltmenize olanak sağlar. Dalgalı çizgi üzerine geldiğinizde hata hakkında ek bilgi görürsünüz. Ayrıca, sol kenar boşluğunda hatanın nasıl düzeltileceğini gösteren öneriler içeren bir ampul de görünebilir. Daha fazla bilgi için bkz. [hafif bulbs ile hızlı eylemler gerçekleştirme](../ide/perform-quick-actions-with-light-bulbs.md).

    ![Fare üzerine gelindiğinde ampul](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

4. [Yer işaretleri](../ide/setting-bookmarks-in-code.md) , üzerinde etkin olarak çalıştığınız dosyalardaki belirli satırlara hızlı bir şekilde gezinmenizi sağlar.

5. Çağrı [hiyerarşisi](../ide/reference/call-hierarchy.md) penceresi, çağıran yöntemleri göstermek için metin düzenleyici bağlam menüsünde çağrılabilir ve giriş işareti altında yöntemi tarafından çağrılır.

6. **Kod lens** , kodunuzun, bağlantılı hataların, iş öğelerinizin, kod incelemelerinizin ve birim testlerinin, tüm Düzenleyiciden çıkmadan başvuruları ve değişiklikleri bulmanıza olanak sağlar. Daha fazla bilgi için bkz. [kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md).

7. **Tanıma göz atma** penceresinde geçerli bağlamınızdan uzaklaşmadan bir yöntem veya tür tanımı satır içi gösterilir. Bu pencere artık XAML için de geçerlidir.

8. **Tanıma Git** bağlam menüsü seçeneği sizi doğrudan işlevin veya nesnenin tanımlandığı yere götürür. Diğer Gezinti komutları da düzenleyiciye sağ tıklanarak kullanılabilir.

9. [Nesne tarayıcısı](https://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470), ilgili bir araç, içerdikleri türleri ve bu türlerin hangi yöntem ve özellikleri içerdiğini görmek için sisteminizde .net veya Windows çalışma zamanı derlemelerini incelemenizi sağlar.

     ![System. Timer öğesini gösteren obect tarayıcısı](../ide/media/objectbrowser.png "ObjectBrowser")

   Düzen menüsü ve Görünüm menüsündeki öğelerin çoğu, kod düzenleyiciyle bir şekilde ilgilidir. Düzenleyici hakkında daha fazla bilgi için bkz. [kod yazma](../ide/writing-code-in-the-code-and-text-editor.md) ve [kodunuzu düzenleme](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Kodunuzu derleme ve oluşturma

Bir proje oluşturmak için kaynak kodu derlemek ve çalıştırılabilir dosyayı oluşturmak için gereken adımları gerçekleştirmek anlamına gelir. Farklı diller farklı derleme işlemlerine sahiptir ve normal web siteleri hiç derlenmezsiniz. Proje türünden bağımsız olarak, derleme menüsü bu komutların standart konumudur. Kodunuzu tek bir tuş vuruşu ile derlemek ve çalıştırmak için F5 'e basın. Her derleyici IDE aracılığıyla tamamen yapılandırılabilir. Derleme araç çubuğu, programınızın bir hata ayıklama sürümü oluşturulup oluşturulmayacağını belirtmenize olanak sağlar. bu sayede, hata ayıklayıcıda kesme noktaları ve tek adımlamayı desteklemek için etkin ve son olarak müşterilere verdiğiniz bir yayın derlemesi. Bir projenin özellik sayfasında daha fazla yapı ayarı ve diğer birçok ayarı yapılandırabilirsiniz. Çözüm Gezgini ' de proje düğümüne sağ tıklayın ve Özellikler ' i seçin. Ayrıca, komut satırından yapıları çalıştırabilirsiniz.

Bir hata veya başarı iletileri de dahil olmak üzere, derleme çıktısı **Çıkış** penceresinde görüntülenir. **Hata listesi** , derleme hatalarıyla ilgili ayrıntılı bilgileri gösterir.

## <a name="debugging-your-code"></a>Kodunuzda hata ayıklama
 Visual Studio 'nun son teknoloji hata ayıklayıcı, yerel projenizde, uzak bir cihazda veya Android veya Windows Phone gibi bir Öykünücüde çalışan kodun hatalarını ayıklamanıza olanak sağlar. Tek seferde kod bir bildirimde ilerleyebileceğiniz gibi değişkenleri inceleyerek, çok iş parçacıklı uygulamalarda ilerleyebileceğiniz gibi, yalnızca belirtilen bir koşul doğru olduğunda yalnızca isabet kesme noktaları da ayarlayabilirsiniz. Kodunuzun bağlamından çıkmak zorunda kalmazsınız, bu sayede tüm bunlar kod Düzenleyicisi 'nde yapılandırılabilir.

 ![Kesme noktası ayarları Özeti penceresi](../ide/media/dbg-breakpoints-peekwindow.png "DBG_Breakpoints_PeekWindow")

 Hata ayıklayıcının kendisinde yerel değişkenleri, çağrı yığınını ve çalışma zamanı ortamının diğer yönlerini görüntülemenize ve yönetmenize olanak tanıyan birden çok pencere vardır. Bu pencereleri **hata ayıklama** menüsünde bulabilirsiniz.

 [Komut penceresi](../ide/reference/immediate-window.md) bir ifadeyi yazıp sonucunu hemen görmenizi sağlar.

 [IntelliTrace](https://msdn.microsoft.com/629e9660-c59a-446b-8c30-290059158f61) penceresi, çalışan bir .net programındaki her yöntem çağrısını ve diğer olayları kaydeder ve bir sorunun nereden kaynaklandığını hızlı bir şekilde bulmanıza yardımcı olabilir.

 Daha fazla bilgi için bkz. [Visual Studio 'Da hata ayıklama](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Kodunuzu test etme
 Visual Studio, yönetilen kod (.NET) ve diğeri yerel C++için bir birim testi çerçevesi içerir. Birim testleri oluşturmak için çözümünüze bir test projesi ekleyin, testlerinizi yazın ve ardından Test Gezgini penceresinden çalıştırın. Daha fazla bilgi için bkz. [birim testi kodunuz](../test/unit-test-your-code.md).

 ![Birim test Gezgini](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

## <a name="analyzing-code-quality-and-performance"></a>Kod kalitesini ve performansını çözümleme
 Visual Studio, statik ve çalışma zamanı analizi için güçlü araçlar içerir. Statik analiz araçları tasarım, Genelleştirme, birlikte çalışabilirlik, performans, güvenlik ve diğer kategorilerdeki olası hataları belirlemenize yardımcı olur. Performans testi veya profil oluşturma, programınızın nasıl çalıştığını ölçmeye içerir. Bu araçlara **Çözümle** menüsünden erişirsiniz. Daha fazla bilgi için bkz. [Visual Studio Ile kaliteyi artırma tanılama araçları](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Cloud Services ve veritabanlarına bağlanma
 Visual Studio 'daki [Sunucu Gezgini](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) penceresinde, SQL Server örnekleri, Azure, Salesforce.com, Office 365 ve Web siteleri dahil olmak üzere kişiselleştirme hesabınızla (oturum açtığınız) yönetilen tüm hesaplara ait kaynaklar gösterilir.

 ![Sunucu Gezgini](../ide/media/vs2015-serverexplorer3.png "vs2015_ServerExplorer3")

 Visual Studio, veritabanlarını oluşturmanızı, hatalarını ayıklamanızı, bakımını ve yeniden düzenleme işlemlerini sağlayan [Microsoft SQL Server veri araçları](https://msdn.microsoft.com/data/tools.aspx) (SSDT) içerir. Bir veritabanı projesiyle veya doğrudan bağlı bir veritabanı örneğiyle ya da şirket içi olarak çalışabilirsiniz.

 Visual Studio 'daki SQL Server Nesne Gezgini, SQL Server Management Studio benzer veritabanı nesnelerinizin bir görünümünü sunar. SQL Server Nesne Gezgini, tablo verilerini Düzenle, şemaları karşılaştırmak ve SQL Server Nesne Gezgini bağlamsal menüleri kullanarak sorguları yürütmek dahil olmak üzere açık vergi veritabanı yönetimi ve tasarım işi yapmanıza olanak sağlar. SSDT Ayrıca, SQL Server 2012 Analysis Services, Reporting Services ve Integration Services Iş zekası (BI) çözümlerini (eski adıyla Business Intelligence Development Studio) geliştirmeye yönelik özel proje türleri ve araçları içerir.

 ![SQL Server Nesne Gezgini](../ide/media/vs2015-sqlobjectexplorer.png "vs2015_SQLObjectExplorer")

## <a name="deploying-your-finished-application"></a>Tamamlanmış uygulamanızı dağıtma
 Uygulamanız müşterilere dağıtmaya hazırsanız, Visual Studio, Windows Mağazası 'na, SharePoint sitesine veya InstallShield veya Windows Installer teknolojilerine dağıtmanıza bakılmaksızın bunu yapmak için araçlar sağlar. Tamamen IDE aracılığıyla erişilebilir. Daha fazla bilgi için bkz. [uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Mimari ve modelleme araçları (yalnızca Kurumsal)
 Uygulamanızı tasarlamak ve modellemek için Visual Studio mimarisi ve modelleme araçlarını kullanabilirsiniz. Bu araçlar kodun yapısını, davranışını ve ilişkilerini görselleştirmenize yardımcı olur. Geliştirme sürecinizin bir parçası olarak uygulama yaşam döngüsü boyunca farklı ayrıntı düzeylerinde modeller oluşturabilirsiniz. Model öğelerini Team Foundation Server iş öğelerine ve geliştirme planınıza bağlayarak modelleriniz ile ilişkili gereksinimleri, görevleri, test çalışmalarını, hataları ve diğer işleri izleyebilirsiniz. Daha fazla bilgi için bkz. [uygulamanızı tasarlama ve modelleme](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Visual Studio SDK aracılığıyla Visual Studio 'Yu genişletme
 Visual Studio, genişletilebilir bir platformdur. Visual Studio uzantısı, IDE ile tümleştirilen özel bir araçtır. Üçüncü taraf uzantıları ekleyebilir veya kendinizinkini oluşturabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio uzantıları geliştirme](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 [Visual Studio Kullanıcı deneyimi yönergeleri](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) , Visual Studio için uzantı yazma konusunda önemli bir başvurudur. Platforma özgü bu yönergeler iletişim kutusu tasarımı, yazı tipleri, renkler, simgeler, ortak denetimler ve yeni özelliğinizi Visual Studio ile sorunsuz bir şekilde tümleşecek diğer etkileşim desenleriyle ilgili bilgiler içerir.

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