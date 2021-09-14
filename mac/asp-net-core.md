---
title: ASP.NET Core Kullanmaya Başlama
description: Bu makalede, yükleme ve yeni proje oluşturma ASP.NET Mac için Visual Studio'da Mac için Visual Studio ile çalışmaya başlama işlemi açıklanmıştır.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/06/2020
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: a2f45069967df412f9245f8044c53ef425a00fdf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725998"
---
# <a name="getting-started-with-aspnet-core"></a>ASP.NET Core Kullanmaya Başlama

 Mac için Visual Studio, en yeni web geliştirme platformu desteğiyle uygulama hizmetinizi geliştirmenizi ASP.NET Core kolaylaştırır. ASP.NET Core .NET Core'da çalışır ve çalışma zamanı için en .NET Framework evrimi. Hızlı performans için ayarlanmıştır, küçük yükleme boyutlarına göre ayarlanmıştır ve Linux ve macOS üzerinde çalıştıracak şekilde yeniden tasarlanmıştır ve Windows.

## <a name="installing-net-core"></a>.NET Core'u yükleme

.NET Core 3.1, yükleme sırasında otomatik olarak Mac için Visual Studio. 'de desteklenen .NET Core sürümleri hakkında daha fazla bilgi Mac için Visual Studio bkz. [.NET Core Desteği.](./net-core-support.md)

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Mac için Visual Studio'ASP.NET Core uygulama oluşturma

Yeni Mac için Visual Studio. Başlangıç Ekranında Yeni Ekran... **Project**

![Yeni Proje İletişim Kutusu](media/asp-net-core-2019-new-asp-core.png)

Bu işlemde Yeni Project iletişim kutusu görüntülenir ve bu iletişim kutusu, uygulamanızı oluşturmak için bir şablon seçmenize olanak sağlar.

ASP.NET Core Application projenizi oluşturmak için önceden hazır bir şablon sağlayacak birkaç proje vardır. Bunlar:

- **.NET Core > Boş**
- **.NET Core > API'si**
- **.NET Core > Web Uygulaması**
- **.NET Core > Web Uygulaması (Model-View-Controller)**
- **.NET Core > Blazor Server Uygulaması**
- **.NET Core > Blazor WebAssembly Uygulaması**

![ASP.NET Project Seçenekleri](media/asp-net-core-2019-new-asp-core.png)

Boş **Web ASP.NET Core seçin ve Ardından** tuşuna **basın.** Adına Project Oluştur'a **basın.** Bu, yeni bir ASP.NET Core oluşturur. Çözüm penceresinin sol bölmesinde ikinci oku genişletin ve **Startup.cs'yi seçin.** Aşağıdaki görüntüye benzer şekilde görüntülenmiştir:

![Yeni ASP.NET Core Boş Project görünümü](media/asp-net-core-2019-empty-project.png)

Boş ASP.NET Core şablonu iki varsayılan dosyayla bir web uygulaması oluşturur: **Program.cs** ve **Startup.cs**, aşağıda açıklanmıştır. Ayrıca projenizin ASP.NET Core, .NET Core çerçevesi ve projeyi oluşturan MSBuild hedeflerini içeren NuGet paketi bağımlılıklarını içeren bir Dependencies klasörü oluşturur:

![Bağımlılıkları görüntüleyen çözüm penceresi](media/asp-net-core-2019-solution-dependencies.png)

### <a name="programcs"></a>Program.cs

Projenizin **Program.cs dosyasını** açın ve inceler. yönteminde birkaç şey `Main` (uygulamanıza giriş) olduğunu fark edin:

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

Bir ASP.NET Core uygulaması, bir örneği aracılığıyla bir konak yapılandırarak ve başlatarak ana yönteminde bir web sunucusu [`WebHostBuilder`](/aspnet/core/fundamentals/hosting) oluşturur. Bu oluşturucu, ana bilgisayar yapılandırılmasına izin vermek için yöntemler sağlar. Şablon uygulamasında aşağıdaki yapılandırmalar kullanılır:

* `.UseStartup<Startup>()`: Başlangıç sınıfını belirtir.

Bununla birlikte, aşağıdakiler gibi ek yapılandırmalar da ebilirsiniz:

