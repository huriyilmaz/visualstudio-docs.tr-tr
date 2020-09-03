---
title: 'Hızlı başlangıç: Test Gezgini ile test temelli geliştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5161b533-2127-4172-b473-d4ffc76ff05b
caps.latest.revision: 17
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eae08427e9ec61c34a98f3581355909317b69559
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672255"
---
# <a name="quick-start-test-driven-development-with-test-explorer"></a>Hızlı Başlangıç: Test Gezgini ile Test Güdümlü Geliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geliştirmede birçok artımlı adım sayesinde kodunuzun düzgün çalışmasını sağlamaya yardımcı olmak için birim testleri oluşturmanızı öneririz. Üçüncü taraflar tarafından geliştirilen bazıları dahil olmak üzere birim testlerini yazmak için kullanabileceğiniz çeşitli çerçeveler vardır. Bazı test çerçeveleri, farklı diller veya platformlarda test etmek için özelleştirilmiştir. Test Gezgini, bu çerçevelerin herhangi birinde birim testleri için tek bir arabirim sağlar. Bağdaştırıcılar, en yaygın kullanılan çerçeveler için kullanılabilir ve diğer çerçeveler için kendi bağdaştırıcılarınızı yazabilirsiniz.

 Test Gezgini, Visual Studio 'nun önceki sürümlerinde bulunan birim testi pencerelerinin yerini alır. Avantajları şunlardır:

- Tek bir arabirim kullanarak .NET, yönetilmeyen, veritabanı ve diğer test türlerini çalıştırın.

- Seçtiğiniz birim testi çerçevesini (NUnit veya MSTest çerçeveleri gibi) kullanın.

- İhtiyacınız olan tüm bilgileri tek bir pencerede görüntüleyin.

## <a name="using-test-explorer"></a>Test Gezgini 'ni kullanma
 ![Tümünü Çalıştır düğmesini gösteren birim test Gezgini](../test/media/unittestexplorer-beta.png "UnitTestExplorer (Beta)")

#### <a name="to-run-unit-tests-by-using-test-explorer"></a>Test Gezgini 'ni kullanarak birim testlerini çalıştırmak için

1. Seçtiğiniz test çerçevelerini kullanan birim testleri oluşturun.

    Örneğin, MSTest çerçevesini kullanan bir test oluşturmak için:

   1. Bir test projesi oluşturun.

        **Yeni proje** iletişim kutusunda **Visual Basic**, **Visual C#** veya **Visual C++**' i genişletin ve ardından **Test**' i seçin.

        **Birim testi projesi**seçin.

   2. Her birim testini bir yöntem olarak yazın. Özniteliği ile her test yönteminin ön eki `[TestMethod]` .

