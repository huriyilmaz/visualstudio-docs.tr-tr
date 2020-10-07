---
title: '3. Adım: ASP.NET Core uygulamanızdaki verilerle çalışma'
description: Bu video öğreticisiyle ASP.NET Core Web uygulamanızda Entity Framework Core kullanarak verilerle çalışmaya başlayın ve adım adım yönergeleri uygulayın.
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
ms.openlocfilehash: 9d01d991daf5c24c02b8cd4976663a9399b251cc
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91780963"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>3. Adım: Entity Framework kullanarak verilerle çalışma

ASP.NET Core Web uygulamanızda Entity Framework Core kullanarak verilerle çalışmaya başlamak için aşağıdaki adımları izleyin.

_İlk ASP.NET Core uygulamanıza veri eklemek için bu videoyu izleyin ve takip edin._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Projenizi açın

Bu videolarla birlikte takip ediyorsanız, önceki bölümde oluşturduğunuz Web uygulaması projesini açın. Buradan başladıysanız, yeni bir proje oluşturmanız ve **ASP.NET Web uygulaması** ' nı ve ardından **Web uygulaması**' nı seçmeniz gerekir. Diğer seçenekleri varsayılan olarak bırakın.

## <a name="add-your-model"></a>Modelinizi ekleyin

ASP.NET Core uygulamanızdaki verilerle çalışmak için yapmanız gereken ilk şey, verilerin nasıl göründüğünü açıklıyor. Çözmeye çalıştığımız sorun ile ilgili işlerin bir *modelini* oluşturan çağrımız. Gerçek dünyada uygulamalarda, bu modellere özel iş mantığı ekleyecek ve bu modellerle ilgili belirli yollarla davranmaları ve görevleri otomatikleştirebiliriz. Bu örnekte, izleme panosu oyunları için basit bir sistem oluşturacağız. Bir oyunu temsil eden bir sınıfa ihtiyacımız var ve bu oyun hakkında, kaç oyuncu destekleyebileceği gibi, bu oyunla ilgili kaydetmek isteyebileceğiniz bazı özellikler de içeriyor. Bu sınıf, *modeller*olarak adlandırılan Web projesinin kökünde oluşturacağınız yeni bir klasöre gidecektir.

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

## <a name="create-the-pages-to-manage-your-game-library"></a>Oyun kitaplığınızı yönetmek için sayfalar oluşturma

Şimdi, oyun kitaplığınızı yönetmek için kullanacağımız sayfaları oluşturmaya hazırız. Bu, ancak gerçekten başaramayabiliriz kolay bir işlemdir. İlk olarak uygulamamızda bu işlevsellikten nerede canlı olduğuna karar vermemiz gerekiyor. Web projesindeki sayfalar klasörünü açın ve yeni bir klasör ekleyin. BT *oyunları*'nı çağırın.

Şimdi oyunlara sağ tıklayıp **Add**  >  **yeni yapı iskelesi Ekle öğesini**seçin. **Entity Framework (CRUD)** seçeneğini kullanarak Razor Pages seçin. CRUD "oluşturma, okuma, güncelleştirme, silme" anlamına gelir ve bu şablon, bu işlemlerin her biri için ("Tümünü Listele" sayfası ve "bir öğenin ayrıntılarını görüntüleme" sayfası dahil) sayfalar oluşturur.

![Visual Studio 2019 ASP.NET Core yapı Iskelesi sayfaları ekleme](media/vs-2019/vs2019-add-scaffold.png)

Oyun modeli sınıfınızı seçin ve yeni bir veri bağlamı sınıfı eklemek için ' + ' simgesini kullanın. Bunu, `AppDbContext` olarak adlandırın. Rest 'i varsayılan olarak bırakın ve **Ekle**' ye tıklayın.

Oyunlar klasörünüze aşağıdaki Razor Pages eklendiğini göreceksiniz:

- . Cshtml oluştur
- Delete. cshtml
- Details. cshtml
- Edit. cshtml
- Index.cshtml

![Visual Studio 2019 ASP.NET Core Scafkatlanmış sayfalar](media/vs-2019/vs2019-scaffolded-pages.png)

*Oyun* klasörüne sayfa eklemenin yanı sıra, scafkatlama işlemi *Startup.cs* sınıfma kod ekledi. `ConfigureServices`Bu sınıftaki yöntemine bakarak, bu kodun eklendiğini görürsünüz:

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

Ayrıca, `AppDbContext` bağlantı dizesinin dosyanın dosyadaki *appsettings.js* eklendiğini de bulabilirsiniz.

Uygulamayı şimdi çalıştırırsanız, henüz veritabanı oluşturulmadığından başarısız olabilir. [Program.cs 'e kod ekleyerek](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio&preserve-view=true#update-main)uygulamayı otomatik olarak veritabanını oluşturacak şekilde yapılandırabilirsiniz:

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<Data.AppDbContext>();
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

Yukarıdaki kodda typeNames 'yi çözümlemek için, using deyimleri var olan bloğunun sonundaki *program.cs* için aşağıdaki using deyimlerini ekleyin:

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

Kodunuzda WebApplication1 yerine proje adınızı kullandığınızdan emin olun.

Kodun çoğu yalnızca hata işleme içindir ve `AppDbContext` uygulama çalışmadan önce EF Core erişim sağlar. Önemli satır, `context.Database.EnsureCreated()` zaten mevcut değilse veritabanını oluşturacak olan bir veritabanıdır. Artık uygulama çalıştırılmaya hazır.

## <a name="test-it-out"></a>Test etme

Uygulamayı çalıştırın ve `/Games` Adres çubuğunda öğesine gidin. Boş bir liste sayfası görürsünüz. Koleksiyona yeni bir eklemek için **Yeni oluştur** ' a tıklayın `Game` . Formu doldurup **Oluştur**' a tıklayın. Liste görünümünde görmeniz gerekir. Tek bir kaydın ayrıntılarını görmek için **Ayrıntılar** ' a tıklayın.

Başka bir kayıt ekleyin. Bir kaydın ayrıntılarını değiştirmek için *Düzenle* ' ye tıklayabilir veya onu kaldırmak için **silebilirsiniz** ; bu, kaydı gerçekten silmeden önce onaylamanız istenir.

![Visual Studio 2019 ASP.NET Core tarayıcıda yapı Iskelesi olan sayfalar](media/vs-2019/vs2019-game-list.png)

Bu, EF Core ve Visual Studio 2019 kullanarak bir ASP.NET Core uygulamasındaki verilerle çalışmaya başlamak için geçen bir uygulamadır.

## <a name="next-steps"></a>Sonraki adımlar

Bir sonraki videoda, uygulamanıza Web API desteğinin nasıl ekleneceğini öğreneceksiniz.

[4. Adım: ASP.NET Core uygulamanızdan bir Web API 'SI gösterme](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Core Entity Framework Core ile Razor Pages](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio&preserve-view=true)
- [EF Core ile Razor Pages ASP.NET Core](/aspnet/core/data/?view=aspnetcore-2.1&preserve-view=true)
