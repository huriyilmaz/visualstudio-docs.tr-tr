---
title: 'İzlenecek yol: yönetilen kod için birim testleri oluşturma ve çalıştırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.assetid: 2b018b18-b412-4e0e-b0ee-b580a2f3ba9c
caps.latest.revision: 85
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 631a180789f5fff373799b78222c25a50ab32912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657098"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-managed-code"></a>İzlenecek yol: Yönetilen Kod için Birim Testleri Oluşturma ve Çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, yönetilen kod ve Visual Studio Test Gezgini için Microsoft birim testi çerçevesini kullanarak bir dizi birim testi oluşturma, çalıştırma ve özelleştirme konusunda size kılavuzluk eder. Geliştirme kapsamında olan bir C# projesi ile çalışmaya başlayın, kodunu çalıştıran testler oluşturun, testleri çalıştırın ve sonuçları inceleyin. Ardından, proje kodunuzu değiştirebilir ve testleri yeniden çalıştırabilirsiniz.

 Bu konu aşağıdaki bölümleri içermektedir:

 [İzlenecek yolu hazırlama](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)

 [Birim testi projesi oluşturma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)

 [Test sınıfı oluşturma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)

- [Test sınıfı gereksinimleri](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)

  [İlk test yöntemini oluşturma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)

- [Test yöntemi gereksinimleri](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)

  [Test oluşturun ve çalıştırın](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)

  [Kodunuzu düzeltemedi ve testlerinizi yeniden çalıştırın](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)

  [Kodunuzu geliştirmek için birim testlerini kullanın](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)

> [!NOTE]
> Bu izlenecek yol, yönetilen kod için Microsoft birim testi çerçevesini kullanır. Test Gezgini, test Gezgini için bağdaştırıcılara sahip üçüncü taraf birim testi çerçevelerinden testleri de çalıştırabilir. Daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçevelerini yüklemeyi](../test/install-third-party-unit-test-frameworks.md)

> [!NOTE]
> Bir komut satırından testlerin nasıl çalıştırılacağı hakkında daha fazla bilgi için bkz. [Izlenecek yol: komut satırı test yardımcı programını kullanma](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867).

## <a name="prerequisites"></a>Ön koşullar

- Banka projesi. [Birim testleri oluşturmak için bkz. örnek proje](../test/sample-project-for-creating-unit-tests.md).

## <a name="prepare-the-walkthrough"></a><a name="BKMK_Prepare_the_walkthrough"></a> İzlenecek yolu hazırlama

1. Visual Studio'yu açın.

2. **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

    **Yeni Proje** iletişim kutusu görünür.

3. **Yüklü şablonlar**altında **Visual C#**' ye tıklayın.

4. Uygulama türleri listesinde **sınıf kitaplığı**' na tıklayın.

5. **Ad** kutusuna yazın `Bank` ve ardından **Tamam**' a tıklayın.

   > [!NOTE]
   > "Bank" adı zaten kullanılıyorsa, proje için başka bir ad seçin.

    Yeni banka projesi oluşturulur ve kod düzenleyicisinde açık olan Class1.cs dosyası ile Çözüm Gezgini görüntülenir.

   > [!NOTE]
   > Class1.cs dosyası kod düzenleyicisinde açık değilse, açmak için Çözüm Gezgini dosya Class1.cs dosyasına çift tıklayın.

6. [Birim testleri oluşturmak Için örnek projeden](../test/sample-project-for-creating-unit-tests.md)kaynak kodu kopyalayın.

7. [Birim testleri oluşturmak için](../test/sample-project-for-creating-unit-tests.md)Class1.cs öğesinin özgün Içeriğini örnek projeden kodla değiştirin.

8. Dosyayı BankAccount.cs olarak kaydet

9. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

   Artık Bank adlı bir projeniz var. Test etmek için kaynak kodu ve ile test etmek için araçlar içerir. **BankAccountNS**için ad alanı, aşağıdaki yordamlarda test ettiğiniz yöntemleri içeren genel sınıf **BankAccount**' u içerir.

   Bu hızlı başlangıç 'ta yöntemine odaklanıyoruz `Debit` . Para bir hesap geri tamamlandığında ve aşağıdaki kodu içerdiğinde borç yöntemi çağrılır:

