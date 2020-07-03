---
title: ASP.NET Core uygulamalar oluşturma
description: Bu makalede, yükleme ve yeni bir proje oluşturma dahil olmak üzere Mac için Visual Studio ' de ASP.NET ile çalışmaya başlama açıklanmaktadır.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.topic: how-to
ms.openlocfilehash: b0337f283fe5bb78f2f63e2f3da12eb9f2679450
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939192"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Mac için Visual Studio’da ASP.NET Core uygulamaları oluşturma

ASP.NET Core, Web uygulamaları ve Hizmetleri, IoT uygulamaları ve mobil arka uçlar gibi modern bulut tabanlı Internet 'e bağlı uygulamalar oluşturmaya yönelik açık kaynaklı ve platformlar arası bir çerçevedir. ASP.NET Core uygulamalar, [.NET Core](https://www.microsoft.com/net/core/platform) veya .NET Framework çalışma zamanları üzerinde çalışabilir. Buluta dağıtılan veya şirket içinde çalışan uygulamalar için iyileştirilmiş bir geliştirme çerçevesi sağlamak üzere tasarlanmıştır. En az ek yük olan modüler bileşenlerden oluşur, bu nedenle çözümlerinizi oluştururken esnekliği koruyabilirsiniz. Windows, Mac ve Linux 'ta ASP.NET Core uygulamalarınızı platformlar arası geliştirebilir ve çalıştırabilirsiniz. [GitHub](https://github.com/aspnet/home)'da açık kaynak ASP.NET Core.

Bu laboratuvarda, Mac için Visual Studio bir ASP.NET Core uygulaması oluşturacaksınız ve keşfedecaksınız.

## <a name="objectives"></a>Amaçlar

> [!div class="checklist"]
> * ASP.NET Core web uygulaması oluşturma
> * Barındırma, yapılandırma ve ara yazılım modelini ASP.NET Core keşfet
> * ASP.NET Core Web uygulamasında hata ayıklama

## <a name="prerequisites"></a>Önkoşullar

- [Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Hedef Kitle

Bu laboratuvar, C# hakkında bilgi sahibi olan geliştiricilere yöneliktir, ancak derin deneyim gerekli değildir.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Görev 1: yeni bir ASP.NET Core uygulaması oluşturma

1. **Mac için Visual Studio**başlatın.

2. **Yeni çözüm > dosya**' yı seçin.

3. **.NET Core > uygulama** kategorisini ve **ASP.NET Core Web uygulaması (C#)** şablonunu seçin. **İleri**’ye tıklayın.

    ![](media/netcore-image1.png)

4. Bir **"CoreLab"** adı girin ve projeyi oluşturmak için **Oluştur** ' a tıklayın. İşlemin tamamlanması biraz zaman alır.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Görev 2: çözümü gezi

1. Varsayılan şablon, **CoreLab**adlı tek bir ASP.NET Core projesi ile bir çözüm oluşturacaktır. İçeriğini göstermek için proje düğümünü genişletin.

    ![](media/netcore-image3.png)

2. Bu proje, veriler (modeller), sunum (görünümler) ve işlevsellik (denetleyiciler) arasındaki sorumlulukların açık bir bölümünü sağlamak için Model-View-Controller (MVC) paradigmasını izler. **HomeController.cs** dosyasını **denetleyiciler** klasöründen açın.

    ![](media/netcore-image4.png)

3. **HomeController** sınıfı-kural- **/Home**ile başlayan tüm gelen istekleri işler. **Dizin** yöntemi, istekleri dizinin köküne (gibi `http://site.com/Home` ) işler ve diğer yöntemler, isteklerini **()** ile işleme istekleri gibi kurala göre adlandırılmış yollarına göre işler `http://site.com/Home/About` . Kuşkusuz, bu tüm yapılandırılabilir. Tek bir önemli, **HomeController** 'ın yeni bir projede varsayılan denetleyici olması, bu nedenle sitenin köküne yönelik isteklerin ( `http://site.com` ), ya da için yapılan istekler gibi **HomeController** **dizininden (** ) geçer `http://site.com/Home` `http://site.com/Home/Index` .

    ![](media/netcore-image5.png)

4. Proje ayrıca, her denetleyiciyle eşlenen diğer klasörleri içeren bir **Görünümler** klasörüne sahiptir (aynı zamanda, **paylaşılan** görünümler için bir de). Örneğin, **/Home/about** yolu IÇIN görünüm cshtml dosyası (html uzantısı), **views/Home/about. cshtml**yolunda olacaktır. Bu dosyayı açın.

    ![](media/netcore-image6.png)

5. Bu CSHTML dosyası, standart etiketlerin ve satır içi C# birleşimine göre HTML işlemek için Razor söz dizimi kullanır. [Çevrimiçi belgelerde](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)bunun hakkında daha fazla bilgi edinebilirsiniz.

    ![](media/netcore-image7.png)

6. Çözüm, Web sitenizin kökü olacak bir **Wwwroot** klasörü de içerir. CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini, site dağıtıldığında olmasını istediğiniz yollarla koyabilirsiniz.

    ![](media/netcore-image8.png)

7. Ayrıca, çalışma zamanında projeyi, paketleri ve uygulamayı yönetmeye yönelik bir dizi yapılandırma dosyası da vardır. Örneğin, varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) **üzerindeappsettings.js**depolanır. Aşağıda iç içe geçmiş dosyadaki appsettings.js**appsettings.Development.js** . Burada, bu ayarların bazılarını/tümünü ortam başına temelinde geçersiz kılabilirsiniz. Mac için Visual Studio, Windows için Visual Studio ile aynı mantığı kullanarak dosyaları bu şekilde iç içe geçirecektir. böylece, daha sık erişmeniz gereken dosyalar Forefront ' de olur. 

    ![](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>3. görev: uygulamanın nasıl barındırıldığını anlama

1. **Çözüm Gezgini**, **program.cs**açın. Bu, uygulamanızı çalıştıracak olan önyükleyici.

    ![](media/netcore-image10.png)

2. Burada yalnızca iki satır kod olmakla kalmaz, çok önemli. Şimdi bunları bozalım. İlk olarak yeni bir **Webhostbuilder** oluşturulur. ASP.NET Core uygulamalar, çalıştırılacağı bir konak gerektirir. Bir konağın, özellik ve hizmet koleksiyonlarını ve bir **Başlangıç** yöntemini kullanıma sunan **ıwebhost** arabirimini uygulaması gerekir. Konak genellikle bir **Web Hostbuilder**örneği kullanılarak oluşturulur ve bu örnek, bir **Webhost** örneği oluşturur ve döndürür. **Webhost** , istekleri işleyecek sunucuya başvuracaktır.

    ![](media/netcore-image11.png)

3. **Webhostbuilder** , uygulama için sunucuyu önyükleyen Konağı oluşturmaktan sorumludur. Bu, **Iver**'i uygulayan bir sunucu sağlamanızı gerektirir. Bu, varsayılan **[olarak, platformlar](/aspnet/core/fundamentals/servers/kestrel)** arası zaman uyumsuz g/ç kitaplığı olan **libuv**tabanlı ASP.NET Core yönelik platformlar arası Web sunucusudur.

    ![](media/netcore-image12.png)

4. Daha sonra, sunucunun içerik kökü ayarlanır. Bu, MVC görünüm dosyaları gibi içerik dosyalarını nerede arayacağını belirler. Varsayılan içerik kökü, uygulamanın çalıştırıldığı klasördür.

    ![](media/netcore-image13.png)

5. Uygulamanın Internet Information Services (IIS) Web sunucusu ile çalışması gerekiyorsa, konak oluşturmanın bir parçası olarak **Useiisıntegration** yöntemi çağrılmalıdır. Bu, **UseKestrel** gibi bir sunucu yapılandırmaz. IIS 'yi ASP.NET Core kullanmak için, hem **UseKestrel** hem de **useiisıntegration**' i belirtmeniz gerekir. **Kestrel** , bir proxy 'nin arkasında çalışacak şekilde tasarlanmıştır ve doğrudan internet 'e yönelik olarak dağıtılmamalıdır. **Useiisıntegration** , IIS 'yi ters ara sunucu olarak belirtir, ancak yalnızca IIS 'e sahip makinelerde çalışırken ilgilidir. Uygulamanızı Windows 'a dağıtırsanız, içinde bırakın. Aksi takdirde, tersi olmaz.

    ![](media/netcore-image14.png)

6. Bu, ayarların yüklenmesini uygulama önyüklemesinden ayırmak için bir temizleyici uygulamadır. Bunu kolayca yapmak için, **Başlangıç** sınıfının, ayarlar ve http işlem hattına ara yazılım ekleme gibi diğer başlangıç görevlerinin çağrılması için çağrılabilmesi Için, **usestartup** çağrılır. Beklenmekte olan birden çok **Usestartup** çağrısı olabilir. Bu, her birinin gerektiğinde önceki ayarların üzerine yazılmasına neden olur.

    ![](media/netcore-image15.png)

7. **Iwebhost** 'yi oluşturmanın son adımı **derlemeyi**çağırmakdır.

    ![](media/netcore-image16.png)

8. **Iwebhost** sınıfları engelleyici olmayan **Başlangıç**uygulamasını uygulamak için gerekli olsa da ASP.NET Core projeler, engelleme kodu ile **başlayan** bir genişletme **Run** yöntemine sahiptir, böylece metodun hemen çıkış yapmasını el ile engellemeniz gerekmez.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>4. görev: uygulamayı çalıştırma ve hata ayıklama

1. **Çözüm Gezgini**, **CoreLab** proje düğümüne sağ tıklayın ve **Seçenekler**' i seçin.

    ![](media/netcore-image18.png)

2. **Proje seçenekleri** iletişim kutusu, uygulamanın nasıl oluşturulduğunu ve çalıştırılacağını ayarlamak için ihtiyacınız olan her şeyi içerir. Sol paneldeki **> yapılandırma > varsayılan düğümünü Çalıştır** ' ı seçin.

3. **Dış konsolda Çalıştır** ' ı işaretleyin ve **konsol çıkışını Duraklat**' işaretini kaldırın. Genellikle şirket içinde barındırılan uygulamanın Konsolu görünür olmaz, bunun yerine sonuçları **Çıkış** paneline kaydeder. Bu laboratuvarın amaçları doğrultusunda, normal geliştirme sırasında bunu yapmanıza gerek olmasa da, bunu ayrı bir pencerede de göstereceğiz.

4. **Tamam**'a tıklayın.

    ![](media/netcore-image19.png)

5. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın. Alternatif olarak, **hata ayıklamayı başlatmak > Çalıştır**' ı seçebilirsiniz.

6. Mac için Visual Studio iki pencere başlatacaktır. Birincisi, size şirket içinde barındırılan sunucu uygulamasına bir görünüm sağlayan bir konsol penceresidir.

    ![](media/netcore-image20.png)

7. İkincisi, siteyi test eden tipik bir tarayıcı penceresidir. Tarayıcının bildiği kadar, bu uygulama herhangi bir yerde barındırılabilir. Bu sayfaya gitmek için **hakkında** ' ya tıklayın.

    ![](media/netcore-image21.png)

8. Diğer şeyler arasında, hakkında sayfası denetleyicide bazı metin kümesini işler.

    ![](media/netcore-image22.png)

9. Her iki Windows açık tutun ve Mac için Visual Studio döndürün. Açık değilse, **denetleyicileri/HomeController. cs** ' i açın.

    ![](media/netcore-image23.png)

10. **About** yönteminin ilk satırında bir kesme noktası ayarlayın. Bunu, kenar boşluğuna tıklayarak veya imleci satır üzerinde ayarlayıp **F9**tuşuna basarak yapabilirsiniz. Bu satır, **views/Home/about. cshtml**konumundaki cshtml sayfasında Işlenen **ViewData** koleksiyonundaki bazı verileri ayarlar.

    ![](media/netcore-image24.png)

11. Tarayıcıya dönün ve hakkında sayfasını yenileyin. Bu, Mac için Visual Studio kesme noktasını tetikler.

12. Verilerini görüntülemek için **ViewData** üyesinin üzerinde fare. Ayrıca, iç içe geçmiş verileri görmek için alt üyelerini genişletebilirsiniz.

    ![](media/netcore-image25.png)

13. Uygulama kesme noktasını, eklemek için kullandığınız yöntemi kullanarak kaldırın.

14. **Görünümler/giriş/about. cshtml**dosyasını açın.

15. **"Ek"** metnini **"değiştirildi"** olarak değiştirin ve dosyayı kaydedin.

    ![](media/netcore-image26.png)

16. Yürütmeye devam etmek için **devam** düğmesine basın.

    ![](media/netcore-image27.png)

17. Güncelleştirilmiş metni görmek için tarayıcı penceresine dönün. Bu değişiklik herhangi bir zamanda yapılabilir ve bir hata ayıklayıcı kesme noktası gerektirmeyebilir. Değişikliğin hemen yansıtıldığını görmüyorsanız Tarayıcıyı yenileyin.

    ![](media/netcore-image28.png)

18. Test tarayıcısı penceresini ve uygulama konsolu 'nu kapatın. Bu, hata ayıklamayı da durdurur.

## <a name="task-5-application-startup-configuration"></a>5. görev: uygulama başlangıç yapılandırması

1. **Çözüm Gezgini**, **Startup.cs**açın. NuGet paketleri arka planda geri yüklendiği ve Roslyn derleyicisi proje bağımlılıklarının tamamen bir resmini oluşturmakta olduğu için başlangıçta bazı Red dalgalı çizgiler fark edebilirsiniz.

    ![](media/netcore-image29.png)

2. **Başlangıç** yöntemini bulun. Bu bölüm, uygulamanın ilk yapılandırmasını tanımlar ve özellikle paketlenmiştir. Şimdi bunu kesintiye uğratır.

    ![](media/netcore-image30.png)

3. Yöntem, **Configurationbuilder** başlatılarak ve temel yolu ayarlanarak başlatılır.

    ![](media/netcore-image31.png)

4. Sonra, dosya üzerinde gerekli bir **appsettings.js** yükler.

    ![](media/netcore-image32.png)

5. Bundan sonra, var olan ayarları geçersiz kılacak şekilde dosyaya ortama özgü **appsettings.js** yüklemeye çalışır. Örneğin, bu belirli bir ortam için kullanılan dosyada bir **appsettings.Development.js** verilmiştir. ASP.NET Core yapılandırma hakkında daha fazla bilgi edinmek için [belgelere](/aspnet/core/fundamentals/configuration)bakın.

    ![](media/netcore-image34.png)

6. Son olarak, ortam değişkenleri Yapılandırma oluşturucusuna eklenir ve yapılandırma oluşturulup kullanım için ayarlanır.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Görev 6: uygulama ara yazılımını ekleme

1. **Başlangıç** sınıfında **Configure** metodunu bulun. Bunun nedeni, HTTP işlem hattına eklenebilmesi ve sunucuya her isteği işlemek için kullanılması için tüm ara yazılımlar yapılandırılır. Bu yöntem yalnızca bir kez çağrıldığında, yöntemlerin içerikleri ( **Usestaticfiles**gibi) her istekte yürütülebilir.

    ![](media/netcore-image36.png)

2. Ayrıca, işlem hattının bir parçası olarak yürütülecek ek ara yazılım ekleyebilirsiniz. Uygulamadan sonra aşağıdaki kodu ekleyin **. **Her giden yanıta otomatik olarak bir **X-test** üst bilgisi eklemek Için usestaticfiles. IntelliSense, siz yazarken kodu tamamlamaya yardımcı olur.

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

    ![](media/netcore-image37.png)

7. **Geliştirme > sayfa kaynaklarını göster**' i seçin.

8. Yeni açılan Geliştirici araçlarının trafiği ve içeriği izleyip çözümleyebilmesi için tarayıcı penceresini yenileyin.

9. Sunucu tarafından oluşturulan localhost HTML sayfası, varsayılan olarak seçilen öğe olur.

    ![](media/netcore-image38.png)

10. **Ayrıntılar kenar çubuğunu**genişletin.

    ![](media/netcore-image39.png)

11. Daha önce koda eklenen yanıt üst bilgisini görmek için kenar çubuğunun en altına kaydırın.

    ![](media/netcore-image40.png)

12. Tatmin edildiğinde tarayıcı penceresini ve konsolunu kapatın.

## <a name="summary"></a>Özet

Bu laboratuvarda, Mac için Visual Studio ASP.NET Core uygulamaları geliştirmeye nasıl başladığınızı öğrendiniz. Daha kapsamlı bir film veritabanı uygulaması geliştirmeyi araştırmak isterseniz, [ASP.NET Core MVC ile çalışmaya başlama](/aspnet/core/tutorials/first-mvc-app/start-mvc) öğreticisine bakın.
