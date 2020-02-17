---
title: UWP uygulamaları için C++ dll 'yi test etme
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: jillfra
ms.workload:
- uwp
author: corob-msft
ms.openlocfilehash: 540ff59838343988e7a27f42f8a10d723de1f649
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77274451"
---
# <a name="how-to-test-a-c-dll"></a>C++ Dll 'yi test etme

Bu konuda, C++ için birim testleri Microsoft Test Çerçevesi ile Evrensel Windows Platformu (UWP) uygulamaları için C++ DLL için oluşturma yöntemlerinden biri açıklanmaktadır. RooterLib DLL, belirsiz bellek sınırı teorik, hesaplama bir tahminini verilen bir sayının kare kökünü hesaplayan bir işlevi uygulayarak gösterir. DLL ardından eğlenceli bir kullanıcı gösteren bir UWP uygulamasında eklenebilir matematik ile yapılabilir şeyler.

Bu konuda birim testi geliştirmede ilk adım olarak kullanma işlemini gösterir. Bu yaklaşım önce test ettiğiniz sistemde belirli bir davranış doğrulayan bir test yöntemi yazın ve ardından testin başarılı olması kod yazacaksınız. Aşağıdaki yordamlar sırasına göre değişiklikler yaparak, bu strateji ilk Yazımdan sonra birim testleri yazma ve test etmek istediğiniz kod tersine çevirebilirsiniz.

Bu konuda ayrıca tek bir Visual Studio çözümü de ayrı projeler için birim testleri ve test etmek istediğiniz DLL oluşturur. Doğrudan DLL projede birim testleri de içerebilir veya ayrı çözümler için birim testleri oluşturabilirsiniz ve. DLL. Hangi yapının kullanılacağı hakkında ipuçları için bkz. [var olan C++ uygulamalara birim testleri ekleme](../test/how-to-use-microsoft-test-framework-for-cpp.md) .

## <a name="Create_the_solution_and_the_unit_test_project"></a>Çözüm ve birim testi projesi oluşturma

::: moniker range="vs-2019"

