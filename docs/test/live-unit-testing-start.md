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
ms.technology: vs-ide-test
ms.workload:
- dotnet
ms.openlocfilehash: 7a1f02972ced010110f7ff43c87c342c956c35623b49b49a0ce0b4ee173e6c2d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121227251"
---
# <a name="get-started-with-live-unit-testing"></a>Live Unit Testing kullanmaya başlama

bir Visual Studio çözümünde Live Unit Testing etkinleştirdiğinizde, test kapsamınız ve testlerinizin durumunu görsel olarak gösterir. Live Unit Testing Ayrıca, kodunuzun her değişiklik yaptığınızda testleri dinamik olarak yürütür ve değişiklikleriniz testlerin başarısız olmasına neden olduğunda sizi anında bilgilendirir.

Live Unit Testing, .NET Framework ya da .net Core ' u hedefleyen çözümleri test etmek için kullanılabilir. Bu öğreticide, .NET Standard hedefleyen basit bir sınıf kitaplığı oluşturarak Live Unit Testing kullanacağınızı öğrenirsiniz ve test etmek üzere .NET Core 'u hedefleyen bir MSTest projesi oluşturacaksınız.

Tam C# çözümü, GitHub [microsoftdocs/VisualStudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) deposundan indirilebilir.

## <a name="prerequisites"></a>Önkoşullar

bu öğreticide, **.net Core platformlar arası geliştirme** iş yüküne Visual Studio Enterprise edition sürümünü yüklemiş olmanız gerekir.

## <a name="create-the-solution-and-the-class-library-project"></a>Çözüm ve sınıf kitaplığı projesi oluşturma

tek bir .NET Standard sınıf kitaplığı projesi olan stringlibrary ' den oluşan bir Visual Studio çözümü oluşturarak başlayın.

Çözüm yalnızca bir veya daha fazla proje için bir kapsayıcıdır. boş bir çözüm oluşturmak için Visual Studio açın ve aşağıdakileri yapın:

1.   >    >  üst düzey Visual Studio menüsünden dosya yeni **Project** seçin.

