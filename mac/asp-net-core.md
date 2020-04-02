---
title: ASP.NET Core Kullanmaya Başlama
description: Bu makalede, yükleme ve yeni bir proje oluşturma da dahil olmak üzere Visual Studio for Mac'te ASP.NET nasıl başlasınız açıklanmaktadır.
author: sayedihashimi
ms.author: sayedha
ms.date: 04/02/2019
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.openlocfilehash: cfe7e7f852530c32efbbaec2fbc92060fadeb40e
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543894"
---
# <a name="getting-started-with-aspnet-core"></a>ASP.NET Core Kullanmaya Başlama

 Mac için Visual Studio, en son ASP.NET Core Web geliştirme platformuna verdiği destekle uygulamanızın hizmetini geliştirmenizi kolaylaştırır. ASP.NET Core, .NET Framework ve çalışma zamanının en son evrimi olan .NET Core'da çalışır. Hızlı performans için ayarlanmış, küçük yükleme boyutları için faktörlü ve Linux ve macOS yanı sıra Windows üzerinde çalıştırmak için yeniden tasarlandı.

## <a name="installing-net-core"></a>.NET Core kurulumu

.NET Core 2.1, Mac için Visual Studio'yı yüklediğinizde otomatik olarak yüklenir.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Mac için Visual Studio'da ASP.NET Core uygulaması oluşturma

Mac için Visual Studio'u açın. Başlangıç Ekranında **Yeni Proje'yi seçin...**

![Yeni Proje İletişim Kutusu](media/asp-net-core-2019-new-asp-core.png)

Bu, Uygulamanızı oluşturmak için bir şablon seçmenize olanak tanıyan Yeni Proje iletişim kutusunu görüntüler.

ASP.NET Çekirdek Uygulamanızı oluşturmaya başlamak için önceden oluşturulmuş bir şablon sağlayacak bir dizi proje vardır. Bunlar:

- **.NET Çekirdek > Boş**
- **.NET Çekirdek > API**
- **.NET Çekirdek > Web Uygulaması**
- **.NET Çekirdek > Web Uygulaması (Model-Görünüm-Denetleyici)**

![ASP.NET Proje Seçenekleri](media/asp-net-core-2019-new-asp-core.png)

ASP.NET **Çekirdek Boş Web Uygulaması'nı** seçin ve **İleri**tuşuna basın. Projeye Bir Ad Verin ve **Oluştur'a**basın. Bu, yeni bir ASP.NET Core uygulaması oluşturur. Çözüm defterinin sol bölmesinde, ikinci oku genişletin ve ardından **Startup.cs**seçin. Aşağıdaki resme benzer görünmelidir:

![Yeni ASP.NET Çekirdek Boş Proje görünümü](media/asp-net-core-2019-empty-project.png)

ASP.NET Core Empty şablonu iki varsayılan dosyaiçeren bir web uygulaması oluşturur: **Program.cs** ve **Startup.cs**, aşağıda açıklanmıştır. Ayrıca, projenizin ASP.NET Core, .NET Core çerçevesi ve projeyi oluşturan MSBuild hedefleri gibi NuGet paket bağımlılıklarını içeren bir Bağımlılıklar klasörü oluşturur:

![Bağımlılıkları gösteren Çözüm Defteri](media/asp-net-core-2019-solution-dependencies.png)

### <a name="programcs"></a>Program.cs

Projenizdeki **Program.cs** dosyasını açın ve inceleyin. `Main` Yöntemde birkaç şeyin meydana geldiğini fark edin – uygulamanıza giriş:

```csharp
    public class Program
    {
        public static void Main(string[] args)
        {
            CreateWebHostBuilder(args).Build().Run();
        }

        public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>();
    }
```

Bir ASP.NET Core uygulaması, bir ana bilgisayar aracını bir örnek üzerinden [`WebHostBuilder`](/aspnet/core/fundamentals/hosting)yapılandırarak ve başlatarak ana yöntemiyle bir web sunucusu oluşturur. Bu oluşturucu, ana bilgisayar yapılandırılmasına izin vermek için yöntemler sağlar. Şablon uygulamasında aşağıdaki yapılandırmalar kullanılır:

