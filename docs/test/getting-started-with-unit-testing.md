---
title: Birim testini kullanmaya başlama
description: Visual Studio 'Yu kullanarak kod durumunu korumak için birim testlerini tanımlayıp çalıştırın ve müşterilerinizin yapabilmesi için hata ve hataları bulun.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31314a669815d38ed408a28e033e4943df0f75d3
ms.sourcegitcommit: 4e28314dc2be59b4c5fd44545c0653f625e74489
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97756662"
---
# <a name="get-started-with-unit-testing"></a>Birim testini kullanmaya başlama

Kod durumunu korumak, kod kapsamını sağlamak ve müşterilerinizin yapabilmesi için hata ve hataları bulmak üzere birim testlerini tanımlamak ve çalıştırmak için Visual Studio 'Yu kullanın. Kodunuzun düzgün çalıştığından emin olmak için birim testlerinizi sıklıkla çalıştırın.

Bu makalede, kod ve çizimler C# kullanır, ancak kavramlar ve Özellikler .NET dilleri, C++, Python, JavaScript ve TypeScript için geçerlidir.

## <a name="create-unit-tests"></a>Birim testleri oluşturma

Bu bölümde, birim testi projesinin nasıl oluşturulduğu açıklanmaktadır.

1. Visual Studio 'da sınamak istediğiniz projeyi açın.

   Bu makalede, örnek bir birim testi gösterimi amacıyla, **Merhaba WorldCore** adlı basit bir "Merhaba Dünya" C# projesi test eder. Bu tür bir projenin örnek kodu aşağıdaki gibidir:

   ```csharp
   namespace HelloWorldCore

      public class Program
      {
         public static void Main()
         {
            Console.WriteLine("Hello World!");
         }
      }
   ```

1. **Çözüm Gezgini**, çözüm düğümünü seçin. Ardından, üstteki menü çubuğundan **Dosya**  >  **Ekle**  >  **Yeni proje**' yi seçin.

1. Yeni proje iletişim kutusunda, kullanmak istediğiniz test çerçevesi için MSTest gibi bir birim testi projesi şablonu bulun ve seçin.

   Visual Studio 2017 sürüm 14,8 ' den başlayarak, .NET dilleri NUnit ve xUnit için yerleşik şablonlar içerir. C++ için, dil tarafından desteklenen bir test çerçevesini seçmeniz gerekir. Python için bkz. test projenizi ayarlamak için [Python kodunda birim testi ayarlama](../python/unit-testing-python-in-visual-studio.md) .

   > [!TIP]
   > C# için daha hızlı bir yöntem kullanarak koddan birim testi projeleri oluşturabilirsiniz. Daha fazla bilgi için bkz. [birim testi projeleri ve test yöntemleri oluşturma](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods). Bu yöntemi .NET Core veya .NET Standard ile kullanmak için Visual Studio 2019 gereklidir.

   Aşağıdaki çizimde, .NET sürümünde desteklenen bir MSTest birim testi gösterilmektedir.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 ' de birim testi proje şablonu](media/vs-2019/add-new-test-project.png)

   **İleri**' ye tıklayın, test projesi için bir ad seçin ve ardından **Oluştur**' a tıklayın.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Visual Studio 2019 ' de birim testi proje şablonu](media/mstest-test-project-template.png)

   Test projesi için Merhaba dünya testleri gibi bir ad seçin ve ardından **Tamam**' a tıklayın.

   ::: moniker-end

   Proje çözümünüze eklenir.

   ![Çözüm Gezgini birim testi projesi](media/vs-2019/solution-explorer.png)

1. Birim testi projesinde, **Başvurular** veya **Bağımlılıklar** ' a sağ tıklayıp **Başvuru Ekle**' yi seçerek test etmek istediğiniz projeye bir başvuru ekleyin.

