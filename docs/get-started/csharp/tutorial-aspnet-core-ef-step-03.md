---
title: '3. Adım: ASP.NET Çekirdek Uygulamanızdaki Verilerle Çalışma'
description: Bu video eğitimi ve adım adım talimatlarla ASP.NET Core Web Uygulamanızda Entity Framework Core'u kullanarak verilerle çalışmaya başlayın.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: cef0db7e5615d08fb5b22c38604a24124c853ebd
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580071"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Adım 3: Varlık Çerçevesi'ni kullanarak verilerle çalışma

ASP.NET Core Web Uygulamanızda Entity Framework Core'u kullanarak verilerle çalışmaya başlamak için aşağıdaki adımları izleyin.

_Bu videoyu izleyin ve ilk ASP.NET Core uygulamanıza veri eklemek için takip edin._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Projenizi açın

Bu videoları takip ediyorsanız, önceki bölümde oluşturduğunuz Web Uygulaması projesini açın. Burada başlıyorsanız, yeni bir proje oluşturmanız ve **web uygulaması ve** ardından Web **Uygulaması**ASP.NET seçmeniz gerekir. Geri kalan seçenekleri varsayılan olarak bırakın.

## <a name="add-your-model"></a>Modelinizi ekleyin

ASP.NET Core uygulamanızdaki verilerle çalışmak için yapmanız gereken ilk şey, verilerin nasıl görünmesi gerektiğini açıklamaktır. Biz buna çözmeye çalıştığımız problemle ilgili şeylerin bir *modelini* yaratmak diyoruz. Gerçek dünya uygulamalarında, bu modellere belirli şekillerde birlikte gibi durabilmeleri ve bizim için görevleri otomatikleştirebilmeleri için özel iş mantığı ekleyeceğiz. Bu örnek için, masa oyunlarını izlemek için basit bir sistem oluşturacağız. Bir oyunu temsil eden bir sınıfa ihtiyacımız var ve bu oyun hakkında kaydetmek isteyebileceğimiz bazı özellikler içeriyor, örneğin kaç oyuncuyu destekleyebileceği gibi. Bu sınıf, web projesinin kökünde oluşturduğumuz *Modeller*adlı yeni bir klasöre gidecek.

```csharp
public class Game
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int PublicationYear { get; set; }
    public int MinimumPlayers { get; set; }
    public int MaximumPlayers { get; set; }
}
```

## <a name="create-the-pages-to-manage-your-game-library"></a>Oyun kitaplığınızı yönetmek için sayfaları oluşturun

Artık oyun kitaplığımızı yönetmek için kullanacağımız sayfaları oluşturmaya hazırız. Bu korkutucu gelebilir ama aslında inanılmaz derecede kolay. Öncelikle uygulamamızda bu işlevselliğin nerede yaşaması gerektiğine karar vermeliyiz. Web projesindeki Sayfalar klasörünü açın ve oraya yeni bir klasör ekleyin. Buna *Oyunlar*deyin.

Şimdi Oyunlar'a tıklayın ve**Yeni İskele Öğe** **ekle'yi** > seçin. **Varlık Çerçevesi (CRUD)** seçeneğini kullanarak Jilet Sayfaları'nı seçin. CRUD "Oluştur, Oku, Güncelle, Sil" anlamına gelir ve bu şablon bu işlemlerin her biri için sayfalar oluşturur (bir "tümünü listele" sayfası ve "bir öğenin ayrıntılarını görüntüle" sayfası dahil).

![Visual Studio 2019 ASP.NET Çekirdek İskele Sayfaları Ekle](media/vs-2019/vs2019-add-scaffold.png)

Oyun modeli sınıfınızı seçin ve yeni bir Veri bağlamı sınıfı eklemek için '+' simgesini kullanın. Bunu, `AppDbContext` olarak adlandırın. Geri sini varsayılan olarak bırakın ve **Ekle'yi**tıklatın.

Oyunlar klasörünüze aşağıdaki Razor Sayfaları neklendi:

- Oluştur.cshtml
- Delete.cshtml
- Ayrıntılar.cshtml
- Edit.cshtml
- Index.cshtml

![Visual Studio 2019 ASP.NET Çekirdek İskele Sayfaları](media/vs-2019/vs2019-scaffolded-pages.png)

*Oyunlar* klasörüne sayfa eklemenin yanı sıra, iskele işlemi *Startup.cs* sınıfıma kod ekledi. Bu sınıfta `ConfigureServices` yönteme baktığınızda bu kodun eklendiğini göreceksiniz:

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

Ayrıca, bağlantı dizesinin `AppDbContext` projenin *appsettings.json* dosyasına eklendiğini de göreceksiniz.

Uygulamayı şimdi çalıştırıyorsanız, henüz veritabanı oluşturulmadı diye başarısız olabilir. Uygulamayı, Program.cs bazı [kodlar ekleyerek](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio#update-main)gerekirse veritabanını otomatik olarak oluşturacak şekilde yapılandırabilirsiniz:

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<AppDbContext>();
            context.Database.EnsureCreated();
        }
        catch (Exception ex)
        {
            var logger = services.GetRequiredService<ILogger<Program>>();
            logger.LogError(ex, "An error occurred creating the DB.");
        }
    }

    host.Run();
}
```

Önceki koddaki tür adlarını çözümlemek için, varolan ifadeleri kullanma bloğunun sonunda *Program.cs* için aşağıdaki ifadeleri ekleyin:

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

Kodunuzda WebApplication1 yerine proje adınızı kullandığınızdan emin olun.

Kodun çoğu sadece hata işleme ve uygulama çalışmaya `AppDbContext` başlamadan önce EF Core'a erişim sağlamak içindir. Önemli `context.Database.EnsureCreated()`satır, zaten yoksa veritabanını oluşturacak olan Artık uygulama çalışmaya hazır.

## <a name="test-it-out"></a>Test etme

Uygulamayı çalıştırın ve `/Games` adres çubuğuna gidin. Boş bir liste sayfası görürsünüz. Koleksiyona yeni bir `Game` yeni eklemek için **Yeni Oluştur'u** tıklatın. Formu doldurun ve **Oluştur'u**tıklatın. Liste görünümünde görmelisiniz. Tek bir kaydın ayrıntılarını görmek için **Ayrıntılar'ı** tıklatın.

Başka bir kayıt ekleyin. Bir kaydın ayrıntılarını değiştirmek için *Düzenle'yi* veya onu kaldırmak için **Sil'i** tıklatabilirsiniz, bu da kaydı gerçekten silmeden önce onaylamanızı ister.

![Visual Studio 2019 ASP.NET Tarayıcıda Çekirdek İskele Sayfaları](media/vs-2019/vs2019-game-list.png)

EF Core ve Visual Studio 2019'u kullanarak ASP.NET Core uygulamasındaki verilerle çalışmaya başlamak için gereken tek şey buydu.

## <a name="next-steps"></a>Sonraki adımlar

Bir sonraki videoda, uygulamanıza web API desteği eklemeyi öğreneceksiniz.

[Adım 4: ASP.NET Core App bir web API açığa](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Core'da Varlık Çerçeve Çekirdeği ne kadar sayfa ASP.NET](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio)
- [EF Core ile ASP.NET Çekirdek Li Jilet Sayfaları](/aspnet/core/data/?view=aspnetcore-2.1)
