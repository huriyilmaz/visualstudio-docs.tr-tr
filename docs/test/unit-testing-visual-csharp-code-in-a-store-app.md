---
title: Birim testi Visual C# kodu
description: UWP uygulamasında bir C# sınıfı için birim testleri oluşturmayı öğrenin. Bu makalede, test odaklı geliştirme gösterilmektedir.
ms.custom: SEO-VS-2020
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 410d5dfefa5980bceabff99d66067987b390a615
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330088"
---
# <a name="unit-test-c-code"></a>C# birim testi sınıfı

Bu makalede, UWP uygulamasında bir C# sınıfı için birim testleri oluşturmanın bir yolu açıklanmaktadır.

Test altındaki sınıf olan **Rooter** sınıfı, belirli bir sayının kare kökünü tahmin eden bir işlevi uygular.

Bu makalede, *test odaklı geliştirme* gösterilmektedir. Bu yaklaşımda, öncelikle test ettiğiniz sistemde belirli bir davranışı doğrulayan bir test yazar ve ardından testi geçiren kodu yazarsınız.

## <a name="create-the-solution-and-the-unit-test-project"></a>Çözüm ve birim testi projesi oluşturma

1. **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.

2. **Boş uygulama (Evrensel Windows)** proje şablonunu arayın ve seçin.

3. Projeyi **Maaltı** olarak adlandırın.

4. **Çözüm Gezgini**, çözüme sağ tıklayın ve **Add**  >  **Yeni proje** Ekle ' yi seçin.

5. **Birim testi uygulaması (Evrensel Windows)** proje şablonunu arayın ve seçin.

6. Test projesi kökü \ **tertest** adını adlandırın.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Test Gezgini 'nde testlerin çalıştırıldığını doğrulama

1. *UnitTest.cs* dosyasına **testyöntemi1** ' ye bazı test kodu ekleyin:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>Sınıfı, test yöntemlerinde sonuçları doğrulamak için kullanabileceğiniz çeşitli statik yöntemler sağlar.

::: moniker range="vs-2017"

2. **Test** menüsünde **Run** > **tüm testleri** Çalıştır ' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. **Test** menüsünde **Tüm Testleri Çalıştır**' ı seçin.

::: moniker-end

   Test projesi oluşturulup çalışır. Biraz uzun sürebileceğinden sabırlı olun. **Test Gezgini** penceresi görünür ve test **geçilen testler** altında listelenir. Pencerenin alt kısmındaki **Özet** bölmesi, seçilen test hakkında ek ayrıntılar sağlar.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Rooter sınıfını Maon projesine ekleyin

1. **Çözüm Gezgini**, **maaltı** projeye sağ tıklayın ve ardından sınıf **Ekle**' yi seçin  >  **Class**.

2. Sınıf dosyasını *Rooter.cs* olarak adlandırın.

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

4. `public`Anahtar sözcüğünü **Rooter** sınıfı bildirimine ekleyin, böylece test kodu buna erişebilir.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Proje başvurusu Ekle

1. RooterTests projesinden Maon uygulamasına bir başvuru ekleyin.

    1. **Çözüm Gezgini**, **RooterTests** projesine sağ tıklayın ve ardından başvuru **Ekle**' yi seçin  >  **Reference**.

    2. **Başvuru Ekle-RooterTests** Iletişim kutusunda **çözüm** ' i genişletin ve **Projeler**' i seçin. **Maaltı** projeyi seçin.

        ![Maaltı projeye başvuru ekleme](../test/media/ute_cs_windows_addreference.png)

2. `using` *UnitTest.cs* dosyasına bir ifade ekleyin:

    1. *UnitTest.cs*'i açın.

    2. Bu kodu satırın altına ekleyin `using Microsoft.VisualStudio.TestTools.UnitTesting;` :

       ```csharp
       using Maths;
       ```

3. **Rooter** işlevini kullanan bir test ekleyin. Aşağıdaki kodu *UnitTest.cs* öğesine ekleyin:

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

   Yeni test, **Test Gezgini** 'Nde, **çalıştırma testleri** düğümünde görünür.

4. "Yükün aynı hedef yolu ile iki veya daha fazla dosya içermesi" hatasını önlemek için, **Çözüm Gezgini**' de, **masekiz** projenin altındaki **özellikler** düğümünü genişletin ve ardından *Default.rd.xml* dosyasını silin.

::: moniker range="vs-2017"

6. **Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin.

   Çözüm oluşturulur ve testler çalışır ve geçer.

   ![Test Gezgini 'nde BasicTest geçildi](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. **Test Gezgini**'Nde **Tüm Testleri Çalıştır**' ı seçin.

   Çözüm oluşturulur ve testler çalışır ve geçer.

   ![Test Gezgini 'nde temel test geçildi](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Test ve uygulama projelerini ayarlamış ve uygulama projesindeki işlevleri çağıran testleri çalıştıracağınızı doğruladınız. Artık gerçek testleri ve kodu yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Testleri tekrarlayarak ve geçiş yapın

1. **Rangetest** adlı yeni bir test ekleyin:

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
   > Geçilen testleri değiştirmenizi öneririz. Bunun yerine yeni bir test ekleyin.

2. **Rangetest** testini çalıştırın ve başarısız olduğunu doğrulayın.

   ![RangeTest başarısız oluyor](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Test yazdıktan hemen sonra, başarısız olduğunu doğrulamak için çalıştırın. Bu, hiç başarısız olmayan bir testi yazmanın kolay bir hata yaşamadan kaçınmanıza yardımcı olur.

3. Yeni testin başarılı olması için test kapsamındaki kodu geliştirin. *Rooter.cs* içindeki **SquareRoot** işlevini şu şekilde değiştirin:

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

4. **Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

4. **Test Gezgini**'Nde **Tüm Testleri Çalıştır**' ı seçin.

::: moniker-end

   Tüm üç test artık geçer.

> [!TIP]
> Her seferinde bir test ekleyerek kod geliştirin. Her yinelemeden sonra tüm testlerin başarılı olduğundan emin olun.

## <a name="refactor-the-code"></a>Kodu yeniden düzenleme

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
> Kararlı bir iyi birim testi kümesi, kodu değiştirirken hata sunmaabileceğinizden emin olmanızı sağlar.

### <a name="eliminate-duplicated-code"></a>Yinelenen kodu kaldırın

**Rangetest** yöntemi, yöntemine geçirilen *tolerans* değişkeninin paydasını sabit olarak kodlar <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> . Aynı tolerans hesaplamasını kullanan ek testler eklemeyi planlıyorsanız, sabit kodlanmış bir değerin birden çok konumda kullanılması kodun bakımını daha zor hale getirir.

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
> Test sınıfına bir yardımcı yöntemi eklerseniz ve **Test Gezgini**'nde görünmesini istemiyorsanız, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> yöntemine özniteliğini eklemeyin.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: test Gezginini kullanarak test odaklı geliştirme](quick-start-test-driven-development-with-test-explorer.md)
