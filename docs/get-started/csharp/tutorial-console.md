---
title: 'Öğretici: Basit bir C# konsol uygulaması oluşturma'
description: Visual Studio'da adım adım C# konsol uygulaması oluşturma hakkında bilgi edinin.
ms.custom: acquisition, seodec18, get-started
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
ms.openlocfilehash: 7317af5667f09ff30d0f2cb54d1399da9d0358de
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113254"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Öğretici: Visual Studio'de basit bir C# konsol uygulaması oluşturma

C# için bu öğreticide, Visual Studio kullanarak bir konsol uygulaması oluşturacak ve çalıştıracak ve siz bunu yaparken Visual Studio tümleşik geliştirme ortamının (IDE) bazı özelliklerini keşfedebilirsiniz.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Başlamak için bir C# uygulama projesi oluşturuz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **Proje'yi**  >    >  **seçin.**
   (Alternatif olarak **Ctrl tuşuna basın** + **Shift ile kaydırma** + **N ).**

3. Yeni Proje iletişim kutusunun sol **bölmesinde** **C#** öğesini genişletin ve **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından dosyayı Hesaplayıcı olarak **_adlayın._**

   ![Visual Studio IDE'de Yeni Proje iletişim kutusundaki Konsol Uygulaması (.NET Core) proje şablonu](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız,.NET Core platformlar arası geliştirme iş yükünü ekleyerek bu şablonu **edinebilirsiniz.** Aşağıdaki adımları uygulayın:

#### <a name="option-1-use-the-new-project-dialog-box"></a>1. Seçenek: Yeni Proje iletişim kutusunu kullan

1. Yeni **Proje iletişim Visual Studio Yükleyicisi** bölmesindeKimlik aç **bağlantısını** seçin.

   ![Yeni Proje Visual Studio Yükleyicisi Aç bağlantısını seçin](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

   ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. Seçenek: Araçlar menü çubuğunu kullanma

1. Yeni Proje iletişim **kutusundan iptal** edin ve üst menü çubuğunda Araçlar Araçları ve **Özellikleri** > **Al'ı seçin.**

1. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range="vs-2019"

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresini görüntüleme](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde Dil** **listesinden C#** dilini seçin. Ardından Platform **listesinden Windows'u** ve proje **türleri** listesinden Konsol'u seçin. 

   Dil, platform ve proje türü filtrelerini uygulayan Konsol Uygulaması şablonunu **ve** ardından Sonraki'yi **seçin.**

    :::image type="content" source="./media/vs-2019/csharp-create-new-project-console-net-core.png" alt-text="Konsol Uygulaması için C# şablonunu seçin (.NET Framework)":::

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.
   >
   > ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; öyleyse, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** Proje adı kutusuna *Hesaplayıcı* yazın **veya** girin. Ardından, **Sonraki'yi seçin.**

    :::image type="content" source="./media/vs-2019/csharp-name-your-calculator-project.png" alt-text="'Yeni projenizi yapılandırma' penceresinde projenize 'Hesaplayıcı' adını girin":::
   
1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET Core 3.1** zaten seçilmiş olması gerekir. Yoksa **.NET Core 3.1'i seçin.** Ardından **Oluştur'a seçin.**

    :::image type="content" source="./media/vs-2019/csharp-target-framework.png" alt-text="'Ek bilgiler' penceresinde .NET Core 3.1'in seçili olduğundan emin olun":::

   Visual Studio projenizi açar ve bu da varsayılan "Merhaba Dünya" kodunu içerir.

::: moniker-end

## <a name="create-the-app"></a>Uygulama oluşturma

İlk olarak, C# ile bazı temel tamsayı matematiklerini keşfederiz. Ardından, temel hesaplayıcı oluşturmak için kod ekleyebilirsiniz. Bundan sonra, hataları bulmak ve düzeltmek için uygulamada hata ayıklarız. Son olarak da kodu geliştirin ve daha verimli hale getiririz.

### <a name="explore-integer-math"></a>Tamsayı matematiğini inceleme

C# ile bazı temel tamsayı matematikleriyle başlayalım.

1. Kod düzenleyicisinde varsayılan "Merhaba Dünya" silin.

    ![Yeni hesaplayıcı Merhaba Dünya varsayılan kod kodunu silin](./media/csharp-console-calculator-deletehelloworld.png)

   Özellikle şöyle bir satır `Console.WriteLine("Hello World!");` silin: .

1. Onun yerine aşağıdaki kodu yazın:

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

    ![IDE'de IntelliSense otomatik tamamlama özelliğini gösteren tamsayı matematik Visual Studio animasyonu](./media/integer-math-intellisense.gif)

1. Programlarınızı **derlemek ve** çalıştırmak için **Hesaplayıcı'nın** yanındaki yeşil Başlat düğmesini seçin veya **F5 tuşuna basın.**

   ![Uygulamayı araç çubuğundan çalıştırmak için Hesaplayıcı düğmesini seçin](./media/csharp-console-calculator-button.png)

   42 + **119** toplamını (161) ortaya koyan bir konsol penceresi açılır.

    ![Tamsayı matematiği sonuçlarını gösteren konsol penceresi](./media/csharp-console-integer-math.png)

1. **(İsteğe bağlı)** Sonucu değiştirmek için işleci değiştirebilirsiniz. Örneğin, kod satırındaki işleci çıkarma, çarpma veya `+` `int c = a + b;` bölme için olarak `-` `*` `/` değiştirebilirsiniz. Ardından programı çalıştırarak sonuç da değişir.

1. Konsol penceresini kapatın.

### <a name="add-code-to-create-a-calculator"></a>Hesap makinesi oluşturmak için kod ekleme

Projenize daha karmaşık bir hesap makinesi kodu kümesi ekleyerek devam edeceğiz.

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

1. Programınızı **çalıştırmak** için Hesap makinesi'ni seçin veya **F5 tuşuna basın.**

   ![Uygulamayı araç çubuğundan çalıştırmak için Hesaplayıcı düğmesini seçin](./media/csharp-console-calculator-button.png)

   Bir konsol penceresi açılır.

1. Konsol penceresinde uygulamalarınızı görüntüp istemleri takip edin ve **42** ve **119 numaralarını ekleyin.**

   Uygulamanın aşağıdaki ekran görüntüsüne benzer olması gerekir:

    ![Hesaplayıcı uygulamasını gösteren konsol penceresi ve hangi eylemlerin gerçekleştir ekli olduğu istemleri içerir](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>Hesaplayıcıya işlev ekleme

Daha fazla işlev eklemek için kodu ince ayarlayacağız.

### <a name="add-decimals"></a>Ondalık basamak ekleme

Hesap makinesi uygulaması şu anda tam sayıları kabul eder ve döndürür. Ancak ondalık sayılara izin veren bir kod eklerken bu daha kesin bir işlemdir.

Aşağıdaki ekran görüntüsünde olduğu gibi, uygulamayı çalıştırarak 42 sayısını 119 sayısına böler ve sonucun tam olarak 0 (sıfır) olduğunu görebilirsiniz.

![Sonuç olarak ondalık sayı göstermeyen Hesaplayıcı uygulamasını gösteren konsol penceresi](./media/csharp-console-calculator-nodecimal.png)

Şimdi kodu, ondalık sayıları işecek şekilde düzeltin.

1. **Bul ve Değiştir denetimlerini** açmak için Ctrl  +  **H** **tuşlarına** basın.

1. Değişkenin her örneğini `int` olarak `float` değiştirebilirsiniz.

   Bul ve Değiştir denetiminde **Match case** (**Alt** C ) ve Match whole word ( Alt W ) durumlarını +    +  **değiştir'i değiştir'e sahip olun.**

    ![Int değişkeninin float olarak değiştirilmesini gösteren Bul ve Değiştir denetimi animasyonu](./media/find-replace-control-animation.gif)

1. Hesap makinesi uygulamanızı yeniden çalıştırın ve **42 sayısını** **119 sayısına bölün.**

   Uygulamanın artık sıfır yerine ondalık sayı döndürttçene dikkat edin.

    ![Sonuç olarak artık ondalık sayı döndüren Hesaplayıcı uygulamasını gösteren Konsol penceresi](./media/csharp-console-calculator-decimal.png)

Ancak uygulama yalnızca ondalık sonuç üretir. Uygulamanın ondalık sayıları da hesaplayası için kodda birkaç ince ayar daha yapacaktır.

1. Değişkenin **her örneğini olarak** değiştirmek ve yöntemin her örneğini olarak değiştirmek için Bul ve Değiştir denetimi (**Ctrl**  +  **H**) `float` `double` `Convert.ToInt32` `Convert.ToDouble` kullanın.

1. Hesap makinesi uygulamanızı çalıştırın ve **42,5 sayısını** **119,75 sayısına bölün.**

   Uygulamanın artık ondalık değerleri kabul eder ve sonucu olarak daha uzun bir ondalık sayı döndürür.

    ![Artık ondalık sayıları kabul eden ve sonuç olarak daha uzun bir ondalık sayı döndüren Hesap makinesi uygulamasını gösteren konsol penceresi](./media/csharp-console-calculator-usedecimals.png)

    (Kodu düzeltme bölümündeki ondalık basamak sayısını [](#revise-the-code) düzelteceğiz.)

## <a name="debug-the-app"></a>Uygulamada hata ayıklama

Temel hesaplayıcı uygulamamızı iyileştirdik, ancak kullanıcı girişi hataları gibi özel durumları işlemek için henüz başarısız kasalar yok.

Örneğin, bir sayıyı sıfıra bölmeye çalışıyorsanız veya uygulama sayısal karakter (veya tam tersi) bekliyorsa bir alfa karakter girersiniz; uygulama çalışmayı durdurabilir, hata döndürür veya beklenmeyen bir sayısal sonuç döndürür.

Şimdi birkaç yaygın kullanıcı girişi hatasını adım adım irdeleelim, hata ayıklayıcısında bu hataları bu hata ayıklayıcıda bulup kodda düzeltelim.

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

Şimdi, herhangi bir s numarayı sıfıra böldükte uygulama başka bir sayı ister. Daha da iyisi: Siz sıfırdan başka bir sayı sağlayana kadar sormayı durdurmaz.

   ![Sıfır olmayan Visual Studio girişi denetimi eklenmiş switch deyiminin kodunu gösteren kod düzenleyicisinin ekran görüntüsü.](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>"Biçim" hatasını düzeltme

Uygulama sayısal bir karakter (veya tam tersi) beklediğinizde alfa karakter girersiniz, konsol uygulaması donar. Visual Studio kod düzenleyicisinde neyin yanlış olduğunu gösterir.

   ![Kod Visual Studio düzenleyicisi biçim hatası gösteriyor](./media/csharp-console-calculator-format-error.png)

Bu hatayı düzeltmek için daha önce girdiğimiz kodu yeniden düzenlememiz gerekir.

#### <a name="revise-the-code"></a>Kodu düzeltme

Tüm kodu işlemek `program` için sınıfına güvenmek yerine, uygulamamızı iki sınıfa böleriz: `Calculator` ve `Program` .

sınıfı `Calculator` hesaplamanın toplu işlerini işler ve sınıf kullanıcı arabirimini ve hata yakalama çalışmalarını `Program` işler.

Haydi başlayalım.

1. Ad alanı içinde açma `Calculator` ve kapatma ayraçları arasındaki her şeyi silin:

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. Ardından, aşağıdaki gibi `Calculator` yeni bir sınıf ekleyin:

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

1. yönergelerini izleyin ve **42** sayısını **119 sayısına bölün.** Uygulamanın aşağıdaki ekran görüntüsüne benzer olması gerekir:

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

:::moniker range="vs-2019"

Bu öğreticinin ikinci bölümüyle devam edin:

> [!div class="nextstepaction"]
> [2. Bölüm ile devam](tutorial-console-part-2.md)
:::moniker-end

## <a name="see-also"></a>Ayrıca bkz.

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Visual Studio'de C# kodunda hata ayıklamayı Visual Studio](tutorial-debugger.md)