Yeni bir test projesi oluşturarak başlayın. **Dosya** menüsünde **Yeni** > **Proje**' yi seçin. **Yeni proje oluştur** iletişim kutusunda, arama kutusuna "test" yazın ve sonra **dili** olarak C++ayarlayın. Ardından proje şablonları listesinden **birim test uygulaması (Evrensel Windows)** öğesini seçin.

   ![Yeni bir UWP test projesi oluştur](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Yeni bir test projesi oluşturarak başlayın. **Dosya** menüsünde **Yeni** > **Proje**' yi seçin. **Yeni proje** iletişim kutusunda, **yüklü** >  **C++ görseli** genişletin ve **Windows Evrensel**' i seçin. Ardından proje şablonları listesinden **birim test uygulaması (Evrensel Windows)** öğesini seçin.

::: moniker-end

1. Yeni proje iletişim kutusunda, **yüklü** >  **C++ görseli** genişletin ve **Windows Evrensel**' i seçin. Ardından proje şablonları listesinden **birim test uygulaması (Evrensel Windows)** öğesini seçin.

2. Projeyi `RooterLibTests`olarak adlandırın; konumu belirtin; çözümü adlandırın `RooterLib`; ve **çözüm için dizin oluşturma** ' nın işaretli olduğundan emin olun.

     ![Çözüm ve proje adını ve konumunu belirtin](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. Yeni projede, **UnitTest1. cpp**' yi açın.

     ![UnitTest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Aşağıdakilere dikkat edin:

    - Her test `TEST_METHOD(YourTestName){...}`kullanılarak tanımlanır.

         Geleneksel işlev imzası yazmanız gerekmez. İmza TEST_METHOD makro tarafından oluşturulur. Makro, void döndüren bir örnek işlevi oluşturur. Ayrıca, test yöntemi hakkında bilgi döndüren statik bir işlev oluşturur. Test Gezgini, yöntem bulmak bu bilgileri sağlar.

    - Test yöntemleri `TEST_CLASS(YourClassName){...}`kullanılarak sınıflar halinde gruplandırılır.

         Testler çalıştırıldığında, her test sınıfının bir örneği oluşturulur. Test yöntemlerini belirtilmemiş sırayla çağrılır. Önce ve sonra her bir modül, sınıf veya yöntemi çağıran özel yöntemi tanımlayabilirsiniz. Daha fazla bilgi için bkz. [Microsoft. VisualStudio. TestTools. CppUnitTestFramework kullanma](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="Verify_that_the_tests_run_in_Test_Explorer"></a>Test Gezgini 'nde testlerin çalıştırıldığını doğrulama

1. Bazı test kodu ekleyin:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     `Assert` sınıfının, test yöntemlerinde sonuçları doğrulamak için kullanabileceğiniz çeşitli statik yöntemler sağladığını unutmayın.

2. **Test** menüsünde **Çalıştır** ' ı ve ardından **Tümünü Çalıştır**' ı seçin.

     Test projesi oluşturur ve çalıştırır. **Test Gezgini** penceresi görünür ve test **geçilen testler**altında listelenir. Pencerenin alt kısmındaki **Özet** bölmesi, seçilen test hakkında ek ayrıntılar sağlar.

     ![Test Gezgini](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="Add_the_DLL_project_to_the_solution"></a>Çözüme DLL projesi ekleme

::: moniker range="vs-2019"

**Çözüm Gezgini**, çözüm adını seçin. Kısayol menüsünde, **Ekle**ve ardından **Yeni proje**' yi seçin. **Yeni Proje Ekle** Iletişim kutusunda **dil** ' i ayarlayın C++ ve arama kutusuna "dll" yazın. Sonuçlar listesinden **birim test uygulaması (Evrensel Windows C++-/CX)** öğesini seçin.

![RooterLib projesi oluşturma](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
**Çözüm Gezgini**, çözüm adını seçin. Kısayol menüsünde, **Ekle**ve ardından **Yeni proje**' yi seçin.

![RooterLib projesi oluşturma](../test/media/ute_cpp_windows_rooterlib_create.png)

::: moniker-end

1. **Yeni Proje Ekle** iletişim kutusunda, **dll (UWP uygulamaları)** öğesini seçin.

2. Aşağıdaki kodu *RooterLib. h* dosyasına ekleyin:

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

     Yorumlar yalnızca dll geliştiriciye ancak herkes tarafından DLL içinde kendi proje başvurusu ifdef bloğu açıklanmaktadır. DLL proje özelliklerini kullanarak, komut satırına ROOTERLIB_EXPORTS sembol ekleyebilirsiniz.

     `CRooterLib` sınıfı bir Oluşturucu ve `SqareRoot` tahmin aracı metodunu bildirir.

3. ROOTERLIB_EXPORTS sembol komut satırına ekleyin.

    1. **Çözüm Gezgini**, **RooterLib** projesini seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.

         ![Önişlemci sembolü tanımı Ekle](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. **RooterLib Özellik sayfası** Iletişim kutusunda **yapılandırma özellikleri**' ni genişletin **C++** ve **Önişlemci**' yi seçin.

    3. **\<Düzenle 'yi seçin...** ön **işlemci tanımları** listesinden > ve sonra **önişlemci tanımları** iletişim kutusuna `ROOTERLIB_EXPORTS` ekleyin.

4. Bildirilen işlevlerin en az uygulamaları ekleyin. *RooterLib. cpp* ' i açın ve aşağıdaki kodu ekleyin:

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

## <a name="make_the_dll_functions_visible_to_the_test_code"></a>DLL işlevlerini test kodu için görünür hale getirme

1. RooterLib RooterLibTests projeye ekleyin.

   1. **Çözüm Gezgini**, **RooterLibTests** projesini ve ardından kısayol menüsünde > başvuru **Ekle** ' yi seçin.

   1. **Başvuru Ekle** Iletişim kutusunda **Projeler**' i seçin. Ardından, **Routerlib** öğesini seçin.

2. *UnitTest1. cpp*Içinde RooterLib üstbilgi dosyasını dahil edin.

   1. *UnitTest1. cpp*öğesini açın.

   2. Bu kodu `#include "CppUnitTest.h"` satırı altına ekleyin:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. İçeri aktarılan işlevini kullanan bir test ekleyin. Aşağıdaki kodu *UnitTest1. cpp*öğesine ekleyin:

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

4. Çözümü oluşturun.

    Yeni test, **Test Gezgini** 'Nde, **çalıştırma testleri** düğümünde görünür.

5. **Test Gezgini**Içinde **Tümünü Çalıştır**' ı seçin.

    ![Temel Test geçildi](../test/media/ute_cpp_testexplorer_basictest.png)

   Test ve kod projelerini ayarlama sahiptir ve doğrulandı, kod projesinde işlevleri çalıştırmak testlerini çalıştırabilirsiniz. Şimdi gerçek test ve kod yazmaya başlayabilirsiniz.

## <a name="Iteratively_augment_the_tests_and_make_them_pass"></a>Testleri tekrarlayarak ve geçiş yapın

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
    > Geçmiş olan testleri değiştirmemenizi öneririz. Bunun yerine, yeni test Ekle, kod testin başarılı olması için güncelleştirin ve ardından başka bir test ekleyin ve benzeri.
    >
    > Kullanıcılarınızın gereksinimlerine değiştirdiğinizde, artık doğru testleri devre dışı bırakın. Yeni testler yazmak ve bunları teker teker artımlı aynı şekilde çalışır duruma getirin.

2. **Test Gezgini**Içinde **Tümünü Çalıştır**' ı seçin.

3. Test başarısız olur.

     ![RangeTest başarısız](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Hemen yazdıktan sonra her testin başarısız olduğunu doğrulayın. Bu, hiçbir zaman başarısız bir test yazma kolay onlardan yardımcı olur.

4. Yeni test geçer, test edilen kod geliştirin. Şunları *RooterLib. cpp*öğesine ekleyin:

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

5. Çözümü derleyin ve ardından **Test Gezgini**Içinde **Tümünü Çalıştır**' ı seçin.

     Her iki testler başarılı.

> [!TIP]
> Aynı anda testleri bir ekleyerek kod geliştirin. Tüm testler her yinelemeden sonra başarılı olduğundan emin olun.

## <a name="Debug_a_failing_test"></a>Başarısız bir testte hata ayıkla

1. *UnitTest1. cpp*öğesine başka bir test ekleyin:

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

2. **Test Gezgini**Içinde **Tümünü Çalıştır**' ı seçin.

    Test başarısız olur. **Test Gezgini**'nde test adını seçin. Onaylama başarısız vurgulanır. Hata iletisi, **Test Gezgini**'nin ayrıntı bölmesinde görünür.

    ![NegativeRangeTests başarısız oldu](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Testin neden başarısız görmek için işlev adım:

   1. `SquareRoot` işlevinin başlangıcında bir kesme noktası ayarlayın.

   2. Başarısız testin kısayol menüsünde, **Seçili testlerin hatalarını ayıkla**' yı seçin.

        Kesme noktasında çalıştırma sona erdiğinde, kodda adım adım.

   3. Özel durumu yakalamak için *RooterLib. cpp* öğesine kod ekleyin:

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

   1. **Test Gezgini**'nde, düzeltilen yöntemi sınamak Için **Tümünü Çalıştır** ' ı seçin ve bir gerileme sunmadığınızdan emin olun.

   Artık tüm sınamaları geçmesi.

   ![Tüm testler başarılı](../test/media/ute_ult_alltestspass.png)

## <a name="Refactor_the_code_without_changing_tests"></a>Testleri değiştirmeden kodu yeniden düzenleme

1. `SquareRoot` işlevinde merkezi hesaplamayı kolaylaştırın:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Yeniden düzenlenmiş yöntemini test etmek için **Tümünü Çalıştır** ' ı seçin ve bir gerileme sunmadığınızdan emin olun.

    > [!TIP]
    > Kararlı bir dizi iyi birim testi kodu değiştirdiğinizde, yeni hatalar oluşturmadığından emin olmanızı sağlar.
    >
    > Diğer değişikliklerden ayrı düzenlemesi tutun.
