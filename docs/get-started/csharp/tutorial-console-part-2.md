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
ms.openlocfilehash: 86649110e83a9bce0768bddc81f148b3c4370793
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128430568"
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
   
   Belirsizliği çözümlemek için, ad alanını `Calculator` `CalculatorProgram` hem *program. cs* hem de *hesaplatorlibrary. cs* olarak olarak değiştirin.

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

   Ayrıca, `DoOperation` çağrı sitesini küçük harfli adlı nesneye başvuracak şekilde değiştirin `calculator` . Kod, bir statik yöntem çağrısı yerine artık bir üye çağrıdır.

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Uygulamayı tekrar çalıştırın. İşiniz bittiğinde, **Hesaplayıcı** proje düğümüne sağ tıklayın ve **klasörü dosya Gezgini 'nde aç**' ı seçin.

1. Dosya Gezgini 'nde, *bin/Debug/* altındaki çıkış klasörüne gidin ve *Hesaplayıcı. log* dosyasını açın. Çıkış aşağıdakine benzer olmalıdır:

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

Bu noktada, *Hesaplatorlibrary. cs* şu koda benzemelidir:

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

*Program. cs* aşağıdaki kod gibi görünmelidir:

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

## <a name="add-a-nuget-package-write-to-a-json-file"></a>NuGet paketi ekleme: JSON dosyasına yazma

nesne verilerini depolamak için popüler ve taşınabilir bir biçimde JSON 'daki çıkış işlemlerine, *newtonsoft. JSON* NuGet paketine başvurabilirsiniz. NuGet paketler, .net sınıf kitaplıkları için birincil dağıtım yöntemidir.