```csharp
// method under test
public void Debit(double amount)
{
    if(amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    m_balance += amount;
}

```

## <a name="create-a-unit-test-project"></a><a name="BKMK_Create_a_unit_test_project"></a> Birim testi projesi oluşturma
 **Önkoşul**: yordamdaki adımları uygulayın, [yönergeyi hazırlayın](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough).

#### <a name="to-create-a-unit-test-project"></a>Birim testi projesi oluşturmak için

1. **Dosya** menüsünde, **Ekle**' yi ve ardından **Yeni proje...** öğesini seçin.

2. Yeni proje iletişim kutusunda, **yüklü**' ı genişletin, **Visual C#**' ı genişletin ve ardından **Test**' i seçin.

3. Şablon listesinden **birim testi projesi**' ni seçin.

4. **Ad** kutusuna BankTest yazın ve ardından **Tamam**' ı seçin.

     **BankTests** projesi **Banka** çözümüne eklenir.

5. **BankTests** projesinde, **Banka** çözümüne bir başvuru ekleyin.

     Çözüm Gezgini, **BankTests** projesinde **Başvurular** ' ı seçin ve bağlam menüsünden **Başvuru Ekle...** öğesini seçin.

6. Başvuru Yöneticisi iletişim kutusunda **çözüm** ' i genişletin ve ardından **Banka** öğesini kontrol edin.

## <a name="create-the-test-class"></a><a name="BKMK_Create_the_test_class"></a> Test sınıfı oluşturma
 Sınıfı doğrulamak için bir test sınıfına ihtiyacımız var `BankAccount` . Proje şablonu tarafından oluşturulan UnitTest1.cs kullanabiliriz, ancak dosya ve sınıfa daha açıklayıcı adlar vermemiz gerekir. Çözüm Gezgini dosyasında dosyayı yeniden adlandırarak bir adımda bunu yapabiliriz.

 **Sınıf dosyasını yeniden adlandırma**

 Çözüm Gezgini, BankTests projesindeki UnitTest1.cs dosyasını seçin. Bağlam menüsünden **Yeniden Adlandır**' ı seçin ve ardından dosyayı BankAccountTests.cs olarak yeniden adlandırın. Projedeki tüm başvuruları ' UnitTest1 ' kod öğesine yeniden adlandırmak isteyip istemediğinizi soran iletişim kutusunda **Evet** ' i seçin. Bu adım, sınıfının adını olarak değiştirir `BankAccountTest` .

 BankAccountTests.cs dosyası artık aşağıdaki kodu içerir:

```csharp
// unit test code
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

 **Test edilen projeye bir using ifadesini ekleyin**

 Ayrıca, tam nitelikli adlar kullanmadan test altındaki projeye çağırmamızı sağlamak için sınıfına bir using deyimleri ekleyebiliriz. Sınıf dosyasının en üstünde şunu ekleyin:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a><a name="BKMK_Test_class_requirements"></a> Test sınıfı gereksinimleri
 Bir test sınıfı için en düşük gereksinimler şunlardır:

- `[TestClass]`Özniteliği, test Gezgini 'nde çalıştırmak istediğiniz birim testi yöntemlerini içeren herhangi bir sınıf için yönetilen kod Için Microsoft birim testi çerçevesinde gereklidir.

- Test Gezgini 'nin çalıştırmasını istediğiniz her test yönteminin `[TestMethod]` özniteliği olmalıdır.

  Özniteliği olmayan bir birim testi projesinde başka sınıflarınız olabilir `[TestClass]` ve özniteliği olmayan test sınıflarında başka yöntemlere sahip olabilirsiniz `[TestMethod]` . Test yöntemlerinizin bu diğer sınıflarını ve yöntemlerini kullanabilirsiniz.

## <a name="create-the-first-test-method"></a><a name="BKMK_Create_the_first_test_method"></a> İlk test yöntemini oluşturma
 Bu yordamda, sınıfının yönteminin davranışını doğrulamak için birim testi yöntemleri yazacağız `Debit` `BankAccount` . Yöntemi yukarıda listelenmiştir.

 Test altındaki yöntemi çözümleyerek, denetlenmesi gereken en az üç davranış olduğunu tespit ettik:

1. Yöntemi bir [ArgumentOutOfRangeException] oluşturur (<!-- TODO: review code entity reference <xref:assetId:///ArgumentOutOfRangeException?qualifyHint=False&amp;autoUpgrade=True>  -->) borç tutarı bakiyesinden fazlaysa.

2. Ayrıca `ArgumentOutOfRangeException` , borç tutarının sıfırdan küçük olup olmadığını da oluşturur.

3. 1 ' de denetimler varsa.) ve 2.) karşılanması durumunda, yöntemi hesap bakiyesinden miktarı çıkartır.

   İlk testte, geçerli bir tutarın (hesap bakiyesinden daha az olan ve sıfırdan büyük olan) hesaba doğru miktarı çizdiğini doğrulayacağız.

#### <a name="to-create-a-test-method"></a>Test yöntemi oluşturmak için

1. `BankAccountNS;`BankAccountTests.cs dosyasına bir using açıklaması ekleyin.

2. Aşağıdaki yöntemi bu `BankAccountTests` sınıfa ekleyin:

   ```csharp
   // unit test code
   [TestMethod]
   public void Debit_WithValidAmount_UpdatesBalance()
   {
       // arrange
       double beginningBalance = 11.99;
       double debitAmount = 4.55;
       double expected = 7.44;
       BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

       // act
       account.Debit(debitAmount);

       // assert
       double actual = account.Balance;
       Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
   }
   ```

   Yöntemi basittir. `BankAccount`Başlangıç bakiyesiyle yeni bir nesne ayarladık ve sonra geçerli bir miktarı geri çektik. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>Son Bakiyenin beklediğimiz şeyi doğrulamak için, yönetilen kod yöntemi Için Microsoft birim testi çerçevesi kullanırız.

### <a name="test-method-requirements"></a><a name="BKMK_Test_method_requirements"></a> Test yöntemi gereksinimleri
 Bir test yönteminin aşağıdaki gereksinimleri karşılaması gerekir:

- Yöntemi özniteliğiyle birlikte tasarlanmalıdır `[TestMethod]` .

- Yöntemin dönmesi gerekir `void` .

- Metodun parametreleri olamaz.

## <a name="build-and-run-the-test"></a><a name="BKMK_Build_and_run_the_test"></a> Test oluşturun ve çalıştırın

#### <a name="to-build-and-run-the-test"></a>Testi derlemek ve çalıştırmak için

1. **Build** menüsünde **Build Solution**öğesini seçin.

     Hata yoksa UnitTestExplorer penceresi, **çalıştırma testi değil** grubunda listelenen **Debit_WithValidAmount_UpdatesBalance** görüntülenir. Test Gezgini başarılı bir derlemeden sonra görünmezse, menüden **Test** ' i seçin, ardından **Windows**' u ve ardından  **Test Gezgini**' ni seçin.

2. Testi çalıştırmak için **Tümünü Çalıştır** ' ı seçin. Test çalıştığı için pencerenin üst kısmındaki durum çubuğunu canlandırılır. Test çalıştırmasının sonunda, tüm test yöntemleri başarılı olursa çubuk yeşile dönüşür veya testlerin herhangi biri başarısız olursa kırmızı olur.

3. Bu durumda, test başarısız olur. Test yöntemi **başarısız testlere**taşınır. grubuna dağıtılmış olur. Pencerenin alt kısmındaki Ayrıntıları görüntülemek için test Gezgini ' nde yöntemi seçin.

## <a name="fix-your-code-and-rerun-your-tests"></a><a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> Kodunuzu düzeltemedi ve testlerinizi yeniden çalıştırın
 **Test sonuçlarını çözümle**

 Test sonucu, hatayı açıklayan bir ileti içerir. Bu `AreEquals` yöntemde, ileti beklendiğini (<strong>Beklenen \<*XXX*> </strong>parametre) ve gerçekten alınan ( **gerçek \<*YYY*> ** parametre) gösterir. Bakiye, başlangıç bakiyesinden ret bekliyorduk, ancak bunun yerine çekme miktarı arttı.

 Borç kodunun yeniden incelenmesi, birim testinin hata bulmasının başarılı olduğunu gösterir. Çekme miktarı, ne zaman çıkarılan Hesap bakiyesine eklenir.

 **Hatayı düzeltin**

 Hatayı düzeltmek için satırı değiştirmeniz yeterlidir

```csharp
m_balance += amount;
```

 örneklerini şununla değiştirin:

```csharp
m_balance -= amount;
```

 **Testi yeniden çalıştırın**

 Test Gezgini 'nde testi yeniden **çalıştırmak Için Tümünü Çalıştır** ' ı seçin. Kırmızı/yeşil çubuk yeşile dönüşür ve test **geçilen testler** grubuna taşınır.

## <a name="use-unit-tests-to-improve-your-code"></a><a name="BKMK_Use_unit_tests_to_improve_your_code"></a> Kodunuzu geliştirmek için birim testlerini kullanın
 Bu bölümde, yinelenen analiz, birim testi geliştirme ve yeniden düzenleme işlemlerinin üretim kodunuzu daha sağlam ve etkili hale getirmenize nasıl yardımcı olduğu açıklanır.

 **Sorunları analiz etme**

 Geçerli bir miktarın yöntemde doğru şekilde kesildiğini onaylamak için bir test yöntemi oluşturduktan sonra `Debit` , özgün analizimizde kalan taleplerine izin vereceğiz:

1. Bu yöntem, `ArgumentOutOfRangeException` Borç tutarının bakiyesinden büyük olması halinde bir oluşturur.

2. Ayrıca `ArgumentOutOfRangeException` , borç tutarının sıfırdan küçük olup olmadığını da oluşturur.

   **Test yöntemleri oluşturma**

   Bu sorunları gidermek için bir test yöntemi oluşturma denemesinde ilk denemede taahhüt görünür:

```csharp
//unit test method
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    account.Debit(debitAmount);

    // assert is handled by ExpectedException
}

