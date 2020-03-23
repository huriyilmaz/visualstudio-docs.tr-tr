---
title: Birim test temelleri
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75846925"
---
# <a name="unit-test-basics"></a>Birim testi temel bilgileri

Birim testleri oluşturup çalıştırarak kodunuzu beklendiği gibi çalışıp çalışmadığını denetleyin. Programınızın işlevselliğini tek tek *birimler*olarak sınayabileceğiniz ayrı sınanabilir davranışlara ayırdığınız için buna birim sınama denir. Visual Studio Test Explorer, birim testlerinizi çalıştırmak ve sonuçlarını Visual Studio'da görüntülemek için esnek ve verimli bir yol sağlar. Visual Studio, yönetilen ve yerel kod için Microsoft birim sınayı çerçevelerini yükler. Birim testleri oluşturmak, çalıştırmak ve bu testlerin sonuçlarını raporlamak için bir *birim test çerçevesi* kullanın. Kodunuzu hala doğru çalıştığını test etmek için değişiklikler yaptığınızda birim testleri yeniden çalıştırın. Visual Studio Enterprise bunu, kod değişikliklerinizden etkilenen testleri algılayan ve siz yazarken arka planda çalıştıran [Canlı Birim Testi](live-unit-testing-intro.md)ile otomatik olarak yapabilir.

Birim testi, yazılım geliştirme iş akışınızın ayrılmaz bir parçası olduğunda kodunuzu kalite üzerinde en büyük etkiye sahiptir. Bir işlev veya başka bir uygulama kodu bloğu yazar yazmaz, standart, sınır ve yanlış giriş verilerine yanıt olarak kodun davranışını doğrulayan ve kod tarafından yapılan açık veya örtülü varsayımları kontrol eden birim testleri oluşturun. *Test odaklı geliştirme*ile, kodu yazmadan önce birim testlerini oluşturursunuz, böylece birim testlerini hem tasarım belgeleri hem de işlevsel belirtimler olarak kullanırsınız.

Kodunuzdan hızlı bir şekilde test projeleri ve test yöntemleri oluşturabilir veya testlergerektiğinde el ile oluşturabilirsiniz. .NET kodunuzu keşfetmek için IntelliTest'i kullandığınızda, test verileri ve bir birim testi paketi oluşturabilirsiniz. Koddaki her deyim için, bu deyimi yürütecek bir test girişi oluşturulur. Kodunuz için birim testleri nasıl [oluşturacağınızı](generate-unit-tests-for-your-code-with-intellitest.md)öğrenin.

Test Gezgini, Test Gezgini eklenti arabirimlerini uygulayan üçüncü taraf ve açık kaynak birim test çerçevelerini de çalıştırabilir. Visual Studio Extension Manager ve Visual Studio galerisi aracılığıyla bu çerçevelerin çoğunu ekleyebilirsiniz. Daha fazla bilgi için [bkz.](../test/install-third-party-unit-test-frameworks.md)

## <a name="get-started"></a>Kullanmaya başlayın

Sizi doğrudan kodlamaya götüren birim testine giriş için şu konulardan birine bakın:

- [İzlenecek yol: Yönetilen kod için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Quickstart: Test Gezgini ile test odaklı geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Visual Studio'da C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>MyBank çözüm örneği

Bu makalede, örnek olarak adlandırılan `MyBank` kurgusal bir uygulamanın geliştirilmesini kullanırız. Bu konudaki açıklamaları izlemek için gerçek koda ihtiyacınız yoktur. Test yöntemleri C# ile yazılır ve Yönetilen Kod için Microsoft Birimi Test Çerçevesi kullanılarak sunulur. Ancak, kavramlar kolayca diğer dillere ve çerçevelere aktarılır.

::: moniker range="vs-2017"
![MyBank Çözümü](../test/media/ute_mybanksolution.png)
::: moniker-end
::: moniker range=">=vs-2019"
![MyBank Çözüm 2019](../test/media/vs-2019/basics-mybank-solution.png)
::: moniker-end

`MyBank` Uygulama için ilk denememiz, tek bir hesabı ve bankayla olan hareketlerini temsil eden bir hesap bileşeni ve tek tek hesapları toplama ve yönetme işlevselliğini temsil eden bir veritabanı bileşenini içerir.

İki proje `MyBank` içeren bir çözüm oluşturuyoruz:

- `Accounts`

- `BankDb`

Projeyi `Accounts` tasarlamaya yönelik ilk denememiz, bir hesap la ilgili temel bilgileri tutmak için bir sınıf, hesaptan varlık yatırma ve çekme gibi her türlü hesabın ortak işlevselliğini belirten bir arabirim ve çek hesabını temsil eden arabirimden türetilen bir sınıf içerir. Aşağıdaki kaynak dosyaları oluşturarak Hesaplar projelerine başlıyoruz:

- *AccountInfo.cs* bir hesabın temel bilgilerini tanımlar.

- *IAccount.cs,* varlıkları `IAccount` bir hesaptan yatırma ve çekme ve hesap bakiyesini alma yöntemleri de dahil olmak üzere bir hesap için standart bir arabirim tanımlar.

- *CheckingAccount.cs,* `CheckingAccount` çek hesabı arabirimini `IAccount` uygulayan sınıfı içerir.

Deneyimlerimize dayanarak biliyoruz ki, çek hesabından para çekme işleminin yapması gereken tek şey, çekilen tutarın hesap bakiyesinden daha az olduğundan emin olmaktır. Bu nedenle, `IAccount.Withdraw` bu `CheckingAccount` durumu denetleyen bir yöntemle yöntemi geçersiz kılarız. Yöntem aşağıdaki gibi görünebilir:

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

Artık bir kodumuz olduğuna göre, test etme zamanı.

## <a name="create-unit-test-projects-and-test-methods"></a>Birim test projeleri ve test yöntemleri oluşturma

Genellikle kodunuzdan birim test projesi ve birim test koçanları oluşturmak için daha hızlıdır. Ya da gereksinimlerinize bağlı olarak birim test projesini ve testleri el ile oluşturmayı seçebilirsiniz. 3. taraf çerçevesi ile birim testleri oluşturmak istiyorsanız, bu uzantılardan birinin yüklü olması gerekir: [NUnit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371) veya [xUnit.](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator)

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Birim test projesi ve birim test koçanları oluşturma

1. Kod düzenleyicisi penceresinden sağ tıklatma menüsünden [**Birim Testleri Oluştur'u**](create-unit-tests-menu.md) sağ tıklatın ve seçin.

   ::: moniker range="vs-2017"
   ![Düzenleyici penceresinden bağlam menüsünü görüntüleyin](../test/media/createunittestsrightclick.png)

   > [!NOTE]
   > **Birim Testleri Oluştur** menüsü komutu yalnızca .NET Framework'ü hedefleyen yönetilen kod için kullanılabilir (ancak .NET Core'u hedeflemez).
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Düzenleyici penceresinden bağlam menüsünü görüntüleyin](../test/media/vs-2019/basics-create-unit-tests.png)

   > [!NOTE]
   > **Birim Testleri Oluştur** menüsü komutu yalnızca yönetilen kod için kullanılabilir.
   ::: moniker-end

