---
title: Birim testi temelleri
description: Visual Studio Test Gezgini 'nin, birim testlerinizi çalıştırmak ve sonuçlarını görüntülemek için esnek ve verimli bir yol sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/07/2019
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5efed99b9934ed91b2194b5a38c99134d6d4b5e5
ms.sourcegitcommit: 686aa3516594ab951d48b192fc60b102eedaf9b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99628038"
---
# <a name="unit-test-basics"></a>Birim testi temel bilgileri

Birim testlerini oluşturarak ve çalıştırarak kodunuzun beklenen şekilde çalışıp çalışmadığını denetleyin. Programınızın işlevselliğini tek tek *birimler* olarak test etmek için kullanabileceğiniz ayrı bir test edilebilir davranışa ayırdığından birim testi adı verilir. Visual Studio Test Gezgini, birim testlerinizi çalıştırmak ve Visual Studio 'da sonuçlarını görüntülemek için esnek ve etkili bir yol sağlar. Visual Studio, yönetilen ve yerel kod için Microsoft birim testi çerçevelerini yüklerken. Birim testleri oluşturmak, çalıştırmak ve bu testlerin sonuçlarını raporlamak için bir *birim test çerçevesi* kullanın. Kodunuzun doğru şekilde çalışmaya devam ettiğinden testte değişiklik yaptığınızda birim testlerini yeniden çalıştırın. Visual Studio Enterprise, kod değişikliklerinden etkilenen testleri algılayan ve bunları yazarken arka planda çalıştıran [Live Unit Testing](live-unit-testing-intro.md)otomatik olarak yapabilir.

Birim testi, yazılım geliştirme iş akışınızın ayrılmaz bir parçası olduğunda kodunuzun kalitesi üzerinde en büyük etkiye sahiptir. Bir işlev veya başka bir uygulama kodu bloğu yazdığınızda, standart, sınır ve hatalı giriş verileri durumlarında kodun davranışını doğrulayan ve kod tarafından yapılan açık ya da örtük varsayımları denetleyen birim testleri oluşturun. *Test odaklı geliştirme* sayesinde, kodu yazmadan önce birim testlerini oluşturursunuz, bu nedenle birim testlerini hem tasarım belgeleri hem de işlevsel özellikler olarak kullanırsınız.

Test Gezgini, test Gezgini eklenti arabirimlerini uygulayan üçüncü taraf ve açık kaynak birim test çerçeveleri de çalıştırabilir. Visual Studio Uzantı Yöneticisi ve Visual Studio Galerisi aracılığıyla bu çerçevelerin birçoğunu ekleyebilirsiniz. Daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçevelerini yüklemeyi](../test/install-third-party-unit-test-frameworks.md).

Kodunuzda test projelerini ve test yöntemlerini hızlıca oluşturabilir ya da gerektiğinde testleri el ile oluşturabilirsiniz. .NET kodunu araştırmak için IntelliTest kullandığınızda, test verileri ve birim testleri paketi oluşturabilirsiniz. Koddaki her deyimin için, bu ifadeyi yürütecek bir test girişi oluşturulur. [.NET kodu için birim testleri oluşturmayı](generate-unit-tests-for-your-code-with-intellitest.md)öğrenin.

## <a name="get-started"></a>başlarken

Doğrudan kodlamaya sahip olan birim testine giriş için aşağıdaki konulardan birine bakın:

- [İzlenecek yol: .NET kodu için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [İzlenecek yol: Test Gezgini ile test temelli geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Visual Studio 'da C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>MyBank çözümü örneği

Bu makalede, örnek olarak adlandırılan kurgusal bir uygulamanın geliştirilmesini kullanırız `MyBank` . Bu konudaki açıklamaları izlemek için gerçek koda ihtiyacınız yoktur. Test yöntemleri C# dilinde yazılır ve yönetilen kod için Microsoft birim testi çerçevesi kullanılarak sunulur. Ancak, kavramlar diğer dillere ve çerçevelere kolayca aktarılır.

::: moniker range="vs-2017"
![MyBank çözümü](../test/media/ute_mybanksolution.png)
::: moniker-end
::: moniker range=">=vs-2019"
![MyBank çözümü 2019](../test/media/vs-2019/basics-mybank-solution.png)
::: moniker-end

Uygulama için bir tasarımda ilk girişimimiz `MyBank` , tek bir hesabı ve Banka işlemlerini temsil eden bir hesap bileşeni ve bireysel Hesapları toplama ve yönetme işlevlerini temsil eden bir veritabanı bileşeni içerir.

`MyBank`İki proje içeren bir çözüm oluşturacağız:

- `Accounts`

- `BankDb`

Projeyi tasarlamada ilk denediğimiz bir `Accounts` Hesap hakkındaki temel bilgileri tutan bir sınıf, hesaptan bir hesap oluşturma ve yerinde çizim varlıkları ve bir denetim hesabını temsil eden arabirimden türetilmiş bir sınıf gibi her türlü hesabın ortak işlevlerini belirten bir arabirim içerir. Aşağıdaki kaynak dosyaları oluşturarak hesaplar projelerine başladık:

- *AccountInfo.cs* , bir hesabın temel bilgilerini tanımlar.

- *IAccount.cs* , bir hesap `IAccount` için bir hesaptan varlık yatırma ve geri çekme ve hesap bakiyesini alma yöntemleri dahil olmak üzere standart bir arabirim tanımlar.

- *CheckingAccount.cs* , `CheckingAccount` `IAccount` bir denetim hesabı için arabirimi uygulayan sınıfı içerir.

Bir denetim hesabından bir çekme gerçekleştirmesinin, geri alınan tutarın hesap bakiyesinden daha az olduğundan emin olmak için bir onay hesabı olması gerektiğini öğreniyoruz. `IAccount.Withdraw`Bu nedenle içindeki yöntemi `CheckingAccount` Bu koşulu denetleyen bir yöntemle geçersiz kıldık. Yöntemi şöyle görünebilir:

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

Artık bir kod olduğuna göre, sınama için zaman atalım.

## <a name="create-unit-test-projects-and-test-methods"></a>Birim testi projeleri ve test yöntemleri oluşturma

C# için, kodunuzun birim test projesi ve birim testi saplamalarını oluşturmak genellikle daha hızlıdır. Ya da, gereksinimlerinize bağlı olarak birim testi projesini ve Testleri el ile oluşturmayı tercih edebilirsiniz. Bir 3. taraf çerçevesi olan koddan birim testleri oluşturmak istiyorsanız şu uzantılardan birinin yüklü olması gerekir: [NUnit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371) veya [xUnit](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator). C# kullanmıyorsanız, bu bölümü atlayın ve [birim testi projesi ve birim testlerini El Ile oluşturun](#create-the-unit-test-project-and-unit-tests-manually)' a gidin.

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Birim testi projesi ve birim testi saplamaları oluştur

1. Kod Düzenleyicisi penceresinde sağ tıklayın ve sağ tıklama menüsünde [**Birim Testleri Oluştur**](create-unit-tests-menu.md) ' u seçin.

   ::: moniker range="vs-2017"
   ![Düzenleyici penceresinde bağlam menüsünü görüntüle](../test/media/createunittestsrightclick.png)

   > [!NOTE]
   > **Birim Testleri Oluştur** menü komutu yalnızca .NET Framework hedefleyen yönetilen kod için kullanılabilir (.NET Core 'u değil).
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Düzenleyici penceresinde bağlam menüsünü görüntüle](../test/media/vs-2019/basics-create-unit-tests.png)

   > [!NOTE]
   > **Birim Testleri Oluştur** menü komutu yalnızca C# kodu için kullanılabilir.
   ::: moniker-end

2. Birim testlerinizi oluşturmak için varsayılanları kabul etmek üzere **Tamam** ' a tıklayın veya birim testi projesini ve birim testlerini oluşturmak ve adlandırmak için kullanılan değerleri değiştirin. Birim testi yöntemlerine varsayılan olarak eklenen kodu seçebilirsiniz.

   ![Visual Studio 'da birim testleri oluştur iletişim kutusu](../test/media/create-unit-tests.png)

3. Birim testi saplamaları, sınıfındaki tüm yöntemler için yeni bir birim testi projesinde oluşturulur.

   ::: moniker range="vs-2017"
   ![Birim testleri oluşturuldu](../test/media/createunittestsstubs.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Birim testleri oluşturuldu](../test/media/vs-2019/basics-test-stub.png)
   ::: moniker-end

4. Şimdi, Birim testinizi anlamlı hale getirmek için [birim testi yöntemlerine nasıl kod ekleneceğini](#write-your-tests) ve kodunuzu kapsamlı test etmek için eklemek isteyebileceğiniz ek birim testlerini öğrenin.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Birim testi projesi ve birim testlerini el ile oluşturma

Bir birim testi projesi genellikle tek bir kod projesinin yapısını yansıtır. MyBank örneğinde, `AccountsTests` çözümüne ve çözümüne adlı iki birim testi projesi eklersiniz `BankDbTests` `MyBanks` . Test projesi adları rastgele olur, ancak standart bir adlandırma kuralını benimseme iyi bir fikirdir.

**Bir çözüme birim testi projesi eklemek için:**

1. **Çözüm Gezgini**, çözüme sağ tıklayın ve   >  **Yeni** **Proje** Ekle ' yi seçin.

::: moniker range="vs-2017"

2. **Yeni proje** iletişim kutusunda, **yüklü** düğümünü genişletin, test projeniz için kullanmak istediğiniz dili seçin ve ardından **Test**' i seçin.

3. Microsoft birim testi çerçevelerinden birini kullanmak için proje şablonları listesinden **birim testi projesi** ' ni seçin. Aksi takdirde, kullanmak istediğiniz birim testi çerçevesinin proje şablonunu seçin. `Accounts`Örneğimizin projeyi test etmek için projeyi adlandırın `AccountsTests` .

   > [!NOTE]
   > Tüm üçüncü taraf ve açık kaynak birim testi çerçeveleri bir Visual Studio proje şablonu sağlamaz. Proje oluşturma hakkında bilgi edinmek için Framework belgesine başvurun.

::: moniker-end

::: moniker range=">=vs-2019"

2. Kullanmak istediğiniz test çerçevesinin birim testi proje şablonunu bulmak için proje şablonu arama kutusunu kullanın.

3. Sonraki sayfada, projeyi adlandırın. `Accounts`Örneğimizin projeyi test etmek için projeyi adlandırın `AccountsTests` .

::: moniker-end

4. Birim testi projenizde, test edilen kod projesine, bizim örneğimizde hesaplar projesine bir başvuru ekleyin.

   Kod projesi başvurusunu oluşturmak için:

   1. **Çözüm Gezgini** içinde projeyi seçin.

   2. **Proje** menüsünde, **Başvuru Ekle**' yi seçin.

   3. **Başvuru Yöneticisi** iletişim kutusunda, **çözüm** düğümünü açın ve **Projeler**' i seçin. Kod projesi adını seçin ve iletişim kutusunu kapatın.

Her birim test projesi, kod projesindeki sınıfların adlarını yansıtan sınıflar içerir. Örneğimizde, `AccountsTests` proje aşağıdaki sınıfları içerir:

- `AccountInfoTests`sınıf, `AccountInfo` projedeki sınıf için birim testi yöntemlerini içerir `Accounts`

- `CheckingAccountTests` sınıfı, sınıfının birim test yöntemlerini içerir `CheckingAccount` .

## <a name="write-your-tests"></a>Testlerinizi yazma

Kullandığınız birim testi çerçevesi, Visual Studio IntelliSense, bir kod projesi için birim testleriniz için kod yazarken size kılavuzluk eder. **Test Gezgini**'nde çalıştırmak için çoğu çerçeve, birim testi yöntemlerini tanımlamak üzere belirli öznitelikler eklemenizi gerektirir. Çerçeveler ayrıca test yönteminin geçtiğini veya başarısız olduğunu göstermek için genellikle onay deyimleri veya yöntem öznitelikleri aracılığıyla bir yol sağlar. Diğer öznitelikler, sınıf başlatılmasında ve her test yönteminden sonra ve sınıf yok edildikten önce çalıştırılan her test yöntemi ve Teari yöntemleri ile, isteğe bağlı kurulum yöntemlerini belirler.

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

Test projesi oluşturduğunuzda, testler **Test Gezgini**'nde görünür. **Test Gezgini** görünür değilse, Visual Studio menüsündeki **Test** ' i seçin, **Windows**' u seçin ve ardından **Test Gezgini** ' ni seçin (veya **CTRL**  +  **E**, **T**'ye basın).

::: moniker range="vs-2017"
![Birim test Gezgini](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Birim test Gezgini](../test/media/vs-2019/basics-test-explorer.png)
::: moniker-end

Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, **Test Gezgini** sonuçları **başarısız testler**, **başarılı** testler, **Atlanan testler** ve **çalıştırma** testleri grupları halinde görüntüleyebilir. Araç çubuğunda farklı grupla seçenekleri arasından seçim yapabilirsiniz.

Ayrıca, genel düzeydeki arama kutusundaki metni eşleştirerek veya önceden tanımlanmış filtrelerden birini seçerek herhangi bir görünümdeki testleri filtreleyebilirsiniz. Herhangi bir zamanda testlerin herhangi bir seçimini çalıştırabilirsiniz. Bir test çalıştırmasının sonuçları, Gezgin penceresinin en üstündeki geçiş/başarısızlık çubuğunda hemen görünür. Test yöntemi sonucunun ayrıntıları, testi seçtiğinizde görüntülenir.

### <a name="run-and-view-tests"></a>Testleri çalıştırma ve görüntüleme

**Test Gezgini** araç çubuğu ilgilendiğiniz testleri keşfetmenize, düzenlemenize ve çalıştırmanıza yardımcı olur.

::: moniker range="vs-2017"
![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

Tüm testlerinizi çalıştırmak **için Tümünü Çalıştır** seçeneğini veya   +  çalıştırılacak testlerin bir alt kümesini seçmek için **Çalıştır** ' ı ( **CTRL**  +  **r**, **T**) seçebilirsiniz. Test ayrıntıları bölmesinde bu testin ayrıntılarını görüntülemek için bir test seçin. Seçili testin kaynak kodunu göstermek için sağ tıklama menüsünde (klavye: **F12**) **testi aç** ' ı seçin.

::: moniker range="vs-2017"

Bireysel testlerin herhangi bir sırada çalıştırılmasını önleyen bir bağımlılığı yoksa, paralel test yürütme özelliğini ![Visual Studio Test Gezgini araç çubuğundaki paralel test yürütme geçiş düğmesi ekran görüntüsü.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.

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
> Her derleme sonrasında birim testlerini çalıştırmak, Visual Studio 2017 Enterprise Edition veya Visual Studio 2019 gerektirir. Visual Studio 2019 ' de, özelliği Enterprise Edition 'ın yanı sıra Community ve Professional Edition 'da bulabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

Her yerel derlemeden sonra birim testlerinizi çalıştırmak için, test Gezgini araç çubuğunda Ayarlar simgesini açın ve **derlemeden sonra Testleri Çalıştır**' ı seçin.

::: moniker-end

### <a name="filter-and-group-the-test-list"></a>Test listesini filtreleme ve gruplandırma

Çok sayıda testiniz olduğunda, listeyi belirtilen dizeye göre filtrelemek için **Test Gezgini** arama kutusunu yazabilirsiniz. Filtre listesinden seçim yaparak filtre olaylarınızı daha fazla kısıtlayabilirsiniz.

::: moniker range="vs-2017"
![Filtre kategorilerini ara](../test/media/ute_searchfilter.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Filtre kategorilerini ara](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
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
::: moniker range=">=vs-2019"
![Yöntem saplama hızlı eylem menüsünü oluştur](../test/media/vs-2019/basics-generate-method-tdd.png)
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

**Y:** Evet. Visual Studio Enterprise ' de Visual Studio kod kapsamı aracını kullanarak, birim testleriniz tarafından gerçekten test edilen kodunuzun miktarını belirleyebilirsiniz. Birim test çerçevesi tarafından çalıştırılabilen yerel ve yönetilen diller ve tüm birim testi çerçeveleri desteklenir.

Seçili testlerde veya bir Çözümdeki tüm testlerde kod kapsamını çalıştırabilirsiniz. **Kod kapsamı sonuçları** penceresi, satır, işlev, sınıf, ad alanı ve modül tarafından uygulanan ürün kodu bloklarının yüzdesini görüntüler.

Bir çözümde test yöntemleri için kod kapsamını çalıştırmak için **Test**  >  **kodu kapsamını tüm testler için Çözümle**' yi seçin.

Kapsam sonuçları, **kod kapsamı sonuçları** penceresinde görünür.

![Kod kapsamı sonuçları](../test/media/ute_codecoverageresults.png)

[Kod kapsamı](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) hakkında daha fazla bilgi edinin.

**S: kodumdaki dış bağımlılıklara sahip yöntemleri test edebilir miyim?**

**Y:** Evet. Visual Studio Enterprise sahipseniz, Microsoft Fakes, yönetilen kod için birim test çerçeveleri kullanarak yazdığınız test yöntemleriyle birlikte kullanılabilir.

Microsoft Fakes, dış bağımlılıklar için yedek sınıflar oluşturmak üzere iki yaklaşımdan yararlanır:

1. *Saplamalar* , hedef bağımlılık sınıfının üst arabiriminden türetilmiş yedek sınıflar oluşturur. Saplama yöntemleri, hedef sınıfın ortak sanal yöntemlerinin yerine kullanılabilir.

2. *Dolgu* , sanal olmayan metotlar için bir hedef yönteme yönelik yedek dolgu metoduna yapılan çağrıları incelemek üzere çalışma zamanı izleme kullanır.

Her iki yaklaşımdaki test yönteminde istediğiniz davranışı belirtmek için bağımlılık yöntemine yapılan çağrıların oluşturulan temsilciler kullanılır.

[Birim testi yöntemlerini Microsoft Fakes ile yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)hakkında daha fazla bilgi edinin.

**S: birim testlerini oluşturmak için başka birim testi çerçeveleri kullanabilir miyim?**

Y **:** Evet, [diğer çerçeveleri bulmak ve yüklemek](../test/install-third-party-unit-test-frameworks.md)için aşağıdaki adımları izleyin. Visual Studio 'Yu yeniden başlattıktan sonra, birim testlerinizi oluşturmak için çözümünüzü yeniden açın ve ardından yüklü çerçevelerinizi buradan seçin:

![Diğer yüklü birim test çerçevesini seçin](../test/media/createunittestsdialogextensions.png)

Birim testi saplamaları, seçilen Framework kullanılarak oluşturulacaktır.
