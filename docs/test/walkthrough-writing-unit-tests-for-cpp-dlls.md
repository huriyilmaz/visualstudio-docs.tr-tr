---
title: "Nasıl kullanılır: C++ DL'ler için birim testleri yazma"
ms.date: 06/13/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 752a2bb53e25954824a1400ee178cd0cbf4adcf2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275428"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Nasıl kullanılır: C++ DL'ler için birim testleri yazma

Bu izleme, test-ilk metodolojisi kullanarak yerel bir C++ DLL'nin nasıl geliştirilebildiğini açıklar. Temel adımlar aşağıdaki gibidir:

1. [Yerel bir test projesi oluşturun.](#create_test_project) Test projesi, DLL projesiyle aynı çözümde yer alır.

2. [Bir DLL projesi oluşturun.](#create_dll_project) Bu izlik yeni bir DLL oluşturur, ancak varolan bir DLL'yi sınamaya yönelik yordam benzerdir.

3. [DLL işlevlerini testlere görünür hale getirin.](#make_functions_visible)

4. [Yinelemeli testleri artırmak](#iterate). Kodun geliştirilmesinin testler tarafından yürütüldürün yürütüldüğü bir "kırmızı- yüz- refactor" dünyasını öneririz.

5. [Hata ayıklama başarısız testleri](#debug). Hata ayıklama modunda testler çalıştırabilirsiniz.

6. [Testleri değiştirmeden tutarken yeniden düzenleme.](#refactor) Yeniden düzenleme, dış davranışını değiştirmeden kodun yapısını iyileştirmek anlamına gelir. Kodun performansını, genişletilebilirliğini veya okunabilirliğini artırmak için bunu yapabilirsiniz. Amaç davranışı değiştirmek olmadığından, kodda yeniden düzenleme değişikliği yaparken testleri değiştirmezsiniz. Testler, yeniden düzenleme yaparken hataları tanıtmadığınızdan emin olun.

7. [Kapsamı kontrol edin.](using-code-coverage-to-determine-how-much-code-is-being-tested.md) Birim testleri, kodunuzu daha fazla kullandıklarında daha kullanışlıdır. Kodunuzun hangi bölümlerinin testler tarafından kullanıldığını keşfedebilirsiniz.

8. [Birimleri dış kaynaklardan yalıt.](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md) Genellikle, Bir DLL, geliştirdiğiniz sistemin diğer DL'ler, veritabanları veya uzak alt sistemler gibi diğer bileşenlerine bağlıdır. Her üniteyi bağımlılıklarından izole olarak test etmek yararlıdır. Dış bileşenler testlerin yavaş çalışmasını sağlayabilir. Geliştirme sırasında, diğer bileşenler tamamlanmamış olabilir.

## <a name="create-a-native-unit-test-project"></a><a name="create_test_project"></a>Yerel birim test projesi oluşturma

1. **Dosya** menüsünde **Yeni** > **Proje'yi**seçin.

     **Visual Studio 2017 ve önceki**: **Yüklü** > **Şablonları** > Genişlet**Görsel C++** > **Testi**.
     **Visual Studio 2019**: **Dili** C++ olarak ayarlayın ve arama kutusuna "test" yazın.

     Yerel **Birim Test Projesi** şablonu veya istediğiniz yüklü çerçeveyi seçin. Google Test veya Boost.Test gibi başka bir şablon seçerseniz, bazı ayrıntılar farklı olsa da temel ilkeler aynıdır.

     Bu izbin de, test `NativeRooterTest`projesinin adı .

2. Yeni projede **unittest1.cpp'yi** inceleyin

     ![TEST&#95;SINIF ve TEST&#95;YÖNTEMİ test projesi](../test/media/utecpp2.png)

     Şuna dikkat edin:

    - Her test kullanılarak `TEST_METHOD(YourTestName){...}`tanımlanır.

         Geleneksel bir işlev imzası yazmak zorunda değildir. İmza makro TEST_METHOD tarafından oluşturulur. Makro, geçersiz dönen bir örnek işlevi oluşturur. Ayrıca, test yöntemi hakkında bilgi döndüren statik bir işlev de oluşturur. Bu bilgiler, test gezgininin yöntemi bulmasını sağlar.

    - Test yöntemleri kullanılarak `TEST_CLASS(YourClassName){...}`sınıflara gruplandırılır.

         Testler çalıştırıldığında, her test sınıfının bir örneği oluşturulur. Test yöntemleri belirtilmemiş bir sırada çağrılır. Her modülden, sınıftan veya yöntemden önce ve sonra çağrılan özel yöntemler tanımlayabilirsiniz.

3. Testlerin Test Gezgini'nde çalıştırıldığını doğrulayın:

    1. Bazı test kodu ekleyin:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Sınıfın, `Assert` test yöntemleriyle sonuçları doğrulamak için kullanabileceğiniz birkaç statik yöntem sağladığına dikkat edin.

    2. **Test** menüsünde Tüm Testleri **Çalıştır'ı** > **All Tests**seçin.

         Test oluşturur ve çalışır.

         **Test Gezgini** görüntülenir.

         Test, Geçti **Testleri**altında görünür.

         ![Bir test ile Unit Test Explorer](../test/media/utecpp04.png)

## <a name="create-a-dll-project"></a><a name="create_dll_project"></a>Bir DLL projesi oluşturma

::: moniker range="vs-2019"

Aşağıdaki adımlar Visual Studio 2019'da nasıl bir DLL projesi oluşturulacağını göstermektedir.

1. **Windows Masaüstü Sihirbazı'nı**kullanarak bir C++ projesi oluşturun : **Solution Explorer'da** çözüm adına sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin. **Dil'i** C++ olarak ayarlayın ve ardından arama kutusuna "windows" yazın. Sonuçlar listesinden **Windows Masaüstü Sihirbazı'nı** seçin.

     Bu gözden geçirme de, `RootFinder`proje adı .

2. **Oluştur**’a basın. Sonraki iletişim kutusunda, **Uygulama türü** altında **Dinamik Bağlantı Kitaplığı 'nı (dll)** seçin ve Ayrıca **Dışa Aktarma Simgelerini**denetleyin.

     **Dışa Aktarma Sembolleri** seçeneği, dışa aktarılan yöntemleri bildirmek için kullanabileceğiniz kullanışlı bir makro oluşturur.

     ![DLL ve Dışa Aktarma Sembolleri için C++ proje sihirbazı kümesi](../test/media/vs-2019/windows-desktop-project-dll.png)

3. Ana *.h* dosyasında dışa aktarılan bir işlevi bildirin:

     ![API makroları ile yeni DLL kodu projesi ve .h dosyası](../test/media/utecpp07.png)

     Bildirimci, `__declspec(dllexport)` sınıfın genel ve korumalı üyelerinin DLL dışında görünür olmasını neden olur. Daha fazla bilgi için [c++ sınıflarında dllimport ve dllexport'u kullanma'ya](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes)bakın.

4. Ana *.cpp* dosyasında, işlev için en az gövde ekleyin:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

::: moniker range="vs-2017"

Aşağıdaki adımlar Visual Studio 2017'de nasıl bir DLL projesi oluşturulacağını göstermektedir.

1. **Win32 Project** şablonu kullanarak bir C++ projesi oluşturun.

     Bu gözden geçirme de, `RootFinder`proje adı .

2. Win32 Uygulama Sihirbazı'nda **DLL** ve **Dışa Aktar Simgelerini** seçin.

     **Dışa Aktarma Sembolleri** seçeneği, dışa aktarılan yöntemleri bildirmek için kullanabileceğiniz kullanışlı bir makro oluşturur.

     ![DLL ve Dışa Aktarma Sembolleri için C++ proje sihirbazı kümesi](../test/media/utecpp06.png)

3. Ana *.h* dosyasında dışa aktarılan bir işlevi bildirin:

     ![API makroları ile yeni DLL kodu projesi ve .h dosyası](../test/media/utecpp07.png)

     Bildirimci, `__declspec(dllexport)` sınıfın genel ve korumalı üyelerinin DLL dışında görünür olmasını neden olur. Daha fazla bilgi için [c++ sınıflarında dllimport ve dllexport'u kullanma'ya](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes)bakın.

4. Ana *.cpp* dosyasında, işlev için en az gövde ekleyin:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="make_functions_visible"></a>DLL projesine çift test projesi

1. Test projesinin proje başvurularına DLL projesini ekleyin:

   1. **Çözüm Gezgini'ndeki** test proje düğümüne sağ tıklayın ve**Başvuru** **Ekle'yi** > seçin.

   2. Başvuru **Ekle** iletişim kutusunda, DLL projesini seçin ve **Ekle'yi**seçin.

        ![C++ proje özellikleri | Yeni Başvuru Ekle](../test/media/utecpp09.png)

2. Ana birim testi *.cpp* dosyasında, DLL kodunun *.h* dosyasını ekleyin:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Dışa aktarılan işlevi kullanan temel bir test ekleyin:

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

    Yeni test Test **Gezgini'nde**görünür.

5. **Test Gezgini'nde,** **Tümlerini Çalıştır'ı**seçin.

    ![Ünite Test Explorer &#45; Temel Testi geçti](../test/media/utecpp10.png)

   Testi ve kod projelerini ayarladınız ve kod projesinde işlevleri çalıştıran testleri çalıştırabileceğinizi doğruladınız. Şimdi gerçek testler ve kod yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a>Testleri yinelemeli bir şekilde artırın ve geçmelerini

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
    > Geçen testleri değiştirmemenizi öneririz. Bunun yerine, yeni bir test ekleyin, testi geçsin diye kodu güncelleştirin ve sonra başka bir test ekleyin ve benzerlerini ekleyin.
    >
    > Kullanıcılarınız gereksinimlerini değiştirdiğinde, artık doğru olmayan testleri devre dışı bırakın. Yeni testler yazın ve aynı artımlı şekilde teker teker çalışmasını sağlayabilir.

2. Çözümü oluşturun ve ardından **Test Gezgini'nde** **Tümlerini Çalıştır'ı**seçin.

     Yeni test başarısız olur.

     ![RangeTest başarısız olur](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Her testin siz yazdıktan hemen sonra başarısız olduğunu doğrulayın. Bu, asla başarısız olmayan bir test yazmanın kolay hatasını önlemenize yardımcı olur.

3. Yeni testin geçmesi için DLL kodunuzu geliştirin:

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

4. Çözümü oluşturun ve ardından **Test Gezgini'nde** **Tümlerini Çalıştır'ı**seçin.

     Her iki test de geçer.

     ![Ünite Test Explorer &#45; Aralık Testi geçti](../test/media/utecpp12.png)

    > [!TIP]
    > Testleri teker teker ekleyerek kod geliştirin. Tüm testlerin her yinelemeden sonra geçtiğinden emin olun.

## <a name="debug-a-failing-test"></a><a name="debug"></a>Başarısız bir testi hata ayıklama

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

2. Çözümü oluşturun ve **Tümlerini Çalıştır'ı**seçin.

3. Başarısız testi açın (veya çift tıklatın).

     Başarısız iddia vurgulanır. Hata iletisi **Test Gezgini'nin**ayrıntı bölmesinde görünür.

     ![NegativeRangeTests başarısız oldu](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4. Testin neden başarısız olduğunu görmek için işlevden geçin:

    1. SquareRoot işlevinin başında bir kesme noktası ayarlayın.

    2. Başarısız olan testin kısayol menüsünde **Hata Ayıklama Seçili Testleri'ni**seçin.

         Çalıştırma kesme noktasında durduğunda, kodu niçin geç.

5. Geliştirmekte olduğunuz işleve kod ekleyin:

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

6. Tüm testler artık geçti.

   ![Tüm testler geçer](../test/media/ute_ult_alltestspass.png)

::: moniker range="vs-2017"

> [!TIP]
> Tek tek testlerin herhangi bir sırada çalıştırılmalarını engelleyen bağımlılıkları yoksa, ![araç çubuğundaki](../test/media/ute_parallelicon-small.png) küçük geçiş düğmesi&#45;UTE&#95;parallelicon ile paralel test yürütmeyi açın. Bu, tüm testleri çalıştırmak için geçen süreyi belirgin bir şekilde azaltabilir.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Tek tek testlerin herhangi bir sırada çalıştırılmalarını engelleyen bağımlılıkları yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütmesini açın. Bu, tüm testleri çalıştırmak için geçen süreyi belirgin bir şekilde azaltabilir.

::: moniker-end

## <a name="refactor-the-code-without-changing-tests"></a><a name="refactor"></a>Testleri değiştirmeden kodu yeniden düzenleme

1. SquareRoot işlevindeki merkezi hesaplamayı basitleştirin:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Çözümü oluşturun ve bir hata getirmediğinizden emin olmak için **Tümlerini Çalıştır'ı**seçin.

    > [!TIP]
    > İyi bir birim testi kümesi, kodu değiştirdiğinizde hataları tanıtmadığınıza dair güven verir.
    >
    > Yeniden düzenlemeyi diğer değişikliklerden ayrı tutun.

## <a name="next-steps"></a>Sonraki adımlar

- **Yalıtım.** DL'lerin çoğu veritabanları ve diğer DL'ler gibi diğer alt sistemlere bağlıdır. Bu diğer bileşenler genellikle paralel olarak geliştirilmiştir. Birim testinin yapılmasına izin vermek için, diğer bileşenler henüz mevcut değilken,

- **Yapı Doğrulama Testleri.** Takımınızın yapı sunucusunda belirli aralıklarla testler gerçekleştirebilirsiniz. Bu, birkaç ekip üyesinin çalışması tümleşik olduğunda hataların kullanılmamasını sağlar.

- **İade testleri.** Her ekip üyesi kodu kaynak denetimine denetlemeden önce bazı testlerin gerçekleştirildiğini belirtebilirsiniz. Genellikle bu, yapı doğrulama testlerinin tam kümesinin bir alt kümesidir.

   Ayrıca, en az kod kapsamı düzeyini de görevden alabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Varolan C++ uygulamalarına birim testleri ekleme](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Microsoft.VisualStudio.TestTools.CppUnitTestFramework Kullanma](how-to-use-microsoft-test-framework-for-cpp.md)
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [Walkthrough: Dinamik bağlantı kitaplığı oluşturma ve kullanma (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [İthalat ve ihracat](/cpp/build/importing-and-exporting)