1. Test etmek istediğiniz kodu içeren projeyi seçin ve **Tamam**' a tıklayın.

   ![Visual Studio 'Ya proje başvurusu ekleme](media/vs-2019/reference-manager.png)

1. Birim testi yöntemine kod ekleyin.

   Örneğin, test çerçevesinden eşleşen doğru belge sekmesini seçerek aşağıdaki kodu kullanabilirsiniz: MSTest, NUnit veya xUnit (yalnızca .NET üzerinde desteklenir).

   # <a name="mstest"></a>[MSTest](#tab/mstest)

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class UnitTest1
      {
         private const string Expected = "Hello World!";
         [TestMethod]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

   # <a name="nunit"></a>[NUnit](#tab/nunit)

   ```csharp
   using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      public class Tests
      {
         private const string Expected = "Hello World!";

         [SetUp]
         public void Setup()
         {
         }
         [Test]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

    # <a name="xunit"></a>[xUnit](#tab/xunit)

    ```csharp
    using System;
    using Xunit;
    using System.IO;
    
    namespace HelloWorldTests
    {
        public class UnitTest1
        {
            private const string Expected = "Hello World!";
            [Fact]
            public void Test1()
            {
                using (var sw = new StringWriter())
                {
                    Console.SetOut(sw);
                    HelloWorldCore.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

## <a name="run-unit-tests"></a>Birim testlerini çalıştırma

1. [Test Gezgini](../test/run-unit-tests-with-test-explorer.md)'ni açın.

   ::: moniker range=">=vs-2019"
   Test Gezgini 'ni açmak için  > üst menü çubuğundan test **Test Gezgini** ' ni seçin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Test Gezgini 'ni açmak için  >  > üst menü çubuğundan Windows **Test Gezgini** 'ni test et ' i seçin.
   ::: moniker-end

1. **Tümünü Çalıştır**' a tıklayarak birim testlerinizi çalıştırın.

   ![Test Gezgini ile birim testleri çalıştırma](media/vs-2019/test-explorer-run-all.png)

   Testler tamamlandıktan sonra yeşil onay işareti bir testin geçtiğini gösterir. Kırmızı bir "x" simgesi testin başarısız olduğunu gösterir.

   ![Test Gezgini 'nde birim test sonuçlarını gözden geçirme](media/vs-2019/unit-test-passed.png)

> [!TIP]
> [Test Gezgini](../test/run-unit-tests-with-test-explorer.md) 'ni, yerleşik test çerçevesinden (MSTest) veya üçüncü taraf test çerçevelerinden birim testlerini çalıştırmak için kullanabilirsiniz. Testleri kategoriler halinde gruplandırabilir, test listesine filtre uygulayabilir ve testlerin çalma listelerini oluşturabilir, kaydedebilir ve çalıştırabilirsiniz. Ayrıca, testlerin hatalarını ayıklayabilir ve test performansını ve kod kapsamını çözümleyebilirsiniz.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>Canlı birim testi sonuçlarını görüntüle (Visual Studio Enterprise)

Visual Studio 2017 veya sonraki sürümlerde MSTest, xUnit veya NUnit test çerçevesini kullanıyorsanız, birim testlerinizin canlı sonuçlarını görebilirsiniz.

> [!NOTE]
> Bu adımları izlemek için Visual Studio Enterprise gereklidir.

1. **Test** Live Unit Testing Başlat ' a tıklayarak **Test** menüsünden canlı birim testi ' ni açın  >    >  .

   ::: moniker range="vs-2017"

   ![Canlı birim testini aç](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 ' de canlı birim testi başlatma](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Kodu yazarken ve düzenlerken testlerin sonuçlarını kod Düzenleyicisi penceresi içinde görüntüleyin.

   ![Testlerin sonuçlarını görüntüleme](media/vs-2019/live-unit-testing-results.png)

1. Bu yöntemi kapsayan testlerin adları gibi daha fazla bilgi görüntülemek için bir test sonucu göstergesine tıklayın.

   ![Test sonucu göstergelerini seçin](media/vs-2019/live-unit-testing-details.png)

Canlı birim testi hakkında daha fazla bilgi için bkz. [canlı birim testi](../test/live-unit-testing-intro.md).

## <a name="use-a-third-party-test-framework"></a>Üçüncü taraf bir test çerçevesi kullanma

Visual Studio 'da, programlama dilinize bağlı olarak Boost, Google ve NUnit gibi üçüncü taraf test çerçeveleri kullanarak birim testlerini çalıştırabilirsiniz. Bir üçüncü taraf çerçevesini kullanmak için:

- Seçtiğiniz çerçeveye yönelik NuGet paketini yüklemek için **NuGet Paket Yöneticisi 'ni** kullanın.

- .Net Visual Studio 2017 sürüm 14,6 ' den başlayarak, Visual Studio NUnit ve xUnit test çerçeveleri için önceden yapılandırılmış test projesi şablonlarını içerir. Şablonlar, desteği etkinleştirmek için gereken NuGet paketlerini de içerir.

- C++ Visual Studio 2017 ve sonraki sürümlerinde, Boost gibi bazı çerçeveler zaten dahil edilmiştir. Daha fazla bilgi için bkz. [Visual Studio 'Da C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md).

Birim testi projesi eklemek için:

1. Test etmek istediğiniz kodu içeren çözümü açın.

2. **Çözüm Gezgini** çözüme sağ tıklayın ve   >  **Yeni proje** Ekle ' yi seçin.

3. Bir birim testi proje şablonu seçin.

   Bu örnekte, [NUnit](https://nunit.org/) ' i seçin

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 'de NUnit test proje şablonu](media/vs-2019/nunit-test-project-template.png)

   **İleri**' ye tıklayın, projeyi adlandırın ve ardından **Oluştur**' a tıklayın.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Projeyi adlandırın ve ardından oluşturmak için **Tamam** ' ı tıklatın.

   ::: moniker-end

   Proje şablonu NUnit ve NUnit3TestAdapter için NuGet başvuruları içerir.

   ![Çözüm Gezgini NUnit NuGet bağımlılıkları](media/vs-2019/nunit-nuget-dependencies.png)

4. Test projesinden test etmek istediğiniz kodu içeren projeye bir başvuru ekleyin.

   **Çözüm Gezgini**' de projeye sağ tıklayın ve ardından başvuru **Ekle**' yi seçin  >  . ( **Başvurular** veya **Bağımlılıklar** düğümünün sağ tıklama menüsünde de bir başvuru ekleyebilirsiniz.)

5. Test yönteminiz için kod ekleyin.

   ![Birim test kodu dosyanıza kod ekleme](media/vs-2019/unit-test-method.png)

6. Test **Gezgini** 'nden veya test kodu ' na sağ tıklayıp **Test Çalıştır**' ı seçerek testi çalıştırın.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Birim testi temel bilgileri](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [Yönetilen kod için birim testleri oluşturma ve çalıştırma](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
