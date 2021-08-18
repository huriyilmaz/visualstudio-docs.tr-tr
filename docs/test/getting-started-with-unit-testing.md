---
title: Birim testini kullanmaya başlama
description: kod durumunu korumak ve müşterilerinizin yapabilmesi için hata ve hataları bulmak üzere birim testlerini tanımlamak ve çalıştırmak için Visual Studio kullanın.
ms.custom: SEO-VS-2020
ms.date: 08/10/2021
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 9141a94d1c100d798b90eeb7d0ce90d15d137b9ddefbbbd92c44a98cf356a5d7
ms.sourcegitcommit: 29a893fb8639ee1d64922e99bf424e10ecce30d5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121465128"
---
# <a name="get-started-with-unit-testing"></a>Birim testini kullanmaya başlama

kod durumunu korumak, kod kapsamı sağlamak ve müşterilerinizin yapabilmesi için hata ve hataları bulmak üzere birim testlerini tanımlamak ve çalıştırmak için Visual Studio kullanın. Kodunuzun düzgün çalıştığından emin olmak için birim testlerinizi sıklıkla çalıştırın.

Bu makalede, kod C# ve C++ kullanıyorsa, çizimler C# dilinde, ancak kavramlar ve Özellikler .NET dilleri, C++, Python, JavaScript ve TypeScript için geçerlidir.

## <a name="create-unit-tests"></a>Birim testleri oluşturma

Bu bölümde, birim testi projesinin nasıl oluşturulduğu açıklanmaktadır.

1. Visual Studio test etmek istediğiniz projeyi açın.

   Örnek birim testi gösterimi amacıyla, bu makalede **HelloWorld** adlı basit bir "Merhaba Dünya" C# veya C++ konsol projesi (C# ' de **Merhaba Dünya çekirdeği** ) test eder. Bu tür bir projenin örnek kodu aşağıdaki gibidir:

   ### <a name="net"></a>[.NET](#tab/dotnet)
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

   ### <a name="c"></a>[C++](#tab/cpp)
   ```cpp
   #include <iostream>

   int main()
   {
      std::cout << "Hello World!\n";
   }
   ```
   ---

1. **Çözüm Gezgini**, çözüm düğümünü seçin. ardından, üst menü çubuğundan **dosya**  >  **ekle**  >  **yeni Project**' yi seçin.

