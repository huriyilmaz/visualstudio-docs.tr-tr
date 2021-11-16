---
title: 'Öğretici: Basit bir C# konsol uygulaması oluşturma '
description: Visual Studio adım C# konsol uygulaması oluşturma hakkında bilgi edinin.
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 09496b55d971173040aa6ad69428979d4d43398a
ms.sourcegitcommit: bfae1f88c278835e26f3200cfced769be3191fc4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2021
ms.locfileid: "132535263"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio-part-1-of-2"></a>Öğretici: Visual Studio'de basit bir C# konsol uygulaması oluşturma (bölüm 1/2)

Bu öğreticide, Visual Studio C# konsol uygulaması oluşturmak ve çalıştırmak ve tümleşik geliştirme ortamının (IDE) Visual Studio keşfetmek için Visual Studio kullanırsınız. Bu öğretici, iki bölümden bir öğretici serisinin 1. bölümü.

Bu öğreticide şunları yaptınız:

> [!div class="checklist"]
> * Yeni bir Visual Studio oluşturun.
> * Bir C# konsol uygulaması oluşturun.
> * Uygulamanıza hata ayıklama.
> * Uygulamanızı kapatın.
> * Kodunuzun tamamını inceleme.

[2. bölümde,](tutorial-console-part-2.md)daha fazla proje eklemek, hata ayıklama püf noktalarını öğrenmek ve üçüncü taraf paketlerine başvuru yapmak için bu uygulamayı genişletebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Yüklü bir Visual Studio gerekir.

::: moniker range="vs-2017"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range=">=vs-2019"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeler sayfasına gidin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Başlamak için bir C# uygulama projesi oluşturun. Proje türü, ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >  
   (Alternatif olarak **Ctrl tuşuna basın** + **Üstkrkt** + **N ).**

