---
title: 'Adım 4: ASP.NET Core App bir web API açığa'
description: Bu video eğitimi ve adım adım talimatlarla ASP.NET Core Web Uygulamanıza bir web API ekleyin.
ms.custom: get-started
ms.date: 02/13/2020
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
ms.openlocfilehash: 5ea9468bdf86986ab542fb1cabc873c9aeb75fd6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580044"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Adım 4: ASP.NET Core uygulamanızdan bir web API'si açığa çıkarma

Mevcut ASP.NET Core uygulamanıza bir web API eklemek için aşağıdaki adımları izleyin.

_Bu videoyu izleyin ve ilk ASP.NET Core uygulamanıza web API desteği eklemek için takip edin._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Projenizi açın

Visual Studio 2019'da ASP.NET Core uygulamanızı açın. Uygulama zaten model türleri yönetmek için EF Core kullanıyor olmalıdır, [bu öğretici serisinin adım 3](tutorial-aspnet-core-ef-step-03.md)olarak yapılandırılmıştır.

## <a name="add-an-api-controller"></a>API denetleyicisi ekleme

Projeye sağ tıklayın ve *Api*adı verilen yeni bir klasör ekleyin. Ardından, bu klasöre sağ tıklayın ve**Yeni İskele Öğe** **ekle'yi** > seçin. **Varlık Çerçevesi'ni kullanarak eylemlerle API Denetleyicisi'ni seçin.** Şimdi varolan bir model sınıfı seçin ve **Ekle'yi**tıklatın.

![Visual Studio 2019 ASP.NET Çekirdek İskele API Denetleyicisi](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Oluşturulan denetleyiciyi gözden geçirme

Oluşturulan kod yeni bir denetleyici sınıfı içerir. Sınıf tanımının en üstünde iki öznitelik vardır.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

İlki, bu denetleyicideki `api/[controller]` eylemlerin rotasını, denetleyicinin adı `GamesController` ise rota nın `api/Games`.

İkinci öznitelik, `[ApiController]`, her eylem yöntemi kendi `[Route]` özniteliği ni içermesini sağlamak gibi sınıfa bazı yararlı doğrulamalar ekler.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

Denetleyici, varolan `AppDbContext`, kendi oluşturucuiçine geçirilen kullanır. Her eylem, uygulamanın verileriyle çalışmak için bu alanı kullanır.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

İlk yöntem, öznitelik kullanılarak `[HttpGet]` belirtildiği gibi basit bir GET isteğidir. Hiçbir parametre alır ve veritabanındaki tüm oyunların bir listesini döndürür.

```csharp
// GET: api/Games/5
[HttpGet("{id}")]
public async Task<IActionResult> GetGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);

    if (game == null)
    {
        return NotFound();
    }

    return Ok(game);
}
```

Bir sonraki yöntem, `{id}` tam rotanın üstteki yorumda gösterildiği `/` gibi `api/Games/5` bir şey olması için aşağıdaki rotaya eklenecek olan rotada belirtilir. Giriş, `id` yöntemdeki `id` parametreye eşlenir. Yöntemin içinde, model geçersizse, `BadRequest` bir sonuç döndürülür. Aksi takdirde, EF sağlanan `id`kayıt eşleşen bulmaya çalışacaktır. Sonuç `NotFound` döndürülemezse, aksi takdirde uygun `Game` kayıt döndürülür.

```csharp
// PUT: api/Games/5
[HttpPut("{id}")]
public async Task<IActionResult> PutGame([FromRoute] int id, [FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    if (id != game.Id)
    {
        return BadRequest();
    }

    _context.Entry(game).State = EntityState.Modified;

    try
    {
        await _context.SaveChangesAsync();
    }
    catch (DbUpdateConcurrencyException)
    {
        if (!GameExists(id))
        {
            return NotFound();
        }
        else
        {
            throw;
        }
    }

    return NoContent();
}
```

Ardından, `[HttpPut]` güncelleştirmeleri gerçekleştirmek için API'ye yapılan bir istek kullanılır. Yeni `Game` kayıt, isteğin gövdesinde sağlanır. Bazı doğrulama ve hata denetimi gerçekleştirilir ve her şey başarılı olursa veritabanındaki kayıt isteğin gövdesinde sağlanan değerlerle güncelleştirilir. Aksi takdirde uygun bir hata yanıtı döndürülür.

```csharp
// POST: api/Games
[HttpPost]
public async Task<IActionResult> PostGame([FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    _context.Game.Add(game);
    await _context.SaveChangesAsync();

    return CreatedAtAction("GetGame", new { id = game.Id }, game);
}
```

Sisteme `[HttpPost]` yeni kayıtlar eklemek için bir istek kullanılır. , `[HttpPut]`kayıt isteğigövdesine eklenir. Geçerliyse, EF Core kaydı veritabanına ekler ve eylem güncelleştirilmiş kaydı (veritabanı tarafından oluşturulan kimliğiyle) ve API'deki kayda bağlantı döndürür.

```csharp
// DELETE: api/Games/5
[HttpDelete("{id}")]
public async Task<IActionResult> DeleteGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);
    if (game == null)
    {
        return NotFound();
    }

    _context.Game.Remove(game);
    await _context.SaveChangesAsync();

    return Ok(game);
}
```

Son olarak, bir `[HttpDelete]` kaydı silmek için kimlikiçeren bir rota kullanılır. İstek geçerliyse ve verilen kimliğiiçeren bir kayıt varsa, EF Core bu isteği veritabanından siler.

## <a name="adding-swagger"></a>Swagger ekleme

Swagger, bir ASP.NET Core uygulamasına bir hizmet kümesi ve ara yazılım olarak eklenebilen bir API dokümantasyon ve test aracıdır. Bunu yapmak için projeye sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. Ardından, **Gözat'ı,** aramayı `Swashbuckle.AspNetCore`ve 4.0.1 sürümünü yükleyin'i tıklatın.

![Visual Studio 2019 Nuget Gönderen Swashbuckle ekle](media/vs-2019/vs2019-nuget-swashbuckle.png)

Yüklendikten sonra, `Startup.cs` açık ve `ConfigureServices` yöntemin sonuna aşağıdaki ekleyin:

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Ayrıca dosyanın üst `using Swashbuckle.AspNetCore.Swagger;` kısmında eklemeniz gerekir.

Ardından, `Configure` yönteme hemen önce `UseMvc`aşağıdakileri ekleyin:

```csharp
// Enable middleware to serve generated Swagger as a JSON endpoint.
app.UseSwagger();

// Enable middleware to serve swagger-ui (HTML, JS, CSS, etc.), 
// specifying the Swagger JSON endpoint.
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
});
```

Artık uygulamanızı oluşturup çalıştırabilmelisiniz. Tarayıcıda adres `/swagger` çubuğuna gidin. Uygulamanızın API uç noktalarının ve modellerinin listesini görmeniz gerekir. 

![Visual Studio 2019 Tarayıcıda Swagger Sayfası](media/vs-2019/vs2019-swagger-browser.png)

Oyunlar altında bir bitiş `Try it out` noktası `Execute` tıklatın, sonra ve farklı uç noktaları nasıl hissettiğini görmek için.

## <a name="next-steps"></a>Sonraki adımlar

Bir sonraki videoda, uygulamanızı Azure'a nasıl dağıtacağınız öğrenilir.

[Adım 5: ASP.NET Çekirdek Uygulamanızı Azure'a Dağıtma](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Swashbuckle ve ASP.NET Core ile Başlarken](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio)
- [ASP.NET Core web API yardım sayfaları Swagger / OpenAPI ile](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2)