---
title: Test güdümlü geliştirme adım adım kılavuz
description: Microsoft Test Framework kullanarak C# dilinde test edilmiş bir yöntem geliştirmeyi öğrenin. Bu yöntem NUnit gibi diğer diller veya test çerçeveleri için kolayca uyarlanabilir.
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: de154900bee2c78453f559c8c90020147e8c528c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106659"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Adım adım kılavuz: Test Gezgini'ni kullanarak test güdümlü geliştirme

Artımlı kod değişiklikleriyle kodunuzun düzgün şekilde çalışmaya devam etmeye yardımcı olmak için birim testleri oluşturun. Bazı üçüncü tarafların geliştirdiği birim testleri de dahil olmak üzere birim testleri yazmak için kullanabileceğiniz çeşitli çerçeveler vardır. Bazı test çerçeveleri farklı dillerde veya platformlarda test etmek için özeldir. Test Gezgini, bu çerçevelerin herhangi birinde birim testleri için tek bir arabirim sağlar. Test Gezgini hakkında daha **fazla bilgi için** [bkz. Test Gezgini ve Test Gezgini SSS](run-unit-tests-with-test-explorer.md) ile birim testleri [çalıştırma.](test-explorer-faq.md)

Bu kılavuzda, Microsoft Test Framework (MSTest) kullanarak C# ile test edilmiş bir yöntemin nasıl geliştireceğiz? Bunu diğer diller veya NUnit gibi diğer test çerçeveleri için kolayca uyarlayabilirsiniz. Daha fazla bilgi için [bkz. Üçüncü taraf birim test çerçevelerini yükleme.](install-third-party-unit-test-frameworks.md)

## <a name="create-a-test-and-generate-code"></a>Test oluşturma ve kod oluşturma

1. Bir C# **Sınıf Kitaplığı (.NET Standard) projesi** oluşturun. Bu proje, test etmek istediğiniz kodu içerir. Projeye **MyMath adını girin.**

2. Aynı çözümde yeni bir MSTest test projesi ekleyin.

   2019 Visual Studio 16.9 sürümünden başlayarak, MSTest proje şablonu adı **MSTest Test Project (.NET Core)** olarak Birim Testi şablonu **Project.**

   Test projesine **MathTests adını girin.**

   ![Yeni kod ve test projeleri](../test/media/test-driven-development-ide.png)

3. Belirli bir giriş için elde edilen sonucu doğrular basit bir test yöntemi yazın. Sınıfına aşağıdaki kodu `UnitTest1` ekleyin:

   ```csharp
   [TestMethod]
   public void BasicRooterTest()
   {
     // Create an instance to test:
     Rooter rooter = new Rooter();
     // Define a test input and output value:
     double expectedResult = 2.0;
     double input = expectedResult * expectedResult;
     // Run the method under test:
     double actualResult = rooter.SquareRoot(input);
     // Verify the result:
     Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 100);
   }
   ```

