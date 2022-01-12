---
title: Uygulama ASP.NET Core
description: Bu makalede, uygulamalarla uygulama oluşturma ve ASP.NET Core oluşturma ve keşfetme Mac için Visual Studio.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.topic: how-to
ms.openlocfilehash: 1f7a84ef1414ee17d563011cb5b1399a7e02cccb
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803810"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Mac için Visual Studio’da ASP.NET Core uygulamaları oluşturma

ASP.NET Core web uygulamaları ve hizmetleri, IoT uygulamaları ve mobil arka uçlar gibi modern bulut tabanlı İnternet'e bağlı uygulamalar için açık kaynak ve platformlar arası bir çerçevedir. ASP.NET Core uygulamaları [.NET Core'da](https://www.microsoft.com/net/core/platform) veya .NET Framework çalıştırabilirsiniz. Buluta dağıtılan veya şirket içinde çalıştırılan uygulamalar için iyileştirilmiş bir geliştirme çerçevesi sağlamak için mimari olarak hazırlandı. Minimum ek yüke sahip modüler bileşenlerden oluşur, bu nedenle çözümlerinizi oluştururken esnekliği korur. Windows, Mac ve Linux ASP.NET Core platformlar arası uygulama geliştirebilir ve çalıştırabilirsiniz. ASP.NET Core açık kaynaktır ve [GitHub.](https://github.com/aspnet/home)

Bu laboratuvarda, ASP.NET Core ile Mac için Visual Studio.

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

2. Yeni **Çözüm >'yi seçin.**

3. **.NET Core uygulama > kategorisini** ve **ASP.NET Core Web Uygulaması (C#) şablonunu** seçin. **İleri**’ye tıklayın.

    ![Yeni projeniz için Bir Web Uygulaması şablonunun nasıl seçilenesini gösteren ekran görüntüsü.](media/netcore-image1.png)

4. Projeyi oluşturmak için **"CoreLab" adını** girin ve **Oluştur'a** tıklayın. Tamamlanması biraz zaman alır.

    ![Web Uygulaması yapılandırmasının, Project Ekleme'nin ekran görüntüsü.](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>2. Görev: Çözümü turlama

1. Varsayılan şablon, CoreLab adlı tek bir ASP.NET Core çözümü **oluşturur.** Proje düğümünü genişletarak içeriğini ortaya çıkarabilirsiniz.

    ![Klasörler ve dosyalar dahil olmak üzere içeriğini görmek için seçilen çözüm projesi düğümünün ekran görüntüsü.](media/netcore-image3.png)

2. Bu proje, veriler (modeller), sunu (görünümler) ve işlevler (denetleyiciler) arasındaki sorumlulukların net bir şekilde bölünmesini sağlamak için model-görünüm-denetleyici (MVC) paradigmasını izler. Controllers **klasöründen HomeController.cs** **dosyasını** açın.

    ![HomeController adlı bir C# sınıfının seçili olduğu çözüm projesinin ekran görüntüsü.](media/netcore-image4.png)

3. **HomeController** class-by kuralı, /Home ile başlatan tüm gelen **istekleri işler.** **Index yöntemi** dizinin köküne (gibi) istekleri, diğer yöntemler ise istekleri kuralına göre adlandırılmış yollarına işler; `http://site.com/Home` örneğin, **about()** işleme istekleri `http://site.com/Home/About` için . Elbette bunların hepsi yapılandırılabilir. **HomeController'ın** yeni projede varsayılan denetleyici olması, bu nedenle sitenin köküne ( ) yönelik isteklerin veya istekleri gibi `http://site.com` **HomeController'ın** **Index()** dizininden geçilmesidir. `http://site.com/Home` `http://site.com/Home/Index`

    ![HomeController adlı bir C# sınıfının ekran görüntüsü.](media/netcore-image5.png)

4. Projede ayrıca, her **denetleyiciyle** eşlene diğer klasörleri içeren bir Görünümler klasörü de vardır (paylaşılan görünümler için **de bir klasör).** Örneğin, **/Home/About** yolu için görünüm CSHTML dosyası (HTML uzantısı) **Views/Home/About.cshtml yolunda olabilir.** Bu dosyayı açın.

    ![Hakkında adlı C S H T M L dosyasının seçili olduğu çözüm projesinin ekran görüntüsü.](media/netcore-image6.png)

5. Bu CSHTML dosyası, standart Razor söz dizimi ve satır içi C# birleşimine göre HTML işlemek için Razor söz dizimi dosyasını kullanır. Bu konuda daha fazla bilgi için çevrimiçi [belgelerde bulabilirsiniz.](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)

    ![C S H T M L dosyasının bir bölümünü gösteren ekran Razor söz dizimi.](media/netcore-image7.png)

6. Çözüm ayrıca web **siteniz için** kök olacak bir wwwroot klasörü içerir. CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini, doğrudan site dağıtıldığında bunları istediğiniz yollara koyabilirsiniz.

    ![w w root klasörünün seçili olduğu çözümün ekran görüntüsü.](media/netcore-image8.png)

7. Ayrıca projeyi, paketlerini ve uygulamayı çalışma zamanında yönetmeye hizmet eden çeşitli yapılandırma dosyaları da vardır. Örneğin, varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) **appsettings.json içinde depolanır.** appsettings.json dosyasının altında **appsettings iç içe geçmiştir. Development.json** dosyası. Burada, bu ayarların bir/hepsini ortam bazında geçersiz kılabilirsiniz. Mac için Visual Studio, daha sık erişmesi gereken dosyaların ön planda olması için Visual Studio Windows ile aynı mantığı kullanarak dosyaları iç içe yerleştirmeyi sağlar. 

    ![JSON dosyasının seçili olduğu ayrıntı görünümünü gösteren ekran görüntüsü.](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>3. Görev: Uygulamanın nasıl barındırıldıklarını anlama

1. **'Çözüm Gezgini** **Program.cs'yi açın.** Bu, uygulamanızı çalıştıracak önyükleyicidir.

    ![Program adlı C# kaynak dosyasının seçili olduğu çözümün ekran görüntüsü.](media/netcore-image10.png)

2. Burada yalnızca iki kod satırı vardır ancak önemli ölçüdedir. Şimdi bunları parçalı olarak bakalım. İlk olarak yeni bir **WebHostBuilder** oluşturulur. ASP.NET Core uygulamaları, yürütülecek bir konak gerektirir. Bir konak, özellik ve hizmet koleksiyonlarını ve bir Start yöntemini ortaya çıkaran **IWebHost** arabirimini **uygulamalı.** Konak genellikle bir **WebHost** örneği oluşturan ve döndüren **bir WebHostBuilder** örneği kullanılarak oluşturulur. **WebHost,** istekleri işecek sunucuya başvurur.

    ![WebHostBuilder türüne sahip host adlı bir değişkeni başlatan deyimiyle birlikte C# Main yönteminin ekran görüntüsü.](media/netcore-image11.png)

3. **WebHostBuilder,** uygulama için sunucuyu önyüklerken konak oluşturmaktan sorumludur, ancak uygulayan bir sunucu sağlamanız **`IServer`** gerekir. Varsayılan olarak, bu **[kestrel,](/aspnet/core/fundamentals/servers/kestrel)** platformlar arası bir I/O ASP.NET Core kitaplığı olan **libuv'u** temel alan platformlar arası bir web sunucusudur.

    ![Sunucuyu UseKestrel yöntemiyle ayarlayan konak değişkenlerini vurgulayan C# Main yönteminin ekran görüntüsü.](media/netcore-image12.png)

4. Ardından sunucunun içerik kökü ayarlanır. Bu, MVC Görünüm dosyaları gibi içerik dosyalarını nerede araması olduğunu belirler. Varsayılan içerik kökü, uygulamanın çalıştır olduğu klasördür.

    ![Sunucu için içerik kökünü UseContentRoot yöntemiyle ayarlayan konak değişkenlerini vurgulayan C# Main yönteminin ekran görüntüsü.](media/netcore-image13.png)

5. Uygulamanın Internet Information Services (IIS) web sunucusuyla çalışması gerekirse, konak oluşturmanın bir parçası olarak **UseIISIntegration** yöntemi çağrılır. Bunun, **UseKestrel** gibi bir sunucu yapılandırmaz. IIS'yi ASP.NET Core için hem **UseKestrel hem** de **UseIISIntegration belirtmeniz gerekir.** **Kestrel** bir ara sunucu arkasında çalıştırılacak şekilde tasarlanmıştır ve doğrudan İnternet'e yönelik dağıtılamamalı. **UseIISIntegration,** IIS'yi ters proxy sunucusu olarak belirtir, ancak yalnızca IIS'ye sahip makinelerde çalıştırılırken kullanılabilir. Uygulamanızı uygulamanıza dağıtırsanız Windows bırakın. Aksi takdirde zarar vermez.

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

2. Project **Seçenekleri iletişim** kutusu, uygulamanın nasıl yerleşik ve çalıştırıcı olduğunu ayarlamak için ihtiyacınız olan her şeyi içerir. Sol **panelden > Yapılandırmaları > Varsayılan** düğümünü seçin.

3. Dış **konsolda çalıştır'ın işaretini kaldırın** ve Konsol çıkışını **duraklat'ın işaretini kaldırın.** Normalde, kendi içinde barındırılan uygulamanın konsolu görünür olmaz, bunun yerine sonuçlarını Çıkış penceresine **günlüğe kaydedilir.** Bu laboratuvarın amaçları doğrultusunda bunu ayrı bir pencerede de gösterebilirsiniz, ancak normal geliştirme sırasında bunu yapmak zorunda değildir.

4. **Tamam**'a tıklayın.

    ![Dış konsolda çalıştır'ın seçili olduğu ve Konsol çıkışını duraklat'ın seçili olduğu YapılandırmaYı Çalıştır sekmesini gösteren ekran görüntüsü.](media/netcore-image19.png)

5. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın. Alternatif olarak, **hata ayıklamayı başlatmak > Çalıştır**' ı seçebilirsiniz.

6. Mac için Visual Studio iki pencere başlatacaktır. Birincisi, size şirket içinde barındırılan sunucu uygulamasına bir görünüm sağlayan bir konsol penceresidir.

    ![Şirket içinde barındırılan sunucu uygulamasının konsol penceresini gösteren ekran görüntüsü.](media/netcore-image20.png)

7. İkincisi, siteyi test eden tipik bir tarayıcı penceresidir. Tarayıcının bildiği kadar, bu uygulama herhangi bir yerde barındırılabilir. Bu sayfaya gitmek için **hakkında** ' ya tıklayın.

    ![Siteyi test etmek için bir tarayıcı penceresi gösteren ekran görüntüsü hakkında seçeneğini vurgular.](media/netcore-image21.png)

8. Diğer şeyler arasında, hakkında sayfası denetleyicide bazı metin kümesini işler.

    ![Hakkında sayfası olan hakkında seçeneğinin seçilmesi sonucunu gösteren ekran görüntüsü.](media/netcore-image22.png)

9. her iki windows açık tutun ve Mac için Visual Studio döndürün. Açık değilse, **denetleyicileri/HomeController. cs** ' i açın.

    ![HomeController C# sınıfının yeniden seçili olduğu çözümü gösteren ekran görüntüsü.](media/netcore-image23.png)

10. **About** yönteminin ilk satırında bir kesme noktası ayarlayın. Bunu, kenar boşluğuna tıklayarak veya imleci satır üzerinde ayarlayıp **F9** tuşuna basarak yapabilirsiniz. Bu satır, **views/Home/about. cshtml** konumundaki cshtml sayfasında Işlenen **ViewData** koleksiyonundaki bazı verileri ayarlar.

    ![Bir kesme noktası kümesiyle Ilgili yöntemini gösteren ekran görüntüsü.](media/netcore-image24.png)

11. Tarayıcıya dönün ve hakkında sayfasını yenileyin. bu, Mac için Visual Studio kesme noktasını tetikler.

12. Verilerini görüntülemek için **ViewData** üyesinin üzerinde fare. Ayrıca, iç içe geçmiş verileri görmek için alt üyelerini genişletebilirsiniz.

    ![Verileri genişletilmiş bir kesme noktasını gösteren ekran görüntüsü.](media/netcore-image25.png)

13. Uygulama kesme noktasını, eklemek için kullandığınız yöntemi kullanarak kaldırın.

14. **Görünümler/giriş/about. cshtml** dosyasını açın.

15. **"Ek"** metnini **"değiştirildi"** olarak değiştirin ve dosyayı kaydedin.

    ![İle Ilgili olarak adında bir değişiklik olan C S H T M L dosyasının ekran görüntüsü.](media/netcore-image26.png)

16. Yürütmeye devam etmek için **devam** düğmesine basın.

    ![devam düğmesini vurgulayan Visual Studio penceresinin ekran görüntüsü.](media/netcore-image27.png)

17. Güncelleştirilmiş metni görmek için tarayıcı penceresine dönün. Bu değişiklik herhangi bir zamanda yapılabilir ve bir hata ayıklayıcı kesme noktası gerektirmeyebilir. Değişikliğin hemen yansıtıldığını görmüyorsanız Tarayıcıyı yenileyin.

    ![Bu kez değiştirilen metinle birlikte hakkında sayfasının ekran görüntüsü.](media/netcore-image28.png)

18. Test tarayıcısı penceresini ve uygulama konsolu 'nu kapatın. Bu, hata ayıklamayı da durdurur.

## <a name="task-5-application-startup-configuration"></a>5. görev: uygulama başlangıç yapılandırması

1. **Çözüm Gezgini**, **Başlangıç. cs**' yi açın. NuGet paketleri arka planda geri yüklendiği ve roslyn derleyicisi proje bağımlılıklarının tamamen bir resmini oluşturmakta olduğu için başlangıçta bazı red dalgalı çizgiler fark edebilirsiniz.

    ![C# sınıf dosyası başlatma seçiliyken çözümün ekran görüntüsü.](media/netcore-image29.png)

2. **Başlangıç** yöntemini bulun. Bu bölüm, uygulamanın ilk yapılandırmasını tanımlar ve özellikle paketlenmiştir. Ayrıntılı olarak inceleyelim.

    ![Başlangıç sınıfının başlangıç yöntemini gösteren ekran görüntüsü.](media/netcore-image30.png)

3. Yöntem, **Configurationbuilder** başlatılarak ve temel yolu ayarlanarak başlatılır.

    ![ConfigurationBuilder türünde Oluşturucu adlı bir değişken başlatarak bir deyimin gösterildiği başlangıç yönteminin ekran görüntüsü.](media/netcore-image31.png)

4. Ardından, gerekli bir **appSettings. JSON** dosyası yükler.

    ![AppSettings adlı json dosyasını eklemek için AddJsonFile yöntemi kullanılarak Oluşturucu değişkenini gösteren başlangıç yönteminin ekran görüntüsü.](media/netcore-image32.png)

5. Bundan sonra, var olan ayarları geçersiz kılacak ortama özgü bir **appSettings. JSON** dosyası yüklemeye çalışır. Örneğin, bu bir belirtilen appSettings 'dir **.** Bu belirli ortam için kullanılan Development. JSON dosyası. ASP.NET Core yapılandırma hakkında daha fazla bilgi edinmek için [belgelere](/aspnet/core/fundamentals/configuration)bakın.

    ![Bir ortama özgü appSettings JSON dosyası eklemek için AddJsonFile yöntemi kullanılarak Oluşturucu değişkenini gösteren başlangıç yönteminin ekran görüntüsü.](media/netcore-image34.png)

6. Son olarak, ortam değişkenleri Yapılandırma oluşturucusuna eklenir ve yapılandırma oluşturulup kullanım için ayarlanır.

    ![Başlangıç yönteminin, ortam değişkenleri ekleyen Oluşturucu değişkenini gösteren ve ardından yapılandırmayı oluşturmak için Build yönteminin kullanıldığı ekran görüntüsü.](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Görev 6: uygulama ara yazılımını ekleme

1. **Başlangıç** sınıfında **Configure** metodunu bulun. Bunun nedeni, HTTP işlem hattına eklenebilmesi ve sunucuya her isteği işlemek için kullanılması için tüm ara yazılımlar yapılandırılır. Bu yöntem yalnızca bir kez çağrıldığında, yöntemlerin içerikleri ( **Usestaticfiles** gibi) her istekte yürütülebilir.

    ![Başlangıç sınıfında configure metodunu gösteren ekran görüntüsü.](media/netcore-image36.png)

2. Ayrıca, işlem hattının bir parçası olarak yürütülecek ek ara yazılım ekleyebilirsiniz. Uygulamadan sonra aşağıdaki kodu ekleyin **.** Her giden yanıta otomatik olarak bir **X-test** üst bilgisi eklemek Için usestaticfiles. IntelliSense, siz yazarken kodu tamamlamaya yardımcı olur.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Projeyi derlemek ve çalıştırmak için **F5** tuşuna basın.

4. Eklenen üstbilgileri denetlemek için tarayıcıyı kullanabiliriz. Aşağıdaki yönergeler Safari 'ye yöneliktir, ancak [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) veya [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console)'ta aynı şekilde yapabilirsiniz.

5. Tarayıcı siteyi yükledikten sonra **Safari > tercihleri**' ni seçin.

6. **Gelişmiş** sekmesinde, **menü çubuğunda geliştir menüsünü göster** ' i işaretleyin ve iletişim kutusunu kapatın.

    ![Safari tercihleri iletişim kutusundaki Gelişmiş bölmesini menü çubuğundaki geliştir menüsünü göster seçeneği belirlenmiş olarak gösteren ekran görüntüsü.](media/netcore-image37.png)

7. **Geliştirme > sayfa kaynaklarını göster**' i seçin.

8. Yeni açılan Geliştirici araçlarının trafiği ve içeriği izleyip çözümleyebilmesi için tarayıcı penceresini yenileyin.

9. Sunucu tarafından oluşturulan localhost HTML sayfası, varsayılan olarak seçilen öğe olur.

    ![Localhost H T M sayfasını vurgulayan ekran görüntüsü.](media/netcore-image38.png)

10. **Ayrıntılar kenar çubuğunu** genişletin.

    ![Ayrıntılar kenar çubuğunu genişletmek için kullanılacak denetimi vurgulayan ekran görüntüsü.](media/netcore-image39.png)

11. Daha önce koda eklenen yanıt üst bilgisini görmek için kenar çubuğunun en altına kaydırın.

    ![Test değeri değeri olan XTest adlı yanıt üst bilgisini vurgulayan ekran görüntüsü.](media/netcore-image40.png)

12. Tatmin edildiğinde tarayıcı penceresini ve konsolunu kapatın.

## <a name="summary"></a>Özet

bu laboratuvarda, Mac için Visual Studio ASP.NET Core uygulamaları geliştirmeye nasıl başladığınızı öğrendiniz. daha kapsamlı bir film veritabanı uygulaması geliştirmeyi araştırmak isterseniz, [ASP.NET Core MVC ile çalışmaya başlama](/aspnet/core/tutorials/first-mvc-app/start-mvc) öğreticisine bakın.
