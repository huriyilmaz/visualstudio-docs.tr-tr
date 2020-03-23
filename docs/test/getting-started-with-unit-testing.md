---
title: Birim testiile başlayın
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90c3cbdee722c4cf12c515f06659cc03f3179e1e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78289860"
---
# <a name="get-started-with-unit-testing"></a>Birim testiile başlayın

Kod durumunu korumak, kod kapsamını sağlamak ve müşterilerinizden önce hataları ve hataları bulmak için birim testlerini tanımlamak ve çalıştırmak için Visual Studio'u kullanın. Kodunuzu düzgün çalıştığından emin olmak için birim testlerinizi sık sık çalıştırın.

## <a name="create-unit-tests"></a>Birim testleri oluşturma

Bu bölümde birim test projesi nasıl oluşturulacak açıklanmaktadır.

1. Visual Studio'da test etmek istediğiniz projeyi açın.

   Örnek bir birim testi göstermek amacıyla, bu makalede **HelloWorldCore**adlı basit bir "Hello World" projesi test edilir. Böyle bir projenin örnek kodu aşağıdaki gibidir:

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

1. **Çözüm Gezgini'nde**çözüm düğümünü seçin. Ardından, üst menü çubuğundan **Dosya** > **Add** > **Ekle Yeni Proje'yi**seçin.

