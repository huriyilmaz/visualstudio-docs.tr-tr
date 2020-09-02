---
title: C++ için Microsoft birim testi çerçevesi ile C-C + + için birim testleri yazma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 4f4b5f10-7314-4725-8c6e-e72f52eff918
caps.latest.revision: 16
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5b6f358f43dcace230e1d58773e58be011d9033e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657086"
---
# <a name="writing-unit-tests-for-cc-with-the-microsoft-unit-testing-framework-for-c"></a>C++ için Microsoft Birim Test Çerçevesi ile C/C++ için Birim Testleri Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, C++ dilinde yazılmış yönetilmeyen kod için birim testleri oluşturabilirsiniz. Yönetilmeyen kod bazen yerel kod olarak adlandırılır.

 Aşağıdaki yordam, başlamanızı sağlayacak temel bilgileri içerir. Sonraki bölümlerde, daha ayrıntılı adımları açıklayan bir anlatım sağlanmıştır.

### <a name="to-write-unit-tests-for-an-unmanaged-code-dll"></a>Yönetilmeyen kod DLL 'SI için birim testlerini yazmak için

1. Testleriniz için ayrı bir Visual Studio projesi oluşturmak için **Yerel test projesi** şablonunu kullanın.

     Proje bazı örnek test kodu içerir.

