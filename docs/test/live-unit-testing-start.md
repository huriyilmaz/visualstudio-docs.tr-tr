---
title: Canlı birim testi ile kodunuzu test etme hakkında bilgi edinin
ms.date: 04/03/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ef0fbd5c422d16df4e361ff95f4ac8deabdd5bae
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287018"
---
# <a name="get-started-with-live-unit-testing"></a>Live Unit Testing kullanmaya başlama

Visual Studio çözümünde Live Unit Testing etkinleştirdiğinizde, test kapsamınız ve testlerinizin durumunu görsel olarak gösterir. Live Unit Testing Ayrıca, kodunuzun her değişiklik yaptığınızda testleri dinamik olarak yürütür ve değişiklikleriniz testlerin başarısız olmasına neden olduğunda sizi anında bilgilendirir.

Live Unit Testing, .NET Framework ya da .NET Core ' u hedefleyen çözümleri test etmek için kullanılabilir. Bu öğreticide, .NET Standard hedefleyen basit bir sınıf kitaplığı oluşturarak Live Unit Testing kullanacağınızı öğrenirsiniz ve test etmek üzere .NET Core 'u hedefleyen bir MSTest projesi oluşturacaksınız.

Tam C# çözümü, GitHub 'daki [microsoftdocs/VisualStudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) deposundan indirilebilir.

## <a name="prerequisites"></a>Ön koşullar

Bu öğreticide, **.NET Core platformlar arası geliştirme** iş yüküne Visual Studio Enterprise Edition sürümünü yüklemiş olmanız gerekir.

## <a name="create-the-solution-and-the-class-library-project"></a>Çözüm ve sınıf kitaplığı projesi oluşturma

Tek bir .NET Standard Class Library projesinden (StringLibrary) oluşan bir Visual Studio çözümü oluşturarak başlayın.

Çözüm yalnızca bir veya daha fazla proje için bir kapsayıcıdır. Boş bir çözüm oluşturmak için Visual Studio 'Yu açın ve aşağıdakileri yapın:

1. **File**  >  **New**  >  En üst düzey Visual Studio menüsünden dosya yeni**Proje** ' yi seçin.