3. Yeni Çalışma Alanı iletişim kutusunun **sol Project** **C#** öğesini genişletin ve **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından dosyayı Hesaplayıcı olarak **_adlayın._**

   ![IDE'de Yeni Uygulama iletişim kutusundaki Konsol Uygulaması (.NET Core) Project şablonunu Visual Studio görüntüsü.](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız,.NET Core platformlar arası geliştirme iş yükünü ekleyerek bu şablonu **edinebilirsiniz.** Aşağıdaki adımları uygulayın:

#### <a name="option-1-use-the-new-project-dialog-box"></a>1. Seçenek: Yeni Project iletişim kutusunu kullanın

1. Yeni **Visual Studio Yükleyicisi** iletişim kutusunun sol bölmesindeKimlik aç **Project** seçin.

   ![Yeni Dosya Aç iletişim kutusundaki Visual Studio Yükleyicisi Seç bağlantısını gösteren Project görüntüsü.](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

   ![Uygulamanın .NET Core platformlar arası geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. Seçenek: Araçlar menü çubuğunu kullanma

1. Yeni Görünüm iletişim **kutusundan Project** ve üst menü çubuğunda Araçlar Araçları **ve** Özellikleri > **Al'ı seçin.**

1. Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range="vs-2019"

1. Yeni Visual Studio'yi açın **ve Başlangıç penceresinde Yeni** proje oluştur'a tıklayın.

   ![Yeni proje oluştur penceresini gösteren ekran görüntüsü.](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde Dil** **listesinden C#** dilini seçin. Ardından, **Windows** listesinden Platform **listesinden Ve Konsol'dan** Seç'i seçin.

   Dil, platform ve proje türü filtrelerini uygulayan Konsol Uygulaması şablonunu **ve** ardından Sonraki'yi **seçin.**

   > [!NOTE]
   > Konsol Uygulaması şablonunu görmüyorsanız Daha **fazla araç** ve **özellik yükle'yi seçin.**
   >
   > ![Daha fazla araç ve özellik yükle bağlantısını gösteren ekran görüntüsü.](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.
   >
   > ![Uygulamanın .NET Core platformlar arası geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; varsa, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** Hesaplayıcı *yazın* veya **Project** girin. Ardından, **Sonraki'yi seçin.**

    :::image type="content" source="./media/vs-2019/csharp-name-your-calculator-project.png" alt-text="'Yeni projenizi yapılandırma' penceresinde projenizi 'Hesaplayıcı' olarak adlandırmayı gösteren ekran görüntüsü.":::

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET Core 3.1** zaten seçilmiş olması gerekir. Yoksa **.NET Core 3.1'i seçin.** Ardından **Oluştur'a seçin.**

    :::image type="content" source="./media/vs-2019/csharp-target-framework.png" alt-text="'Ek bilgiler' penceresinde .NET Core 3.1'in seçildiğinden emin olunan ekran görüntüsü.":::

   Visual Studio projenizi açar ve bu da varsayılan "Merhaba Dünya" kodunu içerir.

::: moniker-end
::: moniker range=">=vs-2022"

1. Yeni Visual Studio'yi açın **ve Başlangıç penceresinde Yeni** proje oluştur'a tıklayın.

   ![Yeni proje oluştur penceresini gösteren ekran görüntüsü.](media/vs-2022/create-new-project.png)

1. Yeni proje **oluştur penceresinde Tüm** diller'i **ve** ardından açılan listeden **C#** öğesini seçin. Tüm **Windows** listesinden **Tüm platformlar'ı** seçin ve Tüm **proje** türleri **listesinden Konsol'a** tıklayın.

   Dil, platform ve proje türü filtrelerini uygulayan Konsol Uygulaması şablonunu **ve** ardından Sonraki'yi **seçin.**

   > [!NOTE]
   > Konsol Uygulaması şablonunu görmüyorsanız Daha **fazla araç** ve **özellik yükle'yi seçin.**
   >
   > ![Daha fazla araç ve özellik yükle bağlantısını gösteren ekran görüntüsü.](media/vs-2022/not-finding-what-looking-for.png)
   >
   > Uygulamanın Visual Studio Yükleyicisi **.NET** masaüstü geliştirme iş yükünü ve ardından Değiştir'i **seçin.**
   >
   > ![Uygulamanın .NET masaüstü geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.](media/vs-2022/dot-net-development-workload.png)

1. Yeni **projenizi yapılandır penceresine** Hesap makinesi adı kutusuna *Hesaplayıcı* **yazın veya Project'yi** **seçin.**

   ![Yeni projenizi yapılandır penceresinde proje Hesaplayıcısını adlandırmayı gösteren ekran görüntüsü.](media/vs-2022/csharp-name-your-calculator-project.png)

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET 6.0** zaten seçilmiş olması gerekir. **Oluştur**’u seçin.

   ![Ek bilgiler penceresinde .NET 6.0'ın seçili olduğunu gösteren ekran görüntüsü.](media/vs-2022/csharp-target-framework.png)

   Visual Studio projenizi açar ve bu da varsayılan "Merhaba Dünya" kodunu içerir.

::: moniker-end

## <a name="create-the-app"></a>Uygulama oluşturma

Bu bölümde şunları yapacaksınız:

- C# ile bazı temel tamsayı matematiklerini keşfedin.
- Temel bir hesap makinesi uygulaması oluşturmak için kod ekleyin.
- Hataları bulmak ve düzeltmek için uygulamada hata ayıklama.
- Kodu geliştirin ve daha verimli hale getirir.

### <a name="explore-integer-math"></a>Tamsayı matematiğini inceleme

C# ile bazı temel tamsayı matematikleriyle başlama.

::: moniker range="<=vs-2019"
1. Kod düzenleyicisinde varsayılan "Merhaba Dünya silin.

    ![Yeni hesaplayıcı uygulamanıza varsayılan Merhaba Dünya silmeyi gösteren ekran görüntüsü.](./media/csharp-console-calculator-deletehelloworld.png)

   Özellikle şöyle bir satır `Console.WriteLine("Hello World!");` silin: .

1. Yerine aşağıdaki kodu yazın:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Bunu yapmak için Visual Studio'daki IntelliSense özelliğinin girişi otomatik tamamlama seçeneği sunduğuna dikkat edin.

    > [!NOTE]
    > Aşağıdaki animasyon, önceki kodu yinelemek için amaçlanan bir animasyondur. Yalnızca otomatik tamamlama özelliğinin nasıl çalıştığını göstermek için tasarlanmıştır.

    ![IDE'de IntelliSense otomatik tamamlama özelliğini gösteren tamsayı matematik Visual Studio animasyonu.](./media/integer-math-intellisense.gif)

1. Programlarınızı **derlemek ve** çalıştırmak için **Hesaplayıcı'nın** yanındaki yeşil Başlat düğmesini seçin veya **F5 tuşuna basın.**

   ![Araç çubuğundan uygulamayı çalıştırmak için Hesap makinesi düğmesini seçmeyi gösteren ekran görüntüsü.](./media/csharp-console-calculator-button.png)

   42 + **119** toplamını (161) ortaya koyan bir konsol penceresi açılır.

    ![Tamsayı matematiği sonuçlarının yer alan konsol penceresini gösteren ekran görüntüsü.](./media/csharp-console-integer-math.png)

1. **(İsteğe bağlı)** Sonucu değiştirmek için işleci değiştirebilirsiniz. Örneğin, kod satırındaki işleci çıkarma, çarpma veya `+` `int c = a + b;` bölme için olarak `-` `*` `/` değiştirebilirsiniz. Ardından programı çalıştırarak sonuç da değişir.

1. Konsol penceresini kapatın.
::: moniker-end

::: moniker range=">=vs-2022"
1. Dosya **Çözüm Gezgini,** sağ bölmede **Program.cs'yi** seçerek dosyayı kod düzenleyicisinde görüntüleyin

1. Kod düzenleyicisinde, varsayılan "Merhaba Dünya" kodunu `Console.WriteLine("Hello World!");` değiştirin.

    ![Program dosyasında değiştirilen satırı gösteren ekran görüntüsü.](media/vs-2022/csharp-console-calculator-delete-hello-world.png)

   satırı aşağıdaki kodla değiştirin:

   ```csharp
       int a = 42;
       int b = 119;
       int c = a + b;
       Console.WriteLine(c);
       Console.ReadKey();
   ```

    Kodu yazabilirseniz, Visual Studio IntelliSense özelliği girişi otomatik tamamlama seçeneği sunar.

    > [!NOTE]
    > Aşağıdaki animasyon önceki kodu göstermek için değil, yalnızca IntelliSense'in nasıl çalıştığını göstermek için tasarlanmıştır.

    ![IDE'de IntelliSense otomatik tamamlama özelliğini gösteren tamsayı matematik Visual Studio animasyonu.](media/integer-math-intellisense.gif)

1. Uygulamanızı derlemek ve çalıştırmak için **F5 tuşuna** basın veya üst araç çubuğunda Hesaplayıcı adının **yanındaki** yeşil oku seçin.

   ![Hata Ayıklama araç çubuğundan uygulamayı çalıştırmak için Hesaplayıcı düğmesini seçmeyi gösteren ekran görüntüsü.](media/vs-2022/csharp-console-calculator-button.png)

   161 olan 42 + 119 toplamını gösteren bir konsol **penceresi açılır.**

    ![Tamsayı matematiği sonuçlarını gösteren Konsol penceresinin ekran görüntüsü.](media/vs-2022/csharp-console-integer-math.png)

1. Konsol penceresini kapatın.

1. İsteğe bağlı olarak, sonucu değiştirmek için işleci değiştirebilirsiniz. Örneğin, kod satırındaki işleci çıkarma, çarpma veya `+` `int c = a + b;` bölme için olarak `-` `*` `/` değiştirebilirsiniz. Uygulamayı çalıştırarak sonuç uygun şekilde değişir.

::: moniker-end

### <a name="add-code-to-create-a-calculator"></a>Hesap makinesi oluşturmak için kod ekleme

Projenize daha karmaşık bir hesap makinesi kodu kümesi ekleyerek devam edebilirsiniz.

1. Kod düzenleyicisinde *program.cs'de* yer alan tüm kodu aşağıdaki yeni kodla değiştirin:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero.
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app.
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number.
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number.
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option.
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math.
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                }
                // Wait for the user to respond before closing.
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

1. Hesaplayıcı **düğmesini** seçin veya **F5 tuşuna** basarak uygulamanızı çalıştırın.

   Bir konsol penceresi açılır.

1. Konsol penceresinde, **42** ve **119** numaralarını birlikte eklemek için istemleri izleyin.

   Uygulamanın aşağıdaki ekran görüntüsüne benzer olması gerekir:

    ![Hesap makinesi uygulamasını istemlerle birlikte gösteren Konsol penceresinin ekran görüntüsü.](media/csharp-console-calculator.png)

### <a name="add-decimal-functionality"></a>Ondalık işlev ekleme

Şimdi daha fazla işlev eklemek için kodu ince ince ince ayarla.

Geçerli hesap makinesi uygulaması yalnızca tam sayıları kabul eder ve döndürür. Örneğin, uygulamayı çalıştırarak 42 sayısını 119 sayısına böler ve sonucun sıfır olması kesin değildir.

![Hesap makinesi uygulamasının sonuç olarak bir tam sayı döndüren konsol penceresinin ekran görüntüsü.](./media/csharp-console-calculator-nodecimal.png)

Ondalıkları işerek duyarlığı geliştirmek için kodu düzeltmek için:

1. Yeni *düzenleyicide program.cs* Visual Studio **Ctrl** + **H tuşlarına** basarak **Bul ve Değiştir denetimine** basın.

1. Denetime *int* yazın ve Değiştir *alanına float* **yazın.**

1. Eşleşme büyük/küçük **harf ve Denetimde** Tam sözcüğü **eşle** simgelerini seçin veya **Alt** C ve +  Alt W **tuşlarına** + **basın.**

1. Tümleri **değiştir simgesini seçin** veya arama ve değiştirme için **Alt** + **A** tuşuna basın.

    ![Int değişkeninin float olarak değiştirilmesini gösteren Bul ve Değiştir denetimi animasyonu.](media/find-replace-control-animation.gif)

1. Hesap makinesi uygulamanızı yeniden çalıştırın ve **42 sayısını** **119 sayısına bölün.**

   Uygulama artık sıfır yerine ondalık sayı döndürür.

    ![Şimdi sonuç olarak ondalık sayı döndüren Hesap makinesi uygulamasını gösteren Konsol penceresinin ekran görüntüsü.](media/csharp-console-calculator-decimal.png)

Artık uygulama ondalık sonuçlar üretebilir. Uygulamanın ondalık basamakları da hesaplayana kadar kodda birkaç değişiklik daha yapma.

1. Değişkenin **her örneğini olarak** değiştirmek ve yönteminin her örneğini olarak değiştirmek için Bul ve Değiştir `float` `double` `Convert.ToInt32` denetimlerini `Convert.ToDouble` kullanın.

1. Hesap makinesi uygulamanızı çalıştırın ve **42,5 sayısını** **119,75 sayısına bölün.**

   Uygulama artık ondalık değerleri kabul eder ve sonucu olarak daha uzun bir ondalık sayı döndürür.

    ![Artık ondalık sayıları kabul eden ve daha uzun ondalık sonuç döndüren Hesap makinesi uygulamasını gösteren Konsol penceresinin ekran görüntüsü.](media/csharp-console-calculator-usedecimals.png)

   Kodu [düzelt bölümünde,](#revise-the-code) sonuçlarda ondalık basamak sayısını azaltabilirsiniz.

## <a name="debug-the-app"></a>Uygulamada hata ayıklama

Temel hesap makinesi uygulamanızı iyileştirebilirsiniz ancak uygulamanız henüz kullanıcı girişi hataları gibi özel durumları işlemez. Örneğin, kullanıcılar sıfıra bölmeyi veya beklenmeyen bir karakter girmeyi denerse uygulama çalışmayı durdurabilir, hata döndürür veya beklenmeyen bir sayısal olmayan sonuç döndürür.

Şimdi birkaç yaygın kullanıcı girişi hatasını adım adım irdeleelim, hata ayıklayıcısında bu hataları bu hata ayıklayıcıda bulup kodda düzeltelim.

> [!TIP]
> Hata ayıklayıcısı ve nasıl çalıştığını görmek için bkz. Hata [ayıklayıcısının Visual Studio bakın.](../../debugger/debugger-feature-tour.md)

### <a name="fix-the-divide-by-zero-error"></a>"Sıfıra bölme" hatasını düzeltme

Bir s numarayı sıfıra bölmeye çalışırsanız konsol uygulaması donabilir ve kod düzenleyicisinde neyin yanlış olduğunu gösterir.

   !['Sıfıra Visual Studio bölmeye çalışıldı' hatası için sarı renkle vurgulanmış bir satırı ve Özel Durum İşlenemedi hatasını gösteren kod düzenleyicisinin ekran görüntüsü.](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> Bazen uygulama donmaz ve hata ayıklayıcı sıfıra bölme hatası göstermez. Bunun yerine uygulama, sonsuz simgesi gibi beklenmeyen bir sayısal olmayan sonuç dönüşe neden olabilir. Aşağıdaki kod düzeltmesi hala geçerlidir.

Kodu bu hatayı işlemek için değiştirmek için:

1. *program.cs'de* ile arasındaki `case "d":` kodu aşağıdaki kodla ifade eden `// Wait for the user to respond before closing` açıklamayı değiştirin:

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so.
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   Kodu değiştirdikten sonra bölümü deyimiyle `switch` aşağıdaki ekran görüntüsüne benzer şekilde görüntü gerekir:

   ![Yeni kod düzenleyicisinde düzeltilmiş anahtar bölümünü Visual Studio ekran görüntüsü.](media/csharp-console-calculator-switch-code.png)

Şimdi, herhangi bir sayı sıfıra böldükçe uygulama başka bir sayı ister ve siz sıfır olmayan bir sayı sağlayana kadar sormaya devam ediyor.

   ![Sıfır olmayan bir sayı sağlamak için tekrarlanan bir istem ile Konsol penceresinin ekran görüntüsü.](media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>"Biçim" hatasını düzeltme

Uygulama sayısal karakter beklediğinizde alfabetik bir karakter girersiniz, uygulama donar. Visual Studio düzenleyicide neyin yanlış olduğunu gösterir.

   ::: moniker range="<=vs-2019"
   ![İşlenemeyen biçim hatasını kod düzenleyicisinde Visual Studio ekran görüntüsü.](media/csharp-console-calculator-format-error.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![İşlenemeyen biçim hatasını kod düzenleyicisinde Visual Studio ekran görüntüsü.](media/vs-2022/csharp-console-calculator-format-error.png)
   ::: moniker-end

Bu özel durumu önlemek için daha önce girdiğiniz kodu yeniden düzenlemeyi sebilirsiniz.

#### <a name="revise-the-code"></a>Kodu düzeltme

Tüm kodu işlemek `program` için sınıfına güvenmek yerine, uygulamanızı iki sınıfa bölebilirsiniz: `Calculator` ve `Program` .

sınıfı hesaplama işlerinin büyük bir kısmını işler ve sınıfı kullanıcı arabirimini ve hata `Calculator` işleme çalışmalarını `Program` işler.

Haydi başlayalım.

1. *program.cs içinde,* ad alanı içinde açılış ve `Calculator` kapanış ayraçları arasındaki her şeyi silin:

    ```csharp
    using System;

    namespace Calculator
    {

    }
    ```

1. Küme ayraçları arasına aşağıdaki yeni sınıfı `Calculator` ekleyin:

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. Ayrıca, aşağıdaki gibi  `Program` yeni bir sınıf ekleyin:

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
    ```

1. Hesaplayıcı **düğmesini** seçin veya **F5 tuşuna** basarak uygulamanızı çalıştırın.

1. yönergelerini izleyin ve **42** sayısını **119 sayısına bölün.** Sonuçlarınız aşağıdaki ekran görüntüsüne benzer şekilde görüntü gerekir:

   ::: moniker range="<=vs-2019"
   ![Yeniden düzenleme yapılan Hesaplayıcı uygulamasının yer alan Konsol penceresini gösteren ekran görüntüsü.](media/csharp-console-calculator-refactored.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Yeniden düzenleme yapılan Hesaplayıcı uygulamasının yer alan Konsol penceresini gösteren ekran görüntüsü.](media/vs-2022/csharp-console-calculator-refactored.png)
   ::: moniker-end

   Artık konsol uygulamasını kapatmayı seçene kadar daha fazla denklem girebilirsiniz. Ayrıca sonuçlarda daha az ondalık basamak vardır. Ayrıca yanlış bir karakter girersiniz, uygun bir hata yanıtı alırsınız.

## <a name="close-the-app"></a>Uygulamayı kapatma

1. Henüz bunu yapmadıysanız Hesap makinesi uygulamasını kapatın.

1. Bölmede **Çıkış** bölmesini Visual Studio.

   ![Giriş bölmesindeki Çıkış bölmesini kapatmayı gösteren Visual Studio.](media/csharp-calculator-close-output-pane.png)

1. Uygulama Visual Studio kaydetmek için **Ctrl** + **S** tuşlarına basın.

[!INCLUDE[../includes/git-source-control.md](../includes/git-source-control.md)]

## <a name="review-code-complete"></a>Gözden geçirme: Kod tamamlandı

Bu öğreticide hesap makinesi uygulamasında birçok değişiklik yaptık. Uygulama artık bilgi işlem kaynaklarını daha verimli bir şekilde ele almaktadır ve kullanıcı giriş hatalarının çoğunu ele almaktadır.

Kodun hepsi tek bir yerde olacak şekilde tam olarak şu şekildedir:

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
}

```

## <a name="next-steps"></a>Sonraki adımlar

:::moniker range="vs-2017"

Diğer öğreticilerle devam edin:

> [!div class="nextstepaction"]
> [C# öğreticileri](/dotnet/csharp/tutorials)

> [!div class="nextstepaction"]
> [Visual Studio IDE'de gezinme](../visual-studio-ide.md)

:::moniker-end

:::moniker range=">=vs-2019"

Bu öğreticinin ikinci bölümüyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici 2. Bölüm: C# konsol uygulamanızı genişletme ve hata ayıklama](tutorial-console-part-2.md)
:::moniker-end
