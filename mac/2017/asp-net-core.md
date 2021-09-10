---
title: ASP.NET Core Kullanmaya Başlama
description: Bu makalede, yükleme ve yeni bir proje ASP.NET dahil Mac için Visual Studio'da Mac için Visual Studio ile çalışmaya başlama işlemi açıklanmıştır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/13/2017
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 2e921ac1e9c85216bebf1626e1454b9fb764f129
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962073"
---
# <a name="getting-started-with-aspnet-core"></a>ASP.NET Core Kullanmaya Başlama

 Mac için Visual Studio, en yeni web geliştirme platformu desteğiyle uygulama hizmetinizi geliştirmenizi ASP.NET Core kolaylaştırır. ASP.NET Core .NET Core'da çalışır. Bu, .NET Framework çalışma zamanıdır. Hızlı performans için ayarlanmıştır, küçük yükleme boyutlarına göre ayarlanmıştır ve Linux ve macOS üzerinde çalıştıracak şekilde yeniden tasarlanmıştır ve Windows.

## <a name="installing-net-core"></a>.NET Core'u yükleme

.NET Core 1.1, yükleme sırasında otomatik olarak Mac için Visual Studio.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Mac için Visual Studio'ASP.NET Core bir Mac için Visual Studio

Yeni Mac için Visual Studio. Hoş geldiniz sayfasında Yeni **Giriş... Project.**

![Yeni Proje İletişim Kutusu](media/asp-net-core-image1.png)

Bu işlemde Yeni Project iletişim kutusu görüntülenir ve bu iletişim kutusu, uygulamanızı oluşturmak için bir şablon seçmenize olanak sağlar.

ASP.NET Core Application projenizi oluşturmak için önceden hazır bir şablon sağlayacak birkaç proje vardır. Bunlar:

- **.NET Core > ASP.NET Core Boş Web Uygulaması**
- **.NET Core > ASP.NET Core Web Uygulaması**
- **.NET Core > ASP.NET Core Web API'si**
- **Çok platformlu > App > Bağlı Uygulama**

![ASP.NET Project Seçenekleri](media/asp-net-core-image11.png)

Boş **Web ASP.NET Core seçin ve Ardından** tuşuna **basın.** Kullanıcıya bir Project ve Oluştur'a **basın.** Bu, ASP.NET Core aşağıdaki görüntüye benzer olması gereken yeni bir uygulama oluşturur:

![Yeni ASP.NET Core Boş Project görünümü](media/asp-net-core-image4.png)

Boş ASP.NET Core Uygulaması iki varsayılan dosyayla bir web uygulaması oluşturur: **Program.cs** ve **Startup.cs**, aşağıda açıklanmıştır. Ayrıca projenizin ASP.NET Core, .NET Core çerçevesi ve projeyi oluşturan MSBuild gibi NuGet paketi bağımlılıklarını içeren bir Dependencies klasörü oluşturur:

![Çözüm Bölmesi görüntüleme](media/asp-net-core-image12.png)

### <a name="programcs"></a>Program.cs

Projenizin **Program.cs dosyasını** açın ve inceler. yönteminde iki şeyin `Main` (uygulamanıza giriş) olduğunu fark edin:

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

Bir ASP.NET Core uygulaması, bir örneği aracılığıyla bir konak yapılandırarak ve başlatarak ana yönteminde bir web sunucusu [`WebHostBuilder`](/aspnet/core/fundamentals/hosting) oluşturur. Bu oluşturucu, ana bilgisayar yapılandırılmasına izin vermek için yöntemler sağlar. Şablon uygulamasında aşağıdaki yapılandırmalar kullanılır:

* `UseKestrel`: Uygulama tarafından kullanılacak Kestrel sunucusunu belirtir
* `UseContentRoot(Directory.GetCurrentDirectory())`: Web projesinin kök klasörünü, uygulama bu klasörden başlatılana kadar uygulamanın içerik kökü olarak kullanır
* `.UseIISIntegration()`: Uygulamanın IIS ile çalışması gerektiğini belirtir. IIS'yi her ASP.NET Core `UseKestrel` ve `UseIISIntegration` ile birlikte kullanmak için belirtilmelidir.
* `.UseStartup<Startup>()`: Başlangıç sınıfını belirtir.

  Derleme ve Çalıştırma yöntemleri, uygulamayı barındıracak ve gelen HTTP isteklerini dinlemeyi başlatacak IWebHost'u derleme.

### <a name="startupcs"></a>Startup.cs

Uygulamanıza için Başlangıç sınıfı, üzerinde `UseStartup()` yönteminde `WebHostBuilder` belirtilir. Bu sınıfta, istek işleme işlem hattını ve hizmetleri nerede yapılandıracaklarını belirteceksiniz.

Projenizin **Startup.cs dosyasını** açın ve inceler:

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