1. Şablon arama kutusuna **çözüm** yazın ve ardından **boş çözüm** şablonunu seçin. Projenin kullanımı **Tylibraries** olarak adlandırın.

   ::: moniker range="vs-2017"

   ![* * yeni Project * * iletişim kutusu](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Çözümü oluşturmayı tamamlama.

Çözümü oluşturduğunuza göre, dizeler ile çalışmak için birkaç uzantı yöntemi içeren StringLibrary adlı bir sınıf kitaplığı oluşturacaksınız.

1. **Çözüm Gezgini**' de, kullanımı, **ek** yazım kitaplıkları çözümüne sağ tıklayın ve  >  **yeni Project** ekle ' yi seçin.

::: moniker range="vs-2017"

2. **yeni Project ekle** iletişim kutusunda C# düğümünü ve ardından **.NET Standard**' ı seçin.

   > [!NOTE]
   > Kitaplığımız belirli bir .NET uygulamasının yerine .NET Standard hedeflediğinden, bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasından çağrılabilir. Daha fazla bilgi için bkz. [.NET Standard](/dotnet/standard/net-standard).

3. Sağ bölmedeki **sınıf kitaplığı (.NET Standard)** şablonunu seçin ve aşağıdaki çizimde gösterildiği gibi **ad** metin kutusuna **StringLibrary** yazın:

   ![* * yeni Project ekle * * iletişim kutusu](./media/lut-start/add-project-cs.png)

4. Projeyi oluşturmak için **Tamam**'ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. Şablon arama kutusuna **sınıf kitaplığı** yazın ve **sınıf kitaplığı (.NET Standard)** şablonunu seçin. **İleri**’ye tıklayın.

   > [!NOTE]
   > Kitaplığımız belirli bir .NET uygulamasının yerine .NET Standard hedeflediğinden, bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasından çağrılabilir. Daha fazla bilgi için bkz. [.NET Standard](/dotnet/standard/net-standard).

3. Proje **StringLibrary** olarak adlandırın.

4. Projeyi oluşturmak için **Oluştur** ' a tıklayın.

::: moniker-end

5. Kod düzenleyicisinde varolan tüm kodu aşağıdaki kodla değiştirin:

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

   StringLibrary üç statik yönteme sahiptir:

   - `StartsWithUpper``true`bir dize, büyük harfle başlıyorsa döndürür; Aksi takdirde, döndürür `false` .

   - `StartsWithLower``true`bir dize küçük harf karakteriyle başlıyorsa döndürür; Aksi takdirde, döndürür `false` .

   - `HasEmbeddedSpaces``true`bir dize gömülü bir boşluk karakteri içeriyorsa döndürür; Aksi takdirde, döndürür `false` .

6.   >  üst düzey Visual Studio menüsünden build **build Solution** öğesini seçin. Derleme başarılı olmalıdır.

## <a name="create-the-test-project"></a>Test projesi oluşturma

Sonraki adım, StringLibrary kitaplığını test etmek için birim test projesi oluşturmaktır. Aşağıdaki adımları gerçekleştirerek birim testlerini oluşturun:

1. **Çözüm Gezgini**' de, kullanımı, **ek** yazım kitaplıkları çözümüne sağ tıklayın ve  >  **yeni Project** ekle ' yi seçin.

::: moniker range="vs-2017"

2. **yeni Project ekle** iletişim kutusunda C# düğümünü seçin, sonra **.net Core**' u seçin.

   > [!NOTE]
   > Birim testlerinizi, sınıf kitaplığınız ile aynı dilde yazmanız gerekmez.

3. sağ bölmedeki **birim testi Project (.net Core)** şablonunu seçin ve aşağıdaki çizimde gösterildiği gibi **ad** metin kutusuna **stringlibrarytests** yazın:

   ![birim test projesi için * * yeni Project ekle * * iletişim kutusu](./media/lut-start/add-unit-test-cs.png)

4. Projeyi oluşturmak için **Tamam**'ı seçin.

   > [!NOTE]
   > Bu Başlangıç Öğreticisi, MSTest test çerçevesiyle Live Unit Testing kullanır. Ayrıca xUnit ve NUnit test çerçevelerini de kullanabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

2. şablon arama kutusuna **birim testi** yazın, dil olarak **C#** ' yi seçin ve ardından .net Core şablonu için **birim testi Project** seçin. **İleri**’ye tıklayın.

   > [!NOTE]
   > Visual Studio 2019 sürüm 16,9 ' den başlayarak, mstest proje şablonu adı **mstest birim testi Project (.net Core)** iken **birim testi Project** olarak değiştirildi.

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

   Birim test kodu bazı ASCII olmayan karakterler içerdiğinden, dosyayı varsayılan ASCII biçiminde kaydederseniz bazı karakterlerin kaybolacağını uyarmak için aşağıdaki iletişim kutusunu görürsünüz.

8. **Diğer kodlamaya sahip Kaydet** düğmesini seçin.

   ![Dosya kodlaması seçin](media/lut-start/ascii-encoding.png)

9. Aşağıdaki çizimde gösterildiği gibi, **Gelişmiş kaydetme seçenekleri** Iletişim kutusunun **kodlama** açılan LISTESINDE **Unicode (imzasız UTF-8)-kod sayfası 65001**' ı seçin:

   ![UTF-8 kodlamasını seçme](media/lut-start/utf8-encoding.png)

10.   >  üst düzey Visual Studio menüsünden derleme **yeniden oluşturma çözümünü** seçerek birim testi projesini derleyin.

Bir sınıf kitaplığı ve bunun için bazı birim testlerini oluşturdunuz. Artık Live Unit Testing kullanmak için gereken başlangıç kuralları tamamladınız.

## <a name="enable-live-unit-testing"></a>Live Unit Testing etkinleştir

Şimdiye kadar, StringLibrary sınıf kitaplığı için testleri yazmış olsanız da onları çalıştırmadınız. Live Unit Testing, bunları etkinleştirdikten sonra otomatik olarak yürütür. Bunu yapmak için aşağıdakileri yapın:

1. İsteğe bağlı olarak, StringLibrary kodunu içeren kod düzenleyici penceresini seçin. bu, bir C# projesi için *class1. cs* veya bir Visual Basic projesi için *class1. vb* ' dir. (Bu adım, Live Unit Testing etkinleştirdikten sonra testlerinizin sonucunu ve kod kapsamınız kapsamını görsel olarak incelemenize olanak sağlar.)

1.   >    >  en üst düzey Visual Studio menüsünden Test Live Unit Testing **başlat** ' ı seçin.

1. Visual Studio, tüm testlerinizi otomatik olarak çalıştıran canlı birim testi başlatır.

::: moniker range="vs-2017"
Testlerinizi çalıştırmayı bitirdiğinde, **Test Gezgini** hem genel sonuçları hem de bireysel testlerin sonucunu görüntüler. Ayrıca, kod Düzenleyicisi penceresi hem test kodu kapsamınızla hem de testleriniz için sonucu grafik olarak görüntüler. Aşağıdaki çizimde gösterildiği gibi, üç testin hepsi başarıyla yürütülür. Ayrıca, testlerimizin yöntemdeki tüm kod yollarını kapsadığından `StartsWithUpper` ve bu testlerin başarıyla yürütüldüğü (yeşil onay işareti, "✓" ile belirtilir) gösterilmektedir. Son olarak, StringLibrary 'deki diğer yöntemlerin hiçbirinin kod kapsamı (mavi bir çizgi ile belirtilir, "➖") olduğunu gösterir.

![Canlı birim testi başladıktan sonra test Gezgini ve kod Düzenleyicisi penceresi](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019"
Testlerinizi çalıştırmayı bitirdiğinde **Live Unit Testing** hem genel sonuçları hem de tek testlerin sonucunu görüntüler. Ayrıca, kod Düzenleyicisi penceresi hem test kodu kapsamınızla hem de testleriniz için sonucu grafik olarak görüntüler. Aşağıdaki çizimde gösterildiği gibi, üç testin hepsi başarıyla yürütülür. Ayrıca, testlerimizin yöntemdeki tüm kod yollarını kapsadığından `StartsWithUpper` ve bu testlerin başarıyla yürütüldüğü (yeşil onay işareti, "✓" ile belirtilir) gösterilmektedir. Son olarak, StringLibrary 'deki diğer yöntemlerin hiçbirinin kod kapsamı (mavi bir çizgi ile belirtilir, "➖") olduğunu gösterir.

![Canlı birim testi başladıktan sonra canlı test Gezgini ve kod Düzenleyicisi penceresi](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

Ayrıca, kod Düzenleyicisi penceresinde belirli bir kod kapsamı simgesini seçerek test kapsamı ve test sonuçları hakkında daha ayrıntılı bilgi edinebilirsiniz. Bu ayrıntıyı incelemek için aşağıdakileri yapın:

1. Yönteminde okuyan satırdaki yeşil onay işaretine tıklayın `if (String.IsNullOrWhiteSpace(s))` `StartsWithUpper` . Aşağıdaki çizimde gösterildiği gibi, Live Unit Testing üç testin bu kod satırını kapsadığını ve tümünün başarıyla yürütüldüğünü gösterir.

   ![' İf ' koşullu bildiriminde kod kapsamı](media/lut-start/code-coverage-cs1.png)

1. Yönteminde okuyan satırdaki yeşil onay işaretine tıklayın `return Char.IsUpper(s[0])` `StartsWithUpper` . Aşağıdaki çizimde gösterildiği gibi, Live Unit Testing yalnızca iki testin bu kod satırına yer ve tüm testlerin başarıyla yürütülmektedir.

   ![Dönüş deyimi için kod kapsamı](media/lut-start/code-coverage-cs2.png)

Tanımlanmamış kod Live Unit Testing büyük sorun eksik kod kapsamıdır. Bunu bir sonraki bölümde ele alasiniz.

## <a name="expand-test-coverage"></a>Test kapsamını genişletme

Bu bölümde birim testlerinizi yöntemine `StartsWithLower` genişletebilirsiniz. Bunu yaparken, Live Unit Testing dinamik olarak kodunuzu test etmeye devam eder.

Kod kapsamı yönteminin `StartsWithLower` kapsamına genişletmek için şunları yapın:

1. Projenizin `TestStartsWithLower` `TestDoesNotStartWithLower` test kaynak kodu dosyasına aşağıdaki ve yöntemlerini ekleyin:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet1":::

1. yöntemine `DirectCallWithNullOrEmpty` yapılan çağrıdan hemen sonra aşağıdaki kodu ekleyerek yöntemini [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) değiştirme.

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet2":::

1. Live Unit Testing kodunuzu değiştirerek yeni ve değiştirilmiş testleri otomatik olarak yürütür. Aşağıdaki çizimde gösterildiği gibi, eklemış olduğunuz ikisi ve değiştirdklerinden biri de dahil olmak üzere tüm testler başarılı oldu.

   ::: moniker range="vs-2017"
   ![Test kapsamı genişlettikten sonra Test Gezgini](media/lut-start/test-dynamic.png)
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
   ![Test Gezgini başarısız bir testi bildiriyor](media/lut-start/test-failure.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Canlı Test Gezgini başarısız bir testi bildiriyor](media/lut-start/vs-2019/test-failure.png)
   ::: moniker-end

1. Kitaplık kodunu görüntüleyen pencereyi seçin. Live Unit Testing kapsamı yöntemine `HasEmbeddedSpaces` genişletti. Ayrıca başarısız olan testlerin kapsamına alınan satırlara kırmızı 🞩 " " ekleyerek test hatalarını raporlar.

1. Metot imzası olan satırın `HasEmbeddedSpaces` üzerine gelin. Live Unit Testing, aşağıdaki çizimde gösterildiği gibi yöntemin bir test kapsamında olduğunu rapor eden bir araç ipucu görüntüler:

   ![Live Unit Testing test hakkında bilgi](media/lut-start/test-failure-info-cs.png)

1. Başarısız **TestHasEmbeddedSpaces testini** seçin. Live Unit Testing, aşağıdaki çizimde gösterildiği gibi tüm testleri çalıştırma ve tüm testlerde hata ayıklama gibi birkaç seçenek sunar:

   ::: moniker range="vs-2017"
   ![Live Unit Testing testin seçenekleri](media/lut-start/test-failure-options.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Live Unit Testing testin seçenekleri](media/lut-start/vs-2019/test-failure-options.png)
   ::: moniker-end

1. Başarısız **testte hata ayıklamak** için Tüm Hata Ayıkla'ya seçin.

1. Visual Studio hata ayıklama modunda yürütür.

   Test, dizide yer alan her dizeyi adlı bir değişkene atar `phrase` ve yöntemine `HasEmbeddedSpaces` iletir. Program yürütmesi, onay ifadesi ilk kez olduğu zaman duraklatılır ve hata ayıklayıcıyı `false` çağırır. Yöntem çağrısında beklenmeyen değerden sonuç alan özel [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) durum iletişim kutusu aşağıdaki çizimde gösterilmiştir.

   ![Live Unit Testing özel durum iletişim kutusu](media/lut-start/exception-dialog-cs.png)

   Ayrıca, aşağıdaki çizimde gösterildiği gibi Visual Studio testimizle ilgili sorunları gidermemize yardımcı olmak için aşağıdaki hata ayıklama araçlarının hepsi kullanılabilir:

   ![Visual Studio ayıklama araçları](media/lut-start/debugging-tools-cs.png)

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
- [Live Unit Testing Sorulan Sorular](live-unit-testing-faq.yml)
