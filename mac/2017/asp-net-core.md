---
title: ASP.NET Core Kullanmaya Başlama
description: Bu makalede, yükleme ve yeni bir proje oluşturma da dahil olmak üzere Visual Studio for Mac'te ASP.NET nasıl başlasınız açıklanmaktadır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/13/2017
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.openlocfilehash: 5f1a617c5562c4f95fec94ae449f48b681fcb7ef
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543754"
---
# <a name="getting-started-with-aspnet-core"></a>ASP.NET Core Kullanmaya Başlama

 Mac için Visual Studio, en son ASP.NET Core Web geliştirme platformuna verdiği destekle uygulamanızın hizmetini geliştirmenizi kolaylaştırır. ASP.NET Core, .NET Framework ve çalışma zamanının en son evrimi olan .NET Core'da çalışır. Hızlı performans için ayarlanmış, küçük yükleme boyutları için faktörlü ve Linux ve macOS yanı sıra Windows üzerinde çalıştırmak için yeniden hayal.

## <a name="installing-net-core"></a>.NET Core kurulumu

.NET Core 1.1, Mac için Visual Studio'yı yüklediğinizde otomatik olarak yüklenir.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Mac için Visual Studio'da ASP.NET Core uygulaması oluşturma

Mac için Visual Studio'u açın. Karşılama sayfasında **Yeni Proje'yi seçin...**

![Yeni Proje İletişim Kutusu](media/asp-net-core-image1.png)

Bu, Uygulamanızı oluşturmak için bir şablon seçmenize olanak tanıyan Yeni Proje iletişim kutusunu görüntüler.

ASP.NET Çekirdek Uygulamanızı oluşturmaya başlamak için önceden oluşturulmuş bir şablon sağlayacak bir dizi proje vardır. Bunlar:

- **.NET Çekirdek > ASP.NET Çekirdek Boş Web Uygulaması**
- **.NET Core > ASP.NET Core Web Uygulaması**
- **.NET Çekirdek > ASP.NET Çekirdek Web API**
- **Çok platformlu > Uygulaması > Bağlantılı Uygulama**

![ASP.NET Proje Seçenekleri](media/asp-net-core-image11.png)

ASP.NET **Çekirdek Boş Web Uygulaması'nı** seçin ve **İleri**tuşuna basın. Projeye Bir Ad Verin ve **Oluştur'a**basın. Bu, aşağıdaki resme benzer görünmesi gereken yeni bir ASP.NET Core uygulaması oluşturur:

![Yeni ASP.NET Çekirdek Boş Proje görünümü](media/asp-net-core-image4.png)

ASP.NET Çekirdek Boş Web Uygulaması iki varsayılan dosyaları ile bir web uygulaması oluşturur: **Program.cs** ve **Startup.cs**, aşağıda açıklanmıştır. Ayrıca, projenizin ASP.NET Core, .NET Core çerçevesi ve projeyi oluşturan MSBuild hedefleri gibi NuGet paket bağımlılıklarını içeren bir Bağımlılıklar klasörü oluşturur:

![Bağımlılıkları gösteren Çözüm Defteri](media/asp-net-core-image12.png)

### <a name="programcs"></a>Program.cs

Projenizdeki **Program.cs** dosyasını açın ve inceleyin. `Main` Yöntemde iki şeyin meydana geldiğini fark edin – uygulamanıza giriş:

```csharp
public static void Main(string[] args)
{
    var host = new WebHostBuilder()
        .UseKestrel()
        .UseContentRoot(Directory.GetCurrentDirectory())
        .UseIISIntegration()
        .UseStartup<Startup>()
        .Build();

    host.Run();
}
```

Bir ASP.NET Core uygulaması, bir ana bilgisayar aracını bir örnek üzerinden [`WebHostBuilder`](/aspnet/core/fundamentals/hosting)yapılandırarak ve başlatarak ana yöntemiyle bir web sunucusu oluşturur. Bu oluşturucu, ana bilgisayar yapılandırılmasına izin vermek için yöntemler sağlar. Şablon uygulamasında aşağıdaki yapılandırmalar kullanılır:

* `UseKestrel`: Kestrel sunucusunun uygulama tarafından kullanılacağını belirtir
* `UseContentRoot(Directory.GetCurrentDirectory())`: Uygulama bu klasörden başlatıldığında web projesinin kök klasörünü uygulamanın içerik kökü olarak kullanır
* `.UseIISIntegration()`: Uygulamanın IIS ile çalışması gerektiğini belirtir. IIS'yi ASP.NET Core `UseKestrel` `UseIISIntegration` ile kullanmak ve belirtilmesi gerekir.
* `.UseStartup<Startup>()`: Başlangıç sınıfını belirtir.

  Oluştur ve Çalıştır yöntemleri, uygulamayı barındıracak ve gelen HTTP isteklerini dinlemeye başlayacak Olan IWebHost'u oluşturur.

### <a name="startupcs"></a>Startup.cs

Uygulamanızın Başlangıç sınıfı, uygulamanın `UseStartup()` yönteminde `WebHostBuilder`belirtilir. İstek işleme ardışık hattını ve hizmetleri nerede yapılandırdığınızı bu sınıfta belirteceksiniz.

Projenizdeki **Startup.cs** dosyasını açın ve inceleyin:

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddConsole();

        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            await context.Response.WriteAsync("Hello World!");
        });
    }
}
```

Bu Başlangıç sınıfı her zaman aşağıdaki kurallara uymalıdır:

- Her zaman halka açık olmalı.
- Bu iki genel yöntem `ConfigureServices` içermelidir: ve`Configure`

Yöntem, `ConfigureServices` uygulamanız tarafından kullanılacak hizmetleri tanımlar.

`Configure` [Middleware](/aspnet/core/fundamentals/middleware)kullanarak istek ardışık oluşturmak için izin verir. Bunlar, istek ve yanıtları işlemek için ASP.NET bir uygulama ardışık alanı içinde kullanılan bileşenlerdir. HTTP ardışık hattı sırayla çağrılan bir dizi istek temsilcisinden oluşur. Her temsilci, isteğin kendisini işlemeyi veya bir sonraki temsilciye geçirmeyi seçebilir.

`Run`',`Map`ve `Use` metotlar , `IApplicationBuilder`üzerinde , kullanarak temsilcileri `Run` yapılandırabilirsiniz, ancak yöntem asla bir sonraki temsilci yi çağırmaz ve her zaman ardışık alanınızın sonunda kullanılmalıdır.

Önceden `Configure` oluşturulmuş şablonun yöntemi birkaç şey yapmak için oluşturulmuş. İlk olarak, geliştirme sırasında kullanılmak üzere bir özel durum işleme sayfasını yapılandırır. Daha sonra, basit bir "Hello World" ile isteyen web sayfasına bir yanıt gönderir.

Bu basit Merhaba, Dünya projesi artık ek bir kod eklenmeden çalıştırılabilir. Uygulamayı çalıştırmak ve tarayıcınızda görüntülemek için araç çubuğundaki Oynat (Üçgen) düğmesine basın:

![Uygulamayı Çalıştır](media/asp-net-core-image5.png)

Mac için Visual Studio, web projenizi başlatmak için rastgele bir bağlantı noktası kullanır. Bunun hangi bağlantı noktası olduğunu öğrenmek için, Görünüm **> Pads**altında listelenen Uygulama Çıktısını açın. Aşağıda gösterilene benzer çıktıları bulmalısınız:

![Dinleme bağlantı noktasını görüntüleyen Uygulama Çıktısı](media/asp-net-core-image6.png)

Seçtiğiniz tarayıcıyı açın ve `http://localhost:5000/`Uygulama Çıktısı'nda Visual Studio çıktısı portu `5000` ile değiştirerek girin. Metni `Hello World!`görmelisiniz:

![metni gösteren tarayıcı](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Denetleyici Ekleme

ASP.NET Çekirdek Uygulamalar, uygulamanın her bölümü için sorumlulukların mantıksal bir ayrımını sağlamak için Model-View-Controller (MVC) tasarım modelini kullanır. MVC aşağıdakilerden oluşur:

- **Model**: Uygulamanın verilerini temsil eden bir sınıf.
- **Görünüm**: Uygulamanın kullanıcı arabirimini (genellikle model verileri) görüntüler.
- **Denetleyici**: Tarayıcı isteklerini işleyen, kullanıcı girişine ve etkileşimine yanıt veren bir sınıftır.

MVC kullanımı hakkında daha fazla bilgi için [ASP.NET Core MVC kılavuzuna genel bakış](/aspnet/core/mvc/overview) bakın.

Denetleyici eklemek için aşağıdakileri yapın:

1. Proje adına sağ tıklayın ve **Yeni Dosyalar > ekle'yi**seçin. **Genel > Boş Sınıf'ı**seçin ve bir denetleyici adı girin:

    ![Yeni Dosya iletişim kutusu](media/asp-net-core-image8.png)

2. Yeni denetleyiciye aşağıdaki kodu ekleyin:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. Bağımlılık `Microsoft.AspNetCore.Mvc` klasörünü sağ tıklayarak ve Paket **Dependency** Ekle'yi seçerek projeye bağımlılık **ekleyin...**.

4. NuGet kitaplığına göz atmak için `Microsoft.AspNetCore.Mvc`Arama kutusunu kullanın ve Paket **Ekle'yi**seçin. Bu işlem birkaç dakika sürebilir ve gerekli bağımlılıklar için çeşitli lisansları kabul etmeniz istenebilir:

    ![Nuget Ekle](media/asp-net-core-image9.png)

5. Başlangıç sınıfında lambda'yı `app.Run` kaldırın ve MVC tarafından kullanılan URL yönlendirme mantığını aşağıdaki koda hangi koda çağırması gerektiğini belirlemek için ayarlayın:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Bu yönlendirme mantığını geçersiz kılacak gibi lambda kaldırmak `app.Run` için emin olun.

    MVC, hangi kodun çalıştırılacağını belirlemek için şeni kullanır:

    `/[Controller]/[ActionName]/[Parameters]`

    Yukarıdaki kod parçacığı eklediğinizde, uygulamanın `HelloWorld` Denetleyici'ye ve eylem yöntemine `Index` varsayılan olarak kaydetmesini söylersiniz.

6. `services.AddMvc();` Aramayı yönteme `ConfigureServices` ekleyin, aşağıda gösterildiği gibi:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Parametre bilgilerini URL'den denetleyiciye de aktarabilirsiniz.

7. Aşağıda gösterildiği gibi HelloWorldController'ınıza başka bir yöntem ekleyin:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Uygulamayı şimdi çalıştırıyorsanız, tarayıcınızı otomatik olarak açmalıdır:

    ![Uygulamayı tarayıcıda çalıştırma](media/asp-net-core-image13.png)

9. Göz atmaya çalışın `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (doğru `xxxx` bağlantı noktası ile değiştirerek), aşağıdakileri görmeniz gerekir:

    ![Bağımsız değişkenlerle tarayıcıda uygulama çalıştırma](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Sorun giderme

.NET Core'u Mac OS 10.11 (El Capitan) ve üzeri üzerine el ile yüklemeniz gerekiyorsa, aşağıdakileri yapın:

1. .NET Core'u yüklemeye başlamadan önce, tüm işletim sistemi güncelleştirmelerini en son kararlı sürüme güncelleştirdiğinizden emin olun. Bunu App Store uygulamasına giderek ve Güncellemeler sekmesini seçerek denetleyebilirsiniz.

2. [.NET Core sitesinde](https://www.microsoft.com/net/core#macos)listelenen adımları izleyin.

.NET Core'un başarıyla yüklendiğinden emin olmak için dört adımı da başarıyla tamamladığından emin olun.

## <a name="summary"></a>Özet

Bu kılavuz ASP.NET Core bir giriş verdi. Ne olduğunu, ne zaman kullanılacağını açıklar ve Mac için Visual Studio'da kullanma hakkında bilgi verirken.
Sonraki adımlar hakkında daha fazla bilgi için aşağıdaki kılavuzlara bakın:
- [ASP.NET Çekirdek](/aspnet/core/) dokümanları.
- Bir Xamarin.Forms uygulaması için ASP.NET Core kullanarak bir REST hizmeti oluşturmak için nasıl gösterir [Yerli Mobil Uygulamalar için Backend Hizmetleri oluşturma.](/aspnet/core/mobile/native-mobile-backend)
- [ASP.NET Core uygulamalı laboratuarı.](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]