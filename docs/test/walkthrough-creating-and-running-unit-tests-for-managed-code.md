---
title: C# birim test eğitimi
ms.date: 05/14/2019
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 4d5878e2c5950e45f65f8d56efdf53cd7b2e89ea
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094677"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>İzlenecek yol: Yönetilen kod için birim testleri oluşturma ve çalıştırma

Bu makalede, yönetilen kod ve Visual Studio **Test Explorer**için Microsoft birim test çerçevesini kullanarak bir dizi birim testi oluşturma, çalıştırma ve özelleştirme konusunda sizi hızlandırıyor. Geliştirilmekte olan bir C# projesiyle başlar, kodunu kullanan, testleri çalıştıran ve sonuçları inceleyen testler oluşturursunuz. Sonra proje kodunu değiştirir ve testleri yeniden çalıştırırsınız.



## <a name="create-a-project-to-test"></a>Test etmek için bir proje oluşturma

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. **Dosya** menüsünde **Yeni** > **Proje**’yi seçin.

   **Yeni Proje** iletişim kutusu görünür.

3. Visual **C#** > **.NET Core** kategorisi altında Konsol Uygulaması **(.NET Core)** proje şablonu'nu seçin.

4. Proje **Bankası'nı**adlandırın ve **ardından Tamam'ı**tıklatın.

   Banka projesi oluşturulur ve kod düzenleyicisinde *Program.cs* dosyası açık olan **Solution Explorer'da** görüntülenir.

   > [!NOTE]
   > Program.cs *Program.cs* düzenleyicide açık değilse, açmak için Solution **Solution Explorer** *Explorer'da Program.cs* dosyayı çift tıklatın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

3. C# Console App **(.NET Core)** proje şablonunu arayın ve seçin ve **ardından İleri'yi**tıklatın.

4. Proje **Bankası'nı**adlandırın ve ardından **Oluştur'u**tıklatın.

   Banka projesi oluşturulur ve kod düzenleyicisinde *Program.cs* dosyası açık olan **Solution Explorer'da** görüntülenir.

   > [!NOTE]
   > Program.cs *Program.cs* düzenleyicide açık değilse, açmak için Solution **Solution Explorer** *Explorer'da Program.cs* dosyayı çift tıklatın.

::: moniker-end

5. *Program.cs* içeriğini bir sınıfı tanımlayan aşağıdaki C# koduyla değiştirin, *BankAccount*:

   ```csharp
   using System;

   namespace BankAccountNS
   {
       /// <summary>
       /// Bank account demo class.
       /// </summary>
       public class BankAccount
       {
           private readonly string m_customerName;
           private double m_balance;

           private BankAccount() { }

           public BankAccount(string customerName, double balance)
           {
               m_customerName = customerName;
               m_balance = balance;
           }

           public string CustomerName
           {
               get { return m_customerName; }
           }

           public double Balance
           {
               get { return m_balance; }
           }

           public void Debit(double amount)
           {
               if (amount > m_balance)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount; // intentionally incorrect code
           }

           public void Credit(double amount)
           {
               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount;
           }

           public static void Main()
           {
               BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

               ba.Credit(5.77);
               ba.Debit(11.22);
               Console.WriteLine("Current balance is ${0}", ba.Balance);
           }
       }
   }
   ```

6. Dosyayı BankAccount.cs sağ *tıklatarak* ve **Çözüm Gezgini'nde** **Yeniden Adlandır'ı** seçerek yeniden adlandırın.

7. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

Artık test edebilirsiniz yöntemleri ile bir proje var. Bu makalede, testler `Debit` yöntem üzerinde duruluyor. Yöntem, `Debit` bir hesaptan para çekildiğinde çağrılır.

## <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

1. **Dosya** menüsünde**Yeni Proje** **Ekle'yi** > seçin.

   > [!TIP]
   > Ayrıca **Çözüm Gezgini'nde** çözüme sağ tıklayıp**Yeni Proje** **Ekle'yi** > seçebilirsiniz.

::: moniker range="vs-2017"

2. Yeni **Proje** iletişim kutusunda, **Yüklenilen**genişletmek, **Visual C#** genişletmek ve sonra **Test'i**seçin.

3. Şablonlar listesinden **MSTest Test Project'i (.NET Core)** seçin.

4. **Ad** kutusuna girin `BankTests`ve **sonra Tamam'ı**seçin.

   **BankTests** projesi **Banka** çözümüne eklenir.

::: moniker-end

