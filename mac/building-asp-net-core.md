---
title: ASP.NET Core uygulamaları
description: Bu makalede, uygulamalarla uygulama oluşturma ve ASP.NET Core oluşturma Mac için Visual Studio.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.topic: how-to
ms.openlocfilehash: 22dfa4a33005afd64be54828f3b49c45244779d2
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964762"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Mac için Visual Studio’da ASP.NET Core uygulamaları oluşturma

ASP.NET Core web uygulamaları ve hizmetleri, IoT uygulamaları ve mobil arka uçlar gibi modern bulut tabanlı İnternet'e bağlı uygulamalar için açık kaynak ve platformlar arası bir çerçevedir. ASP.NET Core uygulamaları [.NET Core'da](https://www.microsoft.com/net/core/platform) veya .NET Framework çalıştırabilirsiniz. Buluta dağıtılan veya şirket içinde çalıştırılan uygulamalar için iyileştirilmiş bir geliştirme çerçevesi sağlamak için mimari olarak hazırlandı. Minimum ek yüke sahip modüler bileşenlerden oluşur, bu nedenle çözümlerinizi oluştururken esnekliği korur. ASP.NET Core, Mac ve Linux üzerinde platformlar arası Windows geliştirebilir ve çalıştırabilirsiniz. ASP.NET Core açık kaynaktır ve [GitHub.](https://github.com/aspnet/home)

Bu laboratuvarda, Mac için Visual Studio ile bir ASP.NET Core uygulaması Mac için Visual Studio.

## <a name="objectives"></a>Hedefler

> [!div class="checklist"]
> * ASP.NET Core web uygulaması oluşturma
> * ASP.NET Core, yapılandırma ve ara yazılım modelini keşfetme
> * Web uygulamasında ASP.NET Core ayıklama

## <a name="prerequisites"></a>Önkoşullar

- [Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Hedef Kitle

Bu laboratuvar, C# hakkında bilgi sahibi olan geliştiricilere yöneliktir ancak derin deneyim gerekli değildir.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>1. Görev: Yeni bir ASP.NET Core oluşturma

1. **Mac için Visual Studio.**

2. Yeni **Çözüm >'ı seçin.**

3. **.NET Core uygulama > kategorisini** ve **ASP.NET Core Web Uygulaması (C#) şablonunu** seçin. **İleri**’ye tıklayın.

    ![Yeni projeniz için Bir Web Uygulaması şablonunun nasıl seçilenesini gösteren ekran görüntüsü.](media/netcore-image1.png)

4. Projeyi oluşturmak için **"CoreLab"** adını girin ve **Oluştur'a** tıklayın. Tamamlanması biraz zaman alır.

    ![Web Uygulaması yapılandırmasının, Project Ekleme'nin ekran görüntüsü.](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>2. Görev: Çözümü turlama

1. Varsayılan şablon, CoreLab adlı tek bir ASP.NET Core çözümü **oluşturur.** Proje düğümünü genişletarak içeriğini ortaya çıkarabilirsiniz.

    ![Klasörler ve dosyalar dahil olmak üzere içeriğini görmek için seçilen çözüm projesi düğümünün ekran görüntüsü.](media/netcore-image3.png)

2. Bu proje, veriler (modeller), sunu (görünümler) ve işlevler (denetleyiciler) arasındaki sorumlulukların net bir şekilde bölünmesini sağlamak için model-görünüm-denetleyici (MVC) paradigmasını izler. Controllers **klasöründen HomeController.cs** **dosyasını** açın.

    ![HomeController adlı bir C# sınıfının seçili olduğu çözüm projesinin ekran görüntüsü.](media/netcore-image4.png)

3. **HomeController** class-by kuralı, /Home ile baş alan tüm gelen **istekleri işlemeye devam ediyor.** **Index yöntemi** dizinin köküne (gibi) istekleri, diğer yöntemler ise istekleri kuralına göre adlandırılmış yollarına işler; `http://site.com/Home` örneğin, **about()** işleme istekleri `http://site.com/Home/About` için . Elbette bunların hepsi yapılandırılabilir. **HomeController'ın** yeni projede varsayılan denetleyici olması, bu nedenle sitenin köküne ( ) yönelik isteklerin veya istekleri gibi `http://site.com` **HomeController'ın** **Index()** dizininden geçilmesidir. `http://site.com/Home` `http://site.com/Home/Index`

    ![HomeController adlı bir C# sınıfının ekran görüntüsü.](media/netcore-image5.png)

4. Projede ayrıca, her **denetleyiciyle** eşlene diğer klasörleri içeren bir Görünümler klasörü de vardır (paylaşılan görünümler için **de bir klasör).** Örneğin, **/Home/About** yolu için görünüm CSHTML dosyası (HTML uzantısı) **Views/Home/About.cshtml yolunda olabilir.** Bu dosyayı açın.

    ![Hakkında adlı C S H T M L dosyasının seçili olduğu çözüm projesinin ekran görüntüsü.](media/netcore-image6.png)

5. Bu CSHTML dosyası, standart Razor söz dizimi ve satır içi C# birleşimine göre HTML işlemek için Razor söz dizimi dosyasını kullanır. Bu konuda daha fazla bilgi için çevrimiçi [belgelerde bulabilirsiniz.](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)

    ![C S H T M L dosyasının bir bölümünü gösteren ekran Razor söz dizimi.](media/netcore-image7.png)

6. Çözüm ayrıca web **siteniz için** kök olacak bir wwwroot klasörü içerir. CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini, doğrudan site dağıtıldığında bunları istediğiniz yollara koyabilirsiniz.

    ![w w root klasörünün seçili olduğu çözümün ekran görüntüsü.](media/netcore-image8.png)

7. Ayrıca projeyi, paketlerini ve uygulamayı çalışma zamanında yönetmeye hizmet eden çeşitli yapılandırma dosyaları da vardır. Örneğin, varsayılan uygulama yapılandırması [üzerinde](/aspnet/core/fundamentals/configuration)appsettings.js **depolanır.** Dosyanın üzerinde appsettings.jsiç içe geçmiş dosya **appsettings.Development.jsdosyasıdır.** Burada, bu ayarların bir/hepsini ortam bazında geçersiz kılabilirsiniz. Mac için Visual Studio, daha sık erişmesi gereken dosyaların ön planda Visual Studio için Windows ile aynı mantığı kullanarak dosyaları bu şekilde iç içe yerleştirmeyi sağlar. 

    ![JSON dosyasının seçili olduğu ayrıntı görünümünü gösteren ekran görüntüsü.](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>3. Görev: Uygulamanın nasıl barındırıldıklarını anlama

1. **'Çözüm Gezgini** **Program.cs'yi açın.** Bu, uygulamanızı çalıştıracak önyükleyicidir.

    ![Program adlı C# kaynak dosyasının seçili olduğu çözümün ekran görüntüsü.](media/netcore-image10.png)

2. Burada yalnızca iki kod satırı vardır ancak önemli ölçüdedir. Şimdi bunları parçalı olarak bakalım. İlk olarak yeni bir **WebHostBuilder** oluşturulur. ASP.NET Core uygulamaları, yürütülecek bir konak gerektirir. Bir konak, özellik ve hizmet koleksiyonlarını ve bir Start yöntemini ortaya çıkaran **IWebHost** arabirimini **uygulamalı.** Konak genellikle bir **WebHost** örneği oluşturan ve döndüren **bir WebHostBuilder** örneği kullanılarak oluşturulur. **WebHost,** istekleri işecek sunucuya başvurur.

    ![WebHostBuilder türüne sahip host adlı bir değişkeni başlatan deyimiyle birlikte C# Main yönteminin ekran görüntüsü.](media/netcore-image11.png)

3. **WebHostBuilder,** uygulama için sunucuyu önyüklerken konak oluşturmaktan sorumludur, ancak bunu uygulayan bir sunucu sağlamanız **`IServer`** gerekir. Varsayılan olarak, bu **[kestrel,](/aspnet/core/fundamentals/servers/kestrel)** platformlar arası bir I/O ASP.NET Core **libuv'u** temel alan platformlar arası bir web sunucusudur.

    ![Sunucuyu UseKestrel yöntemiyle ayarlayan konak değişkenlerini vurgulayan C# Main yönteminin ekran görüntüsü.](media/netcore-image12.png)

4. Ardından sunucunun içerik kökü ayarlanır. Bu, MVC Görünüm dosyaları gibi içerik dosyalarını nerede araması olduğunu belirler. Varsayılan içerik kökü, uygulamanın çalıştır olduğu klasördür.

    ![Sunucu için içerik kökünü UseContentRoot yöntemiyle ayarlayan konak değişkenlerini vurgulayan C# Main yönteminin ekran görüntüsü.](media/netcore-image13.png)

5. Uygulamanın Internet Information Services (IIS) web sunucusuyla çalışması gerekirse, konak oluşturmanın bir parçası olarak **UseIISIntegration** yöntemi çağrılır. Bunun, **UseKestrel** gibi bir sunucu yapılandırmaz. IIS'yi ASP.NET Core için hem **UseKestrel** hem de **UseIISIntegration belirtmeniz gerekir.** **Kestrel** bir ara sunucu arkasında çalıştırılacak şekilde tasarlanmıştır ve doğrudan İnternet'e yönelik olarak dağıtılamamalı. **UseIISIntegration,** IIS'yi ters proxy sunucusu olarak belirtir, ancak yalnızca IIS'ye sahip makinelerde çalıştırılırken ilgili olur. Uygulamanızı uygulamanıza dağıtırsanız Windows bırakın. Aksi takdirde zarar vermez.

    ![UseIISIntegration yöntemiyle ters proxy sunucusunu ayarlayan konak değişkenini vurgulayan C# Main yönteminin ekran görüntüsü.](media/netcore-image14.png)

6. Ayarların yüklenmesini uygulama önyüklemeden ayırmak daha temiz bir uygulamadır. Bunu kolayca yapmak için, Başlangıç sınıfının ayarların ve HTTP işlem hattına ara yazılım ekleme gibi diğer başlangıç görevlerinin yüklenmesi için çağrıl olacağını belirtmek üzere **UseStartup** çağrılır.  Her birinin gerektiğinde önceki ayarların üzerine yazması beklentisiyle birden çok **UseStartup** çağrınız olabilir.

    ![UseStartup seçeneğiyle başlangıç sınıfını ayarlayan konak değişkeni vurgulanan C# Main yönteminin ekran görüntüsü.](media/netcore-image15.png)

7. **IWebHost** oluşturmanın son adımı Derleme çağrısı **yapmakdır.**

    ![Build yöntemiyle konak değişkenlerini vurgulayan C# Main yönteminin ekran görüntüsü.](media/netcore-image16.png)

8. **IWebHost** sınıfları engelleyici olmayan **Başlangıç** uygulamak için gerekliyken, ASP.NET Core projelerinde  Start **with** blocking code sarmalama adlı bir uzantı yöntemi vardır, bu nedenle yöntemin hemen çıkışlarını el ile engellemeniz gerekmez.

    ![Deyim ana bilgisayar noktası Çalıştır'ı vurgulayan C# Main yönteminin ekran görüntüsü.](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>4. Görev: Uygulamayı çalıştırma ve hata ayıklama

1. Bu **Çözüm Gezgini** **CoreLab** proje düğümüne sağ tıklayın ve Seçenekler'i **seçin.**

    ![Seçenekler'i vurgulayan CoreLab çözümünün bağlam menüsünü gösteren ekran görüntüsü.](media/netcore-image18.png)

2. Uygulama **Project iletişim** kutusu, uygulamanın nasıl yerleşik ve çalıştırıcı olduğunu ayarlamak için ihtiyacınız olan her şeyi içerir. Sol **panelden > Yapılandırmaları > Varsayılan** düğümünü seçin.

3. Dış **konsolda çalıştır'ın işaretini kaldırın** ve Konsol çıkışını **duraklat'ın işaretini kaldırın.** Normalde, kendi içinde barındırılan uygulamanın konsolu görünür olmaz, bunun yerine sonuçlarını Çıkış penceresine **günlüğe kaydedilir.** Bu laboratuvarın amaçları doğrultusunda bunu ayrı bir pencerede de gösterebilirsiniz, ancak normal geliştirme sırasında bunu yapmak zorunda değildir.

4. **Tamam**'a tıklayın.

    ![Dış konsolda çalıştır'ın seçili olduğu ve Konsol çıkışını duraklat'ın seçili olduğu YapılandırmaYı Çalıştır sekmesini gösteren ekran görüntüsü.](media/netcore-image19.png)

5. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın. Alternatif olarak, Hata Ayıklamayı **Başlat'> Çalıştır'ı da kullanabilirsiniz.**

6. Mac için Visual Studio iki pencere başlatacak. İlki, size kendi içinde barındırılan sunucu uygulamasına bir görünüm sağlayan bir konsol penceresidir.

    ![Kendinden konak sunucu uygulamasının konsol penceresini gösteren ekran görüntüsü.](media/netcore-image20.png)

7. İkincisi, siteyi test etmek için tipik bir tarayıcı penceresidir. Tarayıcının bildiği gibi bu uygulama herhangi bir yerde barındırabilirsiniz. Bu **sayfaya** gitmek için Hakkında'ya tıklayın.

    ![Hakkında seçeneğini vurgulayan, siteyi test etmek için bir tarayıcı penceresini gösteren ekran görüntüsü.](media/netcore-image21.png)

8. Diğer şeylerin dışında, about sayfası denetleyicide bazı metin kümelerini işler.

    ![Hakkında sayfası olan Hakkında seçeneğinin seçmenizin sonucunda elde edilen sonucu gösteren ekran görüntüsü.](media/netcore-image22.png)

9. Her iki pencereyi de açık tutma ve Mac için Visual Studio. **Henüz açık değilse Controllers/HomeController.cs'yi** açın.

    ![HomeController C# sınıfının yeniden seçili olduğu çözümü gösteren ekran görüntüsü.](media/netcore-image23.png)

10. About yönteminin ilk satırına bir kesme **noktası** ayarlayın. Bunu yapmak için kenar boşluğuna tıklar veya imleci satırda ayarp **F9 tuşuna basabilirsiniz.** Bu satır **Görünümler/Giriş/About.cshtml** sayfasındaki CSHTML sayfasında işlenen **ViewData** koleksiyonunda bazı verileri ayarlar.

    ![Kesme noktası kümesine sahip About yöntemini gösteren ekran görüntüsü.](media/netcore-image24.png)

11. Tarayıcıya geri dönüp hakkında sayfasını yenileyin. Bu, kesme noktası Mac için Visual Studio.

12. Verilerini görüntülemek için **fareyle ViewData** üyesinin üzerine tıklayın. İç içe geçmiş verileri görmek için alt üyelerini de genişletebilirsiniz.

    ![Verileri genişletilmiş bir kesme noktası gösteren ekran görüntüsü.](media/netcore-image25.png)

13. Eklemek için kullanılan yöntemi kullanarak uygulama kesme noktası kaldırın.

14. **Views/Home/About.cshtml dosyasını açın.**

15. **"additional" metnini "changed"** **olarak değiştirin** ve dosyayı kaydedin.

    ![Metninde yapılan bir değişiklikle Hakkında adlı C S H T M L dosyasının ekran görüntüsü.](media/netcore-image26.png)

16. Yürütmeye **devam etmek** için Devam düğmesine basın.

    ![Devam düğmesini Visual Studio ekran görüntüsü.](media/netcore-image27.png)

17. Güncelleştirilmiş metni görmek için tarayıcı penceresine geri dönebilirsiniz. Bu değişiklik herhangi bir zamanda yapılabilir ve hata ayıklayıcı kesme noktası gerektirmez. Değişikliğin hemen yansıtıldıdığını görmüyorsanız tarayıcıyı yenileyin.

    ![Bu kez değiştirilen metinle Hakkında sayfasının ekran görüntüsü.](media/netcore-image28.png)

18. Test tarayıcısı penceresini ve uygulama konsolunu kapatın. Bu işlem hata ayıklamayı da durdurur.

## <a name="task-5-application-startup-configuration"></a>5. Görev: Uygulama başlatma yapılandırması

1. **'Çözüm Gezgini** **Startup.cs'yi açın.** Paketler arka planda geri yüklenirken ve Roslyn NuGet derleyicisi proje bağımlılıklarının eksiksiz bir resmini derlerken başlangıçta bazı kırmızı geçişler fark edersiniz.

    ![Başlangıç adlı C# sınıf dosyasının seçili olduğu çözümün ekran görüntüsü.](media/netcore-image29.png)

2. Başlangıç **yöntemini** bulun. Bu bölüm, uygulamanın ilk yapılandırmasını tanımlar ve yoğun bir şekilde paketlenir. Ayrıntılı olarak inceleyelim.

    ![Startup sınıfının Başlangıç yöntemini gösteren ekran görüntüsü.](media/netcore-image30.png)

3. yöntemi bir **ConfigurationBuilder** başlatarak ve temel yolunu ayararak başlar.

    ![ConfigurationBuilder türüne sahip builder adlı bir değişkeni başlatan deyimini gösteren Başlangıç yönteminin ekran görüntüsü.](media/netcore-image31.png)

4. Ardından, gerekli bir dosyayı **appsettings.jsyükler.**

    ![Appsettings adlı json dosyasını eklemek için AddJsonFile yöntemini kullanan oluşturucu değişkenlerini gösteren Başlangıç yönteminin ekran görüntüsü.](media/netcore-image32.png)

5. Bundan sonra, dosyaya ortama özgü birappsettings.js **yükleme girişiminde bulunarak** mevcut ayarları geçersiz kılar. Örneğin, bu belirli birappsettings.Development.js **kullanılan dosyada** sağlanan bir dosyadır. Uygulama içinde yapılandırma hakkında daha fazla ASP.NET Core için [belgelerine göz at.](/aspnet/core/fundamentals/configuration)

    ![Ortama özgü appsettings json dosyası eklemek için AddJsonFile yöntemini kullanan oluşturucu değişkenlerini gösteren Başlangıç yönteminin ekran görüntüsü.](media/netcore-image34.png)

6. Son olarak, ortam değişkenleri yapılandırma oluşturucuya eklenir ve yapılandırma, kullanım için yerleşik ve ayarlanır.

    ![Ortam değişkenlerini ek olarak oluşturucu değişkeninin ve ardından yapılandırmayı derlemek için Build yönteminin kullandırarak gösteren Başlangıç yönteminin ekran görüntüsü.](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>6. Görev: Uygulama ara yazılımı ekleme

1. **Başlangıç** **sınıfında Configure** yöntemini bulun. Tüm ara yazılımların HTTP işlem hattına eklenecek ve sunucuya yapılan her isteği işley için kullanılacak şekilde yapılandırıldıkları yer burasıdır. Bu yöntem yalnızca bir kez çağrılsa da, her istekte yöntemlerin içeriği **(UseStaticFiles** gibi) yürütülebilirsiniz.

    ![Başlangıç sınıfında Yöntemi yapılandır'ın ekran görüntüsü.](media/netcore-image36.png)

2. İşlem hattının bir parçası olarak yürütülecek ek ara yazılım da ek olarak eklemeye de izin vesersiniz. Uygulamanın ardından aşağıdaki kodu **ekleyin. Giden her yanıta otomatik** olarak **bir X-Test** üst bilgisi eklemek içinStaticFiles kullanın. IntelliSense, siz yazarak kodun tamamlanmasına yardımcı olur.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Projeyi **derlemek ve** çalıştırmak için F5 tuşuna basın.

4. Tarayıcıyı kullanarak üst bilgileri inceleyebilirsiniz ve eklendiklerini doğrulayabilirsiniz. Aşağıdaki yönergeler Safari'ye yöneliktir, ancak aynısını Chrome veya [Firefox'ta](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) da [yapabilirsiniz.](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console)

5. Tarayıcı siteyi yüklerken Safari'yi ve **Tercihler'> seçin.**

6. Gelişmiş **sekmesinde,** menü **çubuğundaKi Geliştirme menüsünü göster'i seçin** ve iletişim kutusunu kapatın.

    ![Safari Tercihleri iletişim kutusundaki Gelişmiş bölmesini menü çubuğundaki Geliştir menüsünü göster seçeneğinin seçili olduğu ekran görüntüsü.](media/netcore-image37.png)

7. Sayfa **Kaynaklarını > Için Geliştir'i seçin.**

8. Yeni açılan geliştirici araçlarının trafiği ve içeriği takip edip analiz etmek için tarayıcı penceresini yenileyin.

9. Sunucu tarafından işlenen localhost HTML sayfası varsayılan olarak seçilen öğe olur.

    ![localhost H T M L sayfasını vurgulayan ekran görüntüsü.](media/netcore-image38.png)

10. Ayrıntılar kenar **çubuğu'larını genişletin.**

    ![Ayrıntılar kenar çubuğu genişletmek için kullanmak üzere denetimi vurgulayan ekran görüntüsü.](media/netcore-image39.png)

11. Daha önce koda eklenen yanıt üst bilgisini görmek için kenar çubuğunun en altına kaydırın.

    ![Test değeri değerine sahip XTest adlı yanıt üst bilgisini vurgulayan ekran görüntüsü.](media/netcore-image40.png)

12. Memnunsanız tarayıcı penceresini ve konsolunu kapatın.

## <a name="summary"></a>Özet

Bu laboratuvarda, ASP.NET Core ile uygulama geliştirmeye Mac için Visual Studio. Daha eksiksiz bir film veritabanı uygulaması geliştirmeyi keşfetmek için [MVC](/aspnet/core/tutorials/first-mvc-app/start-mvc) ile Kullanmaya başlayın öğretici ASP.NET Core bakın.
