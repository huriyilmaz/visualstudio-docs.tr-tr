---
title: TypeScript ile ASP.NET Core uygulaması oluşturma
description: Bu öğreticide, ASP.NET Core ve TypeScript kullanarak bir uygulama oluşturacaksınız
ms.date: 01/03/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 40011b035afdf4a04eb760d13c001e39d9c578c4
ms.sourcegitcommit: 91a054beb6b3a16ed5140f9f829239ec31bbbec8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75810589"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Öğretici: Visual Studio 'da TypeScript ile ASP.NET Core uygulaması oluşturma

Visual Studio geliştirme ASP.NET Core ve TypeScript için bu öğreticide, basit bir Web uygulaması oluşturun, bazı TypeScript kodu ekleyin ve ardından uygulamayı çalıştırın. 

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yüklemek için sayfa.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) ücretsiz yüklemek için sayfa.

::: moniker-end

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> * ASP.NET Core projesi oluşturma
> * TypeScript desteği için NuGet paketini ekleyin
> * Bazı TypeScript kodu ekle
> * Uygulamayı çalıştırma

## <a name="prerequisites"></a>Prerequisites

* Visual Studio 'Nun yüklü olması ve ASP.NET Web geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan **Araçlar ve Özellikler al** > **Araçlar** ' a gidin. **ASP.net ve Web geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Yeni bir ASP.NET Core MVC projesi oluşturma

Visual Studio, *projedeki*tek bir uygulama için dosyaları yönetir. Proje kaynak kodu, kaynakları ve yapılandırma dosyalarını içerir.

Bu öğreticide, ASP.NET Core MVC uygulaması için kod içeren basit bir proje ile başlarsınız.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **ASP.net**yazıp **C#ASP.NET Core Web uygulaması**' nı seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**. **Yeni proje** iletişim kutusunun sol bölmesinde, **C#görsel**' i genişletin ve ardından **.NET Core**' u seçin. Orta bölmede **ASP.NET Core Web uygulaması C#** ' nı ve ardından **Tamam**' ı seçin.
    ::: moniker-end
    **ASP.NET Core Web uygulaması** proje şablonunu görmüyorsanız, **ASP.net ve Web geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

1. **Oluştur**' u seçtikten sonra Iletişim kutusunda **Web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **Oluştur**' u seçin.

   ![MVC şablonunu seçin](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio yeni çözümü oluşturur ve projenizi sağ bölmede açar.

## <a name="add-some-code"></a>Kod ekleme

1. Çözüm Gezgini (sağ bölme). proje düğümüne sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. **Araştır** sekmesinde, **Microsoft. TypeScript. MSBuild**' i arayın ve ardından, paketi yüklemek için **sağdaki aç '** a tıklayın.

   ![NuGet paketi Ekle](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio, NuGet paketini Çözüm Gezgini içindeki **Bağımlılıklar** düğümüne ekler.

   > [!NOTE]
   > Bu öğretici NuGet paketini gerektirir. Alternatif olarak, kendi uygulamalarınızda [TypeScript NPM paketini](https://www.npmjs.com/package/typescript)kullanmak isteyebilirsiniz.

1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve **> yeni klasör ekle**' yi seçin. Yeni klasör için ad *betikleri* kullanın.

1. *Betikler* klasörüne sağ tıklayın ve **> yeni öğe Ekle**' yi seçin. **TYPESCRIPT JSON yapılandırma dosyasını**seçin ve ardından **Ekle**' ye tıklayın.

   Visual Studio, *tsconfig. JSON* dosyasını *Scripts* klasörüne ekler. TypeScript derleyicisi [seçeneklerini yapılandırmak](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) için bu dosyayı kullanabilirsiniz.

1. *Tsconfig. JSON* dosyasını açın ve varsayılan kodu şu kodla değiştirin:

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

   *OutDir* seçeneği, TypeScript derleyicisi tarafından transpiled olan plan JavaScript dosyaları için çıkış klasörünü belirtir.

   Bu yapılandırma, TypeScript kullanımına yönelik temel bir giriş sağlar. Diğer senaryolarda, örneğin, [Gulp veya WebPack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)kullanırken, Araçlar ve yapılandırma tercihlerinize bağlı olarak, transpiled JavaScript dosyaları için farklı bir ara konum isteyebilirsiniz *. /Wwwroot/js*.

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

    Bunu test etmek için `greeter` işlevinden `.lastName` kaldırın, ardından "." öğesini yeniden yazın ve IntelliSense 'i görürsünüz.

    ![IntelliSense 'i görüntüle](../javascript/media/aspnet-core-ts-intellisense.png)

    Son adı koda geri eklemek için `lastName` ' ı seçin.

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

1. `@RenderSection("Scripts", required: false)`çağrısından önce aşağıdaki komut dosyası başvurusunu ekleyin:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Uygulama oluşturma

1. **Build > Build Solution**öğesini seçin.

   Uygulamayı çalıştırdığınızda otomatik olarak oluştursa da, yapı işlemi sırasında gerçekleşen bir şeye göz atmak istiyoruz.

1. *Wwwroot/js* klasörünü açın ve iki yeni dosya, *app. js* ve kaynak eşleme dosyası olan *app. js. Map*' i bulun. Bu dosyalar TypeScript derleyicisi tarafından oluşturulur.

   Hata ayıklama için kaynak eşleme dosyaları gereklidir.

## <a name="run-the-application"></a>Uygulamayı çalıştırın

1. Uygulamayı çalıştırmak için **F5** tuşuna**basın (hata ayıklama > ** **başlatın**).

    Uygulama bir tarayıcıda açılır.

    Tarayıcı penceresinde, **hoş geldiniz** başlığını ve **bana tıklama** düğmesini görürsünüz.

    ![TypeScript ile ASP.NET Core](../javascript/media/aspnet-core-ts-running-app.png)

1. TypeScript dosyasında belirttiğimiz iletiyi göstermek için düğmeye tıklayın.

## <a name="debug-the-application"></a>Uygulamada hata ayıklama

1. Kod düzenleyicisinde sol kenar boşluğuna tıklayarak `app.ts` `greeter` işlevinde bir kesme noktası ayarlayın.

    ![Bir kesme noktası belirleyin](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Uygulamayı çalıştırmak için **F5**'e basın.

   Betik hata ayıklamasını etkinleştirmek için bir iletiye yanıt almanız gerekebilir.

   Uygulama kesme noktasında duraklatılır. Şimdi, değişkenleri inceleyebilir ve hata ayıklayıcı özellikleri kullanabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

ASP.NET Core ile TypeScript kullanma hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [ASP.NET Core ve TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
