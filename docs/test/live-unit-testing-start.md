---
title: Canlı birim testi ile kodunuzu test etme hakkında bilgi edinin
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5b136c91873c0af60705ea361a19e53f28e06b0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653050"
---
# <a name="get-started-with-live-unit-testing"></a>Live Unit Testing kullanmaya başlama

Visual Studio çözümünde Live Unit Testing etkinleştirdiğinizde, test kapsamınız ve testlerinizin durumunu görsel olarak gösterir. Live Unit Testing Ayrıca, kodunuzun her değişiklik yaptığınızda testleri dinamik olarak yürütür ve değişiklikleriniz testlerin başarısız olmasına neden olduğunda sizi anında bilgilendirir.

Live Unit Testing, .NET Framework ya da .NET Core ' u hedefleyen çözümleri test etmek için kullanılabilir. Bu öğreticide, .NET Standard hedefleyen basit bir sınıf kitaplığı oluşturarak Live Unit Testing kullanacağınızı öğrenirsiniz ve test etmek üzere .NET Core 'u hedefleyen bir MSTest projesi oluşturacaksınız.

Tamamen C# çözüm, GitHub 'Daki [microsoftdocs/VisualStudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) deposundan indirilebilir.

## <a name="prerequisites"></a>Prerequisites

Bu öğreticide, **.NET Core platformlar arası geliştirme** iş yüküne Visual Studio Enterprise Edition sürümünü yüklemiş olmanız gerekir.

## <a name="create-the-solution-and-the-class-library-project"></a>Çözüm ve sınıf kitaplığı projesi oluşturma

Tek bir .NET Standard Class Library projesinden (StringLibrary) oluşan bir Visual Studio çözümü oluşturarak başlayın.

Çözüm yalnızca bir veya daha fazla proje için bir kapsayıcıdır. Boş bir çözüm oluşturmak için Visual Studio 'Yu açın ve aşağıdakileri yapın:

1. En üst düzey Visual Studio menüsünden **dosya**  > **Yeni**  > **Proje** ' yi seçin.

