---
title: TypeScript ile ASP.NET Core uygulaması oluşturma
description: Bu öğreticide, ASP.NET Core ve TypeScript kullanarak bir uygulama oluşturabilirsiniz
ms.date: 03/25/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 9b8bee5918a85c2a661911ee71dcfd633fce4cb2
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2021
ms.locfileid: "115094061"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Öğretici: Visual Studio'de TypeScript ASP.NET Core bir uygulama Visual Studio

Visual Studio ve TypeScript ASP.NET Core için bu öğreticide basit bir web uygulaması oluşturacak, bazı TypeScript kodu ekser ve ardından uygulamayı çalıştırabilirsiniz.

::: moniker range=">=vs-2022"

Visual Studio 2022'den başlayarak, ASP.NET Core ve TypeScript ile bir [ASP.NET Core](../javascript/tutorial-asp-net-core-with-angular.md) uygulaması oluşturmak için Visual Studio'da Angular ile Angular ASP.NET Core uygulaması oluşturma.
::: moniker-end

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * ASP.NET Core projesi oluşturma
> * TypeScript NuGet için paket ekleme
> * TypeScript kodu ekleme
> * Uygulamayı çalıştırma
> * npm kullanarak üçüncü taraf kitaplığı ekleme

## <a name="prerequisites"></a>Önkoşullar

* Web geliştirme Visual Studio yük ASP.NET yüklü olması gerekir.

    ::: moniker range="vs-2019"
    Visual Studio 2019'Visual Studio yüklemediyebilirsiniz. [](https://visualstudio.microsoft.com/downloads/)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de henüz yüklememişsinizdir, ücretsiz Visual Studio [](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekse ama zaten yüklü Visual Studio Araçları ve Özellikleri Al... 'a  >  **gidin.** Bu işlem Visual Studio Yükleyicisi. Web geliştirme **ASP.NET iş yükünü ve ardından** Değiştir'i **seçin.**

## <a name="create-a-new-aspnet-core-mvc-project"></a>Yeni bir MVC ASP.NET Core oluşturma

Visual Studio projesinde tek bir uygulamanın dosyalarını *yönetir.* Proje kaynak kodunu, kaynakları ve yapılandırma dosyalarını içerir.

>[!NOTE]
> Boş bir ASP.NET Core projesiyle başlamak ve bir TypeScript ön ucu eklemek için [bkz. ASP.NET Core TypeScript ile](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) ekleme.

