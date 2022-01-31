---
title: 'Öğretici: basit bir C# konsol uygulaması oluşturma '
description: Visual Studio, adım adım ' da C# konsol uygulaması oluşturmayı öğrenin.
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
ms.openlocfilehash: a4c20f71b93f3c6a48a2956581487cd48470b248
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137886884"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio-part-1-of-2"></a>öğretici: Visual Studio basit bir C# konsol uygulaması oluşturma (bölüm 1/2)

bu öğreticide, bir C# konsol uygulaması oluşturup çalıştırmak ve Visual Studio tümleşik geliştirme ortamının (ıde) bazı özelliklerini araştırmak için Visual Studio kullanırsınız. Bu öğretici, iki bölümden oluşan bir öğretici serisinin 1. parçasıdır.

Bu öğreticide şunları yaptınız:

> [!div class="checklist"]
> * Visual Studio projesi oluşturun.
> * Bir C# konsol uygulaması oluşturun.
> * Uygulamanızda hata ayıklayın.
> * Uygulamanızı kapatın.
> * Tüm kodunuzu inceleyin.

[2. bölümde](tutorial-console-part-2.md), bu uygulamayı daha fazla proje eklemek, püf noktalarını hata ayıklama ve üçüncü taraf paketlerine başvuru yapmak üzere genişletirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Visual Studio yüklü olmalıdır.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Başlamak için bir C# uygulama projesi oluşturun. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin.
   (Alternatif olarak, **CTRL** + tuşuna basın **SHIFT** + **N**).

