---
title: UWP uygulamaları için C++ DLL nasıl test edilir?
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: jillfra
ms.workload:
- uwp
author: corob-msft
ms.openlocfilehash: 540ff59838343988e7a27f42f8a10d723de1f649
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77274451"
---
# <a name="how-to-test-a-c-dll"></a>C++ DLL nasıl test edilir?

Bu konu, C++ için Microsoft Test Framework ile Evrensel Windows Platformu (UWP) uygulamaları için c++ DLL için birim testleri oluşturmanın bir yolunu açıklar. RooterLib DLL, belirli bir sayının kare kökünün tahminini hesaplayan bir işlev uygulayarak kalkülüsten sınır teorisinin belirsiz anılarını gösterir. DLL daha sonra bir kullanıcı matematik ile yapılabilir eğlenceli şeyler gösteren bir UWP uygulaması dahil edilebilir.

Bu konu, geliştirmenin ilk adımı olarak birim testini nasıl kullanacağınızı gösterir. Bu yaklaşımda, önce test ettiğiniz sistemde belirli bir davranışı doğrulayan bir test yöntemi yazarsınız ve ardından testi geçen kodu yazarsınız. Aşağıdaki yordamların sırasına göre değişiklikler yaparak, önce test etmek istediğiniz kodu yazmak ve sonra birim testlerini yazmak için bu stratejiyi tersine çevirebilirsiniz.

Bu konu aynı zamanda tek bir Visual Studio çözümü ve birim testleri ve test etmek istediğiniz DLL için ayrı projeler oluşturur. Birim testlerini doğrudan DLL projesine de ekleyebilirsiniz veya birim testleri ve . Dll. Bkz. Hangi yapının kullanılacağına ilişkin ipuçları için [varolan C++ uygulamalarına birim testleri ekleme.](../test/how-to-use-microsoft-test-framework-for-cpp.md)

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="Create_the_solution_and_the_unit_test_project"></a>Çözümü ve birim test projesini oluşturun

::: moniker range="vs-2019"