::: moniker range=">=vs-2019"

2. C# **MSTest Test Project (.NET Core)** proje şablonunu arayın ve seçin ve sonra **İleri'yi**tıklatın.

3. Proje **BankTests**adı .

4. **Oluştur'u**tıklatın.

   **BankTests** projesi **Banka** çözümüne eklenir.

::: moniker-end

5. **BankTests** projesinde, **Banka** projesine bir başvuru ekleyin.

   **Çözüm Gezgini'nde,** BankTests projesi nin altındaki **Bağımlılıklar'ı** seçin ve ardından sağ tıklama menüsünden Başvuru **Ekle'yi** seçin. **BankTests**

6. Başvuru **Yöneticisi** iletişim kutusunda, **Projeler'i**genişletin, **Çözüm'u**seçin ve ardından **Banka** öğesini işaretleyin.

7. **Tamam'ı**seçin.

## <a name="create-the-test-class"></a>Test sınıfını oluşturma

`BankAccount` Sınıfı doğrulamak için bir test sınıfı oluşturun. Proje şablonu tarafından oluşturulan *UnitTest1.cs* dosyasını kullanabilir, ancak dosyayı ve sınıfa daha açıklayıcı adlar verebilirsiniz.

### <a name="rename-a-file-and-class"></a>Dosyayı ve sınıfı yeniden adlandırın

1. **Dosyayı**yeniden adlandırmak için Solution Explorer'da BankTests projesindeki *UnitTest1.cs* dosyayı seçin. Sağ tıklatma menüsünden Yeniden **Adlandır'ı**seçin ve ardından dosyayı *BankAccountTests.cs.*

::: moniker range="vs-2017"

2. Sınıfı yeniden adlandırmak için, açılan ve kod öğesine yapılan başvuruları yeniden adlandırmak isteyip istemediğinizi soran iletişim kutusunda **Evet'i** seçin.

::: moniker-end

::: moniker range=">=vs-2019"

2. Sınıfı yeniden adlandırmak için imleci `UnitTest1` kod düzenleyicisinde konumlandırın, sağ tıklatın ve sonra **Yeniden Adlandır'ı**seçin. **BankAccountTests** yazın ve sonra **Enter**tuşuna basın.

::: moniker-end

*BankAccountTests.cs* dosyası şimdi aşağıdaki kodu içerir:

