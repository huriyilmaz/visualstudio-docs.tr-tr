---
title: 'Öğretici: basit bir C# konsol uygulaması oluşturma'
description: Visual Studio 'da C# konsol uygulamasının nasıl oluşturulduğunu adım adım öğrenin.
ms.custom: vs-acquisition, get-started
ms.date: 02/10/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5f155c2477c97b6f0d18a4cfd3d54386aee68dd9
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390378"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Öğretici: Visual Studio 'da basit bir C# konsol uygulaması oluşturma

C# için bu öğreticide, Visual Studio 'yu kullanarak bir konsol uygulaması oluşturup çalıştırabilir ve bunu yaparken Visual Studio tümleşik geliştirme ortamının (IDE) bazı özelliklerini keşfedebilirsiniz.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2022"

Zaten Visual Studio 2022 Preview sürümünü yüklemediyseniz, ücretsiz olarak yüklemek için [Visual studio 2022 Preview İndirmeleri](https://visualstudio.microsoft.com/vs/preview/vs2022) sayfasına gidin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Başlamak için bir C# uygulama projesi oluşturacağız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.
   (Alternatif olarak, **CTRL** + tuşuna basın **SHIFT** + **N**).

3. **Yeni proje** iletişim kutusunun sol bölmesinde, **C#**' ı genişletin ve ardından **.NET Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından dosya **_Hesaplayıcı_** adını adlandırın.

   ![Visual Studio IDE 'de yeni proje iletişim kutusundaki konsol uygulaması (.NET Core) proje şablonu](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

**Konsol uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **.NET Core platformlar arası geliştirme** iş yükünü ekleyerek buna ulaşabilirsiniz. Aşağıdaki adımları uygulayın:

#### <a name="option-1-use-the-new-project-dialog-box"></a>Seçenek 1: yeni proje iletişim kutusunu kullanma

1. **Yeni proje** iletişim kutusunun sol bölmesindeki **Visual Studio yükleyicisi aç** bağlantısını seçin.

   ![Yeni proje iletişim kutusundan Visual Studio Yükleyicisi Aç bağlantısını seçin](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

   ![Visual Studio Yükleyicisi .NET Core platformlar arası geliştirme iş yükü](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. seçenek: Araçlar menü çubuğunu kullanma

1. **Yeni proje** iletişim kutusunu iptal edin ve üst menü çubuğundan **Araçlar** > **Araçlar ve Özellikler al**' ı seçin.

1. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde dil listesinden **C#** ' ı seçin. Ardından, proje türleri listesinden platform listesinden ve **konsolundan** **Windows** ' u seçin. 

   Dili, platformu ve proje türü filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

    :::image type="content" source="./media/vs-2019/csharp-create-new-project-console-net-core.png" alt-text="Konsol uygulaması için C# şablonunu seçin (.NET Framework)":::

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Sonra, Visual Studio Yükleyicisi **.NET Core platformlar arası geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .NET Core platformlar arası geliştirme iş yükü](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra Visual Studio Yükleyicisi **Değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *Hesaplayıcı* yazın veya girin. Ardından **İleri**' yi seçin.

    :::image type="content" source="./media/vs-2019/csharp-name-your-calculator-project.png" alt-text="' yeni projenizi yapılandırın ' penceresinde, projenizi ' Hesaplayıcı ' olarak adlandırın":::
   
1. **Ek bilgi** penceresinde **.NET Core 3,1** , hedef çerçeve'niz için zaten seçilmelidir. Aksi takdirde, **.NET Core 3,1**' i seçin. Ardından **Oluştur**' u seçin.

    :::image type="content" source="./media/vs-2019/csharp-target-framework.png" alt-text="' ek bilgiler ' penceresinde, .NET Core 3,1 ' ın seçildiğinden emin olun":::

   Visual Studio, varsayılan "Merhaba Dünya" kodunu içeren yeni projenizi açar.

::: moniker-end

## <a name="create-the-app"></a>Uygulama oluşturma

İlk olarak, C# ' de bazı temel tamsayı matematiğini araştıracağız. Daha sonra, temel bir Hesaplayıcı oluşturmak için kod ekleyeceğiz. Bundan sonra, hataları bulmak ve gidermek için uygulamada hata ayıklaması yapacağız. Son olarak, kodu daha verimli hale getirmek için belirginleştireceğiz.

### <a name="explore-integer-math"></a>Tamsayı matematiğini inceleme

C# ' de bazı temel tamsayı matematiğe başlayalım.

1. Kod Düzenleyicisi 'nde varsayılan "Merhaba Dünya" kodunu silin.

    ![Yeni Hesaplayıcı uygulamanızdan varsayılan Merhaba Dünya kodunu silme](./media/csharp-console-calculator-deletehelloworld.png)

   Özellikle, belirten satırı silin `Console.WriteLine("Hello World!");` .

1. Onun yerine, aşağıdaki kodu yazın:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Bunu yaptığınızda, Visual Studio 'daki IntelliSense özelliğinin girişi otomatik tamamlama seçeneğini sunduğunu unutmayın.

    > [!NOTE]
    > Aşağıdaki animasyon, önceki kodun yinelenmesine yönelik değildir. Yalnızca otomatik tamamlama özelliğinin nasıl çalıştığını göstermek için tasarlanmıştır.

    ![Visual Studio IDE 'de IntelliSense otomatik tamamlama özelliğini gösteren tamsayı matematik kodu animasyonu](./media/integer-math-intellisense.gif)

1. Çalışma **Hesaplayıcı** ' ın yanındaki yeşil **Başlat** düğmesini seçerek programınızı derleyip çalıştırın veya **F5** tuşuna basın.

   ![Uygulamayı araç çubuğundan çalıştırmak için hesaplayıcı düğmesini seçin](./media/csharp-console-calculator-button.png)

   42 + 119 toplamını gösteren bir konsol penceresi açılır ve bu da **161**.

    ![Tamsayı matematiğinin sonuçlarını gösteren konsol penceresi](./media/csharp-console-integer-math.png)

1. **(Isteğe bağlı)** Sonucu değiştirmek için işlecini değiştirebilirsiniz. Örneğin, `+` `int c = a + b;` kod satırındaki işleci `-` çıkarma, `*` çarpma veya bölme için olarak değiştirebilirsiniz `/` . Ardından, programı çalıştırdığınızda, sonuç de değişir.

1. Konsol penceresini kapatın.

### <a name="add-code-to-create-a-calculator"></a>Hesaplayıcı oluşturmak için kod ekleme

Projenize daha karmaşık bir hesap makinesi kodu kümesi ekleyerek devam edelim.

1. Kod düzenleyicisinde gördüğünüz tüm kodu silin.

1. Aşağıdaki yeni kodu kod düzenleyicisine girin veya yapıştırın:

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

1. Programınızı çalıştırmak için **Hesaplayıcı** ' ı seçin veya **F5** tuşuna basın.

   ![Uygulamayı araç çubuğundan çalıştırmak için hesaplayıcı düğmesini seçin](./media/csharp-console-calculator-button.png)

   Bir konsol penceresi açılır.

1. Konsol penceresinde uygulamanızı görüntüleyin ve sonra **42** ve **119** sayılarını eklemek için istemleri izleyin.

   Uygulamanız aşağıdaki ekran görüntüsüne benzer görünmelidir:

    ![Hesap makinesi uygulamasını gösteren konsol penceresi ve hangi eylemlerin alınacağı hakkında komut istemleri içerir](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>Hesap makinesine işlevsellik ekleme

Daha fazla işlevsellik eklemek için kodu ince ayar.

### <a name="add-decimals"></a>Ondalık sayı Ekle

Hesaplayıcı uygulaması şu anda kabul ediyor ve tüm sayıları döndürüyor. Ancak, ondalıkla izin veren kodu eklediğimiz takdirde daha kesin olacaktır.

Aşağıdaki ekran görüntüsünde olduğu gibi, uygulamayı çalıştırırsanız ve 42 sayısını 119 olarak bölebiliyorsanız, sonucu 0 (sıfır) olur ve bu da tam değildir.

![Sonuç olarak ondalık sayı döndürmeyen Hesaplayıcı uygulamasını gösteren konsol penceresi](./media/csharp-console-calculator-nodecimal.png)

Onlukları işleyecek şekilde kodu düzeldelim.

1.   +  **Bul ve Değiştir** denetimini açmak için CTRL **H** tuşuna basın.

1. Değişkenin her örneğini olarak değiştirin `int` `float` .

   Bul ve Değiştir denetiminde **eşleşme büyük/küçük harf** (**alt** + **C**) ve **tüm kelimeyi Eşleştir** (**alt** + **W**)  ' i değiştirdiğinizden emin olun.

    ![Int değişkeninin float olarak nasıl değiştirileceğini gösteren bul ve Değiştir denetiminin animasyonu](./media/find-replace-control-animation.gif)

1. Hesaplayıcı uygulamanızı yeniden çalıştırın ve **42** sayısını **119** sayısına bölün.

   Uygulamanın artık sıfır yerine ondalık sayı döndürttçene dikkat edin.

    ![Sonuç olarak artık ondalık sayı döndüren Hesap makinesi uygulamasını gösteren Konsol penceresi](./media/csharp-console-calculator-decimal.png)

Ancak uygulama yalnızca ondalık sonuç üretir. Şimdi uygulamanın ondalık sayıları da hesaplay uygulaması için kodda birkaç değişiklik daha yapacaktır.

1. Değişkenin **her örneğini olarak** değiştirmek ve yöntemin her örneğini olarak değiştirmek için Bul ve Değiştir denetimi (**Ctrl**  +  **H**) `float` `double` `Convert.ToInt32` `Convert.ToDouble` kullanın.

1. Hesap makinesi uygulamanızı çalıştırın ve **42,5 sayısını** **119,75 sayısına bölün.**

   Uygulamanın artık ondalık değerleri kabul eder ve sonucu olarak daha uzun bir ondalık sayı döndürür.

    ![Artık ondalık sayıları kabul eden ve sonuç olarak daha uzun bir ondalık sayı döndüren Hesap makinesi uygulamasını gösteren konsol penceresi](./media/csharp-console-calculator-usedecimals.png)

    (Kodu düzeltme bölümündeki ondalık basamak sayısını [](#revise-the-code) düzelteceğiz.)

## <a name="debug-the-app"></a>Uygulamada hata ayıklama

Temel hesaplayıcı uygulamamızı iyileştirdik, ancak kullanıcı girişi hataları gibi özel durumları işlemek için henüz başarısız kasalar yok.

Örneğin, bir sayıyı sıfıra bölmeye veya uygulama sayısal bir karakter (veya tam tersi) beklediğinizde bir alfa karakter girmeye çalışıyorsanız, uygulama çalışmayı durdurabilir, hata döndürür veya beklenmeyen bir sayısal sonuç döndürür.

Şimdi birkaç yaygın kullanıcı girişi hatasının üzerinden geçelim, hata ayıklayıcıda görünürse bunları bu hata ayıklayıcısında bulup kodda düzeltelim.

> [!TIP]
> Hata ayıklayıcı hakkında daha fazla bilgi ve nasıl çalıştığını görmek için Hata [ayıklayıcısı sayfasında Visual Studio bakın.](../../debugger/debugger-feature-tour.md)

### <a name="fix-the-divide-by-zero-error"></a>"Sıfıra bölme" hatasını düzeltme

Bir s numarayı sıfıra bölmeye çalışırsanız konsol uygulaması donup kod düzenleyicisinde neyin yanlış olduğunu gösterebilir.

   !['Sıfıra Visual Studio bölmeye çalışıldı' için sarı renkle vurgulanmış bir satırı ve Özel Durum İşlenemedi hatasını gösteren kod düzenleyicisinin ekran görüntüsü.](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> Bazen uygulama donmaz ve hata ayıklayıcı sıfıra bölme hatası göstermez. Bunun yerine uygulama, sonsuz simgesi gibi beklenmeyen bir sayısal olmayan sonuç dönüşe neden olabilir. Aşağıdaki kod düzeltmesi hala geçerlidir.

Şimdi bu hatayı işlemek için kodu değiştir bakalım.

1. doğrudan ile arasında görünen ve `case "d":` olarak belirtilen açıklamayı `// Wait for the user to respond before closing` silin.

1. Aşağıdaki kodla değiştirin:

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

   Kodu ekledikten sonra deyiminin yer alan `switch` bölümü aşağıdaki ekran görüntüsüne benzer şekilde görüntü gerekir:

   ![Yeni kod düzenleyicisinde düzeltilmiş "Visual Studio" bölümü](./media/csharp-console-calculator-switch-code.png)

Şimdi herhangi bir s numarayı sıfıra böldükte uygulama başka bir sayı ister. Daha da iyisi: Siz sıfırdan başka bir sayı sağlayana kadar sormayı durdurmaz.

   ![Sıfır olmayan Visual Studio girişi denetimi eklenmiş switch deyiminin kodunu gösteren kod düzenleyicisinin ekran görüntüsü.](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>"Biçim" hatasını düzeltme

Uygulama sayısal bir karakter (veya tam tersi) beklediğinizde alfa karakter girersiniz, konsol uygulaması donar. Visual Studio kod düzenleyicisinde neyin yanlış olduğunu gösterir.

   ![Kod Visual Studio düzenleyicisi biçim hatası gösteriyor](./media/csharp-console-calculator-format-error.png)

Bu hatayı düzeltmek için daha önce girdiğimiz kodu yeniden düzenlememiz gerekir.

#### <a name="revise-the-code"></a>Kodu düzeltme

Tüm kodu işlemek `program` için sınıfına güvenmek yerine, uygulamamızı iki sınıfa böleriz: `Calculator` ve `Program` .

sınıfı hesaplamanın toplu işlerini işler ve sınıf kullanıcı arabirimini ve hata yakalama `Calculator` `Program` çalışmalarını işler.

Haydi başlayalım.

1. Ad alanı içinde açma `Calculator` ve kapatma ayraçları arasındaki her şeyi silin:

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. Ardından, aşağıdaki gibi yeni `Calculator` bir sınıf ekleyin:

    ```csharp
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

    ```

1. Ardından, aşağıdaki gibi  `Program` yeni bir sınıf ekleyin:

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

1. Programınızı **çalıştırmak** için Hesap makinesi'ni seçin veya **F5 tuşuna basın.**

1. yönergelerini izleyin ve **42 sayısını** **119 sayısına bölün.** Uygulamanın aşağıdaki ekran görüntüsüne benzer olması gerekir:

    ![Hangi eylemlerin gerçekleştir ve yanlış girişlerde hata işlemenin istemlerini içeren yeniden yapılandırılmış Hesaplayıcı uygulamasını gösteren konsol penceresi](./media/csharp-console-calculator-refactored.png)

    Konsol uygulamasını kapatmayı seçene kadar daha fazla denklem girme seçeneğiniz olduğunu fark edin. Ayrıca sonuçtaki ondalık basamak sayısını da azaltıldı.

## <a name="close-the-app"></a>Uygulamayı kapatma

1. Henüz bunu yapmadıysanız hesap makinesi uygulamasını kapatın.

1. Bölmede **Çıkış** bölmesini Visual Studio.

   ![Bölmede Çıkış bölmesini Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. Uygulama Visual Studio kaydetmek için **Ctrl** + **S** tuşlarına basın.

1. Visual Studio’yu kapatın.

## <a name="code-complete"></a>Kod tamamlandı

Bu öğreticide hesap makinesi uygulamasında birçok değişiklik yaptık. Uygulama artık bilgi işlem kaynaklarını daha verimli bir şekilde ele almaktadır ve çoğu kullanıcı giriş hatalarını da ele almaktadır.

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
> [2. Bölüm ile devam](tutorial-console-part-2.md)
:::moniker-end

## <a name="see-also"></a>Ayrıca bkz.

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Visual Studio'de C# kodunda hata ayıklamayı Visual Studio](tutorial-debugger.md)
