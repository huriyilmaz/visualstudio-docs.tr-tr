---
title: Ünite test Görsel C# kodu
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 31fbbfaa5d16dd51776f592b89a7846936b3013f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590871"
---
# <a name="unit-test-c-code"></a>C# birim testi sınıfı

Bu makalede, UWP uygulamasında c# sınıfı için birim testleri oluşturmanın bir yolu açıklanmaktadır.

Test altındaki sınıf olan **Rooter** sınıfı, belirli bir sayının kare kökünün tahminini hesaplayan bir işlev uygular.

Bu makalede, *test odaklı geliştirme*göstermektedir. Bu yaklaşımda, önce test ettiğiniz sistemde belirli bir davranışı doğrulayan bir test yazarsınız, sonra da testi geçen kodu yazarsınız.

## <a name="create-the-solution-and-the-unit-test-project"></a>Çözümü ve birim test projesini oluşturun

1. **Dosya** menüsünde **Yeni** > **Proje'yi**seçin.

2. **Boş Uygulama (Evrensel Windows)** proje şablonunu arayın ve seçin.

3. Proje **Matematik**adı .

4. **Çözüm Gezgini'nde,** çözüme sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin.

5. **Birim Test Uygulaması (Evrensel Windows)** proje şablonunu arayın ve seçin.

6. Test projesi **RooterTests**adı.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Testlerin Test Gezgini'nde çalıştırıldığını doğrulama

1. *UnitTest.cs* dosyasına **TestMethod1'e** bazı test kodu ekleyin:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Sınıf, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> test yöntemleriyle sonuçları doğrulamak için kullanabileceğiniz birkaç statik yöntem sağlar.

::: moniker range="vs-2017"

2. **Test** menüsünde Tüm Testleri **Çalıştır'ı** > **All Tests**seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. **Test** menüsünde **Tüm Testleri Çalıştır'ı**seçin.

::: moniker-end

   Test projesi oluşturur ve çalışır. Sabırlı olun çünkü biraz zaman alabilir. **Test Gezgini** penceresi görüntülenir ve test **Geçti Testleri**altında listelenir. Pencerenin altındaki **Özet** bölmesi, seçili test hakkında ek ayrıntılar sağlar.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Matematik projesine Rooter sınıfını ekle

1. **Çözüm Gezgini'nde,** **Matematik** projesine sağ tıklayın ve ardından**Sınıf** **Ekle'yi** > seçin.

2. Sınıf dosyasını *Rooter.cs.*

3. **Rooter** sınıfı *Rooter.cs* dosyasına aşağıdaki kodu ekleyin:

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

   **Rooter** sınıfı bir oluşturucu ve **SquareRoot** tahminci yöntemi bildirir. **SquareRoot** yöntemi yalnızca en az uygulama, sadece test kurulumu temel yapısını test etmek için yeterlidir.

4. Test `public` kodu erişebilsin diye anahtar sözcüğü **Rooter** sınıfı bildirimine ekleyin.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Proje başvurusu ekleme

1. Maths uygulamasına RooterTests projesinden bir başvuru ekleyin.

    1. **Çözüm Gezgini'nde** **RooterTests** projesine sağ tıklayın ve ardından**Kaynak** **Ekle'yi** > seçin.

    2. Başvuru **Ekle - RooterTests** iletişim kutusunda, **Çözümü** genişletin ve **Projeler'i**seçin. **Matematik** projesini seçin.

        ![Matematik projesine referans ekleme](../test/media/ute_cs_windows_addreference.png)

2. UnitTest.cs `using` dosyasına *UnitTest.cs* bir deyim ekleyin:

    1. Açık *UnitTest.cs*.

    2. Bu kodu satırın `using Microsoft.VisualStudio.TestTools.UnitTesting;` altına ekleyin:

       ```csharp
       using Maths;
       ```

3. **Rooter** işlevini kullanan bir test ekleyin. *UnitTest.cs*için aşağıdaki kodu ekleyin:

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

   Yeni test, Test **Gezgini'nde** **Çalıştırılmayan Testler** düğümünde görünür.