```csharp
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

### <a name="add-a-using-statement"></a>Kullanma deyimi ekleme

Tam [ `using` ](/dotnet/csharp/language-reference/keywords/using-statement) nitelikli adlar kullanmadan test altında projeye çağrı yapabilmek için test sınıfına bir deyim ekleyin. Sınıf dosyasının en üstünde, şunları ekleyin:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Test sınıfı gereksinimleri

Bir test sınıfı için minimum gereksinimler şunlardır:

- Öznitelik, `[TestClass]` Test Gezgini'nde çalıştırmak istediğiniz birim test yöntemlerini içeren herhangi bir sınıfta gereklidir.

- Test Gezgini'ni tanımasını istediğiniz her `[TestMethod]` test yöntemiöze sahip olmalıdır.

Özniteliği olmayan `[TestClass]` bir birim test projesinde başka sınıflar da olabilir ve bu özniteliği olmayan `[TestMethod]` test sınıflarında başka yöntemler de olabilir. Bu diğer sınıfları ve yöntemleri test yöntemlerinizden arayabilirsiniz.

## <a name="create-the-first-test-method"></a>İlk test yöntemini oluşturma

Bu yordamda, `Debit` `BankAccount` sınıfın yönteminin davranışını doğrulamak için birim test yöntemleri yazarsınız.

Denetlenmesi gereken en az üç davranış vardır:

- Yöntem, borç <xref:System.ArgumentOutOfRangeException> tutarı bakiyeden büyükse bir değer atar.

- Yöntem, borç <xref:System.ArgumentOutOfRangeException> miktarı sıfırdan küçükse bir atar.

- Borç tutarı geçerliyse, yöntem borç tutarını hesap bakiyesinden çıkarır.

> [!TIP]
> Varsayılan `TestMethod1` yöntemi silebilirsiniz, çünkü bu izbarada kullanmazsınız.

### <a name="to-create-a-test-method"></a>Bir test yöntemi oluşturmak için

İlk test, geçerli bir tutarın (yani hesap bakiyesinden küçük ve sıfırdan büyük olan) hesaptan doğru tutarı çektiğini doğrular. Bu `BankAccountTests` sınıfa aşağıdaki yöntemi ekleyin:

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

Yöntem basittir: başlangıç bakiyesi `BankAccount` olan yeni bir nesne ayarlar ve geçerli bir tutarı çeker. Bitiş bakiyesinin beklendiği gibi olduğunu doğrulamak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> yöntemi kullanır.

### <a name="test-method-requirements"></a>Test yöntemi gereksinimleri

Bir test yöntemi aşağıdaki gereksinimleri karşılamalıdır:

- Bu `[TestMethod]` özellik ile dekore edilmiş.

- Geri `void`dönüyor.

- Parametreleri olamaz.

## <a name="build-and-run-the-test"></a>Testi oluşturma ve çalıştırma

1. **Yapı** menüsünde **Çözüm Oluştur'u**seçin.

2. **Test Gezgini** açık değilse, üst menü çubuğundan **Test** > **Windows** > **Test Gezgini'ni** seçerek açın.

3. Testi çalıştırmak için **Tümlerini Çalıştır'ı** seçin.

   Test çalışırken, **Test Gezgini** penceresinin üst kısmındaki durum çubuğu animasyonludur. Test çalışmasının sonunda, tüm test yöntemleri geçerse çubuk yeşile veya testlerden herhangi biri başarısız olursa kırmızıya döner.

   Bu durumda, test başarısız olur.

4. Pencerenin altındaki ayrıntıları görüntülemek için **Test Gezgini'nde** yöntemi seçin.

## <a name="fix-your-code-and-rerun-your-tests"></a>Kodunuzu düzeltin ve testlerinizi yeniden çalıştırın

Test sonucu, başarısızlığı açıklayan bir ileti içerir. Yöntem `AreEqual` için, ileti ne beklendiğini ve gerçekte ne alındı görüntüler. Bakiyenin düşmesini bekliyordunuz, ancak bunun yerine para çekme miktarı arttı.

Birim testi bir hata ortaya çıkardı: *çekilmesi*gereken zaman para çekme miktarı hesap bakiyesine *eklenir.*

### <a name="correct-the-bug"></a>Hatayı düzeltme

Hatayı düzeltmek için, *BankAccount.cs* dosyasında satırı değiştirin:

```csharp
m_balance += amount;
```

Yeni değer:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Testi yeniden çalıştırın

**Test Gezgini'nde,** testi yeniden çalıştırmak için **Tümlerini Çalıştır'ı** seçin. Kırmızı/yeşil çubuk, testin geçtiğini belirtmek için yeşile döner.

![Visual Studio 2019'da Test Explorer testi geçti](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>Kodunuzu geliştirmek için birim testlerini kullanma

Bu bölümde, yinelemeli bir çözümleme, birim test geliştirme ve yeniden düzenleme işleminin üretim kodunuzu daha sağlam ve etkili hale getirmenize nasıl yardımcı olabileceği açıklanmaktadır.

### <a name="analyze-the-issues"></a>Sorunları çözümle

`Debit` Yöntemde geçerli bir tutarın doğru şekilde düşüldünden onaylayan bir test yöntemi oluşturdunuz. Şimdi, yöntemin borç miktarı <xref:System.ArgumentOutOfRangeException> ya da varsa bir atar doğrulayın:

- bakiyeden daha büyük veya
- sıfırdan az.

### <a name="create-and-run-new-test-methods"></a>Yeni test yöntemleri oluşturma ve çalıştırma

Borç tutarı sıfırdan küçükolduğunda doğru davranışı doğrulamak için bir test yöntemi oluşturun:

```csharp
[TestMethod]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act and assert
    Assert.ThrowsException<System.ArgumentOutOfRangeException>(() => account.Debit(debitAmount));
}
```

Doğru <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> özel durum atıldığını iddia etmek için yöntemi kullanın. Bu yöntem, bir <xref:System.ArgumentOutOfRangeException> atılmadığı sürece testin başarısız olmasını neden olur. Borç miktarı sıfırdan küçük olduğunda daha <xref:System.ApplicationException> genel bir atamak için test altındaki yöntemi geçici&mdash;olarak değiştirirseniz, test doğru şekilde, yani başarısız olur.

Çekilen tutar bakiyeden büyük olduğunda durumu sınamak için aşağıdaki adımları yapın:

1. Adlı `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`yeni bir test yöntemi oluşturun.

2. Yöntem gövdesini `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` yeni yönteme kopyalayın.

3. Bakiyeden `debitAmount` daha büyük bir sayı ayarlayın.

İki testi çalıştırın ve geçtiklerini doğrulayın.

### <a name="continue-the-analysis"></a>Analize devam edin

Test edilen yöntem daha da geliştirilebilir. Geçerli uygulama ile, hangi koşul (veya)`amount > m_balance` `amount < 0`test sırasında atılan istisna neden bilmek için bir yol yoktur. Sadece yöntemde `ArgumentOutOfRangeException` bir yere bir şey atıldığını biliyoruz. Hangi durumda istisnanın atılmasına `BankAccount.Debit` neden olduğunu söyleyebilsek daha`amount > m_balance` `amount < 0`iyi olurdu, böylece yöntemimizin akıl sağlığını doğru bir şekilde kontrol ettiğine emin olabiliriz.

Yine test`BankAccount.Debit`edilen yönteme bakın ve her iki koşullu `ArgumentOutOfRangeException` deyimin de bağımsız değişkenin adını parametre olarak alan bir oluşturucu kullandığını fark edin:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Çok daha zengin bilgileri bildiren bir oluşturucu <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> vardır: bağımsız değişkenin adını, bağımsız değişken değerini ve kullanıcı tanımlı bir iletiyi içerir. Bu oluşturucuyu kullanmak için test altındaki yöntemi yeniden oluşturabilirsiniz. Daha da iyisi, hataları belirtmek için herkese açık tür üyelerini kullanabilirsiniz.

### <a name="refactor-the-code-under-test"></a>Test altındaki kodu yeniden düzenleme

İlk olarak, sınıf kapsamındahata iletileri için iki sabit tanımlayın. Bunları test altında sınıfa `BankAccount`koyun:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Ardından, yöntemdeki iki koşullu `Debit` ifadeyi değiştirin:

```csharp
if (amount > m_balance)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
}

