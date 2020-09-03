---
title: Mağaza uygulamaları için Visual C++ DLL 'i birim testi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 24afc90a-8774-4699-ab01-6602a7e6feb2
caps.latest.revision: 15
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d5f86eb40e1401f98a4c66d0b971fb006762cc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659701"
---
# <a name="unit-testing-a-visual-c-dll-for-store-apps"></a>Mağaza uygulamaları için Visual C++ DLL 'i birim testi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, Windows Mağazası uygulamaları için bir C++ DLL 'SI için birim testleri oluşturmanın bir yolunu açıklar. RooterLib DLL, belirli bir sayının kare kökünü tahmin eden bir işlev uygulayarak, ana bilgisayardan sınır teorisi ercesini gösterir. DLL daha sonra bir Windows Mağazası uygulamasına dahil edilebilir ve bu da Kullanıcı matematik ile yapılabilecek eğlenceli şeyleri gösterir.

 Bu konu, geliştirme aşamasında ilk adım olarak birim testi kullanmayı gösterir. Bu yaklaşımda, önce test ettiğiniz sistemde belirli bir davranışı doğrulayan bir test yöntemi yazar ve ardından testi geçiren kodu yazarsınız. Aşağıdaki yordamların sırasıyla değişiklik yaparak, test etmek istediğiniz kodu yazmak ve ardından birim testlerini yazmak için bu stratejiyi ters çevirebilirsiniz.

 Bu konu ayrıca, tek bir Visual Studio çözümü ve test etmek istediğiniz birim testleri ve DLL için ayrı projeler oluşturur. Birim testlerini doğrudan DLL projesine da dahil edebilir veya birim testleri ve için ayrı çözümler oluşturabilirsiniz. Dosyasını. Hangi yapının kullanılacağı hakkında ipuçları için bkz. [var olan C++ uygulamalarına birim testleri ekleme](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) .

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda
 Bu konu size aşağıdaki görevleri gerçekleştirir:

 [Çözüm ve birim testi projesi oluşturma](#BKMK_Create_the_solution_and_the_unit_test_project)

 [Test Gezgini 'nde testlerin çalıştırıldığını doğrulama](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)

 [Çözüme DLL projesi ekleme](#BKMK_Add_the_DLL_project_to_the_solution)

 [DLL projesine test projesi için birkaç](#BKMK_Couple_the_test_project_to_the_dll_project)

 [Testleri tekrarlayarak ve geçiş yapın](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)

 [Başarısız bir testte hata ayıkla](#BKMK_Debug_a_failing_test)

 [Testleri değiştirmeden kodu yeniden düzenleme](#BKMK_Refactor_the_code_without_changing_tests)

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Çözüm ve birim testi projesi oluşturma

1. **Dosya** menüsünde **Yeni**' yi ve ardından **Yeni proje**' yi seçin.

2. Yeni proje iletişim kutusunda, **yüklü**' ı genişletin ve ardından **Visual C++** ' ı genişletin ve **Windows Mağazası**' nı seçin Ardından, proje şablonları listesinden **birim testi kitaplığı (Windows Mağazası uygulamaları)** öğesini seçin.

     ![C&#43;&#43; birim testi kitaplığı oluşturma](../test/media/ute-cpp-windows-unittestlib-create.png "UTE_Cpp_windows_UnitTestLib_Create")

3. Projeyi adlandırın; `RooterLibTests` konumu belirtin; çözümü adlandırın; `RooterLib` **çözüm için dizin oluştur** ' un işaretli olduğundan emin olun.

     ![Çözüm ve proje adını ve konumunu belirtin](../test/media/ute-cpp-windows-unittestlib-createspecs.png "UTE_Cpp_windows_UnitTestLib_CreateSpecs")

4. Yeni projede, **UnitTest1. cpp**' yi açın.

     ![UnitTest1. cpp](../test/media/ute-cpp-windows-unittest1-cpp.png "UTE_Cpp_windows_unittest1_cpp")

     Şunlara dikkat edin:

    - Her test kullanılarak tanımlanır `TEST_METHOD(YourTestName){...}` .

         Geleneksel bir işlev imzası yazmanız gerekmez. İmza, makro TEST_METHOD tarafından oluşturulur. Makro, void döndüren bir örnek işlevi oluşturur. Ayrıca test yöntemiyle ilgili bilgileri döndüren statik bir işlev oluşturur. Bu bilgiler, test Gezgini 'nin yöntemi bulmasını sağlar.

    - Test yöntemleri kullanılarak sınıflar halinde gruplandırılır `TEST_CLASS(YourClassName){...}` .

         Testler çalıştırıldığında, her bir test sınıfının bir örneği oluşturulur. Test yöntemleri belirtilmemiş bir sırada çağırılır. Her modül, sınıf veya yöntemden önce ve sonra çağrılan özel yöntemler tanımlayabilirsiniz. Daha fazla bilgi için MSDN Kitaplığı 'nda [Microsoft. VisualStudio. TestTools. CppUnitTestFramework kullanma](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md) konusuna bakın.

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Test Gezgini 'nde testlerin çalıştırıldığını doğrulama

1. Bir test kodu ekleyin:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     `Assert`Sınıfının, test yöntemlerinde sonuçları doğrulamak için kullanabileceğiniz çeşitli statik yöntemler sağladığını unutmayın.

2. **Test** menüsünde **Çalıştır** ' ı ve ardından **Tümünü Çalıştır**' ı seçin.

     Test projesi oluşturulup çalışır. Test Gezgini penceresi görünür ve test **geçilen testler**altında listelenir. Pencerenin alt kısmındaki Özet bölmesi, seçilen test hakkında ek ayrıntılar sağlar.

     ![Test Gezgini](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")

## <a name="add-the-dll-project-to-the-solution"></a><a name="BKMK_Add_the_DLL_project_to_the_solution"></a> Çözüme DLL projesi ekleme

1. Çözüm Gezgini, çözüm adını seçin. Kısayol menüsünde **Ekle**' yi ve ardından **Yeni Proje Ekle**' yi seçin.

     ![RooterLib projesi oluşturma](../test/media/ute-cpp-windows-rooterlib-create.png "UTE_Cpp_windows_RooterLib_Create")

2. **Yeni Proje Ekle** iletişim kutusunda, **dll (Windows Mağazası uygulamaları)** öğesini seçin.

3. Aşağıdaki kodu **RooterLib. h** dosyasına ekleyin:

    ```cpp
    // The following ifdef block is the standard way of creating macros which make exporting
    // from a DLL simpler. All files within this DLL are compiled with the ROOTERLIB_EXPORTS
    // symbol defined on the command line. This symbol should not be defined on any project
    // that uses this DLL. This way any other project whose source files include this file see
    // ROOTERLIB_API functions as being imported from a DLL, whereas this DLL sees symbols
    // defined with this macro as being exported.
    #ifdef ROOTERLIB_EXPORTS
    #define ROOTERLIB_API  __declspec(dllexport)
    #else
    #define ROOTERLIB_API __declspec(dllimport)
    #endif //ROOTERLIB_EXPORTS

    class ROOTERLIB_API CRooterLib {
    public:
        CRooterLib(void);
        double SquareRoot(double v);
    };
    ```

     Açıklamalar IDEF bloğunu yalnızca dll geliştiricisi için değil, projesinde DLL 'ye başvuran herkese da açıklamaktadır. DLL 'nin proje özelliklerini kullanarak ROOTERLIB_EXPORTS sembolünü komut satırına ekleyebilirsiniz.

     `CRooterLib`Sınıfı bir Oluşturucu ve `SqareRoot` tahmin aracı metodunu bildirir.

4. ROOTERLIB_EXPORTS sembolünü komut satırına ekleyin.

    1. Çözüm Gezgini, **RooterLib** projesini seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.

         ![Önişlemci sembol tanımı ekleme](../test/media/ute-cpp-windows-addpreprocessorsymbol.png "UTE_Cpp_windows_AddPreprocessorSymbol")

    2. RooterLib Özellik sayfası iletişim kutusunda **yapılandırma özellikleri**' ni genişletin, **C++** ' ı genişletin ve **Önişlemci**' yi seçin.

    3. Ön **\<Edit...>** **işlemci tanımları** listesinden öğesini seçin ve ardından ön `ROOTERLIB_EXPORTS` işlemci tanımları iletişim kutusuna ekleyin.

5. Belirtilen işlevlerin minimal uygulamalarını ekleyin. **RooterLib. cpp** ' i açın ve aşağıdaki kodu ekleyin:

    ```
    // constructor
    CRooterLib::CRooterLib()
    {
    }

    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
    {
        return 0.0;
    }

    ```

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="BKMK_Couple_the_test_project_to_the_dll_project"></a> DLL projesine test projesi için birkaç

1. RooterLib öğesini RooterLibTests projesine ekleyin.

   1. Çözüm Gezgini, **RooterLibTests** projesini seçin ve ardından kısayol menüsünde **Başvurular...** öğesini seçin.

   2. RooterLib proje özellikleri iletişim kutusunda, **ortak özellikler** ' i genişletin ve **çerçeve ve başvurular**' ı seçin.

   3. **Yeni Başvuru Ekle...** seçeneğini belirleyin.

   4. **Başvuru Ekle** Iletişim kutusunda **çözüm** ' i genişletin ve ardından **Projeler**' i seçin. Ardından, **Routerlib** öğesini seçin.

2. **UnitTest1. cpp**Içinde RooterLib üstbilgi dosyasını dahil edin.

   1. **UnitTest1. cpp**öğesini açın.

   2. Bu kodu satırın altına ekleyin `#include "CppUnitTest.h"` :

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. İçeri aktarılan işlevi kullanan bir test ekleyin. Aşağıdaki kodu **UnitTest1. cpp**öğesine ekleyin:

   ```
   TEST_METHOD(BasicTest)
   {
       CRooterLib rooter;
       Assert::AreEqual(
           // Expected value:
           0.0,
           // Actual value:
           rooter.SquareRoot(0.0),
           // Tolerance:
           0.01,
           // Message:
           L"Basic test failed",
           // Line number - used if there is no PDB file:
           LINE_INFO());
   }

   ```

4. Çözümü derleyin.

    Yeni test, test Gezgini 'nde, **çalıştırma testleri** düğümünde görünür.

5. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

    ![Temel test geçildi](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")

   Test ve kod projelerini ayarlamış ve kod projesindeki işlevleri çalıştıran testleri çalıştıracağınızı doğruladınız. Artık gerçek testleri ve kodu yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Testleri tekrarlayarak ve geçiş yapın

1. Yeni bir test ekleyin:

    ```
    TEST_METHOD(RangeTest)
    {
        CRooterLib rooter;
        for (double v = 1e-6; v < 1e6; v = v * 3.2)
        {
            double expected = v;
            double actual = rooter.SquareRoot(v*v);
            double tolerance = expected/1000;
            Assert::AreEqual(expected, actual, tolerance);
        }
    };

    ```

    > [!TIP]
    > Geçilen testleri değiştirmenizi öneririz. Bunun yerine, yeni bir test ekleyin, kodu test geçişi olacak şekilde güncelleştirin ve daha sonra başka bir test ekleyin ve bu şekilde devam edin.
    >
    >  Kullanıcılarınız gereksinimlerini değiştirmelerine göre artık doğru olmayan Testleri devre dışı bırakın. Yeni testler yazın ve aynı anda bir kez, aynı şekilde çalışır hale getirin.

2. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

3. Test başarısız oluyor.

     ![RangeTest başarısız oluyor](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")

    > [!TIP]
    > Her testin yazıldıktan hemen sonra başarısız olduğunu doğrulayın. Bu, hiç başarısız olmayan bir testi yazmanın kolay bir hata yaşamadan kaçınmanıza yardımcı olur.

4. Yeni testin başarılı olması için test kapsamındaki kodu geliştirin. Şunları **RooterLib. cpp**öğesine ekleyin:

    ```cpp
    #include <math.h>
    ...
    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
    {
        double result = v;
        double diff = v;
        while (diff > result/1000)
        {
            double oldResult = result;
            result = result - (result*result - v)/(2*result);
            diff = abs (oldResult - result);
        }
        return result;
    }

    ```

5. Çözümü derleyin ve ardından Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

     Her iki test de geçer.

> [!TIP]
> Her seferinde bir test ekleyerek kod geliştirin. Her yinelemeden sonra tüm testlerin başarılı olduğundan emin olun.

## <a name="debug-a-failing-test"></a><a name="BKMK_Debug_a_failing_test"></a> Başarısız bir testte hata ayıkla

1. **UnitTest1. cpp**öğesine başka bir test ekleyin:

   ```
   // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRooterLib rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          swprintf_s(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          swprintf_s(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
   };

   ```

2. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

    Test başarısız oluyor. Test Gezgini 'nde test adını seçin. Başarısız onaylama vurgulanır. Hata iletisi, test Gezgini 'nin ayrıntı bölmesinde görünür.

    ![Negatiftiverangetests başarısız oldu](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")

3. Testin neden başarısız olduğunu görmek için, işlevi adım adım inceleyin:

   1. İşlevin başlangıcında bir kesme noktası ayarlayın `SquareRoot` .

   2. Başarısız testin kısayol menüsünde, **Seçili testlerin hatalarını ayıkla**' yı seçin.

        Çalıştırma kesme noktasında durdurulduğunda kodda adım adım ilerleyin.

   3. Özel durumu yakalamak için **RooterLib. cpp** öğesine kod ekleyin:

       ```
       #include <stdexcept>
       ...
       double CRooterLib::SquareRoot(double v)
       {
           //Validate the input parameter:
           if (v < 0.0)
           {
             throw std::out_of_range("Can't do square roots of negatives");
           }
       ...

       ```

   1. Test Gezgini 'nde, düzeltilen yöntemi sınamak için **Tümünü Çalıştır** ' ı seçin ve bir gerileme sunmadığınızdan emin olun.

   Şimdi tüm testler geçer.

   ![Tüm testler geçer](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")

## <a name="refactor-the-code-without-changing-tests"></a><a name="BKMK_Refactor_the_code_without_changing_tests"></a> Testleri değiştirmeden kodu yeniden düzenleme

1. İşlevde merkezi hesaplamayı basitleştirme `SquareRoot` :

    ```
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;

    ```

2. Yeniden düzenlenmiş yöntemini test etmek için **Tümünü Çalıştır** ' ı seçin ve bir gerileme sunmadığınızdan emin olun.

    > [!TIP]
    > Kararlı bir iyi birim testi kümesi, kodu değiştirirken hata sunmaabileceğinizden emin olmanızı sağlar.
    >
    >  Yeniden düzenlemeyi diğer değişikliklerden ayrı tutun.
