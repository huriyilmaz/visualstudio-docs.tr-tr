---
title: UWP uygulamaları için C++ DLL'lerini test etmek için
description: C++ için Microsoft Test Framework ile Universal Windows Platform uygulamaları için C++ DLL'si için birim testleri oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 05/01/2019
ms.topic: how-to
ms.author: corob
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- uwp
author: corob-msft
ms.openlocfilehash: 7cb42908ded494a2fcc3941a67b0236530e3eb1adf56a74936789608dd29eb4a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121243789"
---
# <a name="how-to-test-a-c-dll"></a>C++ DLL'lerini test etmek için

Bu konuda, C++ için Microsoft Test Framework ile Evrensel Windows Platformu (UWP) uygulamaları için C++ DLL'si için birim testleri oluşturmanın bir yolu açıklanmıştır. RooterLib DLL'si, belirli bir sayanın karekökünün tahminini hesaplayıcı bir işlev kullanarak matematikten gelen sınır teorisinin belirsiz belleklerini gösterir. Daha sonra DLL, kullanıcıya matematik ile yaplandırı eğlenceli şeyleri gösteren bir UWP uygulamasına dahil olabilir.

Bu konu başlığında, geliştirmenin ilk adımı olarak birim testlerini nasıl kullanabileceğiniz gösterir. Bu yaklaşımda, önce test etmekte olduğunu sistemde belirli bir davranışı doğrular ve ardından testi geçen kodu yazarak bir test yöntemi yazarsiniz. Aşağıdaki yordamların sırasına göre değişiklik yaparak, önce test etmek istediğiniz kodu yazmak ve ardından birim testlerini yazmak için bu stratejiyi tersine çevirebilirsiniz.

Bu konu ayrıca tek bir Visual Studio çözümü ve birim testleri ile test etmek istediğiniz DLL için ayrı projeler oluşturur. Birim testlerini doğrudan DLL projesine de dahil etmek veya birim testleri ve birim testleri için ayrı çözümler .DLL. Hangi [yapının kullanımına yardımcı olacak ipuçları için bkz.](../test/how-to-use-microsoft-test-framework-for-cpp.md) Mevcut C++ uygulamalarına birim testleri ekleme.

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="Create_the_solution_and_the_unit_test_project"></a> Çözümü ve birim testi projesini oluşturma

::: moniker range=">=vs-2019"

