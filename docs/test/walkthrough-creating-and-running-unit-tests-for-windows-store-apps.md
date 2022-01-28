---
title: Evrensel Windows Platformu (UWP) uygulamaları için birim testleri oluşturma ve çalıştırma
description: Visual Studio 'de birim testi UWP uygulamaları hakkında bilgi edinin ve bir C# UWP uygulaması oluşturmak ve test etmek için test odaklı geliştirme kullanın.
ms.custom: SEO-VS-2020
ms.date: 01/20/2022
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 60a8e08afd93d633b3492646f6d31a17d088264e
ms.sourcegitcommit: abd19232659447bc9bf946692a5de49130416bad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2022
ms.locfileid: "137831550"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>İzlenecek yol: UWP uygulamaları için birim testleri oluşturma ve çalıştırma

bu makalede, Visual Studio ' de birim testi Evrensel Windows Platformu (UWP) uygulamalarının nasıl yapılacağı açıklanır. Visual Studio, C#, Visual Basic ve C++ için UWP birim testi proje şablonları sunmaktadır. UWP uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [UWP uygulamalarını kullanmaya başlama](/windows/uwp/get-started/).

Makalede bir UWP uygulamasında C# sınıfı oluşturma ve birim testi yapma örneği gösterilmektedir. Örnek, belirli davranışları doğrulayan testleri yazmak için [test odaklı geliştirmeyi](quick-start-test-driven-development-with-test-explorer.md) kullanır ve ardından testleri geçiren kodu yazar.

## <a name="create-and-run-a-unit-test-project"></a>Birim testi projesi oluşturma ve çalıştırma

Aşağıdaki yordamlarda, UWP uygulamaları için birim testi projelerinin nasıl oluşturulduğu ve çalıştırılacağı açıklanır.

### <a name="create-a-uwp-unit-test-project"></a>UWP birim testi projesi oluşturma

::: moniker range=">=vs-2022"

1. Visual Studio **başlat** penceresinde **yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** sayfasında, arama kutusuna *birim testi* girin. Şablon listesi, birim test projelerine filtre uygular.

1. C# veya Visual Basic için **birim testi uygulaması (evrensel Windows)** şablonunu seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="media/vs-2022/new-uwp-unit-test-app.png" alt-text="Visual Studio 'de yeni UWP birim testi uygulaması oluşturmayı gösteren ekran görüntüsü.":::

1. İsteğe bağlı olarak proje veya çözüm adını ve konumunu değiştirip **Oluştur**' u seçin.

1. İsteğe bağlı olarak hedef ve en düşük platform sürümlerini değiştirip **Tamam**' ı seçin.

Visual Studio test projesi oluşturur ve Visual Studio **Çözüm Gezgini** açar.

:::image type="content" source="media/vs-2022/uwp-unit-test-project-solution-explorer.png"  alt-text="Çözüm Gezgini 'de UWP birim testi projesini gösteren ekran görüntüsü.":::

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio **başlat** penceresinde **yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** sayfasında, arama kutusuna *birim testi* girin. Şablon listesi, birim test projelerine filtre uygular.

1. C# veya Visual Basic için **birim testi uygulaması (evrensel Windows)** şablonunu seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="media/vs-2019/new-uwp-unit-test-app.png" alt-text="Visual Studio 'de yeni UWP birim testi uygulaması oluşturmayı gösteren ekran görüntüsü.":::

1. İsteğe bağlı olarak proje veya çözüm adını ve konumunu değiştirip **Oluştur**' u seçin.

1. İsteğe bağlı olarak hedef ve en düşük platform sürümlerini değiştirip **Tamam**' ı seçin.

Visual Studio test projesi oluşturur ve Visual Studio **Çözüm Gezgini** açar.

:::image type="content" source="media/vs-2019/uwp-unit-test-project-solution-explorer.png"  alt-text="Çözüm Gezgini 'de UWP birim testi projesini gösteren ekran görüntüsü.":::

::: moniker-end

::: moniker range="vs-2017"

1. **Dosya** menüsünden **yeni Project**' yi seçin.

   **yeni Project** iletişim kutusu görüntülenir.

