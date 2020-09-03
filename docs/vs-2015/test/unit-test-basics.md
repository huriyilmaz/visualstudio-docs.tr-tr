---
title: Birim testi temelleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
ms.assetid: a80ba9cd-4575-483c-b957-af7ed8dc7e20
caps.latest.revision: 29
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0657fdd846c201b4f9bff4910bdd9fc271c399c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543786"
---
# <a name="unit-test-basics"></a>Birim Testi Temelleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birim testlerini oluşturarak ve çalıştırarak kodunuzun beklenen şekilde çalışıp çalışmadığını denetleyin. Programınızın işlevselliğini tek tek *birimler*olarak test etmek için kullanabileceğiniz ayrı bir test edilebilir davranışa ayırdığından birim testi adı verilir. Visual Studio Test Gezgini, birim testlerinizi çalıştırmak ve Visual Studio 'da sonuçlarını görüntülemek için esnek ve etkili bir yol sağlar. Visual Studio, yönetilen ve yerel kod için Microsoft birim testi çerçevelerini yüklerken. Birim testleri oluşturmak, çalıştırmak ve bu testlerin sonuçlarını raporlamak için bir *birim test çerçevesi* kullanın. Kodunuzun doğru şekilde çalışmaya devam ettiğinden testte değişiklik yaptığınızda birim testlerini yeniden çalıştırın. Visual Studio Enterprise kullandığınızda, her derlemeden sonra testleri otomatik olarak çalıştırabilirsiniz.

 Birim testi, yazılım geliştirme iş akışınızın ayrılmaz bir parçası olduğunda kodunuzun kalitesi üzerinde en büyük etkiye sahiptir. Bir işlev veya başka bir uygulama kodu bloğu yazdığınızda, standart, sınır ve hatalı giriş verileri durumlarında kodun davranışını doğrulayan ve kod tarafından yapılan açık ya da örtük varsayımları denetleyen birim testleri oluşturun. *Test odaklı geliştirme*sayesinde, kodu yazmadan önce birim testlerini oluşturursunuz, bu nedenle birim testlerini hem tasarım belgeleri hem de işlevsel özellikler olarak kullanırsınız.

 Kodunuzda test projelerini ve test yöntemlerini hızlıca oluşturabilir ya da gerektiğinde testleri el ile oluşturabilirsiniz. .NET kodunuzu araştırmak için IntelliTest kullandığınızda, test verileri ve birim testleri paketi oluşturabilirsiniz. Koddaki her deyimin için, bu ifadeyi yürütecek bir test girişi oluşturulur. [Kodunuz için birim testleri oluşturmayı](https://msdn.microsoft.com/library/dn823749.aspx)öğrenin.

 Test Gezgini, test Gezgini eklenti arabirimlerini uygulayan üçüncü taraf ve açık kaynak birim test çerçeveleri de çalıştırabilir. Visual Studio Uzantı Yöneticisi ve Visual Studio Galerisi aracılığıyla bu çerçevelerin birçoğunu ekleyebilirsiniz. Bkz. [üçüncü taraf birim testi çerçevelerini yüklemeyi](../test/install-third-party-unit-test-frameworks.md)

- [Hızlı başlangıçlar](#BKMK_Quick_starts)

- [MyBank çözümü örneği](#BKMK_The_MyBank_Solution_example)

- [Birim testi projeleri ve test yöntemleri oluşturma](#BKMK_Creating_the_unit_test_projects)

- [Testlerinizi yazma](#BKMK_Writing_your_tests)

- [Testleri test Gezgini 'nde Çalıştır](#BKMK_Running_tests_in_Test_Explorer)

- [Testleri çalıştırma ve görüntüleme](#BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar)

## <a name="unit-testing-overview"></a><a name="BKMK_Unit_testing_overview"></a> Birim teste genel bakış

### <a name="quick-starts"></a><a name="BKMK_Quick_starts"></a> Hızlı başlar
 Doğrudan kodlamaya sahip olan birim testine giriş için aşağıdaki konulardan birine bakın:

- [İzlenecek yol: Yönetilen Kod için Birim Testleri Oluşturma ve Çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Hızlı Başlangıç: Test Gezgini ile Test Güdümlü Geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Test Gezgini ile yerel kod birim testi](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)

## <a name="the-mybank-solution-example"></a><a name="BKMK_The_MyBank_Solution_example"></a> MyBank çözümü örneği
 Bu konu başlığında örnek olarak adlandırılan kurgusal bir uygulamanın geliştirilmesini kullanırız `MyBank` . Bu konudaki açıklamaları izlemek için gerçek koda ihtiyacınız yoktur. Test yöntemleri C# dilinde yazılır ve yönetilen kod için Microsoft birim testi çerçevesi kullanılarak sunulur, ancak kavramlar diğer dillere ve çerçevelere kolayca aktarılır.

 ![MyBank çözümü](../test/media/ute-mybanksolution.png "UTE_MyBankSolution")

 Uygulama için bir tasarımda ilk girişimimiz `MyBank` , tek bir hesabı ve Banka işlemlerini temsil eden bir hesap bileşeni ve bireysel Hesapları toplama ve yönetme işlevlerini temsil eden bir veritabanı bileşeni içerir.

 `MyBank`İki proje içeren bir çözüm oluşturacağız:

- `Accounts`

- `BankDb`

  Projeyi tasarlamada ilk denediğimiz bir `Accounts` Hesap hakkındaki temel bilgileri tutan bir sınıf, hesaptan bir sıra oluşturan ve yerinde çizim varlıkları ve bir denetim hesabını temsil eden arabirimden türetilmiş bir sınıf gibi her türlü hesabın ortak işlevlerini belirten bir arabirim içerir. Aşağıdaki kaynak dosyaları oluşturarak hesaplar projelerine başladık:

- `AccountInfo.cs` bir hesabın temel bilgilerini tanımlar.

- `IAccount.cs``IAccount`bir hesaptan varlıkları depozito ve geri çekme ve hesap bakiyesini alma yöntemleri dahil olmak üzere, bir hesap için standart bir arabirim tanımlar.

- `CheckingAccount.cs``CheckingAccount` `IAccounts` bir denetim hesabı için arabirimi uygulayan sınıfı içerir.

  Bir denetim hesabından bir çekme gerçekleştirmesinin, geri alınan tutarın hesap bakiyesinden daha az olduğundan emin olmak için bir onay hesabı olması gerektiğini öğreniyoruz. `IAccount.Withdaw`Bu nedenle içindeki yöntemi `CheckingAccount` Bu koşulu denetleyen bir yöntemle geçersiz kıldık. Yöntemi şöyle görünebilir:

```csharp

public void Withdraw(double amount)
{
    if(m_balance >= amount)
    {
        m_balance -= amount;
    }
    else
    {
        throw new ArgumentException(amount, "Withdrawal exceeds balance!")
    }
}

```

 Artık bir kod olduğuna göre, sınama için zaman atalım.

## <a name="create-unit-test-projects-and-test-methods"></a><a name="BKMK_Creating_the_unit_test_projects"></a> Birim testi projeleri ve test yöntemleri oluşturma
 Kodunuzda birim testi projesi ve birim testi saplamalarını oluşturmak genellikle daha hızlıdır. Ya da, gereksinimlerinize bağlı olarak birim testi projesini ve Testleri el ile oluşturmayı tercih edebilirsiniz.

 **Birim testi projesi ve birim testi saplamaları oluştur**

1. Kod Düzenleyicisi penceresinde, sağ tıklayın ve bağlam menüsünden **Birim Testleri Oluştur** ' u seçin.

    ![Düzenleyici penceresinde bağlam menüsünü görüntüle](../test/media/createunittestsrightclick.png "Createunittestssa")

2. Birim testlerinizi oluşturmak için varsayılanları kabul etmek üzere Tamam ' a tıklayın veya birim testi projesini ve birim testlerini oluşturmak ve adlandırmak için kullanılan değerleri değiştirin. Birim testi yöntemlerine varsayılan olarak eklenen kodu seçebilirsiniz.

    ![Sağ&#45;düzenleyicide tıklayın ve birim testleri oluştur ' u seçin.](../test/media/createunittestsdialog.png "CreateUnitTestsDialog")

3. Birim testi saplamaları, sınıfındaki tüm yöntemler için yeni bir birim testi projesinde oluşturulur.

    ![Birim testleri oluşturuldu](../test/media/createunittestsstubs.png "Createunittestssaplamaları")

4. Şimdi, Birim testinizi anlamlı hale getirmek için [birim testi yöntemlerine nasıl kod ekleneceğini](#BKMK_Writing_your_tests) ve kodunuzu kapsamlı test etmek için eklemek isteyebileceğiniz ek birim testlerini öğrenin.

   **Birim testi projenizi ve birim testlerinizi el ile oluşturun**

   Bir birim testi projesi genellikle tek bir kod projesinin yapısını yansıtır. MyBank örneğinde, `AccountsTests` çözümüne ve çözümüne adlı iki birim testi projesi eklersiniz `BankDbTests` `MyBanks` . Test projesi adları rastgele olur, ancak standart bir adlandırma kuralını benimseme iyi bir fikirdir.

   **Bir çözüme birim testi projesi eklemek için:**

5. **Dosya** menüsünde **Yeni** ' yi ve ardından **Proje** (klavye CTRL + SHIFT + N) öğesini seçin.

6. Yeni proje iletişim kutusunda, **yüklü** düğümünü genişletin, test projeniz için kullanmak istediğiniz dili seçin ve ardından **Test**' i seçin.

7. Microsoft birim testi çerçevelerinden birini kullanmak için proje şablonları listesinden **birim testi projesi** ' ni seçin. Aksi takdirde, kullanmak istediğiniz birim testi çerçevesinin proje şablonunu seçin. `Accounts`Örneğimizin projeyi test etmek için projeyi adlandırın `AccountsTests` .

   > [!WARNING]
   > Tüm üçüncü taraf ve açık kaynak birim testi çerçeveleri bir Visual Studio proje şablonu sağlamaz. Proje oluşturma hakkında bilgi edinmek için Framework belgesine başvurun.

8. Birim testi projenizde, test edilen kod projesine, bizim örneğimizde hesaplar projesine bir başvuru ekleyin.

    Kod projesi başvurusunu oluşturmak için:

   1. Çözüm Gezgini içinde projeyi seçin.

   2. **Proje** menüsünde, **Başvuru Ekle**' yi seçin.

   3. Başvuru Yöneticisi iletişim kutusunda, **çözüm** düğümünü açın ve **Projeler**' i seçin. Kod projesi adını seçin ve iletişim kutusunu kapatın.

   Her birim test projesi, kod projesindeki sınıfların adlarını yansıtan sınıflar içerir. Örneğimizde, `AccountsTests` proje aşağıdaki sınıfları içerir:

- `AccountInfoTests`sınıf, `AccountInfo` projedeki sınıf için birim testi yöntemlerini içerir `BankAccount`

- `CheckingAccountTests` sınıfı, sınıfının birim test yöntemlerini içerir `CheckingAccount` .

## <a name="write-your-tests"></a><a name="BKMK_Writing_your_tests"></a> Testlerinizi yazma
 Kullandığınız birim testi çerçevesi, Visual Studio IntelliSense, bir kod projesi için birim testleriniz için kod yazarken size kılavuzluk eder. Test Gezgini 'nde çalıştırmak için çoğu çerçeve, birim testi yöntemlerini tanımlamak üzere belirli öznitelikler eklemenizi gerektirir. Çerçeveler ayrıca test yönteminin geçtiğini veya başarısız olduğunu göstermek için genellikle onay deyimleri veya yöntem öznitelikleri aracılığıyla bir yol sağlar. Diğer öznitelikler, sınıf başlatılmasında ve her test yönteminden sonra ve sınıf yok edildikten önce çalıştırılan her test yöntemi ve Teari yöntemleri ile, isteğe bağlı kurulum yöntemlerini belirler.

 AAA (düzenleme, Işlem, onaylama) düzeni test edilen bir yöntem için birim testlerini yazmanın yaygın bir yoludur.

- Bir birim testi yönteminin **düzenleme** bölümü nesneleri başlatır ve test altındaki yönteme geçirilen verilerin değerini ayarlar.

- **Sahne** bölümü, düzenlenmiş parametrelerle test edilen yöntemi çağırır.

- **Onaylama** bölümü, test kapsamındaki yöntemin eyleminin beklendiği gibi davranacağını doğrular.

  `CheckingAccount.Withdraw`Örneğimizin yöntemini test etmek için iki test yazabiliriz: yöntemin standart davranışını doğrulayan ve bakiyesinden daha fazla olan bir çekme geldiğini doğrulayan bir tane. `CheckingAccountTests`Sınıfında, aşağıdaki yöntemleri ekleyeceğiz:

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
    double actual = account.Balance;
    // assert
    Assert.AreEqual(expected, actual);
}

[TestMethod]
[ExpectedException(typeof(ArgumentException))]
public void Withdraw_AmountMoreThanBalance_Throws()
{
    // arrange
    var account = new CheckingAccount("John Doe", 10.0);
    // act
    account.Withdraw(20.0);
    // assert is handled by the ExpectedException
}

```

 `Withdraw_ValidAmount_ChangesBalance` `Assert` Test yönteminin başarılı olup olmadığını ve `Withdraw_AmountMoreThanBalance_Throws` `ExpectedException` test yönteminin başarısını tespit etmek için özniteliğini kullandığını anlamak için açık bir ifade kullandığını unutmayın. Kapak altında, birim test çerçevesi try/catch deyimlerindeki test yöntemlerini sarmalar. Çoğu durumda, bir özel durum yakalanırsa test yöntemi başarısız olur ve özel durum yok sayılır. `ExpectedException`Öznitelik, belirtilen özel durum oluşturulursa test yönteminin geçişine neden olur.

 Microsoft birim testi çerçeveleri hakkında daha fazla bilgi için aşağıdaki konulardan birine bakın:

- [Yönetilen Kod için Microsoft Birim Testi Çerçevesi ile .NET Framework için Birim Testleri Yazma](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)

- [C++ için Microsoft Birim Testi Çerçevesi ile C/C++ için Birim Testleri Yazma](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)

## <a name="set-timeouts-for-unit-tests"></a>Birim testleri için zaman aşımlarını ayarla
 Tek bir test yönteminde zaman aşımı ayarlamak için:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

```vb

```

 Zaman aşımını izin verilen üst sınıra ayarlamak için:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a><a name="BKMK_Running_tests_in_Test_Explorer"></a> Testleri test Gezgini 'nde Çalıştır
 Test projesi oluşturduğunuzda, testler test Gezgini 'nde görünür. Test Gezgini görünür değilse, Visual Studio menüsünden **Test** ' i seçin, **Windows**' u ve ardından **Test Gezgini**' ni seçin.

 ![Birim test Gezgini](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini 'nin varsayılan görünümü sonuçları **başarısız testler**, **başarılı**testler, **Atlanan testler** ve **çalıştırma testleri**gruplarında görüntüler. Bu gruptaki tüm testleri görüntüleyen görünümü açmak için bir grup başlığı seçebilirsiniz.

 Ayrıca, genel düzeydeki arama kutusundaki metni eşleştirerek veya önceden tanımlanmış filtrelerden birini seçerek herhangi bir görünümdeki testleri filtreleyebilirsiniz. Herhangi bir zamanda testlerin herhangi bir seçimini çalıştırabilirsiniz. Bir test çalıştırmasının sonuçları, Gezgin penceresinin en üstündeki geçiş/başarısızlık çubuğunda hemen görünür. Test yöntemi sonucunun ayrıntıları, testi seçtiğinizde görüntülenir.

### <a name="run-and-view-tests"></a><a name="BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar"></a> Testleri çalıştırma ve görüntüleme
 Test Gezgini araç çubuğu ilgilendiğiniz testleri keşfetmenize, düzenlemenize ve çalıştırmanıza yardımcı olur.

 ![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/ute-toolbar.png "UTE_ToolBar")

 Tüm testlerinizi çalıştırmak için **Tümünü Çalıştır** ' ı seçebilirsiniz veya çalıştırılacak testlerin bir alt kümesini seçmek için **Çalıştır** ' ı seçin. Bir test kümesini çalıştırdıktan sonra test Gezgini penceresinin alt kısmında Test çalıştırmasının bir özeti görüntülenir. Alt bölmedeki bu testin ayrıntılarını görüntülemek için bir test seçin. Seçili testin kaynak kodunu göstermek için bağlam menüsünde **testi aç** ' ı (klavye: F12) seçin.

 Bireysel testlerin herhangi bir sırada çalıştırılmasını engelleyen bir bağımlılığı yoksa, araç çubuğunda sırasıyla ![&#95;parallelicon&#45;küçük](../test/media/ute-parallelicon-small.png "UTE_parallelicon-küçük") iki durumlu düğmesiyle paralel test yürütmeyi etkinleştirin. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.

### <a name="run-tests-after-every-build"></a><a name="BKMK_Running_tests_after_every_build"></a> Her derlemeden sonra Testleri Çalıştır

> [!WARNING]
> Her derleme sonrasında birim testlerini çalıştırma yalnızca Visual Studio Enterprise desteklenir.

|Görüntü|Description|
|-|-|
|![Derlemeden sonra Çalıştır](../test/media/ute-runafterbuild-btn.png "UTE_RunAfterBuild_btn")|Birim testlerinizi her yerel derlemeden sonra çalıştırmak için standart menüdeki **Test** ' i seçin, test Gezgini araç çubuğunda **derlemeden sonra Testleri Çalıştır** ' ı seçin.|

### <a name="filter-and-group-the-test-list"></a><a name="BKMK_Filtering_and_grouping_the_test_list"></a> Test listesini filtreleme ve gruplandırma
 Çok sayıda testiniz olduğunda, listeyi belirtilen dizeye göre filtrelemek için test Gezgini arama kutusunu yazabilirsiniz. Filtre listesinden seçim yaparak filtre olaylarınızı daha fazla kısıtlayabilirsiniz.

 ![Filtre kategorilerini ara](../test/media/ute-searchfilter.png "UTE_SearchFilter")

|Görüntü|Description|
|-|-|
|![Test Gezgini Grup düğmesi](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Testlerinizi kategoriye göre gruplandırmak için **Gruplandırma ölçütü** düğmesini seçin.|

 Daha fazla bilgi için bkz. [Test Gezgini ile birim testlerini çalıştırma](../test/run-unit-tests-with-test-explorer.md)

## <a name="qa"></a>Soru-Cevap
 **S: birim testlerinde hata ayıkla Nasıl yaparım??**

 Y **:** Testleriniz için bir hata ayıklama oturumu başlatmak için test Gezgini 'ni kullanın. Visual Studio hata ayıklayıcı ile kodunuzda adım adım geçiş, birim testleri ve test edilen proje arasında sorunsuz bir şekilde geri ve ileri doğru bir şekilde gerçekleşir. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hata ayıklamak istediğiniz bir veya daha fazla test yöntemlerinde bir kesme noktası ayarlayın.

   > [!NOTE]
   > Test yöntemleri herhangi bir sırada çalıştırılabildiğinden, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktaları ayarlayın.

2. Test Gezgini 'nde test yöntemlerini seçin ve sonra kısayol menüsünden **Seçili testlerin hatalarını ayıkla** ' yı seçin.

   [Birim testlerinde hata ayıklama](../debugger/debugging-in-visual-studio.md)hakkında daha fazla bilgi edinin.

   **S: TDD kullanıyorum, testlerimde nasıl kod oluşturabilirim?**

   Y **:** Proje kodunuzda sınıflar ve yöntemler oluşturmak için IntelliSense kullanın. Oluşturmak istediğiniz sınıfı veya yöntemi çağıran bir test yönteminde bir ifade yazın, sonra çağrı altında IntelliSense menüsünü açın. Çağrı yeni sınıfın bir oluşturucusuna ise, menüden **yeni tür oluştur** ' u seçin ve sınıfı kod projenize eklemek için Sihirbazı izleyin. Çağrı bir yönteme ise, IntelliSense menüsünden **Yeni Yöntem Oluştur** ' u seçin.

   ![Yöntem saplama IntelliSense menüsünü oluştur](../test/media/ute-generatemethodstubintellisense.png "UTE_GenerateMethodStubIntellisense")

   **S: testi çalıştırmak için girdi olarak birden çok veri kümesi alan birim testleri oluşturabilir miyim?**

   **Y:** Evet. *Veri tabanlı test yöntemleri* , tek bir birim testi yöntemiyle bir değer aralığını test etmenize olanak sağlar. Test `DataSource` yöntemi için, test etmek istediğiniz değişken değerlerini içeren veri kaynağını ve tabloyu belirten bir öznitelik kullanın.  Yöntem gövdesinde, `TestContext.DataRow[` *ColumnName* Dizin oluşturucuyu kullanarak satır değerlerini değişkenlere atarsınız `]` .

> [!NOTE]
> Bu yordamlar yalnızca, yönetilen kod için Microsoft birim testi çerçevesini kullanarak yazdığınız test yöntemleri için geçerlidir. Farklı bir Framework kullanıyorsanız, eşdeğer işlevsellik için Framework belgelerine başvurun.

 Örneğin, adlı sınıfa gereksiz bir yöntem eklediğimiz varsayın `CheckingAccount` `AddIntegerHelper` . `AddIntegerHelper` iki tamsayı ekler.

 Yöntemi için veri odaklı bir test oluşturmak için `AddIntegerHelper` , önce adlı bir erişim veritabanı `AccountsTest.accdb` ve adlı bir tablo oluşturacağız `AddIntegerHelperData` . `AddIntegerHelperData`Tablo, toplama ve beklenen sonucu belirten bir sütunun ilk ve ikinci işlenenlerini belirtmek için sütunları tanımlar. Uygun değerlere sahip bir dizi satırı doldurduk.

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

 Öznitelikli Yöntem tablodaki her satır için bir kez çalışır. Yinelemelerden herhangi biri başarısız olursa test Gezgini yöntemi için bir test hatası raporlar. Yöntemi için test sonuçları ayrıntı bölmesi, her veri satırı için geçiş/başarısız durum yöntemini gösterir.

 [Veri tabanlı birim testleri](../test/how-to-create-a-data-driven-unit-test.md)hakkında daha fazla bilgi edinin.

 **S: kodumun ne kadarının birim Testlerimin test edildiğini görüntüleyebilir miyim?**

 **Y:** Evet. Visual Studio kod kapsamı aracını kullanarak, birim testleriniz tarafından gerçekten test edilmekte olan kodunuzun miktarını belirleyebilirsiniz. Birim test çerçevesi tarafından çalıştırılabilen yerel ve yönetilen diller ve tüm birim testi çerçeveleri desteklenir.

 Seçili testlerde veya bir Çözümdeki tüm testlerde kod kapsamını çalıştırabilirsiniz. Kod kapsamı sonuçları penceresi, satır, işlev, sınıf, ad alanı ve modül tarafından uygulanan ürün kodu bloklarının yüzdesini görüntüler.

 Bir çözümde test yöntemleri için kod kapsamını çalıştırmak için, Visual Studio menüsünde **testler** ' i seçin ve ardından **kod kapsamını çözümle**' yi seçin.

 Kapsam sonuçları, kod kapsamı sonuçları penceresinde görünür.

 ![Kod kapsamı sonuçları](../test/media/ute-codecoverageresults.png "UTE_CodeCoverageResults")

 [Kod kapsamı](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) hakkında daha fazla bilgi edinin.

 **S: kodumdaki dış bağımlılıklara sahip yöntemleri nasıl test edebilirim?**

 **Y:** Evet. Visual Studio Enterprise sahipseniz, Microsoft Fakes, yönetilen kod için birim test çerçeveleri kullanarak yazdığınız test yöntemleriyle birlikte kullanılabilir.

 Microsoft Fakes, dış bağımlılıklar için alternatif sınıflar oluşturmak üzere iki yaklaşımdan yararlanır.

1. *Saplamalar* , hedef bağımlılık sınıfının üst arabiriminden türetilmiş yedek sınıflar oluşturur. Saplama yöntemleri, hedef sınıfın ortak sanal yöntemlerinin yerine kullanılabilir.

2. *Dolgu* , sanal olmayan metotlar için bir hedef yönteme yönelik yedek dolgu metoduna yapılan çağrıları incelemek üzere çalışma zamanı izleme kullanır.

   Her iki yaklaşımdaki test yönteminde istediğiniz davranışı belirtmek için bağımlılık yöntemine yapılan çağrıların oluşturulan temsilciler kullanılır.

   [Birim testi yöntemlerini Microsoft Fakes ile yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)hakkında daha fazla bilgi edinin.

   **S: birim testlerini oluşturmak için başka birim testi çerçeveleri kullanabilir miyim?**

   Y **:** Evet, [diğer çerçeveleri bulmak ve yüklemek](../test/install-third-party-unit-test-frameworks.md)için aşağıdaki adımları izleyin. Visual Studio 'Yu yeniden başlattıktan sonra, birim testlerinizi oluşturmak için çözümünüzü yeniden açın ve ardından yüklü çerçevelerinizi buradan seçin:

   ![Diğer yüklü birim test çerçevesini seçin](../test/media/createunittestsdialogextensions.png "CreateUnitTestsDialogExtensions")

   Birim testi saplamaları, seçilen Framework kullanılarak oluşturulacaktır.