* `.UseStartup<Startup>()`: Başlangıç sınıfını belirtir.

Ancak, şu gibi ek yapılandırmalar da ekleyebilirsiniz:

* `UseKestrel`: Kestrel sunucusunun uygulama tarafından kullanılacağını belirtir
* `UseContentRoot(Directory.GetCurrentDirectory())`: Uygulama bu klasörden başlatıldığında web projesinin kök klasörünü uygulamanın içerik kökü olarak kullanır
* `.UseIISIntegration()`: Uygulamanın IIS ile çalışması gerektiğini belirtir. IIS'yi ASP.NET Core `UseKestrel` `UseIISIntegration` ile kullanmak ve belirtilmesi gerekir.

### <a name="startupcs"></a>Startup.cs

Uygulamanızın Başlangıç sınıfı, uygulamanın `UseStartup()` yönteminde `CreateWebHostBuilder`belirtilir. İstek işleme ardışık hattını ve hizmetleri nerede yapılandırdığınızı bu sınıfta belirteceksiniz.

Projenizdeki **Startup.cs** dosyasını açın ve inceleyin:

```csharp
    public class Startup
    {
        // This method gets called by the runtime. Use this method to add services to the container.
        // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
        public void ConfigureServices(IServiceCollection services)
        {
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IHostingEnvironment env)
        {
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

Bu basit Merhaba, Dünya projesi artık ek bir kod eklenmeden çalıştırılabilir. Uygulamayı çalıştırmak için, Uygulamayı Oynatma düğmesinin açılır hakkını kullanarak çalıştırmak istediğiniz tarayıcıyı seçebilir veya varsayılan tarayıcınızı kullanmak için Oynat (üçgen) düğmesine basabilirsiniz:

![Tarayıcı Çalıştır](media/asp-net-web-picker.png)

Mac için Visual Studio, web projenizi başlatmak için rastgele bir bağlantı noktası kullanır. Bunun hangi bağlantı noktası olduğunu öğrenmek için, Görünüm **> Pads**altında listelenen Uygulama Çıktısını açın. Aşağıda gösterilene benzer çıktıları bulmalısınız:

![Dinleme bağlantı noktasını görüntüleyen Uygulama Çıktısı](media/asp-net-core-image6.png)

Proje çalışmaya başladıktan sonra, varsayılan web tarayıcınız Uygulama Çıktısı'nda listelenen URL'yi başlatıp bağlanmalıdır. Alternatif olarak, seçtiğiniz herhangi bir tarayıcıyı `http://localhost:5000/`açabilir ve `5000` Uygulama Çıktısı'ndaki Visual Studio çıkışının yerine, istediğiniz bağlantı noktasını girebilirsiniz. Metni `Hello World!`görmelisiniz:

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

.NET Core'u Mac OS 10.12 (Sierra) ve üstü üzerine el ile yüklemeniz gerekiyorsa, aşağıdakileri yapın:

1. .NET Core'u yüklemeye başlamadan önce, tüm işletim sistemi güncelleştirmelerini en son kararlı sürüme güncelleştirdiğinizden emin olun. Bunu App Store uygulamasına giderek ve Güncellemeler sekmesini seçerek denetleyebilirsiniz.

2. [.NET Core sitesinde](https://www.microsoft.com/net/core#macos)listelenen adımları izleyin.

.NET Core'un başarıyla yüklendiğinden emin olmak için tüm adımları başarıyla tamamladığından emin olun.

## <a name="summary"></a>Özet

Bu kılavuz ASP.NET Core bir giriş verdi. Ne olduğunu, ne zaman kullanılacağını açıklar ve Mac için Visual Studio'da kullanma hakkında bilgi verirken.
Sonraki adımlar hakkında daha fazla bilgi için aşağıdaki kılavuzlara bakın:
- [ASP.NET Çekirdek](/aspnet/core/?view=aspnetcore-2.1) dokümanları.
- Bir Xamarin.Forms uygulaması için ASP.NET Core kullanarak bir REST hizmeti oluşturmak için nasıl gösterir [Yerli Mobil Uygulamalar için Backend Hizmetleri oluşturma.](/aspnet/core/mobile/native-mobile-backend)
- [ASP.NET Core uygulamalı laboratuarı.](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]
