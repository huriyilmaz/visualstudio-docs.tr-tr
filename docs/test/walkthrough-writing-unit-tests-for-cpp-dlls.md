---
title: "Nasıl yapılır: C++ dll 'Leri için birim testleri yazma"
description: Test-First yöntemini kullanarak yerel C++ DLL geliştirmeyi öğrenin. Yerel bir test projesi oluşturarak başlayın.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 2d145e1383e8f6c0d7c25ae72232fdbe2a8d703d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727547"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Nasıl yapılır: C++ dll 'Leri için birim testleri yazma

Bu izlenecek yol, test-First yöntemini kullanarak yerel C++ DLL 'nin nasıl geliştirileceği açıklanmaktadır. Temel adımlar aşağıdaki gibidir:

1. [Yerel bir test projesi oluşturun](#create_test_project). Test projesi, DLL projesiyle aynı çözümde bulunur.

2. [BIR DLL projesi oluşturun](#create_dll_project). Bu izlenecek yol yeni bir DLL oluşturur, ancak var olan bir DLL 'yi test etme yordamı benzerdir.

3. [DLL işlevlerini testlere görünür hale getirin](#make_functions_visible).

4. [Testleri](#iterate)yinelemeli olarak güçlendirin. Kodun geliştirilmesi testlerin yaptığı bir "kırmızı yeşil-yeniden düzenleme" döngüsünün kullanılması önerilir.

5. [Başarısız testlerde hata ayıklayın](#debug). Testleri hata ayıklama modunda çalıştırabilirsiniz.

6. [Testleri değişmeden tutarken yeniden düzenleme](#refactor). Yeniden düzenleme, dış davranışını değiştirmeden kodun yapısını iyileştirmek anlamına gelir. Bu kodu, kodun performansını, genişletilebilirliğini veya okunabilirliğini geliştirmek için yapabilirsiniz. Amaç, davranışı değiştirmediğinden, kodda yeniden düzenleme değişikliği yaparken testleri değiştirmeyin. Testler, yeniden düzenleme sırasında hata tanıtmadığınızdan emin olmanıza yardımcı olur.

7. [Kapsama bakın](using-code-coverage-to-determine-how-much-code-is-being-tested.md). Birim testleri, kodunuzun daha fazlasını yaparken daha kullanışlı olur. Kodunuzun hangi bölümlerinin test tarafından kullanıldığını keşfedebilirsiniz.

8. [Birimleri dış kaynaklardan yalıtın](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). Genellikle, bir DLL, diğer dll 'Ler, veritabanları veya uzak alt sistemler gibi geliştirmekte olduğunuz sistem bileşenlerine bağımlıdır. Her birimi bağımlılıklarından yalıtılmış olarak test etmek yararlı olur. Dış bileşenler, testlerin yavaş çalışmasını sağlayabilir. Geliştirme sırasında diğer bileşenler tamamlanmamış olabilir.

## <a name="create-a-native-unit-test-project"></a><a name="create_test_project"></a> Yerel birim testi projesi oluştur

1. **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.

     **Visual Studio 2017 ve önceki sürümler**: **yüklü**  >  **Şablonlar**  >  **Visual C++**  >  **Test**' i genişletin.
     **Visual Studio 2019**: **dili** C++ olarak ayarlayın ve arama kutusuna "test" yazın.

     **Yerel birim testi proje** şablonunu veya tercih ettiğiniz yüklü çerçeveyi seçin. Google Test veya Boost. test gibi başka bir şablon seçerseniz, bazı ayrıntılar farklı olsa da temel ilkeler aynı olur.

     Bu izlenecek yolda, test projesi adlandırılır `NativeRooterTest` .

2. Yeni projede, **UnitTest1. cpp** ' yi inceleyin

     ![Test&#95;sınıfı ve TEST&#95;YÖNTEMIYLE test projesi](../test/media/utecpp2.png)

     Şunlara dikkat edin:

    - Her test kullanılarak tanımlanır `TEST_METHOD(YourTestName){...}` .

         Geleneksel bir işlev imzası yazmanız gerekmez. İmza, makro TEST_METHOD tarafından oluşturulur. Makro, void döndüren bir örnek işlevi oluşturur. Ayrıca test yöntemiyle ilgili bilgileri döndüren statik bir işlev oluşturur. Bu bilgiler, test Gezgini 'nin yöntemi bulmasını sağlar.

    - Test yöntemleri kullanılarak sınıflar halinde gruplandırılır `TEST_CLASS(YourClassName){...}` .

         Testler çalıştırıldığında, her bir test sınıfının bir örneği oluşturulur. Test yöntemleri belirtilmemiş bir sırada çağırılır. Her modül, sınıf veya yöntemden önce ve sonra çağrılan özel yöntemler tanımlayabilirsiniz.

3. Testin test Gezgini 'nde çalıştığını doğrulayın:

    1. Bir test kodu ekleyin:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         `Assert`Sınıfının, test yöntemlerinde sonuçları doğrulamak için kullanabileceğiniz çeşitli statik yöntemler sağladığını unutmayın.

    2. **Test** menüsünde   >  **tüm testleri** Çalıştır ' ı seçin.

         Test derlemeleri ve çalıştırmaları.

         **Test Gezgini** görüntülenir.

         Test **geçilen testler** altında görünür.

         ![Başarılı bir test ile birim test Gezgini](../test/media/utecpp04.png)

## <a name="create-a-dll-project"></a><a name="create_dll_project"></a> DLL projesi oluşturma

::: moniker range="vs-2019"

Aşağıdaki adımlarda, Visual Studio 2019 ' de bir DLL projesi oluşturma gösterilmektedir.

1. **Windows Masaüstü Sihirbazı 'nı** kullanarak bir C++ projesi oluşturma: **Çözüm Gezgini** çözüm adına sağ tıklayın ve   >  **Yeni proje** Ekle ' yi seçin. **Dili** C++ olarak ayarlayın ve arama kutusuna "Windows" yazın. Sonuçlar listesinden **Windows Masaüstü Sihirbazı** ' nı seçin.

     Bu kılavuzda, proje adlandırılır `RootFinder` .

2. **Oluştur**’a basın. Sonraki iletişim kutusunda, **uygulama türü** altında **dinamik bağlantı kitaplığı (dll)** öğesini seçin ve ayrıca **sembolleri dışarı aktar**' ı işaretleyin.

     **Sembolleri dışarı aktar** seçeneği, dışarı aktarılmış yöntemleri bildirmek için kullanabileceğiniz, kullanışlı bir makro oluşturur.

     ![DLL ve dışa aktarma sembolleri için C++ proje Sihirbazı ayarlandı](../test/media/vs-2019/windows-desktop-project-dll.png)

3. Principal *. h* dosyasında bir dışarıya aktarılmış işlev bildirin:

     ![API makroları ile yeni DLL kod projesi ve. h dosyası](../test/media/utecpp07.png)

     Bildirimci, `__declspec(dllexport)` sınıfın genel ve korumalı ÜYELERININ dll dışında görünür olmasına neden olur. Daha fazla bilgi için bkz. [C++ sınıflarında dllimport ve dllexport kullanma](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. Principal *. cpp* dosyasında, işlev için en az bir gövde ekleyin:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

::: moniker range="vs-2017"

Aşağıdaki adımlarda, Visual Studio 2017 ' de bir DLL projesi oluşturma gösterilmektedir.

1. **Win32 Proje** şablonunu kullanarak bir C++ projesi oluşturun.

     Bu kılavuzda, proje adlandırılır `RootFinder` .

2. Win32 uygulama Sihirbazı 'nda **DLL** 'yi seçin ve **sembolleri dışarı aktarın** .

     **Sembolleri dışarı aktar** seçeneği, dışarı aktarılmış yöntemleri bildirmek için kullanabileceğiniz, kullanışlı bir makro oluşturur.

     ![DLL ve dışa aktarma sembolleri için C++ proje Sihirbazı ayarlandı](../test/media/utecpp06.png)

3. Principal *. h* dosyasında bir dışarıya aktarılmış işlev bildirin:

     ![API makroları ile yeni DLL kod projesi ve. h dosyası](../test/media/utecpp07.png)

     Bildirimci, `__declspec(dllexport)` sınıfın genel ve korumalı ÜYELERININ dll dışında görünür olmasına neden olur. Daha fazla bilgi için bkz. [C++ sınıflarında dllimport ve dllexport kullanma](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. Principal *. cpp* dosyasında, işlev için en az bir gövde ekleyin:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="make_functions_visible"></a> DLL projesine test projesi için birkaç

1. DLL projesini test projesinin proje başvurularına ekleyin:

   1. **Çözüm Gezgini** ' deki test projesi düğümüne sağ tıklayın ve başvuru **Ekle**' yi seçin  >  .

   2. **Başvuru Ekle** iletişim kutusunda, DLL projesini seçin ve **Ekle**' yi seçin.

        ![C++ proje özellikleri | Yeni Başvuru Ekle](../test/media/utecpp09.png)

2. Asıl birim testi *. cpp* dosyasında, dll kodunun *. h* dosyasını dahil edin:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. İçe aktarılmış işlevi kullanan temel bir test ekleyin:

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

    Yeni test, **Test Gezgini**'nde görünür.

5. **Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin.

    ![Temel test &#45; birim test Gezgini geçildi](../test/media/utecpp10.png)

   Test ve kod projelerini ayarlamış ve kod projesindeki işlevleri çalıştıran testleri çalıştıracağınızı doğruladınız. Artık gerçek testleri ve kodu yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a> Testleri tekrarlayarak ve geçiş yapın

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
    > Geçilen testleri değiştirmenizi öneririz. Bunun yerine, yeni bir test ekleyin, kodu test geçişi olacak şekilde güncelleştirin ve daha sonra başka bir test ekleyin ve bu şekilde devam edin.
    >
    > Kullanıcılarınız gereksinimlerini değiştirmelerine göre artık doğru olmayan Testleri devre dışı bırakın. Yeni testler yazın ve aynı anda bir kez, aynı şekilde çalışır hale getirin.

2. Çözümü oluşturun ve ardından **Test Gezgini**' nde **Tümünü Çalıştır**' ı seçin.

     Yeni test başarısız olur.

     ![RangeTest başarısız oluyor](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Her testin yazıldıktan hemen sonra başarısız olduğunu doğrulayın. Bu, hiç başarısız olmayan bir testi yazmanın kolay bir hata yaşamadan kaçınmanıza yardımcı olur.

3. Yeni testin başarılı olması için DLL kodunuzu geliştirin:

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

4. Çözümü derleyin ve ardından **Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin.

     Her iki test de geçer.

     ![Birim test Gezgini &#45; Aralık testi geçildi](../test/media/utecpp12.png)

    > [!TIP]
    > Her seferinde bir test ekleyerek kod geliştirin. Her yinelemeden sonra tüm testlerin başarılı olduğundan emin olun.

## <a name="debug-a-failing-test"></a><a name="debug"></a> Başarısız bir testte hata ayıkla

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

2. Çözümü derleyin ve **Tümünü Çalıştır**' ı seçin.

3. Başarısız testi açın (veya çift tıklatın).

     Başarısız onaylama vurgulanır. Hata iletisi, **Test Gezgini**'nin ayrıntı bölmesinde görünür.

     ![Negatiftiverangetests başarısız oldu](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4. Testin neden başarısız olduğunu görmek için, işlevi adım adım inceleyin:

    1. SquareRoot işlevinin başlangıcında bir kesme noktası ayarlayın.

    2. Başarısız testin kısayol menüsünde, **Seçili testlerin hatalarını ayıkla**' yı seçin.

         Çalıştırma kesme noktasında durdurulduğunda kodda adım adım ilerleyin.

5. Geliştirdiğiniz işleve kod ekleyin:

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

6. Şimdi tüm testler geçer.

   ![Tüm testler geçer](../test/media/ute_ult_alltestspass.png)

::: moniker range="vs-2017"

> [!TIP]
> Bireysel testlerin herhangi bir sırada çalıştırılmasını engelleyen bir bağımlılığı yoksa, ![ Test Gezgini araç çubuğundaki paralel test yürütme geçiş düğmesi ekran görüntüsü ile paralel test yürütmeyi açın. Bu düğme seçildiğinde, testler paralel olarak çalışır.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Bireysel testlerin herhangi bir sırada çalıştırılmasını engelleyen bir bağımlılığı yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütme ' yi açın. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.

::: moniker-end

## <a name="refactor-the-code-without-changing-tests"></a><a name="refactor"></a> Testleri değiştirmeden kodu yeniden düzenleme

1. SquareRoot işlevinde merkezi hesaplamayı kolaylaştırın:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Bir hata sunduğunuzdan emin olmak için çözümü derleyin ve **Tümünü Çalıştır**' ı seçin.

    > [!TIP]
    > Uygun bir birim testi kümesi, kodu değiştirirken hata sunmaabileceğinizden emin olmanızı sağlar.
    >
    > Yeniden düzenlemeyi diğer değişikliklerden ayrı tutun.

## <a name="next-steps"></a>Sonraki adımlar

- **Yalıtımı.** Çoğu dll veritabanları ve diğer dll 'Ler gibi diğer alt sistemlere bağımlıdır. Bu diğer bileşenler genellikle paralel olarak geliştirilmiştir. Diğer bileşenler henüz kullanılamadığı sürece birim testi gerçekleştirilmesine izin vermek için, sahte veya

- **Derleme doğrulama testleri.** Ekip oluşturma sunucusunda, belirlenen aralıklarda testlerin gerçekleştirilmesini sağlayabilirsiniz. Bu, birkaç takım üyesinin çalışması tümleştirildiğinde hataların tanıtılmamasını sağlar.

- **İade testleri.** Her bir takım üyesinin, kaynak denetimine kodu denetlemesi için bazı testlerin gerçekleştirilmesini zorunlu hale getirebilirsiniz. Genellikle bu, tüm yapı doğrulama testleri kümesinin bir alt kümesidir.

   Ayrıca, en düşük kod kapsamı düzeyini de kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut C++ uygulamalarına birim testleri ekleme](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Microsoft.VisualStudio.TestTools.CppUnitTestFramework Kullanma](how-to-use-microsoft-test-framework-for-cpp.md)
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [İzlenecek yol: Dinamik bağlantı kitaplığı oluşturma ve kullanma (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [İçeri ve dışarı aktarma](/cpp/build/importing-and-exporting)
