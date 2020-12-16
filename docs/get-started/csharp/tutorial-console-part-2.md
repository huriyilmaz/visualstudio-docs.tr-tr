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
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 55b1e30d214ff85bfc1b7e9c00ebff7e76a95f12
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527884"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Öğretici: basit bir C# konsol uygulamasını genişletme

Bu öğreticide, Visual Studio 'Yu kullanarak ilk bölümde oluşturduğunuz konsol uygulamasını nasıl genişletebileceğinizi öğreneceksiniz. Visual Studio 'da birden fazla projeyi yönetme ve üçüncü taraf paketlerine başvurma gibi günlük geliştirme için ihtiyacınız olan özelliklerden bazılarını öğreneceksiniz.

Bu serinin [ilk bölümünü](tutorial-console.md) henüz tamamladıysanız, hesap makinesi konsol uygulamasına zaten sahipsiniz demektir.  1. bölüm atlamak için, projeyi bir GitHub deposundan açarak başlayabilirsiniz. C# Hesaplayıcı uygulaması [vs-öğreticisi-Samples](https://github.com/MicrosoftDocs/vs-tutorial-samples)deposunda bulunur, bu nedenle yalnızca [öğreticideki bir projeyi açmak Için bir depoyu açın:](../tutorial-open-project-from-repo.md)

## <a name="add-a-new-project"></a>Yeni Proje Ekle

Gerçek dünyada kod, bir çözümde birlikte çalışan çok sayıda proje içerir. Şimdi, hesaplayıcı uygulamasına başka bir proje ekleyelim. Bu, bazı Hesaplayıcı işlevlerini sağlayan bir sınıf kitaplığı olacaktır.

1. Visual Studio 'da yeni proje eklemek için en üst düzey menü komut **dosyasını**  >    >  **Yeni proje** Ekle ' yi kullanabilirsiniz, ancak aynı proje adına ("proje düğümü" olarak adlandırılır) sağ tıklayıp projenin kısayol menüsünü (veya bağlam menüsünü) açabilirsiniz. Bu kısayol menüsü, projelerinize işlevsellik eklemenin birçok yolunu içerir. Bu nedenle, **Çözüm Gezgini**' de proje düğümüne sağ tıklayın ve   >  **Yeni proje** Ekle ' yi seçin.

1. C# proje şablonu **sınıf kitaplığını (.NET Standard)** seçin.

   ![Sınıf kitaplığı proje şablonu seçiminin ekran görüntüsü](media/vs-2019/calculator2-add-project-dark.png)

