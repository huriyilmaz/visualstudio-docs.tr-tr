---
title: ASP.NET Core Kullanmaya Başlama
description: bu makalede, yükleme ve yeni bir proje oluşturma dahil olmak üzere Mac için Visual Studio ASP.NET kullanmaya nasıl başlacağınız açıklanır.
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
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964752"
---
# <a name="getting-started-with-aspnet-core"></a>ASP.NET Core Kullanmaya Başlama

 Mac için Visual Studio, en son ASP.NET Core Web geliştirme platformuna yönelik desteğiyle uygulamanızın hizmetini geliştirmeyi kolaylaştırır. ASP.NET Core, .NET Framework ve çalışma zamanının en son gelişiminde .net Core üzerinde çalışır. Bu, hızlı performans, küçük yüklemeleri ve Linux ve macOS 'ta çalışmaya yönelik olarak, ayrıca Windows ve Linux 'ta çalışmaya yönelik olarak ayarlanmıştır.

## <a name="installing-net-core"></a>.NET Core yükleniyor

.net Core 3,1, Mac için Visual Studio yüklediğinizde otomatik olarak yüklenir. Mac için Visual Studio sürümünde desteklenen .net core sürümleri hakkında daha fazla bilgi için bkz. [.net core desteği](./net-core-support.md).

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Mac için Visual Studio ASP.NET Core uygulama oluşturma

Mac için Visual Studio açın. Başlangıç ekranında **yeni Project...** seçeneğini belirleyin.

![Yeni Proje İletişim Kutusu](media/asp-net-core-2019-new-asp-core.png)

bu işlem, yeni Project iletişim kutusunu görüntüleyecektir ve uygulamanızı oluşturmak için bir şablon seçmenizi sağlar.

ASP.NET Core uygulamanızı oluşturmaya başlamak için size önceden oluşturulmuş bir şablon sağlayacak bir dizi proje vardır. Bunlar:

- **.NET Core > boş**
- **.NET Core > API 'SI**
- **.NET Core > Web uygulaması**
- **.NET Core > Web uygulaması (Model-View-Controller)**
- **.NET Core > Blazor Server uygulaması**
- **.NET Core > Blazor WebAssembly uygulaması**

![ASP.NET Project seçenekleri](media/asp-net-core-2019-new-asp-core.png)

**boş ASP.NET Core Web uygulaması** ' nı seçin ve **ileri**' ye basın. Project bir ad verin ve **oluştur**' a basın. bu, yeni bir ASP.NET Core uygulaması oluşturur. Çözüm penceresinin sol bölmesinde, ikinci oku genişletin ve sonra **Başlangıç. cs**' yi seçin. Aşağıdaki görüntüye benzer görünmelidir:

![yeni ASP.NET Core boş Project görünümü](media/asp-net-core-2019-empty-project.png)

boş ASP.NET Core şablon, aşağıda açıklanan iki varsayılan dosya içeren bir web uygulaması oluşturur: **Program. cs** ve **Startup. cs**. ayrıca, projenin ASP.NET Core, .net Core framework ve projeyi oluşturan MSBuild hedefleri gibi NuGet paket bağımlılıklarını içeren bir bağımlılıklar klasörü de oluşturur:

![Bağımlılıkları görüntüleyen çözüm penceresi](media/asp-net-core-2019-solution-dependencies.png)

### <a name="programcs"></a>Program.cs

Projenizdeki **program. cs** dosyasını açın ve inceleyin. Yöntemde birkaç şeyin gerçekleşdiğine dikkat edin `Main` : uygulamanıza giriş:

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

bir ASP.NET Core uygulaması, bir örneği aracılığıyla ana bilgisayar yapılandırıp başlatarak ana yönteminde bir web sunucusu oluşturur [`WebHostBuilder`](/aspnet/core/fundamentals/hosting) . Bu Oluşturucu konağın yapılandırılmasına izin vermek için yöntemler sağlar. Şablon uygulamasında aşağıdaki yapılandırma kullanılır:

* `.UseStartup<Startup>()`: Başlangıç sınıfını belirtir.

Ancak, gibi ek konfigürasyonlar da ekleyebilirsiniz:

