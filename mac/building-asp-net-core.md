---
title: ASP.NET Core uygulamalar oluşturma
description: bu makale, Mac için Visual Studio ASP.NET Core uygulamalar oluşturma ve keşfetme konusunda size kılavuzluk eder.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.topic: how-to
ms.openlocfilehash: ac3e11fd849cc26949f6286fbe91b64719a4206ec0037370962afe65d6a9b15c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408552"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Mac için Visual Studio’da ASP.NET Core uygulamaları oluşturma

ASP.NET Core, web uygulamaları ve hizmetleri, ıot uygulamaları ve mobil arka uçlar gibi modern bulut tabanlı ınternet 'e bağlı uygulamalar oluşturmaya yönelik açık kaynaklı ve platformlar arası bir çerçevedir. ASP.NET Core uygulamalar, [.net Core](https://www.microsoft.com/net/core/platform) veya .NET Framework çalışma zamanları üzerinde çalışabilir. Buluta dağıtılan veya şirket içinde çalışan uygulamalar için iyileştirilmiş bir geliştirme çerçevesi sağlamak üzere tasarlanmıştır. En az ek yük olan modüler bileşenlerden oluşur, bu nedenle çözümlerinizi oluştururken esnekliği koruyabilirsiniz. Windows, Mac ve Linux 'ta ASP.NET Core uygulamalarınızı platformlar arası geliştirebilir ve çalıştırabilirsiniz. ASP.NET Core [GitHub](https://github.com/aspnet/home)açık kaynaktır.

bu laboratuvarda, Mac için Visual Studio bir ASP.NET Core uygulaması oluşturacaksınız ve keşfedecaksınız.

## <a name="objectives"></a>Hedefler

> [!div class="checklist"]
> * ASP.NET Core web uygulaması oluşturma
> * barındırma, yapılandırma ve ara yazılım modelini ASP.NET Core keşfet
> * ASP.NET Core web uygulamasında hata ayıklama

## <a name="prerequisites"></a>Önkoşullar

- [Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Hedef Kitle

Bu laboratuvar, C# hakkında bilgi sahibi olan geliştiricilere yöneliktir, ancak derin deneyim gerekli değildir.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>görev 1: yeni bir ASP.NET Core uygulaması oluşturma

1. **Mac için Visual Studio** başlatın.

2. **Yeni çözüm > dosya**' yı seçin.

3. **.net Core > uygulama** kategorisini ve **ASP.NET Core Web uygulaması (C#)** şablonunu seçin. **İleri**’ye tıklayın.

    ![Yeni projeniz için bir Web uygulaması şablonunun nasıl seçileceğini gösteren ekran görüntüsü.](media/netcore-image1.png)

4. Bir **"CoreLab"** adı girin ve projeyi oluşturmak için **Oluştur** ' a tıklayın. İşlemin tamamlanması biraz zaman alır.

    ![bir Project adı ekleyerek Web uygulaması yapılandırması ekran görüntüsü.](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Görev 2: çözümü gezi

1. varsayılan şablon, **corelab** adlı tek bir ASP.NET Core projesi ile bir çözüm oluşturacaktır. İçeriğini göstermek için proje düğümünü genişletin.

    ![Klasör ve dosya dahil içeriğini görmek için seçilen çözüm projesi düğümünün ekran görüntüsü.](media/netcore-image3.png)

2. Bu proje, veriler (modeller), sunum (görünümler) ve işlevsellik (denetleyiciler) arasındaki sorumlulukların açık bir bölümünü sağlamak için Model-View-Controller (MVC) paradigmasını izler. **Controllers** klasöründen **HomeController. cs** dosyasını açın.

    ![HomeController adlı C# sınıfına sahip çözüm projesinin ekran görüntüsü.](media/netcore-image4.png)

3. **HomeController** sınıfı-kural- **/Home** ile başlayan tüm gelen istekleri işler. **Dizin** yöntemi, istekleri dizinin köküne (gibi `http://site.com/Home` ) işler ve diğer yöntemler, isteklerini **()** ile işleme istekleri gibi kurala göre adlandırılmış yollarına göre işler `http://site.com/Home/About` . Kuşkusuz, bu tüm yapılandırılabilir. Tek bir önemli, **HomeController** 'ın yeni bir projede varsayılan denetleyici olması, bu nedenle sitenin köküne yönelik isteklerin ( `http://site.com` ), ya da için yapılan istekler gibi **HomeController** **dizininden (** ) geçer `http://site.com/Home` `http://site.com/Home/Index` .

    ![HomeController adlı bir C# sınıfının ekran görüntüsü.](media/netcore-image5.png)

4. Proje ayrıca, her denetleyiciyle eşlenen diğer klasörleri içeren bir **Görünümler** klasörüne sahiptir (aynı zamanda, **paylaşılan** görünümler için bir de). Örneğin, **/Home/about** yolu IÇIN görünüm cshtml dosyası (html uzantısı), **views/Home/about. cshtml** yolunda olacaktır. Bu dosyayı açın.

    ![Seçili hakkında adlı C S H T M dosyasını içeren çözüm projesinin ekran görüntüsü.](media/netcore-image6.png)

5. Bu CSHTML dosyası, standart etiketlerin ve satır içi C# birleşimine göre HTML işlemek için Razor söz dizimi kullanır. [Çevrimiçi belgelerde](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)bunun hakkında daha fazla bilgi edinebilirsiniz.

    ![Razor söz dizimi gösteren bir C S H T M L dosyasının bir kısmının ekran görüntüsü.](media/netcore-image7.png)

6. Çözüm, Web sitenizin kökü olacak bir **Wwwroot** klasörü de içerir. CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini, site dağıtıldığında olmasını istediğiniz yollarla koyabilirsiniz.

    ![W w w root klasörü seçili olan çözümün ekran görüntüsü.](media/netcore-image8.png)

7. Ayrıca, çalışma zamanında projeyi, paketleri ve uygulamayı yönetmeye yönelik bir dizi yapılandırma dosyası da vardır. Örneğin, varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) **üzerindeappsettings.js** depolanır. Aşağıda iç içe geçmiş dosyadaki appsettings.js **appsettings.Development.js** . Burada, bu ayarların bazılarını/tümünü ortam başına temelinde geçersiz kılabilirsiniz. Mac için Visual Studio, dosyaları bu şekilde Windows için Visual Studio ile aynı mantığı kullanarak iç içe geçirecektir. böylece, daha sık erişmeniz gereken dosyalar forefront ' de olur. 

    ![JSON dosyası seçili bir ayrıntı görünümünü gösteren ekran görüntüsü.](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>3. görev: uygulamanın nasıl barındırıldığını anlama

1. **Çözüm Gezgini**, **program. cs**' yi açın. Bu, uygulamanızı çalıştıracak olan önyükleyici.

    ![C# kaynak dosyası program seçildi adlı çözümün ekran görüntüsü.](media/netcore-image10.png)

2. Burada yalnızca iki satır kod olmakla kalmaz, çok önemli. Şimdi bunları bozalım. İlk olarak yeni bir **Webhostbuilder** oluşturulur. ASP.NET Core uygulamalar, çalıştırılacağı bir konak gerektirir. Bir konağın, özellik ve hizmet koleksiyonlarını ve bir **Başlangıç** yöntemini kullanıma sunan **ıwebhost** arabirimini uygulaması gerekir. Konak genellikle bir **Web Hostbuilder** örneği kullanılarak oluşturulur ve bu örnek, bir **Webhost** örneği oluşturur ve döndürür. **Webhost** , istekleri işleyecek sunucuya başvuracaktır.

    ![C# Main yönteminin, WebHostBuilder türünde ana bilgisayar adlı bir değişken Başlatan bir ifadesiyle ekran görüntüsü.](media/netcore-image11.png)

3. **Webhostbuilder** , uygulama için sunucuyu önyükleyen Konağı oluşturmaktan sorumludur, bunu uygulayan bir sunucu sağlamanız gerekir **`IServer`** . bu, varsayılan **[olarak, platformlar](/aspnet/core/fundamentals/servers/kestrel)** arası zaman uyumsuz g/ç kitaplığı olan **libuv** tabanlı ASP.NET Core yönelik platformlar arası web sunucusudur.

    ![UseKestrel yöntemi ile sunucuyu ayarlayarak ana bilgisayar değişkenini vurgulayan C# ana yönteminin ekran görüntüsü.](media/netcore-image12.png)

4. Daha sonra, sunucunun içerik kökü ayarlanır. Bu, MVC görünüm dosyaları gibi içerik dosyalarını nerede arayacağını belirler. Varsayılan içerik kökü, uygulamanın çalıştırıldığı klasördür.

    ![UseContentRoot yöntemiyle sunucunun içerik kökünü ayarlayarak ana bilgisayar değişkenini vurgulayan C# ana yönteminin ekran görüntüsü.](media/netcore-image13.png)

5. uygulamanın Internet Information Services (ııs) web sunucusu ile çalışması gerekiyorsa, konak oluşturmanın bir parçası olarak **useiisıntegration** yöntemi çağrılmalıdır. Bu, **UseKestrel** gibi bir sunucu yapılandırmaz. ııs 'yi ASP.NET Core kullanmak için, hem **UseKestrel** hem de **useiisıntegration**' i belirtmeniz gerekir. **Kestrel** , bir proxy 'nin arkasında çalışacak şekilde tasarlanmıştır ve doğrudan internet 'e yönelik olarak dağıtılmamalıdır. **Useiisıntegration** , IIS 'yi ters ara sunucu olarak belirtir, ancak yalnızca IIS 'e sahip makinelerde çalışırken ilgilidir. uygulamanızı Windows dağıtırsanız, içinde bırakın. Aksi takdirde, tersi olmaz.

    ![C# Main yönteminin, ters proxy sunucusunu Useiisıntegration yöntemiyle ayarlayarak ana bilgisayar değişkenini vurgulayan ekran görüntüsü.](media/netcore-image14.png)

6. Bu, ayarların yüklenmesini uygulama önyüklemesinden ayırmak için bir temizleyici uygulamadır. Bunu kolayca yapmak için, **Başlangıç** sınıfının, ayarlar ve http işlem hattına ara yazılım ekleme gibi diğer başlangıç görevlerinin çağrılması için çağrılabilmesi Için, **usestartup** çağrılır. Beklenmekte olan birden çok **Usestartup** çağrısı olabilir. Bu, her birinin gerektiğinde önceki ayarların üzerine yazılmasına neden olur.

    ![Başlangıç sınıfını UseStartup seçeneğiyle ayarlayarak ana bilgisayar değişkenini vurgulayan C# ana yönteminin ekran görüntüsü.](media/netcore-image15.png)

7. **Iwebhost** 'yi oluşturmanın son adımı **derlemeyi** çağırmakdır.

    ![Build yöntemiyle konak değişkenini vurgulayan C# ana yönteminin ekran görüntüsü.](media/netcore-image16.png)

8. **ıwebhost** sınıfları engelleyici olmayan **başlangıç** uygulamasını uygulamak için gerekli olsa da ASP.NET Core projeler, engelleme kodu ile **başlayan** bir genişletme  yöntemine sahiptir, böylece metodun hemen çıkış yapmasını el ile engellemeniz gerekmez.

    ![C# ana yönteminin, ana bilgisayar noktası çalıştırmasını vurgulayan ekran görüntüsü.](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>4. görev: uygulamayı çalıştırma ve hata ayıklama

1. **Çözüm Gezgini**, **CoreLab** proje düğümüne sağ tıklayın ve **Seçenekler**' i seçin.

    ![CoreLab çözümünün bağlam menüsünü gösteren ekran görüntüsü, vurgulama seçenekleri.](media/netcore-image18.png)

2. **Project seçenekleri** iletişim kutusu, uygulamanın nasıl oluşturulduğunu ve çalıştırılacağını ayarlamak için ihtiyacınız olan her şeyi içerir. Sol paneldeki **> yapılandırma > varsayılan düğümünü Çalıştır** ' ı seçin.

3. **Dış konsolda Çalıştır** ' ı işaretleyin ve **konsol çıkışını Duraklat**' işaretini kaldırın. Genellikle şirket içinde barındırılan uygulamanın Konsolu görünür olmaz, bunun yerine sonuçları **Çıkış** penceresine kaydeder. Bu laboratuvarın amaçları doğrultusunda, normal geliştirme sırasında bunu yapmanıza gerek olmasa da, bunu ayrı bir pencerede de göstereceğiz.

4. **Tamam**'a tıklayın.

    ![Dış konsolda Çalıştır seçili ve konsol çıkışını Duraklat seçili değil, yapılandırmayı Çalıştır Genel sekmesini gösteren ekran görüntüsü.](media/netcore-image19.png)

5. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın. Alternatif olarak, Hata Ayıklamayı **Başlat'> Çalıştır'ı da kullanabilirsiniz.**

6. Mac için Visual Studio iki pencere başlatacak. İlki, size kendi içinde barındırılan sunucu uygulamasına bir görünüm sağlayan bir konsol penceresidir.

    ![Kendinden konak sunucu uygulamasının konsol penceresini gösteren ekran görüntüsü.](media/netcore-image20.png)

7. İkincisi, siteyi test etmek için tipik bir tarayıcı penceresidir. Tarayıcının bildiği gibi bu uygulama herhangi bir yerde barındırabilirsiniz. Bu **sayfaya gitmek** için Hakkında'ya tıklayın.

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

    ![ConfigurationBuilder türüne sahip builder adlı değişkeni başlatan deyimini gösteren Başlangıç yönteminin ekran görüntüsü.](media/netcore-image31.png)

4. Ardından, gerekli birappsettings.js **yükler.**

    ![Appsettings adlı json dosyasını eklemek için AddJsonFile yöntemini kullanan oluşturucu değişkenlerini gösteren Başlangıç yönteminin ekran görüntüsü.](media/netcore-image32.png)

5. Bundan sonra, dosyaya ortama özgü birappsettings.js **yükleme girişiminde bulunarak** mevcut ayarları geçersiz kılar. Örneğin, bu belirli birappsettings.Development.js **kullanılan dosyada** sağlanan bir dosyadır. Uygulama içinde yapılandırma hakkında daha fazla ASP.NET Core için [belgelerine göz at.](/aspnet/core/fundamentals/configuration)

    ![Ortama özgü appsettings json dosyası eklemek için AddJsonFile yöntemini kullanan oluşturucu değişkenlerini gösteren Başlangıç yönteminin ekran görüntüsü.](media/netcore-image34.png)

6. Son olarak, ortam değişkenleri yapılandırma oluşturucuya eklenir ve yapılandırma, kullanım için yerleşik ve ayarlanır.

    ![Ortam değişkenlerini ek olarak oluşturucu değişkeninin ve ardından yapılandırmayı derlemek için Build yönteminin kullandırarak gösteren Başlangıç yönteminin ekran görüntüsü.](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>6. Görev: Uygulama ara yazılımı ekleme

1. **Başlangıç** **sınıfında Configure** yöntemini bulun. Bu, tüm ara yazılımların HTTP işlem hattına eklenecek ve sunucuya yapılan her isteği işley için kullanılacak şekilde yapılandırıldığından emin olun. Bu yöntem yalnızca bir kez çağrılsa da, her istekte yöntemlerin içeriği **(UseStaticFiles** gibi) yürütülebilirsiniz.

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

7. Sayfa **Kaynaklarını Göster >'yi seçin.**

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