Bu öğreticide, bir MVC uygulaması için kod içeren basit bir ASP.NET Core başlayacaktır.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range="vs-2019"
    2019 Visual Studio da başlangıç **penceresinde Yeni proje oluştur'a** tıklayın. Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne**  >  **tıklayın.** **Web uygulaması yazın,** dil **olarak C#** seçin, ardından ASP.NET Core Web Uygulaması **(Model-Görünüm-Denetleyici)** ve ardından Sonraki'yi **seçin.** Sonraki ekranda projeyi olarak ad girin ve ardından Sonraki'yi **seçin.**

    Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **dosya'Project.**  >    >   Yeni Çalışma Alanı iletişim kutusunun sol **Project** **Visual C#** öğesini genişletin ve **.NET Core'ı seçin.** Orta bölmede Web Uygulaması - **C# ASP.NET Core** tamam'ı **seçin.**

    Görüntülenen iletişim kutusunda, iletişim kutusunda Web Uygulaması **(Model-Görünüm-Denetleyici)** seçeneğini ve ardından Oluştur **(veya** Tamam) öğesini **seçin.**

    ![MVC şablonunu seçme](../javascript/media/aspnet-core-ts-mvc-template.png)
    ::: moniker-end
    ASP.NET Core **Web Uygulaması** proje şablonunu görmüyorsanız, web uygulaması ve **web ASP.NET eklemeniz** gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar.](#prerequisites)

    Visual Studio çözümü oluşturur ve projenizi sağ bölmede açar.

## <a name="add-some-code"></a>Kod ekleme

1. Bölmede Çözüm Gezgini (sağ bölme). Proje düğümüne sağ tıklayın ve Paketleri **Yönet'NuGet seçin.** Gözat **sekmesinde** **Microsoft.TypeScript.MSBuild** araması yapın ve ardından paketi **yüklemek** için sağdan Yükle'ye tıklayın.

   ![Paket NuGet ekleme](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio paketi NuGet'daki **Bağımlılıklar** düğümü altına Çözüm Gezgini.

1. Proje düğümüne sağ tıklayın ve Yeni **Öğe'> Ekle'yi seçin.** **TypeScript JSON Yapılandırma Dosyasını seçin ve** ekle'ye **tıklayın.**

   Visual Studio,tsconfig.js *proje* köküne ekler. TypeScript derleyicisi seçeneklerini [yapılandırmak için](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) bu dosyayı kullanabilirsiniz.

1. Aşağıdaki *tsconfig.jsaçın* ve varsayılan kodu aşağıdaki kodla değiştirin:

   ```json
   {
     "compileOnSave": true,
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   *outDir* seçeneği, TypeScript derleyicisi tarafından transpile edilen düz JavaScript dosyalarının çıkış klasörünü belirtir.

   Bu yapılandırma, TypeScript kullanmaya temel bir giriş sağlar. Diğer senaryolarda, [örneğin, gulp](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)veya webpack kullanırken, *wwwroot/js* yerine araçlarınıza ve yapılandırma tercihlerinize bağlı olarak, transpiled JavaScript dosyaları için farklı bir ara konum istiyor olabilir.

1. Yeni Çözüm Gezgini proje düğümüne sağ tıklayın ve Yeni Klasör **ekle'> seçin.** Yeni klasör için *ad* betiklerini kullanın.

1. Scripts klasörüne sağ *tıklayın ve* Yeni **Öğe'> Ekle'yi seçin.** **TypeScript Dosyasını seçin,** dosya adı için *app.ts adını* yazın ve Ekle'ye **tıklayın.**

   Visual Studio *scripts klasörüne app.ts* *ekler.*

1. *app.ts'yi* açın ve aşağıdaki TypeScript kodunu ekleyin.

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    Visual Studio TypeScript kodunuz için IntelliSense desteği sağlar.

    Bunu test etmek için `.lastName` işlevinden `greeter` kaldırın, sonra "." yazın ve IntelliSense'i görürsünüz.

    ![IntelliSense'i görüntüleme](../javascript/media/aspnet-core-ts-intellisense.png)

    Son `lastName` adı koda geri eklemek için öğesini seçin.

1. *Görünümler/Giriş klasörünü* ve ardından *Index.cshtml dosyasını açın.*

1. Aşağıdaki HTML kodunu dosyanın sonuna ekleyin.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. *Views/Shared klasörünü* açın ve *_Layout.cshtml dosyasını açın.*

1. çağrısının önce aşağıdaki betik başvurusunu `@RenderSection("Scripts", required: false)` ekleyin:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Uygulama oluşturma

1. Derleme **ve > Çözümü'ne seçin.**

   Uygulamayı çalıştırarak otomatik olarak derlemeye devam ediyor olsa da, derleme işlemi sırasında olan bir şeye göz atacağız.

1. *wwwroot/js* klasörünü açın,app.jsve *app.js.map* kaynak eşleme *dosyası.* Bu dosyalar TypeScript derleyicisi tarafından oluşturulur.

   Hata ayıklama için kaynak eşleme dosyaları gereklidir.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı **çalıştırmak için F5** '**e**(  >  **Hata AyıklamaYı** Başlat ) basın.

    Uygulama bir tarayıcıda açılır.

    Tarayıcı penceresinde Hoş Geldiniz başlığı ve **Bana** Tıklayın **düğmesini** görebilirsiniz.

    ![ASP.NET Core Script ile kullanma](../javascript/media/aspnet-core-ts-running-app.png)

1. TypeScript dosyasında belirtilen iletiyi görüntülemek için düğmeye tıklayın.

## <a name="debug-the-application"></a>Uygulamada hata ayıklama

1. Kod düzenleyicisinde sol kenar `greeter` `app.ts` boşluğuna tıklayarak işlevinde bir kesme noktası ayarlayın.

    ![Kesme noktası ayarlama](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Uygulamayı çalıştırmak için **F5**'e basın.

   Betik hata ayıklamayı etkinleştirmek için bir iletiyi yanıtlamanız gerekir.

   Uygulama kesme noktası sırasında duraklatılır. Artık değişkenleri inceleyebilirsiniz ve hata ayıklayıcı özelliklerini kullanabilirsiniz.

## <a name="add-typescript-support-for-a-third-party-library"></a>Üçüncü taraf kitaplık için TypeScript desteği ekleme

1. Projenize [dosya eklemek için npm](../javascript/npm-package-management.md#aspnet-core-projects) paket yönetimi `package.json` yönergelerini izleyin. Bu, projenize npm desteği ekler.

   >[!NOTE]
   > Daha ASP.NET Core için istemci tarafı JavaScript ve CSS dosyalarını yüklemek için npm yerine [Kitaplık](/aspnet/core/client-side/libman/) Yöneticisi'ni veya yarn'i de kullanabilirsiniz.

1. Bu örnekte, projenize jQuery için bir TypeScript tanım dosyası ekleyin. Dosyanıza *aşağıdakinipackage.js.*

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Bu, jQuery için TypeScript desteği ekler. jQuery kitaplığının kendisi zaten MVC proje şablonuna dahil edildi (dosyada wwwroot/lib Çözüm Gezgini). Farklı bir şablon kullanıyorsanız jquery npm paketini de dahil etmek zorundayabilirsiniz.

1. uygulama paketi Çözüm Gezgini npm düğümüne sağ tıklayın ve Paketleri Geri **Yükle'yi seçin.**

   >[!NOTE]
   > Bazı senaryolarda, Çözüm Gezgini burada açıklanan bilinen bir sorundan dolayı *npm paketininpackage.js* ile eşitlerinin dışı olduğunu gösteriyor [olabilir.](https://github.com/aspnet/Tooling/issues/479) Örneğin, paket yüklenirken yüklenmemiş gibi görünebilir. Çoğu durumda, *Çözüm Gezgini'package.js* silerek, Visual Studio'i yeniden başlatarak ve bu makalenin önceki sürümlerinde açıklandığı gibi *package.js* dosyasını yeniden ekleyerek güncelleştirme gerçekleştirebilirsiniz.

1. Komut Çözüm Gezgini betikler klasörüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.**

1. **TypeScript Dosyası'ı seçin,** *library.ts yazın ve* Ekle'yi **seçin.**

1. *library.ts içinde* aşağıdaki kodu ekleyin.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString() + " " + v + "!!");
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Kolaylık olması için, bu kod jQuery ve uyarı kullanarak bir ileti görüntüler.

   jQuery için TypeScript tür tanımları eklendiyle, burada gösterildiği gibi bir jQuery nesnesinin ardından bir "." yazarak jQuery nesnelerinde IntelliSense desteği elde edersiniz.

   ![jquery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. _Layout.cshtml dosyasında betik başvurularını içerecek şekilde `library.js` güncelleştirin.

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. Index.cshtml dosyasında dosyanın sonuna aşağıdaki HTML kodunu ekleyin.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Uygulamayı **çalıştırmak için F5** '**e**(  >  **Hata AyıklamaYı** Başlat ) basın.

    Uygulama tarayıcıda açılır.

    jQuery sürümüne güncelleştirilmiş sayfayı görmek için uyarıda Tamam'a **tıklayın: 3.3.1!!**. 

    ![jquery örneği](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Sonraki adımlar

TypeScript'i ASP.NET Core ile kullanma hakkında daha fazla bilgi ASP.NET Core. Visual Studio'de AngularJS programlamayla ilgileniyorsanız, [angularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio) dil hizmeti uzantısını Visual Studio.

> [!div class="nextstepaction"]
> [ASP.NET Core ve TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

> [!div class="nextstepaction"]
> [AngularJS dil hizmeti uzantısı](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