1. Yeni proje iletişim kutusunda, kullanmak istediğiniz test çerçevesi için birim test proje şablonu bulun ve seçin.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019'da ünite test proje şablonu](media/vs-2019/add-new-test-project.png)

   **İleri'yi**tıklatın, test projesi için bir ad seçin ve sonra **Oluştur'u**tıklatın.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Visual Studio 2019'da ünite test proje şablonu](media/mstest-test-project-template.png)

   Test projesi için bir ad seçin ve ardından **Tamam'ı**tıklatın.

   ::: moniker-end

   Proje çözümünüze eklenir.

   ![Çözüm Gezgini'nde birim test projesi](media/vs-2019/solution-explorer.png)

1. Birim test projesinde, **Başvurular** veya **Bağımlılıklar'a** sağ tıklayarak ve ardından **Başvuru Ekle'yi**seçerek test etmek istediğiniz projeye bir başvuru ekleyin.

1. Test edeceğiniz kodu içeren projeyi seçin ve **Tamam'ı**tıklatın.

   ![Visual Studio'da proje başvurusu ekleme](media/vs-2019/reference-manager.png)

1. Birim test yöntemine kod ekleyin.

   Örneğin, bir MSTest projesi için aşağıdaki kodu kullanabilirsiniz.

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

   Veya bir NUnit projesi için aşağıdaki kodu kullanabilirsiniz.

   ```csharp
   using using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
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

> [!TIP]
> Birim testleri oluşturma hakkında daha fazla bilgi için, [yönetilen kod için birim testleri oluştur ve çalıştır'a](walkthrough-creating-and-running-unit-tests-for-managed-code.md)bakın.

## <a name="run-unit-tests"></a>Birim testlerini çalıştırma

1. [Test Gezgini'ni](../test/run-unit-tests-with-test-explorer.md)aç.

   ::: moniker range=">=vs-2019"
   Test Gezgini'ni açmak için üst menü çubuğundan **Test** > **Gezgini'ni** seçin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Test Gezgini'ni açmak için üst menü çubuğundan **Windows** > **Test Gezgini'ni** **test** > edin'i seçin.
   ::: moniker-end

1. **Tümlerini Çalıştır'ı**tıklatarak birim testlerinizi çalıştırın.

   ![Test Gezgini ile birim testleri çalıştırma](media/vs-2019/test-explorer-run-all.png)

   Testler tamamlandıktan sonra, yeşil onay işareti bir testin geçtiğini gösterir. Kırmızı "x" simgesi, bir testin başarısız olduğunu gösterir.

   ![Test Gezgini'nde birim test sonuçlarını gözden geçirme](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Yerleşik test çerçevesinden (MSTest) veya üçüncü taraf test çerçevelerinden birim testleri çalıştırmak için [Test Gezgini'ni](../test/run-unit-tests-with-test-explorer.md) kullanabilirsiniz. Testleri kategorilere ayırabilir, test listesine filtre uygulayabilir ve testlerin çalma listeleri oluşturabilir, kaydedebilir ve çalıştırabilirsiniz. Ayrıca testleri hata ayıklayabilir ve test performansını ve kod kapsamını analiz edebilirsiniz.

## <a name="view-live-unit-test-results"></a>Canlı birim test sonuçlarını görüntüle

Visual Studio 2017 veya sonraki yıllarda MSTest, xUnit veya NUnit test çerçevesini kullanıyorsanız, birim testlerinizin canlı sonuçlarını görebilirsiniz.

> [!NOTE]
> Canlı birim testi yalnızca Enterprise sürümünde kullanılabilir.

1.  >  **Test****Canlı Birim Test** > **Başlat'ı**seçerek **Test** menüsünden canlı ünite testini açın.

   ::: moniker range="vs-2017"

   ![Canlı birim testini açma](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019'da canlı ünite testlerine başlayın](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Kod yazarken ve kodu ederken kod düzenleyicisi penceresindeki testlerin sonuçlarını görüntüleyin.

   ![Testlerin sonuçlarını görüntüleme](media/vs-2019/live-unit-testing-results.png)

1. Bu yöntemi kapsayan testlerin adları gibi daha fazla bilgi görmek için bir test sonuç göstergesini tıklatın.

   ![Test sonuç göstergelerini seçin](media/vs-2019/live-unit-testing-details.png)

Canlı birim testi hakkında daha fazla bilgi için Canlı [birim testine](../test/live-unit-testing-intro.md)bakın.

## <a name="generate-unit-tests-with-intellitest"></a>IntelliTest ile birim testleri oluşturma

IntelliTest çalıştırdığınızda, hangi testlerin başarısız olduğunu görebilir ve bunları düzeltmek için gerekli kodları ekleyebilirsiniz. Bir regresyon paketi sağlamak için bir test projesine kaydetmek için oluşturulan testlerden hangisini seçebilirsiniz. Kodunuzu değiştirirken, oluşturulan testleri kod değişikliklerinizle eşit tutmak için IntelliTest'i yeniden çalıştırın. Nasıl yapılacağını öğrenmek [için](../test/generate-unit-tests-for-your-code-with-intellitest.md)bkz.

> [!TIP]
> IntelliTest yalnızca .NET Framework'u hedefleyen yönetilen kod lar için kullanılabilir.

![IntelliTest ile birim testleri oluşturma](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Kod kapsamını analiz edin

Proje kodunuzun ne oranda aslında birim testleri gibi kodlanmış testler tarafından test edilen belirlemek için Visual Studio kod kapsamı özelliğini kullanabilirsiniz. Hatalara karşı etkili bir şekilde korunmak için, testlerinizin kodunuzu büyük ölçüde kullanmanız gerekir. Nasıl [yapılacağını](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)öğrenmek için bkz.

## <a name="use-a-third-party-test-framework"></a>Üçüncü taraf test çerçevesi kullanma

Visual Studio'da Boost, Google ve NUnit gibi üçüncü taraf test çerçevelerini kullanarak birim testleri çalıştırabilirsiniz. NuGet paketini seçtiğiniz çerçeveye yüklemek için **NuGet Paket Yöneticisi'ni** kullanın. Veya, NUnit ve xUnit test çerçeveleri için Visual Studio, gerekli NuGet paketlerini içeren önceden yapılandırılmış test proje şablonları içerir.

[NUnit](https://nunit.org/)kullanan birim testleri oluşturmak için:

1. Sınamak istediğiniz kodu içeren çözümü açın.

2. **Solution Explorer'da** çözüme sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin.

3. **NUnit Test Project proje** şablonu'nu seçin.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019'da NUnit test proje şablonu](media/vs-2019/nunit-test-project-template.png)

   **İleri'yi**tıklatın, projeyi adlandırın ve sonra **Oluştur'u**tıklatın.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Projeyi adlandırın ve oluşturmak için **Tamam'ı** tıklatın.

   ::: moniker-end

   Proje şablonu NUnit ve NUnit3TestAdapter nuget referansları içerir.

   ![NUnit NuÇözüm Gezgini'nde get bağımlılıkları](media/vs-2019/nunit-nuget-dependencies.png)

4. Test projesinden bir başvuruyu test etmek istediğiniz kodu içeren projeye ekleyin.

   **Solution Explorer'da**projeye sağ tıklayın ve ardından**Başvuru** **Ekle'yi** > seçin. (Başvurular veya **Bağımlılıklar** düğümünün sağ tıklama **References** menüsünden de bir başvuru ekleyebilirsiniz.)

5. Test yönteminize kod ekleyin.

   ![Birim test kodu dosyanıza kod ekleme](media/vs-2019/unit-test-method.png)

6. Testi Test **Explorer'dan** veya test koduna sağ tıklayarak ve **Test(ler) çalıştır'ı**seçerek çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

* [İzlenecek yol: Yönetilen kod için birim testleri oluşturma ve çalıştırma](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Birim Testleri Oluştur komutu](create-unit-tests-menu.md)
* [IntelliTest ile testler oluşturun](generate-unit-tests-for-your-code-with-intellitest.md)
* [Test Gezgini ile testleri çalıştırma](run-unit-tests-with-test-explorer.md)
* [Kod kapsamını analiz edin](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
