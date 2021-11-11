---
title: 'Öğretici 2: C# konsol uygulamanızı genişletme'
description: adım adım Visual Studio bir C# konsol uygulaması geliştirmeyi öğrenin.
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: anandmeg
ms.author: meghaanand
manager: jmartens
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b4b323611897a7977d906eb585f49006b54e5b9e
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264154"
---
# <a name="tutorial-extend-c-console-app-and-debug-in-visual-studio-part-2-of-2"></a>öğretici: Visual Studio 'de C# konsol uygulamasını ve hata ayıklamayı genişletme (bölüm 2/2)

bu öğretici serisinin 2. bölümünde, günlük geliştirme için ihtiyaç duyduğunuz Visual Studio derleme ve hata ayıklama özellikleri hakkında biraz daha ayrıntılı bilgi sahibiz. Bu özellikler birden çok projenin yönetilmesini, hata ayıklamayı ve üçüncü taraf paketlerine başvurmayı içerir. [bu öğreticinin 1. bölümünde](tutorial-console.md)oluşturduğunuz C# konsol uygulamasını çalıştırın ve Visual Studio tümleşik geliştirme ortamının (ıde) bazı özelliklerini keşfedebilirsiniz. Bu öğretici, iki bölümden oluşan bir öğretici serisinin 2. parçasıdır.

Bu öğreticide şunları yaptınız:

> [!div class="checklist"]
> * İkinci bir proje ekleyin.
> * Başvuru kitaplıkları ve paket Ekle.
> * Daha fazla hata ayıklama yapın.
> * Tamamlanan kodunuzu inceleyin.


## <a name="prerequisites"></a>Önkoşullar

Bu makalede çalışmak için şu hesap makinesi uygulamalarından birini kullanabilirsiniz:

- [Bu öğreticinin 1. bölümünde hesap makinesi konsol uygulaması](tutorial-console.md).
- [Vs-öğreticisi-Samples](https://github.com/MicrosoftDocs/vs-tutorial-samples)deposunda C# Hesaplayıcı uygulaması. Başlamak için [depodan uygulamayı açın](../tutorial-open-project-from-repo.md).

## <a name="add-another-project"></a>Başka proje ekleme

Gerçek dünyada kod, bir çözümde birlikte çalışan projeler içerir. Hesaplayıcı uygulamanıza, bazı Hesaplayıcı işlevleri sağlayan bir sınıf kitaplığı projesi ekleyebilirsiniz.

Visual Studio,   >    >  yeni bir proje eklemek için menü komut dosyasını **yeni Project** ekle ' yi kullanın. Bağlam menüsünden bir proje eklemek için **Çözüm Gezgini** ' de çözüme sağ tıklayabilirsiniz.

::: moniker range="vs-2019"
1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve  > **yeni Project** ekle ' yi seçin.

1. **Yeni Proje Ekle** penceresinde, arama kutusuna *sınıf kitaplığı* yazın. C# **sınıf kitaplığı** proje şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Sınıf kitaplığı proje şablonu seçiminin ekran görüntüsü.](media/vs-2019/calculator2-add-project-dark.png)

1. **Yeni projenizi yapılandırın** ekranında, *hesaplatorlibrary* proje adını yazın ve ardından **İleri**' yi seçin.
   
1. İstendiğinde .NET 3,1 ' i seçin. Visual Studio yeni projeyi oluşturur ve çözüme ekler.

   ![Hesaplatorlibrary sınıf kitaplığı projesi eklenen Çözüm Gezgini ekran görüntüsü.](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. *Class1. cs* dosyasını *hesaplatorlibrary. cs* olarak yeniden adlandırın. Dosyayı yeniden adlandırmak için **Çözüm Gezgini** adı ' na sağ tıklayıp **Yeniden Adlandır**' ı seçin, adı seçin ve **F2** tuşuna basabilir ya da adı seçip, ardından yazmak için yeniden tıklayabilirsiniz.

   Bir ileti, dosyadaki başvuruları yeniden adlandırmak isteyip istemediğinizi sorabilir `Class1` . Daha sonraki bir adımda kodu değiştirdiğinizden, yanıt sizin için önemlidir.

1. Şimdi bir proje başvurusu ekleyin, bu nedenle ilk proje yeni sınıf kitaplığının sunduğu API 'Leri kullanabilir. **hesaplayıcı** projesindeki **bağımlılıklar** düğümüne sağ tıklayın ve **Project başvuru ekle**' yi seçin.

   ![Project başvuru ekle menü öğesinin ekran görüntüsü.](media/vs-2019/calculator2-add-project-reference-dark.png)

   **Başvuru Yöneticisi** iletişim kutusu görüntülenir. Bu iletişim kutusunda, projelerinize gereken diğer projelere, derlemelere ve COM DLL 'Lerine başvurular ekleyebilirsiniz.

1. **Başvuru Yöneticisi** iletişim kutusunda, **Hesaplayıt kitaplığı** projesinin onay kutusunu seçin ve ardından **Tamam**' ı seçin.

   ![Başvuru Yöneticisi iletişim kutusunun ekran görüntüsü.](media/vs-2019/calculator2-ref-manager-dark.png)

   Proje başvurusu **Çözüm Gezgini** Içindeki bir **Projeler** düğümü altında görüntülenir.

   ![Proje başvurusuyla Çözüm Gezgini ekran görüntüsü.](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. *Program. cs*' de, `Calculator` sınıfı ve tüm kodunu seçin ve **CTRL** + **X** tuşlarına basarak kesin. Ardından, *hesap \ kitaplık. cs*' de kodu `CalculatorLibrary` ad alanına yapıştırın.
   
   Ayrıca `public` , onu kitaplığın dışına çıkarmak Için Hesaplayıcı sınıfından önce ekleyin.

   *Hesaplatorlibrary. cs* artık aşağıdaki koda benzemelidir:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. *Program. cs* de bir başvuruya sahiptir, ancak çağrının çözümlenmediğini bildiren bir hata oluştu `Calculator.DoOperation` . Çünkü bu `CalculatorLibrary` , farklı bir ad alanında yer alan. Tam nitelikli bir başvuru için, bu `CalculatorLibrary` ad alanını `Calculator.DoOperation` çağrıya ekleyebilirsiniz:

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Ya da `using` dosyanın başlangıcına bir yönerge eklemeyi deneyebilirsiniz:

   ```csharp
   using CalculatorLibrary;
   ```

   Yönergesini eklemek, `using` `CalculatorLibrary` çağıran siteden ad alanını kaldırmanızı sağlamalıdır, ancak şimdi bir belirsizlik var. `Calculator`Sınıf `CalculatorLibrary` veya `Calculator` ad alanı mı?
   
   Belirsizliği çözmek için, ad alanını `Calculator` `CalculatorProgram` *program. cs* içinde olarak değiştirin.

   ```csharp
   namespace CalculatorProgram
   ```

::: moniker-end
::: moniker range=">=vs-2022"
1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve  > **yeni Project** ekle ' yi seçin.

1. **Yeni Proje Ekle** penceresinde, arama kutusuna *sınıf kitaplığı* yazın. C# **sınıf kitaplığı** proje şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Sınıf kitaplığı proje şablonu seçiminin ekran görüntüsü.](media/vs-2022/calculator-add-project.png)

1. **Yeni projenizi yapılandırın** ekranında, *hesaplatorlibrary* proje adını yazın ve ardından **İleri**' yi seçin.
   
1. **Ek bilgi** ekranında, .net 6,0 seçilidir. **Oluştur**’u seçin.
   
   Visual Studio yeni projeyi oluşturur ve çözüme ekler.
   
   ![Hesaplatorlibrary sınıf kitaplığı projesi eklenen Çözüm Gezgini ekran görüntüsü.](media/vs-2022/calculator-solution-explorer-with-class-library.png)

1. *Class1. cs* dosyasını *hesaplatorlibrary. cs* olarak yeniden adlandırın. Dosyayı yeniden adlandırmak için **Çözüm Gezgini** adı ' na sağ tıklayıp **Yeniden Adlandır**' ı seçin, adı seçin ve **F2** tuşuna basabilir ya da adı seçip, ardından yazmak için yeniden tıklayabilirsiniz.

   Bir ileti, dosyadaki başvuruları yeniden adlandırmak isteyip istemediğinizi sorabilir `Class1` . Daha sonraki bir adımda kodu değiştirdiğinizden, yanıt sizin için önemlidir.

1. Şimdi bir proje başvurusu ekleyin, bu nedenle ilk proje yeni sınıf kitaplığının sunduğu API 'Leri kullanabilir. **hesaplayıcı** projesindeki **bağımlılıklar** düğümüne sağ tıklayın ve **Project başvuru ekle**' yi seçin.

   ![Project başvuru ekle menü öğesinin ekran görüntüsü.](media/vs-2022/calculator-add-project-reference.png)

   **Başvuru Yöneticisi** iletişim kutusu görüntülenir. Bu iletişim kutusunda, projelerinize gereken diğer projelere, derlemelere ve COM DLL 'Lerine başvurular ekleyebilirsiniz.

1. **Başvuru Yöneticisi** iletişim kutusunda, **Hesaplayıt kitaplığı** projesinin onay kutusunu seçin ve ardından **Tamam**' ı seçin.

   ![Başvuru Yöneticisi iletişim kutusunun ekran görüntüsü.](media/vs-2022/calculator-reference-manager.png)

   Proje başvurusu **Çözüm Gezgini** Içindeki bir **Projeler** düğümü altında görüntülenir.

   ![Proje başvurusuyla Çözüm Gezgini ekran görüntüsü.](media/vs-2022/calculator-solution-explorer-with-project-reference.png)

1. *Program. cs*' de, `Calculator` sınıfı ve tüm kodunu seçin ve **CTRL** + **X** tuşlarına basarak kesin. Ardından, *hesap \ kitaplık. cs*' de kodu `CalculatorLibrary` ad alanına yapıştırın.
   
   Ayrıca `public` , onu kitaplığın dışına çıkarmak Için Hesaplayıcı sınıfından önce ekleyin.

   *Hesaplatorlibrary. cs* artık aşağıdaki koda benzemelidir:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. *Program. cs* de bir başvuruya sahiptir, ancak çağrının çözümlenmediğini bildiren bir hata oluştu `Calculator.DoOperation` . Çünkü bu `CalculatorLibrary` , farklı bir ad alanında yer alan. Tam nitelikli bir başvuru için, bu `CalculatorLibrary` ad alanını `Calculator.DoOperation` çağrıya ekleyebilirsiniz:

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Ya da `using` dosyanın başlangıcına bir yönerge eklemeyi deneyebilirsiniz:

   ```csharp
   using CalculatorLibrary;
   ```

   Yönergesini eklemek, `using` `CalculatorLibrary` çağıran siteden ad alanını kaldırmanızı sağlamalıdır, ancak şimdi bir belirsizlik var. `Calculator`Sınıf `CalculatorLibrary` veya `Calculator` ad alanı mı?
   
   Belirsizliği çözümlemek için, ad alanını `Calculator` `CalculatorProgram` hem *program. cs* hem de *hesaplatorlibrary. cs* olarak olarak değiştirin.

   ```csharp
   namespace CalculatorProgram
   ```
::: moniker-end

## <a name="reference-net-libraries-write-to-a-log"></a>Başvuru .NET kitaplıkları: bir günlüğe yazma

.NET `Trace` sınıfını, tüm işlemlerin günlüğünü eklemek ve bir metin dosyasına yazmak için kullanabilirsiniz. `Trace`Sınıfı, temel yazdırma hata ayıklama teknikleri için de kullanışlıdır. `Trace`Sınıfı içinde bulunur `System.Diagnostics` ve `System.IO` gibi sınıfları kullanır `StreamWriter` .

1. , `using` *Hesaplakitaplığı. cs*' nin en üstündeki yönergeleri ekleyerek başlayın:

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Sınıfının bu kullanımı, `Trace` bir FILESTREAM ile ilişkilenme sınıfı için bir başvuruya sahip olmalıdır. Bu gereksinim, hesap makinesinin bir nesne olarak daha iyi çalışacağı anlamına gelir; bu nedenle, `Calculator` *Hesaplayılibrary. cs* içindeki sınıfın başlangıcına bir Oluşturucu ekleyin.

   `static`Statik `DoOperation` yöntemi bir üye yöntemi olarak değiştirmek için anahtar sözcüğünü de kaldırın.

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

1. Her hesaplamaya günlük çıktısı ekleyin. `DoOperation` Şimdi aşağıdaki kod gibi görünmelidir:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" if an operation, such as division, could result in an error.

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

1. *Program. cs*' ye geri döndüğünüzde, kırmızı dalgalı alt çizgi artık statik çağrıyı işaretler. Hatayı onarmak için, `calculator` döngüden hemen önce aşağıdaki kod satırını ekleyerek bir değişken oluşturun `while (!endApp)` :

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Ayrıca, `DoOperation` çağrı sitesini küçük harfli adlı nesneye başvuracak şekilde değiştirin `calculator` . Kod artık statik yönteme yapılan bir çağrı yerine üye çağrısıdır.

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Uygulamayı tekrar çalıştırın. Bitirin, Hesap makinesi proje  düğümüne sağ tıklayın ve hesaplayıcıda Klasör **Aç'ı Dosya Gezgini.**

1. Bu Dosya Gezgini *bin/Debug/* altındaki çıkış klasörüne gidin ve *calculator.log dosyasını* açın. Çıkış aşağıdakine benzer olmalıdır:

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

Bu noktada *CalculatorLibrary.cs* şu koda benzer:

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
            double result = double.NaN; // Default value is "not-a-number" if an operation, such as division, could result in an error.

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

*Program.cs* aşağıdaki kod gibi görünüyor olmalı:

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

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Bir NuGet Paketi Ekleme: JSON dosyasına yazma

Nesne verilerini depolamaya yönelik popüler ve taşınabilir bir biçim olan JSON'daki işlemlerin çıkışını yapmak *için, Newtonsoft.Json* NuGet başvurabilirsiniz. NuGet paketleri . NET sınıf kitaplıkları için birincil dağıtım yöntemidir.

1. Bu **Çözüm Gezgini** **CalculatorLibrary** projesi **için Bağımlılıklar** düğümüne sağ tıklayın ve Paket Paketlerini **Yönet'NuGet seçin.**

   ::: moniker range="vs-2019"
   ![Kısayol menüsündeki NuGet Paketlerini Yönet'in ekran görüntüsü.](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Kısayol menüsündeki NuGet Paketlerini Yönet'in ekran görüntüsü.](media/vs-2022/calculator-manage-nuget-packages.png)
   ::: moniker-end

   NuGet Paket Yöneticisi açılır.

   ::: moniker range="vs-2019"
   ![Uygulamanın ekran NuGet Paket Yöneticisi.](media/vs-2019/calculator2-nuget-package-manager-dark.png)
   ::: moniker-end

1. *Newtonsoft.Json paketini arayın ve seçin* ve Yükle'yi **seçin.**

   ::: moniker range="vs-2019"
   ![NuGet Paket Yöneticisi'de Yer alan NuGet bilgileri içeren Newtonsoft J SON NuGet Paket Yöneticisi.](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)
   
   Visual Studio paketi indirir ve projeye ekler. içinde Başvurular düğümünde yeni bir giriş **Çözüm Gezgini.**
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![NuGet Paket Yöneticisi'daki NuGet bilgileri içeren Newtonsoft J SON NuGet Paket Yöneticisi.](media/vs-2022/calculator-nuget-newtonsoft-json.png)
   Değişiklikleri kabul edip etmeyip kabul et istemiyle karşılanmazsanız Tamam'ı **seçin.**
   
   Visual Studio paketi indirir ve projeye ekler. içinde paketler düğümünde yeni **bir** giriş **Çözüm Gezgini.**
   ::: moniker-end

1. `using` `Newtonsoft.Json` *CalculatorLibrary.cs'nin* başına için bir yönerge ekleyin.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Üye `JsonWriter` nesnesini oluşturun ve oluşturucusu `Calculator` aşağıdaki kodla değiştirin:

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

1. `DoOperation`JSON kodunu eklemek için yöntemini `writer` değiştirme:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" if an operation, such as division, could result in an error.
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

1. Kullanıcı işlem verilerini girmeyi bitirip JSON söz dizimini tamamlamak için bir yöntem ekleyin.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. *Program.cs'nin sonunda,*'den `return;` önce için bir çağrı `Finish` ekleyin:

   ```csharp
            // Add call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Uygulamayı derleme ve çalıştırma ve birkaç işlem girmeyi bitirdikten sonra *n* komutunu girerek uygulamayı kapatın.
   
1. *calculatorlog.json dosyasını Dosya Gezgini.* Aşağıdaki içeriğe benzer bir şey görüyor gerekir:

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

## <a name="debug-set-and-hit-a-breakpoint"></a>Hata ayıklama: Kesme noktası ayarlama ve isabet

Hata Visual Studio aracı güçlü bir araçtır. Hata ayıklayıcı, programlama hatasının tam olarak hangi noktada olduğunu bulmak için kodunuz boyunca adım adım yol kullanabilir. Ardından, hangi düzeltmeler yapmak zorunda olduğunu anlıyabilirsiniz ve uygulama çalıştırmaya devam etmek için geçici değişiklikler yapabilirsiniz.

1. *Program.cs'de,* aşağıdaki kod satırına sol tarafta yer alan oluk içinde tıklayın. Ayrıca satıra tıklar, **F9'u** seçer veya satıra sağ tıklar ve Kesme Noktası Ekle **Kesme Noktası** seçeneğini  >  **de seçersiniz.**

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Görüntülenen kırmızı nokta bir kesme noktası gösterir. Kesme noktaları kullanarak uygulamanızı duraklatabilir ve kodu inceebilirsiniz. Herhangi bir yürütülebilir kod satırı üzerinde kesme noktası ayarlayın.

   ![Kesme noktası ayarlamayı gösteren ekran görüntüsü.](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Uygulamayı derleyin ve çalıştırın. Hesaplama için aşağıdaki değerleri girin:

   - İlk sayı için *8 girin.*
   - İkinci sayı için *0 girin.*
   - işleci için biraz eğlenceli bir şeyler bakalım. *d girin.*

   Uygulama, kesme noktası oluşturduğunuz yeri askıya alır. Bu, sol tarafta sarı işaretçi ve vurgulanan kod ile birlikte görünür. Vurgulanan kod henüz yürütülmedi.

   ![Kesme noktasıyla ilgili ekran görüntüsü](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Artık uygulama askıya alındı ve uygulama durumunu inceebilirsiniz.

## <a name="debug-view-variables"></a>Hata ayıklama: Değişkenleri görüntüleme

1. Vurgulanan kodda ve gibi değişkenlerin üzerine `cleanNum1` `op` gelin. Bu değişkenlerin geçerli değerleri ve `8` `d` sırasıyla DataTips içinde görünür.

   ![DataTip görüntülemeyi gösteren ekran görüntüsü.](media/vs-2019/calculator-2-debug-view-datatip.png)

   Hata ayıklama sırasında değişkenlerin beklediğiniz değerleri tutıp tutmay olmadığını kontrol etmek genellikle sorunları düzeltmek için kritik öneme sahiptir.

2. Alt bölmede YerelLer **penceresine** bakın. Kapalı ise YerelLer'de **hata**  >  **ayıkla'Windows'ı**  >   seçerek açın.

   **YerelLer** penceresinde, şu anda kapsamda olan her değişken, değeri ve türüyle birlikte gösterilir.

   ::: moniker range="vs-2019"
   ![Yereller penceresinin ekran görüntüsü.](media/vs-2019/calculator-2-debug-locals-window.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Yereller penceresinin ekran görüntüsü.](media/vs-2022/calculator-debug-locals-window.png)
   ::: moniker-end

3. Otomatikler **penceresine** bakın.

   Otomatikler penceresi Yerel öğeler  penceresine benzer, ancak uygulamanın duraklatılmış olduğu geçerli kod satırına hemen önce ve sonra gelen değişkenleri gösterir.

Ardından, hata ayıklayıcısında her bir deyimde adımlama olarak adlandırılan bir kod *yürütün.*

## <a name="debug-step-through-code"></a>Hata ayıklama: Kodda adım adım ilerler

1. **F11 tuşuna basın** veya Hata **Ayıkla**  >  **adımını seçin.**

   Uygulama, Adımla komutunu kullanarak geçerli deyimi yürütür ve genellikle bir sonraki kod satırı olan sonraki yürütülebilir deyime ilerler. Sol tarafta sarı işaretçi her zaman geçerli deyimi gösterir.

   ![Komutun içine adımla ekran görüntüsü](media/vs-2019/calculator-2-debug-step-into.png)

   sınıfındaki `DoOperation` yöntemine `Calculator` girdiniz.

1. Program akışınıza hiyerarşik bir bakış elde etmek için Çağrı Yığını **penceresine** bakın. Kapalı ise Çağrı Yığınında **Hata Ayıkla'Windows'ı**  >    >   seçerek açın.

   ![Çağrı yığınının ekran görüntüsü](media/vs-2019/calculator-2-debug-call-stack.png)

   Bu görünüm, sarı `Calculator.DoOperation` işaretçiyle gösterilen geçerli yöntemi gösterir. İkinci satır, `Main` *Program.cs'de* yönteminden yöntemini çağıran işlevi gösterir.
   
   Çağrı **Yığını** penceresi, yöntemlerin ve işlevlerin çağrıldığı sırayı gösterir. Bu pencere, kısayol menüsünden Kaynak Koda Git gibi birçok **hata ayıklayıcısı** özelliğine de erişim sağlar.

1. **F10 tuşuna** basın veya **uygulama deyimde** duraklatana kadar birkaç kez Hata  >  Ayıkla Adımını `switch` Seçin.

   ```csharp
   switch (op)
   {
   ```

   Üzerinden Adımla komutu, Geçerli deyim bir işlev çağırsa, hata ayıklayıcının işlevinde kodu çalıştırması ve işlev dönene kadar yürütmeyi askıya almama durumu dışında, Adımla komutuna benzer. Belirli bir işlevle ilgilenmezsiniz, Adım At'dan daha hızlıdır.

1. **F10'a** bir kez daha basın, böylece uygulama aşağıdaki kod satırı üzerinde duraklatılır.

   ```csharp
   if (num2 != 0)
   {
   ```

   Bu kod, sıfıra bölme büyük/küçük harflerini denetler. Uygulama devam ederse, genel bir özel durum (hata) oluşturur, ancak konsolda döndürülen gerçek değeri görüntüleme gibi başka bir şey denemek de iyi olabilir. Seçeneklerden biri, kodda değişiklik yapmak ve ardından hata ayıklamaya devam etmek için *edit-and-continue* adlı bir hata ayıklayıcı özelliği kullanmaktır. Ancak, yürütme akışını geçici olarak değiştirmek farklı bir numaradır.

## <a name="debug-test-a-temporary-change"></a>Hata ayıklama: Geçici bir değişikliği test etmek

1. Deyimde duraklatılmış olan sarı `if (num2 != 0)` işaretçiyi seçin ve aşağıdaki deyime sürükleyin:

   ```csharp
   result = num1 / num2;
   ```

   İşaretçiyi buraya sürüklemek uygulamanın deyimi tamamen atlamasına neden olur, böylece sıfıra `if` böldükte ne olacağını görebilirsiniz.

1. Kod **satırı yürütmek için F10** tuşuna basın.

1. Değişkenin üzerine `result` gelirsiniz, Infinity değerini **gösterir.** C# ile Infinity, sıfıra bölmenin sonucu olur.

1. **F5 tuşuna basın** veya Hata Ayıklama **Devam Hata**  >  **Ayıklama'ya basın.**

   Matematik işlemi sonucunda konsolda sonsuz simgesi görünür.

1. n komutunu girerek uygulamayı düzgün *bir şekilde* kapatın.

## <a name="code-complete"></a>Kod tamamlandı

Tüm adımları tamamlandıktan sonra *CalculatorLibrary.cs* dosyasının tam kodu şu şekildedir:

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
            double result = double.NaN; // Default value is "not-a-number" if an operation, such as division, could result in an error.
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

Tebrikler, bu öğreticiyi tamamladıktan sonra! Daha fazla bilgi edinmek için aşağıdaki içeriğe devam etmek için:

- [Daha fazla C# öğreticiyle devam edin](/dotnet/csharp/tutorials/).
- [hızlı başlangıç: ASP.NET Core bir web uygulaması oluşturun](../../ide/quickstart-aspnet-core.md).
- [Visual Studio C# kodunda hata ayıklamayı öğrenin](tutorial-debugger.md).
- [Birim testlerini oluşturmayı ve çalıştırmayı adım adım](../../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)inceleyin.
- [Bir C# programı çalıştırın](run-program.md).
- [C# IntelliSense hakkında bilgi edinin](../../ide/visual-csharp-intellisense.md).
- [Visual Studio ıde 'ye genel bakış ile devam edin](visual-studio-ide.md).
