---
title: Canlı birim testi ile kodunuzu test etme hakkında bilgi edinin
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bb254dc2d70992c798a95e5e12efcbb72b2a2336
ms.sourcegitcommit: 1a3c2ca995fd44fc72741b3a100c6e57f4f8702c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72262345"
---
# <a name="get-started-with-live-unit-testing"></a>Live Unit Testing kullanmaya başlama

Visual Studio çözümünde Live Unit Testing etkinleştirdiğinizde, test kapsamınız ve testlerinizin durumunu görsel olarak gösterir. Live Unit Testing Ayrıca, kodunuzun her değişiklik yaptığınızda testleri dinamik olarak yürütür ve değişiklikleriniz testlerin başarısız olmasına neden olduğunda sizi anında bilgilendirir.

Live Unit Testing, .NET Framework ya da .NET Core ' u hedefleyen çözümleri test etmek için kullanılabilir. Bu öğreticide, .NET Standard hedefleyen basit bir sınıf kitaplığı oluşturarak Live Unit Testing kullanacağınızı öğrenirsiniz ve test etmek üzere .NET Core 'u hedefleyen bir MSTest projesi oluşturacaksınız.

Tam C# çözümünü indirilebileceğini [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) github deposu.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticide, **.NET Core platformlar arası geliştirme** iş yüküne Visual Studio Enterprise Edition sürümünü yüklemiş olmanız gerekir.

## <a name="create-the-solution-and-the-class-library-project"></a>Çözüm ve sınıf kitaplığı projesi oluşturma

Tek bir .NET Standard Class Library projesinden (StringLibrary) oluşan bir Visual Studio çözümü oluşturarak başlayın.

Yalnızca bir veya daha fazla proje için bir kapsayıcı çözümüdür. Boş bir çözüm oluşturmak için Visual Studio 'Yu açın ve aşağıdakileri yapın:

1. Seçin **dosya** > **yeni** > **proje** en üst düzey Visual Studio menüsünde.