2. DLL 'yi test projesi için erişilebilir hale getirin:

    - `#include``.h`DLL 'nin dışarıdan erişilebilen işlevlerinin bildirimlerini içeren dosya.

         `.h`Dosya ile işaretlenmiş işlev bildirimleri içermelidir `_declspec(dllimport)` . Alternatif olarak, bir DEF dosyası kullanarak yöntemleri dışarı aktarabilirsiniz. Daha fazla bilgi için bkz. [içeri ve dışarı aktarma](https://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b).

         Birim testleriniz yalnızca test edilen DLL 'den aktarılmış işlevlere erişebilir.

    - DLL projesini test projesinin başvurularına ekleyin:

         Test projesinin **özelliklerinde** **ortak özellikler**, **çerçeve ve başvurular**' ı genişletin ve **Başvuru Ekle**' yi seçin.

3. Test projesinde, test makroları ve onaylama sınıfını aşağıdaki şekilde kullanarak test sınıfları ve test yöntemleri oluşturun:

    ```cpp
    #include "stdafx.h"
    #include <CppUnitTest.h>
    #include "..\MyProjectUnderTest\MyCodeUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    TEST_CLASS(TestClassName)
    {
    public:
      TEST_METHOD(TestMethodName)
      {
        // Run a function under test here.
        Assert::AreEqual(expectedValue, actualValue, L"message", LINE_INFO());
      }
    }
    ```

    - `Assert` testin sonucunu doğrulamak için kullanabileceğiniz birkaç statik işlev içerir.

    - `LINE_INFO()`Parametresi isteğe bağlıdır. PDB dosyası olmadığı durumlarda, test çalıştırıcısının bir hata konumunu belirlemesine izin verir.

    - Ayrıca, test kurulumu ve temizleme yöntemleri yazabilirsiniz. Daha fazla bilgi için, makronun tanımını açın `TEST_METHOD` ve CppUnitTest. h içindeki Yorumları okuyun

    - Test sınıfları iç içe geçirilemez.

4. Testleri çalıştırmak için test Gezgini 'ni kullanın:

    1. **Görünüm** menüsünde **diğer pencereler**, **Test Gezgini**' ni seçin.

    2. Visual Studio çözümünü derleyin.

    3. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

    4. Test Gezgini 'nde herhangi bir testi daha ayrıntılı incelemek için:

        1. Hata iletisi ve yığın izlemesi gibi diğer ayrıntıları görmek için test adını seçin.

        2. Hata konumuna veya test koduna gitmek için test adını (örneğin, çift tıklayarak) açın.

        3. Testin kısayol menüsünde, hata ayıklayıcıda testi çalıştırmak için **Seçili testin hatalarını ayıkla** ' yı seçin.

## <a name="walkthrough-developing-an-unmanaged-dll-with-test-explorer"></a><a name="walkthrough"></a> İzlenecek yol: Test Gezgini ile yönetilmeyen DLL geliştirme
 Bu yönergeyi kendi DLL 'nizi geliştirmeye uyarlayabilirsiniz. Asıl adımlar aşağıdaki gibidir:

1. [Yerel bir test projesi oluşturun](#unitTestProject). Testler, geliştirmekte olduğunuz DLL 'den ayrı bir projede oluşturulur.

2. [BIR DLL projesi oluşturun](#createDllProject). Bu izlenecek yol yeni bir DLL oluşturur, ancak var olan bir DLL 'yi test etme yordamı benzerdir.

3. [DLL işlevlerini testlere görünür hale getirin](#coupleProjects).

4. [Testleri](#iterate)yinelemeli olarak güçlendirin. Kodun geliştirilmesi testlerin yaptığı bir "kırmızı yeşil-yeniden düzenleme" döngüsünün kullanılması önerilir.

5. [Başarısız testlerde hata ayıklayın](#debug). Testleri hata ayıklama modunda çalıştırabilirsiniz.

6. [Testleri değişmeden tutarken yeniden düzenleme](#refactor). Yeniden düzenleme, dış davranışını değiştirmeden kodun yapısını iyileştirmek anlamına gelir. Bu kodu, kodun performansını, genişletilebilirliğini veya okunabilirliğini geliştirmek için yapabilirsiniz. Amaç, davranışı değiştirmediğinden, kodda yeniden düzenleme değişikliği yaparken testleri değiştirmeyin. Testler, yeniden düzenleme sırasında hata tanıtmadığınızdan emin olmanıza yardımcı olur. Bu nedenle, testlerin olmadığı gibi, bu değişiklikleri daha çok güvenle yapabilirsiniz.

7. [Kapsama bakın](https://msdn.microsoft.com/library/fc8hec9e.aspx). Birim testleri, kodunuzun daha fazlasını yaparken daha kullanışlı olur. Kodunuzun hangi bölümlerinin test tarafından kullanıldığını keşfedebilirsiniz.

8. [Birimleri dış kaynaklardan yalıtın](https://msdn.microsoft.com/library/hh549174.aspx). Genellikle, bir DLL, diğer dll 'Ler, veritabanları veya uzak alt sistemler gibi geliştirmekte olduğunuz sistem bileşenlerine bağımlıdır. Her birimi bağımlılıklarından yalıtılmış olarak test etmek yararlı olur. Dış bileşenler, testlerin yavaş çalışmasını sağlayabilir. Geliştirme sırasında diğer bileşenler tamamlanmamış olabilir.

### <a name="create-a-native-unit-test-project"></a><a name="unitTestProject"></a> Yerel birim testi projesi oluştur

1. **Dosya** menüsünde, **Yeni**, **Proje**' yi seçin.

     İletişim kutusunda, **yüklü**, **Şablonlar**, **Visual C++**, **Test**' i genişletin.

     **Yerel test projesi** şablonunu seçin.

     Bu izlenecek yolda, test projesi adlandırılır `NativeRooterTest` .

     ![C&#43;&#43; birim testi projesi oluşturma](../test/media/utecpp01.png "UteCpp01")

2. Yeni projede, **UnitTest1. cpp** ' yi inceleyin

     ![Test&#95;sınıfı ve TEST&#95;YÖNTEMIYLE test projesi](../test/media/utecpp2.png "UteCpp2")

     Dikkat edin:

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

    2. **Test** menüsünde, **Çalıştır** , **Tüm testler**' i seçin.

         Test derlemeleri ve çalıştırmaları.

         Test Gezgini görüntülenir.

         Test **geçilen testler**altında görünür.

         ![Başarılı bir test ile birim test Gezgini](../test/media/utecpp04.png "UteCpp04")

### <a name="create-an-unmanaged-dll-project"></a><a name="createDllProject"></a> Yönetilmeyen DLL projesi oluşturma

1. **Win32 Proje** şablonunu kullanarak bir **Visual C++** projesi oluşturun.

     Bu kılavuzda, proje adlandırılır `RootFinder` .

     ![C&#43;&#43; Win32 projesi oluşturma](../test/media/utecpp05.png "UteCpp05")

2. Win32 uygulama Sihirbazı 'nda **DLL** 'yi seçin ve **sembolleri dışarı aktarın** .

     **Sembolleri dışarı aktar** seçeneği, dışarı aktarılmış yöntemleri bildirmek için kullanabileceğiniz, kullanışlı bir makro oluşturur.

     ![C&#43;&#43; Projesi Sihirbazı DLL ve dışa aktarma sembolleri için ayarlandı](../test/media/utecpp06.png "UteCpp06")

3. Principal. h dosyasında bir dışarıya aktarılmış işlev bildirin:

     ![API makroları ile yeni DLL kod projesi ve. h dosyası](../test/media/utecpp07.png "UteCpp07")

     Bildirimci, `__declspec(dllexport)` sınıfın genel ve korumalı ÜYELERININ dll dışında görünür olmasına neden olur. Daha fazla bilgi için bkz. [C++ sınıflarında dllimport ve dllexport kullanma](https://msdn.microsoft.com/library/8d7d1303-b9e9-47ca-96cc-67bf444a08a9).

4. Principal. cpp dosyasında, işlev için en az bir gövde ekleyin:

    ```cpp
    // Find the square root of a number.
    double CRootFinder::SquareRoot(double v)
    {
      return 0.0;
    }
    ```

### <a name="couple-the-test-project-to-the-dll-project"></a><a name="coupleProjects"></a> DLL projesine test projesi için birkaç

1. DLL projesini test projesinin proje başvurularına ekleyin:

   1. Test projesinin özelliklerini açın ve **ortak özellikler**, **çerçeve ve başvurular**' ı seçin.

        ![C&#43;&#43; proje özellikleri &#45; Framework ve başvurular](../test/media/utecpp08.png "UteCpp08")

   2. **Yeni Başvuru Ekle**' yi seçin.

        **Başvuru Ekle** iletişim kutusunda, DLL projesini seçin ve **Ekle**' yi seçin.

        ![C&#43;&#43; proje özellikleri &#45; Yeni Başvuru Ekle](../test/media/utecpp09.png "UteCpp09")

2. Asıl birim testi. cpp dosyasında, DLL kodunun. h dosyasını dahil edin:

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

    Yeni test, test Gezgini 'nde görünür.

5. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

    ![Temel test &#45; birim test Gezgini geçildi](../test/media/utecpp10.png "UteCpp10")

   Test ve kod projelerini ayarlamış ve kod projesindeki işlevleri çalıştıran testleri çalıştıracağınızı doğruladınız. Artık gerçek testleri ve kodu yazmaya başlayabilirsiniz.

### <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a> Testleri tekrarlayarak ve geçiş yapın

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
    >  Kullanıcılarınız gereksinimlerini değiştirmelerine göre artık doğru olmayan Testleri devre dışı bırakın. Yeni testler yazın ve aynı anda bir kez, aynı şekilde çalışır hale getirin.

2. Çözümü oluşturun ve ardından Test Gezgini ' nde **Tümünü Çalıştır**' ı seçin.

     Yeni test başarısız olur.

     ![RangeTest başarısız oluyor](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")

    > [!TIP]
    > Her testin yazıldıktan hemen sonra başarısız olduğunu doğrulayın. Bu, hiç başarısız olmayan bir testi yazmanın kolay bir hata yaşamadan kaçınmanıza yardımcı olur.

3. Yeni testin başarılı olması için test kapsamındaki kodu geliştirin:

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

4. Çözümü derleyin ve ardından Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

     Her iki test de geçer.

     ![Birim test Gezgini &#45; Aralık testi geçildi](../test/media/utecpp12.png "UteCpp12")

    > [!TIP]
    > Her seferinde bir test ekleyerek kod geliştirin. Her yinelemeden sonra tüm testlerin başarılı olduğundan emin olun.

### <a name="debug-a-failing-test"></a><a name="debug"></a> Başarısız bir testte hata ayıkla

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

     Başarısız onaylama vurgulanır. Hata iletisi, test Gezgini 'nin ayrıntı bölmesinde görünür.

     ![Negatiftiverangetests başarısız oldu](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")

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

     ![Tüm testler geçer](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")

> [!TIP]
> Bireysel testlerin herhangi bir sırada çalıştırılmasını engelleyen bir bağımlılığı yoksa, araç çubuğunda sırasıyla ![&#95;parallelicon&#45;küçük](../test/media/ute-parallelicon-small.png "UTE_parallelicon-küçük") iki durumlu düğmesiyle paralel test yürütmeyi etkinleştirin. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.

### <a name="refactor-the-code-without-changing-tests"></a><a name="refactor"></a> Testleri değiştirmeden kodu yeniden düzenleme

1. SquareRoot işlevinde merkezi hesaplamayı kolaylaştırın:

    ```
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Bir hata sunduğunuzdan emin olmak için çözümü derleyin ve **Tümünü Çalıştır**' ı seçin.

    > [!TIP]
    > Uygun bir birim testi kümesi, kodu değiştirirken hata sunmaabileceğinizden emin olmanızı sağlar.
    >
    >  Yeniden düzenlemeyi diğer değişikliklerden ayrı tutun.

## <a name="next-steps"></a>Sonraki adımlar

- **Yalıtımı.** Çoğu dll veritabanları ve diğer dll 'Ler gibi diğer alt sistemlere bağımlıdır. Bu diğer bileşenler genellikle paralel olarak geliştirilmiştir. Diğer bileşenler henüz kullanılamadığı sürece birim testi gerçekleştirilmesine izin vermek için, sahte veya

- **Derleme doğrulama testleri.** Ekip oluşturma sunucusunda, belirlenen aralıklarda testlerin gerçekleştirilmesini sağlayabilirsiniz. Bu, birkaç takım üyesinin çalışması tümleştirildiğinde hataların tanıtılmamasını sağlar.

- **İade testleri.** Her bir takım üyesinin, kaynak denetimine kodu denetlemesi için bazı testlerin gerçekleştirilmesini zorunlu hale getirebilirsiniz. Genellikle bu, tüm yapı doğrulama testleri kümesinin bir alt kümesidir.

     Ayrıca, en düşük kod kapsamı düzeyini de kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Microsoft. VisualStudio. TestTools. CppUnitTestFramework kullanarak](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md) [mevcut C++ uygulamalarına birim testleri ekleme](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) [yönetilen/yönetilmeyen kod birlikte çalışabilirlik](https://msdn.microsoft.com/library/ms973872.aspx) [hata ayıklamasına](../debugger/debugging-native-code.md) genel bakış [: bir dinamik bağlantı kitaplığı oluşturma ve kullanma (C++)](https://msdn.microsoft.com/library/3ae94848-44e7-4955-bbad-7d40f493e941) [içeri ve dışarı aktarma](https://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b)