4. Test kodundan bir tür oluşturma.

   1. İmleci üzerine yerleştirin ve ampul menüsünden Tür oluştur `Rooter` **'Rooter'** Yeni tür  >  **oluştur'a tıklayın.**

      ![Yeni tür hızlı eylemi oluşturma](media/test-driven-development-generate-new-type.png)

   2. Tür Oluştur **iletişim kutusunda,** Project **,** sınıf kitaplığı projesi olarak ayarlayın ve tamam'ı **seçin.** 

      ![Visual Studio 2019'da Tür Oluştur iletişim kutusu](media/test-driven-development-generate-type-dialog.png)

5. Test kodundan bir yöntem oluşturma. İmleci `SquareRoot` üzerine yerleştirerek ampul menüsünden **Generate method 'Rooter.SquareRoot' (Köker.SquareRoot) yöntemini seçin.**

6. Birim testini çalıştırın.

   1. Test **Gezgini'ni** açmak için Test menüsünde **Test** **Gezgini'Windows**  >  **seçin.**

   2. Test **Gezgini'nde,** **testi çalıştırmak** için Tüm Çalıştır düğmesini seçin.

   Çözüm biriktir ve test çalışır ve başarısız olur.

7. Testin adını seçin.

   Testin ayrıntıları Test Ayrıntısı **Özeti bölmesinde** görünür.

   ![Test Gezgini'nde Test Ayrıntısı Özeti](media/test-driven-development-test-detail-summary.png)

8. Testin başarısız olduğu **konuma atlamak** için Yığın İzlemesi'nin altındaki üst bağlantıyı seçin.

Bu noktada, testin başarılı olduğu şekilde değiştirerek bir test ve saplama oluşturduk.

## <a name="verify-a-code-change"></a>Kod değişikliğini doğrulama

1. *Class1.cs dosyasında* kodunu `SquareRoot` geliştirin:

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. **Test Gezgini'nde,** Hepsini **Çalıştır'ı seçin.**

   Çözüm biriktir ve test çalışır ve geçer.

   ![Geçen testi gösteren Test Gezgini](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Giriş aralığını genişletme

Kodun her durumda çalışma güveni artırmak için daha geniş bir giriş değeri aralığı deneyen testler ekleyin.

> [!TIP]
> Geçen mevcut testleri değiştirmekten kaçının. Bunun yerine yeni testler ekleyin. Mevcut testleri yalnızca kullanıcı gereksinimleri değiştiklerinde değiştirebilirsiniz. Bu ilke, kodu genişletmek için çalışmaya devam ettiyseniz mevcut işlevselliği kaybetmemeniz için yardımcı olur.

1. Test sınıfında, giriş değerleri aralığını deneyen aşağıdaki testi ekleyin:

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
        // Create an instance to test.
        Rooter rooter = new Rooter();

        // Try a range of values.
        for (double expected = 1e-8; expected < 1e+8; expected *= 3.2)
        {
            RooterOneValue(rooter, expected);
        }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
        double input = expectedResult * expectedResult;
        double actualResult = rooter.SquareRoot(input);
        Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 1000);
    }
    ```

2. **Test Gezgini'nde,** Hepsini **Çalıştır'ı seçin.**

   Yeni test başarısız olur (ilk test yine de geçse de). Hata noktasını bulmak için başarısız testi seçin ve ardından Test Ayrıntısı Özeti bölmesindeki **ayrıntılara** bakın.

3. Neyin yanlış olabileceğini görmek için test altındaki yöntemini inceler. Kodu `SquareRoot` aşağıdaki gibi değiştirin:

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4. **Test Gezgini'nde,** Hepsini **Çalıştır'ı seçin.**

   Her iki test de artık başarılı oldu.

## <a name="add-tests-for-exceptional-cases"></a>Olağanüstü durumlar için test ekleme

1. Negatif girişler için yeni bir test ekleyin:

    ```csharp
    [TestMethod]
    public void RooterTestNegativeInputx()
    {
        Rooter rooter = new Rooter();
        try
        {
            rooter.SquareRoot(-10);
        }
        catch (System.ArgumentOutOfRangeException)
        {
            return;
        }
        Assert.Fail();
    }
    ```

2. **Test Gezgini'nde,** Hepsini **Çalıştır'ı seçin.**

   Test döngüleri altındaki yöntemi ve el ile iptal edilmesi gerekir.

3. Test **Gezgini'nin** araç çubuğunda **İptal'i seçin.**

   Test yürütülmiyor.

4. yönteminin `SquareRoot` başına aşağıdaki `if` deyimi ekleyerek kodu düzeltin:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. **Test Gezgini'nde,** Hepsini **Çalıştır'ı seçin.**

   Tüm testler geçer.

## <a name="refactor-the-code-under-test"></a>Test altındaki kodu yeniden düzenleme

Kodu yeniden düzenleme, ancak testleri değiştirme.

> [!TIP]
> Yeniden *düzenleme, kodun* daha iyi veya daha kolay anlaşılır olması için tasarlanmış bir değişikliktir. Kodun davranışını değiştirmek amaçlanmaz ve bu nedenle testler değiştirilmez.
>
> Yeniden düzenleme adımlarını, işlevselliği genişleten adımlardan ayrı olarak gerçekleştirmenizi öneririz. Testleri değiştirmeden tutmak, yeniden düzenleme sırasında yanlışlıkla hatalara neden olmadığınızdan size güven verir.

1. yönteminde hesap eden `result` satırı aşağıdaki gibi `SquareRoot` değiştirin:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }

        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
            previousResult = result;
            result = (result + input / result) / 2;
            //was: result = result - (result * result - input) / (2*result);
        }
        return result;
    }
    ```

2. Hepsini **Çalıştır'ı** seçin ve tüm testlerin hala başarılı olduğunu doğrulayın.

   ![3 başarılı testi gösteren Test Gezgini](../test/media/test-driven-development-three-passed-tests.png)