Yeni bir test projesi oluşturarak başlayabilirsiniz. Dosya menüsünde **Yeni** **dosya'Project.**  >   Yeni Uygulama **Oluştur iletişim Project** kutusuna "test" yazın ve Dil'i C++ olarak ayarlayın.  Ardından proje **şablonları listesinden Birim Testi Windows (Evrensel Uygulama)** seçin.

   ![Yeni UWP test projesi oluşturma](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Yeni bir test projesi oluşturarak başlayabilirsiniz. Dosya menüsünde **Yeni** **dosya'Project.**  >   Yeni **Project** iletişim kutusunda Yüklü **uygulama'Visual C++** genişletin  >  **ve** **Evrensel'Windows seçin.** Ardından proje **şablonları listesinden Birim Testi Windows (Evrensel Uygulama)** seçin.

::: moniker-end

1. Yeni Uygulama iletişim Project, Yüklü **uygulama'Visual C++** genişletin  >  **ve** Evrensel'Windows **seçin.** Ardından proje **şablonları listesinden Birim Testi Windows (Evrensel Uygulama)** seçin.

2. Projeyi olarak `RooterLibTests` belirtin; konumu belirtin; çözümü olarak belirtin ve Çözüm için dizin `RooterLib` **oluştur'ın** işaretli olduğundan emin olun.

     ![Çözüm ve proje adını ve konumunu belirtme](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. Yeni projede **unittest1.cpp'yi açın.**

     ![unittest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Şunlara dikkat edin:

    - Her test kullanılarak `TEST_METHOD(YourTestName){...}` tanımlanır.

         Geleneksel işlev imzası yazmak zorunda değildir. İmza, makro TEST_METHOD. Makro, void döndüren bir örnek işlevi üretir. Ayrıca test yöntemi hakkında bilgi döndüren statik bir işlev de üretir. Bu bilgiler, test gezgininin yöntemini bulmasını sağlar.

    - Test yöntemleri kullanılarak sınıflara `TEST_CLASS(YourClassName){...}` gruplandı.

         Testler çalıştırılan her test sınıfının bir örneği oluşturulur. Test yöntemleri belirtilmemiş bir sırada çağrılır. Her modülden, sınıftan veya yöntemden önce ve sonra çağrılan özel yöntemler tanımlayabilirsiniz. Daha fazla bilgi için [bkz. Microsoft.VisualStudio.TestTools.CppUnitTestFramework kullanma.](how-to-use-microsoft-test-framework-for-cpp.md)

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="Verify_that_the_tests_run_in_Test_Explorer"></a> Test Gezgini'nde testlerin çalıştığını doğrulama

1. Bazı test kodu ekleme:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     sınıfının test `Assert` yöntemlerinde sonuçları doğrulamak için kullanabileceğiniz çeşitli statik yöntemler sağladığına dikkat etmek.

2. Test menüsünde **Çalıştır'ı** ve **ardından** Hepsini **Çalıştır'ı seçin.**

     Test projesi derleme ve çalıştırma. **Test Gezgini penceresi** görüntülenir ve test Başarılı Testler altında **listelenir.** Pencerenin **en** altındaki Özet bölmesi, seçilen testle ilgili ek ayrıntılar sağlar.

     ![Test Gezgini](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-dll-project-to-the-solution"></a><a name="Add_the_DLL_project_to_the_solution"></a> DLL projesini çözüme ekleme

::: moniker range=">=vs-2019"

Bu **Çözüm Gezgini** çözüm adını seçin. Kısayol menüsünde Ekle'yi **ve ardından** Yeni öğe'yi **Project.** Yeni Dosya **Ekle iletişim Project** Dil'i C++ olarak ayarlayın ve arama kutusuna "DLL" yazın.  Sonuç listesinden Birim Testi Uygulaması **(Evrensel uygulama - C++/CX) Windows 'yi seçin.**

![RooterLib projesini oluşturma](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
Bu **Çözüm Gezgini** çözüm adını seçin. Kısayol menüsünde Ekle'yi **ve ardından** Yeni öğe'yi **Project.**

![RooterLib projesini oluşturma](../test/media/ute_cpp_windows_rooterlib_create.png)

::: moniker-end

1. Yeni Uygulama **Ekle iletişim Project** DLL **(UWP uygulamaları) öğesini seçin.**

2. *RooterLib.h dosyasına aşağıdaki kodu* ekleyin:

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

     Açıklamalar, ifdef bloğuna yalnızca dll'nin geliştiricisini değil, projesinde DLL'ye başvuru yapan herkese de açıklama sağlar. DLL'ROOTERLIB_EXPORTS proje özelliklerini kullanarak komut satırına ROOTERLIB_EXPORTS simgesini ekebilirsiniz.

     sınıfı `CRooterLib` bir oluşturucu ve tahmin yöntemi `SqareRoot` bildirer.

3. Komut ROOTERLIB_EXPORTS simgesi ekleyin.

    1. Bu **Çözüm Gezgini** **RooterLib projesini** seçin ve ardından kısayol **menüsünden** Özellikler'i seçin.

         ![Ön işlemci sembol tanımı ekleme](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. **RooterLib Özellik Sayfası iletişim kutusunda** Yapılandırma Özellikleri'yi genişletin, C++ öğesini genişletin ve Önişlemci'yi  **seçin.**

    3. **\<Edit...>** **Önişlemci Tanımları listesinden** seçin ve ardından Önişlemci `ROOTERLIB_EXPORTS` **Tanımları iletişim** kutusuna ekleyin.

4. Bildirilen işlevlerin en az uygulamasını ekleyin. *RooterLib.cpp'yi* açın ve aşağıdaki kodu ekleyin:

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

## <a name="make-the-dll-functions-visible-to-the-test-code"></a><a name="make_the_dll_functions_visible_to_the_test_code"></a> Dll işlevlerini test koduna görünür hale yükleme

1. RooterLibTests projesine RooterLib ekleyin.

   1. Bu **Çözüm Gezgini** **RooterLibTests projesini** seçin ve ardından kısayol menüsünde   >  **Başvuru** Ekle'yi seçin.

   1. Başvuru Ekle **iletişim kutusunda** Projeler'i **seçin.** Ardından **RouterLib öğesini** seçin.

2. rooterLib üst bilgi dosyasını *unittest1.cpp dosyasına dahil etmek.*

   1. *unittest1.cpp'yi açın.*

   2. Bu kodu satırın altına `#include "CppUnitTest.h"` ekleyin:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. İçe aktarılan işlevi kullanan bir test ekleyin. *Unittest1.cpp'ye aşağıdaki kodu ekleyin:*

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

    Yeni test Test **Gezgini'nde Testleri** **Çalıştırmama düğümünde** görünür.

5. **Test Gezgini'nde,** Hepsini **Çalıştır'ı seçin.**

    ![Temel Testten geçildi](../test/media/ute_cpp_testexplorer_basictest.png)

   Testi ve kod projelerini ayarladıktan sonra kod projesinde işlevleri çalıştıran testleri çalıştırabilirsiniz. Artık gerçek testler ve kod yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="Iteratively_augment_the_tests_and_make_them_pass"></a> Testleri çoğaltarak geliştirin ve başarıyla geçişlerini snın

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
    > Geçen testleri değiştirmenizi önerilmez. Bunun yerine yeni bir test ekleyin, kodu test başarılı olacak şekilde güncelleştirin ve ardından başka bir test ekleyin ve bu şekilde devam ediyor.
    >
    > Kullanıcılarınız gereksinimlerini değiştir yaptıklarında, artık doğru olan testleri devre dışı bırak. Yeni testler yazın ve bunları aynı artımlı şekilde tek tek çalışır hale yazın.

2. **Test Gezgini'nde,** Hepsini **Çalıştır'ı seçin.**

3. Test başarısız olur.

     ![RangeTest başarısız oluyor](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Siz yazdıktan hemen sonra her testin başarısız olduğunu doğrulayın. Bu, hiçbir zaman başarısız olmayacak bir test yazma hatalarından kaçınmanıza yardımcı olur.

4. Yeni testin başarılı olacak şekilde test altındaki kodu geliştirin. *RooterLib.cpp'ye şunları ekleyin:*

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

5. Çözümü derleme ve Test Gezgini'nde **Hepsini** **Çalıştır'ı seçin.**

     Her iki test de geçer.

> [!TIP]
> Her seferinde bir test ekleyerek kod geliştirin. Her yinelemeden sonra tüm testlerin başarılı olduğundan emin olun.

## <a name="debug-a-failing-test"></a><a name="Debug_a_failing_test"></a> Başarısız bir testte hata ayıkla

1. *UnitTest1. cpp* öğesine başka bir test ekleyin:

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

2. **Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin.

    Test başarısız oluyor. **Test Gezgini**'nde test adını seçin. Başarısız onaylama vurgulanır. Hata iletisi, **Test Gezgini**'nin ayrıntı bölmesinde görünür.

    ![Negatiftiverangetests başarısız oldu](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Testin neden başarısız olduğunu görmek için, işlevi adım adım inceleyin:

   1. İşlevin başlangıcında bir kesme noktası ayarlayın `SquareRoot` .

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

## <a name="refactor-the-code-without-changing-tests"></a><a name="Refactor_the_code_without_changing_tests"></a> Testleri değiştirmeden kodu yeniden düzenleme

1. İşlevde merkezi hesaplamayı basitleştirme `SquareRoot` :

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
