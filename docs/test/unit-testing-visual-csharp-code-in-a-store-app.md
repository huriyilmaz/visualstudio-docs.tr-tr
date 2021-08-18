---
title: Visual C# kodunda birim testi
description: UWP uygulamasında C# sınıfı için birim testleri oluşturma hakkında bilgi edinebilirsiniz. Bu makalede test güdümlü geliştirme gösterildi.
ms.custom: SEO-VS-2020
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- uwp
ms.openlocfilehash: d618099687ea54326418814bfdebe938de13b6dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115310"
---
# <a name="unit-test-c-code"></a>C# birim testi sınıfı

Bu makalede UWP uygulamasında C# sınıfı için birim testleri oluşturmanın bir yolu açıklanmıştır.

Test kapsamındaki sınıf olan **Rooter** sınıfı, belirli bir sayanın karekökünün tahminini hesapan bir işlev kullanır.

Bu makalede *test güdümlü geliştirmesi gösterildi.* Bu yaklaşımda önce test etmekte olduğunu sistemde belirli bir davranışı doğrular ve ardından testi geçen kodu yazarsiniz.

## <a name="create-the-solution-and-the-unit-test-project"></a>Çözümü ve birim testi projesini oluşturma

1. Dosya menüsünde **Yeni** **dosya'Project.**  >  

2. Boş Uygulama **(Evrensel Uygulama) proje şablonunu Windows seçin.**

3. Projeye **Maths adını girin.**

4. Bu **Çözüm Gezgini** çözümüne sağ tıklayın ve Yeni Ekle'yi **Project.**  >  

5. Birim Testi Uygulaması **(Evrensel Uygulama) proje şablonunu Windows seçin.**

6. Test projesine **RooterTests adını girin.**

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Test Gezgini'nde testlerin çalıştığını doğrulama

1. *UnitTest.cs* dosyasında **TestMethod1'e** bazı test kodu ekleme:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   sınıfı, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> test yöntemlerinde sonuçları doğrulamak için kullanabileceğiniz birkaç statik yöntem sağlar.

::: moniker range="vs-2017"

2. Test menüsünde **Tüm** Testleri  > **Çalıştır'ı seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

2. Test menüsünde **Tüm** Testleri **Çalıştır'ı seçin.**

::: moniker-end

   Test projesi derleme ve çalıştırma. Biraz zaman alarken sabırlı olun. **Test Gezgini penceresi** görüntülenir ve test Başarılı Testler altında **listelenir.** Pencerenin **en** altındaki Özet bölmesi, seçilen testle ilgili ek ayrıntılar sağlar.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Maths projesine Rooter sınıfı ekleme

1. Bu **Çözüm Gezgini** Matematik projesine sağ **tıklayın ve** Sınıf Ekle'yi   >  **seçin.**

2. Sınıf dosyasına *Rooter.cs adını girin.*

3. *Rooter.cs* **dosyasının Rooter** sınıfına aşağıdaki kodu ekleyin:

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

   **Rooter sınıfı** bir oluşturucu ve **SquareRoot** tahmin yöntemi bildirer. **SquareRoot yöntemi,** test kurulumunun temel yapısını test etmeye yetecek kadar küçük bir uygulamadır.

4. Test `public` kodunun buna **erişmesi için Anahtar** sözcüğünü Rooter sınıf bildirimine ekleyin.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Proje başvurusu ekleme

1. Maths uygulamasına RooterTests projesinden bir başvuru ekleyin.

    1. Bu **Çözüm Gezgini** **RooterTests** projesine sağ tıklayın ve Başvuru **Ekle'yi**  >  **seçin.**

    2. Başvuru Ekle **- RooterTests** iletişim kutusunda Çözüm'i genişletin ve **Projeler'i** **seçin.** Matematik **projesini** seçin.

        ![Matematik projesine başvuru ekleme](../test/media/ute_cs_windows_addreference.png)

2. `using` *UnitTest.cs dosyasına deyimini* ekleyin:

    1. *UnitTest.cs'yi açın.*

    2. Bu kodu satırın altına `using Microsoft.VisualStudio.TestTools.UnitTesting;` ekleyin:

       ```csharp
       using Maths;
       ```

