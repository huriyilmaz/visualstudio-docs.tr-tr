---
title: UWP uygulamaları için C++ dll 'yi test etme
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- uwp
author: mikeblome
ms.openlocfilehash: 18d8382bcb4f3e348443050e818f0b59c2a18688
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748084"
---
# <a name="how-to-test-a-c-dll"></a>C++ Dll 'yi test etme

Bu konu, için C++ C++Microsoft Test ÇERÇEVESIYLE bir Evrensel Windows platformu (UWP) uygulamaları için birim testleri oluşturmanın bir yolunu açıklamaktadır. RooterLib DLL 'SI, belirli bir sayının kare kökünü tahmin eden bir işlev uygulayarak, ana bilgisayardan sınır teorisi 'nin ercesini gösterir. DLL daha sonra bir UWP uygulamasına dahil edilebilir ve bu da Kullanıcı matematik ile yapılabilecek eğlenceli şeyleri gösterir.

Bu konu, geliştirme aşamasında ilk adım olarak birim testi kullanmayı gösterir. Bu yaklaşımda, önce test ettiğiniz sistemde belirli bir davranışı doğrulayan bir test yöntemi yazar ve ardından testi geçiren kodu yazarsınız. Aşağıdaki yordamların sırasıyla değişiklik yaparak, test etmek istediğiniz kodu yazmak ve ardından birim testlerini yazmak için bu stratejiyi ters çevirebilirsiniz.

Bu konu ayrıca, tek bir Visual Studio çözümü ve test etmek istediğiniz birim testleri ve DLL için ayrı projeler oluşturur. Birim testlerini doğrudan DLL projesine da dahil edebilir veya birim testleri ve için ayrı çözümler oluşturabilirsiniz. Dosyasını. Hangi yapının kullanılacağı hakkında ipuçları için bkz. [var olan C++ uygulamalara birim testleri ekleme](../test/how-to-use-microsoft-test-framework-for-cpp.md) .

## <a name="Create_the_solution_and_the_unit_test_project"></a>Çözüm ve birim testi projesi oluşturma

::: moniker range="vs-2019"