1. Yeni proje iletişim kutusunda, kullanmak istediğiniz test çerçevesi için MSTest (C#) veya **yerel birim test** projesi (C++) gibi bir birim testi proje şablonu bulun ve seçin.

   Visual Studio 2017 sürüm 14,8 ' den başlayarak, .net dilleri nunit ve xunit için yerleşik şablonlar içerir. C++ için, bu örnekte Microsoft yerel birim testi çerçevesini kullanan **yerel birim testi** projesi ' ni seçin. (Farklı bir C++ test çerçeveleri kullanmak için bkz. [C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)). Python için bkz. test projenizi ayarlamak için [Python kodunda birim testi ayarlama](../python/unit-testing-python-in-visual-studio.md) .

   > [!TIP]
   > Yalnızca C# için, daha hızlı bir yöntem kullanarak koddan birim testi projeleri oluşturabilirsiniz. Daha fazla bilgi için bkz. [birim testi projeleri ve test yöntemleri oluşturma](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods). bu yöntemi .net Core veya .NET Standard ile kullanmak için, Visual Studio 2019 gerekir.

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

   ![Visual Studio proje başvurusu Ekle](media/vs-2019/reference-manager.png)

1. Birim testi yöntemine kod ekleyin.

   Örneğin, test çerçevesinden eşleşen doğru belge sekmesini seçerek aşağıdaki kodu kullanabilirsiniz: MSTest, NUnit veya xUnit (yalnızca .NET üzerinde desteklenir) veya C++ Microsoft birim testi çerçevesi.

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
               HelloWorldCore.Program.Main();

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
               HelloWorldCore.Program.Main();

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
                    HelloWorldCore.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

    ### <a name="microsoft-native-unit-test-framework"></a>[Microsoft yerel birim test çerçevesi](#tab/msunittest)

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

1. [Test Gezgini](../test/run-unit-tests-with-test-explorer.md)'ni açın.

   ::: moniker range=">=vs-2019"
   Test Gezgini 'ni açmak için  > üst menü çubuğundan test **Test Gezgini** ' ni seçin (veya **CTRL** + **E**, **T**'ye basın).
   ::: moniker-end
   ::: moniker range="vs-2017"
   test gezgini 'ni açmak için  >  > üst menü çubuğundan test Windows test **gezgini** ' ni seçin.
   ::: moniker-end

1. **Tümünü Çalıştır** ' a tıklayarak birim testlerinizi çalıştırın (veya **CTRL**  +  **R**, **V** tuşlarına basın).

   ![Test Gezgini ile birim testleri çalıştırma](media/vs-2019/test-explorer-run-all.png)

   Testler tamamlandıktan sonra yeşil onay işareti bir testin geçtiğini gösterir. Kırmızı bir "x" simgesi testin başarısız olduğunu gösterir.

   ![Test Gezgini 'nde birim test sonuçlarını gözden geçirme](media/vs-2019/unit-test-passed.png)

> [!TIP]
> [Test Gezgini](../test/run-unit-tests-with-test-explorer.md) 'ni, yerleşik test çerçevesinden (MSTest) veya üçüncü taraf test çerçevelerinden birim testlerini çalıştırmak için kullanabilirsiniz. Testleri kategoriler halinde gruplandırabilir, test listesine filtre uygulayabilir ve testlerin çalma listelerini oluşturabilir, kaydedebilir ve çalıştırabilirsiniz. Ayrıca, testlerin hatalarını ayıklayabilir ve test performansını ve kod kapsamını çözümleyebilirsiniz.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>Canlı birim testi sonuçlarını görüntüle (Visual Studio Enterprise)

Visual Studio 2017 veya sonraki sürümlerde MSTest, xunit veya nunit test çerçevesini kullanıyorsanız, birim testlerinizin canlı sonuçlarını görebilirsiniz.

> [!NOTE]
> bu adımları izlemek için, .net kodu ve şu test çerçevelerinden biri ile birlikte Visual Studio Enterprise gereklidir: MSTest, xunit veya nunit.

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

programlama dilinize bağlı olarak nunit, Boost veya Google C++ test çerçevesi gibi üçüncü taraf test çerçeveleri kullanarak Visual Studio birim testlerini çalıştırabilirsiniz. Bir üçüncü taraf çerçevesini kullanmak için:

- seçtiğiniz çerçeveye ait NuGet paketini yüklemek için **NuGet Paket Yöneticisi** kullanın.

- .Net Visual Studio 2017 sürüm 14,6 ' den başlayarak, Visual Studio nunit ve xunit test çerçeveleri için önceden yapılandırılmış test projesi şablonlarını içerir. şablonlar, desteği etkinleştirmek için gerekli NuGet paketlerini de içerir.

- C++ Visual Studio 2017 ve sonraki sürümlerinde, Google C++ test çerçevesi gibi bazı çerçeveler zaten dahil edilmiştir. Daha fazla bilgi için bkz. [Visual Studio 'de C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md).

Birim testi projesi eklemek için:

1. Test etmek istediğiniz kodu içeren çözümü açın.

2. **Çözüm Gezgini** çözüme sağ tıklayın ve   >  **yeni Project** ekle ' yi seçin.

3. Bir birim testi proje şablonu seçin.

   Bu örnekte, [NUnit](https://nunit.org/) ' i seçin

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 ' de nunit test proje şablonu](media/vs-2019/nunit-test-project-template.png)

   **İleri**' ye tıklayın, projeyi adlandırın ve ardından **Oluştur**' a tıklayın.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Projeyi adlandırın ve ardından oluşturmak için **Tamam** ' ı tıklatın.

   ::: moniker-end

   proje şablonu nunit ve NUnit3TestAdapter için NuGet başvurular içerir.

   ![Çözüm Gezgini nunit NuGet bağımlılıkları](media/vs-2019/nunit-nuget-dependencies.png)

4. Test projesinden test etmek istediğiniz kodu içeren projeye bir başvuru ekleyin.

   **Çözüm Gezgini**' de projeye sağ tıklayın ve ardından başvuru **Ekle**' yi seçin  >  . ( **Başvurular** veya **Bağımlılıklar** düğümünün sağ tıklama menüsünde de bir başvuru ekleyebilirsiniz.)

5. Test yönteminiz için kod ekleyin.

   ![Birim test kodu dosyanıza kod ekleme](media/vs-2019/unit-test-method.png)

6. Test **Gezgini** 'nden veya test kodu ' **na** sağ tıklayıp (veya **CTRL**  +  **R**, **T**) Testi Çalıştır ' ı seçerek testi çalıştırın.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Birim testi temel bilgileri](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [Yönetilen kod için birim testleri oluşturma ve çalıştırma](walkthrough-creating-and-running-unit-tests-for-managed-code.md)

> [!div class="nextstepaction"]
> [C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)
