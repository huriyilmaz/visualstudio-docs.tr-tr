---
title: Birim testini kullanmaya başlama
description: Kod Visual Studio korumak ve müşterilerinizden önce hataları ve hataları bulmak için birim testleri tanımlamak ve çalıştırmak için Visual Studio kullanın.
ms.custom: SEO-VS-2020
ms.date: 12/16/2021
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 88bf2b8abe3356070550133ce788d4b9a339127f
ms.sourcegitcommit: d3578c384959f1b76dd06fb4b5d075fb052f8c69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2021
ms.locfileid: "135375164"
---
# <a name="get-started-with-unit-testing"></a>Birim testini kullanmaya başlama

Kod Visual Studio korumak, kod kapsamından emin olmak ve müşterilerinizden önce hataları ve hataları bulmak için birim testleri tanımlamak ve çalıştırmak için Visual Studio kullanın. Kodunuzun düzgün çalıştığından emin olmak için birim testlerinizi sık sık çalıştırın.

Bu makalede kod C# ve C++ kullanır, çizimler C# dilindedir, ancak kavramlar ve özellikler .NET dilleri, C++, Python, JavaScript ve TypeScript için geçerlidir.

## <a name="create-unit-tests"></a>Birim testleri oluşturma

Bu bölümde, birim testi projesinin nasıl oluşturularak ilgili açıklama yer almaktadır.

1. Test etmek istediğiniz projeyi Visual Studio.

   Örnek bir birim testinin amacı doğrultusunda, bu makale HelloWorld adlı basit bir "Merhaba Dünya" C# veya C++ Konsol **projesini test ediyor.** Böyle bir projenin örnek kodu aşağıdaki gibidir:

   ### <a name="net"></a>[.NET](#tab/dotnet)
   ```csharp
   namespace HelloWorld
   {
      public class Program
      {
         public static void Main()
         {
            Console.WriteLine("Hello World!");
         }
      }
   }
   ```

   ### <a name="c"></a>[C++](#tab/cpp)
   ```cpp
   #include <iostream>

   int main()
   {
      std::cout << "Hello World!\n";
   }
   ```
   ---

1. Bu **Çözüm Gezgini** çözüm düğümünü seçin. Ardından üst menü çubuğundan Dosya Ekle Yeni **Ekle'yi**  >    >  **Project.**

