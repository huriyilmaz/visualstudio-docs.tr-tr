---
title: TypeScript ile ASP.NET Core uygulaması oluşturma
description: Bu eğitimde, ASP.NET Core ve TypeScript kullanarak bir uygulama oluşturmak
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
ms.openlocfilehash: e212aec6d2d3aa7e20cb0ca08c9ea604f32bb08c
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988555"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Öğretici: Visual Studio TypeScript ile ASP.NET Core uygulaması oluşturun

Visual Studio geliştirme ASP.NET Core ve TypeScript için bu eğitimde, basit bir web uygulaması oluşturmak, bazı TypeScript kodu eklemek ve sonra uygulamayı çalıştırın. 

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
> * ASP.NET Core projesi oluşturma
> * TypeScript desteği için NuGet paketini ekleyin
> * Bazı TypeScript kodu ekleme
> * Uygulamayı çalıştırma
> * npm kullanarak bir üçüncü taraf kitaplığı ekleme

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve web geliştirme iş yükü ASP.NET olmalıdır.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'u henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'yi henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekiyorsa ancak visual studio'ya zaten sahipseniz, **Visual** > Studio Installer'ı açan**Araçlar Ve Özellikler...'** a gidin. ASP.NET **ve web geliştirme** iş yükünü seçin ve ardından **Değiştir'i**seçin.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Yeni bir ASP.NET Core MVC projesi oluşturma

Visual Studio, *projedeki*tek bir uygulamaiçin dosyaları yönetir. Proje kaynak kodu, kaynaklar ve yapılandırma dosyalarını içerir.