if (amount < 0)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
}
```

### <a name="refactor-the-test-methods"></a>Test yöntemlerini yeniden düzenleme

Çağrıyı kaldırarak test yöntemlerini <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>yeniden düzenleme. Aramayı bir `try/catch` `Debit()` blokta sarın, beklenen özel durumu yakalayın ve ilişkili iletisini doğrulayın. Yöntem, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> iki dizeleri karşılaştırma kalım yeteneği sağlar.

Şimdi, `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` şuna benzer:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Yeniden test edin, yeniden yazın ve yeniden analiz edin

Test altında yöntemde bir hata olduğunu `Debit` varsayalım ve yöntem, <xref:System.ArgumentOutOfRangeException> istisna dışında doğru iletiyi boş ver'den bile çıkarmaz. Şu anda, test yöntemi bu servis talebi yle işlemiyor. `debitAmount` Değer geçerliyse (yani bakiyeden daha az ve sıfırdan büyükse), hiçbir istisna yakalanır, bu nedenle assert asla işemez. Ancak, test yöntemi geçer. Bu iyi değil, çünkü özel durum atılmazsa test yönteminin başarısız olmasını istiyorsunuz.

Bu, test yöntemindeki bir hatadır. Sorunu gidermek için, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> özel durum atılmadığı durumu işlemek için test yönteminin sonuna bir assert ekleyin.

Testi yeniden çalıştırmak, doğru özel durum yakalanırsa testin artık *başarısız* olduğunu gösterir. Blok `catch` özel durumu yakalar, ancak yöntem yürütmeye devam <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> eder ve yeni assert başarısız olur. Bu sorunu gidermek için, `return` `StringAssert` bloktan `catch` sonra bir deyim ekleyin. Testi yeniden çalıştırmak, bu sorunu giderdiğinizi doğrular. Son sürümü şuna `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` benzer:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

### <a name="conclusion"></a>Sonuç

Test kodundaki iyileştirmeler daha sağlam ve bilgilendirici test yöntemlerine yol açtı. Ama daha da önemlisi, onlar da test altında kod geliştirdi.

> [!TIP]
> Bu izne yönetilen kod için Microsoft birim test çerçevesi kullanır. **Test Gezgini,** **Test Gezgini**için bağdaştırıcıları olan üçüncü taraf birim test çerçevelerinden de testler çalıştırabilir. Daha fazla bilgi için [bkz.](../test/install-third-party-unit-test-frameworks.md)

## <a name="see-also"></a>Ayrıca bkz.

Bir komut satırından testleri çalıştırma hakkında bilgi için [VSTest.Console.exe komut satırı seçeneklerine](vstest-console-options.md)bakın.