1. Şablon arama kutusuna **çözüm** yazın ve ardından **boş çözüm** şablonunu seçin. Projenin kullanımı **Tylibraries**olarak adlandırın.

   ::: moniker range="vs-2017"

   ![* * Yeni proje * * iletişim kutusu](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Çözümü oluşturmayı tamamlama.

Çözümü oluşturduğunuza göre, dizeler ile çalışmak için birkaç uzantı yöntemi içeren StringLibrary adlı bir sınıf kitaplığı oluşturacaksınız.

1. **Çözüm Gezgini**, kullanımı uygun proje çözümüne sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.

::: moniker range="vs-2017"

2. **Yeni Proje Ekle** Iletişim kutusunda C# düğümünü ve ardından **.NET Standard**' yi seçin.

   > [!NOTE]
   > Kitaplığımız belirli bir .NET uygulamasının yerine .NET Standard hedeflediğinden, bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasından çağrılabilir. Daha fazla bilgi için bkz. [.NET Standard](/dotnet/standard/net-standard).

3. Sağ bölmedeki **sınıf kitaplığı (.NET Standard)** şablonunu seçin ve aşağıdaki çizimde gösterildiği gibi **ad** metin kutusuna **StringLibrary** yazın:

   ![* * Yeni Proje Ekle * * iletişim kutusu](./media/lut-start/add-project-cs.png)

4. Projeyi oluşturmak için **Tamam**'ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. Şablon arama kutusuna **sınıf kitaplığı** yazın ve **sınıf kitaplığı (.NET Standard)** şablonunu seçin. **İleri**’ye tıklayın.

   > [!NOTE]
   > Kitaplığımız belirli bir .NET uygulamasının yerine .NET Standard hedeflediğinden, bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasından çağrılabilir. Daha fazla bilgi için bkz. [.NET Standard](/dotnet/standard/net-standard).

3. Proje **StringLibrary**olarak adlandırın.

4. Projeyi oluşturmak için **Oluştur** ' a tıklayın.

::: moniker-end

5. Kod düzenleyicisinde varolan tüm kodu aşağıdaki kodla değiştirin:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary üç statik yönteme sahiptir:

   - `StartsWithUpper``true`bir dize, büyük harfle başlıyorsa döndürür; Aksi takdirde, döndürür `false` .

   - `StartsWithLower``true`bir dize küçük harf karakteriyle başlıyorsa döndürür; Aksi takdirde, döndürür `false` .

   - `HasEmbeddedSpaces``true`bir dize gömülü bir boşluk karakteri içeriyorsa döndürür; Aksi takdirde, döndürür `false` .

6. **Build**  >  Üst düzey Visual Studio menüsünden Build**Build Solution** öğesini seçin. Derleme başarılı olmalıdır.

## <a name="create-the-test-project"></a>Test projesi oluşturma

Sonraki adım, StringLibrary kitaplığını test etmek için birim test projesi oluşturmaktır. Aşağıdaki adımları gerçekleştirerek birim testlerini oluşturun:

1. **Çözüm Gezgini**, kullanımı uygun proje çözümüne sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.

::: moniker range="vs-2017"

2. **Yeni Proje Ekle** Iletişim kutusunda C# düğümünü seçin, sonra **.NET Core**' u seçin.

   > [!NOTE]
   > Birim testlerinizi, sınıf kitaplığınız ile aynı dilde yazmanız gerekmez.

3. Sağ bölmedeki **birim testi projesi (.NET Core)** şablonunu seçin ve aşağıdaki çizimde gösterildiği gibi **ad** metin kutusuna **stringlibrarytests** yazın:

   ![Birim test projesi için * * yeni proje Ekle * * iletişim kutusu](./media/lut-start/add-unit-test-cs.png)

4. Projeyi oluşturmak için **Tamam**'ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. Şablon arama kutusuna **birim testi** yazın ve **MSTest test projesi (.NET Core)** şablonunu seçin. **İleri**’ye tıklayın.

3. Projeyi **Stringlibrarytests**olarak adlandırın.

4. Projeyi oluşturmak için **Oluştur** ' a tıklayın.

::: moniker-end

   > [!NOTE]
   > Bu Başlangıç Öğreticisi, MSTest test çerçevesiyle Live Unit Testing kullanır. Ayrıca xUnit ve NUnit test çerçevelerini de kullanabilirsiniz.

5. Birim testi projesi test edilen sınıf kitaplığına otomatik olarak erişemez. Sınıf kitaplığı projesine bir başvuru ekleyerek test Kitaplığı erişimi verirsiniz. Bunu yapmak için projeye sağ tıklayın `StringLibraryTests` ve başvuru Ekle ' yi seçin **Add**  >  **Reference**. **Başvuru Yöneticisi** iletişim kutusunda, **çözüm** sekmesinin seçili olduğundan emin olun ve aşağıdaki çizimde gösterildiği gibi StringLibrary projesini seçin.

   ![* * Reference Manager * * iletişim kutusu](./media/lut-start/add-reference.png)

6. Şablon tarafından sunulan ortak birim test kodunu şu kodla değiştirin:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Araç çubuğundaki **Kaydet** simgesini seçerek projenizi kaydedin.

   Birim test kodu bazı ASCII olmayan karakterler içerdiğinden, dosyayı varsayılan ASCII biçiminde kaydederseniz bazı karakterlerin kaybolacağını uyarmak için aşağıdaki iletişim kutusunu görürsünüz.

8. **Diğer kodlamaya sahip Kaydet** düğmesini seçin.

   ![Dosya kodlaması seçin](media/lut-start/ascii-encoding.png)

9. Aşağıdaki çizimde gösterildiği gibi, **Gelişmiş kaydetme seçenekleri** Iletişim kutusunun **kodlama** açılan LISTESINDE **Unicode (imzasız UTF-8)-kod sayfası 65001**' ı seçin:

   ![UTF-8 kodlamasını seçme](media/lut-start/utf8-encoding.png)

10. **Build**  >  Üst düzey Visual Studio menüsünden derleme**yeniden oluşturma çözümünü** seçerek birim testi projesini derleyin.

Bir sınıf kitaplığı ve bunun için bazı birim testlerini oluşturdunuz. Artık Live Unit Testing kullanmak için gereken başlangıç kuralları tamamladınız.

## <a name="enable-live-unit-testing"></a>Live Unit Testing etkinleştir

Şimdiye kadar, StringLibrary sınıf kitaplığı için testleri yazmış olsanız da onları çalıştırmadınız. Live Unit Testing, bunları etkinleştirdikten sonra otomatik olarak yürütür. Bunu yapmak için aşağıdakileri yapın:

1. İsteğe bağlı olarak, StringLibrary kodunu içeren kod düzenleyici penceresini seçin. Bu, bir C# projesi için *Class1.cs* veya Visual Basic projesi için *Class1. vb* ' dir. (Bu adım, Live Unit Testing etkinleştirdikten sonra testlerinizin sonucunu ve kod kapsamınız kapsamını görsel olarak incelemenize olanak sağlar.)

1. **Test**  >  **Live Unit Testing**  >  En üst düzey Visual Studio menüsünden test Live Unit Testing**Başlat** ' ı seçin.

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

1. Yönteminde okuyan satırdaki yeşil onay işaretine tıklayın `return Char.IsUpper(s[0])` `StartsWithUpper` . Aşağıdaki çizimde gösterildiği gibi, Live Unit Testing yalnızca iki testin bu kod satırını kapsadığını ve tümünün başarıyla yürütüldüğünü gösterir.

   ![Return ifadesinin kod kapsamı](media/lut-start/code-coverage-cs2.png)

Live Unit Testing tanımladığı önemli sorun, tamamlanmamış kod kapsamı. Sonraki bölümde bu adresi görürsünüz.

## <a name="expand-test-coverage"></a>Test kapsamını Genişlet

Bu bölümde, birim testlerinizi yöntemine genişleteceksiniz `StartsWithLower` . Bunu yaptığınızda, Live Unit Testing kodunuzu test etmek için dinamik olarak devam eder.

Kod kapsamını yöntemine genişletmek için `StartsWithLower` aşağıdakileri yapın:

1. Aşağıdaki `TestStartsWithLower` ve `TestDoesNotStartWithLower` yöntemlerini projenizin test kaynak kodu dosyasına ekleyin:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Yöntemine yapılan `DirectCallWithNullOrEmpty` çağrıdan hemen sonra aşağıdaki kodu ekleyerek yöntemi değiştirin [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) .

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

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

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

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

   Ayrıca, Visual Studio 'nun sunduğu tüm hata ayıklama araçları, aşağıdaki çizimde gösterildiği gibi, başarısız test sitemizi gidermenize yardımcı olmak için kullanılabilir.

   ![Visual Studio hata ayıklama araçları](media/lut-start/debugging-tools-cs.png)

   **Oto** , `phrase` değişkenin değerinin "adı tdescription" olduğunu ve dizinin ikinci öğesi olduğunu unutmayın. Test yöntemi `HasEmbeddedSpaces` `true` Bu dizeyi geçtiğinde döndürülmesini bekler; bunun yerine, döndürür `false` . Daha açık bir şekilde, "\t", sekme karakterini gömülü bir boşluk olarak tanımaz.

1. **Hata Ayıkla**  >  **devam et**' i seçin, **F5**tuşuna basın veya test programını yürütmeye devam etmek için araç çubuğundaki **devam** düğmesine tıklayın. İşlenmemiş bir özel durum oluştuğundan, test sonlanır.
Bu, hatanın ön araştırması için yeterli bilgi sağlar. `TestHasEmbeddedSpaces`(Test yordamı) yanlış bir varsayım yaptı ya da `HasEmbeddedSpaces` gömülü tüm boşlukları doğru bir şekilde tanımıyor.

1. Sorunu tanılamak ve düzeltmek için `StringLibrary.HasEmbeddedSpaces` yöntemiyle başlayın. Yöntemindeki karşılaştırmaya bakın `HasEmbeddedSpaces` . Bir katıştırılmış alanı U + 0020 olarak değerlendirir. Ancak, Unicode standart birkaç boşluk karakteri içerir. Bu, kitaplık kodunun bir boşluk karakteri için yanlış test edilmiş olduğunu önerir.

1. Eşitlik karşılaştırmasını yönteme yönelik bir çağrı ile değiştirin <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> :

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing başarısız test yöntemini otomatik olarak yeniden çalıştırır.

   Live Unit Testing, Ayrıca, kod Düzenleyicisi penceresinde de görüntülenen güncelleştirilmiş sonuçları gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da Live Unit Testing](live-unit-testing.md)
- [Live Unit Testing sık sorulan sorular](live-unit-testing-faq.md)