1. Şablon arama kutusuna **çözüm** yazın ve ardından **boş çözüm** şablonunu seçin.

   ::: moniker range="vs-2017"

   ![\* * Yeni proje * * iletişim kutusu](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Çözümü oluşturmayı tamamlama.

Çözümü oluşturduğunuza göre, dizeler ile çalışmak için birkaç uzantı yöntemi içeren StringLibrary adlı bir sınıf kitaplığı oluşturacaksınız.

1. **Çözüm Gezgini**, kullanımı uygun proje çözümüne sağ tıklayın ve  > **Yeni proje** **Ekle** ' yi seçin.

::: moniker range="vs-2017"

2. **Yeni Proje Ekle** iletişim kutusunda düğümünü ve C# ardından **.NET Standard**' yi seçin.

   > [!NOTE]
   > Kitaplığımız belirli bir .NET uygulamasının yerine .NET Standard hedeflediğinden, bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasından çağrılabilir. Daha fazla bilgi için bkz. [.NET Standard](/dotnet/standard/net-standard).

3. Sağ bölmedeki **sınıf kitaplığı (.NET Standard)** şablonunu seçin ve aşağıdaki görüntüde gösterildiği gibi **ad** metin kutusuna **StringLibrary** yazın:

   ![\* * Yeni Proje Ekle * * iletişim kutusu](./media/lut-start/add-project-cs.png)

4. Projeyi oluşturmak için **Tamam ' ı** seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. Şablon arama kutusuna **sınıf kitaplığı** yazın ve **sınıf kitaplığı (.NET Standard)** şablonunu seçin. **İleri**'ye tıklayın.

   > [!NOTE]
   > Kitaplığımız belirli bir .NET uygulamasının yerine .NET Standard hedeflediğinden, bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasından çağrılabilir. Daha fazla bilgi için bkz. [.NET Standard](/dotnet/standard/net-standard).

3. Proje **StringLibrary**olarak adlandırın.

4. Projeyi oluşturmak için **Oluştur** ' a tıklayın.

::: moniker-end

5. Kod penceresindeki tüm mevcut kodu aşağıdaki kodla değiştirin:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary üç statik yönteme sahiptir:

   - `StartsWithUpper`, bir dize büyük harfle başlıyorsa `true` döndürür; Aksi takdirde, `false` döndürür.

   - bir dize küçük harfli bir karakterle başlıyorsa `true` `StartsWithLower`returns. Aksi takdirde, `false` döndürür.

   - bir dize gömülü bir boşluk karakteri içeriyorsa `HasEmbeddedSpaces` `true` döndürür. Aksi takdirde, `false` döndürür.

6. Üst düzey Visual Studio menüsünden **build**  > **Build Solution** öğesini seçin. Derleme başarılı olmalıdır.

## <a name="create-the-test-project"></a>Test projesi oluşturma

Sonraki adım, StringLibrary kitaplığını test etmek için birim test projesi oluşturmaktır. Aşağıdaki adımları gerçekleştirerek birim testlerini oluşturun:

1. **Çözüm Gezgini**, kullanımı uygun proje çözümüne sağ tıklayın ve  > **Yeni proje** **Ekle** ' yi seçin.

::: moniker range="vs-2017"

2. **Yeni Proje Ekle** iletişim kutusunda C# düğümünü seçin, sonra **.NET Core**' u seçin.

   > [!NOTE]
   > Birim testlerinizi, sınıf kitaplığınız ile aynı dilde yazmanız gerekmez.

3. Sağ bölmedeki **birim testi projesi (.NET Core)** şablonunu seçin ve aşağıdaki görüntüde gösterildiği gibi **ad** metin kutusuna **stringlibrarytests** yazın:

   ![Birim test projesi için * * yeni proje Ekle * * iletişim kutusu](./media/lut-start/add-unit-test-cs.png)

4. Projeyi oluşturmak için **Tamam ' ı** seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. Şablon arama kutusuna **birim testi** yazın ve **birim test projesi (.NET Core)** şablonunu seçin. **İleri**'ye tıklayın.

3. Projeyi **Stringlibrarytests**olarak adlandırın.

4. Projeyi oluşturmak için **Oluştur** ' a tıklayın.

::: moniker-end

   > [!NOTE]
   > Bu Başlangıç Öğreticisi, MSTest test çerçevesiyle Live Unit Testing kullanır. Ayrıca xUnit ve NUnit test çerçevelerini de kullanabilirsiniz.

5. Birim testi projesi test edilen sınıf kitaplığına otomatik olarak erişemez. Sınıf kitaplığı projesine bir başvuru ekleyerek test Kitaplığı erişimi verirsiniz. Bunu yapmak için `StringLibraryTests` projesine sağ tıklayın ve  > **başvuru** **Ekle** ' yi seçin. **Başvuru Yöneticisi** iletişim kutusunda, **çözüm** sekmesinin seçili olduğundan emin olun ve aşağıdaki görüntüde gösterildiği gibi StringLibrary projesini seçin.

   ![\* * Reference Manager * * iletişim kutusu](./media/lut-start/add-reference.png)

6. Şablon tarafından sunulan ortak birim test kodunu şu kodla değiştirin:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Araç çubuğundaki **Kaydet** simgesini seçerek projenizi kaydedin.

8. Birim test kodu bazı ASCII olmayan karakterler içerdiğinden, Visual Studio dosyayı varsayılan ASCII biçiminde kaydederseniz bazı karakterlerin kaybolacağını uyarmak için aşağıdaki iletişim kutusunu görüntüler. **Diğer kodlamaya sahip Kaydet** düğmesini seçin.

   ![Dosya kodlaması seçin](media/lut-start/ascii-encoding.png)

9. Aşağıdaki görüntüde gösterildiği gibi, **Gelişmiş kaydetme seçenekleri** Iletişim kutusunun **kodlama** açılan LISTESINDE **Unicode (imzasız UTF-8)-kod sayfası 65001**' u seçin:

   ![UTF-8 kodlamasını seçme](media/lut-start/utf8-encoding.png)

10. Üst düzey Visual Studio menüsünden **derle**  > **yeniden derle çözümünü** seçerek birim testi projesini derleyin.

Bir sınıf kitaplığı ve bunun için bazı birim testlerini oluşturdunuz. Artık Live Unit Testing kullanmak için gereken başlangıç kuralları tamamladınız.

## <a name="enable-live-unit-testing"></a>Live Unit Testing etkinleştir

Şimdiye kadar, StringLibrary sınıf kitaplığı için testleri yazmış olsanız da onları çalıştırmadınız. Live Unit Testing, bunları etkinleştirdikten sonra otomatik olarak yürütür. Bunu yapmak için aşağıdakileri yapın:

1. İsteğe bağlı olarak, StringLibrary kodunu içeren kod penceresini seçin. Bu, bir C# proje için Class1.cs veya Visual Basic projesi için *Class1. vb* ' dir. (Bu adım, Live Unit Testing etkinleştirdikten sonra testlerinizin sonucunu ve kod kapsamınız kapsamını görsel olarak incelemenize olanak sağlar.)

1. **Test**  > **Live Unit Testing**  >  en üst düzey Visual Studio menüsünden**Başlat** ' ı seçin.

1. Visual Studio, tüm testlerinizi otomatik olarak çalıştıran canlı birim testi başlatır.

Testlerinizi çalıştırmayı bitirdiğinde, **Test Gezgini** hem genel sonuçları hem de bireysel testlerin sonucunu görüntüler. Ayrıca, kod penceresi hem test kodu kapsamınızla hem de testleriniz için sonucu grafik olarak görüntüler. Aşağıdaki görüntüde gösterildiği gibi, üç testin hepsi başarıyla yürütülür. Ayrıca, sınamalarımızın `StartsWithUpper` yöntemindeki tüm kod yollarını kapsadığından ve bu testlerin başarıyla yürütüldüğü (yeşil onay işareti, "✓" ile belirtilir) gösterilmektedir. Son olarak, StringLibrary 'deki diğer yöntemlerin hiçbirinin kod kapsamı (mavi bir çizgi ile belirtilir, "➖") olduğunu gösterir.

![Canlı birim testi başladıktan sonra test Gezgini ve kod penceresi](media/lut-start/lut-results-cs.png)

Ayrıca, kod penceresinde belirli bir kod kapsamı simgesini seçerek test kapsamı ve test sonuçları hakkında daha ayrıntılı bilgi edinebilirsiniz. Bu ayrıntıyı incelemek için aşağıdakileri yapın:

1. @No__t_1 yönteminde `if (String.IsNullOrWhiteSpace(s))` okuyan satırdaki yeşil onay işaretine tıklayın. Aşağıdaki görüntüde gösterildiği gibi, Live Unit Testing üç testin bu kod satırını kapsadığını ve tümünün başarıyla yürütüldüğünü belirtir.

   ![' İf ' koşullu bildiriminde kod kapsamı](media/lut-start/code-coverage-cs1.png)

1. @No__t_1 yönteminde `return Char.IsUpper(s[0])` okuyan satırdaki yeşil onay işaretine tıklayın. Aşağıdaki görüntüde gösterildiği gibi, Live Unit Testing yalnızca iki testin bu kod satırını kapsadığını ve tümünün başarıyla yürütüldüğünü gösterir.

   ![Return ifadesinin kod kapsamı](media/lut-start/code-coverage-cs2.png)

Live Unit Testing tanımladığı önemli sorun, tamamlanmamış kod kapsamı. Sonraki bölümde bu adresi görürsünüz.

## <a name="expand-test-coverage"></a>Test kapsamını Genişlet

Bu bölümde, birim testlerinizi `StartsWithLower` yöntemine genişleteceksiniz. Bunu yaptığınızda, Live Unit Testing kodunuzu test etmek için dinamik olarak devam eder.

Kod kapsamını `StartsWithLower` yöntemine genişletmek için aşağıdakileri yapın:

1. Aşağıdaki `TestStartsWithLower` ve `TestDoesNotStartWithLower` yöntemlerini projenizin test kaynak kodu dosyasına ekleyin:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. [@No__t_2](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu ekleyerek `DirectCallWithNullOrEmpty` yöntemini değiştirin.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing, kaynak kodunuzu değiştirirken yeni ve değiştirilmiş testleri otomatik olarak yürütür. Aşağıdaki **Test Gezgini** görüntüsünde gösterildiği gibi, eklediğiniz iki ve değiştirdiğiniz bir öğe de dahil olmak üzere tüm testler başarılı olmuştur.

   ![Test kapsamını genişlettikten sonra test Gezgini](media/lut-start/test-dynamic.png)

1. StringLibrary sınıfının kaynak kodunu içeren pencereye geçiş yapın. Live Unit Testing artık kod kapsamımızın `StartsWithLower` yöntemine genişletilmişse gösterilmektedir.

    ![StartsWithLower yöntemi için kod kapsamı](media/lut-start/lut-extended-cs.png)

Bazı durumlarda, **Test Gezgini** 'ndeki başarılı testler gri renkte olabilir. Bu, bir testin yürütülmekte olduğunu veya testin en son yürütüldüğünden bu yana etkilenmeyen hiçbir kod değişikliği olmadığından testin yeniden çalıştırılmadığını gösterir.

Şimdiye kadar, tüm sınamalarımız başarılı oldu. Sonraki bölümde, test başarısızlığını nasıl işleyebileceğini inceleyeceğiz.

## <a name="handle-a-test-failure"></a>Test başarısızlığı işleme

Bu bölümde, test başarısızlıklarını belirlemek, sorunlarını gidermek ve gidermek için Live Unit Testing nasıl kullanabileceğinizi keşfedebilirsiniz. Bunu, `HasEmbeddedSpaces` yöntemine test kapsamını genişleterek gerçekleştirirsiniz.

1. Aşağıdaki yöntemi test dosyanıza ekleyin:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Test yürütüldüğünde Live Unit Testing, aşağıdaki görüntüde gösterildiği gibi `TestHasEmbeddedSpaces` yönteminin başarısız olduğunu gösterir:

   ![Başarısız testi bildiren test Gezgini](media/lut-start/test-failure.png)

1. Kitaplık kodunu görüntüleyen pencereyi seçin. Live Unit Testing, `HasEmbeddedSpaces` yöntemine kod kapsamını genişletti. Ayrıca, başarısız testlerin kapsadığı çizgilere kırmızı bir "🞩" ekleyerek test başarısızlığını raporlar.

1. @No__t_0 yöntemi imzasıyla satırın üzerine gelin. Live Unit Testing, aşağıdaki görüntüde gösterildiği gibi, yöntemin bir test tarafından kapsanmakta olduğunu raporlayan bir araç ipucu görüntüler:

   ![Başarısız test hakkındaki bilgileri Live Unit Testing](media/lut-start/test-failure-info-cs.png)

1. Başarısız **Testhasembeddedspaces** testini seçin. Live Unit Testing, aşağıdaki görüntüde gösterildiği gibi, tüm testleri çalıştırma, seçilen testleri çalıştırma, tüm testlerde hata ayıklama ve seçili testlerin hatalarını ayıklama gibi çeşitli seçenekler sunar:

   ![Başarısız test için Live Unit Testing seçenekleri](media/lut-start/test-failure-options.png)

1. Başarısız testin hatalarını ayıklamak için **Seçili hata ayıkla** ' yı seçin.

1. Visual Studio, testi hata ayıklama modunda yürütür.

   Test, bir dizideki her dizeyi `phrase` adlı bir değişkene atar ve `HasEmbeddedSpaces` yöntemine geçirir. Program yürütme, ilk kez onaylama ifadesi `false` hata ayıklayıcıyı duraklatır ve çağırır. [@No__t_1](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) yöntemi çağrısındaki beklenmeyen değerin sonucu olan özel durum iletişim kutusu aşağıdaki görüntüde gösterilmiştir.

   ![Live Unit Testing özel durum iletişim kutusu](media/lut-start/exception-dialog-cs.png)

   Ayrıca, aşağıdaki görüntüde gösterildiği gibi, Visual Studio 'nun sunduğu tüm hata ayıklama araçları, başarısız sınamamız hakkında sorun gidermeye yardımcı olmak için kullanılabilir:

   ![Visual Studio hata ayıklama araçları](media/lut-start/debugging-tools-cs.png)

   **&** Lt; 1} öğesinin `phrase` değerinin, dizinin ikinci öğesi olan "adı tdescription" olduğunu unutmayın. Test yöntemi, bu dizeyi geçtiğinde `HasEmbeddedSpaces` `true` döndürmesini bekler; Bunun yerine, `false` döndürür. Daha açık bir şekilde, "\t", sekme karakterini gömülü bir boşluk olarak tanımaz.

1. **Hata ayıkla**  > **devam et**' i seçin, **F5**tuşuna basın veya test programını yürütmeye devam etmek için araç çubuğundaki **devam** düğmesine tıklayın. İşlenmemiş bir özel durum oluştuğundan, test sonlanır.
Bu, hatanın ön araştırması için yeterli bilgi sağlar. @No__t_0 (test yordamı) yanlış bir varsayım yaptı veya `HasEmbeddedSpaces` gömülü tüm boşlukları doğru bir şekilde tanımıyor.

1. Sorunu tanılamak ve düzeltmek için `StringLibrary.HasEmbeddedSpaces` yöntemiyle başlayın. @No__t_0 yöntemindeki karşılaştırmaya bakın. Bir katıştırılmış alanı U + 0020 olarak değerlendirir. Ancak, Unicode standart birkaç boşluk karakteri içerir. Bu, kitaplık kodunun bir boşluk karakteri için yanlış test edilmiş olduğunu önerir.

1. Eşitlik karşılaştırmasını <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> yöntemi çağrısıyla değiştirin:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing başarısız test yöntemini otomatik olarak yeniden çalıştırır ve aşağıdaki görüntüde gösterildiği gibi kod penceresinde ve **Test Gezgininde**sonuçları güncelleştirir:

    ![Başarılı HasEmbeddedSpaces testi](media/lut-start/test-success-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da Live Unit Testing](live-unit-testing.md)
- [Live Unit Testing sık sorulan sorular](live-unit-testing-faq.md)