* `UseKestrel`: Uygulama tarafından kullanılacak Kestrel sunucusunu belirtir
* `UseContentRoot(Directory.GetCurrentDirectory())`: Uygulama bu klasörden başlatıldığında, uygulamanın içerik kökü olarak Web projesinin kök klasörünü kullanır
* `.UseIISIntegration()`: Uygulamanın IIS ile çalışması gerektiğini belirtir. ııs 'yi ASP.NET Core birlikte kullanmak `UseKestrel` ve `UseIISIntegration` belirtilmesi gerekir.

### <a name="startupcs"></a>Startup.cs

Uygulamanızın başlangıç sınıfı `UseStartup()` , üzerindeki yönteminde belirtilir `CreateWebHostBuilder` . Bu sınıf, istek işleme işlem hattını belirtmenizi ve herhangi bir hizmeti yapılandırdığınız yerdir.

Projenizdeki **Startup. cs** dosyasını açın ve inceleyin:

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

Bu başlangıç sınıfının her zaman aşağıdaki kurallara uyması gerekir:

- Her zaman ortak olmalıdır
- İki ortak yöntemi içermelidir: `ConfigureServices` ve `Configure`

`ConfigureServices`Yöntemi, uygulamanız tarafından kullanılacak hizmetleri tanımlar.

, `Configure` [Ara yazılımı](/aspnet/core/fundamentals/middleware)kullanarak istek işlem hattınızı oluşturmanıza olanak sağlar. bunlar, istekleri ve yanıtları işlemek için bir ASP.NET uygulama işlem hattı içinde kullanılan bileşenlerdir. HTTP işlem hattı, sırayla çağrılan bir dizi istek temsilcisinden oluşur. Her temsilci, isteğin kendisini işlemeye veya bir sonraki temsilciye geçirmeye seçim yapabilir.

,, Ve yöntemlerini kullanarak temsilcileri yapılandırabilirsiniz `Run` `Map` `Use` `IApplicationBuilder` , ancak `Run` Yöntem bir sonraki temsilciyi asla çağırmaz ve her zaman ardışık düzenin sonunda kullanılmalıdır.

`Configure`Önceden oluşturulmuş şablonun yöntemi birkaç şeyi yapmak üzere oluşturulmuştur. İlk olarak, geliştirme sırasında kullanılmak üzere bir özel durum işleme sayfasını yapılandırır. Daha sonra, istek yapan web sayfasına basit bir "Merhaba Dünya" ile yanıt gönderir.

Bu basit Merhaba, Dünya Projesi artık ek kod eklenmeksizin çalıştırılabilir. Uygulamayı çalıştırmak için, yürütme düğmesinin sağ açılır menüsünü kullanarak uygulamayı çalıştırmak istediğiniz tarayıcıyı seçebilir ya da varsayılan tarayıcınızı kullanmak için yalnızca Oynat (üç taraflı) düğmesine basabilirsiniz:

![Tarayıcı çalıştırması](media/asp-net-web-picker.png)

Mac için Visual Studio, web projenizi başlatmak için rastgele bir bağlantı noktası kullanır. bu bağlantı noktasını öğrenmek için, **görünüm > diğer Windows** menüsünden listelenen uygulama çıktısını açın. Aşağıdakine benzer bir çıktıyı aşağıda gösterildiği gibi bulmalısınız:

![Dinleme bağlantı noktasını görüntüleyen uygulama çıkışı](media/asp-net-core-image6.png)

Proje çalışmaya başladıktan sonra varsayılan Web tarayıcınız, uygulama çıkışında listelenen URL 'yi başlatıp bağlantı etmelidir. alternatif olarak, istediğiniz herhangi bir tarayıcıyı açabilir ve `http://localhost:5000/` öğesini, `5000` uygulama çıkışında çıktı Visual Studio bağlantı noktası ile değiştirerek yazabilirsiniz. Şu metni görmeniz gerekir `Hello World!` :