Bu Başlangıç sınıfının her zaman aşağıdaki kurallara uyması gerekir:

- Her zaman genel olması gerekir
- İki genel yöntemi içermesi gerekir: `ConfigureServices` ve `Configure`

`ConfigureServices`yöntemi, uygulama tarafından kullanılacak hizmetleri tanımlar.

, `Configure` Ara Yazılım kullanarak istek işlem hattınızı [oluşturmanızı sağlar.](/aspnet/core/fundamentals/middleware) Bunlar, istekleri ve yanıtları işlemek ASP.NET bir uygulama işlem hattında kullanılan bileşenlerdir. HTTP işlem hattı sırasıyla çağrılan bir dizi istek temsilcisi içerir. Her temsilci isteğin kendisini işlemeyi veya bir sonraki temsilciye geçmeyi seçebilir.

üzerinde , ve yöntemlerini kullanarak temsilcileri yapılandırebilirsiniz, ancak yöntemi hiçbir zaman bir sonraki temsilciyi çağırmaz ve her zaman işlem `Run` `Map` `Use` `IApplicationBuilder` `Run` hattınız sonunda kullanılmalıdır.

Önceden `Configure` yapılmış şablonun yöntemi, birkaç işlem yapmak için hazır edilmiştir. İlk olarak, geliştirme sırasında kullanmak üzere bir özel durum işleme sayfası yapılandırıyor. Ardından, istekte bulunan web sayfasına basit bir "Merhaba Dünya.

Bu basit Merhaba Dünya projesi artık ek kod eklenmeden çalıştırabilir. Uygulamayı çalıştırmak ve tarayıcınızda görüntülemek için araç çubuğundaki Oynat (Üçgen) düğmesine basın:

![Uygulamayı Çalıştır](media/asp-net-core-image5.png)

Mac için Visual Studio web projenizi başlatmak için rastgele bir bağlantı noktası kullanır. Bu bağlantı noktasının ne olduğunu bulmak için Görünüm ve Giriş Paneli altında listelenen **Uygulama > açın.** Aşağıda gösterilene benzer bir çıkış bulmalısiniz:

![Dinleme bağlantı noktasını görüntüleyen Uygulama Çıkışı](media/asp-net-core-image6.png)

Tercih tarayıcınızı açın ve girin ve yerine Uygulama Çıkışı'Visual Studio `http://localhost:5000/` `5000` bağlantı noktasını girin. metnini görüyor `Hello World!` gerekir:

![metin gösteren tarayıcı](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Denetleyici Ekleme

ASP.NET Core Uygulamalar, uygulamanın her parçası için mantıksal bir sorumluluk ayrımı sağlamak üzere Model-View-Controller (MVC) tasarım desenini kullanır. MVC aşağıdakilerden oluşur:

- **Model:** Uygulamanın verilerini temsil eden bir sınıf.
- **Görünüm:** Uygulamanın kullanıcı arabirimini (genellikle model verileridir) görüntüler.
- **Denetleyici:** Tarayıcı isteklerini ele alan, kullanıcı girişine ve etkileşimine yanıt veren bir sınıf.

MVC kullanma hakkında daha fazla bilgi için [bkz. MVC ASP.NET Core genel](/aspnet/core/mvc/overview) bakış.

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

5. Başlangıç sınıfında, lambda'yı kaldırın ve aşağıdaki koda çağıran kodu belirlemek için `app.Run` MVC tarafından kullanılan URL yönlendirme mantığını ayarlayın:

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

10.11 (El Capitan) ve sonraki bir sürümüne .NET Core'Mac OS el ile yüklemeniz gerekirse, şunları yapın:

1. .NET Core'u yüklemeye başlamadan önce tüm işletim sistemi güncelleştirmelerini en son kararlı sürüme güncelleştirilmiş olduğundan emin olun. Bunu kontrol etmek için App Store ve Güncelleştirmeler sekmesini seçin.

2. .NET Core sitesinde [listelenen adımları izleyin.](https://www.microsoft.com/net/core#macos)

.NET Core'ın başarıyla yüklü olduğundan emin olmak için dört adımın da başarıyla tamamlandığından emin olun.

## <a name="summary"></a>Özet

Bu kılavuzda, ASP.NET Core. ne olduğunu, ne zaman kullanılacağını ve Mac için Visual Studio ' de kullanma hakkında bilgi sağlandığını açıklar.
Buradaki sonraki adımlar hakkında daha fazla bilgi için aşağıdaki kılavuzlara bakın:
- belgeleri [ASP.NET Core](/aspnet/core/) .
- [yerel mobil uygulamalar için arka uç hizmetleri oluşturma](/aspnet/core/mobile/native-mobile-backend), bir Xamarin. Forms uygulaması için ASP.NET Core kullanarak REST hizmeti oluşturmayı gösterir.
- [uygulamalı laboratuvar ASP.NET Core](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]