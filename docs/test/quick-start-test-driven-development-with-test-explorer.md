---
title: Test odaklı geliştirme Kılavuzu
description: Microsoft Test çerçevesi kullanarak C# ' de test edilmiş bir yöntemi geliştirmeyi öğrenin ve bu, NUnit gibi diğer dillere veya test çerçevelerine kolayca uyum sağlayabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 294c99081668baa2ed19df00989ceac768979481
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683946"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>İzlenecek yol: test Gezginini kullanarak test odaklı geliştirme

Artımlı kod değişiklikleri aracılığıyla kodunuzun düzgün çalışmasını sağlamaya yardımcı olmak için birim testleri oluşturun. Üçüncü taraflar tarafından geliştirilen bazıları dahil olmak üzere birim testlerini yazmak için kullanabileceğiniz çeşitli çerçeveler vardır. Bazı test çerçeveleri, farklı diller veya platformlarda test için özelleştirilmiştir. Test Gezgini, bu çerçevelerin herhangi birinde birim testleri için tek bir arabirim sağlar. **Test Gezgini** hakkında daha fazla bilgi için bkz. Test Gezgini ve [Test Gezgini](test-explorer-faq.md) [ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md) SSS.

Bu izlenecek yol, Microsoft Test çerçevesi (MSTest) kullanarak C# ' de test edilmiş bir yöntemin nasıl geliştirileceğini göstermektedir. Diğer diller veya NUnit gibi diğer test çerçeveleri için kolayca uyum sağlayabilirsiniz. Daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçevelerini yüklemeyi](install-third-party-unit-test-frameworks.md).

## <a name="create-a-test-and-generate-code"></a>Test oluşturma ve kod üretme

1. C# **sınıf kitaplığı (.NET Standard)** projesi oluşturun. Bu proje, test etmek istediğimiz kodu içerecektir. Projeyi **MyMath** olarak adlandırın.

2. Aynı çözümde yeni bir MSTest test projesi ekleyin.

   Visual Studio 2019 sürüm 16,9 ' den başlayarak, MSTest projesi şablon adı **MSTest test projesinden (.NET Core)** **birim testi projesine** değişti.

   Test projesini **MathTests** olarak adlandırın.

   ![Yeni kod ve test projeleri](../test/media/test-driven-development-ide.png)

3. Belirli bir giriş için elde edilen sonucu doğrulayan basit bir test yöntemi yazın. Sınıfına aşağıdaki kodu ekleyin `UnitTest1` :

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

4. Test kodundan bir tür oluşturun.

   1. İmleci üzerine getirin `Rooter` ve ardından ampul menüsünde **' Rooter ' türü oluştur '** u seçerek  >  **yeni tür oluşturun**.

      ![Yeni tür hızlı eylem Oluştur](media/test-driven-development-generate-new-type.png)

   2. **Tür oluştur** iletişim kutusunda, **projeyi** **MyMath**, sınıf kitaplığı projesi olarak ayarlayın ve ardından **Tamam**' ı seçin.

      ![Visual Studio 2019 'de tür oluştur iletişim kutusu](media/test-driven-development-generate-type-dialog.png)

5. Test kodundan bir yöntem oluşturun. İmleci üzerine getirin `SquareRoot` ve ardından ampul menüsünde **' Rooter. SquareRoot ' metodunu üret**' i seçin.

6. Birim testini çalıştırın.

   1. **Test Gezgini**'ni açmak için, **Test** menüsünde **Windows**  >  **Test Gezgini**' ni seçin.

   2. **Test Gezgini**'nde, testi çalıştırmak Için **Tümünü Çalıştır** düğmesini seçin.

   Çözüm oluşturulur ve test çalışır ve başarısız olur.

7. Testin adını seçin.

   Testin ayrıntıları **Test ayrıntısı Özeti** bölmesinde görünür.

   ![Test Gezgini 'nde test ayrıntısı Özeti](media/test-driven-development-test-detail-summary.png)

8. Testin başarısız olduğu konuma geçmek için **yığın izleme** altındaki en üstteki bağlantıyı seçin.

Bu noktada, testin başarılı olması için değiştirebileceğiniz bir test ve bir saplama oluşturdunuz.

## <a name="verify-a-code-change"></a>Kod değişikliğini doğrulama

1. *Class1.cs* dosyasında, şu kodu geliştirebilirsiniz `SquareRoot` :

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. **Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin.

   Çözüm oluşturulur ve test çalıştırmaları ve geçirir.

   ![Bir geçen testi gösteren test Gezgini](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Giriş aralığını genişletme

Kodun her durumda çalıştığından emin olmak için, daha geniş bir giriş değerleri aralığı deneyen testler ekleyin.

> [!TIP]
> Başarılı olan testlerin değiştirilmesini önleyin. Bunun yerine, yeni testler ekleyin. Mevcut testleri yalnızca kullanıcı gereksinimleri değiştiğinde değiştirin. Bu ilke, kodu genişletmek için çalışırken mevcut işlevselliği kaybetmemenizi sağlamaya yardımcı olur.

1. Test sınıfında, aşağıdaki testi ekleyerek bir giriş değerleri aralığı dener:

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

2. **Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin.

   Yeni test başarısız olur (ancak ilk test devam eder). Başarısızlık noktasını bulmak için, başarısız testi seçin ve ardından **Test ayrıntısı Özeti** bölmesindeki ayrıntılara bakın.

3. Neyin yanlış olabileceğini görmek için test kapsamındaki yöntemi inceleyin. `SquareRoot`Kodu aşağıdaki gibi değiştirin:

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

4. **Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin.

   Her iki test artık geçer.

## <a name="add-tests-for-exceptional-cases"></a>Olağanüstü durumlar için testler ekleme

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

2. **Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin.

   Test döngüleri altındaki yöntemi el ile iptal edilmesi gerekir.

3. **Test Gezgini** araç çubuğunda **iptal** ' i seçin.

   Test yürütmeyi durduruyor.

4. `SquareRoot`Yönteminin başına aşağıdaki ifadeyi ekleyerek kodu düzeltir `if` :

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. **Test Gezgini** Içinde **Tümünü Çalıştır**' ı seçin.

   Tüm testler geçer.

## <a name="refactor-the-code-under-test"></a>Test altındaki kodu yeniden düzenleme

Kodu yeniden düzenleyin, ancak testleri değiştirmeyin.

> [!TIP]
> Yeniden *düzenleme* , kodun daha iyi veya anlaşılması daha kolay hale getirmek için tasarlanan bir değişikdir. Kodun davranışını değiştirmek için tasarlanmamıştır ve bu nedenle testler değiştirilmez.
>
> Yeniden düzenleme adımlarını işlevselliği genişleten adımlardan ayrı olarak gerçekleştirmenizi öneririz. Testlerin değişmeden tutulması, yanlışlıkla yeniden düzenleme sırasında hata sunmamanızı sağlar.

1. Yönteminde hesaplayan satırı `result` `SquareRoot` aşağıdaki gibi değiştirin:

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

2. **Tümünü Çalıştır**' ı seçin ve tüm testlerin hala başarılı olduğunu doğrulayın.

   ![Geçen 3 testi gösteren test Gezgini](../test/media/test-driven-development-three-passed-tests.png)