```

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>Doğru özel durumun atılmak için özniteliği kullanıyoruz. Özniteliği, bir oluşturulmadığı takdirde testin başarısız olmasına neden olur `ArgumentOutOfRangeException` . Testi hem pozitif hem de negatif değerlerle çalıştırın `debitAmount` ve ardından test altındaki yöntemi geçici olarak değiştirerek <xref:System.ApplicationException> Miktar sıfırdan küçükse, testin doğru şekilde davrandığını gösterir. Geri kalan miktar bakiyesinden daha büyük olduğunda, durumu test etmek için şunlar gerekir:

1. Adlı yeni bir test yöntemi oluşturun `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` .

2. Yöntem gövdesini ' dan `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` yeni yönteme kopyalayın.

3. `debitAmount`Sayısını bakiyesinden daha büyük bir sayı olarak ayarlayın.

   **Testleri çalıştırma**

   İki yöntemi farklı değerlerle çalıştırmak `debitAmount` , testlerin kalan durumlarımızı yeterince doğru şekilde işlemesini gösterir. Tüm üç testi çalıştırmak, özgün analizimizin tüm durumlarının doğru şekilde kapsandığından emin olun.

   **Analize devam edin**

   Ancak, son iki test yöntemi de biraz rahatlığı vardır. Her iki test çalıştırıldığında, test kapsamındaki kodda hangi koşulun oluşturulduğu konusunda emin olamaz. İki koşulu birbirinden ayıran bazı yollardan yararlanabilirsiniz. Sorunu daha fazla düşünürken, hangi koşulun ihlal edildiğini bilmenin, testlerin güvenirimizi artırabileceği görünür hale gelir. Bu bilgiler, test edilen yöntemi tarafından oluşturulduğunda özel durumu işleyen üretim mekanizmasına da yardımcı olabilir. Yöntem oluşturulduğunda daha fazla bilgi oluşturma, her konuda yardımcı olur, ancak `ExpectedException` öznitelik bu bilgileri sağlayaamaz.

   Test altındaki yönteme baktığınızda, her iki koşullu deyimin da `ArgumentOutOfRangeException` bağımsız değişkenin adını parametre olarak alan bir Oluşturucu kullanıp göreceğiz:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

 MSDN Kitaplığı 'nın bir aramasından çok daha zengin bilgi raporlayan bir oluşturucunun bulunduğunu keşfettik. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` bağımsız değişkenin adını, bağımsız değişken değerini ve Kullanıcı tanımlı bir iletiyi içerir. Bu Oluşturucuyu kullanmak için test altındaki yöntemi yeniden düzenleyebilirsiniz. Daha da iyisi, hataları belirtmek için genel kullanıma açık tür üyelerini kullanabiliriz.

 **Test altındaki kodu yeniden düzenleme**

 Sınıf kapsamındaki hata iletileri için önce iki sabit tanımlamalısınız:

```csharp
// class under test
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";
```

 Sonra yöntemdeki iki koşullu deyimi değiştirirsiniz `Debit` :

```csharp
// method under test
// ...
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
// ...
```

 **Test yöntemlerini yeniden düzenleme**

 Test yönteemizdeki ilk olarak özniteliği kaldırdık `ExpectedException` . Bunun yerine, oluşturulan özel durumu yakalar ve doğru koşul ifadesinde oluşturulduğunu doğrulıyoruz. Bununla birlikte, artık kalan koşullarımızı doğrulamak için iki seçenekten daha fazla karar vermelisiniz. Örneğin `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` yönteminde, aşağıdaki eylemlerden birini ele geçirebilir:

- `ActualValue`Özel durum özelliğinin (oluşturucunun ikinci parametresi `ArgumentOutOfRangeException` ), başlangıç bakiyesinden büyük olduğunu onaylayın. Bu seçenek, `ActualValue` özel durumun özelliğini test yönteminin değişkenine karşı test etmemiz `beginningBalance` ve ayrıca, `ActualValue` öğesinin sıfırdan büyük olduğunu doğrulamanız gerekir.

- İletinin (oluşturucunun üçüncü parametresi), sınıfında tanımlanan öğesini içerdiğini onaylayın `DebitAmountExceedsBalanceMessage` `BankAccount` .

  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName>Microsoft birim testi çerçevesindeki yöntemi, ilk seçeneğin gerekli olduğu hesaplamalar olmadan ikinci seçeneği doğrulamamızı sağlar.

  Yeniden gözden geçirin ikinci bir deneme `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` şöyle görünebilir:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
    }
}
```

 **Yeniden test etme, yeniden yazma ve yeniden çözümleme**

 Test yöntemlerini farklı değerlerle yeniden test ettiğimiz zaman, aşağıdaki olgularla karşılaştık:

1. Bakiyesinden daha büyük olan bir onaylama kullanarak doğru hatayı yakalayabiliyoruz, onay `debitAmount` `Contains` geçirilir, özel durum yok sayılır ve bu nedenle test yöntemi geçirilir. Bu, istediğimiz davranıştır.

2. `debitAmount`0 ' dan küçük bir değer kullandığımızda, yanlış hata iletisi döndürüldüğünden onaylama işlemi başarısız olur. Ayrıca, `ArgumentOutOfRange` test kodu yolu altında yönteminde başka bir noktada geçici bir özel durum sunduğumuz onay başarısız olur. Bu çok iyidir.

3. `debitAmount`Değer geçerliyse (örneğin, bakiyedeki küçüktür, ancak sıfırdan büyükse, hiçbir özel durum yakalanmaz, bu nedenle onaylama hiçbir şekilde yakalanmaz. Test yöntemi geçirilir. Hiçbir özel durum atılmadığı takdirde test yönteminin başarısız olmasını istediğimiz için bu iyi değildir.

   Üçüncü olgu test yöntemindeki bir hatadır. Sorunu çözmeye çalışmak için, bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> özel durumun oluşturulduğu durumu işlemek üzere test yönteminin sonuna bir onaylama ekleyeceğiz.

   Ancak yeniden test etmek, doğru özel durum yakalanırsa testin artık başarısız olduğunu gösterir. Catch deyimleri özel durumu sıfırlar ve Yöntem yürütülmeye devam eder, yeni onaylama sırasında başarısız oluyor. Yeni sorunu çözmek için, `return` öğesinden sonra bir ifade ekleyeceğiz `StringAssert` . Yeniden test etme, sorunlarımızı düzelttiğimiz onaylar. En son sürümümüzü `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` aşağıdaki gibi görünür:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
        return;
    }
    Assert.Fail("No exception was thrown.");
}

```

 Bu son bölümde, test kodumuzu geliştirdiğimiz iş, daha sağlam ve bilgilendirici test yöntemlerine yol açmıştır. Ancak daha da önemlisi, ek analiz, test kapsamındaki projemizde daha iyi bir koda de sahiptir.
