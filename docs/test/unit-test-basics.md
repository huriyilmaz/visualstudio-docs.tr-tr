---
title: Birim testi temelleri
description: Test Gezgini Visual Studio nin birim testlerinizi çalıştırmanın ve sonuçlarını görüntülemenin esnek ve verimli bir yolunu nasıl sağladığını öğrenin.
ms.date: 12/28/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 7d36ff9219c3bcffafee8f742e454a8e78d63e6d
ms.sourcegitcommit: 96b09d12bec776367737f91e56e46cec85ad3376
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2022
ms.locfileid: "135700530"
---
# <a name="unit-test-basics"></a>Birim testi temel bilgileri

Birim testleri oluşturarak ve çalıştırarak kodunuzun beklendiği gibi çalışa çalışa bir kontrol edin. Bu, program işlevselliğini ayrı ayrı birim olarak test etmek için sınanabilir davranışlara dönüştüren birim testi olarak adlandırılan bir *özelliktir.* Visual Studio Test Gezgini, birim testlerinizi çalıştırmanın ve sonuçlarını farklı bir şekilde görüntülemenin esnek ve verimli bir Visual Studio. Visual Studio, yönetilen ve yerel kod için Microsoft birim testi çerçevelerini yüklür. Birim testleri *oluşturmak, çalıştırmak* ve bu testlerin sonuçlarını rapor etmek için birim testi çerçevesi kullanın. Kodunuzun hala düzgün çalıştığını test etmek için değişiklikler yaptığınız zaman birim testlerini yeniden çalıştırma. Visual Studio Enterprise kod değişikliklerinizin [etkilendiği testleri algılayan ve](live-unit-testing-intro.md)siz yazarak arka planda çalıştıran Live Unit Testing ile bunu otomatik olarak yapabilirsiniz.

Birim testi, yazılım geliştirme iş akışınız için önemli bir parça olduğunda kodunuzun kalitesi üzerinde en büyük etkiye sahiptir. Bir işlev veya başka bir uygulama kodu bloğu yazar yazmaz, standart, sınır ve yanlış giriş verileri durumlarına yanıt olarak kodun davranışını doğrular ve kod tarafından yapılan açık veya örtülü varsayımları kontrol eder. Test *güdümlü geliştirme* ile, kodu yazmadan önce birim testlerini oluşturabilirsiniz, bu nedenle birim testlerini hem tasarım belgeleri hem de işlevsel belirtimler olarak kullanırız.

Test Gezgini, Test Gezgini eklenti arabirimlerini uygulayan üçüncü taraf ve açık kaynak birim test çerçevelerini de çalıştırabilirsiniz. Visual Studio Extension Manager ve Visual Studio galerisi aracılığıyla bu çerçevelerin Visual Studio ebilirsiniz. Daha fazla bilgi için [bkz. Üçüncü taraf birim test çerçevelerini yükleme.](../test/install-third-party-unit-test-frameworks.md)

Test projelerini ve test yöntemlerini kodunuzdan hızla oluşturabilir veya ihtiyacınız olan testleri el ile oluşturabilirsiniz. .NET kodunu keşfetmek için IntelliTest'i kullanarak test verileri ve birim testi paketi oluşturabilirsiniz. Kodda yer alan her deyim için, bu deyimi yürütecek bir test girişi oluşturulur. .NET kodu [için birim testleri oluşturma hakkında bilgi bulabilirsiniz.](generate-unit-tests-for-your-code-with-intellitest.md)

## <a name="get-started"></a>başlarken

Sizi doğrudan kodlamaya alan birim testlerine giriş için şu konulardan birini ele alın:

- [Adım adım kılavuz: .NET kodu için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Adım adım kılavuz: Test Gezgini ile test güdümlü geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Visual Studio'da C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>MyBank çözüm örneği

Bu makalede örnek olarak adlı kurgusal bir uygulamanın `MyBank` geliştirilmesini kullanıyoruz. Bu konudaki açıklamaları takip etmek için gerçek koda ihtiyacınız yok. Test yöntemleri C# ile yazılır ve Yönetilen Kod için Microsoft Birim Testi Çerçevesi kullanılarak sunulmaktadır. Ancak kavramlar diğer dillere ve çerçevelere kolayca aktarılır.

::: moniker range="vs-2017"
![MyBank Çözümü](../test/media/ute_mybanksolution.png)
::: moniker-end
::: moniker range="vs-2019"
![MyBank Çözümü 2019](../test/media/vs-2019/basics-mybank-solution.png)
::: moniker-end
::: moniker range=">=vs-2022"
![MyBank Çözümü 2022](../test/media/vs-2022/basics-mybank-solution.png)
::: moniker-end

Uygulama tasarımında ilk girişimimiz tek bir hesabı ve bankayla yaptığı işlemleri temsil eden bir hesap bileşeni ve tek tek hesapları toplama ve yönetme işlevselliğini temsil eden bir `MyBank` veritabanı bileşeni içerir.

İki proje `MyBank` içeren bir çözüm oluşturacağız:

- `Accounts`

- `BankDb`

Projeyi tasarlamaya ilişkin ilk girişimimiz bir hesapla ilgili temel bilgileri tutmak için bir sınıf, hesaptan varlıklarını almak ve geri almak gibi her türlü hesabın ortak işlevselliğini belirten bir arabirim ve bir denetim hesabını temsil eden arabirimden türetilen bir sınıf `Accounts` içerir. Hesaplar projelerine başlamak için aşağıdaki kaynak dosyaları oluşturacağız:

- *AccountInfo.cs,* bir hesabın temel bilgilerini tanımlar.

- *IAccount.cs,* bir hesaptan varlıklarını alma ve hesap bakiyesini alma yöntemlerini içeren standart `IAccount` bir arabirim tanımlar.

- *CheckingAccount.cs,* `CheckingAccount` bir denetim hesabı için `IAccount` arabirimi uygulayan sınıfı içerir.

Bir çek hesabından gelen bir şeyin geri çekilen tutarın hesap bakiyesi altında olduğundan emin olmak gerektiğini deneyimden biliyoruz. Bu nedenle, içinde `IAccount.Withdraw` yöntemini bu koşulu kontrol alan bir yöntemle geçersiz `CheckingAccount` kılaruz. yöntemi aşağıdaki gibi olabilir:

```csharp
public void Withdraw(double amount)
{
    if(m_balance >= amount)
    {
        m_balance -= amount;
    }
    else
    {
        throw new ArgumentException(nameof(amount), "Withdrawal exceeds balance!");
    }
}
```

Koda sahip olduğunuza göre test zamanı geldi.

## <a name="create-unit-test-projects-and-test-methods-c"></a>Birim testi projeleri ve test yöntemleri oluşturma (C#)

C# için genellikle birim testi projesini ve birim testi saplamalarını kodunuzdan oluşturmak daha hızlıdır. Veya gereksinimlerinize bağlı olarak birim testi projesini ve testleri el ile oluşturabilirsiniz. Üçüncü taraf çerçeve ile koddan birim testleri oluşturmak için şu uzantılardan birinin yüklü olması gerekir: [NUnit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371) veya [xUnit](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator). C# kullanmadısanız bu bölümü atlayıp Birim testi projesini [ve birim testlerini el ile](#create-the-unit-test-project-and-unit-tests-manually)oluşturma bölümüne gidin.

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Birim testi projesi ve birim testi saplamaları oluşturma

1. Kod düzenleyicisi penceresinde sağ tıklayın ve sağ tıklama [**menüsünden Birim**](create-unit-tests-menu.md) Testleri Oluştur'u seçin.

   ::: moniker range="vs-2017"
   ![Düzenleyici penceresinde bağlam menüsünü görüntüleme](../test/media/createunittestsrightclick.png)

   > [!NOTE]
   > Birim **Testleri Oluştur menü** komutu yalnızca .NET Core'.NET Framework yönetilen kod için kullanılabilir.
   ::: moniker-end
   ::: moniker range="vs-2019"
   ![Düzenleyici penceresinde bağlam menüsünü görüntüleme](../test/media/vs-2019/basics-create-unit-tests.png)

   > [!NOTE]
   > Birim **Testleri Oluştur menü** komutu yalnızca C# kodu için kullanılabilir. Bu yöntemi .NET Core veya .NET Standard kullanmak için Visual Studio 2019 gerekir.
   ::: moniker-end

   ::: moniker range=">=vs-2022"
   ![Düzenleyici penceresinde bağlam menüsünü görüntüleme](../test/media/vs-2022/basics-create-unit-tests.png)

   > [!NOTE]
   > Birim **Testleri Oluştur menü** komutu yalnızca C# kodu için kullanılabilir. Bu yöntemi .NET Core veya .NET Standard kullanmak için Visual Studio 2019 gerekir.
   ::: moniker-end

2. Birim **testlerinizi** oluşturmak için varsayılan değerleri kabul etmek için Tamam'a tıklayın veya birim testi projesini ve birim testlerini oluşturmak ve ad olarak değiştirmek için kullanılan değerleri değiştirebilirsiniz. Birim testi yöntemlerine varsayılan olarak eklenen kodu seçin.

   ::: moniker range="<=vs-2019"
   ![Visual Studio'da Birim Testleri Oluştur iletişim Visual Studio](../test/media/create-unit-tests.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio'da Birim Testleri Oluştur iletişim Visual Studio](../test/media/vs-2022/create-unit-tests.png)
   ::: moniker-end

3. Birim testi saplamaları, sınıfındaki tüm yöntemler için yeni bir birim testi projesinde oluşturulur.

   ::: moniker range="vs-2017"
   ![Birim testleri oluşturulur](../test/media/createunittestsstubs.png)
   ::: moniker-end
   ::: moniker range="vs-2019"
   ![Birim testleri oluşturulur](../test/media/vs-2019/basics-test-stub.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Birim testleri oluşturulur](../test/media/vs-2022/basics-test-stub.png)
   ::: moniker-end

4. Şimdi, birim testlerinizi [](#write-your-tests) anlamlı hale gelecek şekilde testlerinizi yazmayı ve kodunuzu kapsamlı bir şekilde test etmek için eklemek istediğiniz ek birim testlerini öğrenin.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Birim testi projesini ve birim testlerini el ile oluşturma

Birim testi projesi genellikle tek bir kod projesinin yapısını yansıtıyor. MyBank örneğinde çözüme ve adlı iki birim testi `AccountsTests` `BankDbTests` projesi `MyBanks` eklersiniz. Test projesi adları rastgeledir, ancak standart adlandırma kuralının benimsenerek iyi bir fikirdir.

**Bir çözüme birim testi projesi eklemek için:**

1. Bu **Çözüm Gezgini,** çözüme sağ tıklayın ve Yeni Ekle'yi **Project.**  >   

::: moniker range="vs-2017"

2. Yeni **Project** iletişim kutusunda Yüklü düğümünü  genişletin, test projeniz için kullanmak istediğiniz dili seçin ve ardından Test'i **seçin.**

3. Microsoft birim testi çerçevelerinden birini kullanmak için proje şablonları **listesinden Birim Testi Project'yi** seçin. Aksi takdirde, kullanmak istediğiniz birim testi çerçevesinin proje şablonunu seçin. Örneğimizin `Accounts` projesini test etmek için projeyi olarak `AccountsTests` adlarsiniz.

   > [!NOTE]
   > Tüm üçüncü taraf ve açık kaynak birim test çerçeveleri bir proje Visual Studio sağlamaz. Proje oluşturma hakkında bilgi için çerçeve belgesine bakın.

::: moniker-end

::: moniker range=">=vs-2019"

2. Kullanmak **istediğiniz** test çerçevesine bir birim testi proje şablonu bulmak için proje şablonu arama kutusuna test yazın. (Bu konudaki örneklerde MSTest kullanıyoruz.)

3. Sonraki sayfada projeyi olarak ad girin. Örneğimizin `Accounts` projesini test etmek için projeyi olarak ad vesersiniz. `AccountsTests`

::: moniker-end

4. Birim testi projenize, bizim örneğimizde, test altındaki kod projesine bir başvuru ekleyin Hesaplar projesi.

   Kod projesine başvuru oluşturmak için:
   
   1. Çözüm Gezgini'daki birim testi projesinde, Başvurular  veya  Bağımlılıklar düğümüne sağ  tıklayın ve ardından Project Başvurusu ekle veya Başvuru Ekle **'yi**(hangisi varsa) seçin.

   2. Başvuru Yöneticisi **iletişim kutusunda** Çözüm düğümünü açın **ve** Projeler'i **seçin.** Kod projesi adını seçin ve iletişim kutusunu kapatın.

Her birim testi projesi, kod projesinde sınıfların adlarını yansıtan sınıflar içerir. Bizim örneğimizde `AccountsTests` proje aşağıdaki sınıfları içerir:

- `AccountInfoTests` sınıfı, projesinde sınıfı için birim `AccountInfo` testi yöntemlerini `Accounts` içerir

- `CheckingAccountTests` sınıfı, sınıfının birim testi yöntemlerini `CheckingAccount` içerir.

## <a name="write-your-tests"></a>Testlerinizi yazma

IntelliSense'i kullanarak Visual Studio test çerçevesi, kod projesi için birim testlerinizi yazmanız için size yol sağlar. **Test Gezgini'nde çalıştırmak** için çoğu çerçeve, birim testi yöntemlerini tanımlamak için belirli öznitelikler eklemenizi gerektirir. Çerçeveler ayrıca test yönteminin başarılı veya başarısız olduğunu belirtmek için genellikle onay deyimleri veya yöntem öznitelikleri aracılığıyla bir yol sağlar. Diğer öznitelikler, sınıf başlatma sırasında ve her test yöntemi ve her test yöntemi sonra ve sınıfı yok olmadan önce çalıştırılma yöntemleri önce isteğe bağlı kurulum yöntemlerini tanımlama.

AAA (Düzenle, Eylem, Onay) düzeni, test altındaki bir yöntem için birim testleri yazmanın yaygın bir yolu.

- Birim  testi yönteminin Düzenle bölümü nesneleri başlatıyor ve test altındaki yöntemine geçirilen verilerin değerini ayarlar.

- **Sahne** bölümü, düzenlenmiş parametrelerle test edilen yöntemi çağırır.

- **Onaylama** bölümü, test kapsamındaki yöntemin eyleminin beklendiği gibi davranacağını doğrular. .NET için, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> sınıftaki yöntemler genellikle doğrulama için kullanılır.

`CheckingAccount.Withdraw`Örneğimizin yöntemini test etmek için iki test yazabiliriz: yöntemin standart davranışını doğrulayan ve bakiyesinden daha fazla olan bir çekme 'nın başarısız olacağını doğrulayan bir tane (Aşağıdaki kod, .net 'te desteklenen bir MSTest birim testi gösterir.). `CheckingAccountTests`Sınıfında, aşağıdaki yöntemleri ekleyeceğiz:

```csharp
[TestMethod]
public void Withdraw_ValidAmount_ChangesBalance()
{
    // arrange
    double currentBalance = 10.0;
    double withdrawal = 1.0;
    double expected = 9.0;
    var account = new CheckingAccount("JohnDoe", currentBalance);

    // act
    account.Withdraw(withdrawal);

    // assert
    Assert.AreEqual(expected, account.Balance);
}

[TestMethod]
public void Withdraw_AmountMoreThanBalance_Throws()
{
    // arrange
    var account = new CheckingAccount("John Doe", 10.0);

    // act and assert
    Assert.ThrowsException<System.ArgumentException>(() => account.Withdraw(20.0));
}
```

Microsoft birim testi çerçeveleri hakkında daha fazla bilgi için aşağıdaki konulardan birine bakın:

- [Kodunuzun birim testi](unit-test-your-code.md)

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

- [Birim testlerinde MSTest çerçevesini kullanma](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

## <a name="set-timeouts-for-unit-tests"></a>Birim testleri için zaman aşımlarını ayarla

MSTest çerçevesini kullanıyorsanız, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TimeoutAttribute> tek bir test yönteminde bir zaman aşımı ayarlamak için kullanabilirsiniz:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

Zaman aşımını izin verilen üst sınıra ayarlamak için:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a>Testleri test Gezgini 'nde Çalıştır

Test projesi oluşturduğunuzda, testler **Test Gezgini**'nde görünür. **test gezgini** görünür değilse, Visual Studio menüsünde **Test** ' i seçin, **Windows**' i seçin ve ardından **Test gezgini** ' ni seçin (veya **Ctrl**  +  **E**, **T**' ye basın).

::: moniker range="vs-2017"
![Birim test Gezgini](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range="vs-2019"
![Birim test Gezgini](../test/media/vs-2019/basics-test-explorer.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Birim test Gezgini](../test/media/vs-2022/basics-test-explorer.png)
::: moniker-end

Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, **Test Gezgini** sonuçları **başarısız testler**, **başarılı** testler, **Atlanan testler** ve **çalıştırma** testleri grupları halinde görüntüleyebilir. Araç çubuğunda farklı grupla seçenekleri arasından seçim yapabilirsiniz.

Ayrıca, genel düzeydeki arama kutusundaki metni eşleştirerek veya önceden tanımlanmış filtrelerden birini seçerek herhangi bir görünümdeki testleri filtreleyebilirsiniz. Herhangi bir zamanda testlerin herhangi bir seçimini çalıştırabilirsiniz. Bir test çalıştırmasının sonuçları, Gezgin penceresinin en üstündeki geçiş/başarısızlık çubuğunda hemen görünür. Test yöntemi sonucunun ayrıntıları, testi seçtiğinizde görüntülenir.

### <a name="run-and-view-tests"></a>Testleri çalıştırma ve görüntüleme

**Test Gezgini** araç çubuğu ilgilendiğiniz testleri keşfetmenize, düzenlemenize ve çalıştırmanıza yardımcı olur.

::: moniker range="vs-2017"
![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range="vs-2019"
![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/vs-2022/test-explorer-toolbar-diagram-17-0.png)
::: moniker-end

Tüm testlerinizi çalıştırmak **için Tümünü Çalıştır** seçeneğini veya   +  çalıştırılacak testlerin bir alt kümesini seçmek için **Çalıştır** ' ı ( **CTRL**  +  **r**, **T**) seçebilirsiniz. Test ayrıntıları bölmesinde bu testin ayrıntılarını görüntülemek için bir test seçin. Seçili testin kaynak kodunu göstermek için sağ tıklama menüsünde (klavye: **F12**) **testi aç** ' ı seçin.

::: moniker range="vs-2017"

Bireysel testlerin herhangi bir sırada çalıştırılmasını önleyen bir bağımlılığı yoksa, paralel test yürütme özelliğini ![Visual Studio test gezgini araç çubuğundaki paralel test yürütme geçiş düğmesi ekran görüntüsü.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.

::: moniker-end

::: moniker range=">=vs-2019"

Bireysel testlerin herhangi bir sırada çalıştırılmasını engelleyen bir bağımlılığı yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütme ' yi açın. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.

::: moniker-end

### <a name="run-tests-after-every-build"></a>Her derlemeden sonra Testleri Çalıştır

::: moniker range="vs-2017"

|Düğme|Description|
|-|-|
|![Derlemeden sonra Çalıştır](../test/media/ute_runafterbuild_btn.png)|Her yerel derlemeden sonra birim testlerinizi çalıştırmak için standart menüdeki **Test** ' i seçin ve ardından **Test Gezgini** araç çubuğunda **derlemeden sonra Testleri Çalıştır** ' ı seçin.|

> [!NOTE]
> her derlemeden sonra birim testlerini çalıştırmak için Visual Studio 2017 Enterprise edition veya Visual Studio 2019 gerekir. Visual Studio 2019 ' de, özelliği Enterprise edition 'ın yanı sıra Community ve Professional edition 'da bulabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

Her yerel derlemeden sonra birim testlerinizi çalıştırmak için, test Gezgini araç çubuğunda Ayarlar simgesini açın ve **derlemeden sonra Testleri Çalıştır**' ı seçin.

::: moniker-end

### <a name="filter-and-group-the-test-list"></a>Test listesini filtreleme ve gruplandırma

Çok sayıda testiniz olduğunda, listeyi belirtilen dizeye göre filtrelemek için **Test Gezgini** arama kutusunu yazabilirsiniz. Filtre listesinden seçim yaparak filtre olaylarınızı daha fazla kısıtlayabilirsiniz.

::: moniker range="vs-2017"
![Filtre kategorilerini ara](../test/media/ute_searchfilter.png)
::: moniker-end
::: moniker range="vs-2019"
![Filtre kategorilerini ara](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Filtre kategorilerini ara](../test/media/vs-2022/test-explorer-search-filter-17-0.png)
::: moniker-end

|Düğme|Description|
|-|-|
|![Test Gezgini Grup düğmesi](../test/media/ute_groupby_btn.png)|Testlerinizi kategoriye göre gruplandırmak için **Gruplandırma ölçütü** düğmesini seçin.|

Daha fazla bilgi için bkz. [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md).

## <a name="qa"></a>Soru-Cevap

**S: birim testlerinde hata ayıkla Nasıl yaparım??**

Y **:** Testleriniz için bir hata ayıklama oturumu başlatmak için **Test Gezgini** 'ni kullanın. Visual Studio hata ayıklayıcı ile kodunuzda adım adım geçiş, birim testleri ve test edilen proje arasında sorunsuz bir şekilde geri ve ileri doğru bir şekilde gerçekleşir. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hata ayıklamak istediğiniz bir veya daha fazla test yöntemlerinde bir kesme noktası ayarlayın.

    > [!NOTE]
    > Test yöntemleri herhangi bir sırada çalıştırılabildiğinden, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktaları ayarlayın.

2. **Test Gezgini**'nde test yöntemlerini seçin ve sonra kısayol menüsünden **Seçili testlerin hatalarını ayıkla** ' yı seçin.

[Birim testlerinde hata ayıklama](../debugger/debugger-feature-tour.md)hakkında daha fazla bilgi edinin.

**S: TDD kullanıyorum, testlerimde nasıl kod oluşturabilirim?**

Y **:** Proje kodunuzda sınıflar ve yöntemler oluşturmak için hızlı eylemler kullanın. Oluşturmak istediğiniz sınıfı veya yöntemi çağıran bir test yönteminde bir ifade yazın, ardından hata altında görüntülenen ampul ' ı açın. Çağrı yeni sınıfın bir oluşturucusuna ise, menüden **tür oluştur** ' u seçin ve sınıfı kod projenize eklemek için Sihirbazı izleyin. Çağrı bir yönteme ise, IntelliSense menüsünde **Yöntem Oluştur** ' u seçin.

::: moniker range="vs-2017"
![Yöntem saplama hızlı eylem menüsünü oluştur](../test/media/ute_generatemethodstubintellisense.png)
::: moniker-end
::: moniker range="vs-2019"
![Yöntem saplama hızlı eylem menüsünü oluştur](../test/media/vs-2019/basics-generate-method-tdd.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Yöntem saplama hızlı eylem menüsünü oluştur](../test/media/vs-2022/basics-generate-method-tdd.png)
::: moniker-end

**S: testi çalıştırmak için girdi olarak birden çok veri kümesi alan birim testleri oluşturabilir miyim?**

**Y:** Evet. *Veri tabanlı test yöntemleri* , tek bir birim testi yöntemiyle bir değer aralığını test etmenize olanak sağlar. Test `DataSource` yöntemi için, test etmek istediğiniz değişken değerlerini içeren veri kaynağını ve tabloyu belirten bir öznitelik kullanın.  Yöntem gövdesinde, `TestContext.DataRow[` *ColumnName* Dizin oluşturucuyu kullanarak satır değerlerini değişkenlere atarsınız `]` .

> [!NOTE]
> Bu yordamlar yalnızca, yönetilen kod için Microsoft birim testi çerçevesini kullanarak yazdığınız test yöntemleri için geçerlidir. Farklı bir Framework kullanıyorsanız, eşdeğer işlevsellik için Framework belgelerine başvurun.

Örneğin, adlı sınıfa gereksiz bir yöntem eklediğimiz varsayın `CheckingAccount` `AddIntegerHelper` . `AddIntegerHelper` iki tamsayı ekler.

Yöntemi için veri odaklı bir test oluşturmak için `AddIntegerHelper` önce *AccountsTest. accdb* adlı bir erişim veritabanı ve adlı bir tablo oluşturacağız `AddIntegerHelperData` . `AddIntegerHelperData`Tablo, toplama ve beklenen sonucu belirten bir sütunun ilk ve ikinci işlenenlerini belirtmek için sütunları tanımlar. Uygun değerlere sahip bir dizi satırı doldurduk.

```csharp
[DataSource(
    @"Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\Projects\MyBank\TestData\AccountsTest.accdb",
    "AddIntegerHelperData"
)]
[TestMethod()]
public void AddIntegerHelper_DataDrivenValues_AllShouldPass()
{
    var target = new CheckingAccount();
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.AddIntegerHelper(x, y);
    Assert.AreEqual(expected, actual);
}
```

Öznitelikli Yöntem tablodaki her satır için bir kez çalışır. Yinelemelerden herhangi biri başarısız olursa **Test Gezgini** yöntemi için bir test hatası raporlar. Yöntemi için test sonuçları ayrıntı bölmesi, her veri satırı için geçiş/başarısız durum yöntemini gösterir.

[Veri tabanlı birim testleri](../test/how-to-create-a-data-driven-unit-test.md)hakkında daha fazla bilgi edinin.

**S: kodumun ne kadarının birim Testlerimin test edildiğini görüntüleyebilir miyim?**

**Y:** Evet. Visual Studio Enterprise ' de Visual Studio kod kapsamı aracını kullanarak, gerçekten birim testleriniz tarafından test edilmiş kodunuzun miktarını belirleyebilirsiniz. Birim test çerçevesi tarafından çalıştırılabilen yerel ve yönetilen diller ve tüm birim testi çerçeveleri desteklenir.

Seçili testlerde veya bir Çözümdeki tüm testlerde kod kapsamını çalıştırabilirsiniz. **Kod kapsamı sonuçları** penceresi, satır, işlev, sınıf, ad alanı ve modül tarafından uygulanan ürün kodu bloklarının yüzdesini görüntüler.

Bir çözümde test yöntemleri için kod kapsamını çalıştırmak için **Test**  >  **kodu kapsamını tüm testler için Çözümle**' yi seçin.

Kapsam sonuçları, **kod kapsamı sonuçları** penceresinde görünür.

::: moniker range="<=vs-2019"
![Kod kapsamı sonuçları](../test/media/ute_codecoverageresults.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Kod kapsamı sonuçları](../test/media/vs-2022/ute-code-coverage-results.png)
::: moniker-end

[Kod kapsamı](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)hakkında daha fazla bilgi edinin.

**S: kodumdaki dış bağımlılıklara sahip yöntemleri test edebilir miyim?**

**Y:** Evet. Visual Studio Enterprise sahipseniz, Microsoft Fakes yönetilen kod için birim test çerçeveleri kullanarak yazdığınız test yöntemleriyle birlikte kullanılabilir.

Microsoft Fakes dış bağımlılıklar için alternatif sınıflar oluşturmak üzere iki yaklaşımdan yararlanır:

1. *Saplamalar* , hedef bağımlılık sınıfının üst arabiriminden türetilmiş yedek sınıflar oluşturur. Saplama yöntemleri, hedef sınıfın ortak sanal yöntemlerinin yerine kullanılabilir.

2. *Dolgu* , sanal olmayan metotlar için bir hedef yönteme yönelik yedek dolgu metoduna yapılan çağrıları incelemek üzere çalışma zamanı izleme kullanır.

Her iki yaklaşımdaki test yönteminde istediğiniz davranışı belirtmek için bağımlılık yöntemine yapılan çağrıların oluşturulan temsilciler kullanılır.

[Birim test yöntemlerini Microsoft Fakes yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)hakkında daha fazla bilgi edinin.

**S: birim testlerini oluşturmak için başka birim testi çerçeveleri kullanabilir miyim?**

Y **:** Evet, [diğer çerçeveleri bulmak ve yüklemek](../test/install-third-party-unit-test-frameworks.md)için aşağıdaki adımları izleyin. Visual Studio yeniden başlattıktan sonra, birim testlerinizi oluşturmak için çözümünüzü yeniden açın ve ardından yüklü çerçevelerinizi buradan seçin:

![Diğer yüklü birim test çerçevesini seçin](../test/media/createunittestsdialogextensions.png)

Birim testi saplamaları, seçilen Framework kullanılarak oluşturulacaktır.