3. **yeni Project** iletişim kutusunun sol bölmesinde, **C#**' ı genişletin ve ardından **.net Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından dosya **_Hesaplayıcı_** adını adlandırın.

   ![konsol uygulaması (.net Core) proje şablonunu Visual Studio ıde 'deki yeni Project iletişim kutusunda gösteren ekran görüntüsü.](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

**Konsol uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **.NET Core platformlar arası geliştirme** iş yükünü ekleyerek buna ulaşabilirsiniz. Aşağıdaki adımları uygulayın:

#### <a name="option-1-use-the-new-project-dialog-box"></a>seçenek 1: yeni Project iletişim kutusunu kullanma

1. **yeni Project** iletişim kutusunun sol bölmesindeki **Visual Studio Yükleyicisi aç** bağlantısını seçin.

   ![yeni Project iletişim kutusundan Visual Studio Yükleyicisi aç bağlantısını seçin ' i gösteren ekran görüntüsü.](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

   ![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükünü gösteren ekran görüntüsü.](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. seçenek: Araçlar menü çubuğunu kullanma

1. **yeni Project** iletişim kutusunu iptal edin ve üst menü çubuğundan **araçlar** > **araçlar ve özellikler al**' ı seçin.

1. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio açın ve başlangıç penceresinde **yeni proje oluştur** ' u seçin.

   ![Yeni proje oluştur penceresini gösteren ekran görüntüsü.](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde dil listesinden **C#** ' ı seçin. ardından, proje türleri listesinden Platform listesinden ve **konsolundan** **Windows** ' yi seçin.

   Dili, platformu ve proje türü filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **daha fazla araç ve özellik yükleyebilirsiniz**' i seçin.
   >
   > ![Daha fazla araç ve özellik yüklemesi bağlantısını gösteren ekran görüntüsü.](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > sonra, Visual Studio Yükleyicisi **.net Core platformlar arası geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükünü gösteren ekran görüntüsü.](./media/dot-net-core-xplat-dev-workload.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *hesaplayıcı* yazın veya girin. Ardından **İleri**' yi seçin.

    :::image type="content" source="./media/vs-2019/csharp-name-your-calculator-project.png" alt-text="' Yeni projenizi yapılandırma ' penceresinde projenizin ' Hesaplayıcı ' olarak adlandırmasını gösteren ekran görüntüsü.":::

1. **Ek bilgi** penceresinde **.NET Core 3,1** , hedef çerçeve'niz için zaten seçilmelidir. Aksi takdirde, **.NET Core 3,1**' i seçin. Ardından **Oluştur**' u seçin.

    :::image type="content" source="./media/vs-2019/csharp-target-framework.png" alt-text="' Ek bilgiler ' penceresinde .NET Core 3,1 ' in seçildiğinden emin olan ekran görüntüsü.":::

   Visual Studio, varsayılan "Merhaba Dünya" kodunu içeren yeni projenizi açar.
   Düzenleyicide görüntülemek için, genellikle Visual Studio sağ tarafında olan Çözüm Gezgini penceresinde kod dosyası *program. cs* ' yi seçin.

   Varsayılan "Merhaba Dünya" kodu, "Hello, World!" sabit dizesini göstermek için yöntemini çağırır <xref:System.Console.WriteLine%2A> Konsol penceresinde. F5 tuşuna basarsanız, varsayılan programı hata ayıklama modunda çalıştırabilirsiniz. Uygulama hata ayıklayıcıda çalıştıktan sonra konsol penceresi açık kalır. Konsol penceresini kapatmak için herhangi bir tuşa basın.

::: moniker-end
::: moniker range=">=vs-2022"

1. Visual Studio açın ve başlangıç penceresinde **yeni proje oluştur** ' u seçin.

   ![Yeni proje oluştur penceresini gösteren ekran görüntüsü.](media/vs-2022/create-new-project.png)

1. **Yeni proje oluştur** penceresinde **tüm diller**' i seçin ve ardından açılan listeden **C#** ' ı seçin. **tüm platformlar** listesinden **Windows** seçin ve **tüm proje türleri** listesinden **konsol** ' ı seçin.

   Dili, platformu ve proje türü filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **daha fazla araç ve özellik yükleyebilirsiniz**' i seçin.
   >
   > ![Daha fazla araç ve özellik yüklemesi bağlantısını gösteren ekran görüntüsü.](media/vs-2022/not-finding-what-looking-for.png)
   >
   > Visual Studio Yükleyicisi **.net masaüstü geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.
   >
   > ![Visual Studio Yükleyicisi .net masaüstü geliştirme iş yükünü gösteren ekran görüntüsü.](media/vs-2022/dot-net-development-workload.png)

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *hesaplayıcı* yazın veya girin ve ardından **ileri**' yi seçin.

   ![Yeni projeyi yapılandırma pencerenizde proje hesaplayıcısını adlandırmayı gösteren ekran görüntüsü.](media/vs-2022/csharp-name-your-calculator-project.png)

1. **Ek bilgi** penceresinde, **.net 6,0** hedef çerçeve'niz için zaten seçilmelidir. **Oluştur**’u seçin.

   ![Ek bilgi penceresinde .NET 6,0 seçili olduğunu gösteren ekran görüntüsü.](media/vs-2022/csharp-target-framework.png)

   Visual Studio, varsayılan "Merhaba Dünya" kodunu içeren yeni projenizi açar.

   Düzenleyicide görüntülemek için, genellikle Visual Studio sağ tarafında olan Çözüm Gezgini penceresinde kod dosyası *program. cs* ' yi seçin.

   Tek Code deyimleri, "Hello, World!" sabit dizesini göstermek için yöntemini çağırır <xref:System.Console.WriteLine%2A> Konsol penceresinde. F5 tuşuna basarsanız, varsayılan programı hata ayıklama modunda çalıştırabilirsiniz. Uygulama hata ayıklayıcıda çalıştıktan sonra konsol penceresi açık kalır. Konsol penceresini kapatmak için herhangi bir tuşa basın.
   
   > [!NOTE]
   > .NET 6 ' dan itibaren, konsol şablonunu kullanan yeni projeler önceki sürümlerden farklı bir kod oluşturur. Daha fazla bilgi edinmek için bkz. [Yeni C# şablonları üst düzey deyimler oluşturma](/dotnet/core/tutorials/top-level-templates) sayfası. 

::: moniker-end

## <a name="create-the-app"></a>Uygulama oluşturma

Bu bölümde şunları yapacaksınız:

- C# dilinde bazı temel tamsayı matematiğini gezin.
- Temel bir Hesaplayıcı uygulaması oluşturmak için kod ekleyin.
- Hataları bulmak ve gidermek için uygulamada hata ayıklayın.
- Kodu daha verimli hale getirmek için iyileştirin.

### <a name="explore-integer-math"></a>Tamsayı matematiğini inceleme

C# ' de bazı temel tamsayı matematiği ile başlayın.

::: moniker range="<=vs-2019"
1. Kod Düzenleyicisi 'nde varsayılan "Merhaba Dünya" kodunu silin.

    ![Yeni Hesaplayıcı uygulamanızdan varsayılan Merhaba Dünya kodunu silmeyi gösteren ekran görüntüsü.](./media/csharp-console-calculator-deletehelloworld.png)

   Özellikle, `Console.WriteLine("Hello World!");` belirten satırı silin.

1. Onun yerine, aşağıdaki kodu yazın:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    bunu yaptığınızda, Visual Studio ıntellisense özelliğinin girişi otomatik tamamlama seçeneğini sunduğunu unutmayın.

    > [!NOTE]
    > Aşağıdaki animasyon, önceki kodun yinelenmesine yönelik değildir. Yalnızca otomatik tamamlama özelliğinin nasıl çalıştığını göstermek için tasarlanmıştır.

    ![Visual Studio ıde 'de ıntellisense otomatik tamamlama özelliğini gösteren tamsayı matematik kodu animasyonu.](./media/integer-math-intellisense.gif)

1. Çalışma **Hesaplayıcı** ' ın yanındaki yeşil **Başlat** düğmesini seçerek programınızı derleyip çalıştırın veya **F5** tuşuna basın.

   ![Araç çubuğundan uygulamayı çalıştırmak için hesaplayıcı düğmesini seçmeyi gösteren ekran görüntüsü.](./media/csharp-console-calculator-button.png)

   42 + 119 toplamını gösteren bir konsol penceresi açılır ve bu da **161**.

    ![Tamsayı matematik sonuçlarıyla bir konsol penceresi gösteren ekran görüntüsü.](./media/csharp-console-integer-math.png)

1. **(Isteğe bağlı)** Sonucu değiştirmek için işlecini değiştirebilirsiniz. Örneğin, kod satırındaki işleci `int c = a + b;` çıkarma, `*` çarpma veya `/` bölme için olarak `-` değiştirebilirsiniz `+` . Ardından, programı çalıştırdığınızda, sonuç de değişir.

1. Konsol penceresini kapatın.
::: moniker-end

::: moniker range=">=vs-2022"
1. **Çözüm Gezgini**, sağ bölmede, dosyayı kod düzenleyicisinde göstermek için **program. cs** ' yi seçin

1. Kod Düzenleyicisi 'nde, varsayılan "Merhaba Dünya" kodunun yerine şunu `Console.WriteLine("Hello World!");` koyun.

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

1. İsteğe bağlı olarak, sonucu değiştirmek için işlecini değiştirebilirsiniz. Örneğin, kod satırındaki işleci `int c = a + b;` çıkarma, `*` çarpma veya `/` bölme için olarak `-` değiştirebilirsiniz `+` . Uygulamayı çalıştırdığınızda, sonuç buna göre değişir.

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

1. Visual Studio düzenleyicisinde *program. cs* ' de, **bul ve değiştir** denetimini açmak için **Ctrl** + **H** tuşuna basın.

1. Denetime *int* yazın ve **Replace** alanına *float* yazın.

1. **Eşleştirme durumu** için simgeleri seçin ve denetimdeki **tüm kelimeyi eşleştirin** veya **alt** + **C** ve **alt** + **W** tuşlarına basın.

1. Aramayı çalıştırmak ve değiştirmek için **Tümünü Değiştir** simgesini seçin veya **alt** + **A** 'ya basın.

    ![Bul ve Değiştir denetiminin, int değişkeninin float olarak nasıl değiştirileceğini gösteren animasyon.](media/find-replace-control-animation.gif)

1. Hesaplayıcı uygulamanızı yeniden çalıştırın ve **42** sayısını **119** sayısına bölün.

   Uygulama artık sıfır yerine ondalık sayı döndürüyor.

    ![Artık bir sonuç olarak ondalık sayı döndüren Hesaplayıcı uygulamasını gösteren konsol penceresinin ekran görüntüsü.](media/csharp-console-calculator-decimal.png)

Uygulama artık ondalık sonuçlar üretebilir. Uygulamanın ondalıkları çok fazla hesaplayabilmesi için kodun birkaç tane daha olduğunu daha yapın.

1. Değişkenin her bir `float` örneğini olarak `double` değiştirmek ve yönteminin her bir `Convert.ToInt32` örneğini olarak `Convert.ToDouble` değiştirmek için **Bul ve Değiştir** denetimini kullanın.

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

1. *Program. cs*' de, ve aşağıdaki kodla belirten yorum `// Wait for the user to respond before closing` arasındaki `case "d":` kodu değiştirin:

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

   Kodu değiştirdikten sonra, ifadesiyle olan `switch` bölüm aşağıdaki ekran görüntüsüne benzer şekilde görünmelidir:

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

Tüm kodu işlemek için sınıfa güventense `program` , uygulamanızı iki sınıfa ayırabilirsiniz: `Calculator` ve `Program` .

`Calculator`Sınıfı, hesaplama işinin toplu işini işler ve `Program` sınıfı kullanıcı arabirimini ve hata işleme işini işler.

Haydi başlayalım.

1. *Program. cs*' de, ad alanındaki açılış ve kapanış ayraçları arasındaki her şeyi `Calculator` silin:

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

1. Ayrıca, aşağıdaki gibi yeni  `Program` bir sınıf da ekleyin:

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

   Artık konsol uygulamasını kapatmayı seçinceye kadar daha fazla denklem girebilirsiniz. Sonuçlarda daha az ondalık basamak de vardır. Ayrıca yanlış bir karakter girersiniz, uygun bir hata yanıtı alırsınız.

## <a name="close-the-app"></a>Uygulamayı kapatma

1. Henüz bunu yapmadıysanız Hesap makinesi uygulamasını kapatın.

1. Bölmede **Çıkış** bölmesini Visual Studio.

   ![Giriş bölmesindeki Çıkış bölmesini kapatmayı gösteren Visual Studio.](media/csharp-calculator-close-output-pane.png)

1. Uygulama Visual Studio kaydetmek için **CtrlS**+ tuşlarına basın.

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