3. **Rooter** işlevini kullanan bir test ekleyin. Aşağıdaki kodu *UnitTest.cs'ye ekleyin:*

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

   Yeni test Test **Gezgini'nde Testleri** **Çalıştırmama düğümünde** görünür.

4. "Yük aynı hedef yola sahip iki veya daha fazla dosya içeriyor" hatasını  önlemek için  **Çözüm Gezgini'de** Matematik projesinin altındaki Özellikler düğümünü genişletin veDefault.rd.xml *silin.*

::: moniker range="vs-2017"

6. **Test Gezgini'nde,** Hepsini **Çalıştır'ı seçin.**

   Çözüm derlemeleri ve testleri çalıştırarak geçer.

   ![Test Gezgini'nde geçirilen BasicTest](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. Test **Gezgini'nde** Tüm Testleri **Çalıştır'ı seçin.**

   Çözüm derlemeleri ve testleri çalıştırarak geçer.

   ![Test Gezgini'nde geçirilen Temel Test](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Test ve uygulama projelerini ayarladıktan sonra uygulama projesinde işlevleri çağıran testler çalıştırabilirsiniz. Artık gerçek testler ve kod yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Testleri çoğaltarak geliştirin ve başarıyla geçişlerini snın

1. RangeTest adlı yeni bir test **ekleyin:**

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
   > Geçen testleri değiştirmenizi önerilmez. Bunun yerine yeni bir test ekleyin.

2. **RangeTest testini** çalıştırın ve başarısız olduğunu doğrulayın.

   ![RangeTest başarısız oluyor](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Bir test yazdıktan hemen sonra başarısız olduğunu doğrulamak için çalıştırın. Bu, hiçbir zaman başarısız olmayacak bir test yazma hatalarından kaçınmanıza yardımcı olur.

3. Yeni testin başarılı olacak şekilde test altındaki kodu geliştirin. *Rooter.cs'de* **SquareRoot** işlevini şu şekilde değiştirebilirsiniz:

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

4. **Test Gezgini'nde,** Hepsini **Çalıştır'ı seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

4. Test **Gezgini'nde** Tüm Testleri **Çalıştır'ı seçin.**

::: moniker-end

   Üç test de artık başarılı oldu.

> [!TIP]
> Testleri tek tek ekleyerek kod geliştirin. Tüm testlerin her yinelemeden sonra başarılı olduğundan emin olun.

## <a name="refactor-the-code"></a>Kodu yeniden düzenleme

Bu bölümde, hem uygulama hem de test kodunu yeniden düzenlemeye devam ediyor ve hala başarılı olduğundan emin olmak için testleri yeniden çalıştırabilirsiniz.

### <a name="simplify-the-square-root-estimation"></a>Karekök tahminini basitleştirme

1. Aşağıdaki gibi bir kod satırı **değiştirerek SquareRoot** işlevinde merkezi hesaplamayı basitleştirin:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Regresyona neden olmadığınızdan emin olmak için tüm testleri çalıştırın. Hepsi başarılı olmalı.

> [!TIP]
> Kararlı bir dizi iyi birim testi, kodu değiştirirken hatalara neden olmadığınız için güven verir.

### <a name="eliminate-duplicated-code"></a>Yinelenen kodu ortadan kaldırma

**RangeTest** yöntemi, yöntemine geçirilen tolerans *değişkeninin* paydalarını sabit olarak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> kodlar. Aynı tolerans hesaplaması kullanan ek testler eklemeyi planlıyorsanız, birden çok konumda sabit kodlu bir değerin kullanımı kodun bakımını yapmayı zorlaştırır.

1. Tolerans değerini hesaplamak için **UnitTest1** sınıfına özel bir yardımcı yöntem ekleyin ve ardından RangeTest'den bu **yöntemi çağırarak.**

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
> Bir test sınıfına yardımcı yöntem ekler ve bunun **Test** Gezgini'nde görünmesini istemiyorsanız, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğini yöntemine eklemezsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: Test Gezgini'ni kullanarak test güdümlü geliştirme](quick-start-test-driven-development-with-test-explorer.md)