1. Proje adı **Hesaplakitaplığı**' nı yazıp **Oluştur**' u seçin. Visual Studio yeni projeyi oluşturur ve çözüme ekler.

   ![Hesaplatorlibrary sınıf kitaplığı projesi eklenen Çözüm Gezgini ekran görüntüsü](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. *Class1.cs* yerine **CalculatorLibrary.cs** dosyasını yeniden adlandırın. Yeniden adlandırmak için **Çözüm Gezgini** adına tıklayabilir veya sağ tıklayıp **Yeniden Adlandır**' ı seçebilir veya **F2** tuşuna basabilirsiniz.

   Dosyadaki tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulur `Class1` . Daha sonraki bir adımda kodu değiştirdiğinizden, yanıt sizin için önemlidir.

1. Şimdi, ilk projenin yeni sınıf kitaplığı tarafından kullanıma sunulan API 'Leri kullanabilmesi için bir proje başvurusu eklememiz gerekir.  İlk projedeki **Başvurular** düğümüne sağ tıklayın ve **proje başvurusu Ekle**' yi seçin.

   ![Proje başvurusu Ekle menü öğesinin ekran görüntüsü](media/vs-2019/calculator2-add-project-reference-dark.png)

   **Başvuru Yöneticisi** iletişim kutusu görüntülenir. Bu iletişim kutusu, diğer projelere başvurular eklemenizi sağlar, Ayrıca, projelerinize gereken derlemeleri ve COM DLL 'Leri.

   ![Başvuru Yöneticisi iletişim kutusunun ekran görüntüsü](media/vs-2019/calculator2-ref-manager-dark.png)

1. **Başvuru Yöneticisi** iletişim kutusunda, **Hesaplayıt kitaplığı** projesinin onay kutusunu seçin ve **Tamam**' ı seçin.  Proje başvurusu **Çözüm Gezgini** Içindeki bir **Projeler** düğümü altında görüntülenir.

   ![Proje başvurusuyla Çözüm Gezgini ekran görüntüsü](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. *Program.cs* içinde, `Calculator` sınıfı ve tüm kodunu seçin ve **CTRL + X** tuşlarına basarak program.cs öğesinden kesin. Ardından, *CalculatorLibrary.cs*' de **hesaplamadı**' da kodu `CalculatorLibrary` ad alanına yapıştırın. Daha sonra, hesaplayıcı sınıfını `public` kitaplığın dışına çıkarmak için oluşturun. *CalculatorLibrary.cs* içindeki kod artık aşağıdaki koda benzemelidir:

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

1. Programı yeniden çalıştırın ve işiniz bittiğinde proje düğümüne sağ tıklayın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin ve ardından Dosya Gezgini ' nde çıkış klasörüne gidin. *Bin/Debug/netcoreapp 3.1* olabilir ve *Hesaplayıcı. log* dosyasını açabilirsiniz.

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

1. Pakette Newtonsoft.Jsaraması yapın ve **yüklemeyi** seçin.

   ![Newtonsoft NuGet paket bilgilerinin ekran görüntüsü](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Paket indirilir ve projenize eklenir ve **Çözüm Gezgini** başvurular düğümünde yeni bir giriş görüntülenir.

1. *CalculatorLibrary.cs* başlangıcında System.IO ve Newtonsoft.Json paketine yönelik bir using yönergesi ekleyin.

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

## <a name="debug-set-and-hit-a-breakpoint"></a>Hata Ayıkla: kesme noktası ayarlama ve isabet

Visual Studio hata ayıklayıcı, programlama sırasında hata yaptığınız kesin noktayı bulmak için kodunuzu adım adım çalıştırmanıza olanak tanıyan güçlü bir araçtır. Kodunuzda yapmanız gereken düzeltmeleri anlamış olursunuz. Visual Studio, programı çalıştırmaya devam edebilmeniz için geçici değişiklikler yapmanıza olanak sağlar.

1. *Program.cs*' de, aşağıdaki kodun solundaki kenar boşluğuna tıklayın (veya kısayol menüsünü açın ve **kesme** noktası  >  **Ekle kesme noktası**' nı seçin veya **F9** tuşuna basın):

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Görüntülenen kırmızı daire bir kesme noktasını gösterir. Kesme noktalarını kullanarak uygulamanızı duraklatabilir ve kodu inceleyebilirsiniz. Herhangi bir çalıştırılabilir kod satırında bir kesme noktası ayarlayabilirsiniz.

   ![Kesme noktası ayarlamanın ekran görüntüsü](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Uygulamayı derleyin ve çalıştırın.

1. Çalışan uygulamada, hesaplama için bazı değerler yazın:

   - İlk numara için **8** yazın ve girin.
   - İkinci numara için **0** yazın ve girin.
   - İşleci için biraz eğlenceye sahip olalım. **d** yazın ve girin.

   Uygulama, sol tarafta sarı işaretçiye ve vurgulanan koda göre belirtilen kesme noktasını oluşturduğunuz yeri askıya alır. Vurgulanan kod henüz yürütülmedi.

   ![Kesme noktasına vurarak ekran görüntüsü](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Şimdi, uygulama askıya alındığında uygulamanızın durumunu inceleyebilirsiniz.

## <a name="debug-view-variables"></a>Hata Ayıkla: değişkenleri görüntüle

1. Vurgulanan kodda, ve gibi değişkenlerin üzerine gelin `cleanNum1` `op` . Bu değişkenlerin ( `8` ve `d` sırasıyla) geçerli değerlerini, veri ipuçlarında görünen şekilde görürsünüz.

   ![Veri Ipucunu görüntüleme ekran görüntüsü](media/vs-2019/calculator-2-debug-view-datatip.png)

   Hata ayıklarken, değişkenlerin tutmak istediğiniz değerleri içerip içermediğini görmek için genellikle sorunları çözmek için kritik önem taşır.

2. Alt bölmede **Yereller** penceresine bakın. (Kapalıysa, **Hata Ayıkla**  >  ' yı seçin. **Windows**  >  **Yerelleri açmak Için Yereller** .)

   Yereller penceresinde, şu anda kapsamda olan her bir değişkeni, değeri ve türü ile birlikte görürsünüz.

   ![Yereller penceresinin ekran görüntüsü](media/vs-2019/calculator-2-debug-locals-window.png)

3. **Oto** penceresine bakın.

   Bu pencere, **Yereller** penceresi ile benzerdir, ancak uygulamanızın duraklatıldığı geçerli kod satırını takip eden ve izleyen değişkenleri gösterir.

   Daha sonra, hata ayıklayıcı tek bir ifadede, *Adımlama* olarak adlandırılan kodu yürütecaksınız.

## <a name="debug-step-through-code"></a>Hata Ayıkla: kod içinde adımla

1. **F11** tuşuna basın (veya **hata ayıklama**  >  **adımı**).

   Step Into komutunu kullanarak, uygulama geçerli ifadeyi yürütür ve sonraki yürütülebilir ifadeye (genellikle bir sonraki kod satırına) ilerler. Sol taraftaki sarı işaretçi her zaman geçerli ifadeyi gösterir.

   ![Adımın komut ekran görüntüsü](media/vs-2019/calculator-2-debug-step-into.png)

   Yalnızca sınıfındaki yöntemine bir adım daha gördünüz `DoOperation` `Calculator` .

1. Program akışınız hakkında hiyerarşik bir görünüm almak için **çağrı yığını** penceresine bakın. (Kapalıysa, **Hata Ayıkla**  >  ' yı seçin. **Windows**  >  **Çağrı yığını**.)

   ![Çağrı yığınının ekran görüntüsü](media/vs-2019/calculator-2-debug-call-stack.png)

   Bu görünüm `Calculator.DoOperation` , sarı işaretçi tarafından belirtilen geçerli yöntemi gösterir ve ikinci satır, `Main` *program.cs* içindeki yöntemden, çağıran işlevi gösterir. Çağrı yığını penceresi, yöntemlerin ve işlevlerin hangi sırada **çağrılacağını** gösterir. Ayrıca, kısayol menüsünden **kaynak koda git** gibi birçok hata ayıklayıcı özelliğine erişim sağlar.

1. Uygulama bildirimde duraklayana kadar, **F10** tuşuna basın (veya **hata ayıklama**  >  **adımından** fazla) `switch` .

   ```csharp
   switch (op)
   {
   ```

   Step Over komutu, geçerli deyimin bir işlev çağırması durumunda hata ayıklayıcının kodu çağrılan işlev içinde çalıştırmasını ve işlevin dönüşene kadar yürütmeyi askıya almamasının dışında adımla komutuna benzer. Belirli bir işlevle ilgilenmiyorsanız, yukarıdaki adımla kodda gezinmek daha hızlı bir yoldur.

1. Uygulamanın aşağıdaki kod satırında duraklaması için bir kez **F10** tuşuna basın.

   ```csharp
   if (num2 != 0)
   {
   ```

   Bu kod, sıfıra bölme durumunu denetler. Uygulama devam ederse, genel bir özel durum (hata) oluşturur, ancak bunu bir hata olduğunu düşünsün ve konsolda döndürülen gerçek değeri görüntüleme gibi başka bir şey yapmak istediğinizi varsayalım. Bir seçenek, kodda değişiklik yapmak ve sonra hata ayıklamaya devam etmek için Düzenle ve devam et adlı bir hata ayıklayıcı özelliği kullanmaktır. Bununla birlikte, yürütme akışını geçici olarak değiştirmek için size farklı bir eliz gösterilecektir.

## <a name="debug-test-a-temporary-change"></a>Hata Ayıkla: geçici bir değişikliği test etme

1. Şu anda deyimde duraklatılmış olan sarı işaretçiyi seçin `if (num2 != 0)` ve aşağıdaki ifadeye sürükleyin.

   ```csharp
   result = num1 / num2;
   ```

   Bunu yaptığınızda, uygulama, `if` sıfıra bölme yaparken ne olacağını görmek için, ifadesini tamamen atlar.

1. Kod satırını yürütmek için **F10** tuşuna basın.

1. Değişkenin üzerine gelin `result` ve bir değeri depolayıp depoladığını görürsünüz `Infinity` .

   C# ' de, `Infinity` sıfıra böldüğünüzde sonuç olur.

1. **F5** tuşuna basın (veya hata ayıklama  >  **devam** Ayıkla).

   Sonsuzluk sembolü, matematik işleminin sonucu olarak konsolunda görünür.

1. ' N ' komutunu kullanarak uygulamayı düzgün bir şekilde kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamlama! Daha da fazla bilgi edinmek için aşağıdaki öğreticilerle devam edin.

> [!div class="nextstepaction"]
> [Daha fazla C# öğreticilerine devam edin](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Visual Studio IDE 'ye genel bakış ile devam edin](/../visual-studio-ide.md)

## <a name="see-also"></a>Ayrıca bkz.

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Visual Studio 'da C# kodunda hata ayıklamayı öğrenin](tutorial-debugger.md)
