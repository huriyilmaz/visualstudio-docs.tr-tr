---
title: Birim testi temelleri
description: Test Gezgini Visual Studio nin birim testlerinizi çalıştırmanın ve sonuçlarını görüntülemenin esnek ve verimli bir yolunu nasıl sağladığını öğrenin.
ms.date: 07/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b2b11a06b070bee16d986635cb6f20ee940a306f
ms.sourcegitcommit: fa253b04f1f6757c62a286e541b9bef36a97d1f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2021
ms.locfileid: "114703370"
---
# <a name="unit-test-basics"></a>Birim testi temel bilgileri

Birim testleri oluşturarak ve çalıştırarak kodunuzun beklendiği gibi çalışa çalışa bir kontrol edin. Program işlevselliğini ayrı ayrı birim olarak test etmek için ayrı ayrı test edilebilir davranışlara dönüştüren birim testi olarak adlandırılan bu işleve birim testi *denir.* Visual Studio Test Gezgini, birim testlerinizi çalıştırmanın ve sonuçları tek tek görüntülemenin esnek ve verimli bir Visual Studio. Visual Studio yönetilen ve yerel kod için Microsoft birim testi çerçevelerini yüklür. Birim testleri *oluşturmak, çalıştırmak* ve bu testlerin sonuçlarını rapor etmek için birim testi çerçevesi kullanın. Kodunuzun hala düzgün çalıştığını test etmek için değişiklikler yaptığınız zaman birim testlerini yeniden çalıştırabilirsiniz. Visual Studio Enterprise kod değişikliklerinizin [etkilendiği testleri algılayan ve](live-unit-testing-intro.md)siz yazarak arka planda çalıştıran Live Unit Testing ile bunu otomatik olarak yapabilirsiniz.

Birim testi, yazılım geliştirme iş akışınız için önemli bir parça olduğunda kodunuzun kalitesi üzerinde en büyük etkiye sahiptir. Bir işlev veya başka bir uygulama kodu bloğu yazar yazmaz, standart, sınır ve yanlış giriş verileri durumlarına yanıt olarak kodun davranışını doğrular ve kod tarafından yapılan açık veya örtülü varsayımları kontrol eder. Test *güdümlü geliştirme* ile, kodu yazmadan önce birim testlerini oluşturabilirsiniz, bu nedenle birim testlerini hem tasarım belgeleri hem de işlevsel belirtimler olarak kullanırız.

Test Gezgini, Test Gezgini eklenti arabirimlerini uygulayan üçüncü taraf ve açık kaynak birim test çerçevelerini de çalıştırabilirsiniz. Visual Studio Extension Manager ve Visual Studio galerisi aracılığıyla bu çerçevelerin Visual Studio ebilirsiniz. Daha fazla bilgi için [bkz. Üçüncü taraf birim test çerçevelerini yükleme.](../test/install-third-party-unit-test-frameworks.md)

Test projelerini ve test yöntemlerini kodunuzdan hızla oluşturabilir veya ihtiyacınız olan testleri el ile oluşturabilirsiniz. .NET kodunu keşfetmek için IntelliTest'i kullanarak test verileri ve birim testi paketi oluşturabilirsiniz. Kodda yer alan her deyim için, bu deyimi yürütecek bir test girişi oluşturulur. .NET kodu [için birim testleri oluşturma hakkında bilgi bulabilirsiniz.](generate-unit-tests-for-your-code-with-intellitest.md)

## <a name="get-started"></a>başlarken

Sizi doğrudan kodlamaya alan birim testlerine giriş için şu konulardan birini ele alın:

- [Adım adım kılavuz: .NET kodu için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Adım adım kılavuz: Test Gezgini ile test güdümlü geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Visual Studio'da C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>MyBank çözüm örneği

Bu makalede örnek olarak adlı kurgusal bir uygulamanın `MyBank` geliştirilmesini kullanıyoruz. Bu konudaki açıklamaları takip etmek için gerçek koda ihtiyacınız yok. Test yöntemleri C# ile yazılır ve Yönetilen Kod için Microsoft Birim Testi Çerçevesi kullanılarak sunulmaktadır. Ancak, kavramlar kolayca diğer dillere ve çerçevelere aktarılır.

::: moniker range="vs-2017"
![MyBank Çözümü](../test/media/ute_mybanksolution.png)
::: moniker-end
::: moniker range=">=vs-2019"
![MyBank Çözümü 2019](../test/media/vs-2019/basics-mybank-solution.png)
::: moniker-end

Uygulama tasarımında ilk girişimimiz tek bir hesabı ve bankayla yaptığı işlemleri temsil eden bir hesap bileşeni ve tek tek hesapları toplama ve yönetme işlevselliğini temsil eden bir `MyBank` veritabanı bileşeni içerir.

İki proje `MyBank` içeren bir çözüm oluşturacağız:

- `Accounts`

- `BankDb`

Projeyi tasarlamaya ilişkin ilk girişimimiz, bir hesapla ilgili temel bilgileri tutmak için bir sınıf, hesaptan varlıklarını almak ve geri almak gibi her türlü hesabın ortak işlevselliğini belirten bir arabirim ve bir denetim hesabını temsil eden arabirimden türetilen bir sınıf `Accounts` içerir. Hesaplar projelerine başlamak için aşağıdaki kaynak dosyaları oluşturacağız:

- *AccountInfo.cs,* bir hesabın temel bilgilerini tanımlar.

- *IAccount.cs,* bir hesaptan varlıklarını almak ve hesap bakiyesini almak için kullanılan yöntemleri içeren standart `IAccount` bir arabirim tanımlar.

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

## <a name="create-unit-test-projects-and-test-methods"></a>Birim testi projeleri ve test yöntemleri oluşturma

C# için genellikle birim testi projesini ve birim testi saplamalarını kodunuzdan oluşturmak daha hızlıdır. Veya gereksinimlerinize bağlı olarak birim testi projesini ve testleri el ile oluşturabilirsiniz. Üçüncü taraf çerçeve ile koddan birim testleri oluşturmak için şu uzantılardan birinin yüklü olması gerekir: [NUnit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371) veya [xUnit](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator). C# kullanmadısanız bu bölümü atlayıp Birim testi projesini [ve birim testlerini el ile oluşturma bölümüne gidin.](#create-the-unit-test-project-and-unit-tests-manually)

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Birim testi projesi ve birim testi saplamaları oluşturma

1. Kod düzenleyicisi penceresinde sağ tıklayın ve sağ tıklama [**menüsünden Birim**](create-unit-tests-menu.md) Testleri Oluştur'u seçin.

   ::: moniker range="vs-2017"
   ![Düzenleyici penceresinden bağlam menüsünü görüntüleme](../test/media/createunittestsrightclick.png)

   > [!NOTE]
   > Birim **Testleri Oluştur menü** komutu yalnızca .NET Core'.NET Framework yönetilen kod için kullanılabilir.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Düzenleyici penceresinden bağlam menüsünü görüntüleme](../test/media/vs-2019/basics-create-unit-tests.png)

   > [!NOTE]
   > Birim **Testleri Oluştur menü** komutu yalnızca C# kodu için kullanılabilir.
   ::: moniker-end

2. Birim **testlerinizi** oluşturmak için varsayılan değerleri kabul etmek için Tamam'a tıklayın veya birim testi projesini ve birim testlerini oluşturmak ve ad olarak değiştirmek için kullanılan değerleri değiştirebilirsiniz. Birim testi yöntemlerine varsayılan olarak eklenen kodu seçin.

   ![Visual Studio'de Birim Testleri Oluştur iletişim Visual Studio](../test/media/create-unit-tests.png)

3. Birim testi saplamaları, sınıftaki tüm yöntemler için yeni bir birim testi projesinde oluşturulur.

   ::: moniker range="vs-2017"
   ![Birim testleri oluşturulur](../test/media/createunittestsstubs.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Birim testleri oluşturulur](../test/media/vs-2019/basics-test-stub.png)
   ::: moniker-end

4. Şimdi birim test yöntemlerine kod ek olarak birim [testini](#write-your-tests) anlamlı hale nasıl ekleycenizi ve kodunuzu kapsamlı bir şekilde test etmek için eklemek istediğiniz ek birim testlerini öğrenin.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Birim testi projesini ve birim testlerini el ile oluşturma

Birim testi projesi genellikle tek bir kod projesinin yapısını yansıtıyor. MyBank örneğinde, çözüme ve adlı iki birim testi `AccountsTests` `BankDbTests` projesi `MyBanks` eklersiniz. Test projesi adları rastgeledir, ancak standart adlandırma kuralının benimsenerek iyi bir fikirdir.

**Bir çözüme birim testi projesi eklemek için:**

1. Bu **Çözüm Gezgini,** çözüme sağ tıklayın ve Yeni **Ekle'yi Project.**  >   

::: moniker range="vs-2017"

2. Yeni **Project** iletişim kutusunda Yüklü düğümünü  genişletin, test projeniz için kullanmak istediğiniz dili seçin ve ardından Test'i **seçin.**

3. Microsoft birim testi çerçevelerinden birini kullanmak için proje şablonları **listesinden Birim Testi Project'yi** seçin. Aksi takdirde, kullanmak istediğiniz birim testi çerçevesinin proje şablonunu seçin. Örneğimizin `Accounts` projesini test etmek için projeye adını ve ardından `AccountsTests` yazın.

   > [!NOTE]
   > Tüm üçüncü taraf ve açık kaynak birim test çerçeveleri bir proje Visual Studio sağlamaz. Proje oluşturma hakkında bilgi için çerçeve belgesine bakın.

::: moniker-end

::: moniker range=">=vs-2019"

2. Kullanmak istediğiniz test çerçevesine bir birim testi proje şablonu bulmak için proje şablonu arama kutusunu kullanın.

3. Sonraki sayfada projeyi olarak ad girin. Örneğimizin `Accounts` projesini test etmek için projeyi olarak ad vesersiniz. `AccountsTests`

::: moniker-end

4. Birim testi projenize, bizim örneğimizde, test altındaki kod projesine bir başvuru ekleyin.

   Kod projesine başvuru oluşturmak için:

   1. içinde projeyi **Çözüm Gezgini.**

   2. Yeni **Project** **Ekle'yi seçin.**

   3. Başvuru Yöneticisi **iletişim kutusunda** Çözüm düğümünü açın **ve** Projeler'i **seçin.** Kod projesi adını seçin ve iletişim kutusunu kapatın.

Her birim testi projesi, kod projesinde sınıfların adlarını yansıtan sınıflar içerir. Bizim örneğimizde `AccountsTests` proje aşağıdaki sınıfları içerir:

- `AccountInfoTests` sınıfı, projesinde sınıfı için birim `AccountInfo` testi yöntemlerini `Accounts` içerir

- `CheckingAccountTests` sınıfı, sınıfının birim testi yöntemlerini `CheckingAccount` içerir.

## <a name="write-your-tests"></a>Testlerinizi yazma

IntelliSense'i kullanarak Visual Studio test çerçevesi, kod projesi için birim testlerinizi yazmanız için size yol sağlar. **Test Gezgini'nde çalıştırmak** için çoğu çerçeve, birim testi yöntemlerini tanımlamak için belirli öznitelikler eklemenizi gerektirir. Çerçeveler ayrıca test yönteminin başarılı veya başarısız olduğunu belirtmek için genellikle onay deyimleri veya yöntem öznitelikleri aracılığıyla bir yol sağlar. Diğer öznitelikler, sınıf başlatma sırasında ve her test yöntemi ve her test yöntemi sonra ve sınıfı yok olmadan önce çalıştırılma yöntemleri önce isteğe bağlı kurulum yöntemlerini tanımlama.

AAA (Düzenle, Eylem, Onay) düzeni, test altındaki bir yöntem için birim testleri yazmanın yaygın bir yolu.

- Birim  testi yönteminin Düzenle bölümü nesneleri başlatıyor ve test altındaki yöntemine geçirilen verilerin değerini ayarlar.

- Act **bölümü,** düzenlenmiş parametrelerle test altındaki yöntemini çağırır.

- **Assert bölümü,** test altındaki yöntemin eyleminin beklendiği gibi davranacağını doğrular.

Örneğimizin yöntemini test etmek için iki test yazabiliriz: biri yöntemin standart davranışını doğrular, biri de bakiyeden daha fazlasının başarısız olduğunu `CheckingAccount.Withdraw` doğrular. sınıfında `CheckingAccountTests` aşağıdaki yöntemleri ekleriz:

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

Microsoft birim testi çerçeveleri hakkında daha fazla bilgi için aşağıdaki konulardan birini ziyaret edin:

- [Kodunuzu birim testi](unit-test-your-code.md)

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

- [Birim testlerinde MSTest çerçevesini kullanma](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

## <a name="set-timeouts-for-unit-tests"></a>Birim testleri için zaman aşımı ayarlama

MSTest çerçevesini kullanıyorsanız, tek bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TimeoutAttribute> test yönteminde zaman aşımı ayarlamak için kullanabilirsiniz:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

Zaman aşımını izin verilen maksimum değere ayarlamak için:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a>Test Gezgini'nde testleri çalıştırma

Test projesini derlemek için testler Test **Gezgini'nde görünür.** **Test Gezgini görünmüyorsa,** Visual Studio menüsünde **Test'i** seçin, Windows'ı seçin ve ardından **Test** Gezgini'ni seçin **(veya Ctrl** E , T  +  **tuşlarına** **basın).**

::: moniker range="vs-2017"
![Birim Testi Gezgini](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Birim Testi Gezgini](../test/media/vs-2019/basics-test-explorer.png)
::: moniker-end

Testlerinizi çalıştırarak, yazarak ve yeniden çalıştırdığında, **Test** Gezgini sonuçları Başarısız Testler  **,** **Başarılı** Testler, Atlanan Testler ve Testleri **Çalıştırmama gruplarında görüntüler.** Araç çubuğunda farklı gruplara göre seçenekler seçebilirsiniz.

Ayrıca, arama kutusunda genel düzeyde metinleri eşleştirerek veya önceden tanımlanmış filtrelerden birini seçerek herhangi bir görünümde testleri filtreleebilirsiniz. Testlerden herhangi bir seçimi herhangi bir zamanda çalıştırabilirsiniz. Test çalıştırması sonuçları, gezgin penceresinin üst kısmında yer alan geçiş/hata çubuğunda hemen görünür. Testi seçerek test yöntemi sonuçlarının ayrıntıları görüntülenir.

### <a name="run-and-view-tests"></a>Testleri çalıştırma ve görüntüleme

**Test Gezgini araç** çubuğu ilgilendiğimiz testleri keşfetmenize, düzenlemenize ve çalıştırmanıza yardımcı olur.

::: moniker range="vs-2017"
![Test Gezgini araç çubuğundan testleri çalıştırma](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini araç çubuğundan testleri çalıştırma](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

Tüm testlerinizi **çalıştırmak için Hepsini** Çalıştır'ı seçebilir **(veya Ctrl** R , V tuşlarına basın) veya çalıştıracak testlerin bir alt kümesini  +  **(Ctrl** R , T) seçmek için   +   **Çalıştır'ı seçebilirsiniz.** Test ayrıntıları bölmesinde bu testin ayrıntılarını görüntülemek için bir test seçin. Seçilen **testin** kaynak kodunu görüntülemek için sağ tıklama menüsünden (Klavye: **F12**) Testi Aç'ı seçin.

::: moniker range="vs-2017"

Tek tek testlerin herhangi bir sırada çalışmasına engel olan bağımlılıklar yoksa, ile paralel test yürütmesini ![Test Gezgini araç çubuğundaki Paralel test yürütme iki durumlu Visual Studio düğmesinin ekran görüntüsü.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğmeyi seçin. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

Tek tek testlerin herhangi bir sırada çalışmasına engel olan bağımlılıklar yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütmeyi açın. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.

::: moniker-end

### <a name="run-tests-after-every-build"></a>Her derlemeden sonra testleri çalıştırma

::: moniker range="vs-2017"

|Düğme|Açıklama|
|-|-|
|![Derlemeden sonra çalıştır](../test/media/ute_runafterbuild_btn.png)|Birim testlerinizi her yerel derlemeden sonra çalıştırmak için standart  menüde **Test'i** ve ardından Test Gezgini araç çubuğunda Derlemeden Sonra Testleri **Çalıştır'ı** seçin.|

> [!NOTE]
> Her derlemeden sonra birim testlerinin çalıştır Visual Studio 2017 Enterprise sürümü veya 2019 Visual Studio gerekir. Bu Visual Studio 2019'da, Community ve Professional sürümlerine ek olarak Enterprise kullanılabilir.

::: moniker-end

::: moniker range=">=vs-2019"

Birim testlerinizi her yerel derlemeden sonra çalıştırmak için Test Gezgini araç çubuğunda ayarlar simgesini açın ve Derlemeden Sonra **Testleri Çalıştır'ı seçin.**

::: moniker-end

### <a name="filter-and-group-the-test-list"></a>Test listesini filtreleme ve grupla

Çok sayıda testiniz olduğunda, listeyi belirtilen dizeye göre filtrelemek için **Test** Gezgini arama kutusuna yazabilirsiniz. Filtre listesinden seçimle filtre olayınızı daha fazla kısıtabilirsiniz.

::: moniker range="vs-2017"
![Filtre kategorilerini arama](../test/media/ute_searchfilter.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Filtre kategorilerini arama](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

|Düğme|Açıklama|
|-|-|
|![Test Gezgini grup düğmesi](../test/media/ute_groupby_btn.png)|Testlerinizi kategoriye göre gruplayabilirsiniz. **Grupla düğmesini** seçin.|

Daha fazla bilgi için [bkz. Test Gezgini ile birim testleri çalıştırma.](../test/run-unit-tests-with-test-explorer.md)

## <a name="qa"></a>Soru-Cevap

**S: Nasıl yaparım? birim testlerinde hata ayıklaması mı var?**

**A:** Test **Gezgini'ni** kullanarak testleriniz için hata ayıklama oturumu başlatın. Visual Studio hata ayıklayıcısı ile kodunuzu adımlamanız, sizi birim testleri ile test altındaki proje arasında sorunsuz bir şekilde ileri ve geri alır. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hata ayıklamak istediğiniz bir veya daha fazla test yönteminde bir kesme noktası ayarlayın.

    > [!NOTE]
    > Test yöntemleri herhangi bir sırayla çalıştırılana kadar, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktaları ayarlayın.

2. **Test Gezgini'nde** test yöntemlerini seçin ve ardından kısayol **menüsünden Seçili Testlerde Hata** Ayıkla'yı seçin.

Birim testlerinde hata ayıklama [hakkında daha fazla bilgi edinebilirsiniz.](../debugger/debugger-feature-tour.md)

**S: TDD kullanıyorsanız testlerimde nasıl kod oluşturulur?**

**A:** Proje kodunda sınıflar ve yöntemler oluşturmak için Hızlı Eylemler'i kullanın. Oluşturmak istediğiniz sınıfı veya yöntemi çağıran bir test yönteminde deyimi yazın, sonra hatanın altında görünen ampul'i açın. Çağrı yeni sınıfın oluşturucusu içinse,  menüden Tür oluştur'a tıklayın ve sihirbazı takip edin ve sınıfı kod projenize girin. Çağrı bir yönteme ise IntelliSense **menüsünden** Yöntem oluştur'a tıklayın.

::: moniker range="vs-2017"
![Yöntem Saplama Hızlı Eylem Menüsü Oluşturma](../test/media/ute_generatemethodstubintellisense.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Yöntem Saplama Hızlı Eylem Menüsü Oluşturma](../test/media/vs-2019/basics-generate-method-tdd.png)
::: moniker-end

**S: Testi çalıştırmak için giriş olarak birden çok veri kümesi alan birim testleri oluşturabilir miyim?**

**Y:** Evet. *Veri odaklı test yöntemleri,* bir değer aralığını tek bir birim test yöntemiyle test edersiniz. Test `DataSource` yöntemi için, test etmek istediğiniz değişken değerlerini içeren veri kaynağını ve tabloyu belirten bir özniteliği kullanın.  Yöntem gövdesinde, Satır değerlerini ColumnName diziner'ı kullanarak `TestContext.DataRow[` *değişkenlere* `]` atarsınız.

> [!NOTE]
> Bu yordamlar yalnızca yönetilen kod için Microsoft birim testi çerçevesini kullanarak yazmanız gereken test yöntemleri için geçerlidir. Farklı bir çerçeve kullanıyorsanız, eşdeğer işlevsellik için çerçeve belgelerine başvurun.

Örneğin, adlı sınıfına gereksiz bir yöntem `CheckingAccount` `AddIntegerHelper` eklensin. `AddIntegerHelper` iki tamsayı ekler.

yöntemi için veri odaklı bir test oluşturmak `AddIntegerHelper` için önce *AccountsTest.accdb* adlı bir Access veritabanı ve adlı bir tablo oluştururuz. `AddIntegerHelperData` Tablo, toplamanın birinci ve ikinci işlenenlerini belirtmek için sütunları ve `AddIntegerHelperData` beklenen sonucu belirtmek için bir sütun tanımlar. Bir dizi satırı uygun değerlerle doldururuz.

```csharp
[DataSource(
    @"Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\Projects\MyBank\TestData\AccountsTest.accdb&quot;,
    &quot;AddIntegerHelperData"
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

Öznitelikli yöntem, tablodaki her satır için bir kez çalışır. **Yinelemelerden** herhangi biri başarısız olursa Test Gezgini yöntemi için bir test hatası raporlar. yönteminin test sonuçları ayrıntı bölmesi, her veri satırı için başarılı/başarısız durum yöntemini gösterir.

Veri odaklı birim [testleri hakkında daha fazla bilgi.](../test/how-to-create-a-data-driven-unit-test.md)

**S: Birim testlerimin kodumdan ne kadarı test olduğunu sınayabilir miyim?**

**Y:** Evet. Kod kapsamı aracını kullanarak birim testlerinizi gerçekten test Visual Studio kodunuzun miktarını Visual Studio Enterprise. Yerel ve yönetilen diller ve Birim Testi Çerçevesi tarafından çalıştırılana tüm birim testi çerçeveleri de desteklene.

Seçilen testlerde veya bir çözümde yer alan tüm testlerde kod kapsamı çalıştırabilirsiniz. Kod **Kapsamı Sonuçları** penceresi satır, işlev, sınıf, ad alanı ve modül tarafından alıştırma yapılan ürün kodu bloklarının yüzdesini görüntüler.

Bir çözümde test yöntemleri için kod kapsamı çalıştırmak için Tüm Testler için Kod Kapsamı Analizini **Test**  >  **Etme'yi seçin.**

Kapsam sonuçları, Kod **Kapsamı Sonuçları penceresinde** görüntülenir.

![Kod kapsamı sonuçları](../test/media/ute_codecoverageresults.png)

Kod kapsamı hakkında daha [fazla bilgi.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

**S: Kodumda dış bağımlılıkları olan yöntemleri test miyim?**

**Y:** Evet. Başka bir Visual Studio Enterprise Microsoft Fakes, yönetilen kod için birim testi çerçevelerini kullanarak yazarak test yöntemleriyle kullanılabilir.

Microsoft Fakes bağımlılıklar için yedek sınıflar oluşturmak için iki yaklaşım kullanır:

1. *Saplamalar,* hedef bağımlılık sınıfının üst arabiriminden türetilmiş yedek sınıflar üretir. Saplama yöntemleri, hedef sınıfın genel sanal yöntemleriyle 2.

2. *Dolgular,* çağrıları hedef yönteme yönlendiren çalışma zamanı ölçümlerini sanal olmayan yöntemler için alternatif dolgu yöntemiyle kullanır.

Her iki yaklaşımda da bağımlılık yöntemine yapılan çağrıların oluşturulan temsilcilerini kullanarak test yönteminde istediğiniz davranışı belirtirsiniz.

Microsoft Fakes [ile birim testi yöntemlerini yalıtma hakkında daha fazla bilgi Microsoft Fakes.](../test/isolating-code-under-test-with-microsoft-fakes.md)

**S: Birim testleri oluşturmak için diğer birim testi çerçevelerini kullanabilir miyim?**

**A:** Evet, diğer çerçeveleri bulmak [ve yüklemek için bu adımları izleyin.](../test/install-third-party-unit-test-frameworks.md) Yeniden başlatıldıktan Visual Studio birim testlerinizi oluşturmak için çözümlerinizi yeniden açın ve ardından burada yüklü çerçevelerinizi seçin:

![Diğer yüklü birim test çerçevesini seçin](../test/media/createunittestsdialogextensions.png)

Birim testi saplamaları, seçilen Framework kullanılarak oluşturulacaktır.
