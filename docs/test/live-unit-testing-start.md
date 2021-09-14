---
title: Live Unit Test ile kodunuzu test etmeyi öğrenin
description: Live Unit Testing'i hedef alan basit bir sınıf kitaplığı .NET Standard ve test etmek için .NET Core'ı hedef alan bir MSTest projesi oluşturarak bu kitaplığı kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/03/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- dotnet
ms.openlocfilehash: 2041845ab82ec539ccaec0befd3275aeab7c0493
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628106"
---
# <a name="get-started-with-live-unit-testing"></a>Live Unit Testing kullanmaya başlama

Bir çözümde Live Unit Testing etkinleştir Visual Studio, test kapsamınızı ve testlerin durumunu görsel olarak gösterir. Live Unit Testing ayrıca kodunuzu değiştirerek testleri dinamik olarak yürütür ve değişiklikleriniz testlerin başarısız olması durumuna neden olduğunda hemen size haber eder.

Live Unit Testing, .NET Core veya .NET Core'.NET Framework çözümleri test etmek için kullanılabilir. Bu öğreticide, .NET Standard'ı hedef alan basit bir sınıf kitaplığı oluşturarak Live Unit Testing'ı kullanmayı öğrenecek ve test etmek için .NET Core'ı hedef alan bir MSTest projesi oluştur bulacaksınız.

C# çözümünün eksiksiz bir şekilde indirildikten sonra [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) GitHub.

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici, **.NET Core** platformlar arası Visual Studio Enterprise iş yüküyle bir sürüm yüklemesini gerektirir.

## <a name="create-the-solution-and-the-class-library-project"></a>Çözümü ve sınıf kitaplığı projesini oluşturma

StringLibrary adlı Visual Studio sınıf kitaplığı projesini içeren UtilityLibraries adlı .NET Standard bir çözüm oluşturarak başlayabilirsiniz.

Çözüm yalnızca bir veya daha fazla proje için bir kapsayıcıdır. Boş bir çözüm oluşturmak için Visual Studio açın ve şunları yapın:

1. Üst **düzey**  >  **Project**  >   Menüsünden Dosya Yeni Dosya Visual Studio seçin.

