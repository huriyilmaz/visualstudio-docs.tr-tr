---
title: 'Öğretici: basit bir C# konsol uygulamasını genişletme'
description: Visual Studio 'da C# konsol uygulaması geliştirmeyi adım adım öğrenin.
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fd0d2b3e112a4bf08481fa8f043f70121d827010
ms.sourcegitcommit: cea9e5787ff33e0e18aa1942bf4236748e0ef547
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197484"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Öğretici: basit bir C# konsol uygulamasını genişletme

Bu öğreticide, Visual Studio 'Yu kullanarak ilk bölümde oluşturduğunuz konsol uygulamasını nasıl genişletebileceğinizi öğreneceksiniz. Visual Studio 'da birden fazla projeyi yönetme ve üçüncü taraf paketlerine başvurma gibi günlük geliştirme için ihtiyacınız olan özelliklerden bazılarını öğreneceksiniz.

Bu serinin [ilk bölümünü](tutorial-console.md) henüz tamamladıysanız, hesap makinesi konsol uygulamasına zaten sahipsiniz demektir.  1. bölüm atlamak için, projeyi bir GitHub deposundan açarak başlayabilirsiniz. C# Hesaplayıcı uygulaması [vs-öğreticisi-Samples](https://github.com/MicrosoftDocs/vs-tutorial-samples)deposunda bulunur, bu nedenle yalnızca [öğreticideki bir projeyi açmak Için bir depoyu açın:](../tutorial-open-project-from-repo.md)

## <a name="add-a-new-project"></a>Yeni Proje Ekle

Gerçek dünyada kod, bir çözümde birlikte çalışan çok sayıda proje içerir. Şimdi, hesaplayıcı uygulamasına başka bir proje ekleyelim. Bu, bazı Hesaplayıcı işlevlerini sağlayan bir sınıf kitaplığı olacaktır.

1. Visual Studio 'da yeni proje eklemek için en üst düzey menü komut **dosyasını**  >  **Add**  >  **Yeni proje** Ekle ' yi kullanabilirsiniz, ancak aynı proje adına ("proje düğümü" olarak adlandırılır) sağ tıklayıp projenin kısayol menüsünü (veya bağlam menüsünü) açabilirsiniz. Bu kısayol menüsü, projelerinize işlevsellik eklemenin birçok yolunu içerir. Bu nedenle, **Çözüm Gezgini**' de proje düğümüne sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.

1. C# proje şablonu **sınıf kitaplığını (.NET Standard)** seçin.

   ![Sınıf kitaplığı proje şablonu seçiminin ekran görüntüsü](media/vs-2019/calculator2-add-project-dark.png)