2. şablonlar ' ın altında, birim testleri oluşturmak istediğiniz programlama dilini seçin ve ardından ilişkili Windows evrensel birim testi kitaplığı ' nı seçin. örneğin, **Visual C#** ' yi ve ardından **Windows evrensel**' i seçin ve ardından **birim testi kitaplığı (evrensel Windows)** öğesini seçin.

3. Seçim **Ad** metin kutusuna, proje için kullanmak istediğiniz adı girin.

4. Seçim Projeyi, **konum** metin kutusuna girerek oluşturmak istediğiniz yolu değiştirin veya **Araştır** düğmesini seçin.

5. Seçim **Çözüm** adı metin kutusuna çözümünüz için kullanmak istediğiniz adı girin.

6. **Çözüm için dizin oluştur** seçeneğini seçili bırakın ve **Tamam** düğmesini seçin.

   :::image type="content" source="media/unit_test_win8_1.png" alt-text="Özel birim testi kitaplığını gösteren ekran görüntüsü.":::

**Çözüm GEZGINI** UWP birim testi projesi ile doldurulur ve kod Düzenleyicisi UnitTest1 başlıklı varsayılan birim testini görüntüler.

:::image type="content" source="media/unit_test_win8_unittestexplorer_newprojectcreated.png" alt-text="Yeni bir özel birim testi projesi gösteren ekran görüntüsü.":::

::: moniker-end

### <a name="edit-the-projects-application-manifest"></a>Projenin uygulama bildirimini Düzenle

1. **Çözüm Gezgini**, *Package. appxmanifest* dosyasına sağ tıklayın ve **Aç**' ı seçin.

1. Bildirim tasarımcısında **yetenekler** sekmesini seçin.

1. **Yetenekler** listesinde, kod ve birim testi için gereken özellikleri seçin. Örneğin, kodunuzun ve birim testinin internet 'e erişmesi gerekiyorsa **Internet** onay kutusunu seçin.

Yalnızca birim testinin düzgün çalışması için gereken özellikleri seçin.

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/unit-test.png" alt-text="Birim testi bildirimini gösteren ekran görüntüsü.":::

::: moniker-end

::: moniker range="vs-2019"

:::image type="content" source="media/vs-2019/unit-test.png" alt-text="Birim testi bildirimini gösteren ekran görüntüsü.":::

::: moniker-end

::: moniker range="vs-2017"

:::image type="content" source="media/unit-test.png" alt-text="Birim testi bildirimini gösteren ekran görüntüsü.":::

::: moniker-end

### <a name="add-code-to-unit-test-the-uwp-app"></a>UWP uygulamasını birim testine kod ekleme

