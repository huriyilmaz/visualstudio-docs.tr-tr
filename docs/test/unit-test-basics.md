---
title: Birim testi temelleri
ms.date: 08/07/2019
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77ac5ffd14f97fd6fdd753327fe193ceb80ea57e
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846925"
---
# <a name="unit-test-basics"></a>Birim testi temel bilgileri

Kod oluşturma ve birim testleri çalıştırarak beklendiği gibi çalışıp çalışmadığını denetleyin. Birim test, test edebilirsiniz ayrık test edilebilir davranışları programınızın işlevlerini olarak tek tek bölümlere ayırmak denir *birimleri*. Visual Studio Test Gezgini, birim testleri çalıştırmak ve Visual Studio'da sonuçlarını görüntülemek için esnek ve verimli bir yol sağlar. Visual Studio için Microsoft birim test çerçeveler yönetilen ve yerel kod için yükler. Kullanım bir *birim testi çerçevesi* birim testleri oluşturmak için bunları çalıştırmak ve bu testlerin sonuçları rapor. Kodunuzun düzgün çalışıp çalışmadığını test etmek için değişiklik yaptığınız zaman yeniden çalıştır birim testleri. Visual Studio Enterprise ile otomatik olarak bunu yapabilirsiniz [Live Unit Testing](live-unit-testing-intro.md), hangi kodunuz tarafından etkilenen testleri algılar değiştirir ve bunları siz yazarken arka planda çalışır.

Yazılım geliştirme iş akışınızın bir parçası olduğunda birim testi kodunuzun kalitesini üzerinde en büyük etkiye sahiptir. Bir işlev veya diğer blok uygulama kodu yazdığınız hemen ardından standart, sınır ve giriş verisi hatalı durumda yanıt kodu davranışını doğrulayın ve kod tarafından yapılan açık veya örtülü varsayımlar kontrol birim testleri oluşturun. İle *test güdümlü geliştirme*, birim testleri tasarım belgeleri ve işlevsel özellikleri kullanmak için kod yazmadan önce birim testleri oluşturun.

Test projelerini hızla oluşturmak ve kodunuzdan test yöntemleri veya ihtiyaç duyduğunuz gibi el ile testler oluşturun. .NET kodunuzu keşfetmek için Intellitest kullandığınızda, test verileri ve birim testleri paketi oluşturabilirsiniz. Koddaki her ifade için bir test girişi oluşturulur o ifadeyi yürütecek. Hakkında bilgi edinin [kodunuz için birim testleri oluşturma](generate-unit-tests-for-your-code-with-intellitest.md).

Test Gezgini, Test Gezgini eklentisi arabirimleri uyguladıysanız birim testi çerçevelerini üçüncü taraf ve açık kaynak da çalıştırabilirsiniz. Birçok Visual Studio Uzantı Yöneticisi ve Visual Studio Galerisi aracılığıyla bu çerçevesini ekleyebilirsiniz. Daha fazla bilgi için [üçüncü taraf birim testi çerçevelerini yükleme](../test/install-third-party-unit-test-frameworks.md).

## <a name="get-started"></a>Kullanmaya başlayın

Doğrudan kodlama içine alan birim testine giriş için aşağıdaki konulardan birine bakın:

- [İzlenecek yol: Oluşturma ve yönetilen kod için birim testleri çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Hızlı Başlangıç: temelli geliştirme, Test Gezgini ile Test](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Visual Studio'da C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>MyBank çözümü örneği

Bu makalede, örnek olarak `MyBank` adlı kurgusal bir uygulamanın geliştirilmesini kullanırız. Bu konudaki açıklamaları izlemek için gerçek kod gerekmez. Test yöntemlerini C# dilinde yazılmış ve yönetilen kod için Microsoft birim testi çerçevesini kullanarak sunulur. Ancak, diğer dillerde ve çerçevelerde kavramları kolayca aktarılır.

::: moniker range="vs-2017"
![MyBank çözümü](../test/media/ute_mybanksolution.png)
::: moniker-end
::: moniker range=">=vs-2019"
![MyBank çözümü 2019](../test/media/vs-2019/basics-mybank-solution.png)
::: moniker-end

Bizim için bir tasarım ilk denemesini `MyBank` uygulama ayrı bir hesap ve kendi banka işlemleri temsil eden bir hesapları bileşen ve toplama ve yönetmek için işlevleri temsil eden bir veritabanı bileşeni içerir Bireysel hesaplar.

Oluşturduğumuz bir `MyBank` iki proje içeren bir çözümü:

- `Accounts`

- `BankDb`

Bizim ilk denemesini tasarlama `Accounts` projesini içeren bir hesap, ortak işlevsellik ürünü ve hesabı ve bir sınıf varlıklar geri alınmasının gibi hesabının herhangi bir türde belirten bir arabirim hakkındaki temel bilgileri tutmak için bir sınıf Çek hesabı temsil eden arabirimden türetilmiş. Aşağıdaki kaynak dosyaları oluşturarak hesapları projeleri başlamadan:

- *AccountInfo.cs* hesabınız için temel bilgileri tanımlar.

- *IAccount.cs* bir standardı tanımlar `IAccount` havale ve varlıklar bir hesaptan geri alma ve hesap bakiyesi almak için yöntemleri dahil olmak üzere, hesap için arabirim.

- *CheckingAccount.cs* içeren `CheckingAccount` uygulayan sınıf `IAccount` Çek hesabı için arabirim.

Çek Hesabı hesabından yapmanız gereken, bir şey çekilen miktarın bakiyeden hesap bakiyesinden daha az olduğundan emin olmaktır deneyiminden biliyoruz. Biz geçersiz kılmak için `IAccount.Withdraw` yönteminde `CheckingAccount` denetleyen ve bu koşul için bir yöntem. Yöntem şuna benzeyebilir:

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

Biz bazı koda sahip olduğunuza göre bunu test etmek için zamanı geldi.

## <a name="create-unit-test-projects-and-test-methods"></a>Birim test projesi oluşturmak ve test yöntemleri

Genellikle, kod birim testi saptamalar ve birim testi projesi oluşturmak hızlı olur. Veya, gereksinimlerinize bağlı olarak el ile testleri ve birim testi projesi oluşturmak tercih edebilirsiniz. Bir 3. taraf çerçevesiyle birim testleri oluşturmak istiyorsanız şu uzantılardan birinin yüklü olması gerekir: [NUnit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371) veya [xUnit](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator).

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Birim testi projesi oluşturma ve birim testi saptamaları

1. Kod Düzenleyicisi penceresinde sağ tıklayın ve sağ tıklama menüsünde [**Birim Testleri Oluştur**](create-unit-tests-menu.md) ' u seçin.

   ::: moniker range="vs-2017"
   ![Bağlam menüsü düzenleyici penceresinde görüntüleme](../test/media/createunittestsrightclick.png)

   > [!NOTE]
   > **Birim Testleri Oluştur** menü komutu yalnızca .NET Framework hedefleyen yönetilen kod için kullanılabilir (.NET Core 'u değil).
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Bağlam menüsü düzenleyici penceresinde görüntüleme](../test/media/vs-2019/basics-create-unit-tests.png)

   > [!NOTE]
   > **Birim Testleri Oluştur** menü komutu yalnızca yönetilen kod için kullanılabilir.
   ::: moniker-end

2. Tıklayın **Tamam** birim testleri oluşturma veya oluşturma ve birim testi projesi ve birim testlerini adı için kullanılan değerleri değiştirmek için Varsayılanları kabul etmek için. Varsayılan olarak, birim test yöntemlerini için eklenen kodu seçebilirsiniz.

   ![Visual Studio 'da birim testleri oluştur iletişim kutusu](../test/media/create-unit-tests.png)

3. Birim test Saplamaları sınıfındaki tüm yöntemler için yeni bir birim test projesi oluşturulur.

   ::: moniker range="vs-2017"
   ![Birim testlerini oluşturulur](../test/media/createunittestsstubs.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Birim testlerini oluşturulur](../test/media/vs-2019/basics-test-stub.png)
   ::: moniker-end

4. Bilgi edinmek için artık ileriye gitmek nasıl [kodu için birim test yöntemlerini ekleyin](#write-your-tests) anlamlı birim sınamanız ve kodunuzu sınamanız eklemek isteyebileceğiniz herhangi bir ek birim test yapma.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Birim testi el ile proje ve birim testleri oluşturma

Birim testi projesi genellikle tek bir kod proje yapısını yansıtır. Adlı iki birim testi projelerini eklediğiniz MyBank örnekte `AccountsTests` ve `BankDbTests` için `MyBanks` çözüm. Test proje adı isteğe bağlı, ancak standart bir adlandırma kuralı benimseyen iyi bir fikirdir.

**Birim testi projesi çözüme eklemek için:**

1. **Çözüm Gezgini**, çözüme sağ tıklayın ve > **Yeni** **Proje** **Ekle** ' yi seçin.

::: moniker range="vs-2017"

2. İçinde **yeni proje** iletişim kutusunda **yüklü** düğümü, test projeniz için kullanın ve ardından istediğiniz dili seçin **Test**.

3. Microsoft birim testi çerçevelerini birini kullanmak üzere, **Birim Test projesi** proje şablonları listesinden. Aksi takdirde, kullanmak istediğiniz test çerçevesi biriminin proje şablonu seçin. Sınanacak `Accounts` proje örneğimiz, proje garip gelse `AccountsTests`.

   > [!NOTE]
   > Tüm üçüncü taraf ve açık kaynak birim testi çerçevelerini bir Visual Studio Proje şablonu sağlar. Bir proje oluşturma hakkında daha fazla bilgi için framework belgeye başvurun.

::: moniker-end

::: moniker range=">=vs-2019"

2. Kullanmak istediğiniz test çerçevesinin birim testi proje şablonunu bulmak için proje şablonu arama kutusunu kullanın.

3. Sonraki sayfada, projeyi adlandırın. Örneğimizin `Accounts` projeyi test etmek için, proje `AccountsTests`adını yazabilirsiniz.

::: moniker-end

4. Birim test projenizde örneğimizde hesapları projesi için test edilen kod projesine bir başvuru ekleyin.

   Kod projesine bir başvuru oluşturmak için:

   1. Projede seçin **Çözüm Gezgini**.

   2. Üzerinde **proje** menüsünde seçin **Başvuru Ekle**.

   3. Üzerinde **başvuru Yöneticisi** açık iletişim kutusunu **çözüm** düğüm ve **projeleri**. Kod proje adını seçin ve iletişim kutusunu kapatın.

Her birim testi projesi kod projesinde sınıfların adlarını yansıtan sınıfları içerir. Bizim örneğimizde `AccountsTests` proje aşağıdaki sınıfları içerebilir:

- `AccountInfoTests` sınıfı için birim test yöntemlerini içeren `AccountInfo` sınıfını `Accounts` proje

- `CheckingAccountTests` sınıfı için birim test yöntemlerini içeren `CheckingAccount` sınıfı.

## <a name="write-your-tests"></a>Testlerinizi yazma

Birim testi çerçevesi kullandığınız ve Visual Studio IntelliSense birim testleriniz için bir kod projesi için kod yazma aracılığıyla size yol gösterir. Çalıştırılacak **Test Gezgini**, çoğu çerçeveleri, birim tanımlamak için özel öznitelikler test yöntemleri eklemeniz gerekir. Çerçeveleri ayrıca bir yol sağlar; genellikle aracılığıyla deyimleri ya da yöntem öznitelikleri assert — test yöntemi başarılı olup olmadığını belirtmek için. Diğer öznitelikleri sınıf başlatma ve her bir test yöntemi ve her test yönteminin sonra ve sınıf yok önce çalıştırılır kaldırma yöntemleri önce isteğe bağlı kurulum yöntemlerle belirleyin.

AAA (Düzenle, eylem, onay) düzeni, test edilen bir yöntem için birim testleri yazma genel bir yoludur.

- **Yerleştir** bölümü bir birim test yöntemi, nesneleri başlatır ve yöntemi testten geçirilen verileri değerini ayarlar.

- **Yasası** bölüm düzenlenmiş parametrelerle test altındaki yöntemi çağırır.

- **Assert** bölümü, test altındaki yöntem eylem beklendiği gibi çalıştığını doğrular.

Sınanacak `CheckingAccount.Withdraw` yöntemi Bizim örneğimizde, biz iki test yazabilirsiniz: standart yöntemin davranışını doğrular ve birden çok bakiyesi olan bir mevzuatı başarısız olacağını doğrular. İçinde `CheckingAccountTests` sınıfı, biz aşağıdaki yöntemleri ekleyin:

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

Microsoft birim testi çerçevelerini hakkında daha fazla bilgi için aşağıdaki konulardan birine bakın:

- [Birim testi kod](unit-test-your-code.md)

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

- [MSTest framework birim testleri kullanın](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

## <a name="set-timeouts-for-unit-tests"></a>Birim testleri için zaman aşımını ayarlayın

MSTest çerçevesini kullanıyorsanız, tek bir test yönteminde zaman aşımı ayarlamak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TimeoutAttribute> kullanabilirsiniz:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

İzin verilen maksimum zaman aşımını ayarlamak için:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a>Testleri Test Gezgini'nde çalıştırma

Testleri test projesini oluşturduğunuzda görünür **Test Gezgini**. Varsa **Test Gezgini** görünür durumda değilse seçin **Test** Visual Studio menüsünde **Windows**ve ardından **Test Gezgini**.

::: moniker range="vs-2017"
![Birim Test Gezgini](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Birim Test Gezgini](../test/media/vs-2019/basics-test-explorer.png)
::: moniker-end

Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, **Test Gezgini** sonuçları **başarısız testler**, **başarılı**testler, **Atlanan testler** ve **çalıştırma**testleri grupları halinde görüntüleyebilir. Araç çubuğunda farklı grupla seçenekleri arasından seçim yapabilirsiniz.

Ayrıca, arama kutusuna genel düzeyde eşleşen metin veya önceden tanımlanmış filtrelerden birini seçerek herhangi bir görünümde testlere filtre uygulayabilirsiniz. Herhangi bir zamanda herhangi bir seçimi testler çalıştırabilirsiniz. Bir test çalıştırması sonuçlarını hemen Gezgini penceresinin en üstündeki geçer/başarısız çubuğunda görünür. Bir test yönteminin sonucunun ayrıntılarını test seçtiğinizde görüntülenir.

### <a name="run-and-view-tests"></a>Testleri görüntülemek ve çalıştırmak

**Test Gezgini** araç, keşfedin, düzenlemek ve ilginizi çeken testler yardımcı olur.

::: moniker range="vs-2017"
![Test Gezgini araç çubuğundan Testleri Çalıştır](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini araç çubuğundan Testleri Çalıştır](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

Seçebileceğiniz **tümünü Çalıştır** tüm testleri çalıştırmak veya **çalıştırma** bir alt kümesini Çalıştırılacak testleri seçmek için. Test ayrıntıları bölmesinde bu testin ayrıntılarını görüntülemek için bir test seçin. Seçili testin kaynak kodunu göstermek için sağ tıklama menüsünde (klavye: **F12**) **testi aç** ' ı seçin.

::: moniker range="vs-2017"

Bireysel testler herhangi bir sırada çalıştırılan engelleyen bağımlılık varsa, paralel test yürütme ile Aç ![ALIŞTIR&#95;parallelicon&#45;küçük](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.

::: moniker-end

::: moniker range=">=vs-2019"

Bireysel testlerin herhangi bir sırada çalıştırılmasını engelleyen bir bağımlılığı yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütme ' yi açın. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.

::: moniker-end

### <a name="run-tests-after-every-build"></a>Her derleme sonrasında Testleri Çalıştır

::: moniker range="vs-2017"

|Düğme|Açıklama|
|-|-|
|![Yapıdan sonra çalıştırmak](../test/media/ute_runafterbuild_btn.png)|Her yerel derlemeden sonra birim testlerinizi çalıştırmak için standart menüdeki **Test** ' i seçin ve ardından **Test Gezgini** araç çubuğunda **derlemeden sonra Testleri Çalıştır** ' ı seçin.|

> [!NOTE]
> Her derleme sonrasında birim testlerini çalıştırmak, Visual Studio 2017 Enterprise Edition veya Visual Studio 2019 gerektirir. Visual Studio 2019 ' de, özelliği Enterprise Edition 'ın yanı sıra Community ve Professional Edition 'da bulabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

Her yerel derlemeden sonra birim testlerinizi çalıştırmak için, test Gezgini araç çubuğunda Ayarlar simgesini açın ve **derlemeden sonra Testleri Çalıştır**' ı seçin.

::: moniker-end

### <a name="filter-and-group-the-test-list"></a>Test listesini gruplandırma ve filtreleme

Çok sayıda testiniz olduğunda, listeyi belirtilen dizeye göre filtrelemek için **Test Gezgini** arama kutusunu yazabilirsiniz. Filtre etkinliğiniz filtre listeden seçerek daha fazla kısıtlayabilirsiniz.

::: moniker range="vs-2017"
![Arama filtre kategorisi](../test/media/ute_searchfilter.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Arama filtre kategorisi](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

|Düğme|Açıklama|
|-|-|
|![Test Gezgini Grup düğmesi](../test/media/ute_groupby_btn.png)|Kategoriye göre testlerinizi gruplamak için seçin **Group By** düğmesi.|

Daha fazla bilgi için [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md).

## <a name="qa"></a>SORU- CEVAP

**S: nasıl birim testleri debug?**

**Y:** kullanım **Test Gezgini** testleriniz için hata ayıklama oturumu başlatmak için. Kodunuzu Visual Studio hata ayıklayıcısı ile sorunsuz bir şekilde Adımlama, İleri ve geri birim testleri ve test altındaki projeye arasında sürer. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hatalarını ayıklamak istediğiniz bir veya daha fazla test yöntemlerinde kesme noktası ayarlayın.

    > [!NOTE]
    > Test yöntemleri herhangi bir sırada çalışabileceğinden, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktalarını ayarlayın.

2. İçinde **Test Gezgini**, test yöntemlerini seçin ve ardından **seçilen Testlerde Hata Ayıkla** kısayol menüsünden.

Hakkında daha ayrıntılı bilgi edinin [birim testleri hata ayıklama](../debugger/debugger-feature-tour.md).

**S: TDD kullanıyorum varsa nasıl miyim kod benim testlerden oluşturun?**

Y **:** Proje kodunuzda sınıflar ve yöntemler oluşturmak için hızlı eylemler kullanın. Oluşturmak istediğiniz sınıfı veya yöntemi çağıran bir test yönteminde bir ifade yazın, ardından hata altında görüntülenen ampul ' ı açın. Çağrı yeni sınıfın bir oluşturucusuna ise, menüden **tür oluştur** ' u seçin ve sınıfı kod projenize eklemek için Sihirbazı izleyin. Çağrı bir yönteme ise, IntelliSense menüsünde **Yöntem Oluştur** ' u seçin.

::: moniker range="vs-2017"
![Yöntem saplama hızlı eylem menüsünü oluştur](../test/media/ute_generatemethodstubintellisense.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Yöntem saplama hızlı eylem menüsünü oluştur](../test/media/vs-2019/basics-generate-method-tdd.png)
::: moniker-end

**Testi çalıştırmak için giriş olarak birden çok veri kümesi Al birim testleri oluşturabilirim miyim?**

**Y:** Evet. *Veri tabanlı test yöntemleri* , bir tek birim test yöntemi ile bir aralıktaki değerleri test olanak tanır. Kullanım bir `DataSource` test etmek istediğiniz değişken değerleri veri kaynağını seçin ve bu tablo belirten test yöntemini içeren özniteliği.  Yöntem gövdesinde, satır değerlerini kullanarak değişkenlere atamak `TestContext.DataRow[` *ColumnName* `]` dizin oluşturucu.

> [!NOTE]
> Yalnızca yönetilen kod için Microsoft birim testi çerçevesini kullanarak yazma yöntemleri test etmek için bu yordamları uygulayın. Farklı bir framework kullanıyorsanız, eşdeğer bir işlevselliği için framework belgelerine bakın.

Örneğin, gereksiz bir yönteme eklediğimiz varsayın `CheckingAccount` adlı sınıfı `AddIntegerHelper`. `AddIntegerHelper` iki tamsayı ekler.

İçin veri odaklı bir test oluşturmak için `AddIntegerHelper` yöntemi, ilk oluştururuz adında bir Access veritabanı *AccountsTest.accdb* ve adlı bir tablo `AddIntegerHelperData`. `AddIntegerHelperData` Tablo eklenmesi, birinci ve ikinci işlenenden belirtmek için sütunları ve beklenen sonuç belirtmek için bir sütun tanımlar. Size bir dizi satır uygun değerlerle doldurun.

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

Öznitelikli yöntem, tablodaki her satır için bir kez çalışır. **Test Gezgini** yinelemeleri başarısız yöntemi için test hatası bildirir. Test sonuçları ayrıntılar bölmesine yöntemi, her veri satırının geçer/başarısız durumu yöntemi gösterir.

Daha fazla bilgi edinin [veri temelli birim testlerini](../test/how-to-create-a-data-driven-unit-test.md).

**Birim testlerimi benim kodumu ne kadarı test görüntüleyebilir miyim?**

**Y:** Evet. Visual Studio Enterprise ' de Visual Studio kod kapsamı aracını kullanarak, birim testleriniz tarafından gerçekten test edilen kodunuzun miktarını belirleyebilirsiniz. Yerel ve yönetilen diller ve Birim Test çerçevesi tarafından çalıştırılabilir tüm birim testi çerçevelerini desteklenir.

Kod kapsamı Seçili testler ya da bir çözümdeki tüm testleri çalıştırabilirsiniz. **Kod kapsamı sonuçlarını** penceresi satır, işlevi, sınıf, ad alanı ve modül tarafından uygulanan ürünün kodu bloklarının yüzdesini görüntüler.

Bir çözümde test yöntemlerine ait kod kapsamını çalıştırmak için **test** > **Tüm testler Için kod kapsamını analiz et**' i seçin.

Kapsama sonuçlarını görünür **kod kapsamı sonuçlarını** penceresi.

![Kod kapsamı sonuçları](../test/media/ute_codecoverageresults.png)

Daha fazla bilgi edinin [kod kapsamı](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .

**Dış bağımlılıkları olan kodumu yöntemleri test miyim?**

**Y:** Evet. Visual Studio Enterprise yüklüyse, Microsoft Fakes ile yönetilen kod için birim testi çerçevelerini kullanarak yazdığınız test yöntemleri kullanılabilir.

Microsoft Fakes, dış bağımlılıklar için yedek sınıflar oluşturmak için iki yaklaşım kullanır:

1. *Saptamalar* hedef bağımlılık sınıfının üst arabirimden türetilmiş yedek sınıflar oluşturun. Hedef sınıfın ortak sanal yöntemler için saptama yöntemleri yerine kullanılabileceği.

2. *Dolgular* yerine dolgu yöntemi sanal olmayan yöntemler için bir hedef yöntem çağrısına yöneltmektir için çalışma zamanı Araçları'nı kullanın.

Her iki yaklaşım test yönteminde istediğiniz davranışını belirtmek için bağımlılık yöntemine yönelik çağrılar, oluşturulan temsilcileri kullanın.

Daha fazla bilgi edinin [birim test yöntemlerini Microsoft Fakes ile izole](../test/isolating-code-under-test-with-microsoft-fakes.md).

**S: diğer birim testi çerçevelerini birim testleri oluşturmak için kullanabilir miyim?**

**Y:** Evet, bu adımları [bulun ve diğer çatıları Yükle](../test/install-third-party-unit-test-frameworks.md). Visual Studio'yu yeniden başlatmanızın ardından, birim testleri oluşturmak için çözümü yeniden açın ve yüklü Framework burada seçin:

![Diğer yüklü birim testi çerçevesini seçin](../test/media/createunittestsdialogextensions.png)

Seçili olan altyapıda kullanarak, birim test Saplamaları oluşturulur.
