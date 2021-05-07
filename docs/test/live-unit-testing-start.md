---
title: Canlı birim testi ile kodunuzu test etme hakkında bilgi edinin
description: .NET Standard hedefleyen ve test etmek üzere .NET Core ' u hedefleyen bir MSTest projesi oluşturan basit bir sınıf kitaplığı oluşturarak Live Unit Testing kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/03/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2270216e7245f20d26df580ad90dc627319adcc1
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798641"
---
# <a name="get-started-with-live-unit-testing"></a>Live Unit Testing kullanmaya başlama

Visual Studio çözümünde Live Unit Testing etkinleştirdiğinizde, test kapsamınız ve testlerinizin durumunu görsel olarak gösterir. Live Unit Testing Ayrıca, kodunuzun her değişiklik yaptığınızda testleri dinamik olarak yürütür ve değişiklikleriniz testlerin başarısız olmasına neden olduğunda sizi anında bilgilendirir.

Live Unit Testing, .NET Framework ya da .NET Core ' u hedefleyen çözümleri test etmek için kullanılabilir. Bu öğreticide, .NET Standard hedefleyen basit bir sınıf kitaplığı oluşturarak Live Unit Testing kullanacağınızı öğrenirsiniz ve test etmek üzere .NET Core 'u hedefleyen bir MSTest projesi oluşturacaksınız.

Tam C# çözümü, GitHub 'daki [microsoftdocs/VisualStudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) deposundan indirilebilir.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticide, **.NET Core platformlar arası geliştirme** iş yüküne Visual Studio Enterprise Edition sürümünü yüklemiş olmanız gerekir.

## <a name="create-the-solution-and-the-class-library-project"></a>Çözüm ve sınıf kitaplığı projesi oluşturma

Tek bir .NET Standard Class Library projesinden (StringLibrary) oluşan bir Visual Studio çözümü oluşturarak başlayın.

Çözüm yalnızca bir veya daha fazla proje için bir kapsayıcıdır. Boş bir çözüm oluşturmak için Visual Studio 'Yu açın ve aşağıdakileri yapın:

1.   >    >  En üst düzey Visual Studio menüsünden dosya yeni **Proje** ' yi seçin.

