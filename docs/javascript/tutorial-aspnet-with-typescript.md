---
title: TypeScript ile ASP.NET Core uygulaması oluşturma
description: bu öğreticide, ASP.NET Core ve TypeScript kullanarak bir uygulama oluşturacaksınız
ms.date: 03/25/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 9a4067f356f5e8beb598a3ab0366125cf2b95b35
ms.sourcegitcommit: 65a1b6aae8387735f05a83b45e1a6865e9805e1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2021
ms.locfileid: "129339593"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>öğretici: Visual Studio TypeScript ile ASP.NET Core uygulaması oluşturma

bu öğreticide Visual Studio geliştirme ASP.NET Core ve TypeScript için, basit bir web uygulaması oluşturun, bazı TypeScript kodu ekleyin ve uygulamayı çalıştırın.

::: moniker range=">=vs-2022"

Visual Studio 2022 ' den başlayarak ASP.NET Core ile Angular veya vue kullanmak istiyorsanız, TypeScript ile bir ASP.NET Core uygulaması oluşturmak için ASP.NET Core tek sayfalı uygulama (SPA) şablonlarını kullanmanız önerilir. daha fazla bilgi için [Angular](../javascript/tutorial-asp-net-core-with-angular.md) veya [vue](../javascript/tutorial-asp-net-core-with-vue.md)Visual Studio öğreticileri inceleyin.
::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end
::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * ASP.NET Core projesi oluşturma
> * TypeScript desteği için NuGet paketini ekleme
> * Bazı TypeScript kodu ekle
> * Uygulamayı çalıştırma
> * NPM kullanarak bir üçüncü taraf kitaplığı ekleme

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve ASP.NET web geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range="vs-2019"
    zaten 2019 Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    zaten 2017 Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
    ::: moniker-end

    iş yükünü yüklemeniz gerekir, ancak zaten Visual Studio sahipseniz **araçlar**  >  **ve özellikler al.**.. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. **ASP.NET ve web geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.

## <a name="create-a-new-aspnet-core-mvc-project"></a>yeni bir ASP.NET Core MVC projesi oluşturma

Visual Studio *projedeki* tek bir uygulama için dosyaları yönetir. Proje kaynak kodu, kaynakları ve yapılandırma dosyalarını içerir.

>[!NOTE]
> boş bir ASP.NET Core projesiyle başlamak ve bir typescript ön ucu eklemek için, bkz. [typescript ile ASP.NET Core](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) .

bu öğreticide, ASP.NET Core MVC uygulaması için kod içeren basit bir proje ile başlarsınız.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range="vs-2019"
    Visual Studio 2019 ' de, başlangıç penceresinde **yeni proje oluştur** ' u seçin. Başlangıç penceresi açık değilse **Dosya**  >  **Başlangıç penceresi**' ni seçin. **web** uygulaması yazın, dil olarak **C#** ' yi seçin, ardından **ASP.NET Core web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **ileri**' yi seçin. Sonraki ekranda, projeyi adlandırın ve ardından **İleri**' yi seçin.

    Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin. **yeni Project** iletişim kutusunun sol bölmesinde, **Visual C#**' ı genişletin ve ardından **.net Core**' u seçin. orta bölmede, **Web uygulaması-C# ASP.NET Core** seçin ve ardından **tamam**' ı seçin.

    Görüntülenen iletişim kutusunda, iletişim kutusunda **Web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **Oluştur** (veya **Tamam**) öğesini seçin.

    ![MVC şablonunu seçin](../javascript/media/aspnet-core-ts-mvc-template.png)
    ::: moniker-end
    **ASP.NET Core web uygulaması** proje şablonunu görmüyorsanız, **ASP.NET ve web geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni çözümü oluşturur ve projenizi sağ bölmede açar.

## <a name="add-some-code"></a>Kod ekleme

