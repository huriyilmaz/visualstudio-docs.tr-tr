---
title: 'Öğretici: Basit bir C# konsol uygulaması oluşturun'
description: Visual Studio'da adım adım c# konsol uygulaması oluşturmayı öğrenin.
ms.custom: seodec18, get-started
ms.date: 02/18/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 528887c477814b7011cf941a9198f83701beee54
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "78215429"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Öğretici: Visual Studio'da basit bir C# konsol uygulaması oluşturun

C# için yapılan bu eğitimde, visual studio'yu kullanarak bir konsol uygulaması oluşturup çalıştıracaksınız ve bunu yaparken Visual Studio tümleşik geliştirme ortamının (IDE) bazı özelliklerini keşfedeceksiniz.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Başlamak için bir C# uygulama projesi oluşturacağız. Proje türü, daha bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.
   (Alternatif olarak, **Ctrl**+**Shift**+**N**tuşuna basın).

3. **Yeni Proje** iletişim kutusunun sol bölmesinde **C#** seçeneğini genişletin ve **ardından .NET Core'u**seçin. Orta bölmede Konsol **Uygulaması'nı (.NET Core)** seçin. Sonra dosya ***Hesap makinesi***adı .

   ![Visual Studio IDE'deki Yeni Proje iletişim kutusunda Konsol Uygulaması (.NET Core) proje şablonu](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

**Konsol Uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **.NET Core çapraz platform geliştirme** iş yükünü ekleyerek bu uygulamayı elde edebilirsiniz. Aşağıdaki adımları uygulayın:

#### <a name="option-1-use-the-new-project-dialog-box"></a>Seçenek 1: Yeni Proje iletişim kutusunu kullanma

1. **Yeni Proje** iletişim kutusunun sol bölmesinde Görsel **Stüdyo Yükleyici** Aç bağlantısını seçin.

   ![Yeni Proje iletişim kutusundan Open Visual Studio Installer bağlantısını seçin](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio Installer başlattı. **.NET Core çapraz platform geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

   ![.NET Core platform ötesi geliştirme iş yükü Visual Studio Installer'da](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Seçenek 2: Araçlar menü çubuğunu kullanma

1. **Yeni Proje** iletişim kutusundan ve üst menü çubuğundan iptal etme, **Araçlar** > **Araçları ve Özellikleri Al'ı**seçin.

1. Visual Studio Installer başlattı. **.NET Core çapraz platform geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Görsel Stüdyo 2019'u açın.

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   !['Yeni proje oluşturma' penceresini görüntüleme](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, Dil listesinden **C#'yi** seçin ve ardından Platform listesinden **Windows'u** seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **Konsol Uygulaması (.NET Core)** şablonunu seçin ve **sonra İleri'yi**seçin.

   ![Konsol Uygulaması için C# şablonunu seçin (.NET Framework)](./media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > **Konsol Uygulaması (.NET Core)** şablonunu görmüyorsanız, yeni **bir proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Aradığınızı bulamıyor' iletisinden 'Daha fazla araç ve özellik yükleyin' bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ardından, Visual Studio Installer'da **.NET Core çapraz platform geliştirme** iş yükünü seçin.
   >
   > ![.NET Core platform ötesi geliştirme iş yükü Visual Studio Installer'da](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra Visual Studio Installer'daki **Değiştir** düğmesini seçin. Çalışmanızı kaydetmeniz istenebilir; eğer öyleyse, bunu yapın. Ardından, iş yükünü yüklemeye **devam** et'i seçin. Daha sonra, bu "[Proje oluştur](#create-a-project)" yordamındaki 2.

1. Yeni **proje pencerenizi Yapılandır'da** **Proje adı** kutusuna *Hesap Makinesi* yazın veya girin. Ardından **Oluştur'u**seçin.

   !['Yeni projenizi yapılandır' penceresinde, projenize 'Hesap Makinesi' adını](./media/vs-2019/csharp-name-your-calculator-project.png)

   Visual Studio varsayılan "Hello World" kodunu içeren yeni projenizi açar.
   
::: moniker-end

## <a name="create-the-app"></a>Uygulama oluşturma

İlk olarak, C# bazı temel dosyon matematiği inceleyeceğiz. Daha sonra, temel bir hesap makinesi oluşturmak için kod ekleriz. Bundan sonra, hataları bulmak ve düzeltmek için uygulamayı hata ayıklayacağız. Ve son olarak, kodu daha verimli hale getirmek için hassaslaştıracağız.

### <a name="explore-integer-math"></a>Tamsayı matematiğini inceleme

C#'daki bazı temel sonda matematiği ile başlayalım.

1. Kod düzenleyicisinde varsayılan "Hello World" kodunu silin.

    ![Yeni hesap makinesi uygulamanızdan varsayılan Hello World kodunu silme](./media/csharp-console-calculator-deletehelloworld.png)

   Özellikle, diyor satırı silin, `Console.WriteLine("Hello World!");`.

1. Onun yerine, aşağıdaki kodu yazın:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Bunu yaptığınızda Visual Studio'daki IntelliSense özelliğinin girişi otomatik olarak tamamlama seçeneği sunduğuna dikkat edin.

    > [!NOTE]
    > Aşağıdaki animasyon, önceki kodu çoğaltmak için tasarlanmamıştır. Yalnızca otomatik tamamlama özelliğinin nasıl çalıştığını göstermek için tasarlanmıştır.

    ![Visual Studio IDE'deki IntelliSense otomatik tamamlama özelliğini gösteren tamsayı matematik kodunun animasyonu](./media/integer-math-intellisense.gif)

1. Programınızı oluşturmak ve çalıştırmak için **Hesap Makinesi'nin** yanındaki yeşil **Başlat** düğmesini seçin veya **F5 tuşuna**basın.

   ![Uygulamayı araç çubuğundan çalıştırmak için Hesap Makinesi düğmesini seçin](./media/csharp-console-calculator-button.png)

   42 + 119'un toplamını gösteren bir konsol penceresi açılır, bu da **161'dir.**

    ![Tamsayı matematiğinin sonuçlarını gösteren konsol penceresi](./media/csharp-console-integer-math.png)

1. **(İsteğe bağlı)** Sonucu değiştirmek için işleci değiştirebilirsiniz. `+` Örneğin, kod `int c = a + b;` `-` satırındaki işleci çıkarma, `*` çarpma veya `/` bölme için değiştirebilirsiniz. Daha sonra, programı çalıştırdığınızda, sonuç da değişir.

1. Konsol penceresini kapatın.

### <a name="add-code-to-create-a-calculator"></a>Hesap makinesi oluşturmak için kod ekleme

Projenize daha karmaşık bir hesap makinesi kodu kümesi ekleyerek devam edelim.

1. Kod düzenleyicisinde gördüğünüz tüm kodları silin.

1. Kod düzenleyicisine aşağıdaki yeni kodu girin veya yapıştırın:

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

1. Programınızı çalıştırmak için **Hesap Makinesi'ni** seçin veya **F5 tuşuna**basın.

   ![Uygulamayı araç çubuğundan çalıştırmak için Hesap Makinesi düğmesini seçin](./media/csharp-console-calculator-button.png)

   Konsol penceresi açılır.

1. Uygulamanızı konsol penceresinde görüntüleyin ve **ardından 42** ve **119**numaralarını eklemek için istemleri izleyin.

   Uygulamanız aşağıdaki ekran görüntüsüne benzer olmalıdır:

    ![Hesap Makinesi uygulamasını gösteren konsol penceresi ve hangi eylemlerin yapılacağı istemleri içerir](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>Hesap makinesine işlevsellik ekleme

Daha fazla işlevsellik eklemek için kodu değiştirelim.

### <a name="add-decimals"></a>Ondalık sayılar ekleme

Hesap makinesi uygulaması şu anda tam sayıları kabul eder ve döndürür. Ancak, ondalık sayılara izin veren kod eklersek daha kesin olacaktır.

Aşağıdaki ekran görüntüsünde olduğu gibi, uygulamayı çalıştırıp 42 sayısını 119 sayısına bölerseniz, sonucunuz 0 (sıfır) olur, ki bu kesin değildir.

![Sonuç olarak ondalık sayı döndürmeyen Hesap Makinesi uygulamasını gösteren konsol penceresi](./media/csharp-console-calculator-nodecimal.png)

Kodu ondalık sayılarla işleyebilsin diye düzeltelim.

1. **Bul ve Değiştir** denetimini açmak için **Ctrl** + **F** tuşuna basın.

1. Değişkenin her `int` örneğini `float`' ' ye değiştirin

   Bul ve **Değiştir** denetiminde **Match case** **(Alt**+**C)** ve **Match tüm sözcüğü** **(Alt**+**W)** olarak değiştirdiğinden emin olun.

    ![Int değişkeninin float'a nasıl değiştirilebildiğini gösteren Bul ve Değiştir denetiminin animasyonu](./media/find-replace-control-animation.gif)

1. Hesap makinesi uygulamanızı yeniden çalıştırın ve **42** sayısını **119**sayısına bölün.

   Uygulamanın artık sıfır yerine ondalık sayı döndürttüğüne dikkat edin.

    ![Sonuç olarak ondalık sayı döndüren Hesap Makinesi uygulamasını gösteren konsol penceresi](./media/csharp-console-calculator-decimal.png)

Ancak, uygulama yalnızca ondalık bir sonuç üretir. Uygulamanın ondalık sayıları da hesaplayabilmesi için kodda birkaç değişiklik daha yapalım.

1. `float` Değişkenin her `double`örneğini '' olarak değiştirmek ve `Convert.ToInt32` yöntemin her örneğini `Convert.ToDouble`' ye değiştirmek için Bul ve **Değiştir** denetimini **(Ctrl** + **F)** kullanın.

1. Hesap makinesi uygulamanızı çalıştırın ve **42,5** sayısını **119,75**sayısına bölün.

   Uygulamanın artık ondalık değerleri kabul ettiğine ve sonucu olarak daha uzun bir ondalık sayı döndürttesine dikkat edin.

    ![Artık ondalık sayıları kabul eden ve sonuç olarak daha uzun bir ondalık sayı döndüren Hesap Makinesi uygulamasını gösteren konsol penceresi](./media/csharp-console-calculator-usedecimals.png)

    (Kodu [Gözden Geçir](#revise-the-code) bölümündeki ondalık basamak sayısını düzelteceğiz.)

## <a name="debug-the-app"></a>Uygulamayı hata ayıklama

Temel hesap makinesi uygulamamızda iyileştirildi, ancak kullanıcı giriş hataları gibi özel durumları işlemek için henüz başarısız güvenli bir uygulama yok.

Örneğin, bir sayıyı sıfıra bölmeye çalışırsanız veya uygulama sayısal bir karakter (veya tam tersi) beklediğinde bir alfa karakteri girerseniz, uygulama çalışmayı durdurabilir, bir hatayı döndürebilir veya beklenmeyen bir sayısal olmayan sonucu döndürebilir.

Birkaç yaygın kullanıcı giriş hatası üzerinden yürüyelim, hata ayıklayıcıda bu hataları bulup, bunları orada görünürlerse bu hataları tespit edelim ve kodda düzeltelim.

> [!TIP]
> Hata ayıklama ve nasıl çalıştığı hakkında daha fazla bilgi için [Visual Studio hata ayıklama sayfasına](../../debugger/debugger-feature-tour.md) ilk bakışta bakın.

### <a name="fix-the-divide-by-zero-error"></a>"Sıfıra böl" hatasını düzeltme

Bir sayıyı sıfıra bölmeye çalıştığınızda, konsol uygulaması donabilir ve kod düzenleyicisinde neyin yanlış olduğunu gösterebilir.

   ![Visual Studio kod düzenleyicisi sıfıra bölme hatasını gösterir](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> Bazen uygulama donmaz ve hata ayıklama sıfıra bölme hatası göstermez. Bunun yerine, uygulama sonsuzluk simgesi gibi beklenmeyen bir sayısal olmayan sonucu döndürebilir. Aşağıdaki kod düzeltmesi hala geçerlidir.

Bu hatayı işlemek için kodu değiştirelim.

1. Doğrudan ve 'yi yazan `case "d":` `// Wait for the user to respond before closing`açıklama arasında görünen kodu silin.

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

   Kodu ekledikten sonra, deyimin `switch` yer verdiği bölüm aşağıdaki ekran görüntüsüne benzer olmalıdır:

   ![Visual Studio kod düzenleyicisinde gözden geçirilmiş "anahtar" bölümü](./media/csharp-console-calculator-switch-code.png)

Şimdi, herhangi bir sayıyı sıfıra böldüğünüzde, uygulama başka bir sayı ister. Daha da iyisi: Sıfırdan başka bir sayı sağlayana kadar sormak durmaz.

   ![Visual Studio kod düzenleyicisi sıfıra bölme hatasını gösterir](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>"Biçim" hatasını düzeltme

Uygulama sayısal bir karakter (veya tam tersi) beklediğinde bir alfa karakteri girerseniz, konsol uygulaması donar. Visual Studio daha sonra kod düzenleyicisinde neyin yanlış olduğunu gösterir.

   ![Visual Studio kod düzenleyicisi bir biçim hatası gösterir](./media/csharp-console-calculator-format-error.png)

Bu hatayı gidermek için, daha önce girdiğimiz kodu yeniden düzenlememiz gerekir.

#### <a name="revise-the-code"></a>Kodu gözden geçirin

Tüm kodu işlemek `program` için sınıfa güvenmek yerine, uygulamamızı iki sınıfa böleriz: `Calculator` ve `Program`.

Sınıf `Calculator` hesaplama çalışmasının büyük bölümünü işleyecek `Program` ve sınıf kullanıcı arabirimi ve hata yakalama işini işleyecek.

Başlayalım.

1. Açılış ve `Calculator` kapanış ayraçları arasındaki ad alanındaki her şeyi silin:

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. Ardından, aşağıdaki `Calculator` gibi yeni bir sınıf ekleyin:

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

1. Ardından, aşağıdaki `Program` gibi yeni bir sınıf ekleyin:

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

1. Programınızı çalıştırmak için **Hesap Makinesi'ni** seçin veya **F5 tuşuna**basın.

1. İstemleri izleyin ve **42** sayısını **119**sayısına bölün. Uygulamanız aşağıdaki ekran görüntüsüne benzer olmalıdır:

    ![Hangi eylemlerin yapılacağını ve yanlışgirişler için hata kullanımını istemleri istemleri içeren refactored Hesap Makinesi uygulamasını gÜ](./media/csharp-console-calculator-refactored.png)

    Konsol uygulamasını kapatmayı seçene kadar daha fazla denklem girme seçeneğiniz olduğuna dikkat edin. Ayrıca sonuç olarak ondalık basamak sayısını da azalttık.

## <a name="close-the-app"></a>Uygulamayı kapat

1. Henüz yapmadıysanız, hesap makinesi uygulamasını kapatın.

1. Visual Studio'daki **Çıkış** bölmesini kapatın.

   ![Visual Studio'da Çıkış bölmesini kapatın](./media/csharp-calculator-close-output-pane.png)

1. Visual Studio'da uygulamanızı kaydetmek için **Ctrl**+**S** tuşuna basın.

1. Visual Studio’yu kapatın.

## <a name="code-complete"></a>Kod tamamlandı

Bu eğitim sırasında, hesap makinesi uygulamasında birçok değişiklik yaptık. Uygulama artık bilgi işlem kaynaklarını daha verimli bir şekilde işliyor ve çoğu kullanıcı giriş hatasını işliyor.

İşte tüm kodun tamamı, hepsi tek bir yerde:

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

Bu öğretici tamamladıktan sonra tebrikler! Daha fazla bilgi edinmek için aşağıdaki öğreticilere devam edin.

> [!div class="nextstepaction"]
> [Daha fazla C# öğreticisiyle devam edin](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Ayrıca bkz.

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Visual Studio'da C# kodunu hata ayıklamayı öğrenin](tutorial-debugger.md)
