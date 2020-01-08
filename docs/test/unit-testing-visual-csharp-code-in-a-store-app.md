---
title: Visual C# koduna birim testi
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 31fbbfaa5d16dd51776f592b89a7846936b3013f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590871"
---
# <a name="unit-test-c-code"></a>C# birim testi sınıfı

Bu makalede, UWP uygulamasında bir C# sınıf için birim testleri oluşturmanın bir yolu açıklanmaktadır.

Test altındaki sınıf olan **Rooter** sınıfı, belirli bir sayının kare kökünü tahmin eden bir işlevi uygular.

Bu makalede, *test odaklı geliştirme*gösterilmektedir. Bu yaklaşımda, öncelikle test ettiğiniz sistemde belirli bir davranışı doğrulayan bir test yazar ve ardından testi geçiren kodu yazarsınız.

## <a name="create-the-solution-and-the-unit-test-project"></a>Çözüm ve birim testi projesi oluşturma

1. Üzerinde **dosya** menüsünde seçin **yeni** > **proje**.

2. **Boş uygulama (Evrensel Windows)** proje şablonunu arayın ve seçin.

3. Projeyi **Maaltı**olarak adlandırın.

4. **Çözüm Gezgini**, çözüme sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.

5. **Birim testi uygulaması (Evrensel Windows)** proje şablonunu arayın ve seçin.

6. Test projesi kökü \ **tertest**adını adlandırın.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Testleri Test Gezgini'nde çalıştırma doğrulayın

1. *UnitTest.cs* dosyasına **testyöntemi1** ' ye bazı test kodu ekleyin:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> sınıfı, test yöntemlerinde sonuçları doğrulamak için kullanabileceğiniz çeşitli statik yöntemler sağlar.

::: moniker range="vs-2017"

2. **Test** menüsünde, **Tüm testler**> **Çalıştır** ' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. **Test** menüsünde **Tüm Testleri Çalıştır**' ı seçin.

::: moniker-end

   Test projesi oluşturur ve çalıştırır. Biraz uzun sürebileceğinden sabırlı olun. **Test Gezgini** penceresi görünür ve test altında listelenen **başarılı testler**. **Özeti** pencerenin alt kısmındaki bölmesi, seçilen test hakkında ek ayrıntılar sağlar.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Matematik projeye Rooter sınıfı Ekle

1. **Çözüm Gezgini**, **maaltı** projeye sağ tıklayın ve ardından > **sınıfı** **Ekle** ' yi seçin.

2. Sınıf dosyasının adı *Rooter.cs*.

3. Aşağıdaki kodu **Rooter** sınıfı *Rooter.cs* dosyasına ekleyin:

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

   **Rooter** sınıfı bir Oluşturucu ve **SquareRoot** tahmin aracı metodunu bildirir. **SquareRoot** yöntemi yalnızca en az bir uygulama, test kurulumunun temel yapısını test etmek için yeterlidir.

4. `public` anahtar sözcüğünü **Rooter** sınıfı bildirimine ekleyin, böylece test kodu buna erişebilir.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Bir proje başvurusu Ekle

1. RooterTests projesinden Maon uygulamasına bir başvuru ekleyin.

    1. **Çözüm Gezgini**, **RooterTests** projesine sağ tıklayın ve ardından > **başvuru** **Ekle** ' yi seçin.

    2. İçinde **Başvuru Ekle - RooterTests** iletişim kutusunda **çözüm** ve **projeleri**. **Maaltı** projeyi seçin.

        ![Matematik projeye bir başvuru ekleyin](../test/media/ute_cs_windows_addreference.png)

2. *UnitTest.cs* dosyasına bir `using` ifadesini ekleyin:

    1. *UnitTest.cs*'i açın.

    2. Aşağıdaki bu kod ekleme `using Microsoft.VisualStudio.TestTools.UnitTesting;` satırı:

       ```csharp
       using Maths;
       ```

3. **Rooter** işlevini kullanan bir test ekleyin. Aşağıdaki kodu *UnitTest.cs*öğesine ekleyin:

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

   Yeni test görünür **Test Gezgini** içinde **çalıştırılmamış testler** düğümü.

