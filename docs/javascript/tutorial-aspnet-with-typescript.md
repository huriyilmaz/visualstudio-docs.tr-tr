---
title: TypeScript ile ASP.NET Core uygulaması oluşturma
description: Bu öğreticide, ASP.NET Core ve TypeScript kullanarak bir uygulama oluşturacaksınız
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 91c712ce396000ff9babaf70335edfd5709a3000
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183099"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Öğretici: Visual Studio 'da TypeScript ile ASP.NET Core uygulaması oluşturma

Visual Studio geliştirme ASP.NET Core ve TypeScript için bu öğreticide, basit bir Web uygulaması oluşturun, bazı TypeScript kodu ekleyin ve ardından uygulamayı çalıştırın. 

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * ASP.NET Core projesi oluşturma
> * TypeScript desteği için NuGet paketini ekleyin
> * Bazı TypeScript kodu ekle
> * Uygulamayı çalıştırma
> * NPM kullanarak bir üçüncü taraf kitaplığı ekleme

## <a name="prerequisites"></a>Ön koşullar

* Visual Studio 'Nun yüklü olması ve ASP.NET Web geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' ü henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/)   sayfasına giderek ücretsiz olarak yükleme yapın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' ü henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/)   sayfasına giderek ücretsiz olarak yükleme yapın.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak zaten Visual Studio 'ya sahipseniz **Araçlar**  >  **ve Özellikler al.**.. ' a giderek Visual Studio yükleyicisi açılır. **ASP.net ve Web geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Yeni bir ASP.NET Core MVC projesi oluşturma

Visual Studio, *projedeki*tek bir uygulama için dosyaları yönetir. Proje kaynak kodu, kaynakları ve yapılandırma dosyalarını içerir.

>[!NOTE]
> Boş bir ASP.NET Core projesiyle başlamak ve bir TypeScript ön ucu eklemek için, bkz. [TypeScript ile ASP.NET Core](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) .

Bu öğreticide, ASP.NET Core MVC uygulaması için kod içeren basit bir proje ile başlarsınız.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresi açık değilse **Dosya**  >  **Başlangıç penceresi**' ni seçin. Başlangıç penceresinde **Yeni proje oluştur**' u seçin. Dil açılan listesinde **C#**' ı seçin. Arama kutusuna **ASP.net**yazın ve ardından **ASP.NET Core Web uygulaması**' nı seçin. **İleri**’yi seçin.

    Proje için bir ad yazın ve **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#**' ı genişletin ve ardından **.NET Core**' u seçin. Orta bölmede, **Web uygulaması-C# ASP.NET Core**seçin ve ardından **Tamam**' ı seçin.
    ::: moniker-end
    **ASP.NET Core Web uygulaması** proje şablonunu görmüyorsanız, **ASP.net ve Web geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