Yeni bir test projesi oluşturarak başlayın. **Dosya** menüsünde, **Yeni** > **Proje**' yi seçin. **Yeni proje oluştur** iletişim kutusunda, arama kutusuna "test" yazın ve sonra **dili** olarak C++ayarlayın. Ardından proje şablonları listesinden **birim test uygulaması (Evrensel Windows)** öğesini seçin.

   ![Yeni bir UWP test projesi oluştur](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Yeni bir test projesi oluşturarak başlayın. **Dosya** menüsünde, **Yeni** > **Proje**' yi seçin. **Yeni proje** iletişim kutusunda, **yüklü**  >  **C++ görseli** genişletin ve **Windows Evrensel**' i seçin. Ardından proje şablonları listesinden **birim test uygulaması (Evrensel Windows)** öğesini seçin.

::: moniker-end

1. Yeni proje iletişim kutusunda, **yüklü**  >  **C++ görseli** genişletin ve **Windows Evrensel**' i seçin. Ardından proje şablonları listesinden **birim test uygulaması (Evrensel Windows)** öğesini seçin.

2. Projeyi `RooterLibTests` olarak adlandırın; konumu belirtin; çözümü adlandırın `RooterLib`; ve **çözüm için dizin oluşturma** ' nın işaretli olduğundan emin olun.

     ![Çözüm ve proje adını ve konumunu belirtin](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. Yeni projede, **UnitTest1. cpp**' yi açın.

     ![UnitTest1. cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Aşağıdakilere dikkat edin:

    - Her test `TEST_METHOD(YourTestName){...}` kullanılarak tanımlanır.

         Geleneksel bir işlev imzası yazmanız gerekmez. İmza, makro TEST_METHOD tarafından oluşturulur. Makro, void döndüren bir örnek işlevi oluşturur. Ayrıca test yöntemiyle ilgili bilgileri döndüren statik bir işlev oluşturur. Bu bilgiler, test Gezgini 'nin yöntemi bulmasını sağlar.

    - Test yöntemleri `TEST_CLASS(YourClassName){...}` kullanılarak sınıflar halinde gruplandırılır.

         Testler çalıştırıldığında, her bir test sınıfının bir örneği oluşturulur. Test yöntemleri belirtilmemiş bir sırada çağırılır. Her modül, sınıf veya yöntemden önce ve sonra çağrılan özel yöntemler tanımlayabilirsiniz. Daha fazla bilgi için bkz. [Microsoft. VisualStudio. TestTools. CppUnitTestFramework kullanma](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="Verify_that_the_tests_run_in_Test_Explorer"></a>Test Gezgini 'nde testlerin çalıştırıldığını doğrulama

1. Bir test kodu ekleyin:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     @No__t_0 sınıfının, test yöntemlerinde sonuçları doğrulamak için kullanabileceğiniz çeşitli statik yöntemler sağladığını unutmayın.

2. **Test** menüsünde **Çalıştır** ' ı ve ardından **Tümünü Çalıştır**' ı seçin.

     Test projesi oluşturulup çalışır. **Test Gezgini** penceresi görünür ve test **geçilen testler**altında listelenir. Pencerenin alt kısmındaki **Özet** bölmesi, seçilen test hakkında ek ayrıntılar sağlar.

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

     Açıklamalar IDEF bloğunu yalnızca dll geliştiricisi için değil, projesinde DLL 'ye başvuran herkese da açıklamaktadır. DLL 'nin proje özelliklerini kullanarak komut satırına ROOTERLIB_EXPORTS sembolünü ekleyebilirsiniz.

     @No__t_0 sınıfı bir Oluşturucu ve `SqareRoot` tahmin aracı metodunu bildirir.

3. Komut satırına ROOTERLIB_EXPORTS sembolünü ekleyin.

    1. **Çözüm Gezgini**, **RooterLib** projesini seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.

         ![Önişlemci sembol tanımı ekleme](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. **RooterLib Özellik sayfası** Iletişim kutusunda **yapılandırma özellikleri**' ni genişletin **C++** ve **Önişlemci**' yi seçin.

    3. **@No__t_1Edit seçin...** ön **işlemci tanımları** listesinden > ve sonra **önişlemci tanımları** iletişim kutusuna `ROOTERLIB_EXPORTS` ekleyin.

4. Belirtilen işlevlerin minimal uygulamalarını ekleyin. *RooterLib. cpp* ' i açın ve aşağıdaki kodu ekleyin:

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

1. RooterLib öğesini RooterLibTests projesine ekleyin.

   1. **Çözüm Gezgini**, **RooterLibTests** projesini ve ardından kısayol menüsünde  >  başvuru **Ekle** ' yi seçin.

   1. **Başvuru Ekle** Iletişim kutusunda **Projeler**' i seçin. Ardından, **Routerlib** öğesini seçin.

2. *UnitTest1. cpp*Içinde RooterLib üstbilgi dosyasını dahil edin.

   1. *UnitTest1. cpp*öğesini açın.

   2. Bu kodu `#include "CppUnitTest.h"` satırı altına ekleyin:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. İçeri aktarılan işlevi kullanan bir test ekleyin. Aşağıdaki kodu *UnitTest1. cpp*öğesine ekleyin:

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

    ![Temel test geçildi](../test/media/ute_cpp_testexplorer_basictest.png)

   Test ve kod projelerini ayarlamış ve kod projesindeki işlevleri çalıştıran testleri çalıştıracağınızı doğruladınız. Artık gerçek testleri ve kodu yazmaya başlayabilirsiniz.

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
    > Geçilen testleri değiştirmenizi öneririz. Bunun yerine, yeni bir test ekleyin, kodu test geçişi olacak şekilde güncelleştirin ve daha sonra başka bir test ekleyin ve bu şekilde devam edin.
    >
    > Kullanıcılarınız gereksinimlerini değiştirmelerine göre artık doğru olmayan Testleri devre dışı bırakın. Yeni testler yazın ve aynı anda bir kez, aynı şekilde çalışır hale getirin.

2. **Test Gezgini**Içinde **Tümünü Çalıştır**' ı seçin.

3. Test başarısız oluyor.

     ![RangeTest başarısız oluyor](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Her testin yazıldıktan hemen sonra başarısız olduğunu doğrulayın. Bu, hiç başarısız olmayan bir testi yazmanın kolay bir hata yaşamadan kaçınmanıza yardımcı olur.

4. Yeni testin başarılı olması için test kapsamındaki kodu geliştirin. Şunları *RooterLib. cpp*öğesine ekleyin:

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

     Her iki test de geçer.

> [!TIP]
> Her seferinde bir test ekleyerek kod geliştirin. Her yinelemeden sonra tüm testlerin başarılı olduğundan emin olun.

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

    Test başarısız oluyor. **Test Gezgini**'nde test adını seçin. Başarısız onaylama vurgulanır. Hata iletisi, **Test Gezgini**'nin ayrıntı bölmesinde görünür.

    ![Negatiftiverangetests başarısız oldu](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Testin neden başarısız olduğunu görmek için, işlevi adım adım inceleyin:

   1. @No__t_0 işlevinin başlangıcında bir kesme noktası ayarlayın.

   2. Başarısız testin kısayol menüsünde, **Seçili testlerin hatalarını ayıkla**' yı seçin.

        Çalıştırma kesme noktasında durdurulduğunda kodda adım adım ilerleyin.

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

   Şimdi tüm testler geçer.

   ![Tüm testler geçer](../test/media/ute_ult_alltestspass.png)

## <a name="Refactor_the_code_without_changing_tests"></a>Testleri değiştirmeden kodu yeniden düzenleme

1. @No__t_0 işlevinde merkezi hesaplamayı kolaylaştırın:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Yeniden düzenlenmiş yöntemini test etmek için **Tümünü Çalıştır** ' ı seçin ve bir gerileme sunmadığınızdan emin olun.

    > [!TIP]
    > Kararlı bir iyi birim testi kümesi, kodu değiştirirken hata sunmaabileceğinizden emin olmanızı sağlar.
    >
    > Yeniden düzenlemeyi diğer değişikliklerden ayrı tutun.