2. Bireysel testlerin herhangi bir sırada çalıştırılmasını engelleyen bir bağımlılığı yoksa, araç çubuğunda sırasıyla ![&#95;parallelicon&#45;küçük](../test/media/ute-parallelicon-small.png "UTE_parallelicon-küçük") iki durumlu düğmesiyle paralel test yürütmeyi etkinleştirin. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.

3. Menü çubuğunda, **Test**, **birim testlerini Çalıştır**, **Tüm testler**' i seçin.

    Çözüm oluşturulur ve testler çalışır.

    Test Gezgini açılır ve sonuçların özetini görüntüler.

   **Testlerin tam listesini görmek için:** Herhangi bir kategoride **Tümünü göster** ' i seçin.

   **Bir test sonucunun ayrıntılarını görmek için:** Ayrıntılar bölmesinde özel durum iletileri gibi ayrıntıları görüntülemek için test Gezgini 'nde test ' i seçin.

   **Bir testin koduna gitmek için:** Test Gezgini 'nde teste çift tıklayın veya kısayol menüsünde **testi aç** ' ı seçin.

   **Bir testte hata ayıklamak için:** Bir veya daha fazla test için kısayol menüsünü açın ve **Seçili testlerin hatalarını ayıkla**' yı seçin.

> [!IMPORTANT]
> Görüntülenen sonuçlar en son çalıştırma içindir. Renkli sonuçlar çubuğunda yalnızca çalıştırılan testlerin sonuçları gösterilir. Örneğin, birkaç test çalıştırırsanız ve bunlardan bazıları başarısız olur ve sonra yalnızca başarılı testleri çalıştırırsanız, sonuçlar çubuğunda tüm yeşil görünür.

> [!NOTE]
> Hiç test yoksa, test Gezgini 'ni kullanmakta olduğunuz test çerçevesine bağlamak için bir bağdaştırıcı yüklediğinizden emin olun. Daha fazla bilgi için bkz. [farklı bir test çerçevesi kullanma](/visualstudio/test/getting-started-with-unit-testing#use-a-third-party-test-framework).

## <a name="walkthrough-using-unit-tests-to-develop-a-method"></a><a name="walkthrough"></a> İzlenecek yol: bir yöntem geliştirmek için birim testlerini kullanma
 Bu izlenecek yol, Microsoft birim testi çerçevesini kullanarak C# ' de test edilmiş bir yöntemin nasıl geliştirileceğini göstermektedir. Diğer dillere kolayca uyarlayabilir ve NUnit gibi diğer test çerçevelerini kullanabilirsiniz. Daha fazla bilgi için bkz. [farklı bir test çerçevesi kullanma](/visualstudio/test/getting-started-with-unit-testing#use-a-third-party-test-framework).

#### <a name="creating-the-test-and-method"></a>Test ve yöntem oluşturma

1. Visual C# sınıf kitaplığı projesi oluşturun. Bu proje, teslim etmek istediğimiz kodu içerecektir. Bu örnekte, adlandırılır `MyMath` .

2. Bir test projesi oluşturun.

   - **Yeni proje** Iletişim kutusunda **Visual C#**' ı seçin, **Test** edin ve ardından **birim testi projesi**' ni seçin.

        ![Yeni kod ve test projeleri](../test/media/unittestexplorerwalk1.png "UnitTestExplorerWalk1")

3. Temel bir test yöntemi yazın. Belirli bir giriş için elde edilen sonucu doğrulayın:

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
     Assert.AreEqual(expectedResult, actualResult,
         delta: expectedResult / 100);
   }
   ```

4. Testten yöntemi oluşturun.

   1. İmleci üzerine getirin `Rooter` ve ardından kısayol menüsünde **Oluştur**, **yeni tür**' i seçin.

   2. **Yeni tür oluştur** iletişim kutusunda, **projeyi** sınıf kitaplığı projesi olarak ayarlayın. Bu örnekte bu değer `MyMath`’dur.

   3. İmleci üzerine getirin `SquareRoot` ve ardından kısayol menüsünde **Oluştur**, **Yöntem saplaması**' nı seçin.

5. Birim testini çalıştırın.

   1. **Test** menüsünde, **birim testlerini Çalıştır**, **Tüm testler**' i seçin.

        Çözüm oluşturulur ve çalışır.

        Test Gezgini açılır ve sonuçları görüntüler.

        Test **başarısız testler**altında görünür.

6. Testin adını seçin.

    Testin ayrıntıları Test Gezgini 'nin alt bölümünde görünür.

7. Testin başarısız olduğunu görmek için **yığın izleme** altındaki öğeleri seçin.

   ![Başarısız testi gösteren birim test Gezgini.](../test/media/unittestexplorerwalkthrough2.png "UnitTestExplorerWalkthrough2")

   Bu noktada, testin başarılı olması için değiştireceğiniz bir test ve bir saplama oluşturdunuz.

#### <a name="after-every-change-make-all-the-tests-pass"></a>Her değişiklikten sonra tüm testlerin geçişini yapın

1. İçinde `MyMath\Rooter.cs` , şu kodu geliştirebilirsiniz `SquareRoot` :

    ```csharp
    public double SquareRoot(double input)
     {
       return input / 2;
     }
    ```

2. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

     Kod derlemeleri ve test çalıştırmaları.

     Test geçirilir.

     ![Bir geçen testi gösteren birim test Gezgini.](../test/media/unittestexplorerwalkthrough3.png "UnitTestExplorerWalkthrough3")

#### <a name="add-tests-to-extend-the-range-of-inputs"></a>Giriş aralığını genişletmek için testler ekleyin

1. Kodunuzun her durumda çalıştığından emin olmak için, daha geniş bir giriş değerleri aralığı deneyen testler ekleyin.

    > [!TIP]
    > Başarılı olan testlerin değiştirilmesini önleyin. Bunun yerine, yeni testler ekleyin. Mevcut testleri yalnızca kullanıcı gereksinimleri değiştiğinde değiştirin. Bu ilke, kodu genişletmek için çalışırken mevcut işlevselliği kaybetmemenizi sağlamaya yardımcı olur.

     Test Sınıfınıza aşağıdaki testi ekleyin ve bu bir giriş değeri aralığı dener:

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
      // Create an instance to test:
      Rooter rooter = new Rooter();
      // Try a range of values:
      for (double expectedResult = 1e-8;
          expectedResult < 1e+8;
          expectedResult = expectedResult * 3.2)
      {
        RooterOneValue(rooter, expectedResult);
      }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
      double input = expectedResult * expectedResult;
      double actualResult = rooter.SquareRoot(input);
      Assert.AreEqual(expectedResult, actualResult,
          delta: expectedResult / 1000);
    }
    ```

2. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

     Yeni test başarısız olsa da, ilk test yine de geçer.

     Başarısızlık noktasını bulmak için, başarısız testi seçin ve ardından Test Gezgini 'nin alt bölümünde, **yığın izlemenin**en üstteki öğesini seçin.

3. Neyin yanlış olabileceğini görmek için test kapsamındaki yöntemi inceleyin. `MyMath.Rooter`Sınıfında, kodu yeniden yazın:

    ```
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

4. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

     Her iki test artık geçer.

#### <a name="add-tests-for-exceptional-cases"></a>Olağanüstü durumlar için testler ekleme

1. Negatif girişler için bir test ekleyin:

    ```csharp
    [TestMethod]
     public void RooterTestNegativeInputx()
     {
         Rooter rooter = new Rooter();
         try
         {
             rooter.SquareRoot(-10);
         }
         catch (ArgumentOutOfRangeException e)
         {
             return;
         }
         Assert.Fail();
     }
    ```

2. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

     Test döngülerine ait yöntemi ve el ile iptal edilmesi gerekir.

3. **İptal**' i seçin.

     Sınama 10 saniye sonra duraklar.

4. Yöntem kodunu çözme:

    ```csharp

    public double SquareRoot(double input)
    {
      if (input <= 0.0)
      {
        throw new ArgumentOutOfRangeException();
      }
    ...
    ```

5. Test Gezgini içinde **Tümünü Çalıştır**' ı seçin.

     Tüm testler geçer.

#### <a name="refactor-without-changing-tests"></a>Testleri değiştirmeden yeniden düzenleme

1. Kodu basitleştirir, ancak testleri değiştirmeyin.

    > [!TIP]
    > Yeniden *düzenleme* , kodun daha iyi hale getirme veya kodun anlaşılması daha kolay hale getirmek için tasarlanan bir değişikdir. Kodun davranışını değiştirmek için tasarlanmamıştır ve bu nedenle testler değiştirilmez.
    >
    >  Yeniden düzenleme adımlarını işlevselliği genişleten adımlardan ayrı olarak gerçekleştirmenizi öneririz. Testlerin değişmeden tutulması, yanlışlıkla yeniden düzenleme sırasında hata sunmamanızı sağlar.

    ```csharp
    public class Rooter
    {
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
    }
    ```

2. **Tümünü Çalıştır**' ı seçin.

     Tüm testler yine de başarılı.

     ![3 geçilen testi gösteren birim test Gezgini.](../test/media/unittestexplorerwalkthrough4.png "UnitTestExplorerWalkthrough4")
