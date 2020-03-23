---
title: ASP.NET Temel uygulamaları oluşturma
description: Bu makalede, yükleme ve yeni bir proje oluşturma da dahil olmak üzere Visual Studio for Mac'te ASP.NET nasıl başlasınız açıklanmaktadır.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: 5600fd2f0b6d83a3bd27350a4d4f0137ea44ced2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75398275"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Mac için Visual Studio’da ASP.NET Core uygulamaları oluşturma

ASP.NET Core, web uygulamaları ve hizmetleri, IoT uygulamaları ve mobil arka uçlar gibi modern bulut tabanlı internet bağlantılı uygulamalar oluşturmak için açık kaynak kodlu ve çapraz platform çerçevesidir. ASP.NET Core uygulamaları [.NET Core'da](https://www.microsoft.com/net/core/platform) veya .NET Framework çalışma saatlerinde yayınlanabilir. Buluta dağıtılan veya şirket içinde çalışan uygulamalar için optimize edilmiş bir geliştirme çerçevesi sağlamak üzere tasarlandı. En az yükü olan modüler bileşenlerden oluşur, böylece çözümlerinizi yaparken esnekliği korursunuz. Windows, Mac ve Linux'ta ASP.NET Core uygulamalarınızı geliştirebilir ve çalıştırabilirsiniz. ASP.NET Core [GitHub](https://github.com/aspnet/home)açık kaynak.

Bu laboratuvarda, Mac için Visual Studio ile bir ASP.NET Core uygulaması oluşturacak ve keşfe çıkacaksınız.

## <a name="objectives"></a>Amaçlar

> [!div class="checklist"]
> * ASP.NET Core web uygulaması oluşturma
> * ASP.NET Core barındırma, yapılandırma ve ara yazılım modelini keşfedin
> * ASP.NET Core web uygulamasını hata ayıklama

## <a name="prerequisites"></a>Önkoşullar

- [Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Hedef Kitle

Derin deneyim gerekli olmasa da, bu laboratuvar C # aşina geliştiriciler için tasarlanmıştır.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Görev 1: Yeni bir ASP.NET Core uygulaması oluşturma

1. **Mac için Visual Studio**başlatın.

2. **Yeni Çözüm > Dosya'yı**seçin.

3. **.NET Core > App** kategorisini ve **ASP.NET Çekirdek Web Uygulaması (C#)** şablonunu seçin. **İleri**'ye tıklayın.

    ![](media/netcore-image1.png)

4. **"CoreLab"** adını girin ve projeyi oluşturmak için **Oluştur'u** tıklatın. Tamamlanması biraz zaman alacak.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Görev 2: Çözümü gezme

1. Varsayılan şablon **CoreLab**adlı tek bir ASP.NET Core proje ile bir çözüm üretecektir. İçeriğini ortaya çıkarmak için proje düğümünü genişletin.

    ![](media/netcore-image3.png)

2. Bu proje, veri (modeller), sunu (görünümler) ve işlevsellik (denetleyiciler) arasındaki sorumlulukların net bir bölümünü sağlamak için model görünümü denetleyicisi (MVC) paradigmasını izler. **Denetleyiciler** klasöründen **HomeController.cs** dosyasını açın.

    ![](media/netcore-image4.png)

3. **HomeController** class-by convention-ile başlayan tüm gelen istekleri **işler /Home.** **Dizin** yöntemi, istekleri dizin köküne (beğen) `http://site.com/Home`işler ve diğer yöntemler **istekleri, About()** işleme istekleri `http://site.com/Home/About`gibi, kural kuralına göre adlandırılmış yola işler. Tabii ki, bunların hepsi yapılandırılabilir. Bir kayda değer **HomeController** yeni bir projede varsayılan denetleyici olmasıdır,`http://site.com`bu yüzden sitenin köküne istekleri ( ) `http://site.com/Home` `http://site.com/Home/Index` **HomeController** **Index()** üzerinden gider diveya .

    ![](media/netcore-image5.png)

4. Projede ayrıca, her denetleyiciyle eşlenebilen diğer klasörleri (ve **Paylaşılan** görünümler için bir klasör içeren bir **Görünümler** klasörü de vardır. Örneğin, **/Home/About** yolu için CSHTML dosyası (HTML uzantısı) görünümü **Görünümler/Ana Sayfa/About.cshtml**adresinde olacaktır. O dosyayı aç.

    ![](media/netcore-image6.png)

5. Bu CSHTML dosyası, standart etiketler ve satır altı C#'ın birleşimine dayalı olarak HTML işlemek için Razor sözdizimini kullanır. Bu konuda daha fazla bilgi için [çevrimiçi belgelerde](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)bulabilirsiniz.

    ![](media/netcore-image7.png)

6. Çözüm ayrıca web sitenizin kökü olacak bir **wwwroot** klasörü içerir. CSS, resimler ve JavaScript kitaplıkları gibi statik site içeriğini doğrudan site dağıtıldığında olmasını istediğiniz yollara yerleştirebilirsiniz.

    ![](media/netcore-image8.png)

7. Projeyi, paketlerini ve uygulamayı çalışma zamanında yönetmeye hizmet eden çeşitli yapılandırma dosyaları da vardır. Örneğin, varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) **appsettings.json'da**depolanır. appsettings.json dosyasının altında yer alan **uygulama ayarları dır. Development.json** dosyası. Burada, bu ayarların bir kısmını/tümlerini ortam başına geçersiz kılabilirsiniz. Mac için Visual Studio, Windows için Visual Studio ile aynı mantığı kullanarak dosyaları bu şekilde yuvalar, böylece daha sık erişmeniz gereken dosyalar ön planda dır. 

    ![](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Görev 3: Uygulamanın nasıl barındırılan olduğunu anlama

1. **Çözüm Explorer**Gönderen , **açık Program.cs**. Bu, başvurunuzu yürütecek olan bootstrapper.

    ![](media/netcore-image10.png)

2. Burada sadece iki kod satırı olsa da, bunlar önemli. Onları yıkalım. İlk olarak, yeni bir **WebHostBuilder** oluşturulur. ASP.NET Core uygulamaları çalıştırmak için bir ana bilgisayar gerektirir. Bir ana bilgisayar, özellik ve hizmet koleksiyonlarını ve **Başlangıç** yöntemini ortaya çıkaran **IWebHost** arabirimini uygulamalıdır. Ana bilgisayar genellikle bir **WebHostBuilder**örneği kullanılarak oluşturulur, hangi oluşturur ve bir **WebHost** örneği döndürür. **WebHost** istekleri işleyecek sunucubaşvurur.

    ![](media/netcore-image11.png)

3. **WebHostBuilder** uygulama için sunucu bootstrap olacak ana bilgisayar oluşturmak için sorumlu olsa da, **IServer**uygulayan bir sunucu sağlamanızı gerektirir. Varsayılan olarak, bu **[Kestrel](/aspnet/core/fundamentals/servers/kestrel)**, **libuv**dayalı ASP.NET Core için bir çapraz platform web sunucusu , bir çapraz platform asynchronous G / O kütüphane.

    ![](media/netcore-image12.png)

4. Ardından, sunucunun içerik kökü ayarlanır. Bu, MVC View dosyaları gibi içerik dosyalarını nerede araması olduğunu belirler. Varsayılan içerik kökü, uygulamanın çalıştırıldığı klasördür.

    ![](media/netcore-image13.png)

5. Uygulamanın Internet Information Services (IIS) web sunucusuyla çalışması gerekiyorsa, **useiisintegration** yöntemi ana bilgisayar Oluşturmanın bir parçası olarak çağrılmalıdır. Bu **useKestrel** yaptığı gibi bir sunucu yapılandırmak değildir. IIS'yi ASP.NET Core ile kullanmak için **hem UseKestrel** hem de **UseIISIntegration**belirtmeniz gerekir. **Kerkenez** bir proxy arkasında çalıştırmak için tasarlanmıştır ve doğrudan internet bakan dağıtılmamalıdır. **UseIISIntegration,** IIS'yi ters proxy sunucusu olarak belirtir, ancak yalnızca IIS'si olan makinelerde çalışırken alakalıdır. Uygulamanızı Windows'a dağıtırsanız, uygulamayı içinde bırakın. Başka türlü acıtmaz.

    ![](media/netcore-image14.png)

6. Ayarların yüklenmesiyle uygulama bootstrapping'den ayırmak daha temiz bir uygulamadır. Bunu kolayca yapmak için, Başlangıç **sınıfının** ayarlar ve diğer başlangıç görevlerinin yüklenmesi için çağrılması gerektiğini belirtmek için **UseStartup** çağrılır, örneğin ARA YAZıLıMları HTTP ardışık bölümüne eklemek gibi. Her birinin gerektiğinde önceki ayarların üzerine yazabileceği beklentisiyle birden çok **UseStartup** çağrınız olabilir.

    ![](media/netcore-image15.png)

7. **IWebHost** oluşturmada son adım **Build**aramaktır.

    ![](media/netcore-image16.png)

8. **IWebHost** sınıfları non-blocking **Başlat**uygulamak için gerekli olsa da, ASP.NET Çekirdek projeleri hemen çıkış yöntemini el ile önlemek gerekmez, böylece engelleme kodu ile **Başlat** sarar **Çalıştır** adlı bir uzantı yöntemi var.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Görev 4: Uygulamayı çalıştırma ve hata ayıklama

1. **Solution Explorer'da** **CoreLab** proje düğümüne sağ tıklayın ve **Seçenekler'i**seçin.

    ![](media/netcore-image18.png)

2. **Proje Seçenekleri** iletişim kutusu, uygulamanın oluşturulup çalıştırılan şeklini ayarlamak için ihtiyacınız olan her şeyi içerir. Sol panelden > Varsayılan düğüm **yapılandırmaları > Çalıştır'ı** seçin.

3. **Dış konsolda Çalıştır'ı** denetleyin ve **Duraklat konsol çıktısını**kaldırın. Normalde kendi kendine barındırılan uygulama konsolu görünür olmaz, ancak bunun yerine **Çıkış** pad sonuçlarını günlüğe kaydeder. Bu laboratuvarın amaçları için, bunu ayrı bir pencerede de göstereceğiz, ancak normal gelişim sırasında bunu yapmanızgerekmez.

4. **Tamam**'a tıklayın.

    ![](media/netcore-image19.png)

5. Uygulamayı oluşturmak ve çalıştırmak için **F5** tuşuna basın. Alternatif olarak, **Hata Ayıklama'yı başlat> çalıştır'ı**seçebilirsiniz.

6. Mac için Visual Studio iki pencere başlatacak. Bunlardan ilki, kendi kendine barındırılan sunucu uygulamasına bir görünüm sağlayan bir konsol penceresidir.

    ![](media/netcore-image20.png)

7. İkincisi, siteyi test etmek için tipik bir tarayıcı penceresidir. Bildiğim kadarıyla tarayıcı bilir, bu uygulama her yerde barındırılabilir. Bu sayfaya gitmek için **Hakkında'yı** tıklatın.

    ![](media/netcore-image21.png)

8. Diğer şeylerin yanı sıra, hakkında sayfa denetleyicide ayarlanmış bazı metin işler.

    ![](media/netcore-image22.png)

9. Her iki pencereyi de açık tutun ve Mac için Visual Studio'ya geri dönün. Zaten açık değilse **Kumandalar/HomeController.cs'yi** açın.

    ![](media/netcore-image23.png)

10. **About** yönteminin ilk satırında bir kesme noktası ayarlayın. Bunu kenar boşluğuna tıklayarak veya imleci çizgiüzerinde ayarlayarak ve **F9**tuşuna basarak yapabilirsiniz. Bu satır, **Görünümler/Ana Sayfa/About.cshtml'deki**CSHTML sayfasında işlenen **ViewData** koleksiyonundaki bazı verileri ayarlar.

    ![](media/netcore-image24.png)

11. Tarayıcıya dönün ve ilgili sayfayı yenileyin. Bu Mac için Visual Studio kırılma noktası tetikler.

12. Verilerini görüntülemek için **ViewData** üyesinin üzerinde fare. İç içe geçen verileri görmek için alt üyelerini de genişletebilirsiniz.

    ![](media/netcore-image25.png)

13. Eklemek için kullandığınız yöntemi kullanarak uygulama kesme noktasını kaldırın.

14. **Açık Görünümler/Ana Sayfa/About.cshtml**.

15. **"Ek" metnini** **"değiştirildi"** olarak değiştirin ve dosyayı kaydedin.

    ![](media/netcore-image26.png)

16. Yürütmeye devam etmek için **Devam et** düğmesine basın.

    ![](media/netcore-image27.png)

17. Güncelleştirilmiş metni görmek için tarayıcı penceresine dönün. Bu değişiklik herhangi bir zamanda yapılabilir ve mutlaka bir hata ayıklama kesme noktası gerektirmez. Değişikliğin hemen yansıtTığını görmüyorsanız tarayıcıyı yenileyin.

    ![](media/netcore-image28.png)

18. Test tarayıcısı penceresini ve uygulama konsolu kapatın. Bu hata ayıklamayı da durduracaktır.

## <a name="task-5-application-startup-configuration"></a>Görev 5: Uygulama başlatma yapılandırması

1. **Çözüm Explorer**gönderen, **açık Startup.cs**. NuGet paketleri arka planda geri yüklenirken ve Roslyn derleyicisi proje bağımlılıklarının tam bir resmini oluşturduğundan, başlangıçta bazı kırmızı dalgalı lıklar fark edebilirsiniz.

    ![](media/netcore-image29.png)

2. **Başlangıç** yöntemini bulun. Bu bölümde uygulama için ilk yapılandırma tanımlanır ve yoğun olarak paketlenmiştir. Hadi parçalayalım.

    ![](media/netcore-image30.png)

3. Yöntem, **configurationbuilder'ı** başlatarak ve temel yolunu ayarlayarak başlar.

    ![](media/netcore-image31.png)

4. Ardından, gerekli **appsettings.json** dosyayükler.

    ![](media/netcore-image32.png)

5. Bundan sonra, varolan ayarları geçersiz kılacak ortama özgü bir **appsettings.json** dosyasını yüklemeye çalışır. Örneğin, bu sağlanan bir **uygulama ayarlarıdır. Development.json** dosyası bu belirli ortam için kullanılır. ASP.NET Core'daki yapılandırma hakkında daha fazla bilgi için [dokümanlara](/aspnet/core/fundamentals/configuration)göz atın.

    ![](media/netcore-image34.png)

6. Son olarak, ortam değişkenleri yapılandırma oluşturucuya eklenir ve yapılandırma oluşturulur ve kullanım için ayarlanır.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Görev 6: Uygulama ara yazılım ekleme

1. **Başlangıç** sınıfında **Yapılandırma** yöntemini bulun. Bu, tüm ara yazılımların HTTP ardışık hattına eklenebilecek ve sunucuya her isteği işlemek için kullanılabileceğini nisbetinde yapılandırıldığı yerdir. Bu yöntem yalnızca bir kez çağrılsa da, yöntemlerin içeriği **(UseStaticFiles**gibi) her istekte yürütülebilir.

    ![](media/netcore-image36.png)

2. Ayrıca, ardışık yolun bir parçası olarak yürütülecek ek ara yazılımlar da ekleyebilirsiniz. Uygulamadan sonra aşağıdaki kodu **ekleyin. **Giden her yanıta otomatik olarak Bir **X-Test** üstbilgisi eklemek için StaticFiles'ı kullanın. IntelliSense, siz yazarken kodun tamamlanmasına yardımcı olur.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Projeyi oluşturmak ve çalıştırmak için **F5** tuşuna basın.

4. Tarayıcıyı, eklendiğini doğrulamak için üstbilgiincelemek için kullanabiliriz. Aşağıdaki talimatlar Safari için, ancak [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) veya [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console)aynı şeyi yapabilirsiniz.

5. Tarayıcı siteyi yüklendikten sonra **Safari > Tercihleri'ni**seçin.

6. **Gelişmiş** **sekmesinde, menü çubuğunda Geliştir menüsünü göster'i** işaretleyin ve iletişim kutusunu kapatın.

    ![](media/netcore-image37.png)

7. **Sayfa Kaynaklarını Göster>'yi**seçin.

8. Yeni açılan geliştirici araçlarının trafiği ve içeriği izleyip analiz edebilmeleri için tarayıcı penceresini yenileyin.

9. Sunucu tarafından işlenen yerel barındırma HTML sayfası varsayılan olarak seçilen öğe olacaktır.

    ![](media/netcore-image38.png)

10. Ayrıntılar **kenar çubuğunu**genişletin.

    ![](media/netcore-image39.png)

11. Daha önce koda eklenen yanıt üstbilgisini görmek için kenar çubuğunun altına gidin.

    ![](media/netcore-image40.png)

12. Memnun olduğunuzda tarayıcı penceresini ve konsolu kapatın.

## <a name="summary"></a>Özet

Bu laboratuvarda, Visual Studio for Mac ile ASP.NET Core uygulamaları geliştirmeye nasıl başladığınızı öğrendiniz. Daha eksiksiz bir film veritabanı uygulaması geliştirmeyi keşfetmek istiyorsanız, [Core MVC](/aspnet/core/tutorials/first-mvc-app/start-mvc) ASP.NET ile başlayın' a bakın.