1. Çözüm Gezgini (sağ bölme). proje düğümüne sağ tıklayın ve **NuGet paketlerini yönet**' i seçin. **araştır** sekmesinde, **Microsoft. TypeScript. MSBuild** araması yapın ve ardından **paketi yüklemek için sağdaki aç '** a tıklayın.

   ![NuGet paketi ekle](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio, NuGet paketini Çözüm Gezgini **bağımlılıklar** düğümü altına ekler.

1. Proje düğümüne sağ tıklayın ve **> yeni öğe Ekle**' yi seçin. **TYPESCRIPT JSON yapılandırma dosyasını** seçin ve ardından **Ekle**' ye tıklayın.

   Visual Studio *tsconfig. json* dosyasını proje köküne ekler. TypeScript derleyicisi [seçeneklerini yapılandırmak](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) için bu dosyayı kullanabilirsiniz.

1. *Tsconfig. JSON* dosyasını açın ve varsayılan kodu şu kodla değiştirin:

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

   *OutDir* seçeneği, TypeScript derleyicisi tarafından transpiled olan düz JavaScript dosyaları için çıkış klasörünü belirtir.

   Bu yapılandırma, TypeScript kullanımına yönelik temel bir giriş sağlar. Diğer senaryolarda, örneğin, [Gulp veya WebPack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)kullanırken, transpiled JavaScript dosyaları için *Wwwroot/js* yerine araçlar ve yapılandırma tercihlerinize bağlı olarak farklı bir ara konum isteyebilirsiniz.

1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve **> yeni klasör ekle**' yi seçin. Yeni klasör için ad *betikleri* kullanın.

1. *Betikler* klasörüne sağ tıklayın ve **> yeni öğe Ekle**' yi seçin. **TypeScript dosyasını** seçin, dosya adı için *app. TS* adını yazın ve ardından **Ekle**' ye tıklayın.

   Visual Studio *scripts* klasörüne *app. ts* ekler.

1. *App. TS* ' i açın ve aşağıdaki TypeScript kodunu ekleyin.

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

    Visual Studio TypeScript kodunuz için ıntellisense desteği sağlar.

    Bunu test etmek için, `.lastName` işlevinden kaldırın `greeter` , ardından "." öğesini yeniden yazın ve IntelliSense ' i görürsünüz.

    ![IntelliSense 'i görüntüle](../javascript/media/aspnet-core-ts-intellisense.png)

    `lastName`Son adı koda geri eklemeyi seçin.

1. *Görünümler/giriş* klasörünü açın ve *Index. cshtml* dosyasını açın.

1. Aşağıdaki HTML kodunu dosyanın sonuna ekleyin.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. *Görünümler/paylaşılan* klasörünü açın ve ardından *_Layout. cshtml* dosyasını açın.

1. Çağrısının önüne şu komut dosyası başvurusunu ekleyin `@RenderSection("Scripts", required: false)` :

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Uygulama oluşturma

1. **Build > Build Solution** öğesini seçin.

   Uygulamayı çalıştırdığınızda otomatik olarak oluştursa da, yapı işlemi sırasında gerçekleşen bir şeye göz atmak istiyoruz.

1. *Wwwroot/js* klasörünü açın ve iki yeni dosya, *app.js* ve kaynak eşleme dosyası olan *app.js. Map*' i bulun. Bu dosyalar TypeScript derleyicisi tarafından oluşturulur.

   Hata ayıklama için kaynak eşleme dosyaları gereklidir.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **F5** tuşuna **basın (hata ayıklama**  >  **başlatma hata** ayıklaması).

    Uygulama bir tarayıcıda açılır.

    Tarayıcı penceresinde, **hoş geldiniz** başlığını ve **bana tıklama** düğmesini görürsünüz.

    ![TypeScript ile ASP.NET Core](../javascript/media/aspnet-core-ts-running-app.png)

1. TypeScript dosyasında belirttiğimiz iletiyi göstermek için düğmeye tıklayın.

## <a name="debug-the-application"></a>Uygulamada hata ayıklama

1. `greeter` `app.ts` Kod düzenleyicisinde sol kenar boşluğuna tıklayarak içindeki işlevinde bir kesme noktası ayarlayın.

    ![Kesme noktası ayarlama](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Uygulamayı çalıştırmak için **F5**'e basın.

   Betik hata ayıklamasını etkinleştirmek için bir iletiye yanıt almanız gerekebilir.

   Uygulama kesme noktasında duraklatılır. Şimdi, değişkenleri inceleyebilir ve hata ayıklayıcı özellikleri kullanabilirsiniz.

## <a name="add-typescript-support-for-a-third-party-library"></a>Üçüncü taraf kitaplığı için TypeScript desteği ekleme

1. Projenize bir dosya eklemek için [NPM paket yönetiminde](../javascript/npm-package-management.md#aspnet-core-projects) yönergeleri izleyin `package.json` . Bu, projenize NPM desteği ekler.

   >[!NOTE]
   > ASP.NET Core projeleri için, istemci tarafı JavaScript ve CSS dosyalarını yüklemek üzere npm yerine [kitaplık yöneticisi](/aspnet/core/client-side/libman/) 'ni veya yarn 'yi de kullanabilirsiniz.

1. Bu örnekte, projenize jQuery için bir TypeScript tanım dosyası ekleyin. *Package. JSON* dosyanıza aşağıdakini ekleyin.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Bu, jQuery için TypeScript desteği ekler. JQuery kitaplığı, MVC proje şablonuna zaten dahil edilmiştir (Çözüm Gezgini ' de Wwwroot/lib bölümüne bakın). Farklı bir şablon kullanıyorsanız, jQuery NPM paketini de eklemeniz gerekebilir.

1. Çözüm Gezgini paket yüklü değilse, NPM düğümüne sağ tıklayın ve **paketleri geri yükle**' yi seçin.

   >[!NOTE]
   > Bazı senaryolarda Çözüm Gezgini, [burada](https://github.com/aspnet/Tooling/issues/479)açıklanan bilinen bir sorun nedeniyle NPM paketinin *Package. JSON* ile eşitlenmemiş olduğunu gösterebilir. Örneğin, paket yüklendiğinde yüklü değil olarak görünebilir. çoğu durumda, bu makalenin önceki kısımlarında açıklandığı gibi package *. json*' ı silerek Çözüm Gezgini güncelleştirebilir, Visual Studio yeniden başlatarak ve *package. json* dosyasını yeniden ekleyebilirsiniz.

1. Bu Çözüm Gezgini scripts klasörüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.**

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

   jQuery için TypeScript tür tanımları eklendiyle, burada gösterildiği gibi bir jQuery nesnesinin ardından bir "." yazarak jQuery nesneleri üzerinde IntelliSense desteği elde edersiniz.

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

TypeScript'i ASP.NET Core ile kullanma hakkında daha fazla bilgi ASP.NET Core. angularJS programlama ile ilgileniyorsanız Visual Studio için [AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio) dil hizmeti uzantısını Visual Studio.

> [!div class="nextstepaction"]
> [ASP.NET Core ve TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

> [!div class="nextstepaction"]
> [AngularJS dil hizmeti uzantısı](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