1. Yeni proje iletişim kutusunda, kullanmak üzere birim testi projesini bulun.

   ::: moniker range=">=vs-2019"
   **MSTest** (C#) veya Yerel Birim Testi projesi (C++) gibi kullanmak istediğiniz **test** çerçevesine yönelik bir birim testi proje şablonu bulmak için arama kutusuna **test** yazın ve seçin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Yüklü **düğümünü** genişletin, test projeniz için kullanmak istediğiniz dili seçin ve ardından Test'i **seçin.**
   ::: moniker-end

   2017 Visual Studio 14.8 sürümünden itibaren .NET dilleri NUnit ve xUnit için yerleşik şablonlar içerir. C++ için, bu örnekte Microsoft **Yerel Birim Testi** Çerçevesi'nin kullandığı Yerel Birim Testi projesini seçin. (Farklı bir C++ test çerçevesi kullanmak için [bkz. C/C++ için birim testleri yazma).](../test/writing-unit-tests-for-c-cpp.md) Python için test [projenizi ayarlamak için bkz. Python kodunda](../python/unit-testing-python-in-visual-studio.md) birim testi ayarlama.

   > [!TIP]
   > Yalnızca C# için daha hızlı bir yöntem kullanarak koddan birim testi projeleri oluşturabilirsiniz. Daha fazla bilgi için [bkz. Birim testi projeleri ve test yöntemleri oluşturma.](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods-c) Bu yöntemi .NET Core veya .NET Standard kullanmak için Visual Studio 2019 gerekir.

   Aşağıdaki çizimde. .NET'te desteklenen bir MSTest birim testi gösterilmiştir.

   ::: moniker range=">=vs-2022"

   ![Visual Studio 2022'de birim testi proje şablonu](media/vs-2022/add-new-test-project.png)

   **Sonraki'ye** tıklayın, test projesi için bir ad seçin ve ardından Oluştur'a **tıklayın.**

   ::: moniker-end
   ::: moniker range="vs-2019"

   ![Visual Studio 2019'da birim testi proje şablonu](media/vs-2019/add-new-test-project.png)

   **Sonraki'ye** tıklayın, test projesi için bir ad seçin ve ardından Oluştur'a **tıklayın.**

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Visual Studio 2017'de birim testi proje şablonu](media/mstest-test-project-template.png)

   Test projesi için HelloWorldTests gibi bir ad seçin ve ardından Tamam'a **tıklayın.**

   ::: moniker-end

   Proje çözümünüze eklenir.

   ::: moniker range=">=vs-2022"
   ![Çözüm Gezgini'de birim testi projesi](media/vs-2022/solution-explorer.png)
   ::: moniker-end
   ::: moniker range="<=vs-2019"
   ![Çözüm Gezgini'de birim testi projesi](media/vs-2019/solution-explorer.png)
   ::: moniker-end

1. Birim testi projesinde, Başvurular veya Bağımlılıklar'a sağ tıklar ve  ardından Başvuru  Ekle veya Başvuru Ekle'yi seçerek test etmek istediğiniz projeye bir **Project ekleyin.** 

1. Test etmek istediğiniz kodu içeren projeyi seçin ve Tamam'a **tıklayın.**

   ::: moniker range=">=vs-2022"
   ![Projeye proje başvurusu Visual Studio](media/vs-2022/reference-manager.png)
   ::: moniker-end
   ::: moniker range="<=vs-2019"
   ![Projeye proje başvurusu Visual Studio](media/vs-2019/reference-manager.png)
   ::: moniker-end

1. Birim testi yöntemine kod ekleyin.

   Örneğin, test çerçeveniz ile eşleşen doğru belge sekmesini seçerek aşağıdaki kodu kullanabilirsiniz: MSTest, NUnit veya xUnit (yalnızca .NET'te desteklenen) veya C++ Microsoft Yerel Birim Test Çerçevesi.

   ### <a name="mstest"></a>[MSTest](#tab/mstest)

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
               HelloWorld.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

   ### <a name="nunit"></a>[NUnit](#tab/nunit)

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
               HelloWorld.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

    ### <a name="xunit"></a>[xUnit](#tab/xunit)

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
                    HelloWorld.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

    ### <a name="microsoft-native-unit-test-framework"></a>[Microsoft Yerel Birim Test Çerçevesi](#tab/msunittest)

    ```cpp
    #include "pch.h"
    #include "CppUnitTest.h"
    #include "../HelloWorldUnitTestCPP/HelloWorldUnitTestCPP.cpp"   // Update using your project name

    using namespace Microsoft::VisualStudio::CppUnitTestFramework;

    namespace HelloWorldTests
    {
       TEST_CLASS(HelloWorldTests)
       {
       public:

          TEST_METHOD(TestMethod)
          {
             std::string expected = "Hello World!\n";

             std::stringstream buffer;
             std::streambuf* sbuf = std::cout.rdbuf(); // Save cout's buffer
             std::cout.rdbuf(buffer.rdbuf()); // Redirect cout to the stringstream buffer

             // Call main() in your test
             int result = main();

             // When finished, redirect cout to the original buffer 
             std::cout.rdbuf(sbuf);
             std::cout << "std original buffer: \n";
             std::cout << buffer.get();

             // Test
             Assert::AreEqual(expected, buffer.str());
          }
       };
    }
    ```

    ---

## <a name="run-unit-tests"></a>Birim testlerini çalıştırma

1. [Test Gezgini'ni açın.](../test/run-unit-tests-with-test-explorer.md)

   ::: moniker range=">=vs-2019"
   Test Gezgini'ni açmak için üst menü **çubuğundan Test** Gezgini'ni seçin >  (veya **Ctrl** E , T + **tuşlarına** **basın).**
   ::: moniker-end
   ::: moniker range="vs-2017"
   Test Gezgini'ni açmak **için** üst menü çubuğundan Test Gezgini Windows Test >  >  Gezgini'ni seçin.
   ::: moniker-end

1. Birim testlerinizi çalıştırmak için Hepsini **Çalıştır'a tıklayın** (veya **Ctrl**  +  **R**, **V tuşlarına basın).**

   ::: moniker range=">=vs-2022"
   ![Test Gezgini ile birim testleri çalıştırma](media/vs-2022/test-explorer-run-all.png)
   ::: moniker-end
   ::: moniker range="<=vs-2019"
   ![Test Gezgini ile birim testleri çalıştırma](media/vs-2019/test-explorer-run-all.png)
   ::: moniker-end

   Testler tamamlandıktan sonra yeşil onay işareti testin başarılı olduğunu gösterir. Kırmızı "x" simgesi testin başarısız olduğunu gösterir.

   ::: moniker range=">=vs-2022"
   ![Test Gezgini'nde birim testi sonuçlarını gözden geçirme](media/vs-2022/unit-test-passed.png)
   ::: moniker-end
   ::: moniker range="<=vs-2019"
   ![Test Gezgini'nde birim testi sonuçlarını gözden geçirme](media/vs-2019/unit-test-passed.png)
   ::: moniker-end

> [!TIP]
> Yerleşik test [çerçevesinden](../test/run-unit-tests-with-test-explorer.md) (MSTest) veya üçüncü taraf test çerçevelerinden birim testleri çalıştırmak için Test Gezgini'ni kullanabilirsiniz. Testleri kategorilere gruplandırabilir, test listesini filtrenin ve testlerin çalma listelerini oluşturabilir, kaydedebilir ve çalıştırabilirsiniz. Ayrıca testlerde hata ayıklar, test performansını ve kod kapsamayı analiz edersiniz.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>Canlı birim testi sonuçlarını görüntüleme (Visual Studio Enterprise)

Visual Studio 2017 veya sonraki bir yıl içinde MSTest, xUnit veya NUnit test çerçevesini kullanıyorsanız birim testlerinin canlı sonuçlarını görüntüebilirsiniz.

> [!NOTE]
> Bu adımları takip etmek Visual Studio Enterprise .NET kodu ve şu test çerçevelerinden biri ile birlikte gereklidir: MSTest, xUnit veya NUnit.

1. Test menüsünde Test ve **Başlat** seçeneğini kullanarak canlı birim   >  **Live Unit Testing**  >  **açın.**

   ::: moniker range="vs-2017"

   ![Canlı birim testlerini açma](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019'da canlı birim testlerini başlatma](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   ![Visual Studio 2022'de canlı birim testlerini başlatma](media/vs-2022/start-live-unit-testing.png)

   ::: moniker-end

1. Kod yazıp düzenlerken kod düzenleyicisi penceresinde testlerin sonuçlarını görüntüleme.

   ::: moniker range="<=vs-2019"
   ![Testlerin sonuçlarını görüntüleme](media/vs-2019/live-unit-testing-results.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Testlerin sonuçlarını görüntüleme](media/vs-2022/live-unit-testing-results.png)
   ::: moniker-end

1. Bir test sonucu göstergesine tıklar ve bu yöntemin üzerinde yer alan testlerin adları gibi daha fazla bilgi elde edin.

   ::: moniker range="<=vs-2019"
   ![Test sonucu göstergelerini seçme](media/vs-2019/live-unit-testing-details.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Test sonucu göstergelerini seçme](media/vs-2022/live-unit-testing-details.png)
   ::: moniker-end

Canlı birim testi hakkında daha fazla bilgi için bkz. [Canlı birim testi.](../test/live-unit-testing-intro.md)

## <a name="use-a-third-party-test-framework"></a>Üçüncü taraf test çerçevesi kullanma

Programlama dilinize bağlı Visual Studio NUnit, Boost veya Google C++ Test Çerçevesi gibi üçüncü taraf test çerçevelerini kullanarak birim testlerini Visual Studio'de çalıştırarak birim testlerini çalıştırın. Üçüncü taraf çerçeve kullanmak için:

- Tercih **NuGet Paket Yöneticisi** çerçeveye NuGet paketini yüklemek için NuGet paketini kullanın.

- (.NET) 2017 Visual Studio 14.6 sürümünden başlayarak, Visual Studio NUnit ve xUnit test çerçeveleri için önceden yapılandırılmış test projesi şablonları içerir. Şablonlar, desteği etkinleştirmek için gerekli NuGet paketleri de içerir.

- (C++) 2017 Visual Studio ve sonraki sürümlerde Google C++ Test Çerçevesi gibi bazı çerçeveler zaten dahil edildi. Daha fazla bilgi için [bkz. C/C++ için](../test/writing-unit-tests-for-c-cpp.md)birim testleri yazma Visual Studio.

Birim testi projesi eklemek için:

1. Test etmek istediğiniz kodu içeren çözümü açın.

2. içinde çözüme sağ tıklayın ve **Çözüm Gezgini**   >  **Ekle'yi Project.**

3. Bir birim testi proje şablonu seçin.

   Bu örnekte [NUnit'i seçin](https://nunit.org/)

   ::: moniker range=">=vs-2022"
   ![Visual Studio 2022'de NUnit test projesi şablonu](media/vs-2022/nunit-test-project-template.png)
   ::: moniker-end

   ::: moniker range="vs-2019"
   ![Visual Studio 2019'da NUnit test projesi şablonu](media/vs-2019/nunit-test-project-template.png)

   **Sonraki'ye** tıklayın, projeyi olarak ad girin ve ardından Oluştur'a **tıklayın.**
   ::: moniker-end

   ::: moniker range="vs-2017"
   Projeye bir ad ve ardından **tamam'a** tıklar ve projeyi oluşturun.
   ::: moniker-end

   Proje şablonu NUnit ve NUnit3TestAdapter'a NuGet başvurularını içerir.

   ::: moniker range=">=vs-2022"
   ![NUnit NuGet bağımlılıkları Çözüm Gezgini](media/vs-2022/nunit-nuget-dependencies.png)
   ::: moniker-end
   ::: moniker range="<=vs-2019"
   ![NUnit NuGet bağımlılıkları Çözüm Gezgini](media/vs-2019/nunit-nuget-dependencies.png)
   ::: moniker-end

4. Test projesinden test etmek istediğiniz kodu içeren projeye bir başvuru ekleyin.

   içinde projeye sağ tıklayın ve **Çözüm Gezgini** **Ekle'yi**  >  **seçin.** (Ayrıca, Başvurular veya Bağımlılıklar düğümünün sağ tıklama **menüsünden de** **başvuru ekleyebilirsiniz.)**

5. Test yönteminize kod ekleyin.

   ::: moniker range=">=vs-2022"
   ![Birim testi kod dosyanıza kod ekleme](media/vs-2022/unit-test-method.png)
   ::: moniker-end
   ::: moniker range="<=vs-2019"
   ![Birim testi kod dosyanıza kod ekleme](media/vs-2019/unit-test-method.png)
   ::: moniker-end

6. **Testi** Test Gezgini'nde çalıştırın veya test koduna sağ tıklar ve Testleri Çalıştır 'ı (veya **Ctrl** R ,   +   **T) seçin.**

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Birim testi temel bilgileri](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [Yönetilen kod için birim testleri oluşturma ve çalıştırma](walkthrough-creating-and-running-unit-tests-for-managed-code.md)

> [!div class="nextstepaction"]
> [C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)