1. Proje adı **Hesaplakitaplığı**' nı yazıp **Oluştur**' u seçin. Visual Studio yeni projeyi oluşturur ve çözüme ekler.

   ![Hesaplatorlibrary sınıf kitaplığı projesi eklenen Çözüm Gezgini ekran görüntüsü](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. *Class1.cs*yerine **CalculatorLibrary.cs**dosyasını yeniden adlandırın. Yeniden adlandırmak için **Çözüm Gezgini** adına tıklayabilir veya sağ tıklayıp **Yeniden Adlandır**' ı seçebilir veya **F2** tuşuna basabilirsiniz.

   Dosyadaki tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulur `Class1` . Daha sonraki bir adımda kodu değiştirdiğinizden, yanıt sizin için önemlidir.

1. Şimdi, ilk projenin yeni sınıf kitaplığı tarafından kullanıma sunulan API 'Leri kullanabilmesi için bir proje başvurusu eklememiz gerekir.  İlk projedeki **Başvurular** düğümüne sağ tıklayın ve **proje başvurusu Ekle**' yi seçin.

   ![Proje başvurusu Ekle menü öğesinin ekran görüntüsü](media/vs-2019/calculator2-add-project-reference-dark.png)

   **Başvuru Yöneticisi** iletişim kutusu görüntülenir. Bu iletişim kutusu, diğer projelere başvurular eklemenizi sağlar, Ayrıca, projelerinize gereken derlemeleri ve COM DLL 'Leri.

   ![Başvuru Yöneticisi iletişim kutusunun ekran görüntüsü](media/vs-2019/calculator2-ref-manager-dark.png)

1. **Başvuru Yöneticisi** iletişim kutusunda, **Hesaplayıt kitaplığı** projesinin onay kutusunu seçin ve **Tamam**' ı seçin.  Proje başvurusu **Çözüm Gezgini**Içindeki bir **Projeler** düğümü altında görüntülenir.

   ![Proje başvurusuyla Çözüm Gezgini ekran görüntüsü](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. *Program.cs*içinde, `Calculator` sınıfı ve tüm kodunu seçin ve **CTRL + X** tuşlarına basarak program.cs öğesinden kesin. Ardından, *CalculatorLibrary.cs*' de **hesaplamadı**' da kodu `CalculatorLibrary` ad alanına yapıştırın. Daha sonra, hesaplayıcı sınıfını `public` kitaplığın dışına çıkarmak için oluşturun. *CalculatorLibrary.cs* içindeki kod artık aşağıdaki koda benzemelidir:

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

1. İlk projenin bir başvurusu var, ancak Hesaplayıcı. DoOperation çağrısının çözümlenmediğini belirten bir hata görürsünüz. Bunun nedeni, Hesaplagönderenin bir fark ad alanında olması, bu nedenle `CalculatorLibrary` tam nitelikli bir başvuru için ad alanı eklemektir.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Bunun yerine, dosyanın başlangıcına bir using yönergesi eklemeyi deneyin:

   ```csharp
   using CalculatorLibrary;
   ```

   Bu değişiklik, hesap kaldırma adı ' nı çağrı sitesinden kaldırmanızı sağlar, ancak artık bir belirsizlik var. , `Calculator` Hesaplayıcı 'daki sınıftır veya ad alanı Hesaplayıcısı mi?  Belirsizliği çözümlemek için ad alanını yeniden adlandırın `CalculatorProgram` .

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Başvuru .NET kitaplıkları: bir günlüğe yazma

1. Artık tüm işlemlerin bir günlüğünü eklemek ve bir metin dosyasına yazmak istediğinizi varsayalım. .NET `Trace` sınıfı bu işlevselliği sağlar. (Temel yazdırma hata ayıklama teknikleri de yararlı olur.)  Trace sınıfı System. Diagnostics içinde bulunur ve gibi System.IO sınıfların olması gerekir `StreamWriter` , bu nedenle using yönergelerini ekleyerek başlayın:

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Trace sınıfının nasıl kullanıldığına bakarak, bir FILESTREAM ile ilişkili olan sınıfı için bir başvuruya sahip olmanız gerekir. Yani, hesaplayıcı bir nesne olarak daha iyi çalışır, bu nedenle bir Oluşturucu ekleyelim.

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

1. Statik `DoOperation` yöntemi bir üye yöntemi olarak değiştirmemiz gerekiyor.  Ayrıca günlük için her bir hesaplamaya çıktı ekleyelim, böylece DoOperation aşağıdaki koda benzer şekilde görünür:

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

1. Artık Program.cs 'e geri döndüğünüzde, statik çağrı kırmızı dalgalı bir metinle işaretlenir. Bunu onarmak için `calculator` while döngüsünden hemen önce aşağıdaki satırı ekleyerek bir değişken oluşturun:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Ve çağrı sitesini `DoOperation` aşağıdaki gibi değiştirin:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Programı yeniden çalıştırın ve işiniz bittiğinde proje düğümüne sağ tıklayın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin ve ardından Dosya Gezgini ' nde çıkış klasörüne gidin. *Bin/Debug/netcoreapp 3.1*olabilir ve *Hesaplayıcı. log* dosyasını açabilirsiniz.

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>NuGet paketi ekleme: JSON dosyasına yazma

1. Artık, nesne verilerini depolamak için popüler ve taşınabilir bir biçimdeki işlemleri bir JSON biçiminde çıkarmak istediğinizi varsayalım. Bu işlevselliği uygulamak için, üzerinde Newtonsoft.JsNuGet paketine başvuracağız. NuGet paketleri .NET sınıf kitaplıklarının dağıtılması için birincil araçtır. **Çözüm Gezgini**, hesap \ yönetim projesi için **Başvurular** düğümüne sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.

   ![Kısayol menüsünde NuGet paketlerinin yönetilmesi ekran görüntüsü](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   NuGet Paket Yöneticisi açılır.

   ![NuGet Paket Yöneticisi ekran görüntüsü](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Pakette Newtonsoft.Jsaraması yapın ve **yüklemeyi**seçin.

   ![Newtonsoft NuGet paket bilgilerinin ekran görüntüsü](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Paket indirilir ve projenize eklenir ve **Çözüm Gezgini**başvurular düğümünde yeni bir giriş görüntülenir.

1. *CalculatorLibrary.cs*başlangıcında System.IO ve Newtonsoft.Json paketine yönelik bir using yönergesi ekleyin.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Şimdi Hesaplayıcı için oluşturucuyu aşağıdaki kodla değiştirin ve JsonWriter üye nesnesini oluşturun:

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

1. `DoOperation`JSON yazıcı kodunu eklemek için yöntemi değiştirin:

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

1. Kullanıcı işlem verilerini girmeyi tamamladıktan sonra JSON sözdizimini tamamlayacak bir yöntem eklemeniz gerekir.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. *Program.cs*' de, sonunda bitirmek için bir çağrı ekleyin.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Uygulamayı derleyin ve çalıştırın ve birkaç işlem girmeyi tamamladıktan sonra, ' n ' komutunu kullanarak uygulamayı düzgün bir şekilde kapatın.  Şimdi dosyada calculatorlog.jsaçın ve aşağıdakine benzer bir şey görmeniz gerekir:

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

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamlama! Daha da fazla bilgi edinmek için aşağıdaki öğreticilerle devam edin.

> [!div class="nextstepaction"]
> [Daha fazla C# öğreticilerine devam edin](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Visual Studio IDE 'ye genel bakış ile devam edin](/../visual-studio-ide.md)

## <a name="see-also"></a>Ayrıca bkz.

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Visual Studio 'da C# kodunda hata ayıklamayı öğrenin](tutorial-debugger.md)
