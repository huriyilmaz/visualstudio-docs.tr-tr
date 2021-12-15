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
ms.openlocfilehash: b7bb5dae6761409c6d1dc9f80ec26dedc155b229
ms.sourcegitcommit: 04fb8ba0f7ea73ba17baa88f10563c8600e7fd7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "135121765"
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

Daha önce yüklememiş Visual Studio indirmeler [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına gidip ücretsiz yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [Visual Studio](https://visualstudio.microsoft.com/downloads) sayfasına gidip ücretsiz yükleyin.

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

1. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

   ![Uygulamanın .NET Core platformlar arası geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. Seçenek: Araçlar menü çubuğunu kullanma

1. Yeni Görünüm iletişim **kutusundan Project** ve üst menü çubuğunda Araçlar Araçları ve **Özellikleri** > **Al'ı seçin.**

1. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

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
   > Uygulama Visual Studio Yükleyicisi **.NET** masaüstü geliştirme iş yükünü ve ardından Değiştir'i **seçin.**
   >
   > ![Uygulamanın .NET masaüstü geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.](media/vs-2022/dot-net-development-workload.png)

1. Yeni **projenizi yapılandır penceresine** Hesap makinesi adı kutusuna *Hesaplayıcı* **yazın Project girin** ve ardından Sonraki'yi **seçin.**

   ![Yeni projenizi yapılandır penceresinde proje Hesaplayıcısını adlandırmayı gösteren ekran görüntüsü.](media/vs-2022/csharp-name-your-calculator-project.png)

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET 6.0** zaten seçilmiş olması gerekir. **Oluştur**’u seçin.

   ![Ek bilgiler penceresinde .NET 6.0'ın seçili olduğunu gösteren ekran görüntüsü.](media/vs-2022/csharp-target-framework.png)

   Visual Studio projenizi açar ve bu da varsayılan "Merhaba Dünya" kodunu içerir.
   
   > [!NOTE]
   > .NET 6'dan başlayarak, konsol şablonunu kullanan yeni projeler önceki sürümlerden farklı kod oluşturur. Daha fazla bilgi edinmek için [Yeni C# şablonları üst düzey deyimler oluşturma sayfasına](/core/tutorials/top-level-templates.md) bakın. 

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

    ![Varsayılan hesaplayıcı kodunu yeni Merhaba Dünya silmeyi gösteren ekran görüntüsü.](./media/csharp-console-calculator-deletehelloworld.png)

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
1. **Çözüm Gezgini**, sağ bölmede, dosyayı kod düzenleyicisinde göstermek için **program. cs** ' yi seçin

1. Kod Düzenleyicisi 'nde, varsayılan "Merhaba Dünya" kodunun yerine şunu koyun `Console.WriteLine("Hello World!");` .

    ![Program dosyasında değiştirilecek satırı gösteren ekran görüntüsü.](media/vs-2022/csharp-console-calculator-delete-hello-world.png)

   Satırı aşağıdaki kodla değiştirin:

   ```csharp
       int a = 42;
       int b = 119;
       int c = a + b;
       Console.WriteLine(c);
       Console.ReadKey();
   ```

    kodu yazarsanız Visual Studio ıntellisense özelliği girişi otomatik tamamlama seçeneği sunar.

    > [!NOTE]
    > Aşağıdaki animasyon önceki kodu göstermeye yönelik değildir, ancak yalnızca IntelliSense 'in nasıl çalıştığını gösterir.

    ![Visual Studio ıde 'de ıntellisense otomatik tamamlama özelliğini gösteren tamsayı matematik kodu animasyonu.](media/vs-2022/integer-math-intellisense.gif)

1. Uygulamanızı derlemek ve çalıştırmak için **F5**'e basın veya üstteki araç çubuğunda ad **Hesaplayıcı** ' ın yanındaki yeşil oku seçin.

   ![Hata ayıklama araç çubuğundan uygulamayı çalıştırmak için hesaplayıcı düğmesini seçmeyi gösteren ekran görüntüsü.](media/vs-2022/csharp-console-calculator-button.png)

   42 + 119 toplamını gösteren bir konsol penceresi açılır ve bu, **161**.

    ![Tamsayı matematiğinin sonuçlarını gösteren konsol penceresinin ekran görüntüsü.](media/vs-2022/csharp-console-integer-math.png)

1. Konsol penceresini kapatın.

1. İsteğe bağlı olarak, sonucu değiştirmek için işlecini değiştirebilirsiniz. Örneğin, `+` `int c = a + b;` kod satırındaki işleci `-` çıkarma, `*` çarpma veya bölme için olarak değiştirebilirsiniz `/` . Uygulamayı çalıştırdığınızda, sonuç buna göre değişir.

::: moniker-end

### <a name="add-code-to-create-a-calculator"></a>Hesaplayıcı oluşturmak için kod ekleme

Projenize daha karmaşık bir hesap makinesi kodu kümesi ekleyerek devam edin.

::: moniker range="<=vs-2019"

1. Kod Düzenleyicisi 'nde, *program. cs* dosyasındaki tüm kodu aşağıdaki yeni kodla değiştirin:

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

1. Uygulamanızı çalıştırmak için **Hesaplayıcı** düğmesini seçin veya **F5** tuşuna basın.

   Bir konsol penceresi açılır.

1. Konsol penceresinde, **42** ve **119** sayılarını birlikte eklemek için istemleri izleyin.

   Uygulamanız aşağıdaki ekran görüntüsüne benzer görünmelidir:

    ![Hesap makinesi uygulamasını istemlerle gösteren konsol penceresinin ekran görüntüsü.](media/csharp-console-calculator.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Kod Düzenleyicisi 'nde, *program. cs* dosyasındaki tüm kodu aşağıdaki yeni kodla değiştirin:

    ```csharp
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
    ```

1. Uygulamanızı çalıştırmak için **Hesaplayıcı** düğmesini seçin veya **F5** tuşuna basın.

   Bir konsol penceresi açılır.

1. Konsol penceresinde, **42** ve **119** sayılarını birlikte eklemek için istemleri izleyin.

   Uygulamanız aşağıdaki ekran görüntüsüne benzer görünmelidir:

    ![Hesap makinesi uygulamasını istemlerle gösteren konsol penceresinin ekran görüntüsü.](media/csharp-console-calculator.png)

::: moniker-end

### <a name="add-decimal-functionality"></a>Ondalık işlevsellik ekleme

Şimdi, daha fazla işlevsellik eklemek için kodu ince ayar.

Geçerli Hesaplayıcı uygulaması yalnızca tüm sayıları kabul eder ve döndürür. Örneğin, uygulamayı çalıştırırsanız ve 42 sayısını 119 sayı olarak bölebiliyorsanız, sonucu sıfırdır; bu da tam değildir.

![Bir sonuç olarak tam sayı döndüren Hesaplayıcı uygulamasını gösteren konsol penceresinin ekran görüntüsü.](./media/csharp-console-calculator-nodecimal.png)

Onlukları işleyerek duyarlılığı artırmak üzere kodu onarmak için:

1. Visual Studio düzenleyicisinde *program. cs* ' de,  + **bul ve değiştir** denetimini açmak için Ctrl **H** tuşuna basın.

1. Denetime *int* yazın ve **Replace** alanına *float* yazın.

1. **Eşleştirme durumu** için simgeleri seçin ve denetimdeki **tüm kelimeyi eşleştirin** veya **alt** + **C** ve **alt** + **W** tuşlarına basın.

1. Aramayı çalıştırmak ve değiştirmek için **Tümünü Değiştir** simgesini seçin veya **alt** + **A** 'ya basın.

    ![Bul ve Değiştir denetiminin, int değişkeninin float olarak nasıl değiştirileceğini gösteren animasyon.](media/find-replace-control-animation.gif)

1. Hesaplayıcı uygulamanızı yeniden çalıştırın ve **42** sayısını **119** sayısına bölün.

   Uygulama artık sıfır yerine ondalık sayı döndürüyor.

    ![Artık bir sonuç olarak ondalık sayı döndüren Hesaplayıcı uygulamasını gösteren konsol penceresinin ekran görüntüsü.](media/csharp-console-calculator-decimal.png)

Uygulama artık ondalık sonuçlar üretebilir. Uygulamanın ondalıkları çok fazla hesaplayabilmesi için kodun birkaç tane daha olduğunu daha yapın.

1. Değişkenin her  bir örneğini `float` olarak değiştirmek `double` ve yönteminin her bir örneğini olarak değiştirmek için bul ve Değiştir denetimini kullanın `Convert.ToInt32` `Convert.ToDouble` .

1. Hesaplayıcı uygulamanızı çalıştırın ve **42,5** sayısını **119,75** sayısına bölün.

   Uygulama artık ondalık değerleri kabul ediyor ve sonuç olarak daha uzun bir ondalık sayı döndürüyor.

    ![Artık ondalık sayıları kabul eden ve daha uzun bir ondalık sonuç döndüren Hesaplayıcı uygulamasını gösteren konsol penceresinin ekran görüntüsü.](media/csharp-console-calculator-usedecimals.png)

   [Kodu gözden geçir](#revise-the-code) bölümünde, sonuçlardaki ondalık basamak sayısını azaltırsınız.

## <a name="debug-the-app"></a>Uygulamada hata ayıklama

Temel Hesaplayıcı uygulamanızı geliştirdiniz, ancak uygulamanız kullanıcı giriş hataları gibi özel durumları henüz işlemedi. Örneğin, kullanıcılar sıfıra bölmeye veya beklenmedik bir karakter girmeye çalıştıklarında, uygulama çalışmayı durdurabilir, bir hata döndürebilir veya beklenmedik bir sayısal sonuç döndürebilir.

Birkaç ortak kullanıcı girişi hatasını gözden geçirelim, orada görüntiklerinde bunları hata ayıklayıcıda bulalım ve kodda çözme.

> [!TIP]
> hata ayıklayıcı ve nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Visual Studio hata ayıklayıcıya](../../debugger/debugger-feature-tour.md)bakın.

### <a name="fix-the-divide-by-zero-error"></a>"Sıfıra bölme" hatasını çözme

Bir sayıyı sıfıra bölmeye çalışırsanız, konsol uygulaması donabilir ve kod düzenleyicisinde neyin yanlış olduğunu gösterir.

   ![sarı renkle vurgulanmış bir çizgiyi gösteren Visual Studio kodu düzenleyicisinin ekran görüntüsü ve ' sıfıra bölünmeye çalışıldı ' için işlenmeyen özel durum hatası.](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> Bazen uygulama dondurmaz ve hata ayıklayıcı sıfıra bölme hatası göstermez. Bunun yerine, uygulama sonsuz bir simge gibi beklenmedik bir sayısal sonuç döndürebilir. Aşağıdaki kod düzeltilmesi hala geçerlidir.

Kodu bu hatayı işleyecek şekilde değiştirmek için:

1. *Program. cs*' de, `case "d":` ve aşağıdaki kodla belirten yorum arasındaki kodu değiştirin `// Wait for the user to respond before closing` :

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

   Kodu değiştirdikten sonra, ifadesiyle olan bölüm `switch` aşağıdaki ekran görüntüsüne benzer şekilde görünmelidir:

   ![Visual Studio kod düzenleyicisinde düzeltilen anahtar bölümünü gösteren ekran görüntüsü.](media/csharp-console-calculator-switch-code.png)

Böylece, herhangi bir sayıyı sıfıra BÖP, uygulama başka bir sayı ister ve sıfır dışında bir sayı sağlamamaya devam eder.

   ![Sıfır dışında bir sayı sağlamak için yinelenen istem içeren bir konsol penceresinin ekran görüntüsü.](media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>"Biçim" hatasını çözme

Uygulama sayısal bir karakter beklerken alfabetik bir karakter girerseniz, uygulama donuyor. Visual Studio, kod düzenleyicisinde neyin yanlış olduğunu gösterir.

   ::: moniker range="<=vs-2019"
   ![Visual Studio kod düzenleyicisinde işlenmemiş biçim hatasını gösteren ekran görüntüsü.](media/csharp-console-calculator-format-error.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio kod düzenleyicisinde işlenmemiş biçim hatasını gösteren ekran görüntüsü.](media/vs-2022/csharp-console-calculator-format-error.png)
   ::: moniker-end

Bu özel durumu engellemek için, daha önce girdiğiniz kodu yeniden düzenleyebilirsiniz.

#### <a name="revise-the-code"></a>Kodu gözden geçirin

`program`Tüm kodu işlemek için sınıfa güventense, uygulamanızı iki sınıfa ayırabilirsiniz: `Calculator` ve `Program` .

`Calculator`Sınıfı, hesaplama işinin toplu işini işler ve `Program` sınıfı kullanıcı arabirimini ve hata işleme işini işler.

Haydi başlayalım.

1. *Program. cs*' de, `Calculator` ad alanındaki açılış ve kapanış ayraçları arasındaki her şeyi silin:

    ```csharp
    using System;

    namespace Calculator
    {

    }
    ```

1. Küme ayraçları arasında aşağıdaki yeni `Calculator` sınıfı ekleyin:

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

1. Ayrıca  `Program` , aşağıdaki gibi yeni bir sınıf da ekleyin:

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

1. Uygulamanızı çalıştırmak için **Hesaplayıcı** düğmesini seçin veya **F5** tuşuna basın.

1. İstemleri izleyin ve **42** sayısını **119** sayısına bölün. Sonuçlarınız aşağıdaki ekran görüntüsüne benzer görünmelidir:

   ::: moniker range="<=vs-2019"
   ![Yeniden düzenlenmiş Hesaplayıcı uygulamasıyla bir konsol penceresi gösteren ekran görüntüsü.](media/csharp-console-calculator-refactored.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Yeniden düzenlenmiş Hesaplayıcı uygulamasıyla bir konsol penceresi gösteren ekran görüntüsü.](media/vs-2022/csharp-console-calculator-refactored.png)
   ::: moniker-end

   Artık konsol uygulamasını kapatmayı seçinceye kadar daha fazla denklem girebilirsiniz. Sonuçlarda daha az ondalık basamak de vardır. Yanlış bir karakter girerseniz, uygun bir hata yanıtı alırsınız.

## <a name="close-the-app"></a>Uygulamayı kapat

1. Daha önce yapmadıysanız, hesaplayıcı uygulamasını kapatın.

1. Visual Studio **Çıkış** bölmesini kapatın.

   ![Visual Studio ' de çıkış bölmesini kapatmayı gösteren ekran görüntüsü.](media/csharp-calculator-close-output-pane.png)

1. Visual Studio ' de,  + uygulamanızı kaydetmek için Ctrl **S** tuşuna basın.

[!INCLUDE[../includes/git-source-control.md](../includes/git-source-control.md)]

## <a name="review-code-complete"></a>İnceleme: kod Tamam

Bu öğreticide, hesaplayıcı uygulamasında birçok değişiklik yaptık. Uygulama, işlem kaynaklarını daha verimli bir şekilde işler ve çoğu kullanıcı giriş hatasını işler.

Hepsi tek bir yerde olmak üzere kodun tamamı aşağıda verilmiştir:

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

Daha fazla öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [C# öğreticileri](/dotnet/csharp/tutorials)

> [!div class="nextstepaction"]
> [Visual Studio IDE'de gezinme](../visual-studio-ide.md)

:::moniker-end

:::moniker range=">=vs-2019"

Bu öğreticinin ikinci kısmıyla devam edin:

> [!div class="nextstepaction"]
> [Öğretici Bölüm 2: C# konsol uygulamanızı genişletme ve hata ayıklama](tutorial-console-part-2.md)
:::moniker-end
