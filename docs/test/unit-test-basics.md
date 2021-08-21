---
title: Birim testi temelleri
description: Visual Studio Test gezgini 'nin, birim testlerinizi çalıştırmak ve sonuçlarını görüntülemek için esnek ve verimli bir yol sağladığını öğrenin.
ms.date: 07/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: da403ab2aec782d65bf5699963848ce918afdf0e
ms.sourcegitcommit: e6aeefef5b659a56e6e433d155bfd269c46bceb0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2021
ms.locfileid: "122603625"
---
# <a name="unit-test-basics"></a>Birim testi temel bilgileri

Birim testlerini oluşturarak ve çalıştırarak kodunuzun beklenen şekilde çalışıp çalışmadığını denetleyin. Programınızın işlevselliğini tek tek *birimler* olarak test etmek için kullanabileceğiniz ayrı bir test edilebilir davranışa ayırdığından birim testi adı verilir. Visual Studio Test Gezgini, birim testlerinizi çalıştırmak ve Visual Studio sonuçlarını görüntülemek için esnek ve etkili bir yol sağlar. Visual Studio, yönetilen ve yerel kod için Microsoft birim testi çerçevelerini yükleyecek. Birim testleri oluşturmak, çalıştırmak ve bu testlerin sonuçlarını raporlamak için bir *birim test çerçevesi* kullanın. Kodunuzun doğru şekilde çalışmaya devam ettiğinden testte değişiklik yaptığınızda birim testlerini yeniden çalıştırın. Visual Studio Enterprise, kod değişikliklerinden etkilenen testleri algılayan ve bunları yazarken arka planda çalıştıran [Live Unit Testing](live-unit-testing-intro.md)otomatik olarak yapabilir.

Birim testi, yazılım geliştirme iş akışınızın ayrılmaz bir parçası olduğunda kodunuzun kalitesi üzerinde en büyük etkiye sahiptir. Bir işlev veya başka bir uygulama kodu bloğu yazdığınızda, standart, sınır ve hatalı giriş verileri durumlarında kodun davranışını doğrulayan ve kod tarafından yapılan açık ya da örtük varsayımları denetleyen birim testleri oluşturun. *Test odaklı geliştirme* sayesinde, kodu yazmadan önce birim testlerini oluşturursunuz, bu nedenle birim testlerini hem tasarım belgeleri hem de işlevsel özellikler olarak kullanırsınız.

Test Gezgini, test Gezgini eklenti arabirimlerini uygulayan üçüncü taraf ve açık kaynak birim test çerçeveleri de çalıştırabilir. bu çerçevelerin çoğunu Visual Studio uzantısı yöneticisi ve Visual Studio galerisi aracılığıyla ekleyebilirsiniz. Daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçevelerini yüklemeyi](../test/install-third-party-unit-test-frameworks.md).

Kodunuzda test projelerini ve test yöntemlerini hızlıca oluşturabilir ya da gerektiğinde testleri el ile oluşturabilirsiniz. .NET kodunu araştırmak için IntelliTest kullandığınızda, test verileri ve birim testleri paketi oluşturabilirsiniz. Koddaki her deyimin için, bu ifadeyi yürütecek bir test girişi oluşturulur. [.NET kodu için birim testleri oluşturmayı](generate-unit-tests-for-your-code-with-intellitest.md)öğrenin.

## <a name="get-started"></a>başlarken

Doğrudan kodlamaya sahip olan birim testine giriş için aşağıdaki konulardan birine bakın:

- [İzlenecek yol: .NET kodu için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [İzlenecek yol: Test Gezgini ile test temelli geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Visual Studio 'de C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)

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

- *AccountInfo. cs* bir hesabın temel bilgilerini tanımlar.

- *IAccount. cs* , bir hesap `IAccount` için bir hesaptan varlık depozito ve geri çekme ve hesap bakiyesini alma yöntemleri dahil olmak üzere bir hesap için standart bir arabirim tanımlar.

- *CheckingAccount. cs* , `CheckingAccount` `IAccount` bir denetim hesabı arabirimini uygulayan sınıfı içerir.

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

## <a name="create-unit-test-projects-and-test-methods-c"></a>Birim testi projeleri ve test yöntemleri oluşturma (C#)

C# için, kodunuzun birim test projesi ve birim testi saplamalarını oluşturmak genellikle daha hızlıdır. Ya da, gereksinimlerinize bağlı olarak birim testi projesini ve Testleri el ile oluşturmayı tercih edebilirsiniz. Bir 3. taraf çerçevesi olan koddan birim testleri oluşturmak istiyorsanız şu uzantılardan birinin yüklü olması gerekir: [NUnit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371) veya [xUnit](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator). C# kullanmıyorsanız, bu bölümü atlayın ve [birim testi projesi ve birim testlerini El Ile oluşturun](#create-the-unit-test-project-and-unit-tests-manually)' a gidin.

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Birim testi projesi ve birim testi saplamaları oluştur

1. Kod Düzenleyicisi penceresinde sağ tıklayın ve sağ tıklama menüsünde [**Birim Testleri Oluştur**](create-unit-tests-menu.md) ' u seçin.

   ::: moniker range="vs-2017"
   ![Düzenleyici penceresinde bağlam menüsünü görüntüle](../test/media/createunittestsrightclick.png)

   > [!NOTE]
   > **birim testleri oluştur** menü komutu yalnızca .NET Framework hedefleyen yönetilen kod için kullanılabilir (.net Core 'u değil).
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Düzenleyici penceresinde bağlam menüsünü görüntüle](../test/media/vs-2019/basics-create-unit-tests.png)

   > [!NOTE]
   > **Birim Testleri Oluştur** menü komutu yalnızca C# kodu için kullanılabilir. bu yöntemi .net Core veya .NET Standard ile kullanmak için, Visual Studio 2019 gerekir.
   ::: moniker-end

2. Birim testlerinizi oluşturmak için varsayılanları kabul etmek üzere **Tamam** ' a tıklayın veya birim testi projesini ve birim testlerini oluşturmak ve adlandırmak için kullanılan değerleri değiştirin. Birim testi yöntemlerine varsayılan olarak eklenen kodu seçebilirsiniz.

   ![Visual Studio ' de birim testleri oluştur iletişim kutusu](../test/media/create-unit-tests.png)

3. Birim testi saplamaları, sınıfındaki tüm yöntemler için yeni bir birim testi projesinde oluşturulur.

   ::: moniker range="vs-2017"
   ![Birim testleri oluşturuldu](../test/media/createunittestsstubs.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Birim testleri oluşturuldu](../test/media/vs-2019/basics-test-stub.png)
   ::: moniker-end

4. Şimdi, Birim testinizi anlamlı hale getirmek için [testlerinizi nasıl yazacağınızı](#write-your-tests) ve kodunuzu kapsamlı test etmek için eklemek isteyebileceğiniz ek birim testlerini öğrenin.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Birim testi projesi ve birim testlerini el ile oluşturma

Bir birim testi projesi genellikle tek bir kod projesinin yapısını yansıtır. MyBank örneğinde, `AccountsTests` çözümüne ve çözümüne adlı iki birim testi projesi eklersiniz `BankDbTests` `MyBanks` . Test projesi adları rastgele olur, ancak standart bir adlandırma kuralını benimseme iyi bir fikirdir.

**Bir çözüme birim testi projesi eklemek için:**

1. **Çözüm Gezgini**, çözüme sağ tıklayın ve   >  **yeni** **Project** ekle ' yi seçin.

::: moniker range="vs-2017"

2. **yeni Project** iletişim kutusunda, **yüklü** düğümünü genişletin, test projeniz için kullanmak istediğiniz dili seçin ve ardından **test**' i seçin.

3. Microsoft birim testi çerçevelerinden birini kullanmak için, proje şablonları listesinden **birim testi Project** seçin. Aksi takdirde, kullanmak istediğiniz birim testi çerçevesinin proje şablonunu seçin. `Accounts`Örneğimizin projeyi test etmek için projeyi adlandırın `AccountsTests` .

   > [!NOTE]
   > tüm üçüncü taraf ve açık kaynak birim testi çerçeveleri Visual Studio bir proje şablonu sağlamaz. Proje oluşturma hakkında bilgi edinmek için Framework belgesine başvurun.

::: moniker-end

::: moniker range=">=vs-2019"

2. Kullanmak istediğiniz test çerçevesinin birim testi proje şablonunu bulmak için proje şablonu arama kutusuna **Test** yazın. (Bu konudaki örneklerde MSTest kullanıyoruz.)

3. Sonraki sayfada, projeyi adlandırın. `Accounts`Örneğimizin projeyi test etmek için projeyi adlandırın `AccountsTests` .

::: moniker-end

4. Birim testi projenizde, test edilen kod projesine, bizim örneğimizde hesaplar projesine bir başvuru ekleyin.

   Kod projesi başvurusunu oluşturmak için:
   
   1. Çözüm Gezgini ' deki birim testi projesinde, **başvurular** veya **bağımlılıklar** düğümüne sağ tıklayın ve ardından, varsa **Project başvuru ekle** veya **başvuru ekle**' yi seçin.

   2. **Başvuru Yöneticisi** iletişim kutusunda, **çözüm** düğümünü açın ve **Projeler**' i seçin. Kod projesi adını seçin ve iletişim kutusunu kapatın.

Her birim test projesi, kod projesindeki sınıfların adlarını yansıtan sınıflar içerir. Örneğimizde, `AccountsTests` proje aşağıdaki sınıfları içerir:

- `AccountInfoTests`sınıf, `AccountInfo` projedeki sınıf için birim testi yöntemlerini içerir `Accounts`

- `CheckingAccountTests` sınıfı, sınıfının birim test yöntemlerini içerir `CheckingAccount` .

## <a name="write-your-tests"></a>Testlerinizi yazma

kullandığınız birim testi çerçevesi, ıntellisense Visual Studio, bir kod projesi için birim testleriniz için kod yazarken size kılavuzluk eder. **Test Gezgini**'nde çalıştırmak için çoğu çerçeve, birim testi yöntemlerini tanımlamak üzere belirli öznitelikler eklemenizi gerektirir. Çerçeveler ayrıca test yönteminin geçtiğini veya başarısız olduğunu göstermek için genellikle onay deyimleri veya yöntem öznitelikleri aracılığıyla bir yol sağlar. Diğer öznitelikler, sınıf başlatılmasında ve her test yönteminden sonra ve sınıf yok edildikten önce çalıştırılan her test yöntemi ve Teari yöntemleri ile, isteğe bağlı kurulum yöntemlerini belirler.

AAA (düzenleme, Işlem, onaylama) düzeni test edilen bir yöntem için birim testlerini yazmanın yaygın bir yoludur.

- Bir birim testi yönteminin **düzenleme** bölümü nesneleri başlatır ve test altındaki yönteme geçirilen verilerin değerini ayarlar.

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

Siz testlerinizi çalıştırarak, yazarak ve yeniden çalıştırdığında, **Test** Gezgini sonuçları Başarısız  Testler **,** **Başarılı** Testler, Atlanan Testler ve Testleri **Çalıştırmama gruplarında görüntüler.** Araç çubuğunda farklı gruplara göre seçenekler seçebilirsiniz.

Ayrıca, arama kutusunda genel düzeyde metinleri eşleştirerek veya önceden tanımlanmış filtrelerden birini seçerek herhangi bir görünümde testleri filtreleebilirsiniz. Testlerden herhangi bir seçimi herhangi bir zamanda çalıştırabilirsiniz. Bir test çalıştırması sonuçları, gezgin penceresinin üst kısmında yer alan geçiş/hata çubuğunda hemen görünür. Testi seçerek test yöntemi sonuçlarının ayrıntıları görüntülenir.

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

Tek tek testlerin herhangi bir sırada çalıştırılamalarını engelleyen bağımlılıkları yoksa, ile paralel test yürütmeyi ![Test Gezgini araç çubuğundaki Paralel test yürütme iki durumlu Visual Studio düğmesinin ekran görüntüsü.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğmeyi seçin. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

Tek tek testlerin herhangi bir sırada çalışmasına engel olan bağımlılıklar yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütmeyi açın. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.

::: moniker-end

### <a name="run-tests-after-every-build"></a>Her derlemeden sonra testleri çalıştırma

::: moniker range="vs-2017"

|Düğme|Description|
|-|-|
|![Derlemeden sonra çalıştır](../test/media/ute_runafterbuild_btn.png)|Birim testlerinizi her yerel derlemeden sonra çalıştırmak için standart  menüde **Test'i** ve ardından Test Gezgini araç çubuğunda Derlemeden Sonra Testleri **Çalıştır'ı** seçin.|

> [!NOTE]
> Her derlemeden sonra birim testlerinin çalıştır Visual Studio 2017 Enterprise sürümü veya 2019 Visual Studio gerekir. Bu Visual Studio 2019'da bu özellik Community ve Professional sürümüne ek olarak Enterprise kullanılabilir.

::: moniker-end

::: moniker range=">=vs-2019"

Birim testlerinizi her yerel derlemeden sonra çalıştırmak için Test Gezgini araç çubuğunda ayarlar simgesini açın ve Derlemeden Sonra **Testleri Çalıştır'ı seçin.**

::: moniker-end

### <a name="filter-and-group-the-test-list"></a>Test listesini filtreleme ve grupla

Çok sayıda teste sahip olduğunda, listeyi belirtilen dizeye göre filtrelemek için **Test** Gezgini arama kutusuna yazabilirsiniz. Filtre listesinden seçimle filtre olayınızı daha fazla kısıtabilirsiniz.

::: moniker range="vs-2017"
![Filtre kategorilerini arama](../test/media/ute_searchfilter.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Filtre kategorilerini arama](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

|Düğme|Description|
|-|-|
|![Test Gezgini grup düğmesi](../test/media/ute_groupby_btn.png)|Testlerinizi kategoriye göre gruplayabilirsiniz. **Grupla düğmesini** seçin.|

Daha fazla bilgi için [bkz. Test Gezgini ile birim testleri çalıştırma.](../test/run-unit-tests-with-test-explorer.md)

## <a name="qa"></a>Soru-Cevap

**S: Nasıl yaparım? birim testlerinde hata ayıklaması mı var?**

**A:** Test **Gezgini'ni** kullanarak testleriniz için hata ayıklama oturumu başlatın. Visual Studio hata ayıklayıcısıyla kodunuzu adımlamanız sizi birim testleri ile test altındaki proje arasında sorunsuz bir şekilde geri alır. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hata ayıklamak istediğiniz bir veya daha fazla test yönteminde bir kesme noktası ayarlayın.

    > [!NOTE]
    > Test yöntemleri herhangi bir sırayla çalıştırılana kadar, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktaları ayarlayın.

2. **Test Gezgini'nde** test yöntemlerini seçin ve ardından kısayol **menüsünden Seçili Testlerde Hata** Ayıkla'yı seçin.

Birim testlerinde hata ayıklama [hakkında daha fazla bilgi edinebilirsiniz.](../debugger/debugger-feature-tour.md)

**S: TDD kullanıyorsanız testlerimde nasıl kod oluşturulur?**

**A:** Proje kodunda sınıflar ve yöntemler oluşturmak için Hızlı Eylemler'i kullanın. Oluşturmak istediğiniz sınıfı veya yöntemi çağıran bir test yönteminde deyimi yazın, sonra hatanın altında görüntülenen ampule açın. Çağrı yeni sınıfın oluşturucusu içinse,  menüden Tür oluştur'a tıklayın ve sihirbazı takip edin ve sınıfı kod projenize eklemek için sihirbazı izleyin. Çağrı bir yönteme ise IntelliSense **menüsünden** Yöntem oluştur'a tıklayın.

::: moniker range="vs-2017"
![Yöntem Saplama Hızlı Eylem Menüsü Oluşturma](../test/media/ute_generatemethodstubintellisense.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Yöntem Saplama Hızlı Eylem Menüsü Oluşturma](../test/media/vs-2019/basics-generate-method-tdd.png)
::: moniker-end

**S: Testi çalıştırmak için giriş olarak birden çok veri kümesi alan birim testleri oluşturabilir miyim?**

**Y:** Evet. *Veri odaklı test yöntemleri,* bir değer aralığını tek bir birim test yöntemiyle test edersiniz. Test yöntemi için, test etmek istediğiniz değişken değerlerini içeren veri kaynağını `DataSource` ve tabloyu belirten bir özniteliği kullanın.  Yöntem gövdesinde, Satır değerlerini ColumnName diziner'ı kullanarak `TestContext.DataRow[` *değişkenlere* `]` atarsınız.

> [!NOTE]
> Bu yordamlar yalnızca yönetilen kod için Microsoft birim testi çerçevesini kullanarak yazmanız gereken test yöntemleri için geçerlidir. Farklı bir çerçeve kullanıyorsanız, eşdeğer işlevsellik için çerçeve belgelerine başvurun.

Örneğin, adlı sınıfına gereksiz bir yöntem `CheckingAccount` ekleyolojiyi `AddIntegerHelper` varsayalım. `AddIntegerHelper` iki tamsayı ekler.

yöntemi için veri odaklı bir test oluşturmak `AddIntegerHelper` için önce *AccountsTest.accdb* adlı bir Access veritabanı ve adlı bir tablo oluştururuz. `AddIntegerHelperData` Tablo, toplamanın birinci ve ikinci işlenenlerini belirtmek için sütunları ve `AddIntegerHelperData` beklenen sonucu belirtmek için bir sütun tanımlar. Bir dizi satırı uygun değerlerle doldururuz.

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

ile birim testi [yöntemlerini yalıtma hakkında daha fazla bilgi Microsoft Fakes.](../test/isolating-code-under-test-with-microsoft-fakes.md)

**S: Birim testleri oluşturmak için diğer birim testi çerçevelerini kullanabilir miyim?**

Y **:** Evet, [diğer çerçeveleri bulmak ve yüklemek](../test/install-third-party-unit-test-frameworks.md)için aşağıdaki adımları izleyin. Visual Studio yeniden başlattıktan sonra, birim testlerinizi oluşturmak için çözümünüzü yeniden açın ve ardından yüklü çerçevelerinizi buradan seçin:

![Diğer yüklü birim test çerçevesini seçin](../test/media/createunittestsdialogextensions.png)

Birim testi saplamaları, seçilen Framework kullanılarak oluşturulacaktır.