1. Şablon arama kutusuna **çözüm** yazın ve ardından **boş çözüm** şablonunu seçin.

   ::: moniker range="vs-2017"

   ![** ** Yeni Proje iletişim kutusu](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Çözümü oluşturmayı tamamlama.

Çözümü oluşturduğunuza göre, dizeler ile çalışmak için birkaç uzantı yöntemi içeren StringLibrary adlı bir sınıf kitaplığı oluşturacaksınız.

1. **Çözüm Gezgini**' de, kullanımı uygun**Yeni proje**öğesine sağ tıklayın ve ardından **Ekle** >  ' yi seçin.

::: moniker range="vs-2017"

2. İçinde **Yeni Proje Ekle** iletişim kutusunda Seç C# düğümünü seçip **.NET Standard**.

   > [!NOTE]
   > Kitaplığımız belirli bir .NET uygulamasının yerine .NET Standard hedeflediğinden, bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasından çağrılabilir. Daha fazla bilgi için [.NET Standard](/dotnet/standard/net-standard).

3. Sağ bölmedeki **sınıf kitaplığı (.NET Standard)** şablonunu seçin ve aşağıdaki görüntüde gösterildiği gibi **ad** metin kutusuna **StringLibrary** yazın:

   ![** Ekleme yeni proje ** iletişim](./media/lut-start/add-project-cs.png)

4. Seçin **Tamam** projeyi oluşturmak için.

::: moniker-end

::: moniker range=">=vs-2019"

2. Şablon arama kutusuna **sınıf kitaplığı** yazın ve **sınıf kitaplığı (.NET Standard)** şablonunu seçin. **İleri**’ye tıklayın.

   > [!NOTE]
   > Kitaplığımız belirli bir .NET uygulamasının yerine .NET Standard hedeflediğinden, bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasından çağrılabilir. Daha fazla bilgi için [.NET Standard](/dotnet/standard/net-standard).

3. Proje **StringLibrary**olarak adlandırın.

4. Projeyi oluşturmak için **Oluştur** ' a tıklayın.

::: moniker-end

5. Tüm mevcut kodlar kod penceresinde, aşağıdaki kodla değiştirin:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary üç statik yönteme sahiptir:

   - `StartsWithUpper` döndürür `true` Aksi halde, bir dizeyi büyük harfli bir karakterle; başlarsa döndürür `false`.

   - `StartsWithLower`döndürür `true` Aksi halde, bir dize bir küçük harf karakteri ile; başlarsa döndürür `false`.

   - `HasEmbeddedSpaces` döndürür `true` bir katıştırılmış bir boşluk karakteri; bir dize içeriyorsa, aksi takdirde, döndürür `false`.

6. Seçin **derleme** > **Çözümü Derle** en üst düzey Visual Studio menüsünde. Derleme başarılı olmalıdır.

## <a name="create-the-test-project"></a>Test projesi oluşturma

Sonraki adım, StringLibrary kitaplığını test etmek için birim test projesi oluşturmaktır. Birim testleri, aşağıdaki adımları uygulayarak oluşturun:

1. **Çözüm Gezgini**' de, kullanımı uygun**Yeni proje**öğesine sağ tıklayın ve ardından **Ekle** >  ' yi seçin.

::: moniker range="vs-2017"

2. İçinde **Yeni Proje Ekle** iletişim kutusunda Seç C# düğümünü seçip **.NET Core**.

   > [!NOTE]
   > Birim testleri, sınıf kitaplığı olarak aynı dilde yazmak zorunda değildir.

3. Sağ bölmedeki **birim testi projesi (.NET Core)** şablonunu seçin ve aşağıdaki görüntüde gösterildiği gibi **ad** metin kutusuna **stringlibrarytests** yazın:

   ![** Ekleme yeni proje ** iletişim kutusu için birim test projesi](./media/lut-start/add-unit-test-cs.png)

4. Seçin **Tamam** projeyi oluşturmak için.

::: moniker-end

::: moniker range=">=vs-2019"

2. Şablon arama kutusuna **birim testi** yazın ve **birim test projesi (.NET Core)** şablonunu seçin. **İleri**’ye tıklayın.

3. Projeyi **Stringlibrarytests**olarak adlandırın.

4. Projeyi oluşturmak için **Oluştur** ' a tıklayın.

::: moniker-end

   > [!NOTE]
   > Bu kullanmaya başlama öğreticilerinde Live Unit Testing ile MSTest test çerçevesi kullanır. XUnit ve NUnit test çerçeveleri de kullanabilirsiniz.

5. Birim test projesi otomatik olarak test ettiği sınıf kitaplığı erişemez. Sınıf kitaplığı projesine bir başvuru ekleyerek, test kitaplığı erişimi sağlar. Bunu yapmak için sağ `StringLibraryTests` seçin ve proje **Ekle** > **başvuru**. **Başvuru Yöneticisi** iletişim kutusunda, **çözüm** sekmesinin seçili olduğundan emin olun ve aşağıdaki görüntüde gösterildiği gibi StringLibrary projesini seçin.

   ![** ** Başvuru Yöneticisi iletişim kutusu](./media/lut-start/add-reference.png)

6. Aşağıdaki kod ile şablon tarafından sağlanan Demirbaş birim testi kodu değiştirin:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Seçerek projenizi kaydetmek **Kaydet** araç çubuğundaki simgeye.

8. Birim test kodu bazı ASCII olmayan karakterler içerdiğinden, Visual Studio dosyayı varsayılan ASCII biçiminde kaydederseniz bazı karakterlerin kaybolacağını uyarmak için aşağıdaki iletişim kutusunu görüntüler. Seçin **diğer kodlama ile Kaydet** düğmesi.

   ![Dosya kodlama seçin](media/lut-start/ascii-encoding.png)

9. Aşağıdaki görüntüde gösterildiği gibi, **Gelişmiş kaydetme seçenekleri** Iletişim kutusunun **kodlama** açılan LISTESINDE **Unicode (imzasız UTF-8)-kod sayfası 65001**' u seçin:

   ![UTF-8 kodlaması seçme](media/lut-start/utf8-encoding.png)

10. Birim test projesi seçerek derleyin **derleme** > **çözümü yeniden derle** en üst düzey Visual Studio menüsünde.

Bunun için bir sınıf kitaplığı ve bunun yanı sıra bazı birim testlerinin oluşturdunuz. Live Unit Testing kullanmak için gereken hazırlık aşamaları artık tamamladınız.

## <a name="enable-live-unit-testing"></a>Live Unit Testing etkinleştir

Şimdiye kadar, StringLibrary sınıf kitaplığı için testleri yazmış olsanız da onları çalıştırmadınız. Etkinleştirdikten sonra Live Unit Testing bunları otomatik olarak yürütür. Bunu yapmak için aşağıdakileri yapın:

1. İsteğe bağlı olarak, StringLibrary kodunu içeren kod penceresini seçin. Bu *Class1.cs* bir C# projesi için veya *Class1.vb* Visual Basic projesi için. (Bu adım, Live Unit Testing etkinleştirdikten sonra testlerinizin sonucunu ve kod kapsamınız kapsamını görsel olarak incelemenize olanak sağlar.)

1. Seçin **Test** > **Live Unit Testing** > **Başlat** en üst düzey Visual Studio menüsünde.

1. Canlı birim testlerinizi otomatik olarak çalışan Test, Visual Studio başlatılır.

Testlerinizi çalıştıran tamamlandığında **Test Gezgini** hem genel sonuçları, hem de tek tek testlerin sonuçlarını görüntüler. Ayrıca, kod penceresi grafik, test kod kapsamı hem testleriniz için sonuç görüntüler. Aşağıdaki görüntüde gösterildiği gibi, üç testin hepsi başarıyla yürütülür. Ayrıca testlerimizin tüm kod yollarında kapsamına gösterir `StartsWithUpper` yöntemi ve başarılı bir şekilde yürütüldü bu testlerin tümü ("✓" Yeşil onay işaretiyle belirtilir). Son olarak, StringLibrary 'deki diğer yöntemlerin hiçbirinin kod kapsamı (mavi bir çizgi ile belirtilir, "➖") olduğunu gösterir.

![Live Unit testing'i başlatma sonra Test Gezgini ve kod penceresi](media/lut-start/lut-results-cs.png)

Kod penceresinde belirli kod kapsamı simgesini seçerek kapsamı ve test sonuçlarını test hakkında daha ayrıntılı bilgiler de alabilirsiniz. Bu ayrıntılı incelemek için aşağıdakileri yapın:

1. Yeşil bir onay işareti yazan satıra tıklayın `if (String.IsNullOrWhiteSpace(s))` içinde `StartsWithUpper` yöntemi. Aşağıdaki görüntüde gösterildiği gibi, Live Unit Testing üç testin bu kod satırını kapsadığını ve tümünün başarıyla yürütüldüğünü belirtir.

   !['If' koşul deyimi için kod kapsamı](media/lut-start/code-coverage-cs1.png)

1. Yeşil bir onay işareti yazan satıra tıklayın `return Char.IsUpper(s[0])` içinde `StartsWithUpper` yöntemi. Aşağıdaki görüntüde gösterildiği gibi, Live Unit Testing yalnızca iki testin bu kod satırını kapsadığını ve tümünün başarıyla yürütüldüğünü gösterir.

   ![Return deyimi için kod kapsamı](media/lut-start/code-coverage-cs2.png)

Live Unit Testing tanımlayan önemli bir sorun tamamlanmamış kod kapsamı ' dir. Sonraki bölümde karşılayabilirsiniz.

## <a name="expand-test-coverage"></a>Test kapsamı genişletin

Birim testleriniz genişletmek Bu bölümde, `StartsWithLower` yöntemi. Bunu, ancak Live Unit Testing dinamik olarak kodunuzu test etmek devam eder.

Kod kapsamını genişletmek için `StartsWithLower` yöntemi, aşağıdakileri yapın:

1. Aşağıdaki `TestStartsWithLower` ve `TestDoesNotStartWithLower` projenizin test kaynak kodunu yöntemleri:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Değiştirme `DirectCallWithNullOrEmpty` yöntem çağrısının hemen sonra aşağıdaki kodu ekleyerek [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) yöntemi.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Kaynak kodunuzu değiştirdiğinizde Live Unit Testing yeni ve değiştirilen testleri otomatik olarak yürütür. Aşağıdaki **Test Gezgini** görüntüsünde gösterildiği gibi, eklediğiniz iki ve değiştirdiğiniz bir öğe de dahil olmak üzere tüm testler başarılı olmuştur.

   ![Test kapsamını genişlettikten sonra test Gezgini](media/lut-start/test-dynamic.png)

1. StringLibrary sınıfının kaynak kodunu içeren pencereye geçiş yapın. Live Unit Testing bizim kod kapsamı için genişletilmiş şimdi gösterir `StartsWithLower` yöntemi.

    ![Kod kapsamı StartsWithLower yöntemi](media/lut-start/lut-extended-cs.png)

Bazı durumlarda, başarılı testler **Test Gezgini** grileştirilmiş olabilir. Bir test şu anda yürütülmekte olan veya son yürütülen olduğundan test olduğundan, kod değişiklikleri yeniden çalıştırılamayan test erişememeleri gösterir.

Şu ana kadar tüm yaptığımız testleri başarılı olduğunda. Sonraki bölümde, test hatası nasıl işleyebileceğini inceleyeceğiz.

## <a name="handle-a-test-failure"></a>Test hatası işleme

Bu bölümde, nasıl Live Unit Testing belirlemek, sorun giderme ve test hatalarını gidermek için kullanabileceğiniz hakkında bilgi edineceksiniz. İçin test kapsamını genişleterek bunu yaparsınız `HasEmbeddedSpaces` yöntemi.

1. Test dosyanıza aşağıdaki yöntemi ekleyin:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Test yürütüldüğünde Live Unit Testing, aşağıdaki görüntüde gösterildiği gibi `TestHasEmbeddedSpaces` yönteminin başarısız olduğunu gösterir:

   ![Başarısız testi bildiren test Gezgini](media/lut-start/test-failure.png)

1. Kitaplık kodu görüntüler penceresi seçin. Live Unit Testing, `HasEmbeddedSpaces` yöntemine kod kapsamını genişletti. Kırmızı ekleyerek de test hatası raporları "🞩" testler başarısız tarafından kapsanan satırlar için.

1. Satırı üzerine `HasEmbeddedSpaces` metodu imzası. Live Unit Testing, aşağıdaki görüntüde gösterildiği gibi, yöntemin bir test tarafından kapsanmakta olduğunu raporlayan bir araç ipucu görüntüler:

   ![Başarısız test hakkındaki bilgileri Live Unit Testing](media/lut-start/test-failure-info-cs.png)

1. Başarısız seçin **TestHasEmbeddedSpaces** test edin. Live Unit Testing, aşağıdaki görüntüde gösterildiği gibi, tüm testleri çalıştırma, seçilen testleri çalıştırma, tüm testlerde hata ayıklama ve seçili testlerin hatalarını ayıklama gibi çeşitli seçenekler sunar:

   ![Başarısız test için Live Unit Testing seçenekleri](media/lut-start/test-failure-options.png)

1. Seçin **seçili hata ayıklama** başarısız test hatalarını ayıklamak için.

1. Visual Studio test hata ayıklama modunda yürütülür.

   Test, bir dizideki her dizeyi `phrase` adlı bir değişkene atar ve `HasEmbeddedSpaces` yöntemine geçirir. Program yürütme duraklatır ve hata ayıklayıcı ilk saat onayı ifade çağırır `false`. [@No__t-1](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) Yöntem çağrısındaki beklenmeyen değerin sonucu olan özel durum iletişim kutusu aşağıdaki görüntüde gösterilmiştir.

   ![Live Unit Testing özel durum iletişim kutusu](media/lut-start/exception-dialog-cs.png)

   Ayrıca, aşağıdaki görüntüde gösterildiği gibi, Visual Studio 'nun sunduğu tüm hata ayıklama araçları, başarısız sınamamız hakkında sorun gidermeye yardımcı olmak için kullanılabilir:

   ![Visual Studio hata ayıklama araçları](media/lut-start/debugging-tools-cs.png)

   İçinde Not **Otolar** penceresi, değerini `phrase` değişkeni "Name\tDescription" olduğu dizinin ikinci öğesi ise. Test yöntemi bekliyor `HasEmbeddedSpaces` döndürülecek `true` bunun yerine, bu dize; geçirildiğinde döndürür `false`. Evidently, onu sekme karakteri, "\t", katıştırılmış bir boşluk algılamaz.

1. Seçin **hata ayıklama** > **devam**, basın **F5**, veya **devam** yürütmeye devam araç çubuğunda Test programı. İşlenmeyen bir özel durum oluştuğundan test sonlandırır.
Bu hatanın bir ön araştırma için yeterli bilgi sağlar. Her iki `TestHasEmbeddedSpaces` (test yordamı) yapılan yanlış bir varsayım veya `HasEmbeddedSpaces` doğru tüm gömülü boşluklar tanımıyor.

1. Sorunu tanılamak ve düzeltmek için `StringLibrary.HasEmbeddedSpaces` yöntemiyle başlayın. Karşılaştırmada bakın `HasEmbeddedSpaces` yöntemi. Bunu, U + 0020 olmasını katıştırılmış bir boşluk olarak kabul eder. Ancak, Unicode standardı diğer boşluk karakterleri içerir. Bu, kitaplık kodu yanlış bir boşluk karakteri sınadığı önerir.

1. Eşitlik karşılaştırma çağrısı ile Değiştir <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> yöntemi:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing başarısız test yöntemini otomatik olarak yeniden çalıştırır ve aşağıdaki görüntüde gösterildiği gibi kod penceresinde ve **Test Gezgininde**sonuçları güncelleştirir:

    ![Başarılı HasEmbeddedSpaces testi](media/lut-start/test-success-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Live Unit Testing](live-unit-testing.md)
- [Live Unit Testing sık sorulan sorular](live-unit-testing-faq.md)