1. Şablon **arama** kutusuna çözüm yazın ve Boş Çözüm **şablonunu** seçin. Projeye **UtilityLibraries adını girin.**

   ::: moniker range="vs-2017"

   ![**Yeni Project** iletişim kutusu](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Çözümü oluşturmayı bitirin.

Artık çözümü oluşturduğunuza göre dizelerle çalışmak için bir dizi uzantı yöntemi içeren StringLibrary adlı bir sınıf kitaplığı oluşturabilirsiniz.

1. Bu **Çözüm Gezgini** Yardımcı Programlar çözümüne sağ tıklayın ve Yeni Ekle'yi **Project.**  >  

::: moniker range="vs-2017"

2. Yeni Dosya **Ekle iletişim Project** C# düğümünü seçin ve sonra da yeni .NET Standard. 

   > [!NOTE]
   > Kitaplığımız belirli .NET Standard bir .NET uygulaması yerine bir .NET uygulamasını hedeflese de, bu .NET uygulamasının bu sürümünü destekleyen herhangi bir .NET uygulamasından .NET Standard. Daha fazla bilgi için [bkz. .NET Standard.](/dotnet/standard/net-standard)

3. Sağ **bölmede Sınıf Kitaplığı (.NET Standard)** şablonunu seçin ve Aşağıdaki çizimde  gösterildiği gibi Ad metin kutusuna **StringLibrary** yazın:

   ![**Yeni Dosya Ekle** Project iletişim kutusu](./media/lut-start/add-project-cs.png)

4. Projeyi oluşturmak için **Tamam**'ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. Sınıf **kitaplığını** şablon arama kutusuna yazın ve Sınıf Kitaplığı **(.NET Standard) şablonunu** seçin. **İleri**’ye tıklayın.

   > [!NOTE]
   > Kitaplığımız belirli .NET Standard bir .NET uygulaması yerine bir .NET uygulamasını hedeflese de, bu .NET uygulamasının bu sürümünü destekleyen herhangi bir .NET uygulamasından .NET Standard. Daha fazla bilgi için [bkz. .NET Standard.](/dotnet/standard/net-standard)

3. Projeyi **StringLibrary olarak adlandır.**

4. Projeyi **oluşturmak için** Oluştur'a tıklayın.

::: moniker-end

5. Kod düzenleyicisinde var olan tüm kodu aşağıdaki kodla değiştirin:

   ```csharp
   using System;

   namespace UtilityLibraries
   {
       public static class StringLibrary
       {
           public static bool StartsWithUpper(this string s)
           {
               if (String.IsNullOrWhiteSpace(s))
                   return false;

               return Char.IsUpper(s[0]);
           }

           public static bool StartsWithLower(this string s)
           {
               if (String.IsNullOrWhiteSpace(s))
                   return false;

               return Char.IsLower(s[0]);
           }

           public static bool HasEmbeddedSpaces(this string s)
           {
               foreach (var ch in s.Trim())
               {
                   if (ch == ' ')
                       return true;
               }
               return false;
           }
       }
   }
   ```

   StringLibrary'nin üç statik yöntemi vardır:

   - `StartsWithUpper` , `true` bir dize büyük harf karakterle başlıyorsa döndürür; aksi takdirde `false` döndürür.

   - `StartsWithLower`, `true` bir dize küçük harf karakterle başlıyorsa, aksi takdirde `false` döndürür.

   - `HasEmbeddedSpaces` , `true` bir dize katıştırılmış bir boşluk karakteri içeriyorsa döndürür; aksi takdirde `false` döndürür.

6. Üst **düzey**  >  **derleme menüsünde** Derleme Çözümü'Visual Studio seçin. Derlemenin başarılı olması gerekir.

## <a name="create-the-test-project"></a>Test projesini oluşturma

Sonraki adım, StringLibrary kitaplığını test etmek için birim testi projesi oluşturmaktır. Aşağıdaki adımları gerçekleştirerek birim testlerini oluşturun:

1. Bu **Çözüm Gezgini** Yardımcı Programlar çözümüne sağ tıklayın ve Yeni Ekle'yi **Project.**  >  

::: moniker range="vs-2017"

2. Yeni Dosya **Ekle iletişim Project** C# düğümünü ve ardından **.NET Core'ı seçin.**

   > [!NOTE]
   > Birim testlerinizi sınıf kitaplığınız ile aynı dilde yazmanız zorunda değildir.

3. Sağ **bölmede Birim Testi Project (.NET Core)** şablonunu seçin ve Aşağıdaki çizimde  gösterildiği gibi Ad metin kutusuna **StringLibraryTests** yazın:

   ![Birim testi projesi için **Project Ekle** iletişim kutusu](./media/lut-start/add-unit-test-cs.png)

4. Projeyi oluşturmak için **Tamam**'ı seçin.

   > [!NOTE]
   > Bu başlarken öğreticisinde MSTest test Live Unit Testing ile ilgili temel bilgi 2011 ve 2. xUnit ve NUnit test çerçevelerini de kullanabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

2. Şablon **arama kutusuna** birim testi yazın, dil olarak **C#** öğesini seçin ve ardından .NET Core Project Birim Testi şablonunu seçin.  **İleri**’ye tıklayın.

   > [!NOTE]
   > 2019 Visual Studio 16.9 sürümünden başlayarak, MSTest proje şablonu adı **MSTest Birim Testi Project (.NET Core)** olarak Birim **Testi** Project.

3. Projeyi **StringLibraryTests olarak adlandırarak Sonraki'ye** **tıklayın.**

4. Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   > [!NOTE]
   > Bu başlarken öğreticisinde MSTest test Live Unit Testing ile ilgili temel bilgi 2011 ve 2. xUnit ve NUnit test çerçevelerini de kullanabilirsiniz.

::: moniker-end

5. Birim testi projesi, testte olduğu sınıf kitaplığına otomatik olarak erişe değil. Sınıf kitaplığı projesine bir başvuru ekleyerek test kitaplığı erişimi verirsiniz. Bunu yapmak için projeye sağ tıklayın ve `StringLibraryTests` Başvuru **Ekle'yi**  >  **seçin.** Başvuru **Yöneticisi iletişim** kutusunda,  Çözüm sekmesinin seçili olduğundan emin olun ve aşağıdaki çizimde gösterildiği gibi StringLibrary projesini seçin.

   ![**Başvuru Yöneticisi** iletişim kutusu](./media/lut-start/add-reference.png)

6. Şablon tarafından sağlanan ortak birim test kodunu aşağıdaki kodla değiştirin:

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using UtilityLibraries;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestStartsWithUpper()
           {
               // Tests that we expect to return true.
               string[] words = { "Alphabet", "Zebra", "ABC", "Αθήνα", "Москва" };
               foreach (var word in words)
               {
                   bool result = word.StartsWithUpper();
                   Assert.IsTrue(result,
                                 $"Expected for '{word}': true; Actual: {result}");
               }
           }

           [TestMethod]
           public void TestDoesNotStartWithUpper()
           {
               // Tests that we expect to return false.
               string[] words = { "alphabet", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                                  "1234", ".", ";", " " };
               foreach (var word in words)
               {
                   bool result = word.StartsWithUpper();
                   Assert.IsFalse(result,
                                  $"Expected for '{word}': false; Actual: {result}");
               }
           }

           [TestMethod]
           public void DirectCallWithNullOrEmpty()
           {
               // Tests that we expect to return false.
               string[] words = { String.Empty, null };
               foreach (var word in words)
               {
                   bool result = StringLibrary.StartsWithUpper(word);
                   Assert.IsFalse(result,
                                  $"Expected for '{(word == null ? "<null>" : word)}': " +
                                  $"false; Actual: {result}");
               }
           }
       }
   }
   ```

7. Araç çubuğundaki Kaydet simgesini **seçerek** projenizi kaydedin.

   Birim testi kodu ASCII olmayan bazı karakterlere sahip olduğundan, dosyayı varsayılan ASCII biçiminde kaydetmenizi sağlarsanız bazı karakterlerin kaybolacak uyarısı için aşağıdaki iletişim kutusunu görüntülersiniz.

8. Diğer Kodlama **ile Kaydet düğmesini** seçin.

   ![Dosya kodlaması seçme](media/lut-start/ascii-encoding.png)

9. Gelişmiş **Kaydetme Seçenekleri** iletişim kutusunun  Kodlama açılan listesinde, aşağıdaki çizimde gösterildiği gibi Unicode (imza olmadan **UTF-8) - Codepage 65001**'i seçin:

   ![UTF-8 kodlamasını seçme](media/lut-start/utf8-encoding.png)

10. Üst düzey derleme menüsünden Çözümü **Yeniden**  >   Derle'yi seçerek birim testi Visual Studio derle.

Bir sınıf kitaplığının yanı sıra bunun için bazı birim testleri de oluşturdunız. Artık bu aracı kullanmak için gereken ön Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Enable Live Unit Testing

Şu ana kadar StringLibrary sınıf kitaplığı için testleri yazmadınız ancak bunları yürütmedisiniz. Live Unit Testing etkinleştiren otomatik olarak yürütülür. Bunu yapmak için şunları yapın:

1. İsteğe bağlı olarak, StringLibrary kodunu içeren kod düzenleyicisi penceresini seçin. Bu, bir *C# projesi için Class1.cs* veya bir C# projesi için *Class1.vb* Visual Basic olur. (Bu adım, testlerinizi etkinleştiren testleri ve kod kapsamı kapsamını görsel olarak incelemenize Live Unit Testing.)

1. Üst   >  **düzey Live Unit Testing** Başlat  >  **menüsünden** Test Visual Studio seçin.

1. Visual Studio tüm testlerinizi otomatik olarak çalıştıran Canlı Birim Testi'ne başlar.

::: moniker range="vs-2017"
Test Gezgini, testlerinizi **çalıştırmayı tamamlarsa hem** genel sonuçları hem de tek tek testlerin sonuçlarını görüntüler. Ayrıca, kod düzenleyicisi penceresi hem test kodu kapsamınızı hem de test sonuçlarınızı grafiksel olarak görüntüler. Aşağıdaki çizimde gösterildiği gibi üç test de başarıyla yürütülür. Ayrıca testlerimizin yönteminde tüm kod yollarını kapsamıştır ve bu testlerin hepsi başarıyla yürütülür (yeşil onay `StartsWithUpper` işaretiyle ""). Son olarak, StringLibrary'de diğer yöntemlerden hiçbirinin kod kapsamına sahip olduğunu (mavi çizgiyle gösterilen "➖").

![Canlı Birim testi başladıktan sonra Test Gezgini ve kod düzenleyicisi penceresi](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019&quot;
Testlerinizi çalıştırmanız tamamlansa **Live Unit Testing** sonuçları ve tek tek testlerin sonuçlarını görüntüler. Ayrıca, kod düzenleyicisi penceresi hem test kodu kapsamınızı hem de test sonuçlarınızı grafiksel olarak görüntüler. Aşağıdaki çizimde gösterildiği gibi üç test de başarıyla yürütülür. Ayrıca testlerimizin yönteminde tüm kod yollarını kapsamıştır ve bu testlerin hepsi başarıyla yürütülür (yeşil onay `StartsWithUpper` işaretiyle &quot;"). Son olarak, StringLibrary'de diğer yöntemlerden hiçbirinin kod kapsamına sahip olduğunu (mavi çizgiyle gösterilen "➖").

![Canlı Birim testi başladıktan sonra Canlı Test Gezgini ve kod düzenleyicisi penceresi](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

Ayrıca, kod düzenleyicisi penceresinde belirli bir kod kapsamı simgesini seçerek test kapsamı ve test sonuçları hakkında daha ayrıntılı bilgi edinebilirsiniz. Bu ayrıntıyı incelemek için şunları yapın:

1. yönteminde okunan satırda yeşil onay `if (String.IsNullOrWhiteSpace(s))` işaretine `StartsWithUpper` tıklayın. Aşağıdaki çizimde gösterildiği gibi, Live Unit Testing üç testin bu kod satırına yer ve hepsinin başarıyla yürütülmektedir.

   !['if' koşullu deyimi için kod kapsamı](media/lut-start/code-coverage-cs1.png)

1. yönteminde okunan satırda yeşil onay `return Char.IsUpper(s[0])` işaretine `StartsWithUpper` tıklayın. Aşağıdaki çizimde gösterildiği gibi, Live Unit Testing yalnızca iki testin bu kod satırını kapsadığını ve tümünün başarıyla yürütüldüğünü gösterir.

   ![Return ifadesinin kod kapsamı](media/lut-start/code-coverage-cs2.png)

Live Unit Testing tanımladığı önemli sorun, tamamlanmamış kod kapsamı. Sonraki bölümde bu adresi görürsünüz.

## <a name="expand-test-coverage"></a>Test kapsamını Genişlet

Bu bölümde, birim testlerinizi yöntemine genişleteceksiniz `StartsWithLower` . Bunu yaptığınızda, Live Unit Testing kodunuzu test etmek için dinamik olarak devam eder.

Kod kapsamını yöntemine genişletmek için `StartsWithLower` aşağıdakileri yapın:

1. Aşağıdaki `TestStartsWithLower` ve `TestDoesNotStartWithLower` yöntemlerini projenizin test kaynak kodu dosyasına ekleyin:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet1":::

1. Yöntemine yapılan `DirectCallWithNullOrEmpty` çağrıdan hemen sonra aşağıdaki kodu ekleyerek yöntemi değiştirin [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) .

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet2":::

1. Live Unit Testing, kaynak kodunuzu değiştirirken yeni ve değiştirilmiş testleri otomatik olarak yürütür. Aşağıdaki çizimde gösterildiği gibi, eklediğiniz iki ve değiştirdiğiniz bir öğe de dahil olmak üzere tüm testler başarılı olmuştur.

   ::: moniker range="vs-2017"
   ![Test kapsamını genişlettikten sonra test Gezgini](media/lut-start/test-dynamic.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Test kapsamını genişlettikten sonra canlı test Gezgini](media/lut-start/vs-2019/test-dynamic.png)
   ::: moniker-end

1. StringLibrary sınıfının kaynak kodunu içeren pencereye geçiş yapın. Live Unit Testing artık kod kapsamımızın yönteme genişletilme olduğunu gösterir `StartsWithLower` .

    ![StartsWithLower yöntemi için kod kapsamı](media/lut-start/lut-extended-cs.png)

Bazı durumlarda, **Test Gezgini** 'ndeki başarılı testler gri renkte olabilir. Bu, bir testin yürütülmekte olduğunu veya testin en son yürütüldüğünden bu yana etkilenmeyen hiçbir kod değişikliği olmadığından testin yeniden çalıştırılmadığını gösterir.

Şimdiye kadar, tüm sınamalarımız başarılı oldu. Sonraki bölümde, test başarısızlığını nasıl işleyebileceğini inceleyeceğiz.

## <a name="handle-a-test-failure"></a>Test başarısızlığı işleme

Bu bölümde, test başarısızlıklarını belirlemek, sorunlarını gidermek ve gidermek için Live Unit Testing nasıl kullanabileceğinizi keşfedebilirsiniz. Bu, test kapsamını yönteme genişleterek bunu yapacaksınız `HasEmbeddedSpaces` .

1. Aşağıdaki yöntemi test dosyanıza ekleyin:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet3":::

1. Test yürütüldüğünde, `TestHasEmbeddedSpaces` Aşağıdaki çizimde gösterildiği gibi, yönteminin başarısız olduğunu Live Unit Testing.

   ::: moniker range="vs-2017"
   ![Başarısız testi bildiren test Gezgini](media/lut-start/test-failure.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Başarısız bir testi bildiren canlı test Gezgini](media/lut-start/vs-2019/test-failure.png)
   ::: moniker-end

1. Kitaplık kodunu görüntüleyen pencereyi seçin. Live Unit Testing, yönteme kod kapsamını genişletmiştir `HasEmbeddedSpaces` . Ayrıca, 🞩 başarısız testlerin kapsadığı satırlara kırmızı bir "" ekleyerek test başarısızlığını raporlar.

1. Yöntem imzasına sahip çizginin üzerine gelin `HasEmbeddedSpaces` . Live Unit Testing, aşağıdaki çizimde gösterildiği gibi, yöntemin bir test tarafından ele alınmakta olduğunu raporlayan bir araç ipucu görüntüler.

   ![Başarısız test hakkındaki bilgileri Live Unit Testing](media/lut-start/test-failure-info-cs.png)

1. Başarısız **Testhasembeddedspaces** testini seçin. Live Unit Testing, aşağıdaki çizimde gösterildiği gibi, tüm testleri çalıştırma ve tüm testlerin hatalarını ayıklama gibi birkaç seçenek sunar:

   ::: moniker range="vs-2017"
   ![Başarısız test için Live Unit Testing seçenekleri](media/lut-start/test-failure-options.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Başarısız test için Live Unit Testing seçenekleri](media/lut-start/vs-2019/test-failure-options.png)
   ::: moniker-end

1. Başarısız testin hatalarını ayıklamak için **Tümünü hata ayıkla** ' yı seçin.

1. Visual Studio, testi hata ayıklama modunda yürütür.

   Test, bir dizideki her dizeyi adlı bir değişkene atar `phrase` ve `HasEmbeddedSpaces` yöntemine geçirir. Program yürütme, ilk kez onaylama ifadesi olduğunda hata ayıklayıcıyı duraklatır ve çağırır `false` . Yöntem çağrısındaki beklenmeyen değerin sonucu olan özel durum iletişim kutusu [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) Aşağıdaki çizimde gösterilmiştir.

   ![Live Unit Testing özel durum iletişim kutusu](media/lut-start/exception-dialog-cs.png)

   ayrıca, Visual Studio tarafından sağlanan hata ayıklama araçlarının tümü, aşağıdaki çizimde gösterildiği gibi, başarısız test sitemizi gidermenize yardımcı olacak şekilde sunulmaktadır:

   ![Visual Studio hata ayıklama araçları](media/lut-start/debugging-tools-cs.png)

   **Oto** , `phrase` değişkenin değerinin "adı tdescription" olduğunu ve dizinin ikinci öğesi olduğunu unutmayın. Test yöntemi `HasEmbeddedSpaces` `true` Bu dizeyi geçtiğinde döndürülmesini bekler; bunun yerine, döndürür `false` . Daha açık bir şekilde, "\t", sekme karakterini gömülü bir boşluk olarak tanımaz.

1. **Hata Ayıkla**  >  **devam et**' i seçin, **F5** tuşuna basın veya test programını yürütmeye devam etmek için araç çubuğundaki **devam** düğmesine tıklayın. İşlenmemiş bir özel durum oluştuğundan, test sonlanır.
Bu, hatanın ön araştırması için yeterli bilgi sağlar. `TestHasEmbeddedSpaces`(Test yordamı) yanlış bir varsayım yaptı ya da `HasEmbeddedSpaces` gömülü tüm boşlukları doğru bir şekilde tanımıyor.

1. Sorunu tanılamak ve düzeltmek için `StringLibrary.HasEmbeddedSpaces` yöntemiyle başlayın. Yöntemindeki karşılaştırmaya bakın `HasEmbeddedSpaces` . Bir katıştırılmış alanı U + 0020 olarak değerlendirir. Ancak, Unicode standart birkaç boşluk karakteri içerir. Bu, kitaplık kodunun bir boşluk karakteri için yanlış test edilmiş olduğunu önerir.

1. Eşitlik karşılaştırmasını yönteme yönelik bir çağrı ile değiştirin <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> :

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/program2.cs" id="Snippet1":::

1. Live Unit Testing başarısız test yöntemini otomatik olarak yeniden çalıştırır.

   Live Unit Testing, Ayrıca, kod Düzenleyicisi penceresinde de görüntülenen güncelleştirilmiş sonuçları gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Live Unit Testing](live-unit-testing.md)
- [Live Unit Testing sık sorulan sorular](live-unit-testing-faq.yml)