4. "Yük aynı hedef yolu olan iki veya daha fazla dosya içerir" hatasını önlemek **için, Solution**Explorer'da, **Maths** projesi altındaki **Özellikler** düğümünü genişletin ve ardından *Varsayılan.rd.xml* dosyasını silin.

::: moniker range="vs-2017"

6. **Test Gezgini'nde,** **Tümlerini Çalıştır'ı**seçin.

   Çözüm oluşturur ve testler çalışır ve geçer.

   ![Test Gezgini'nde temel test geçti](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. **Test Gezgini'nde,** Tüm **Testleri Çalıştır'ı**seçin.

   Çözüm oluşturur ve testler çalışır ve geçer.

   ![Test Gezgini'nde Temel Test geçti](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Test ve uygulama projelerini ayarladınız ve uygulama projesinde işlevleri arayan testleri çalıştırabileceğinizi doğruladınız. Şimdi gerçek testler ve kod yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Testleri yinelemeli bir şekilde artırın ve geçmelerini

1. **RangeTest**adlı yeni bir test ekle:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > Geçen testleri değiştirmemenizi öneririz. Bunun yerine yeni bir test ekleyin.

2. **RangeTest** testini çalıştırın ve başarısız olduğunu doğrulayın.

   ![RangeTest başarısız olur](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Bir test yazdıktan hemen sonra, başarısız olduğunu doğrulamak için çalıştırın. Bu, asla başarısız olmayan bir test yazmanın kolay hatasını önlemenize yardımcı olur.

3. Yeni testin geçmesi için test altındaki kodu geliştirin. Rooter.cs'daki *Rooter.cs* **SquareRoot** işlevini şu şekilde değiştirin:

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

::: moniker range="vs-2017"

4. **Test Gezgini'nde,** **Tümlerini Çalıştır'ı**seçin.

::: moniker-end

::: moniker range=">=vs-2019"

4. **Test Gezgini'nde,** Tüm **Testleri Çalıştır'ı**seçin.

::: moniker-end

   Üç test de geçti.

> [!TIP]
> Testleri teker teker ekleyerek kod geliştirin. Tüm testlerin her yinelemeden sonra geçtiğinden emin olun.

## <a name="refactor-the-code"></a>Kodu yeniden düzenleme

Bu bölümde, hem uygulama hem de test kodunu yeniden küçlersiniz, ardından testleri yineleyip geçtiklerinden emin olursunuz.

### <a name="simplify-the-square-root-estimation"></a>Kare kök tahminini basitleştirin

1. Bir kod satırını değiştirerek **SquareRoot** işlevindeki merkezi hesaplamayı basitleştirin:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Bir gerileme getirmediğinden emin olmak için tüm testleri çalıştırın. Hepsi geçmeli.

> [!TIP]
> İyi birim testleri kararlı bir dizi kodu değiştirdiğinizde hataları tanıttı değil güven verir.

### <a name="eliminate-duplicated-code"></a>Yinelenen kodu ortadan kaldırma

**RangeTest** yöntemi, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> yönteme geçirilen *tolerans* değişkeninin paydasını sabit kodlar. Aynı tolerans hesaplamasını kullanan ek testler eklemeyi planlıyorsanız, birden çok konumda sabit kodlanmış bir değerin kullanılması kodun korunmasını zorlaştırır.

1. Tolerans değerini hesaplamak için **UnitTest1** sınıfına özel bir yardımcı yöntemi ekleyin ve ardından bu yöntemi **RangeTest'ten**arayın.

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
        // Old code
        // double tolerance = expected/1000;

        // New code
        double tolerance = ToleranceHelper(expected);
    }
    ...
    ```

2. Hala geçtiğinden emin olmak için **RangeTest'i** çalıştırın.

> [!TIP]
> Bir test sınıfına yardımcı yöntem eklerseniz ve **test gezgininde**görünmesini istemiyorsanız, yönteme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> öznitelik eklemeyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Walkthrough: Test Gezgini'ni kullanarak test odaklı geliştirme](quick-start-test-driven-development-with-test-explorer.md)