Yeni bir test projesi oluşturarak başlayın. **Dosya** menüsünde **Yeni** > **Proje'yi**seçin. Yeni **Proje Oluştur** iletişim kutusunda, arama kutusuna "test" yazın ve ardından **Dil'i** C++'a ayarlayın. Ardından, proje şablonları listesinden **Birim Test Uygulaması'nı (Evrensel Windows)** seçin.

   ![Yeni bir UWP test projesi oluşturma](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Yeni bir test projesi oluşturarak başlayın. **Dosya** menüsünde **Yeni** > **Proje'yi**seçin. Yeni **Proje** iletişim kutusunda, **Yüklü** > **Visual C++** seçeneğini genişletin ve **Windows Universal'ı**seçin. Ardından, proje şablonları listesinden **Birim Test Uygulaması'nı (Evrensel Windows)** seçin.

::: moniker-end

1. Yeni Proje iletişim kutusunda, **Yüklü** > **Visual C++** seçeneğini genişletin ve **Windows Universal'ı**seçin. Ardından, proje şablonları listesinden **Birim Test Uygulaması'nı (Evrensel Windows)** seçin.

2. Projeyi `RooterLibTests`adlandırın; konumu belirtin; çözüm `RooterLib`adı ; ve **çözüm için create dizininin** kontrol edildiğinden emin olun.

     ![Çözümü ve proje adını ve konumunu belirtin](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. Yeni projede **unittest1.cpp'yi**aç.

     ![unittest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Şunlara dikkat edin:

    - Her test kullanılarak `TEST_METHOD(YourTestName){...}`tanımlanır.

         Geleneksel bir işlev imzası yazmak zorunda değildir. İmza makro TEST_METHOD tarafından oluşturulur. Makro, geçersiz dönen bir örnek işlevi oluşturur. Ayrıca, test yöntemi hakkında bilgi döndüren statik bir işlev de oluşturur. Bu bilgiler, test gezgininin yöntemi bulmasını sağlar.

    - Test yöntemleri kullanılarak `TEST_CLASS(YourClassName){...}`sınıflara gruplandırılır.

         Testler çalıştırıldığında, her test sınıfının bir örneği oluşturulur. Test yöntemleri belirtilmemiş bir sırada çağrılır. Her modülden, sınıftan veya yöntemden önce ve sonra çağrılan özel yöntemler tanımlayabilirsiniz. Daha fazla bilgi için [Bkz. Microsoft.VisualStudio.TestTools.CppUnitTestFramework kullanarak.](how-to-use-microsoft-test-framework-for-cpp.md)

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="Verify_that_the_tests_run_in_Test_Explorer"></a>Testlerin Test Gezgini'nde çalıştırıldığını doğrulama

1. Bazı test kodu ekleyin:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Sınıfın, `Assert` test yöntemleriyle sonuçları doğrulamak için kullanabileceğiniz birkaç statik yöntem sağladığına dikkat edin.

2. **Test** menüsünde **Çalıştır'ı** seçin ve ardından **Tümlerini Çalıştır'ı**seçin.

     Test projesi oluşturur ve çalışır. **Test Gezgini** penceresi görüntülenir ve test **Geçti Testleri**altında listelenir. Pencerenin altındaki **Özet** bölmesi, seçili test hakkında ek ayrıntılar sağlar.

     ![Test Gezgini](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-dll-project-to-the-solution"></a><a name="Add_the_DLL_project_to_the_solution"></a>Çözüme DLL projesini ekleme

::: moniker range="vs-2019"

**Çözüm Gezgini'nde**çözüm adını seçin. Kısayol menüsünden **Ekle**ve ardından **Yeni Proje'yi**seçin. Yeni **Proje Ekle** iletişim kutusunda **Dil'i** C++ olarak ayarlayın ve arama kutusuna "DLL" yazın. Sonuç listesinden **Birim Test Uygulaması'nı (Evrensel Windows - C++/CX)** seçin.

![RooterLib projesini oluşturma](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
**Çözüm Gezgini'nde**çözüm adını seçin. Kısayol menüsünden **Ekle**ve ardından **Yeni Proje'yi**seçin.

![RooterLib projesini oluşturma](../test/media/ute_cpp_windows_rooterlib_create.png)

::: moniker-end

1. Yeni **Proje Ekle** iletişim kutusunda **DLL (UWP uygulamaları)** seçeneğini belirleyin.

2. *RooterLib.h* dosyasına aşağıdaki kodu ekleyin:

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

     Açıklamalar ifdef blok sadece dll geliştiricisi için, ama kendi projesinde DLL başvurulan herkes için açıklar. DLL'nin proje özelliklerini kullanarak komut satırına ROOTERLIB_EXPORTS simgesini ekleyebilirsiniz.

     Sınıf `CRooterLib` bir oluşturucu ve `SqareRoot` tahminci yöntemi bildirir.

3. Komut satırına ROOTERLIB_EXPORTS simgesini ekleyin.

    1. **Çözüm Gezgini'nde** **RooterLib** projesini seçin ve ardından kısayol menüsünden **Özellikler'i** seçin.

         ![Önişlemci sembolü tanımı ekleme](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. **RooterLib Özellik Sayfası** iletişim kutusunda, **Yapılandırma Özelliklerini**genişletin, **C++'ı** genişletin ve **Önİşlemci'yi**seçin.

    3. **Önİşlemeİşlemci Tanımlar** listesinden ** \<>'yı edin** ve ardından **Önİşlemci Tanımlar** iletişim kutusuna ekleyin. `ROOTERLIB_EXPORTS`

4. Bildirilen işlevlerin en az uygulamalarını ekleyin. *RooterLib.cpp'yi* açın ve aşağıdaki kodu ekleyin:

    ```cpp
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

## <a name="make-the-dll-functions-visible-to-the-test-code"></a><a name="make_the_dll_functions_visible_to_the_test_code"></a>DLl işlevlerini test koduna görünür hale getirme

1. RooterLib'i RooterLib projesine ekleyin.

   1. **Çözüm Gezgini'nde** **RooterLibTests** projesini seçin ve ardından kısayol menüsünde**Başvuru** **Ekle'yi** > seçin.

   1. Başvuru **Ekle** iletişim kutusunda **Projeler'i**seçin. Ardından **RouterLib** öğesini seçin.

2. *Unittest1.cpp'ye*RooterLib üstbilgi dosyasını ekleyin.

   1. *Açık unittest1.cpp*.

   2. Bu kodu satırın `#include "CppUnitTest.h"` altına ekleyin:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. İçe aktarılan işlevi kullanan bir test ekleyin. *Unittest1.cpp*için aşağıdaki kodu ekleyin:

   ```cpp
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

    Yeni test, Test **Gezgini'nde** **Çalıştırılmayan Testler** düğümünde görünür.

5. **Test Gezgini'nde,** **Tümlerini Çalıştır'ı**seçin.

    ![Temel Test geçti](../test/media/ute_cpp_testexplorer_basictest.png)

   Testi ve kod projelerini ayarladınız ve kod projesinde işlevleri çalıştıran testleri çalıştırabileceğinizi doğruladınız. Şimdi gerçek testler ve kod yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="Iteratively_augment_the_tests_and_make_them_pass"></a>Testleri yinelemeli bir şekilde artırın ve geçmelerini

1. Yeni bir test ekleyin:

    ```cpp
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
    > Geçen testleri değiştirmemenizi öneririz. Bunun yerine, yeni bir test ekleyin, testi geçsin diye kodu güncelleştirin ve sonra başka bir test ekleyin ve benzerlerini ekleyin.
    >
    > Kullanıcılarınız gereksinimlerini değiştirdiğinde, artık doğru olmayan testleri devre dışı bırakın. Yeni testler yazın ve aynı artımlı şekilde teker teker çalışmasını sağlayabilir.

2. **Test Gezgini'nde,** **Tümlerini Çalıştır'ı**seçin.

3. Test başarısız olur.

     ![RangeTest başarısız olur](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Her testin siz yazdıktan hemen sonra başarısız olduğunu doğrulayın. Bu, asla başarısız olmayan bir test yazmanın kolay hatasını önlemenize yardımcı olur.

4. Yeni testin geçmesi için test altındaki kodu geliştirin. *RooterLib.cpp*için aşağıdakileri ekleyin:

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

5. Çözümü oluşturun ve ardından **Test Gezgini'nde** **Tümlerini Çalıştır'ı**seçin.

     Her iki test de geçer.

> [!TIP]
> Testleri teker teker ekleyerek kod geliştirin. Tüm testlerin her yinelemeden sonra geçtiğinden emin olun.

## <a name="debug-a-failing-test"></a><a name="Debug_a_failing_test"></a>Başarısız bir testi hata ayıklama

1. *unittest1.cpp*için başka bir test ekle :

   ```cpp
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

2. **Test Gezgini'nde,** **Tümlerini Çalıştır'ı**seçin.

    Test başarısız olur. **Test**Gezgini'nde test adını seçin. Başarısız iddia vurgulanır. Hata iletisi **Test Gezgini'nin**ayrıntı bölmesinde görünür.

    ![NegativeRangeTests başarısız oldu](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Testin neden başarısız olduğunu görmek için işlevden geçin:

   1. `SquareRoot` İşlevin başında bir kesme noktası ayarlayın.

   2. Başarısız olan testin kısayol menüsünde **Hata Ayıklama Seçili Testleri'ni**seçin.

        Çalıştırma kesme noktasında durduğunda, kodu niçin geç.

   3. Özel durumu yakalamak için *RooterLib.cpp'ye* kod ekleyin:

       ```cpp
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

   1. **Test Gezgini'nde,** düzeltilen yöntemi test etmek ve bir gerileme getirmediğinizden emin olmak için **Tümlerini Çalıştır'ı** seçin.

   Tüm testler artık geçti.

   ![Tüm testler geçer](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code-without-changing-tests"></a><a name="Refactor_the_code_without_changing_tests"></a>Testleri değiştirmeden kodu yeniden düzenleme

1. İşlevdeki merkezi `SquareRoot` hesaplamayı basitleştirin:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Refactored yöntemini test etmek ve bir gerileme getirmediğinden emin olmak için **Tümlerini Çalıştır'ı** seçin.

    > [!TIP]
    > İyi birim testleri kararlı bir dizi kodu değiştirdiğinizde hataları tanıttı değil güven verir.
    >
    > Yeniden düzenlemeyi diğer değişikliklerden ayrı tutun.