1. Görüntülenen iletişim kutusunda, iletişim kutusunda **Web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **Oluştur** (veya **Tamam**) öğesini seçin.

   ![MVC şablonunu seçin](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio yeni çözümü oluşturur ve projenizi sağ bölmede açar.

## <a name="add-some-code"></a>Kod ekleme

1. Çözüm Gezgini (sağ bölme). proje düğümüne sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. **Araştır** sekmesinde, **Microsoft. TypeScript. MSBuild**' i arayın ve ardından, paketi yüklemek için **sağdaki aç '** a tıklayın.

   ![NuGet paketi Ekle](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio, NuGet paketini Çözüm Gezgini içindeki **Bağımlılıklar** düğümüne ekler.

   > [!NOTE]
   > Bu öğretici NuGet paketini gerektirir. Alternatif olarak, kendi uygulamalarınızda [TypeScript NPM paketini](https://www.npmjs.com/package/typescript)kullanmak isteyebilirsiniz.

1. Proje düğümüne sağ tıklayın ve **> yeni öğe Ekle**' yi seçin. **TYPESCRIPT JSON yapılandırma dosyasını**seçin ve ardından **Ekle**' ye tıklayın.

   Visual Studio, *tsconfig. JSON* dosyasını proje köküne ekler. TypeScript derleyicisi [seçeneklerini yapılandırmak](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) için bu dosyayı kullanabilirsiniz.

1. *Tsconfig. JSON* dosyasını açın ve varsayılan kodu şu kodla değiştirin:

   ```json
   {
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

   Bu yapılandırma, TypeScript kullanımına yönelik temel bir giriş sağlar. Diğer senaryolarda, örneğin, [Gulp veya WebPack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)kullanırken, transpiled JavaScript dosyaları için *Wwwroot/js*yerine araçlar ve yapılandırma tercihlerinize bağlı olarak farklı bir ara konum isteyebilirsiniz.

1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve **> yeni klasör ekle**' yi seçin. Yeni klasör için ad *betikleri* kullanın.

1. *Betikler* klasörüne sağ tıklayın ve **> yeni öğe Ekle**' yi seçin. **TypeScript dosyasını**seçin, dosya adı için *app. TS* adını yazın ve ardından **Ekle**' ye tıklayın.

   Visual Studio, *Scripts* klasörüne *app. TS* ekler.

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

    Visual Studio, TypeScript kodunuz için IntelliSense desteği sağlar.

    Bunu test etmek için, `.lastName` işlevinden kaldırın `greeter` , ardından "." öğesini yeniden yazın ve IntelliSense ' i görürsünüz.

    ![IntelliSense 'i görüntüle](../javascript/media/aspnet-core-ts-intellisense.png)

    `lastName`Son adı koda geri eklemeyi seçin.

1. *Görünümler/giriş* klasörünü açın ve *index. html*dosyasını açın.

1. Aşağıdaki HTML kodunu dosyanın sonuna ekleyin.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. *Görünümler/paylaşılan* klasörünü açın ve ardından *_Layout. cshtml*dosyasını açın.

1. Çağrısının önüne şu komut dosyası başvurusunu ekleyin `@RenderSection("Scripts", required: false)` :

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Uygulama oluşturma

1. **Build > Build Solution**öğesini seçin.

   Uygulamayı çalıştırdığınızda otomatik olarak oluştursa da, yapı işlemi sırasında gerçekleşen bir şeye göz atmak istiyoruz.

1. *Wwwroot/js* klasörünü açın ve iki yeni dosya, *app. js* ve kaynak eşleme dosyası olan *app. js. Map*' i bulun. Bu dosyalar TypeScript derleyicisi tarafından oluşturulur.

   Hata ayıklama için kaynak eşleme dosyaları gereklidir.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **F5** tuşuna**basın (hata ayıklama**  >  **başlatma hata**ayıklaması).

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
   > ASP.NET Core projeleri için, istemci tarafı JavaScript ve CSS dosyalarını yüklemek üzere NPM yerine [Kitaplık Yöneticisi](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) 'ni veya Yarn 'yi de kullanabilirsiniz.

1. Bu örnekte, projenize jQuery için bir TypeScript tanım dosyası ekleyin. *Package. JSON* dosyanıza aşağıdakini ekleyin.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Bu, jQuery için TypeScript desteği ekler. JQuery kitaplığı, MVC proje şablonuna zaten dahil edilmiştir (Çözüm Gezgini ' de Wwwroot/lib bölümüne bakın). Farklı bir şablon kullanıyorsanız, jQuery NPM paketini de eklemeniz gerekebilir.

1. Çözüm Gezgini paket yüklü değilse, NPM düğümüne sağ tıklayın ve **paketleri geri yükle**' yi seçin.

   >[!NOTE]
   > Bazı senaryolarda Çözüm Gezgini, [burada](https://github.com/aspnet/Tooling/issues/479)açıklanan bilinen bir sorun nedeniyle NPM paketinin *Package. JSON* ile eşitlenmemiş olduğunu gösterebilir. Örneğin, paket yüklendiğinde yüklü değil olarak görünebilir. Çoğu durumda, bu makalenin önceki kısımlarında açıklandığı gibi Package *. JSON*' u silerek, Visual Studio 'yu yeniden başlatarak ve *Package. JSON* dosyasını yeniden ekleyerek Çözüm Gezgini güncelleştirebilirsiniz.

1. Çözüm Gezgini, betikler klasörüne sağ tıklayın ve **Add**  >  **Yeni öğe**Ekle ' yi seçin.

1. **TypeScript dosyası**' nı seçin, *Library. TS*yazın ve **Ekle**' yi seçin.

1. *Library. TS*' de aşağıdaki kodu ekleyin.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString());
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Kolaylık olması için, bu kod jQuery ve uyarı kullanarak bir ileti görüntüler.

   JQuery için TypeScript tür tanımları eklendiğinde, burada gösterildiği gibi jQuery nesnesini izleyen bir "." yazdığınızda jQuery nesnelerinde IntelliSense desteği alırsınız.

   ![jQuery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. _Layout. cshtml içinde, komut dosyası başvurularını içerecek şekilde güncelleştirin `library.js` .

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. Index. cshtml 'de, dosyanın sonuna aşağıdaki HTML 'yi ekleyin.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Uygulamayı çalıştırmak için **F5** tuşuna**basın (hata ayıklama**  >  **başlatma hata**ayıklaması).

    Uygulama tarayıcıda açılır.

    JQuery sürümüne güncelleştirilmiş sayfayı görmek için uyarıda **Tamam** ' a tıklayın **: 3.3.1!!**.

    ![jQuery örneği](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Sonraki adımlar

ASP.NET Core ile TypeScript kullanma hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [ASP.NET Core ve TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
