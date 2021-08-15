---
title: "Nasıl bilinir: C++ URL'leri için birim testleri yazma"
description: Test-first metodolojisi kullanarak yerel bir C++ DLL'si geliştirmeyi öğrenin. Başlangıç olarak yerel bir test projesi oluşturma.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 9c18bec4b6e25148c23a0e44cff95438322ea20c0cdd6f7aa57079f0cce6d268
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226803"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Nasıl bilinir: C++ URL'leri için birim testleri yazma

Bu kılavuzda, test-first metodolojisi kullanılarak yerel bir C++ DLL'leri geliştirme açıklanır. Temel adımlar aşağıdaki gibidir:

1. [Yerel test projesi oluşturun.](#create_test_project) Test projesi, DLL projesiyle aynı çözümde bulunur.

2. [DLL projesi oluşturun.](#create_dll_project) Bu kılavuz yeni bir DLL oluşturur, ancak var olan bir DLL'i test etme yordamı benzerdir.

3. [DLL işlevlerinin testlere görünür hale gelir.](#make_functions_visible)

4. [Testlerini çoğaltarak geliştirin.](#iterate) Kodun geliştirilmesinin testler tarafından yönlendirilecek bir "kırmızı-yeşil-yeniden düzenleme" döngüsü önerilir.

5. [Başarısız testlerde hata ayıklama.](#debug) Testleri hata ayıklama modunda çalıştırabilirsiniz.

6. [Testleri değiştirmeden yeniden düzenleme.](#refactor) Yeniden düzenleme, dış davranışını değiştirmeden kodun yapısını geliştirmek anlamına gelir. Kodun performansını, genişletilebilirliğini veya okunabilirliğini geliştirmek için bunu yapabiliriz. Amaç davranışı değiştirmek değil, kodda yeniden düzenleme değişikliği yaparken testleri değiştirmezsiniz. Testler, yeniden düzenleme sırasında hatalara neden olmaz.

7. [Kapsamı kontrol edin.](using-code-coverage-to-determine-how-much-code-is-being-tested.md) Birim testleri, kodunuzun daha fazla alıştırması sırasında daha kullanışlıdır. Kodunuzun hangi bölümlerinin testler tarafından kullanılmış olduğunu keşfedebilirsiniz.

8. [Birimleri dış kaynaklardan yalıtmak.](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md) Bir DLL genellikle geliştirmekte olduğunu sistemin diğer bileşenlerine (diğer DLL'ler, veritabanları veya uzak alt sistemler gibi) bağımlıdır. Her birimi bağımlılıklarından yalıtarak test etmek yararlıdır. Dış bileşenler, testlerin yavaş çalışmasına neden olabilir. Geliştirme sırasında diğer bileşenler tamamlanmadı olabilir.

## <a name="create-a-native-unit-test-project"></a><a name="create_test_project"></a> Yerel birim testi projesi oluşturma

1. Dosya menüsünde **Yeni** **dosya'Project.**  >  

     **Visual Studio 2017 ve önceki sürümler:** Test **etmek için**  >  **Yüklü**  >  **Visual C++**  >  **genişletin.**
     **Visual Studio 2019:** **Dil'i** C++ olarak ayarlayın ve arama kutusuna "test" yazın.

     Yerel Birim **Testi Project** şablonunu veya istediğiniz yüklü çerçeveyi seçin. Google Test veya Boost.Test gibi başka bir şablon seçerseniz, bazı ayrıntılar farklı olsa da temel ilkeler aynıdır.

     Bu kılavuzda test projesi olarak `NativeRooterTest` adlandırılmıştır.

2. Yeni projede **unittest1.cpp'yi incele**

     ![TEST&#95;CLASS ve TEST&#95;METODU ile projeyi test](../test/media/utecpp2.png)

     Şunlara dikkat edin:

    - Her test kullanılarak `TEST_METHOD(YourTestName){...}` tanımlanır.

         Geleneksel işlev imzası yazmak zorunda değildir. İmza, makro TEST_METHOD. Makro, void döndüren bir örnek işlevi üretir. Ayrıca test yöntemi hakkında bilgi döndüren statik bir işlev de üretir. Bu bilgiler, test gezgininin yöntemini bulmasını sağlar.

    - Test yöntemleri kullanılarak sınıflara `TEST_CLASS(YourClassName){...}` gruplandı.

         Testler çalıştırılan her test sınıfının bir örneği oluşturulur. Test yöntemleri belirtilmemiş bir sırada çağrılır. Her modülden, sınıftan veya yöntemden önce ve sonra çağrılan özel yöntemler tanımlayabilirsiniz.

3. Test Gezgini'nde testlerin çalıştığını doğrulayın:

    1. Bazı test kodu ekleme:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         sınıfının test `Assert` yöntemlerinde sonuçları doğrulamak için kullanabileceğiniz çeşitli statik yöntemler sağladığına dikkat etmek.

    2. Test menüsünde **Tüm** Testleri   >  **Çalıştır'ı seçin.**

         Test derlemelerini ve çalıştırmalarını sağlar.

         **Test Gezgini** görüntülenir.

         Test, Başarılı Testler **altında görünür.**

         ![Tek bir geçmiş test ile Birim Testi Gezgini](../test/media/utecpp04.png)

## <a name="create-a-dll-project"></a><a name="create_dll_project"></a> DLL projesi oluşturma

::: moniker range=">=vs-2019"

Aşağıdaki adımlar, 2019'da dll Visual Studio gösterir.

1. **Windows Masaüstü** Sihirbazı'nı kullanarak bir C++ projesi oluşturun: Çözüm Gezgini'de çözüm adına sağ tıklayın ve **Project.**  >   **Dil'i** C++ olarak ayarlayın ve arama kutusuna "windows" yazın. Sonuçlar **Windows Masaüstü Sihirbazı'nı** seçin.

     Bu kılavuzda proje olarak `RootFinder` adlandırılmıştır.

2. **Oluştur**’a basın. Sonraki iletişim kutusunda, Uygulama türü altında **Dinamik Bağlantı** Kitaplığı **(dll) öğesini seçin** ve ayrıca Sembolleri Dışarı **Aktar'ı seçin.**

     Sembolleri **Dışarı Aktar** seçeneği, dışarı aktaran yöntemleri bildirebilirsiniz kullanışlı bir makro üretir.

     ![DLL ve Dışarı Aktarma Sembolleri için C++ proje sihirbazı kümesi](../test/media/vs-2019/windows-desktop-project-dll.png)

3. Asıl *.h* dosyasında dışarı aktaran bir işlev bildir:

     ![API makroları ile yeni DLL kod projesi ve .h dosyası](../test/media/utecpp07.png)

     Bildirimleyici, `__declspec(dllexport)` sınıfın ortak ve korumalı üyelerinin DLL dışında görünür olmasına neden olur. Daha fazla bilgi için bkz. C++ Sınıflarında [dllimport ve dllexport kullanma.](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes)

4. Sorumlu *.cpp dosyasında* işlev için en küçük bir gövde ekleyin:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

::: moniker range="vs-2017"

Aşağıdaki adımlar, 2017'de bir DLL Visual Studio gösterir.

1. Win32 Project kullanarak **bir C++ projesi** oluşturun.

     Bu kılavuzda proje olarak `RootFinder` adlandırılmıştır.

2. Win32 **Uygulama Sihirbazı'nda** **DLL** ve Dışarı Aktarma Sembolleri'ni seçin.

     Sembolleri **Dışarı Aktar** seçeneği, dışarı aktaran yöntemleri bildirebilirsiniz kullanışlı bir makro üretir.

     ![DLL ve Dışarı Aktarma Sembolleri için C++ proje sihirbazı kümesi](../test/media/utecpp06.png)

3. Asıl *.h* dosyasında dışarı aktaran bir işlev bildir:

     ![API makroları ile yeni DLL kod projesi ve .h dosyası](../test/media/utecpp07.png)

     Bildirimleyici, `__declspec(dllexport)` sınıfın ortak ve korumalı üyelerinin DLL dışında görünür olmasına neden olur. Daha fazla bilgi için bkz. C++ Sınıflarında [dllimport ve dllexport kullanma.](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes)

4. Sorumlu *.cpp dosyasında* işlev için en küçük bir gövde ekleyin:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="make_functions_visible"></a> Test projesini DLL projesiyle birlikte kullanın

1. DLL projesini test projesinin proje başvurularını ekleyin:

   1. Içinde test projesi düğümüne sağ tıklayın ve **Çözüm Gezgini** **Ekle'yi**  >  **seçin.**

   2. Başvuru Ekle **iletişim kutusunda** DLL projesini seçin ve Ekle'yi **seçin.**

        ![C++ proje özellikleri | Yeni Başvuru Ekle](../test/media/utecpp09.png)

2. Asıl birim testi *.cpp dosyasına* DLL *kodunun .h* dosyasını ekleyin:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Dışarı aktaran işlevi kullanan temel bir test ekleyin:

   ```cpp
   TEST_METHOD(BasicTest)
   {
      CRootFinder rooter;
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

    Yeni test Test **Gezgini'nde görünür.**

5. **Test Gezgini'nde,** Hepsini **Çalıştır'ı seçin.**

    ![Temel Test &#45; Birim Testi Gezgini](../test/media/utecpp10.png)

   Testi ve kod projelerini ayarladıktan sonra kod projesinde işlevleri çalıştıran testleri çalıştırabilirsiniz. Artık gerçek testler ve kod yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a> Testleri çoğaltarak geliştirin ve başarıyla geçişlerini snın

1. Yeni bir test ekleyin:

    ```cpp
    TEST_METHOD(RangeTest)
    {
      CRootFinder rooter;
      for (double v = 1e-6; v < 1e6; v = v * 3.2)
      {
        double actual = rooter.SquareRoot(v*v);
        Assert::AreEqual(v, actual, v/1000);
      }
    }
    ```

    > [!TIP]
    > Geçen testleri değiştirmenizi önerilmez. Bunun yerine, yeni bir test ekleyin, kodu test başarılı olacak şekilde güncelleştirin ve ardından başka bir test ekleyin ve bu şekilde devam ediyor.
    >
    > Kullanıcılarınız gereksinimlerini değiştir yaptıklarında, artık doğru olan testleri devre dışı bırak. Yeni testler yazın ve bunları aynı artımlı şekilde tek tek çalışır hale yazın.

2. Çözümü derleme ve Test Gezgini'nde **Hepsini** **Çalıştır'ı seçin.**

     Yeni test başarısız oluyor.

     ![RangeTest başarısız oluyor](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Siz yazdıktan hemen sonra her testin başarısız olduğunu doğrulayın. Bu, hiçbir zaman başarısız olmayacak bir test yazma hatalarından kaçınmanıza yardımcı olur.

3. DLL kodunuzu yeni testin başarılı olacak şekilde geliştirin:

    ```cpp
    #include <math.h>
    ...
    double CRootFinder::SquareRoot(double v)
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

4. Çözümü derleme ve Test Gezgini'nde **Hepsini** **Çalıştır'ı seçin.**

     Her iki test de geçer.

     ![Birim Testi Gezgini &#45; Aralık Testi geçirildi](../test/media/utecpp12.png)

    > [!TIP]
    > Testleri tek tek ekleyerek kod geliştirin. Tüm testlerin her yinelemeden sonra başarılı olduğundan emin olun.

## <a name="debug-a-failing-test"></a><a name="debug"></a> Başarısız olan testte hata ayıklama

1. Başka bir test ekleyin:

    ```cpp
    #include <stdexcept>
    ...
    // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRootFinder rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          _swprintf(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          _swprintf(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
    }
    ```

2. Çözümü derleme ve Hepsini **Çalıştır'ı seçin.**

3. Başarısız olan testi açın (veya çift tıklayın).

     Başarısız onay vurgulanmış. Hata iletisi Test Gezgini'nin ayrıntı bölmesinde **görünür.**

     ![NegativeRangeTests başarısız oldu](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4. Testin neden başarısız olduğunu görmek için işlevin üzerinden geçin:

    1. SquareRoot işlevinin başında bir kesme noktası ayarlayın.

    2. Başarısız testin kısayol menüsünde Seçili Testlerde **Hata Ayıkla'yı seçin.**

         Çalıştırma kesme noktası içinde durduğunda kodun üzerinden geçin.

5. Geliştirmekte olduğu işleve kod ekleme:

    ```cpp

    #include <stdexcept>
    ...
    double CRootFinder::SquareRoot(double v)
    {
        // Validate parameter:
        if (v < 0.0)
        {
          throw std::out_of_range("Can't do square roots of negatives");
        }

    ```

6. Tüm testler artık başarılı olur.

   ![Tüm testler başarılı](../test/media/ute_ult_alltestspass.png)

::: moniker range="vs-2017"

> [!TIP]
> Tek tek testlerin herhangi bir sırada çalışmasına engel olan bağımlılıkları yoksa, Test Gezgini araç çubuğundaki paralel test yürütme iki durumlu düğmesinin ekran görüntüsü ile paralel ![ test yürütmeyi açın. Bu düğme seçildiğinde testler paralel olarak çalıştırıldığında.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğmeyi seçin. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Tek tek testlerin herhangi bir sırada çalışmasına engel olan bağımlılıklar yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütmeyi açın. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.

::: moniker-end

## <a name="refactor-the-code-without-changing-tests"></a><a name="refactor"></a> Testleri değiştirmeden kodu yeniden düzenleme

1. SquareRoot işlevinde merkezi hesaplamayı basitleştirin:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Çözümü derlemek ve **Hata oluşturmamadan** emin olmak için Hepsini Çalıştır'ı seçin.

    > [!TIP]
    > İyi bir birim testi kümesi, kodu değiştirirken hatalara neden olmadığınız için güven verir.
    >
    > Yeniden düzenlemeyi diğer değişikliklerden ayrı tutma.

## <a name="next-steps"></a>Sonraki adımlar

- **Yalıtım.** Çoğu URL, veritabanları ve diğer URL'ler gibi diğer alt sistemlere bağımlıdır. Bu diğer bileşenler genellikle paralel olarak geliştiriliyor. Diğer bileşenler henüz kullanılabilirken birim testinin gerçekleştirilmesi için sahte veya

- **Doğrulama Testleri Oluşturma.** Testlerinizi belirli aralıklarla takımınız derleme sunucusunda gerçekleştirebilirsiniz. Bu, birkaç ekip üyesinin işi tümleştirildiklerinden hataların ortaya çıktımalarını sağlar.

- **Testleri iade edin.** Her ekip üyesi kodu kaynak denetimine denetlemeden önce bazı testlerin gerçekleştiriliyor olması zorunlu kılınabilir. Genellikle bu, derleme doğrulama testlerinin tam kümesinin bir alt kümesidir.

   Ayrıca, en düşük kod kapsamı düzeyini zorunlu bulundurabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut C++ uygulamalarına birim testleri ekleme](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Microsoft.VisualStudio.TestTools.CppUnitTestFramework Kullanma](how-to-use-microsoft-test-framework-for-cpp.md)
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [İzlenecek yol: Dinamik bağlantı kitaplığı oluşturma ve kullanma (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [İçeri ve dışarı aktarma](/cpp/build/importing-and-exporting)
