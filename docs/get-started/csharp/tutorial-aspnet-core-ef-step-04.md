---
title: "4. Adım: ASP.NET Core uygulamanızdan bir Web API 'SI gösterme"
description: Bu video öğreticisiyle ASP.NET Core Web uygulamanıza bir Web API 'SI ekleyin ve adım adım yönergeleri uygulayın.
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
ms.openlocfilehash: 9a2ee576808698e19726cadfea7ba560ce3bdb7c
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91780932"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>4. Adım: ASP.NET Core uygulamanızdan bir Web API 'SI kullanıma sunma

Mevcut ASP.NET Core uygulamanıza bir Web API 'SI eklemek için bu adımları izleyin.

_İlk ASP.NET Core uygulamanıza Web API desteği eklemek için bu videoyu izleyin ve takip edin._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Projenizi açın

ASP.NET Core uygulamanızı Visual Studio 2019 ' de açın. Uygulama, [Bu öğretici serisinin 3. adımında](tutorial-aspnet-core-ef-step-03.md)yapılandırıldığı gibi model türlerinizi yönetmek için zaten EF Core kullanıyor olmalıdır.

## <a name="add-an-api-controller"></a>API denetleyicisi ekleme

Projeye sağ tıklayın ve *API*adlı yeni bir klasör ekleyin. Sonra bu klasöre sağ tıklayın ve **Add**  >  **yeni yapı iskelesi Ekle öğesini**seçin. **Entity Framework kullanarak, eylemler Içeren API denetleyicisi ' ni seçin.** Şimdi var olan bir model sınıfını seçin ve **Ekle**' ye tıklayın.

![Visual Studio 2019 ASP.NET Core Scafkatlanmış API denetleyicisi](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Oluşturulan denetleyiciyi gözden geçirme

Oluşturulan kod yeni bir denetleyici sınıfı içerir. Sınıf tanımının en üstünde iki öznitelik bulunur.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

Birincisi, bu denetleyicideki eylemler için yolu belirtir. Bu, `api/[controller]` denetleyicinin yol olarak adlandırılması durumunda olacağı anlamına gelir `GamesController` `api/Games` .

İkinci özniteliği, `[ApiController]` sınıfa bazı yararlı doğrulamalar ekler; örneğin, her eylem yönteminin kendi özniteliğini içermesi gerekir `[Route]` .

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

Denetleyici, oluşturucuya geçirilmiş olan varolanı kullanır `AppDbContext` . Her eylem, uygulamanın verileriyle çalışmak için bu alanı kullanır.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

İlk yöntem, özniteliği kullanılarak belirtilen basit bir GET isteğidir `[HttpGet]` . Hiçbir parametre alır ve veritabanındaki tüm oyunların listesini döndürür.

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

Sonraki yöntem, `{id}` yol içinde, bir sonraki yola eklenecek rota ' ı belirtir `/` . bu nedenle, tam yol `api/Games/5` en üstteki açıklamada gösterildiği gibi bir şey olacaktır. `id`Giriş, `id` yöntemindeki parametreye eşlenir. Yöntemi içinde, model geçersizse, bir `BadRequest` sonuç döndürülür. Aksi halde, EF, belirtilen kaydıyla eşleşen kaydı bulmaya çalışacaktır `id` . `NotFound`Sonuç döndürülmezse, uygun `Game` kayıt döndürülür.

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

Ardından, bir `[HttpPut]` API 'ye yapılan istek, güncelleştirmeleri gerçekleştirmek için kullanılır. Yeni `Game` kayıt isteğin gövdesinde sağlanır. Bazı doğrulama ve hata denetimi gerçekleştirilir ve her şey başarılı olursa veritabanındaki kayıt, isteğin gövdesinde belirtilen değerlerle güncelleştirilir. Aksi takdirde uygun bir hata yanıtı döndürülür.

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

`[HttpPost]`Sisteme yeni kayıtlar eklemek için bir istek kullanılır. ' De olduğu gibi, `[HttpPut]` kayıt, isteğin gövdesine eklenir. Geçerliyse, EF Core kaydı veritabanına ekler ve eylem güncelleştirilmiş kaydı (veritabanı oluşturulan KIMLIĞIYLE birlikte) ve API 'deki kayda yönelik bir bağlantıyı döndürür.

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

Son olarak, bir `[HttpDelete]` kaydı silmek IÇIN kimlik ile bir yol kullanılır. İstek geçerliyse ve belirtilen KIMLIĞE sahip bir kayıt varsa EF Core veritabanından silin.

## <a name="adding-swagger"></a>Swagger ekleniyor

Swagger, bir ASP.NET Core uygulamasına bir dizi hizmet ve ara yazılım olarak eklenebilen bir API belgeleri ve test aracıdır. Bunu yapmak için projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Ardından, **Araştır**' a tıklayın, `Swashbuckle.AspNetCore` 4.0.1 sürümünü arayın ve yüklemeyi yapın.

![Visual Studio 2019 NuGet 'Den swashbuckle ekleme](media/vs-2019/vs2019-nuget-swashbuckle.png)

Yüklendikten sonra, öğesini açın `Startup.cs` ve yönteminin sonuna şunu ekleyin `ConfigureServices` :

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Ayrıca, `using Swashbuckle.AspNetCore.Swagger;` dosyanın en üstüne de eklemeniz gerekir.

Ardından, aşağıdaki `Configure` yöntemi yöntemine ekleyin `UseMvc` :

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

Artık uygulamanızı derleyip çalıştırabilmelisiniz. Tarayıcıda, adres çubuğunda öğesine gidin `/swagger` . Uygulamanızın API uç noktaları ve modellerinin bir listesini görmeniz gerekir.

![Visual Studio 2019 Swagger sayfası tarayıcıda](media/vs-2019/vs2019-swagger-browser.png)

Oyunlar altında bir uç noktaya tıklayın `Try it out` ve `Execute` farklı uç noktaların nasıl davranacağını görmek için.

## <a name="next-steps"></a>Sonraki adımlar

Bir sonraki videoda, uygulamanızı Azure 'a dağıtmayı öğreneceksiniz.

[5. Adım: ASP.NET Core uygulamanızı Azure 'a dağıtma](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Swashbuckle ve ASP.NET Core kullanmaya başlama](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio&preserve-view=true)
- [Swagger/Openapı ile Web API Yardım sayfaları ASP.NET Core](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2&preserve-view=true)