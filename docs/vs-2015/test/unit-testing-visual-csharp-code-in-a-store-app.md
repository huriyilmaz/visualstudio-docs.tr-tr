---
title: Bir mağaza uygulamasında Visual C# kodu için birim testi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 23cb0d82-0451-464e-98ea-fa66e7010ead
caps.latest.revision: 21
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81876493d48407549237ed626fc6ec5d2175fcd7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659600"
---
# <a name="unit-testing-visual-c-code-in-a-store-app"></a>Bir mağaza uygulamasındaki Visual C# kodunu birim testi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, bir Windows Mağazası uygulamasında bir Visual C# sınıfı için birim testleri oluşturmanın bir yolu açıklanmaktadır. Rooter sınıfı, belirli bir sayının kare kökünü tahmini hesaplayan bir işlev uygulayarak, sınır teorisi 'nin depolarından oluşan eru sayısını gösterir. Bu uygulama daha sonra bu işlevi kullanarak bir kullanıcıyı matematik ile yapılabilecek eğlenceli şeyleri gösterir.

 Bu konuda, geliştirme sürecinde ilk adım olarak birim testinin nasıl kullanılacağı gösterilmektedir. Bu yaklaşımda, önce test ettiğiniz sistemde belirli bir davranışı doğrulayan bir test yöntemi yazar ve ardından testi geçiren kodu yazarsınız. Aşağıdaki yordamların sırasıyla değişiklik yaparak, test etmek istediğiniz kodu yazmak ve ardından birim testlerini yazmak için bu stratejiyi ters çevirebilirsiniz.

 Bu konu ayrıca, tek bir Visual Studio çözümü ve test etmek istediğiniz birim testleri ve DLL için ayrı projeler oluşturur. Birim testlerini doğrudan DLL projesine da dahil edebilir veya birim testleri ve DLL için ayrı çözümler oluşturabilirsiniz.