>[!NOTE]
> Boş bir ASP.NET Core projesiyle başlamak ve Bir TypeScript ön ucu eklemek için, bunun yerine [TypeScript ile ASP.NET Core'a](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) bakın.

Bu eğitimde, ASP.NET Core MVC uygulaması nın kodunu içeren basit bir projeyle başlarsınız.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresi açık değilse, **Dosya** > **Başlangıç Penceresi'ni**seçin. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin. Dil açılır listesinde **C#** seçeneğini belirleyin. Arama kutusunda, **ASP.NET**yazın, ardından **ASP.NET Core Web Application'ı**seçin. **İleri**’yi seçin.

    Proje için bir ad yazın ve **Oluştur'u**seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni Proje** iletişim kutusunun sol bölmesinde **Visual C#** seçeneğini genişletin ve **ardından .NET Core'u**seçin. Orta bölmede, **Core Web Application - C# ASP.NET**seçin, ardından **Tamam'ı**seçin.
    ::: moniker-end
    **ASP.NET Çekirdek Web Uygulaması** proje şablonu görmüyorsanız, ASP.NET ve web **geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı talimatlar için [Önkoşullar'a](#prerequisites)bakın.

1. Görüntülenen iletişim kutusunda, iletişim kutusunda **Web Uygulaması 'nı (Model-View-Controller)** seçin ve ardından **Oluştur'u** (veya **Tamam)'ı**seçin.

   ![MVC şablonu seçin](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio yeni çözümü oluşturur ve projenizi doğru bölmede açar.

## <a name="add-some-code"></a>Bazı kod ekleme

1. Çözüm Gezgini'nde (sağ bölme). proje düğümüne sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. **Gözat** sekmesinde, **Microsoft.TypeScript.MSBuild'i**arayın ve paketi yüklemek için sağtarafta **Yükle'yi** tıklatın.

   ![NuGet paketi ekle](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio, Solution Explorer'daki **Bağımlılıkdüğümün** altına NuGet paketini ekler.

   > [!NOTE]
   > Bu öğretici NuGet paketini gerektirir. Alternatif olarak, kendi uygulamalarınızda [TypeScript npm paketini](https://www.npmjs.com/package/typescript)kullanmak isteyebilirsiniz.

1. Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve **Yeni Klasör > ekle'yi**seçin. Yeni klasör için ad *komut dosyalarını* kullanın.

1. *Komut dosyaları* klasörüne sağ tıklayın ve Yeni Öğe **> ekle'yi**seçin. **TypeScript JSON Yapılandırma Dosyasını**seçin ve sonra **Ekle'yi**tıklatın.

   Visual Studio *komut dosyası* klasörüne *tsconfig.json* dosyasını ekler. TypeScript derleyicisi için [seçenekleri yapılandırmak](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) için bu dosyayı kullanabilirsiniz.

1. *tsconfig.json'u* açın ve varsayılan kodu aşağıdaki kodla değiştirin:

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "../wwwroot/js"
     },
     "exclude": [
       "node_modules",
       "wwwroot"
     ]
   }
   ```

   *OutDir* seçeneği, TypeScript derleyicisi tarafından aktarılan javascript dosyalarının çıktı klasörünü belirtir.

   Bu yapılandırma, TypeScript'i kullanmak için temel bir giriş sağlar. Diğer senaryolarda, örneğin [yudum veya web paketi](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)kullanırken, araçlarınıza ve yapılandırma tercihlerinize bağlı olarak, aktarılan JavaScript dosyaları için farklı bir ara konum isteyebilirsiniz. * /wwwroot/js*.

1. *Komut dosyaları* klasörüne sağ tıklayın ve Yeni Öğe **> ekle'yi**seçin. **TypeScript Dosyası'nı**seçin, dosya adı için *app.ts* adını yazın ve sonra **Ekle'yi**tıklatın.

   Visual Studio *komut dosyaları* klasörüne *app.ts* ekler.

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

    Visual Studio, TypeScript kodunuz için IntelliSense desteği sağlar.

    Bunu sınamak `.lastName` için `greeter` işlevden kaldırın, ardından "."'yi yeniden yazın ve IntelliSense'i görün.

    ![IntelliSense'i görüntüle](../javascript/media/aspnet-core-ts-intellisense.png)

    Soyadını koda geri eklemek için seçin. `lastName`

1. *Görünümler / Giriş* klasörünü açın ve *ardından index.html'i*açın.

1. Aşağıdaki HTML kodunu dosyanın sonuna ekleyin.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. *Görünümler / Paylaşılan* klasörü açın ve sonra *_Layout.cshtml'i*açın.

1. Aramadan önce aşağıdaki komut `@RenderSection("Scripts", required: false)`dosyası başvurularını ekleyin:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Uygulama oluşturma

1. **Yapı > Çözüm Oluştur'u**seçin.

   Uygulama çalıştırdığınızda otomatik olarak oluştursa da, oluşturma işlemi sırasında meydana gelen bir şeye bir göz atmak istiyoruz.

1. *wwwroot / js* klasörünü açın ve iki yeni dosya, *app.js* ve kaynak harita dosyası, *app.js.map*bulabilirsiniz. Bu dosyalar TypeScript derleyicisi tarafından oluşturulur.

   Hata ayıklama için kaynak harita dosyaları gereklidir.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **F5** **(Hata** > **Ayıklama Hata Ayıklama)** tuşuna basın.

    Uygulama bir tarayıcıda açılır.

    Tarayıcı penceresinde **Hoş Geldiniz** başlığını ve **Beni Tıklat** düğmesini görürsünüz.

    ![TypeScript ile ASP.NET Çekirdek](../javascript/media/aspnet-core-ts-running-app.png)

1. TypeScript dosyasında belirttiğimiz iletiyi görüntülemek için düğmeyi tıklatın.

## <a name="debug-the-application"></a>Uygulamada hata ayıklama

1. Kod düzenleyicisindeki `greeter` sol `app.ts` kenar boşluğunu tıklatarak işlevde bir kesme noktası ayarlayın.

    ![Kesme noktası ayarlama](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Uygulamayı çalıştırmak için **F5**'e basın.

   Komut dosyası hata ayıklamasını etkinleştirmek için bir iletiyi yanıtlamanız gerekebilir.

   Uygulama kesme noktasında duraklar. Artık değişkenleri inceleyebilir ve hata ayıklama özelliklerini kullanabilirsiniz.

## <a name="add-typescript-support-for-a-third-party-library"></a>Üçüncü taraf kitaplığı için TypeScript desteği ekleme

1. Projenize bir `package.json` dosya eklemek için [npm paket yönetimindeki](../javascript/npm-package-management.md#aspnet-core-projects) yönergeleri izleyin. Bu, projenize nPM desteği ekler.

   >[!NOTE]
   > ASP.NET Core projeleri için, istemci tarafındaki JavaScript ve CSS dosyalarını yüklemek için npm yerine [Kitaplık Yöneticisi](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) veya iplik de kullanabilirsiniz.

1. Bu örnekte, projenize jQuery için bir TypeScript tanım dosyası ekleyin. *Paket.json* dosyanıza aşağıdakileri ekleyin.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Bu jQuery için TypeScript desteği ekler. JQuery kitaplığı zaten MVC proje şablonuna dahildir (Solution Explorer'da wwwroot/lib'in altına bakın). Farklı bir şablon kullanıyorsanız, jquery npm paketini de eklemeniz gerekebilir.

1. Solution Explorer'daki paket yüklenmezse, npm düğümüne sağ tıklayın ve **Paketleri Geri Yükle'yi**seçin.

   >[!NOTE]
   > Bazı senaryolarda, Solution Explorer, [burada](https://github.com/aspnet/Tooling/issues/479)açıklanan bilinen bir sorun nedeniyle bir npm paketinin *package.json* ile eşitlenmemiş olduğunu gösterebilir. Örneğin, paket yüklendiğinde yüklü değilmiş gibi görünebilir. Çoğu durumda, *package.json'u*silerek Solution Explorer'ı güncelleştirebilirsiniz, Visual Studio'yu yeniden başlatabilir ve bu makalede daha önce açıklandığı gibi *package.json* dosyasını yeniden ekleyebilirsiniz.

1. Çözüm Gezgini'nde, komut dosyaları klasörüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin.

1. **TypeScript Dosyası'nı**seçin, *library.ts*yazın ve **Ekle'yi**seçin.

1. *library.ts*olarak, aşağıdaki kodu ekleyin.

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

   Basitlik için, bu kod jQuery ve bir uyarı kullanarak bir ileti görüntüler.

   JQuery için TypeScript türü tanımları eklendi, burada gösterildiği gibi bir jQuery nesnesi aşağıdaki bir "." yazdığınızda jQuery nesneleri üzerinde IntelliSense desteği olsun.

   ![jquery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. _Layout.cshtml'de, komut dosyası `library.js`başvurularını içerecek şekilde güncelleştirin.

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. Index.cshtml'de, dosyanın sonuna aşağıdaki HTML'yi ekleyin.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Uygulamayı çalıştırmak için **F5** **(Hata** > **Ayıklama Hata Ayıklama)** tuşuna basın.

    Uygulama tarayıcıda açılır.

    JQuery sürümü ne kadar güncellenen sayfayı görmek için uyarı da **Tamam'ı** **tıklatın: 3.3.1!!**.

    ![jquery örneği](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Sonraki adımlar

ASP.NET Core ile TypeScript'i kullanma hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [ASP.NET Çekirdek ve TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