![metin gösteren tarayıcı](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Denetleyici Ekleme

ASP.NET Core Uygulamalar, uygulamanın her bir bölümü için bir sorumluluk için bir mantık ayrımı sağlamak üzere Model-View-Controller (MVC) tasarım modelini kullanır. MVC tasarım stili aşağıdaki kavramlardan oluşur:

- **Model**: uygulamanın verilerini temsil eden bir sınıf.
- **Görünüm**: uygulamanın kullanıcı arabirimini (genellikle model verileri) görüntüler.
- **Denetleyici**: Tarayıcı isteklerini işleyen, kullanıcı girişine ve etkileşime yanıt veren bir sınıf.

mvc kullanma hakkında daha fazla bilgi için [ASP.NET Core MVC kılavuzuna genel bakış](/aspnet/core/mvc/overview) bölümüne bakın.

Bir denetleyici eklemek için aşağıdakileri yapın:

1. Project adına sağ tıklayın ve **> yeni dosya ekle**' yi seçin. **Genel > boş sınıfı**' nı seçin ve bir denetleyici adı girin:

    ![Yeni dosya iletişim kutusu](media/asp-net-core-image8.png)

2. Aşağıdaki kodu yeni denetleyiciye ekleyin:

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

3. Bağımlılık `Microsoft.AspNetCore.Mvc` klasörüne sağ tıklayıp **paket Ekle...** seçeneğini belirleyerek  bağımlılığı projeye ekleyin.

4. için NuGet kitaplığına gitmek için arama kutusunu kullanın `Microsoft.AspNetCore.Mvc` ve **paket ekle**' yi seçin. Bu işlem birkaç dakika sürebilir ve gerekli bağımlılıklar için çeşitli lisanslar kabul etmeniz istenebilir:

    ![NuGet Ekle](media/asp-net-core-image9.png)

5. Başlangıç sınıfında, lambda 'yi kaldırın `app.Run` ve MVC tarafından aşağıdaki için hangi kodun çağrılmasını gerektiğini öğrenmek için kullanılan URL yönlendirme mantığını ayarlayın:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    `app.Run`Bu, yönlendirme mantığını geçersiz kılacaktır, lambda 'yi kaldırdığınızdan emin olun.

    MVC, hangi kodun çalıştırılacağını anlamak için aşağıdaki biçimi kullanır:

    `/[Controller]/[ActionName]/[Parameters]`

    Yukarıdaki kod parçacığını eklediğinizde, uygulamanın denetleyiciye varsayılan olarak `HelloWorld` ve eylem yöntemine söylemiş olursunuz `Index` .

6. `services.AddMvc();` `ConfigureServices` Aşağıdaki gösterildiği gibi yöntemine çağrı ekleyin:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Ayrıca, URL 'den denetleyiciye parametre bilgilerini geçirebilirsiniz.

7. Merhaba Dünya denetleyicinize aşağıda gösterildiği gibi başka bir yöntem ekleyin:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Uygulamayı şimdi çalıştırırsanız, tarayıcınızı otomatik olarak açması gerekir:

    ![Uygulamayı tarayıcıda çalıştırma](media/asp-net-core-image13.png)

9. Gözatmaya `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` ( `xxxx` doğru bağlantı noktasıyla değiştirme) çalışırsanız, aşağıdakileri görmeniz gerekir:

    ![Uygulama, bağımsız değişkenlerle tarayıcıda çalıştırılıyor](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Sorun giderme

MacOS 10,12 (Sierra) ve üzeri sürümlerde .NET Core 'u el ile yüklemeniz gerekiyorsa şunları yapın:

1. .NET Core'u yüklemeye başlamadan önce tüm işletim sistemi güncelleştirmelerini en son kararlı sürüme güncelleştirilmiş olduğundan emin olun. Bunu kontrol etmek için App Store ve Güncelleştirmeler sekmesini seçin.

2. .NET Core sitesinde [listelenen adımları izleyin.](https://www.microsoft.com/net/core#macos)

.NET Core'ın başarıyla yüklü olduğundan emin olmak için tüm adımları başarıyla tamamlayın.

## <a name="summary"></a>Özet

Bu kılavuzda, ASP.NET Core. Bu, ne olduğunu, ne zaman kullanıcalarını açıklar ve veri kaynaklarında kullanma hakkında Mac için Visual Studio.
Sonraki adımlar hakkında daha fazla bilgi için aşağıdaki kılavuzlara bakın:
- [ASP.NET Core](/aspnet/core/) belgeleri.
- [Yerel Mobil Uygulamalar için Arka](/aspnet/core/mobile/native-mobile-backend)Uç Hizmetleri oluşturma. Bu, Xamarin.Forms uygulaması için ASP.NET Core rest hizmeti oluşturmayı gösterir.
- [ASP.NET Core bir laboratuvar.](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]