1. Şablon arama kutusuna **çözüm** yazın ve ardından **boş çözüm** şablonunu seçin. Projenin kullanımı **Tylibraries** olarak adlandırın.

   ::: moniker range="vs-2017"

   ![* * Yeni proje * * iletişim kutusu](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Çözümü oluşturmayı tamamlama.

Çözümü oluşturduğunuza göre, dizeler ile çalışmak için birkaç uzantı yöntemi içeren StringLibrary adlı bir sınıf kitaplığı oluşturacaksınız.

1. **Çözüm Gezgini**, kullanımı uygun proje çözümüne sağ tıklayın ve   >  **Yeni proje** Ekle ' yi seçin.

::: moniker range="vs-2017"

2. Yeni Proje **Ekle iletişim kutusunda** C# düğümünü seçin ve sonra da .NET Standard. 

   > [!NOTE]
   > Kitaplığımız belirli .NET Standard bir .NET uygulaması yerine bir .NET uygulamasını hedeflese de, bu .NET uygulamasının bu sürümünü destekleyen herhangi bir .NET uygulamasından .NET Standard. Daha fazla bilgi için [bkz. .NET Standard.](/dotnet/standard/net-standard)

3. Sağ **bölmede Sınıf Kitaplığı (.NET Standard)** şablonunu seçin ve Aşağıdaki çizimde  gösterildiği gibi Ad metin kutusuna **StringLibrary** yazın:

   ![**Yeni Proje Ekle** iletişim kutusu](./media/lut-start/add-project-cs.png)

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

   - `StartsWithUpper` , `true` bir dize büyük harf karakterle başlıyorsa, aksi takdirde `false` döndürür.

   - `StartsWithLower`, `true` bir dize küçük harf karakterle başlıyorsa, aksi takdirde `false` döndürür.

   - `HasEmbeddedSpaces` , `true` bir dize katıştırılmış bir boşluk karakteri içeriyorsa döndürür; aksi takdirde `false` döndürür.

6. Üst **düzey**  >  **derleme menüsünde** Derleme Çözümü'Visual Studio seçin. Derlemenin başarılı olması gerekir.

## <a name="create-the-test-project"></a>Test projesini oluşturma

Sonraki adım, StringLibrary kitaplığını test etmek için birim testi projesi oluşturmaktır. Aşağıdaki adımları gerçekleştirerek birim testlerini oluşturun:

1. **Çözüm Gezgini**, kullanımı uygun proje çözümüne sağ tıklayın ve   >  **Yeni proje** Ekle ' yi seçin.

::: moniker range="vs-2017"

2. **Yeni Proje Ekle** Iletişim kutusunda C# düğümünü seçin, sonra **.NET Core**' u seçin.

   > [!NOTE]
   > Birim testlerinizi, sınıf kitaplığınız ile aynı dilde yazmanız gerekmez.

3. Sağ bölmedeki **birim testi projesi (.NET Core)** şablonunu seçin ve aşağıdaki çizimde gösterildiği gibi **ad** metin kutusuna **stringlibrarytests** yazın:

   ![Birim test projesi için * * yeni proje Ekle * * iletişim kutusu](./media/lut-start/add-unit-test-cs.png)

4. Projeyi oluşturmak için **Tamam**'ı seçin.

   > [!NOTE]
   > Bu Başlangıç Öğreticisi, MSTest test çerçevesiyle Live Unit Testing kullanır. Ayrıca xUnit ve NUnit test çerçevelerini de kullanabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

2. Şablon arama kutusuna **birim testi** yazın, dil olarak **C#** ' yi seçin ve ardından .NET Core şablonu için **birim testi projesi** ' ni seçin. **İleri**’ye tıklayın.

   > [!NOTE]
   > Visual Studio 2019 sürüm 16,9 ' den başlayarak, MSTest proje şablonu adı **MSTest birim testi projesinden (.NET Core)** **birim testi projesine** değişti.

3. Projeyi **Stringlibrarytests** olarak adlandırın ve **İleri**' ye tıklayın.

4. Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.

   > [!NOTE]
   > Bu Başlangıç Öğreticisi, MSTest test çerçevesiyle Live Unit Testing kullanır. Ayrıca xUnit ve NUnit test çerçevelerini de kullanabilirsiniz.

::: moniker-end

5. Birim testi projesi test edilen sınıf kitaplığına otomatik olarak erişemez. Sınıf kitaplığı projesine bir başvuru ekleyerek test Kitaplığı erişimi verirsiniz. Bunu yapmak için projeye sağ tıklayın `StringLibraryTests` ve başvuru Ekle ' yi seçin   >  . **Başvuru Yöneticisi** iletişim kutusunda, **çözüm** sekmesinin seçili olduğundan emin olun ve aşağıdaki çizimde gösterildiği gibi StringLibrary projesini seçin.

   ![* * Reference Manager * * iletişim kutusu](./media/lut-start/add-reference.png)

6. Şablon tarafından sunulan ortak birim test kodunu şu kodla değiştirin:

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

7. Araç çubuğundaki **Kaydet** simgesini seçerek projenizi kaydedin.

   Birim testi kodu ASCII olmayan bazı karakterlere sahip olduğundan, dosyayı varsayılan ASCII biçiminde kaydetmenizi sağlarsanız bazı karakterlerin kaybolacak uyarısı için aşağıdaki iletişim kutusunu görüntülenir.

8. Diğer Kodlama **ile Kaydet düğmesini** seçin.

   ![Dosya kodlaması seçme](media/lut-start/ascii-encoding.png)

9. Gelişmiş **Kaydetme Seçenekleri** iletişim kutusunun  Kodlama açılan listesinde, aşağıdaki çizimde gösterildiği gibi Unicode (imza olmadan **UTF-8) - Kod sayfası 65001'i** seçin:

   ![UTF-8 kodlamasını seçme](media/lut-start/utf8-encoding.png)

10. Üst düzey derleme menüsünden Çözümü **Yeniden**  >   Derle'yi seçerek birim testi Visual Studio derle.

Bir sınıf kitaplığının yanı sıra bunun için bazı birim testleri de oluşturdunız. Artık bu aracı kullanmak için gereken ön Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Enable Live Unit Testing

Şu ana kadar StringLibrary sınıf kitaplığı için testleri yazmadınız ancak bunları yürütmedisiniz. Live Unit Testing etkinleştiren otomatik olarak yürütür. Bunu yapmak için şunları yapın:

1. İsteğe bağlı olarak, StringLibrary kodunu içeren kod düzenleyicisi penceresini seçin. Bu, bir *C# projesi için Class1.cs* veya bir C# projesi için *Class1.vb* Visual Basic olur. (Bu adım, testlerinizi etkinleştiren testleri ve kod kapsamı kapsamını görsel olarak incelemenize Live Unit Testing.)

1. Üst **düzey**  >  **Live Unit Testing**  >  **Başlat menüsünden** Test Visual Studio seçin.

1. Visual Studio tüm testlerinizi otomatik olarak çalıştıran Canlı Birim Testi'ne başlar.

::: moniker range="vs-2017"
Test Gezgini, testlerinizi **çalıştırmayı tamamlarsa hem** genel sonuçları hem de tek tek testlerin sonuçlarını görüntüler. Ayrıca, kod düzenleyicisi penceresi hem test kodu kapsamınızı hem de test sonuçlarınızı grafiksel olarak görüntüler. Aşağıdaki çizimde gösterildiği gibi üç test de başarıyla yürütülür. Ayrıca, testlerimizin yöntemdeki tüm kod yollarını kapsadığından `StartsWithUpper` ve bu testlerin başarıyla yürütüldüğü (yeşil onay işareti, "✓" ile belirtilir) gösterilmektedir. Son olarak, StringLibrary 'deki diğer yöntemlerin hiçbirinin kod kapsamı (mavi bir çizgi ile belirtilir, "➖") olduğunu gösterir.

![Canlı birim testi başladıktan sonra test Gezgini ve kod Düzenleyicisi penceresi](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019"
Testlerinizi çalıştırmayı bitirdiğinde **Live Unit Testing** hem genel sonuçları hem de tek testlerin sonucunu görüntüler. Ayrıca, kod Düzenleyicisi penceresi hem test kodu kapsamınızla hem de testleriniz için sonucu grafik olarak görüntüler. Aşağıdaki çizimde gösterildiği gibi, üç testin hepsi başarıyla yürütülür. Ayrıca, testlerimizin yöntemdeki tüm kod yollarını kapsadığından `StartsWithUpper` ve bu testlerin başarıyla yürütüldüğü (yeşil onay işareti, "✓" ile belirtilir) gösterilmektedir. Son olarak, StringLibrary 'deki diğer yöntemlerin hiçbirinin kod kapsamı (mavi bir çizgi ile belirtilir, "➖") olduğunu gösterir.

![Canlı birim testi başladıktan sonra canlı test Gezgini ve kod Düzenleyicisi penceresi](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

Ayrıca, kod Düzenleyicisi penceresinde belirli bir kod kapsamı simgesini seçerek test kapsamı ve test sonuçları hakkında daha ayrıntılı bilgi edinebilirsiniz. Bu ayrıntıyı incelemek için aşağıdakileri yapın:

1. Yönteminde okuyan satırdaki yeşil onay işaretine tıklayın `if (String.IsNullOrWhiteSpace(s))` `StartsWithUpper` . Aşağıdaki çizimde gösterildiği gibi, Live Unit Testing üç testin bu kod satırını kapsadığını ve tümünün başarıyla yürütüldüğünü gösterir.

   ![' İf ' koşullu bildiriminde kod kapsamı](media/lut-start/code-coverage-cs1.png)

1. Yönteminde okuyan satırdaki yeşil onay işaretine tıklayın `return Char.IsUpper(s[0])` `StartsWithUpper` . Aşağıdaki çizimde gösterildiği gibi, Live Unit Testing yalnızca iki testin bu kod satırını kapsadığını ve tümünün başarıyla yürütüldüğünü gösterir.

   ![Return ifadesinin kod kapsamı](media/lut-start/code-coverage-cs2.png)

Live Unit Testing tanımladığı önemli sorun, tamamlanmamış kod kapsamı. Sonraki bölümde bu adresi görürsünüz.

## <a name="expand-test-coverage"></a>Test kapsamını Genişlet

Bu bölümde birim testlerinizi yöntemine `StartsWithLower` genişletebilirsiniz. Bunu yaparken, Live Unit Testing dinamik olarak kodunuzu test etmeye devam eder.

Kod kapsamı yönteminin `StartsWithLower` kapsamına genişletmek için şunları yapın:

1. Projenizin `TestStartsWithLower` `TestDoesNotStartWithLower` test kaynak kodu dosyasına aşağıdaki ve yöntemlerini ekleyin:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet1":::

1. yöntemine `DirectCallWithNullOrEmpty` yapılan çağrıdan hemen sonra aşağıdaki kodu ekleyerek yöntemini [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) değiştirme.

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet2":::

1. Live Unit Testing kodunuzu değiştirerek yeni ve değiştirilmiş testleri otomatik olarak yürütür. Aşağıdaki çizimde gösterildiği gibi, eklemış olduğunuz ikisi ve değiştirdklerinden biri de dahil olmak üzere tüm testler başarılı oldu.

   ::: moniker range="vs-2017"
   ![Test kapsamını genişlettikten sonra Test Gezgini](media/lut-start/test-dynamic.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Test kapsamını genişlettikten sonra Canlı Test Gezgini](media/lut-start/vs-2019/test-dynamic.png)
   ::: moniker-end

1. StringLibrary sınıfının kaynak kodunu içeren pencereye geçiş. Live Unit Testing kod kapsamımızın yöntemine genişletildi olduğunu `StartsWithLower` gösteriyor.

    ![StartsWithLower yöntemi için kod kapsamı](media/lut-start/lut-extended-cs.png)

Bazı durumlarda Test Gezgini'nde **başarılı testler** gri olabilir. Bu, bir testin yürütültülürken olduğunu veya son yürütülürken testi etkileyen bir kod değişikliği olmadığını çünkü testin yeniden çalıştırılamay olmadığını gösterir.

Şimdiye kadar tüm testlerimiz başarılı oldu. Sonraki bölümde test hatalarını nasıl işleyebilirsiniz?

## <a name="handle-a-test-failure"></a>Test hatalarını işleme

Bu bölümde test hatalarını belirlemek, gidermek ve Live Unit Testing için bu bilgileri nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz. Bunu yapmak için test kapsamını yöntemine `HasEmbeddedSpaces` genişletebilirsiniz.

1. Test dosyanıza aşağıdaki yöntemi ekleyin:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet3":::

1. Test yürütülürken Live Unit Testing yöntemin başarısız `TestHasEmbeddedSpaces` olduğunu gösterir. Aşağıdaki çizimde gösterildiği gibi:

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

   Ayrıca, Visual Studio 'nun sunduğu tüm hata ayıklama araçları, aşağıdaki çizimde gösterildiği gibi, başarısız test sitemizi gidermenize yardımcı olmak için kullanılabilir.

   ![Visual Studio hata ayıklama araçları](media/lut-start/debugging-tools-cs.png)

   Otomatikler **penceresinde** değişkenin değerinin dizinin ikinci öğesi olan `phrase` "Name\tDescription" olduğunu unutmayın. Test yöntemi, bu `HasEmbeddedSpaces` dize `true` geçiriken dönüş bekler; bunun yerine `false` döndürür. Görünen o ki sekme karakteri olan "\t" karakterini ekli alan olarak tanımaz.

1. Devamında **Hata**  >  **Ayıkla'yı** seçin,  **F5** tuşuna basın veya test programını yürütmeye devam etmek için araç çubuğundaKi Devam düğmesine tıklayın. İşlenemeyen bir özel durum meydana geldiği için test sonlandırılır.
Bu, hatanın ön araştırması için yeterli bilgi sağlar. (Test `TestHasEmbeddedSpaces` yordamı) yanlış bir varsayımda bulundu veya `HasEmbeddedSpaces` tüm ekli alanları doğru şekilde tanımıyor.

1. Sorunu tanılamak ve düzeltmek için yöntemiyle `StringLibrary.HasEmbeddedSpaces` çalışmaya başlamanız gerekir. yönteminde karşılaştırmaya `HasEmbeddedSpaces` bakın. Ekli bir alanı U+0020 olarak kabul ediyor. Ancak, Unicode Standart bir dizi başka boşluk karakteri içerir. Bu, kitaplık kodunun yanlış bir şekilde boşluk karakteri için test edilmiş olduğunu önerir.

1. Eşitlik karşılaştırmasını yöntemine yapılan bir çağrıyla <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> değiştirin:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/program2.cs" id="Snippet1":::

1. Live Unit Testing başarısız test yöntemini otomatik olarak yeniden çalıştırıyor.

   Live Unit Testing, kod düzenleyicisi penceresinde de görünen güncelleştirilmiş sonuçları gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Live Unit Testing'Visual Studio](live-unit-testing.md)
- [Live Unit Testing Sık Sorulan Sorular](live-unit-testing-faq.yml)