Visual Studio kod düzenleyicisinde, testlerin gerektirdiği onayları ve mantığı eklemek için birim test kodu dosyasını düzenleyin. Örnekler için, bu makalenin ilerleyen kısımlarında bulunan [birim testi C# sınıfına](#unit-test-a-c-class) bakın.

### <a name="run-the-unit-test-with-test-explorer"></a>Test Gezgini ile birim testini çalıştırma

::: moniker range=">=vs-2022"

Çözümü oluşturun ve **Test Gezgini**'ni kullanarak birim testini çalıştırın.

1. Visual Studio **test** menüsünde **test gezgini**' ni seçin. **Test Gezgini** penceresi açılır.

1. **Test Gezgini** Içinde **Tümünü Çalıştır** simgesini seçin. UWP projelerindeki testleri keşfetmesi için **Tümünü Çalıştır** ' i kullanmanız gerekir.

   :::image type="content" source="media/vs-2022/test-explorer.png" alt-text="Test Gezgini Tümünü Çalıştır simgesini gösteren ekran görüntüsü.":::

Çözüm oluşturulur ve birim testi çalışır. Test çalıştıktan sonra test, test **Gezgini** test listesinde sonuç ve süre hakkında bilgi içeren görüntülenir.

:::image type="content" source="media/vs-2022/test-explorer-run.png" alt-text="Test Gezgini ile tamamlanan test bilgilerini gösteren ekran görüntüsü.":::

Ayrıca, **Test Gezgini**'nde tek tek testleri seçebilir ve Testleri **çalıştırmak** veya **hatalarını ayıklamak** için sağ tıklayın veya test kodunu açmak için test ' e **gidebilirsiniz** . Üstteki menüden testleri gruplandırabilir, listelerine testler ekleyebilir veya test seçeneklerini açabilirsiniz.

:::image type="content" source="media/vs-2022/test-explorer-done.png" alt-text="Test Gezgini bağlam menüsünü gösteren ekran görüntüsü.":::

::: moniker-end

::: moniker range="vs-2019"

Çözümü oluşturun ve **Test Gezgini**'ni kullanarak birim testini çalıştırın. 

1. Visual Studio **test** menüsünde **test gezgini**' ni seçin. **Test Gezgini** penceresi açılır.

1. **Test Gezgini** Içinde **Tümünü Çalıştır** simgesini seçin. UWP projelerindeki testleri keşfetmesi için **Tümünü Çalıştır** ' i kullanmanız gerekir.

   :::image type="content" source="media/vs-2019/test-explorer.png" alt-text="Test Gezgini Tümünü Çalıştır simgesini gösteren ekran görüntüsü.":::

Çözüm oluşturulur ve birim testi çalışır. Test çalıştıktan sonra test, test **Gezgini** test listesinde sonuç ve süre hakkında bilgi içeren görüntülenir.

:::image type="content" source="media/vs-2019/test-explorer-run.png" alt-text="Test Gezgini ile tamamlanan test bilgilerini gösteren ekran görüntüsü.":::

Ayrıca, **Test Gezgini**'nde tek tek testleri seçebilir ve Testleri **çalıştırmak** veya **hatalarını ayıklamak** için sağ tıklayın veya test kodunu açmak için test ' e **gidebilirsiniz** . Üstteki menüden testleri gruplandırabilir, listelerine testler ekleyebilir veya test **seçeneklerini** açabilirsiniz.

:::image type="content" source="media/vs-2019/test-explorer-done.png" alt-text="Test Gezgini bağlam menüsünü gösteren ekran görüntüsü.":::

::: moniker-end

::: moniker range="vs-2017"

Çözümü oluşturmak ve test Gezgini 'ni kullanarak birim testini çalıştırmak için:

1. Visual Studio **test** menüsünde **Windows**' i seçin ve ardından **Test gezgini**' ni seçin. **Test Gezgini** penceresi açılır.

1. **Build** menüsünde **Build Solution** öğesini seçin.  Birim testiniz artık **Test Gezgini**'nde gösteriliyor.

   > [!NOTE]
   > **Test Gezgini**'nde birim testlerinin listesini güncelleştirmek için çözümü derlemeniz gerekir.

1. **Test Gezgini**' nde, oluşturduğunuz birim testini seçin ve **Tümünü Çalıştır**' ı seçin.

   :::image type="content" source="media/unit-test-run.png" alt-text="Test Gezgini Tümünü Çalıştır komutunu gösteren ekran görüntüsü.":::

Çözüm oluşturulur ve birim testi çalışır. Test çalıştıktan sonra test, test **Gezgini** test listesinde sonuç ve süre hakkında bilgi içeren görüntülenir.

:::image type="content" source="media/unit-test-done.png" alt-text="Test Gezgini ile tamamlanan test bilgilerini gösteren ekran görüntüsü.":::

> [!TIP]
> Test Gezgini 'nde listelenen bir veya daha fazla birim testi seçebilir ve sağ tıklayıp **Seçili Testleri Çalıştır**' ı seçebilirsiniz.
>
> Ayrıca, **Seçili testlerin hatalarını ayıklamayı**, **testi açmayı** ve **Özellikler** seçeneğini kullanmayı da seçebilirsiniz.
>
> :::image type="content" source="media/unit-test-context-menu.png" alt-text="Test Gezgini bağlam menüsünü gösteren ekran görüntüsü.":::

::: moniker-end

## <a name="unit-test-a-c-class"></a>C# sınıfı birim testi

Kalıcı bir iyi birim testleri kümesi, kodu değiştirirken hata sunmadığınız güvenceyi artırır. Aşağıdaki örnek, UWP uygulamasında bir C# sınıfı için birim testleri oluşturmanın bir yolunu gösterir. Örnek, belirli davranışı doğrulayan testleri yazmak için *test odaklı geliştirmeyi* kullanır ve ardından testleri geçiren kodu yazar.

Örnek **Maaltı** kod projesinde, **Rooter** sınıfı bir sayının tahmini kare kökünü hesaplayan bir işlev uygular. **RooterTests** proje birimi **Rooter** sınıfını sınar.

### <a name="create-the-solution-and-projects"></a>Çözüm ve projeleri oluşturma

UWP uygulama projesini oluşturun:

1. Visual Studio **dosya** menüsünde **yeni Project**' yi seçin.
1. **yeni proje oluştur** sayfasında, arama kutusuna *boş uygulama* girin ve ardından C# **boş uygulama (evrensel Windows)** proje şablonunu seçin.
1. **Yeni projenizi yapılandırın** sayfasında, projeyi *maaltı* olarak adlandırın ve **Oluştur**' u seçin.
1. İsteğe bağlı olarak hedef ve en düşük platform sürümlerini değiştirip **Tamam**' ı seçin. Visual Studio projeyi oluşturur ve **Çözüm Gezgini** açar.

Birim testi projesi oluşturun:

1. **Çözüm Gezgini**, **maaltı** çözüme sağ tıklayın ve   >  **yeni Project** ekle ' yi seçin.
1. **yeni proje ekle** sayfasında, arama kutusuna *birim testi* girin ve ardından C# **birim testi uygulaması (evrensel Windows)** proje şablonunu seçin.
1. Test projesi kökü \ *tertest* adını adlandırın ve **Oluştur**' u seçin.
1. İsteğe bağlı olarak hedef ve en düşük platform sürümlerini değiştirip **Tamam**' ı seçin. **RooterTests** projesi **Çözüm Gezgini** içindeki **maaltı** çözüm altında görünür.

### <a name="verify-that-tests-run-in-test-explorer"></a>Test Gezgini 'nde testlerin çalıştırıldığını doğrulama

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>Sınıfı, test yöntemlerinde sonuçları doğrulamak için kullanabileceğiniz çeşitli statik yöntemler sağlar.

::: moniker range=">=vs-2019"

1. **Çözüm Gezgini** altında, **RooterTests** projesindeki *UnitTest. cs* dosyasını seçin.

1. Aşağıdaki kodu içine ekleyin `TestMethod1` :

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

1. **Test Gezgini**'Nde **Tüm Testleri Çalıştır**' ı seçin.

1. Test projesi oluşturulup çalışır ve test **geçen testlerin** altında görünür. Sağdaki **Grup Özeti** bölmesi, test hakkındaki ayrıntıları sağlar.

::: moniker-end

::: moniker range="vs-2017"


1. **Çözüm Gezgini** altında, **RooterTests** projesindeki *UnitTest. cs* dosyasını seçin.

1. Aşağıdaki kodu içine ekleyin `TestMethod1` :

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

1. **Test** menüsünde  > **tüm testleri** Çalıştır ' ı seçin.

Test projesi oluşturulup çalışır. **Test Gezgini** penceresi görünür ve test **geçilen testler** altında görünür. Pencerenin alt kısmındaki Özet bölmesi, seçilen test hakkında daha fazla ayrıntı sağlar.


::: moniker-end

### <a name="add-a-class-to-the-app-project"></a>Uygulama projesine bir sınıf ekleyin

::: moniker range=">=vs-2022"

1. **Çözüm Gezgini**, **maaltı** projeye sağ tıklayın ve sınıf **Ekle** ' yi seçin > .

1. Sınıf dosyasını *Rooter. cs* olarak adlandırın ve **Ekle**' yi seçin.

1. Kod Düzenleyicisi 'nde, `Rooter` *Rooter. cs* dosyasındaki sınıfına aşağıdaki kodu ekleyin:

   ```csharp
   public Rooter()
   {
   }
   
   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   `Rooter`Sınıfı bir Oluşturucu ve `SquareRoot` tahmin aracı metodunu bildirir. `SquareRoot`Yöntemi temel test kurulumunu test etmek için en az bir uygulama.

1. `internal`Anahtar sözcüğünü `public` sınıf bildiriminde olarak değiştirin `Rooter` , böylece test kodu buna erişebilir.

   ```csharp
   public class Rooter
   ```
::: moniker-end

::: moniker range="<=vs-2019"

1. **Çözüm Gezgini**, **maaltı** projeye sağ tıklayın ve sınıf **Ekle** ' yi seçin > .

1. Sınıf dosyasını *Rooter. cs* olarak adlandırın ve **Ekle**' yi seçin.

1. Kod Düzenleyicisi 'nde, `Rooter` *Rooter. cs* dosyasındaki sınıfına aşağıdaki kodu ekleyin:

   ```csharp
   public Rooter()
   {
   }
   
   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   `Rooter`Sınıfı bir Oluşturucu ve `SquareRoot` tahmin aracı metodunu bildirir. `SquareRoot`Yöntemi temel test kurulumunu test etmek için en az bir uygulama.

1. `public`Anahtar sözcüğünü `Rooter` sınıf bildirimine ekleyin, böylece test kodu buna erişebilir.

   ```csharp
   public class Rooter
   ```
::: moniker-end

### <a name="add-a-reference-from-the-test-project-to-the-app-project"></a>Test projesinden uygulama projesine bir başvuru ekleyin

::: moniker range=">=vs-2022"

1. **Çözüm Gezgini**, **RooterTests** projesine sağ tıklayın ve başvuru Ekle ' yi seçin  > .

1. **Başvuru Yöneticisi-RooterTests** Iletişim kutusunda **Projeler**' i genişletin ve **maaltı** projeyi seçin.

   :::image type="content" source="media/vs-2022/add-reference.png" alt-text="Maaltı projeye başvuru eklemeyi gösteren ekran görüntüsü.":::

1. **Tamam**’ı seçin.

1. Aşağıdaki `using` Ifadeyi *UnitTest. cs* öğesine ekleyin, `using Microsoft.VisualStudio.TestTools.UnitTesting;` satır sonra:

   ```csharp
   using Maths;
   ```
::: moniker-end

::: moniker range="vs-2019"

1. **Çözüm Gezgini**, **RooterTests** projesine sağ tıklayın ve başvuru Ekle ' yi seçin  > .

1. **Başvuru Yöneticisi-RooterTests** Iletişim kutusunda **Projeler**' i genişletin ve **maaltı** projeyi seçin.

   :::image type="content" source="media/ute_cs_windows_addreference.png" alt-text="Maaltı projeye başvuru eklemeyi gösteren ekran görüntüsü.":::

1. **Tamam**’ı seçin.

1. Aşağıdaki `using` Ifadeyi *UnitTest. cs* öğesine ekleyin, `using Microsoft.VisualStudio.TestTools.UnitTesting;` satır sonra:

   ```csharp
   using Maths;
   ```
::: moniker-end

::: moniker range="vs-2017"


1. **Çözüm Gezgini**, **RooterTests** projesine sağ tıklayın ve başvuru Ekle ' yi seçin  > .

1. **Başvuru Yöneticisi-RooterTests** Iletişim kutusunda **Projeler**' i genişletin ve **maaltı** projeyi seçin.

   :::image type="content" source="media/add-reference.png" alt-text="Maaltı projeye başvuru eklemeyi gösteren ekran görüntüsü.":::

1. **Tamam**’ı seçin.

1. Aşağıdaki `using` Ifadeyi *UnitTest. cs* öğesine ekleyin, `using Microsoft.VisualStudio.TestTools.UnitTesting;` satır sonra:

   ```csharp
   using Maths;
   ```
::: moniker-end

### <a name="add-a-test-that-uses-the-app-function"></a>Uygulama işlevini kullanan bir test ekleyin

1. Aşağıdaki test yöntemini *UnitTest. cs* öğesine ekleyin:

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

   Yeni test, **Çözüm Gezgini** ve **Test Gezgini**'nin **çalıştırma testleri** düğümünde görünür.

1. "Yükün aynı hedef yolu ile iki veya daha fazla dosya içermesi" hatasını önlemek için, **Çözüm Gezgini**' de, **masekiz** projenin altındaki **Özellikler** düğümünü genişletin ve *Default.rd.xml* dosyasını silin.

1. Tüm dosyaları kaydedin.

### <a name="run-the-tests"></a>Testleri çalıştırma

::: moniker range=">=vs-2022"

**Test Gezgini**'Nde **Tüm Testleri Çalıştır** simgesini seçin. Çözüm oluşturulur ve testler çalışır ve geçer.

:::image type="content" source="media/vs-2022/test-explorer-uwp-app.png" alt-text="Test Gezgini 'nde geçilen temel testi gösteren ekran görüntüsü":::


::: moniker-end

::: moniker range="vs-2019"

**Test Gezgini**'Nde **Tüm Testleri Çalıştır** simgesini seçin. Çözüm oluşturulur ve testler çalışır ve geçer.

:::image type="content" source="media/vs-2019/test-explorer-uwp-app.png" alt-text="Test Gezgini 'nde geçilen temel testi gösteren ekran görüntüsü":::


::: moniker-end

::: moniker range="vs-2017"

**Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin. Çözüm oluşturulur ve testler çalışır ve geçer.

:::image type="content" source="media/ute_cpp_testexplorer_basictest.png" alt-text="Test Gezgini 'nde bir BasicTest geçildi gösteren ekran görüntüsü":::


::: moniker-end

Test ve uygulama projelerini ayarlamış ve uygulama projesindeki işlevleri çağıran testleri çalıştıracağınızı doğruladınız. Artık gerçek testleri ve kodu yazabilirsiniz.

### <a name="add-tests-and-make-them-pass"></a>Testler ekleyin ve geçiş yapın

Geçilen testleri değiştirmemelidir. Bunun yerine yeni testler ekleyin. Her seferinde bir test ekleyerek kod geliştirin ve tüm testlerin Her yinelemeden sonra geçmesini sağlayın.

::: moniker range=">=vs-2022"

1. `RangeTest` *UnitTest. cs* öğesine çağrılan yeni bir test ekleyin:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

1. **Rangetest** testini çalıştırın ve başarısız olduğunu doğrulayın.

   :::image type="content" source="media/vs-2022/test-explorer-rangetest-fail.png" alt-text="Test Gezgini 'nde RangeTest başarısız olduğunu gösteren ekran görüntüsü.":::

   > [!TIP]
   > Test tabanlı geliştirmede, bir testi yazdıktan hemen sonra çalıştırırsınız. Bu uygulama, hiçbir şekilde başarısız olmayan bir testi yazmanın kolay bir hata yaşamadan kaçınmanıza yardımcı olur.

1. Yeni testin başarılı olması için uygulama kodunuzu düzeltemedi. *Rooter. cs* dosyasında, `SquareRoot` işlevi aşağıdaki gibi değiştirin:

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

1. **Test Gezgini**'nde **Tüm Testleri Çalıştır** simgesini seçin. Tüm üç test artık geçer.

::: moniker-end

::: moniker range="vs-2019"

1. `RangeTest` *UnitTest. cs* öğesine çağrılan yeni bir test ekleyin:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

1. **Rangetest** testini çalıştırın ve başarısız olduğunu doğrulayın.

   :::image type="content" source="media/vs-2019/test-explorer-rangetest-fail.png" alt-text="Test Gezgini 'nde RangeTest başarısız olduğunu gösteren ekran görüntüsü.":::

   > [!TIP]
   > Test tabanlı geliştirmede, bir testi yazdıktan hemen sonra çalıştırırsınız. Bu uygulama, hiçbir şekilde başarısız olmayan bir testi yazmanın kolay bir hata yaşamadan kaçınmanıza yardımcı olur.

1. Yeni testin başarılı olması için uygulama kodunuzu düzeltemedi. *Rooter. cs* dosyasında, `SquareRoot` işlevi aşağıdaki gibi değiştirin:

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

1. **Test Gezgini**'nde **Tüm Testleri Çalıştır** simgesini seçin. Tüm üç test artık geçer.

::: moniker-end

::: moniker range="vs-2017"

1. `RangeTest` *UnitTest. cs* öğesine çağrılan yeni bir test ekleyin:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

1. **Rangetest** testini çalıştırın ve başarısız olduğunu doğrulayın.

   :::image type="content" source="media/range-test-fail.png" alt-text="Test Gezgini 'nde RangeTest başarısız olduğunu gösteren ekran görüntüsü.":::

   > [!TIP]
   > Test tabanlı geliştirmede, bir testi yazdıktan hemen sonra çalıştırırsınız. Bu uygulama, hiçbir şekilde başarısız olmayan bir testi yazmanın kolay bir hata yaşamadan kaçınmanıza yardımcı olur.

1. Yeni testin başarılı olması için uygulama kodunuzu düzeltemedi. *Rooter. cs* dosyasında, `SquareRoot` işlevi aşağıdaki gibi değiştirin:

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

1. **Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin. Tüm üç test artık geçer.

::: moniker-end

### <a name="refactor-the-code"></a>Kodu yeniden düzenleme

Bu bölümde, hem uygulamayı hem de test kodunu yeniden tasarlayacaktır, ardından yine de başarılı olduklarından emin olmak için testleri yeniden çalıştırın.

#### <a name="simplify-the-square-root-estimation"></a>Kare kök tahmini 'ni basitleştirme

1. *Rooter. cs*' de, `SquareRoot` aşağıdaki satırı değiştirerek işlevde merkezi hesaplamayı kolaylaştırın:

   `estimate = estimate - (estimate * estimate - x) / (2 * estimate);`

   Amaç

   `estimate = (estimate + x/estimate) / 2.0;`

1. Gerileme sunmadığınızdan emin olmak için tüm testleri çalıştırın. Testlerin hepsi başarılı olmalıdır.

#### <a name="remove-duplicate-test-code"></a>Yinelenen test kodunu kaldır

`RangeTest`Yöntemi, `tolerance` yöntemine geçirilen değişkenin paydasını sabit olarak kodlar <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> . Aynı tolerans hesaplamasını kullanan daha fazla test eklemeyi planlıyorsanız, çeşitli konumlarda sabit kodlanmış bir değer kullanmak kodun bakımını zorlaştırır. Bunun yerine, `UnitTest1` tolerans değerini hesaplamak için sınıfa özel bir yardımcı yöntemi ekleyebilirsiniz ve ardından bu yöntemi öğesinden çağırabilirsiniz `RangeTest` .

Yardımcı yöntemini, *UnitTest. cs* içinde eklemek için:

1. `UnitTest1` sınıfına aşağıdaki yöntemi ekleyin:

   ```csharp
   private double ToleranceHelper(double expected)
   {
   return expected / 1000;
   }
   ```

1. İçinde `RangeTest` , aşağıdaki satırı değiştirin:

   `double tolerance = expected/1000;`

   Amaç

   `double tolerance = ToleranceHelper(expected);`

1. Hala başarılı olduğundan emin olmak için **rangetest** testini çalıştırın.

> [!TIP]
> Test sınıfına bir yardımcı yöntemi eklerseniz ve **Test Gezgini**'nde listede bir yardımcı yöntem görünmesini istemiyorsanız, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğini yöntemine eklemeyin.

## <a name="next-steps"></a>Sonraki adımlar

- [Birim testi araçları ve görevleri](../test/unit-test-your-code.md)
- [İzlenecek yol: Yönetilen kod için birim testleri oluşturma ve çalıştırma](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [İzlenecek yol: test Gezginini kullanarak test odaklı geliştirme](quick-start-test-driven-development-with-test-explorer.md)