1. **Çözüm Gezgini**' de, **hesaplatorlibrary** projesi için **bağımlılıklar** düğümüne sağ tıklayın ve **NuGet paketlerini yönet**' i seçin.

   ::: moniker range="vs-2019"
   ![kısayol menüsündeki NuGet paketlerinin yönetme ekran görüntüsü.](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![kısayol menüsündeki NuGet paketlerinin yönetme ekran görüntüsü.](media/vs-2022/calculator-manage-nuget-packages.png)
   ::: moniker-end

   NuGet Paket Yöneticisi açılır.

   ::: moniker range="vs-2019"
   ![NuGet Paket Yöneticisi ekran görüntüsü.](media/vs-2019/calculator2-nuget-package-manager-dark.png)
   ::: moniker-end

1. *Newtonsoft. JSON* paketini arayıp seçin ve ardından **Install**' ı seçin.

   ::: moniker range="vs-2019"
   ![newtonsoft J SON NuGet paket bilgilerinin NuGet Paket Yöneticisi ekran görüntüsü.](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)
   
   Visual Studio paketi indirir ve projeye ekler. **Çözüm Gezgini**' deki başvurular düğümünde yeni bir giriş görüntülenir.
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![newtonsoft J SON NuGet paket bilgilerinin NuGet Paket Yöneticisi ekran görüntüsü.](media/vs-2022/calculator-nuget-newtonsoft-json.png)
   Değişikliklerin kabul edilip edilmeyeceğini onaylamanız istenirse **Tamam**' ı seçin.
   
   Visual Studio paketi indirir ve projeye ekler. **Çözüm Gezgini** içindeki **paketler** düğümünde yeni bir giriş görüntülenir.
   ::: moniker-end

1. `using` `Newtonsoft.Json` *Hesaplakitaplığı. cs*' nin başlangıcında için bir yönerge ekleyin.

   ```csharp
   using Newtonsoft.Json;
   ```

1. `JsonWriter`Üye nesnesini oluşturun ve `Calculator` oluşturucuyu aşağıdaki kodla değiştirin:

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

1. `DoOperation`JSON kodunu eklemek için yöntemi değiştirin `writer` :

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

1. Kullanıcı işlem verilerini girmeyi tamamladıktan sonra JSON sözdizimini tamamlayacak bir yöntem ekleyin.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. *Program. cs*' nin sonunda, öğesinden önce, `return;` öğesine bir çağrı ekleyin `Finish` :

   ```csharp
            // Add call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Uygulamayı derleyin ve çalıştırın ve birkaç işlem girmeyi tamamladıktan sonra *n* komutunu girerek uygulamayı kapatın.
   
1. Dosya Gezgini 'nde *hesaplatorlog. JSON* dosyasını açın. Aşağıdaki içeriğe benzer bir şey görmeniz gerekir:

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

## <a name="debug-set-and-hit-a-breakpoint"></a>Hata Ayıkla: kesme noktası ayarlama ve isabet

Visual Studio hata ayıklayıcı güçlü bir araçtır. Hata ayıklayıcı, programlama hatası olduğunda tam noktayı bulmak için kodunuzda adım adım ileredebilir. Daha sonra yapmanız gereken düzeltmeleri anlayabilir ve uygulamanızı çalıştırmaya devam edebilmeniz için geçici değişiklikler yapmanız yeterlidir.

1. *Program. cs*' de, aşağıdaki kod satırının solundaki cilt payını tıklatın. Ayrıca, satıra tıklayıp **F9**' i seçebilir ya da satıra sağ **tıklayıp kesme**  >  **noktası Ekle kesme noktası**' nı seçebilirsiniz.

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Görüntülenen kırmızı nokta bir kesme noktasını gösterir. Kesme noktalarını kullanarak uygulamanızı duraklatabilir ve kodu inceleyebilirsiniz. Herhangi bir çalıştırılabilir kod satırında bir kesme noktası ayarlayabilirsiniz.

   ![Kesme noktası ayarlamayı gösteren ekran görüntüsü.](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Uygulamayı derleyin ve çalıştırın. Hesaplama için aşağıdaki değerleri girin:

   - İlk numara için *8* girin.
   - İkinci numara için *0* girin.
   - İşleci için biraz eğlenceye sahip olalım. *D* girin.

   Uygulama, sol tarafta sarı işaretçiye ve vurgulanan koda göre belirtilen kesme noktasını oluşturduğunuz yeri askıya alır. Vurgulanan kod henüz yürütülmedi.

   ![Kesme noktasına vurarak ekran görüntüsü](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Artık uygulama askıya alındığında uygulamanızın durumunu inceleyebilirsiniz.

## <a name="debug-view-variables"></a>Hata Ayıkla: değişkenleri görüntüle

1. Vurgulanan kodda, ve gibi değişkenlerin üzerine gelin `cleanNum1` `op` . Bu değişkenlerin geçerli değerleri `8` ve `d` sırasıyla, veri ipuçlarında görünür.

   ![Bir DataTip görüntülemeyi gösteren ekran görüntüsü.](media/vs-2019/calculator-2-debug-view-datatip.png)

   Hata ayıklarken, değişkenlerin beklenen değerleri içerip içermediğini görmek için genellikle sorunları düzeltmek için kritik öneme sahip olup olmadığını kontrol edin.

2. Alt bölmede **Yereller** penceresine bakın. kapatılmışsa, açmak için **hata ayıkla**  >  **Windows**  >  **yereller** ' i seçin.

   **Yereller** penceresi, şu anda kapsamda olan her bir değişkeni, değeri ve türü ile birlikte gösterir.

   ::: moniker range="vs-2019"
   ![Yereller penceresinin ekran görüntüsü.](media/vs-2019/calculator-2-debug-locals-window.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Yereller penceresinin ekran görüntüsü.](media/vs-2022/calculator-debug-locals-window.png)
   ::: moniker-end

3. **Oto** penceresine bakın.

   Bu pencere, **Yereller** penceresi ile benzerdir, ancak uygulamanın duraklatıldığı geçerli kod satırını takip eden ve hemen önceki değişkenleri gösterir.

Daha sonra, hata ayıklayıcı tek bir deyimindeki kodu, *Adımlama* olarak adlandırılan bir kez yürütün.

## <a name="debug-step-through-code"></a>Hata Ayıkla: kod içinde adımla

1. **F11** tuşuna basın veya **hata ayıklama**  >  **adımı**' nı seçin.

   Step Into komutunu kullanarak, uygulama geçerli ifadeyi yürütür ve genellikle sonraki kod satırında bir sonraki yürütülebilir ifadeye ilerler. Sol taraftaki sarı işaretçi her zaman geçerli ifadeyi gösterir.

   ![Adımın komut ekran görüntüsü](media/vs-2019/calculator-2-debug-step-into.png)

   Yalnızca sınıfındaki yöntemine bir adım daha eklemiş olursunuz `DoOperation` `Calculator` .

1. Program akışınız hakkında hiyerarşik bir görünüm almak için **çağrı yığını** penceresine bakın. kapalıysa, açmak için **hata ayıkla**  >  **Windows**  >  **çağrı yığını** ' nı seçin.

   ![Çağrı yığınının ekran görüntüsü](media/vs-2019/calculator-2-debug-call-stack.png)

   Bu görünüm `Calculator.DoOperation` , sarı işaretçiyle belirtilen geçerli yöntemi gösterir. İkinci satır, `Main` *program. cs* dosyasındaki yönteminden yöntemini çağıran işlevi gösterir.
   
   Çağrı yığını penceresi, yöntemlerin ve işlevlerin hangi sırada **çağrılacağını** gösterir. Bu pencere Ayrıca, kısayol menüsünden **kaynak koda git** gibi birçok hata ayıklayıcı özelliğine erişim sağlar.

1. Uygulama deyimde duraklayana kadar, **F10** tuşuna basın veya **hata ayıklama**  >  **adımından** daha fazla kez ' yi seçin `switch` .

   ```csharp
   switch (op)
   {
   ```

   Step Over komutu, geçerli ifade bir işlev çağırırsa, hata ayıklayıcı işlev içinde kodu çalıştırırsa ve işlevin dönüşene kadar yürütmeyi askıya almamasının dışında adımla komutuna benzerdir. Belirli bir işlevle ilgilenmiyorsanız, üzerine adımla adımlıdan daha hızlıdır.

1. Uygulamanın aşağıdaki kod satırında duraklaması için **F10** bir kez daha tuşuna basın.

   ```csharp
   if (num2 != 0)
   {
   ```

   Bu kod, sıfıra bölme durumunu denetler. Uygulama devam ederse, genel bir özel durum (hata) oluşturur, ancak konsoldaki gerçek döndürülen değeri görüntüleme gibi başka bir şey de denemek isteyebilirsiniz. Bir seçenek, kodda değişiklik yapmak ve sonra hata ayıklamaya devam etmek için *Düzenle ve devam et* adlı bir hata ayıklayıcı özelliği kullanmaktır. Ancak, yürütme akışını geçici olarak değiştirmek için farklı bir püf noktası vardır.

## <a name="debug-test-a-temporary-change"></a>Hata Ayıkla: geçici bir değişikliği test etme

1. Şu anda deyimde duraklatılmış olan sarı işaretçiyi seçin `if (num2 != 0)` ve aşağıdaki ifadeye sürükleyin:

   ```csharp
   result = num1 / num2;
   ```

   İşaretçinin buraya sürüklenmesi, uygulamanın deyimin tamamen atlanmasına neden olur `if` , böylece sıfıra bölene olacağını görebilirsiniz.

1. Kod satırını yürütmek için **F10** tuşuna basın.

1. Değişkenin üzerine geldiğinizde `result` , **sonsuz** değerini gösterir. C# ' de, sıfıra böleceği zaman sonsuzluk sonuç olur.

1. **F5** tuşuna basın veya **hata**  >  **ayıklamayı devam** Ayıkla ' yı seçin.

   Sonsuzluk sembolü, matematik işleminin sonucu olarak konsolunda görünür.

1. *N* komutunu girerek uygulamayı düzgün bir şekilde kapatın.

## <a name="code-complete"></a>Kod Tamam

Tüm adımları tamamladıktan sonra, *Hesaplamakitaplığı. cs* dosyasının tüm kodu aşağıda verilmiştir:

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

*Program. cs* kodu aşağıda verilmiştir: 

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

Tebrikler, bu öğreticiyi tamamlama! Daha fazla bilgi edinmek için aşağıdaki içerikle devam edin:

- [Daha fazla C# öğreticisi ile devam edin.](/dotnet/csharp/tutorials/)
- [Hızlı Başlangıç: Web ASP.NET Core oluşturma.](../../ide/quickstart-aspnet-core.md)
- [içinde C# kodunda hata ayıklamayı Visual Studio.](tutorial-debugger.md)
- [Birim testlerini oluşturma ve çalıştırma adımlarını adım adım takip etmek.](../../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Bir C# programı çalıştırın.](run-program.md)
- [C# IntelliSense hakkında bilgi edinebilirsiniz.](../../ide/visual-csharp-intellisense.md)
- [IDE'ye Visual Studio devam eder.](visual-studio-ide.md)
