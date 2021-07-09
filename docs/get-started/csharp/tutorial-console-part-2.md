---
title: 'Öğretici: Basit bir C# konsol uygulamasını genişletme'
description: Visual Studio'de adım adım C# konsol uygulaması geliştirmeyi öğrenin.
ms.custom: vs-acquisition, get-started
ms.date: 04/15/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 84a79015dc4b1147f078b0a970df52c553189c92
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549504"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Öğretici: Basit bir C# konsol uygulamasını genişletme

Bu öğreticide, ilk bölümde oluşturduğunuz konsol Visual Studio genişletmek için Visual Studio kullanmayı öğrenirsiniz. Birden çok proje yönetme ve üçüncü taraf paketlere Visual Studio gibi günlük geliştirme için ihtiyacınız olan özelliklerden bazıları hakkında bilgi edinmek için bu sayfayı kullanabilirsiniz.

Bu serinin ilk [bölümünü tamamladıysanız](tutorial-console.md) Hesaplayıcı konsol uygulamasına sahipsinizdir.  1. bölümü atlamak için projeyi bir GitHub açarak başlayabilirsiniz. C# Hesaplayıcısı uygulaması [vs-tutorial-samples(vs-tutorial-samples)](https://github.com/MicrosoftDocs/vs-tutorial-samples)bir repoda yer alan bu nedenle [öğretici:](../tutorial-open-project-from-repo.md) Bir repodan proje açma adımlarını takip edebilirsiniz.

## <a name="add-a-new-project"></a>Yeni proje ekleme

Gerçek dünya kodu, bir çözümde birlikte çalışan birçok proje içerir. Şimdi Hesap makinesi uygulamasına başka bir proje ek o zaman. Bu, hesaplayıcı işlevlerden bazılarını sağlayan bir sınıf kitaplığıdır.

1. Visual Studio'da, yeni bir proje eklemek için Dosya Ekle Yeni Project üst düzey menü komutunu kullanabilirsiniz, ancak mevcut proje adına sağ tıklar  >    >   ("proje düğümü" olarak adlandırılır) ve projenin kısayol menüsünü (veya bağlam menüsünü) açabilirsiniz. Bu kısayol menüsü, projelerinize işlev eklemek için birçok yol içerir. Bu nedenle, Çözüm Gezgini'de **proje düğüme** sağ tıklayın ve Yeni Ekle'yi **Project.**  >  

1. C# proje şablonu Sınıf **kitaplığını (.NET Standard) seçin.**

   ![Sınıf Kitaplığı proje şablonu seçiminin ekran görüntüsü](media/vs-2019/calculator2-add-project-dark.png)