4. "Yükün aynı hedef yolu ile iki veya daha fazla dosya içermesi" hatasını önlemek için, **Çözüm Gezgini**' de, **masekiz** projenin altındaki **Özellikler** düğümünü genişletin ve ardından *default. RD. xml* dosyasını silin.

::: moniker range="vs-2017"

6. İçinde **Test Gezgini**, seçin **tümünü Çalıştır**.

   Çözüm oluşturulur ve testler çalışır ve geçer.

   ![Test Gezgini 'nde BasicTest geçildi](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. **Test Gezgini**'Nde **Tüm Testleri Çalıştır**' ı seçin.

   Çözüm oluşturulur ve testler çalışır ve geçer.

   ![Test Gezgini 'nde temel test geçildi](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Test ve uygulama projelerini ayarlamış ve uygulama projesindeki işlevleri çağıran testleri çalıştıracağınızı doğruladınız. Şimdi gerçek test ve kod yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Yinelemeli olarak testleri genişletme ve onları geçirin

1. **Rangetest**adlı yeni bir test ekleyin:

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
   > Geçmiş olan testleri değiştirmemenizi öneririz. Bunun yerine yeni bir test ekleyin.

2. **Rangetest** testini çalıştırın ve başarısız olduğunu doğrulayın.

   ![RangeTest başarısız](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Test yazdıktan hemen sonra, başarısız olduğunu doğrulamak için çalıştırın. Bu, hiçbir zaman başarısız bir test yazma kolay onlardan yardımcı olur.

3. Yeni test geçer, test edilen kod geliştirin. *Rooter.cs* içindeki **SquareRoot** işlevini şu şekilde değiştirin:

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

4. İçinde **Test Gezgini**, seçin **tümünü Çalıştır**.

::: moniker-end

::: moniker range=">=vs-2019"

4. **Test Gezgini**'Nde **Tüm Testleri Çalıştır**' ı seçin.

::: moniker-end

   Üç testi şimdi geçirin.

> [!TIP]
> Aynı anda testleri bir ekleyerek kod geliştirin. Tüm testler her yinelemeden sonra başarılı olduğundan emin olun.

## <a name="refactor-the-code"></a>Kodu yeniden düzenleyin

Bu bölümde, hem uygulama hem de test kodunu yeniden düzenleyin ve ardından devam ettiğinden emin olmak için testleri yeniden çalıştırın.

### <a name="simplify-the-square-root-estimation"></a>Kare kök tahmini 'ni basitleştirme

1. Bir kod satırını aşağıdaki gibi değiştirerek **SquareRoot** işlevindeki merkezi hesaplamayı kolaylaştırın:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Bir gerileme sunmadığınızdan emin olmak için tüm testleri çalıştırın. Hepsi başarılı olmalıdır.

> [!TIP]
> Kararlı bir dizi iyi birim testi kodu değiştirdiğinizde, yeni hatalar oluşturmadığından emin olmanızı sağlar.

### <a name="eliminate-duplicated-code"></a>Yinelenen kodu kaldırın

**Rangetest** yöntemi, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> yöntemine geçirilen *tolerans* değişkeninin paydasını sabit olarak kodlar. Aynı tolerans hesaplamasını kullanan ek testler eklemeyi planlıyorsanız, sabit kodlanmış bir değerin birden çok konumda kullanılması kodun bakımını daha zor hale getirir.

1. Tolerans değerini hesaplamak için **UnitTest1** sınıfına özel bir yardımcı yöntemi ekleyin ve sonra bu yöntemi **rangetest**' ten çağırın.

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

2. Hala başarılı olduğundan emin olmak için **Rangetest** çalıştırın.

> [!TIP]
> Test sınıfına bir yardımcı yöntemi eklerseniz ve **Test Gezgini**'nde görünmesini istemiyorsanız, yöntemine <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğini eklemeyin.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: test Gezginini kullanarak test odaklı geliştirme](quick-start-test-driven-development-with-test-explorer.md)