* `UseKestrel`: Uygulama tarafından kullanılacak Kestrel sunucusunu belirtir
* `UseContentRoot(Directory.GetCurrentDirectory())`: Web projesinin kök klasörünü, uygulama bu klasörden başlatılana kadar uygulamanın içerik kökü olarak kullanır
* `.UseIISIntegration()`: Uygulamanın IIS ile çalışması gerektiğini belirtir. IIS'yi hem ASP.NET Core hem `UseKestrel` de ile kullanmak için `UseIISIntegration` belirtilmelidir.

### <a name="startupcs"></a>Startup.cs

Uygulamanıza için Başlangıç sınıfı, üzerinde `UseStartup()` yönteminde `CreateWebHostBuilder` belirtilir. Bu sınıfta, istek işleme işlem hattını ve hizmetleri nerede yapılandıracaklarını belirteceksiniz.

Projenizin **Startup.cs dosyasını** açın ve inceler:

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

Bu Başlangıç sınıfının her zaman aşağıdaki kurallara uyması gerekir:

- Her zaman genel olması gerekir
- İki genel yöntemi içermesi gerekir: `ConfigureServices` ve `Configure`

`ConfigureServices`yöntemi, uygulama tarafından kullanılacak hizmetleri tanımlar.

, `Configure` Ara Yazılım kullanarak istek işlem hattınızı [oluşturmanızı sağlar.](/aspnet/core/fundamentals/middleware) Bunlar, istekleri ve yanıtları işlemek ASP.NET bir uygulama işlem hattında kullanılan bileşenlerdir. HTTP işlem hattı, sırasıyla çağrılan bir dizi istek temsilcisini içerir. Her temsilci isteğin kendisini işlemeyi veya bir sonraki temsilciye geçmeyi seçebilir.

üzerinde , ve yöntemlerini kullanarak temsilcileri yapılandırebilirsiniz, ancak yöntemi hiçbir zaman bir sonraki temsilciyi çağırmaz ve her zaman işlem `Run` `Map` `Use` `IApplicationBuilder` `Run` hattınız sonunda kullanılmalıdır.

Önceden `Configure` yapılmış şablonun yöntemi, birkaç işlem yapmak için hazır edilmiştir. İlk olarak, geliştirme sırasında kullanmak üzere bir özel durum işleme sayfası yapılandırıyor. Ardından, istekte bulunan web sayfasına basit bir "Merhaba Dünya" gönderir.

Bu basit Merhaba Dünya projesi artık ek kod eklenmeden çalıştırabilir. Uygulamayı çalıştırmak için, oynat düğmesinin sağ üst açılan listesinden uygulamayı çalıştırmak istediğiniz tarayıcıyı seçin veya varsayılan tarayıcınızı kullanmak için Oynat (üçgen) düğmesine basabilirsiniz:

![Tarayıcı Çalıştırma](media/asp-net-web-picker.png)

Mac için Visual Studio web projenizi başlatmak için rastgele bir bağlantı noktası kullanır. Bu bağlantı noktasının ne olduğunu bulmak için Görünüm ve Diğer Girişler menüsünün altında **> Uygulama Windows** açın. Aşağıda gösterilene benzer bir çıkış bulmalısiniz:

![Dinleme bağlantı noktasını görüntüleyen Uygulama Çıkışı](media/asp-net-core-image6.png)

Proje çalıştırılana kadar varsayılan web tarayıcınızın başlatılması ve Uygulama Çıktısı'da listelenen URL'ye bağlanması gerekir. Alternatif olarak, tercih edin herhangi bir tarayıcıyı açabilir ve girerek yerine Uygulama Çıkışı'Visual Studio `http://localhost:5000/` `5000` bağlantı noktasını girebilirsiniz. metnini görüyor `Hello World!` gerekir:

![metin gösteren tarayıcı](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Denetleyici Ekleme

ASP.NET Core Uygulamalar, uygulamanın her parçası için mantıksal bir sorumluluk ayrımı sağlamak üzere Model-View-Controller (MVC) tasarım desenini kullanır. MVC tasarım deseni aşağıdaki kavramlardan oluşur:

- **Model:** Uygulamanın verilerini temsil eden bir sınıf.
- **Görünüm:** Uygulamanın kullanıcı arabirimini (genellikle model verileridir) görüntüler.
- **Denetleyici:** Tarayıcı isteklerini ele alan, kullanıcı girişine ve etkileşimine yanıt veren bir sınıf.

MVC kullanma hakkında daha fazla bilgi için [bkz. MVC ASP.NET Core](/aspnet/core/mvc/overview) genel bakış.

Denetleyici eklemek için şunları yapın:

1. Yeni dosya adına sağ tıklayın Project Yeni **Dosyalar'a >'yi seçin.** Genel **sınıf > Boş Sınıf'ı** seçin ve bir denetleyici adı girin:

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

3. Bağımlılık `Microsoft.AspNetCore.Mvc` klasörüne sağ tıklar ve  Paket Ekle... öğesini seçerek bağımlılığı **projeye ekleyin.**

4. arama kutusunu kullanarak için NuGet kitaplığına göz atabilir `Microsoft.AspNetCore.Mvc` ve Paket **Ekle'yi seçin.** Bu yükleme birkaç dakika sürebilir ve gerekli bağımlılıklar için çeşitli lisansları kabul etme istendiğinde:

    ![Nuget ekleme](media/asp-net-core-image9.png)

5. Başlangıç sınıfında, lambda'yı kaldırın ve aşağıdaki koda çağıran kodu belirlemek için MVC tarafından `app.Run` kullanılan URL yönlendirme mantığını ayarlayın:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Yönlendirme mantığını geçersiz `app.Run` kılacak olduğundan lambda'yı kaldırarak emin olun.

    MVC, çalıştıracak kodu belirlemek için aşağıdaki biçimi kullanır:

    `/[Controller]/[ActionName]/[Parameters]`

    Yukarıdaki kod parçacığını eklerken, uygulamaya varsayılan olarak Controller'a ve `HelloWorld` eylem yöntemine `Index` söylemeniz gerekir.

6. Aşağıda `services.AddMvc();` gösterildiği gibi `ConfigureServices` yöntemine çağrıyı ekleyin:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Parametre bilgilerini URL'den denetleyiciye de geçebilirsiniz.

7. Aşağıda gösterildiği gibi HelloWorldController'nıza başka bir yöntem ekleyin:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Uygulamayı şimdi çalıştırdıysanız otomatik olarak tarayıcınızı açması gerekir:

    ![Uygulamayı tarayıcıda çalıştırma](media/asp-net-core-image13.png)

9. 'a göz `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` atmaya (yerine `xxxx` doğru bağlantı noktasını değiştirmeyi) deneyin; aşağıdakilere bakın:

    ![Uygulamayı bağımsız değişkenlerle tarayıcıda çalıştırma](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Sorun giderme

macOS 10.12 (Sierra) ve sonraki bir sürümüne .NET Core'u el ile yüklemeniz gerekirse, şunları yapın:

1. .NET Core'u yüklemeye başlamadan önce tüm işletim sistemi güncelleştirmelerini en son kararlı sürüme güncelleştirilmiş olduğundan emin olun. Bunu kontrol etmek için App Store ve Güncelleştirmeler sekmesini seçin.

2. .NET Core sitesinde [listelenen adımları izleyin.](https://www.microsoft.com/net/core#macos)

.NET Core'ın başarıyla yüklü olduğundan emin olmak için tüm adımları başarıyla tamamlayın.

## <a name="summary"></a>Özet

Bu kılavuzda, ASP.NET Core. Bu, ne olduğunu, ne zaman kullanıLL'nin ne zaman olduğunu açıklar ve Mac için Visual Studio.
Sonraki adımlar hakkında daha fazla bilgi için aşağıdaki kılavuzlara bakın:
- [ASP.NET Core](/aspnet/core/) belgeleri.
- [Yerel Mobil Uygulamalar için Arka](/aspnet/core/mobile/native-mobile-backend)Uç Hizmetleri oluşturma, Xamarin.Forms uygulaması için ASP.NET Core rest hizmeti oluşturmayı gösterir.
- [ASP.NET Core bir laboratuvar.](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]