1. **CalculatorLibrary proje adını yazın ve** Oluştur'a **seçin.** Tekrar sorulsa .NET 3.1'i seçin. Visual Studio yeni projeyi oluşturur ve çözüme ekler.

   ![CalculatorLibrary sınıf Çözüm Gezgini projesinin ekli olduğu uygulamanın ekran görüntüsü](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. *Class1.cs yerine* **CalculatorLibrary.cs dosyasını yeniden adlandırır.** Yeniden adlandırmak için dosyanın **Çözüm Gezgini** tıklar veya sağ tıklar ve Yeniden Adlandır'ı **seçebilir** ya da **F2 tuşuna basın.**

   Dosyada herhangi bir başvuruyu yeniden adlandırmak istediğiniz `Class1` sorulabilirsiniz. Kodu gelecek bir adımda değiştireceğiz.

1. Şimdi bir proje başvurusu eklememiz gerekiyor, böylece ilk proje yeni sınıf kitaplığı tarafından ortaya çıkarilen API'leri kullanabilir.  İlk projedeki **Bağımlılıklar düğümüne sağ** tıklayın ve Başvuru ekle'Project **seçin.**

   ![Başvuru ekle menü Project ekran görüntüsü](media/vs-2019/calculator2-add-project-reference-dark.png)

   Başvuru **Yöneticisi iletişim** kutusu görüntülenir. Bu iletişim kutusu, projelerinize gereken derlemelerin ve COM URL'lerinin yanı sıra diğer projelere başvurular eklemenize olanak sağlar.

   ![Başvuru Yöneticisi iletişim kutusunun ekran görüntüsü](media/vs-2019/calculator2-ref-manager-dark.png)

1. Başvuru **Yöneticisi iletişim** kutusunda **CalculatorLibrary** projesi onay kutusunu seçin ve Tamam'ı **seçin.**  Proje başvurusu, içinde bir **Projeler** düğümü altında **Çözüm Gezgini.**

   ![Proje başvurusuyla Çözüm Gezgini ekran görüntüsü](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. *Program.cs'de* sınıfını ve tüm kodunu `Calculator` seçin ve **CTRL+X** tuşlarına basarak Program.cs'den kesin. Ardından **CalculatorLibrary'de** *CalculatorLibrary.cs* içinde kodu ad alanına `CalculatorLibrary` yapıştırın. Ardından Calculator sınıfını `public` kitaplığın dışında göstermek için kullanın. *CalculatorLibrary.cs'de* yer alan kod artık aşağıdaki koda benzer:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. İlk projenin bir başvurusu vardır ancak Calculator.DoOperation çağrısının çözümlenemezse bir hatayla karşılaştınız. Bunun nedeni CalculatorLibrary'nin farklı bir ad alanı içinde yer alan tam başvuru `CalculatorLibrary` için ad alanı eklemesidir.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Bunun yerine dosyanın başına bir using yönergesi eklemeyi deneyin:

   ```csharp
   using CalculatorLibrary;
   ```

   Bu değişiklik CalculatorLibrary ad alanını çağrı sitesinden kaldırmanız gerekir, ancak şimdi bir belirsizlik vardır. Sınıf `Calculator` CalculatorLibrary içinde mi yoksa Calculator ad alanı mı?  Belirsizlik sorununu çözmek için ad alanını yeniden `CalculatorProgram` adlandıryın.

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Başvuru .NET kitaplıkları: günlüğe yazma

1. Şimdi tüm işlemlerin günlüğünü eklemek ve bir metin dosyasına yazmak istediğinizi varsayalım. .NET `Trace` sınıfı bu işlevselliği sağlar. (Temel yazdırma hata ayıklama teknikleri için de yararlıdır.)  Trace sınıfı System.Diagnostics içindedir ve gibi System.IO sınıflara ihtiyacımız olacak. Bu nedenle `StreamWriter` *CalculatorLibrary.cs'nin* en üstüne using yönergelerini ekleyerek başlayalım:

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Trace sınıfının nasıl kullandığına bakarak, bir dosya akışı ile ilişkili olan sınıfı için bir başvuru üzerinde tutmanız gerekir. Bu da hesaplayıcının nesne olarak daha iyi çalışa bir nesne olduğu anlamına gelir. Bu nedenle *CalculatorLibrary.cs'de Calculator* sınıfının başına bir oluşturucu eklesek.

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. Statik yöntemi üye yöntemi olarak `DoOperation` değiştirmemiz gerekiyor, bu nedenle anahtar sözcüğünü `static` kaldırın.  DoOperation'ın aşağıdaki koda benzin gibi göründüğünüz için günlük için her hesaplamaya çıkış da ek o zaman:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. Şimdi *Program.cs'ye* geri dön, statik çağrı kırmızı bir bayrakla işaretlenir. Bunu düzeltmek için, `calculator` döngüden hemen önce aşağıdaki satırı ekleyerek bir değişken `while (!endApp)` oluşturun:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Ve çağrısı sitesini aşağıdaki gibi değiştirin; böylece bu küçük harfle adlandırılmış nesneye başvurur, böylece statik bir yönteme çağrı yapmak yerine bunu bir üye çağrısı `DoOperation` `calculator` yapar:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Programı yeniden çalıştırın ve bitirin, proje düğümüne sağ tıklayın ve Klasör aç'ı **Dosya Gezgini** seçin, ardından Dosya Gezgini klasörüne gidin. *bin/Debug/netcoreapp3.1 olabilir* ve *calculator.log dosyasını* açın.

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

Bu noktada *CalculatorLibrary.cs* şu şekilde görünüyor olabilir:

```csharp
using System;
using System.IO;
using System.Diagnostics;


namespace CalculatorLibrary
{
    public class Calculator
    {

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                    break;
                case "s":
                    result = num1 - num2;
                    Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                    break;
                case "m":
                    result = num1 * num2;
                    Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }
}
```

*Program.cs de* aşağıdakine benzemektedir:

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Bir NuGet Paketi ekleme: JSON dosyasına yazma

1. Şimdi, işlemleri nesne verilerini depolamak için popüler ve taşınabilir bir biçim olan JSON biçiminde çıkış yapmak istediğinizi varsayalım. Bu işlevi uygulamak için, NuGet paketine Newtonsoft.Jsgerekir. NuGet paketleri, .NET sınıf kitaplıklarının dağıtımı için birincil araçtır. Bu **Çözüm Gezgini** CalculatorLibrary projesinin **Bağımlılıklar** düğümüne sağ tıklayın ve Paket **Yönetimi'ni NuGet seçin.**

   ![Kısayol menüsündeki NuGet Paketlerini Yönet ekran görüntüsü](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   NuGet Paket Yöneticisi açılır.

   ![Ekran görüntüsü NuGet Paket Yöneticisi](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Pakette Newtonsoft.Jsve Yükle'yi **seçin.**

   ![Newtonsoft NuGet paketinin ekran görüntüsü](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Paket indirilir ve projenize eklenir ve uygulamanın Başvurular düğümünde yeni bir giriş **Çözüm Gezgini.**

1. *CalculatorLibrary.cs'nin* System.IO ve Newtonsoft.Jsiçin bir using yönergesi ekleyin.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Şimdi Hesap makinesi oluşturucus una aşağıdaki kodla değiştirin ve JsonWriter üye nesnesini oluşturun:

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. `DoOperation`JSON yazıcı kodunu eklemek için yöntemini değiştirme:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Kullanıcı işlem verilerini girmeyi bitirip JSON söz dizimini tamamlamak için bir yöntem eklemeniz gerekir.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. *Program.cs'de* sonuna Finish çağrısı ekleyin.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Uygulamayı derleme ve çalıştırma ve birkaç işlem girmeyi bitirdikten sonra 'n' komutunu kullanarak uygulamayı düzgün bir şekilde kapatın.  Şimdi, calculatorlog.jsdosyasını açın ve aşağıdakine benzer bir şey görüyor olun:

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="debug-set-and-hit-a-breakpoint"></a>Hata ayıklama: kesme noktası ayarlama ve isabet

Hata Visual Studio hata ayıklayıcısı, programlama hatasının tam olarak hangi noktada olduğunu bulmak için kodunuzu adım adım çalıştırmanıza olanak sağlayan güçlü bir araçtır. Ardından kodunda hangi düzeltmelerin gerekli olduğunu anlarsınız. Visual Studio, programı çalıştırmaya devam etmek için geçici değişikliklere izin verir.

1. *Program.cs'de,* aşağıdaki kodun sol tarafından kenar boşluğuna tıklayın (veya kısayol menüsünü açın ve **Kesme Noktası** Ekle Kesme Noktası'yı seçin  >  veya **F9 tuşuna basın):**

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Görüntülenen kırmızı daire bir kesme noktası gösterir. Kesme noktaları kullanarak uygulamanızı duraklatabilir ve kodu inceebilirsiniz. Herhangi bir yürütülebilir kod satırı üzerinde kesme noktası ayarlayın.

   ![Kesme noktası ayarlama ekran görüntüsü](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Uygulamayı derleyin ve çalıştırın.

1. Çalışan uygulamada hesaplama için bazı değerler yazın:

   - İlk sayı için **8 yazın** ve girin.
   - İkinci sayı için **0 yazın** ve girin.
   - işleci için biraz eğlenceli olabilir; **d yazın** ve girin.

   Uygulama, sol tarafta sarı işaretçi ve vurgulanan kod ile gösterilen kesme noktası oluşturduğunuz yeri askıya alır. Vurgulanan kod henüz yürütülmedi.

   ![Kesme noktasıyla ilgili ekran görüntüsü](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Şimdi, uygulama askıya alındıyla birlikte uygulama durumunu inceebilirsiniz.

## <a name="debug-view-variables"></a>Hata ayıklama: değişkenleri görüntüleme

1. Vurgulanan kodda ve gibi değişkenlerin üzerine `cleanNum1` `op` gelin. DataTips'te görünen bu değişkenlerin ( `8` ve ) geçerli değerlerini `d` görüyorsunuz.

   ![DataTip görüntüleme ekran görüntüsü](media/vs-2019/calculator-2-debug-view-datatip.png)

   Hata ayıklama sırasında, değişkenlerin tutmasını beklediğiniz değerleri tutıp tutmay olmadığını kontrol etmek genellikle sorunları düzeltmek için kritik öneme sahiptir.

2. Alt bölmede Yereller **penceresine** bakın. (Kapalı ise Hata Ayıkla'ya **seçin**  >  **Windows**  >  **Açmak için** yereller.)

   Yereller penceresinde, değeri ve türüyle birlikte şu anda kapsamda olan her bir değişkeni görebilirsiniz.

   ![Yereller penceresinin ekran görüntüsü](media/vs-2019/calculator-2-debug-locals-window.png)

3. Otomatikler **penceresine** bakın.

   Otomatikler penceresi Yerel öğeler  penceresine benzer, ancak uygulamanın duraklatılmış olduğu geçerli kod satırına hemen önce ve sonra gelen değişkenleri gösterir.

   Ardından, hata ayıklayıcısında her bir deyiminde adımlama olarak adlandırılan bir kod *yürütebilirsiniz.*

## <a name="debug-step-through-code"></a>Hata ayıklama: kodda adım adım

1. **F11 tuşuna** basın (veya **Hata Ayıkla**  >  **adımını içine alın).**

   Uygulama, Adımla komutunu kullanarak geçerli deyimi yürütür ve sonraki yürütülebilir deyime (genellikle bir sonraki kod satırı) ilerler. Sol tarafta sarı işaretçi her zaman geçerli deyimi gösterir.

   ![Komutun içine adımla ekran görüntüsü](media/vs-2019/calculator-2-debug-step-into.png)

   sınıfındaki yöntemine `DoOperation` `Calculator` girdiniz.

1. Program akışınıza hiyerarşik bir bakış elde etmek için Çağrı Yığını **penceresine** bakın. (Kapalı ise Hata Ayıkla'ya **seçin**  >  **Windows**  >  **Çağrı Yığını**.)

   ![Çağrı yığınının ekran görüntüsü](media/vs-2019/calculator-2-debug-call-stack.png)

   Bu görünüm sarı işaretçiyle gösterilen geçerli yöntemi, ikinci satır `Calculator.DoOperation` `Main` ise *Program.cs'de* yönteminden çağıran işlevi gösterir. Çağrı **Yığını** penceresi, yöntemlerin ve işlevlerin çağrıldığı sırayı gösterir. Ayrıca, kısayol menüsünden Kaynak Koduna Git gibi birçok **hata ayıklayıcısı** özelliğine erişim sağlar.

1. Uygulama deyimi duraklatana kadar **F10** 'a (veya Hata Ayıklama   >  Adımı) birkaç kez `switch` basın.

   ```csharp
   switch (op)
   {
   ```

   Üzerinden Adımla komutu, Geçerli deyim bir işlev çağırsa, hata ayıklayıcının çağıran işlevde kodu çalıştırması ve işlev dönene kadar yürütmeyi askıya almama durumu dışında, Adımla komutuna benzer. Belirli bir işlevle ilgilenmezken Kodda gezinmenin daha hızlı bir yoludur.

1. Uygulamanın aşağıdaki kod satırına duraklatmak için **F10'a** bir kez daha basın.

   ```csharp
   if (num2 != 0)
   {
   ```

   Bu kod, sıfıra bölme büyük/küçük harflerini denetler. Uygulama devam ederse, genel bir özel durum (hata) oluşturur, ancak bunu bir hata olarak değerlendirin ve konsolda döndürülen gerçek değeri görüntüleme gibi başka bir şey yapmak istediğiniz varsayın. Seçeneklerden biri, kodda değişiklik yapmak ve ardından hata ayıklamaya devam etmek için Düzenle ve devam adlı bir hata ayıklayıcı özelliği kullanmaktır. Ancak, yürütme akışını geçici olarak değiştirmeniz için size farklı bir püf noktası gösteriz.

## <a name="debug-test-a-temporary-change"></a>Hata ayıklama: Geçici bir değişikliği test etmek

1. Deyimde duraklatılmış olan sarı `if (num2 != 0)` işaretçiyi seçin ve aşağıdaki deyime sürükleyin.

   ```csharp
   result = num1 / num2;
   ```

   Bunu yaparak uygulama deyimini tamamen `if` atlar, böylece sıfıra böldükte ne olacağını görebilir.

1. Kod **satırı yürütmek için F10** tuşuna basın.

1. değişkeninin `result` üzerine gelin ve değerini depolar. `Infinity`

   C# `Infinity` içinde, sıfıra bölerek elde edilen sonuç olur.

1. **F5 tuşuna** basın (veya Hata **Ayıklama Devam**  >  **Hata Ayıklama).**

   Infinity simgesi, matematik işlemi sonucunda konsolda gösterilir.

1. 'n' komutunu kullanarak uygulamayı düzgün bir şekilde kapatın.

## <a name="code-complete"></a>Kod tamamlandı

Tüm adımlar tamamlandıktan sonra *CalculatorLibrary.cs* dosyasının tam kodu şu şekildedir:

```csharp
using System;
using System.IO;
using System.Diagnostics;
using Newtonsoft.Json;

namespace CalculatorLibrary
{
    public class Calculator
    {

        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }

        public void Finish()
        {
            writer.WriteEndArray();
            writer.WriteEndObject();
            writer.Close();
        }
    }
}
```

Program.cs için kod *şu şekildedir:* 

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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
            calculator.Finish();
            return;
        }
    }
}
```

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamladıktan sonra! Daha da fazla bilgi edinmek için aşağıdaki öğreticilerle devam edin.

> [!div class="nextstepaction"]
> [Daha fazla C# öğreticisi ile devam edin](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [IDE'Visual Studio genel bakış ile devam](/../visual-studio-ide.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
- [Visual Studio'de C# kodunda hata ayıklamayı Visual Studio](tutorial-debugger.md)