2. Birim testlerinizi oluşturmak için varsayılanları kabul etmek veya birim test projesini oluşturmak ve adlarını değiştirmek için **Tamam'ı** tıklatın. Birim test yöntemlerine varsayılan olarak eklenen kodu seçebilirsiniz.

   ![Visual Studio'da Birim Testleri oluşturma iletişim kutusu](../test/media/create-unit-tests.png)

3. Ünite test koçanları, sınıftaki tüm yöntemler için yeni bir birim test projesinde oluşturulur.

   ::: moniker range="vs-2017"
   ![Birim testleri oluşturulur](../test/media/createunittestsstubs.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Birim testleri oluşturulur](../test/media/vs-2019/basics-test-stub.png)
   ::: moniker-end

4. Şimdi, birim testinizi anlamlı hale getirmek için [birim test yöntemlerine kod eklemeyi](#write-your-tests) ve kodunuzu iyice test etmek için eklemek isteyebileceğin ekstra birim testlerini öğrenmek için ilerleyin.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Birim test projesini ve birim testlerini el ile oluşturma

Birim test projesi genellikle tek bir kod projesinin yapısını yansıttır. MyBank örneğinde, `AccountsTests` `BankDbTests` çözüme `MyBanks` iki birim test projesi eklenir. Test proje adları rasgele, ancak standart bir adlandırma kuralı benimseyerek iyi bir fikirdir.

**Bir çözüme birim test projesi eklemek için:**

1. **Çözüm Gezgini'nde,** çözüme sağ tıklayın ve**Yeni** **Proje** **Ekle'yi** > seçin.

::: moniker range="vs-2017"

2. Yeni **Proje** iletişim kutusunda, **Yüklü** düğümgenişletmek, test projeniz için kullanmak istediğiniz dili seçin ve sonra **Test'i**seçin.

3. Microsoft birim test çerçevelerinden birini kullanmak için, proje şablonları listesinden **Birim Test Projesi'ni** seçin. Aksi takdirde, kullanmak istediğiniz birim test çerçevesinin proje şablonunu seçin. Örneğimizin `Accounts` projesini sınamak için projeye `AccountsTests`isim verirdiniz.

   > [!NOTE]
   > Tüm üçüncü taraf ve açık kaynak birim test çerçeveleri Visual Studio proje şablonu sağlamaz. Proje oluşturma hakkında bilgi için çerçeve belgeye başvurun.

::: moniker-end

::: moniker range=">=vs-2019"

2. Kullanmak istediğiniz test çerçevesi için birim test projesi şablonu bulmak için proje şablonu arama kutusunu kullanın.

3. Bir sonraki sayfada, projeyi adlandırın. Örneğimizin `Accounts` projesini sınamak için projeye `AccountsTests`isim verebilirsiniz.

::: moniker-end

4. Birim test projenizde, hesap lar projesine örneğimizde test altındaki kod projesine bir başvuru ekleyin.

   Kod projesine başvuru oluşturmak için:

   1. **Çözüm Gezgini'nde**projeyi seçin.

   2. **Proje** menüsünde **Referans Ekle'yi**seçin.

   3. Başvuru **Yöneticisi** iletişim **kutusunda, Çözüm** düğümlerini açın ve **Projeler'i**seçin. Kod proje adını seçin ve iletişim kutusunu kapatın.

Her birim test projesi, kod projesindeki sınıfların adlarını yansıtan sınıflar içerir. Örneğimizde, `AccountsTests` proje aşağıdaki sınıfları içerecek:

- `AccountInfoTests`sınıf projede `AccountInfo` sınıf için birim `Accounts` test yöntemlerini içerir

- `CheckingAccountTests`sınıf için `CheckingAccount` birim test yöntemlerini içerir.

## <a name="write-your-tests"></a>Testlerinizi yazın

Kullandığınız birim test çerçevesi ve Visual Studio IntelliSense, bir kod projesi için birim testleriiçin kod yazmanızda size yol gösterecektir. **Test Gezgini'nde**çalışmak için çoğu çerçeve, birim test yöntemlerini tanımlamak için belirli öznitelikler eklemenizi gerektirir. Çerçeveler, genellikle assert deyimleri veya yöntem öznitelikleri yoluyla, test yönteminin geçip geçmediğini veya başarısız olup olmadığını belirtmek için bir yol da sağlar. Diğer öznitelikler, sınıf başlatma da ve her test yönteminden önce ve her test yönteminden sonra ve sınıf yok edilmeden önce çalıştırılabilen isteğe bağlı kurulum yöntemlerini tanımlar.

AAA (Düzenle, Hareket, İddia) deseni, test altındaki bir yöntem için birim testleri yazmanın yaygın bir yoludur.

- Birim test yönteminin **Düzenle** bölümü nesneleri başharfe çözer ve test altında yönteme geçirilen verilerin değerini ayarlar.

- **Yasa** bölümü, düzenlenen parametrelerle test altındaki yöntemi çağırır.

- **Assert** bölümü, test altındaki yöntemin eyleminin beklendiği gibi hareket ettiğini doğrular.

Örneğimizin `CheckingAccount.Withdraw` yöntemini sınamak için iki test yazabiliriz: biri yöntemin standart davranışını doğrulayan, diğeri de bakiyeden daha fazlasının geri çekilmesinin başarısız olacağını doğrulayan bir test. Sınıfa `CheckingAccountTests` aşağıdaki yöntemleri ekliyoruz:

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

Microsoft birimi sınama çerçeveleri hakkında daha fazla bilgi için aşağıdaki konulardan birine bakın:

- [Birim kodunuzu test edin](unit-test-your-code.md)

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

- [Birim testlerinde MSTest çerçevesini kullanma](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

## <a name="set-timeouts-for-unit-tests"></a>Birim testleri için ayar zaman zaman ları

MSTest çerçevesini kullanıyorsanız, tek bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TimeoutAttribute> test yönteminde bir zaman alameti ayarlamak için şunları kullanabilirsiniz:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

Zaman anına izin verilen maksimum zaman dilimini ayarlamak için:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a>Test Gezgini'nde testleri çalıştırma

Test projesini oluşturduğunuzda, testler **Test Gezgini'nde**görünür. **Test Gezgini** görünmüyorsa, Visual Studio menüsünde **Test'i** seçin, **Windows'u**seçin ve ardından **Test Gezgini'ni**seçin.

::: moniker range="vs-2017"
![Ünite Test Explorer](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Ünite Test Explorer](../test/media/vs-2019/basics-test-explorer.png)
::: moniker-end

Testlerinizi çalıştırdığınızda, yazdıkça ve yeniden çalıştırdınız, **Test Gezgini** sonuçları Başarısız Testler , **Geçti Testleri,** **Atlanan Testler** ve **Çalıştırmama**testlerinden oluşan gruplar halinde görüntüleyebilir. **Failed Tests** Araç çubuğunda seçeneklere göre farklı grup seçebilirsiniz.

Ayrıca, genel düzeyde arama kutusundaki metni eşleştirerek veya önceden tanımlanmış filtrelerden birini seçerek testleri herhangi bir görünümde filtreleyebilirsiniz. İstediğiniz zaman herhangi bir test seçkisini çalıştırabilirsiniz. Bir test çalışmasının sonuçları, explorer penceresinin üst kısmındaki geçiş/başarısız çubuğunda hemen görünür. Testi seçtiğinizde test yöntemi sonucunun ayrıntıları görüntülenir.

### <a name="run-and-view-tests"></a>Testleri çalıştırma ve görüntüleme

**Test Gezgini** araç çubuğu, ilgilendiğiniz testleri keşfetmenize, düzenlemenize ve çalıştırmanıza yardımcı olur.

::: moniker range="vs-2017"
![Test Gezgini araç çubuğundan testleri çalıştırma](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini araç çubuğundan testleri çalıştırma](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

Tüm testlerinizi çalıştırmak için **Tümlerini Çalıştır'ı** seçebilir veya çalıştırmak için bir test alt kümesi seçmek için **Çalıştır'ı** seçebilirsiniz. Test ayrıntıları bölmesinde bu testin ayrıntılarını görüntülemek için bir test seçin. Seçili testin kaynak kodunu görüntülemek için sağ tıklama menüsünden (Klavye: **F12)** **Testi Aç'ı** seçin.

::: moniker range="vs-2017"

Tek tek testlerin herhangi bir sırada çalıştırılmalarını engelleyen bağımlılıkları yoksa, ![UTE&#95;parallelicon küçük&#45;](../test/media/ute_parallelicon-small.png) araç çubuğundaki geçiş düğmesini titretin. Bu, tüm testleri çalıştırmak için geçen süreyi belirgin bir şekilde azaltabilir.

::: moniker-end

::: moniker range=">=vs-2019"

Tek tek testlerin herhangi bir sırada çalıştırılmalarını engelleyen bağımlılıkları yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütmesini açın. Bu, tüm testleri çalıştırmak için geçen süreyi belirgin bir şekilde azaltabilir.

::: moniker-end

### <a name="run-tests-after-every-build"></a>Her yapıdan sonra testleri çalıştırma

::: moniker range="vs-2017"

|Düğme|Açıklama|
|-|-|
|![Yapıdan sonra çalıştırın](../test/media/ute_runafterbuild_btn.png)|Birim testlerinizi her yerel yapıdan sonra çalıştırmak için standart menüde **Test et'i** seçin ve ardından **Test Gezgini** araç çubuğunda **Yap'tan sonra Testleri Çalıştır'ı** seçin.|

> [!NOTE]
> Her yapıdan sonra birim testleri çalıştırmak visual studio 2017 Enterprise sürümü veya Visual Studio 2019 gerektirir. Visual Studio 2019'da bu özellik, Enterprise sürümüne ek olarak Topluluk ve Profesyonel sürümünde de mevcuttur.

::: moniker-end

::: moniker range=">=vs-2019"

Birim testlerinizi her yerel yapıdan sonra çalıştırmak için, Test Gezgini araç çubuğundaki ayarlar simgesini açın ve **Yapıdan Sonra Testleri Çalıştır'ı**seçin.

::: moniker-end

### <a name="filter-and-group-the-test-list"></a>Test listesini filtreleme ve gruplandırma

Çok sayıda testiniz olduğunda, listeyi belirtilen dizeye göre filtrelemek için **Test Gezgini** arama kutusuna yazabilirsiniz. Filtre listesinden seçim yaparak filtre olayınızı daha fazla kısıtlayabilirsiniz.

::: moniker range="vs-2017"
![Arama filtresi kategorileri](../test/media/ute_searchfilter.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Arama filtresi kategorileri](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

|Düğme|Açıklama|
|-|-|
|![Test Explorer grup düğmesi](../test/media/ute_groupby_btn.png)|Testlerinizi kategoriye göre gruplandırmak için **Grup By** düğmesini seçin.|

Daha fazla bilgi için test [gezgini ile birim testlerini çalıştır'a](../test/run-unit-tests-with-test-explorer.md)bakın.

## <a name="qa"></a>Soru-Cevap

**S: Birim testlerini nasıl hata ayıklamam?**

**A:** Testleriniz için hata ayıklama oturumu başlatmak için **Test Gezgini'ni** kullanın. Visual Studio hata ayıklayıcı ile kodunuzu sorunsuz bir şekilde gözden geçirmek, ünite testleri ile test altındaki proje arasında ileri geri götürmenizi ister. Hata ayıklamaya başlamak için:

1. Visual Studio düzenleyicisinde, hata ayıklamak istediğiniz bir veya daha fazla test yönteminde bir kesme noktası ayarlayın.

    > [!NOTE]
    > Sınama yöntemleri herhangi bir sırada çalıştırılabildiği için, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktaları ayarlayın.

2. **Test Gezgini'nde,** test yöntemlerini seçin ve ardından kısayol menüsünden **Hata Ayıklama Seçili Testleri'ni** seçin.

[Hata ayıklama ünitesi testleri](../debugger/debugger-feature-tour.md)hakkında daha fazla bilgi edinin.

**S: TDD kullanıyorsam, testlerimden nasıl kod oluştururum?**

**A:** Proje kodunuzda sınıflar ve yöntemler oluşturmak için Hızlı Eylemler'i kullanın. Oluşturmak istediğiniz sınıfı veya yöntemi çağıran bir test yöntemine bir deyim yazın ve ardından hatanın altında görünen ampulü açın. Arama yeni sınıfın bir oluşturucusuna ysa, menüden **türü oluştur'u** seçin ve kodu projenize sınıfı eklemek için sihirbazı izleyin. Arama bir yönteme sayılsa, IntelliSense menüsünden **yöntem üret'i** seçin.

::: moniker range="vs-2017"
![Yöntem Saplama Hızlı Eylem Menüsü Oluştur](../test/media/ute_generatemethodstubintellisense.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Yöntem Saplama Hızlı Eylem Menüsü Oluştur](../test/media/vs-2019/basics-generate-method-tdd.png)
::: moniker-end

**S: Testi çalıştırmak için giriş olarak birden çok veri kümesi alan birim testleri oluşturabilir miyim?**

**Y:** Evet. *Veri tabanlı test yöntemleri,* tek bir birim test yöntemiyle bir dizi değeri sınamamanızı sağlar. Test `DataSource` etmek istediğiniz değişken değerlerini içeren veri kaynağını ve tabloyu belirten test yöntemi için bir öznitelik kullanın.  Yöntem gövdesinde, `TestContext.DataRow[` *Sütun Adı* `]` dizinleyicisini kullanarak satır değerlerini değişkenlere atarsınız.

> [!NOTE]
> Bu yordamlar yalnızca yönetilen kod için Microsoft birim test çerçevesini kullanarak yazdığınız test yöntemleri için geçerlidir. Farklı bir çerçeve kullanıyorsanız, eşdeğer işlevsellik için çerçeve belgelerine başvurun.

Örneğin, adlı `CheckingAccount` `AddIntegerHelper`sınıfa gereksiz bir yöntem eklediğimizi varsayabiliriz. `AddIntegerHelper`iki tümsek ekler.

Yöntem için veri tabanlı bir test oluşturmak için önce *AccountsTest.accdb* adında bir Access veritabanı ve . `AddIntegerHelperData` `AddIntegerHelper` Tablo, `AddIntegerHelperData` ekin birinci ve ikinci operandlarını belirtmek için sütunları ve beklenen sonucu belirtmek için bir sütun tanımlar. Bir dizi satırı uygun değerlerle doldururuz.

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

Atfedilen yöntem, tablodaki her satır için bir kez çalışır. **Yinelemelerden** herhangi biri başarısız olursa, Test Gezgini yöntem için bir test hatası bildirir. Yöntemiçin test sonuçları ayrıntı bölmesi, her veri satırı için geçiş/başarısız durum yöntemini gösterir.

[Veri tabanlı birim testleri](../test/how-to-create-a-data-driven-unit-test.md)hakkında daha fazla bilgi edinin.

**S: Kodumun ne kadarının birim testlerim tarafından test edildiğimi görebilir miyim?**

**Y:** Evet. Visual Studio Enterprise'daki Visual Studio kod kapsama aracını kullanarak birim testleriniz tarafından gerçekten test edilen kodunuzun miktarını belirleyebilirsiniz. Yerel ve yönetilen diller ve Birim Test Çerçevesi tarafından çalıştırılabilen tüm birim test çerçeveleri desteklenir.

Bir çözümde, seçili testlerde veya tüm testlerde kod kapsamı çalıştırabilirsiniz. **Kod Kapsamı Sonuçları** penceresi, satır, işlev, sınıf, ad alanı ve modül tarafından yapılan ürün kodu bloklarının yüzdesini görüntüler.

Bir çözümde test yöntemleri için kod kapsamını çalıştırmak**için, Tüm Testler için** **Test** > Analiz Kodu Kapsamı'nı seçin.

Kapsam sonuçları **Kod Kapsamı Sonuçları** penceresinde görünür.

![Kod kapsamı sonuçları](../test/media/ute_codecoverageresults.png)

[Kod kapsamı](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) hakkında daha fazla bilgi edinin.

**S: Kodumda dış alametleri olan yöntemleri sınayabilir miyim?**

**Y:** Evet. Visual Studio Enterprise'ınız varsa, Microsoft Fakes yönetilen kod için birim test çerçeveleri kullanarak yazdığınız test yöntemleriyle kullanılabilir.

Microsoft Fakes dış bağımlılıklar için yedek sınıflar oluşturmak için iki yaklaşım kullanır:

1. *Saplamalar,* hedef bağımlılık sınıfının üst arabiriminden türetilen yedek sınıflar oluşturur. Saplama yöntemleri, hedef sınıfın genel sanal yöntemlerinin yerini alabilir.

2. *Şimler,* çağrıları sanal olmayan yöntemleriçin yerine bir şim yöntemine yönlendirmek için çalışma zamanı enstrümantasyonunu kullanır.

Her iki yaklaşımda da, sınama yönteminde istediğiniz davranışı belirtmek için bağımlılık yöntemine yapılan çağrıların oluşturulan temsilcilerini kullanırsınız.

[Microsoft Fakes ile birim test yöntemlerini yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)hakkında daha fazla bilgi edinin.

**S: Birim testleri oluşturmak için diğer birim test çerçevelerini kullanabilir miyim?**

**A:** Evet, [diğer çerçeveleri bulmak ve yüklemek](../test/install-third-party-unit-test-frameworks.md)için aşağıdaki adımları izleyin. Visual Studio'yı yeniden başlattıktan sonra, birim testlerinizi oluşturmak için çözümünüzü yeniden açın ve yüklü çerçevelerinizi buradan seçin:

![Diğer yüklü birim test çerçevelerini seçin](../test/media/createunittestsdialogextensions.png)

Birim test koçanlarınız seçili çerçeve kullanılarak oluşturulur.
