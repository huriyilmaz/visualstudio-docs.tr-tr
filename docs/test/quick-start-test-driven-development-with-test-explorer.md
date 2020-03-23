---
title: Test odaklı geliştirme walkthrough
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: a264975014fea88126bbca0589fe037e629dae10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566286"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Walkthrough: Test Gezgini'ni kullanarak test odaklı geliştirme

Artımlı kod değişiklikleri yle kodunuzu doğru çalışmaya yardımcı olmak için birim testleri oluşturun. Birim testleri yazmak için kullanabileceğiniz, bazıları üçüncü taraflarca geliştirilen ler de dahil olmak üzere çeşitli çerçeveler vardır. Bazı test çerçeveleri farklı dillerde veya platformlarda sınama için özelleştirilmiştir. Test Gezgini, bu çerçevelerden herhangi birinde birim testleri için tek bir arabirim sağlar. **Test Gezgini**hakkında daha fazla bilgi için, Test Gezgini ve [Test Gezgini SSS](test-explorer-faq.md) [ile Birim testlerini çalıştır'a](run-unit-tests-with-test-explorer.md) bakın.

Bu izim, Microsoft Test Framework (MSTest) kullanarak C#'da test edilmiş bir yöntemin nasıl geliştirilebildiğini gösterir. Bunu kolayca diğer dillere veya NUnit gibi diğer test çerçevelerine uyarlayabilirsiniz. Daha fazla bilgi için [bkz.](install-third-party-unit-test-frameworks.md)

## <a name="create-a-test-and-generate-code"></a>Bir test oluşturma ve kod oluşturma

1. C# **Sınıf Kitaplığı (.NET Standart)** projesi oluşturun. Bu proje, test etmek istediğimiz kodu içerir. Proje **MyMath**adı .

2. Aynı çözümde, yeni bir **MSTest Test Projesi (.NET Core) projesi** ekleyin. Test projesi **MathTests**adı .

   ![Yeni kod ve test projeleri](../test/media/test-driven-development-ide.png)

3. Belirli bir giriş için elde edilen sonucu doğrulayan basit bir test yöntemi yazın. `UnitTest1` Sınıfa aşağıdaki kodu ekleyin:

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

   1. İmleci üzerine `Rooter`yerleştirin ve ardından ampul menüsünden **'Rooter'** > Oluştur türünü seçin Yeni tür**oluştur.**

      ![Yeni tür hızlı eylem oluşturma](media/test-driven-development-generate-new-type.png)

   2. Türü **Oluştur** iletişim kutusunda **Project'i** **MyMath'e**, sınıf kitaplığı projesine ayarlayın ve ardından **Tamam'ı**seçin.

      ![Visual Studio 2019'da Tür iletişim kutusu oluştur](media/test-driven-development-generate-type-dialog.png)

5. Test kodundan bir yöntem oluşturun. İmleci üzerine `SquareRoot`yerleştirin ve ampul menüsünden **'Rooter.SquareRoot' yöntemini oluştur'u**seçin.

6. Birim testini çalıştırın.

   1. Test **Gezgini'ni**açmak için, **Test** menüsünde **Windows** > **Test Gezgini'ni**seçin.

   2. **Test Gezgini'nde,** testi çalıştırmak için **Tümlerini Çalıştır** düğmesini seçin.

   Çözüm oluşturur ve test çalışır ve başarısız olur.

7. Testin adını seçin.

   Testin ayrıntıları **Test Ayrıntı Özeti** bölmesinde görünür.

   ![Test Gezgini'nde Test Detay Özeti](media/test-driven-development-test-detail-summary.png)

8. Testin başarısız olduğu konuma atlamak için **Yığın İzleme'nin** altındaki en üst teki bağlantıyı seçin.

Bu noktada, testin geçmesi için değiştirebileceğiniz bir test ve saplama oluşturdunuz.

## <a name="verify-a-code-change"></a>Kod değişikliğini doğrulama

1. *Class1.cs* dosyasında, kodu `SquareRoot`geliştirmek:

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. **Test Gezgini'nde,** **Tümlerini Çalıştır'ı**seçin.

   Çözüm oluşturur ve test çalışır ve geçer.

   ![Geçen testi gösteren Test Gezgini](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Girdi aralığını genişletme

Kodun her durumda çalıştığına olan güvenimizi artırmak için, daha geniş bir giriş değeri aralığını deneyen testler ekleyin.

> [!TIP]
> Geçen varolan testleri değiştirmekten kaçının. Bunun yerine, yeni testler ekleyin. Varolan testleri yalnızca kullanıcı gereksinimleri değiştiğinde değiştirin. Bu ilke, kodu genişletmeye çalışırken varolan işlevselliği kaybetmemenize yardımcı olur.

1. Test sınıfında, bir dizi giriş değeri deneen aşağıdaki testi ekleyin:

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

2. **Test Gezgini'nde,** **Tümlerini Çalıştır'ı**seçin.

   Yeni test başarısız olur (ilk test hala geçse de). Hata noktasını bulmak için, başarısız testi seçin ve ardından **Test Ayrıntı Özeti** bölmesindeki ayrıntılara bakın.

3. Sorunun ne olabileceğini görmek için test altındaki yöntemi inceleyin. Kodu `SquareRoot` aşağıdaki gibi değiştirin:

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

4. **Test Gezgini'nde,** **Tümlerini Çalıştır'ı**seçin.

   Her iki test de artık geçti.

## <a name="add-tests-for-exceptional-cases"></a>İstisnai durumlar için testler ekleme

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

2. **Test Gezgini'nde,** **Tümlerini Çalıştır'ı**seçin.

   Yöntem test döngüleri altında ve el ile iptal edilmelidir.

3. **Test Gezgini'nin**araç çubuğunda **İptal'i** seçin.

   Test yürütmeyi durdurur.

4. Yöntemin `SquareRoot` başında aşağıdaki `if` ifadeyi ekleyerek kodu düzeltin:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. **Test Gezgini'nde,** **Tümlerini Çalıştır'ı**seçin.

   Tüm testler geçer.

## <a name="refactor-the-code-under-test"></a>Test altındaki kodu yeniden düzenleme

Kodu yeniden düzenleme, ancak testleri değiştirmeyin.

> [!TIP]
> *Yeniden düzenleme,* kodun daha iyi veya anlaşılması daha kolay bir performans göstermesini sağlamayı amaçlayan bir değişikliktir. Kodun davranışını değiştirmek için tasarlanmamıştır ve bu nedenle testler değiştirilmez.
>
> Yeniden düzenleme adımlarını işlevselliği genişleten adımlardan ayrı olarak gerçekleştirmenizi öneririz. Testleri değiştirmeden tutmak, yeniden düzenleme sırasında yanlışlıkla hata lar uygulamaya niçin kullanılmadığınıza dair size güven verir.

1. `result` Yöntemde hesaplanan satırı aşağıdaki `SquareRoot` gibi değiştirin:

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

2. **Tümlerini Çalıştır'ı**seçin ve tüm testlerin hala geçtiğini doğrulayın.

   ![Test Gezgini 3 geçmiş testleri gösteriyor](../test/media/test-driven-development-three-passed-tests.png)