> [!NOTE]
> Visual Studio Community, Enterprise. ve profesyonel birim testi için ek özellikler sağlar.
>
> - Microsoft Test Gezgini için bir eklenti bağdaştırıcısı oluşturmuş olan herhangi bir üçüncü taraf ve açık kaynak birim testi çerçevesini kullanın. Ayrıca testler için kod kapsamı bilgilerini analiz edebilir ve görüntüleyebilirsiniz.
>   - Her derlemeden sonra testlerinizi çalıştırın.
>   - VS Enterprise Ayrıca, sistem ve üçüncü taraf işlevselliği için test kodunu değiştirerek, testlerinizi kendi kodunuzda odaklanmanıza yardımcı olan, yönetilen kod için bir yalıtım çerçevesi olan Microsoft Fakes 'i de içerir.
>
>   Daha fazla bilgi için bkz. MSDN kitaplığındaki [birim testlerini kullanarak kodu doğrulama](https://msdn.microsoft.com/library/dd264975.aspx) .

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda
 [Çözüm ve birim testi projesi oluşturma](#BKMK_Create_the_solution_and_the_unit_test_project)

 [Test Gezgini 'nde testlerin çalıştırıldığını doğrulama](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)

 [Rooter sınıfını Maon projesine ekleyin](#BKMK_Add_the_Rooter_class_to_the_Maths_project)

 [Test projesini uygulama projesine birkaç](#BKMK_Couple_the_test_project_to_the_app_project)

 [Testleri tekrarlayarak ve geçiş yapın](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)

 [Başarısız bir testte hata ayıkla](#BKMK_Debug_a_failing_test)

 [Kodu yeniden düzenleme](#BKMK_Refactor_the_code_)

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Çözüm ve birim testi projesi oluşturma

1. **Dosya** menüsünde **Yeni**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, **yüklü**' ı genişletin, sonra **Visual C#** ' yi genişletin ve **Windows Mağazası**' nı seçin. Ardından proje şablonları listesinden **boş uygulama** ' yı seçin.

3. Projeyi adlandırın `Maths` ve **çözüm Için dizin oluştur** ' un seçili olduğundan emin olun.

4. Çözüm Gezgini, çözüm adını seçin, kısayol menüsünden **Ekle** ' yi seçin ve ardından **Yeni proje**' yi seçin.

5. **Yeni proje** iletişim kutusunda, **yüklü**' ı genişletin, sonra **Visual C#** ' yi genişletin ve **Windows Mağazası** ' nı seçin. Ardından, proje şablonları listesinden **birim testi kitaplığı (Windows Mağazası uygulamaları)** öğesini seçin.

     ![Birim testi projesi oluşturma](../test/media/ute-cs-windows-createunittestproject.png "UTE_Cs_windows_CreateUnitTestProject")

6. Visual Studio Düzenleyicisi 'nde UnitTest1.cs açın.

    ```csharp

    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;
    using Maths;

    namespace RooterTests
    {
        [TestClass]
        public class UnitTest1

            [TestMethod]
            public void TestMethod1()
            {

            }

    ```

     Şunlara dikkat edin:

    1. Her test, kullanılarak tanımlanır `[TestMethod]` . Test metodu void döndürmelidir ve herhangi bir parametreye sahip olamaz.

    2. Test yöntemleri, özniteliğiyle donatılmış bir sınıfta olmalıdır `[TestClass]` .

         Testler çalıştırıldığında, her bir test sınıfının bir örneği oluşturulur. Test yöntemleri belirtilmemiş bir sırada çağırılır.

    3. Her modül, sınıf veya yöntemden önce ve sonra çağrılan özel yöntemler tanımlayabilirsiniz. Daha fazla bilgi için, MSDN Kitaplığı 'ndaki [birim testlerinde Microsoft. VisualStudio. TestTools. UnitTesting üyelerini kullanma](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md) konusuna bakın.

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Test Gezgini 'nde testlerin çalıştırıldığını doğrulama

1. UnitTest1.cs dosyasına bazı test kodu ekleyin `TestMethod1` : **UnitTest1.cs**

    ```csharp

    [TestMethod]
    public void TestMethod1()
    {
        Assert.AreEqual(0, 0);
    }

    ```

     `Assert`Sınıfının, test yöntemlerinde sonuçları doğrulamak için kullanabileceğiniz çeşitli statik yöntemler sağladığını unutmayın.

2. **Test** menüsünde **Çalıştır** ' ı ve ardından **Tümünü Çalıştır**' ı seçin.

     Test projesi oluşturulup çalışır. Test Gezgini penceresi görünür ve test **geçilen testler**altında listelenir. Pencerenin alt kısmındaki Özet bölmesi, seçilen test hakkında ek ayrıntılar sağlar.

     ![Test Gezgini](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")

## <a name="add-the-rooter-class-to-the-maths-project"></a><a name="BKMK_Add_the_Rooter_class_to_the_Maths_project"></a> Rooter sınıfını Maon projesine ekleyin

1. Çözüm Gezgini ' de, **Maaltı** proje adını seçin. Kısayol menüsünde, **Ekle**' yi ve ardından **sınıf**' ı seçin.

2. Sınıf dosyasını adlandırın `Rooter.cs`

3. Aşağıdaki kodu Rooter sınıfı **Rooter.cs** dosyasına ekleyin:

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

     `Rooter`Sınıfı bir Oluşturucu ve `SqareRoot` tahmin aracı metodunu bildirir.

4. `SqareRoot`Yöntemi yalnızca en az bir uygulama, test kurulumunun temel yapısını test etmek için yeterlidir.

## <a name="couple-the-test-project-to-the-app-project"></a><a name="BKMK_Couple_the_test_project_to_the_app_project"></a> Test projesini uygulama projesine birkaç

1. RooterTests projesine, Masekiz uygulamasına bir başvuru ekleyin.

   1. Çözüm Gezgini, **RooterTests** projesini seçin ve kısayol menüsünde **Başvuru Ekle...** öğesini seçin.

   2. **Başvuru Ekle-RooterTests** Iletişim kutusunda **çözüm** ' i genişletin ve **Projeler**' i seçin. Ardından, **Maaltı** öğeyi seçin.

        ![Maaltı projeye başvuru ekleme](../test/media/ute-cs-windows-addreference.png "UTE_Cs_windows_AddReference")

2. UnitTest1.cs dosyasına bir using ifadesini ekleyin:

   1. **UnitTest1.cs**'i açın.

   2. Bu kodu satırın altına ekleyin `using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;` :

       ```csharp
       using Maths;
       ```

3. Rooter işlevini kullanan bir test ekleyin. Aşağıdaki kodu **UnitTest1. cpp**öğesine ekleyin:

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

4. Çözümü derleyin.

    Yeni test, test Gezgini 'nde, **çalıştırma testleri** düğümünde görünür.

5. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

    ![Temel test geçildi](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")

   Test ve kod projelerini ayarlamış ve kod projesindeki işlevleri çalıştıran testleri çalıştıracağınızı doğruladınız. Artık gerçek testleri ve kodu yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Testleri tekrarlayarak ve geçiş yapın

1. Yeni bir test ekleyin:

    ```csharp
    [TestMethod]
    public void RangeTest()
    {
        Rooter rooter = new Rooter();
        for (double v = 1e-6; v < 1e6; v = v * 3.2)
        {
            double expected = v;
            double actual = rooter.SquareRoot(v*v);
            double tolerance = ToleranceHelper(expected);
            Assert.AreEqual(expected, actual, tolerance);
        }
    }

    ```

    > [!TIP]
    > Geçilen testleri değiştirmenizi öneririz. Bunun yerine, yeni bir test ekleyin, kodu test geçişi olacak şekilde güncelleştirin ve daha sonra başka bir test ekleyin ve bu şekilde devam edin.
    >
    >  Kullanıcılarınız gereksinimlerini değiştirmelerine göre artık doğru olmayan Testleri devre dışı bırakın. Yeni testler yazın ve aynı anda bir kez, aynı şekilde çalışır hale getirin.

2. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

3. Test başarısız oluyor.

     ![RangeTest başarısız oluyor](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")

    > [!TIP]
    > Yazdıktan hemen sonra, her testin başarısız olduğunu doğrulayın. Bu, hiç başarısız olmayan bir testi yazmanın kolay bir hata yaşamadan kaçınmanıza yardımcı olur.

4. Yeni testin başarılı olması için test kapsamındaki kodu geliştirin. `SqareRoot` **Rooter.cs** içindeki işlevi şu şekilde değiştirin:

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

5. Çözümü derleyin ve ardından Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

     Tüm üç test artık geçer.

> [!TIP]
> Her seferinde bir test ekleyerek kod geliştirin. Her yinelemeden sonra tüm testlerin başarılı olduğundan emin olun.

## <a name="debug-a-failing-test"></a><a name="BKMK_Debug_a_failing_test"></a> Başarısız bir testte hata ayıkla

1. **UnitTest1.cs**'e başka bir test ekleyin:

   ```csharp
   // Verify that negative inputs throw an exception.
   [TestMethod]
   public void NegativeRangeTest()
   {
       string message;
       Rooter rooter = new Rooter();
       for (double v = -0.1; v > -3.0; v = v - 0.5)
       {
           try
           {
               // Should raise an exception:
               double actual = rooter.SquareRoot(v);

               message = String.Format("No exception for input {0}", v);
               Assert.Fail(message);
           }
           catch (ArgumentOutOfRangeException ex)
           {
               continue; // Correct exception.
           }
           catch (Exception e)
           {
               message = String.Format("Incorrect exception for {0}", v);
               Assert.Fail(message);
           }
       }
   }

   ```

2. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

    Test başarısız oluyor. Test Gezgini 'nde test adını seçin. Başarısız onaylama vurgulanır. Hata iletisi, test Gezgini 'nin ayrıntı bölmesinde görünür.

    ![Negatiftiverangetests başarısız oldu](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")

3. Testin neden başarısız olduğunu görmek için, işlevi adım adım inceleyin:

   1. İşlevin başlangıcında bir kesme noktası ayarlayın `SquareRoot` .

   2. Başarısız testin kısayol menüsünde, **Seçili testlerin hatalarını ayıkla**' yı seçin.

        Çalıştırma kesme noktasında durdurulduğunda kodda adım adım ilerleyin.

   3. Özel durumu yakalamak için Rooter yöntemine kod ekleyin:

       ```csharp
       public double SquareRoot(double x)
       {
           if (x < 0.0)
           {
               throw new ArgumentOutOfRangeException();
       }

       ```

   1. Test Gezgini 'nde, düzeltilen yöntemi sınamak için **Tümünü Çalıştır** ' ı seçin ve bir gerileme sunmadığınızdan emin olun.

   Şimdi tüm testler geçer.

   ![Tüm testler geçer](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")

## <a name="refactor-the-code"></a><a name="BKMK_Refactor_the_code_"></a> Kodu yeniden düzenleme
 **SquareRoot işlevindeki merkezi hesaplamayı kolaylaştırın.**

1. Sonuç uygulamasını değiştirme

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;

    ```

2. Yeniden düzenlenmiş yöntemini test etmek için **Tümünü Çalıştır** ' ı seçin ve bir gerileme sunmadığınızdan emin olun.

> [!TIP]
> Kararlı bir iyi birim testi kümesi, kodu değiştirirken hata sunmaabileceğinizden emin olmanızı sağlar.

 **Yinelenen kodu kaldırmak için test kodunu yeniden düzenleyin.**

 `RangeTest`Yönteminin yönteminde kullanılan tolerans değişkeninin paydasını sabit olarak kodyacağını unutmayın `Assert` . Aynı tolerans hesaplamasını kullanan ek testler eklemeyi planlıyorsanız, sabit kodlanmış değerin birden çok konumda kullanılması hatalara yol açabilir.

1. Tolerans değerini hesaplamak için Unit1Test sınıfına özel bir yöntem ekleyin ve sonra bunun yerine bu yöntemi çağırın.

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // old code
        // double tolerance = expected/1000;
        // new code
        double tolerance = ToleranceHelper(expected);
        Assert.AreEqual(expected, actual, tolerance);
    }
    ...

    ```

2. Yeniden düzenlenmiş yöntemini sınamak için **Tümünü Çalıştır** ' ı seçin ve bir hata sunmadığınızdan emin olun.

> [!NOTE]
> Bir test sınıfına bir yardımcı yöntemi eklemek için, `[TestMethod]` metoduna özniteliği eklemeyin. Test Gezgini çalıştırılacak yöntemi kaydetmez.
