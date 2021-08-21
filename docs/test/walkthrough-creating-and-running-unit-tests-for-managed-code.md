---
title: C# birim testi öğreticisi
description: Yönetilen kod için Microsoft birim testi çerçevesini ve Test Gezgini'ni kullanarak bir dizi birim testi oluşturma, çalıştırma ve Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/17/2021
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 9b515e9d5311556b6eed8c6417f372e2cc861d94
ms.sourcegitcommit: e6aeefef5b659a56e6e433d155bfd269c46bceb0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2021
ms.locfileid: "122603573"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>İzlenecek yol: Yönetilen kod için birim testleri oluşturma ve çalıştırma

Bu makale, yönetilen kod için Microsoft birim testi çerçevesini ve Test Gezgini'ni kullanarak bir dizi birim testi oluşturma, çalıştırma ve özelleştirme Visual Studio **adım adım açıklanmıştır.** Geliştirme aşamasında olan bir C# projesiyle başlayacak, kodunun alıştırmasını yapılacak testler oluşturacak, testleri çalıştıracak ve sonuçları inceleyebilirsiniz. Ardından proje kodunu değiştirir ve testleri yeniden çalıştırabilirsiniz. Bu adımları gerçekleştirmeden önce bu görevlere kavramsal bir genel bakışa sahip olmak için [bkz. Birim testi temelleri.](../test/unit-test-basics.md)

## <a name="create-a-project-to-test"></a>Test etmek için proje oluşturma

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. Dosya menüsünde **Yeni** **dosya'Project.** > 

   **Yeni Proje** iletişim kutusu görünür.

3. Visual **C#** > **.NET Core kategorisi** altında Konsol Uygulaması **(.NET Core) proje** şablonunu seçin.

4. Projeye Bank adını **ve** ardından Tamam'a **tıklayın.**

   Banka projesi, *Program.cs* **Çözüm Gezgini** kod düzenleyicisinde açık şekilde oluşturulur ve bu dosyada görüntülenir.

   > [!NOTE]
   > Düzenleyicide *Program.cs* açık yoksa, *program.cs dosyasındaki Program.cs* **dosyasına Çözüm Gezgini** çift tıklayın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

3. .NET Core için C# **Konsol Uygulaması** proje şablonunu arayın ve seçin ve ardından Sonraki 'ye **tıklayın.**

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi **.NET Core platformlar arası geliştirme iş yükünü** seçin.

4. Projeye Bank adını **ve** ardından Sonraki'ye **tıklayın.**

   Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   Banka projesi, *Program.cs* **Çözüm Gezgini** kod düzenleyicisinde açık şekilde oluşturulur ve bu dosyada görüntülenir.

   > [!NOTE]
   > Düzenleyicide *Program.cs* açık yoksa, *program.cs dosyasındaki Program.cs* **dosyasına Çözüm Gezgini** çift tıklayın.

::: moniker-end

5. *Program.cs içeriğini* BankAccount sınıfını tanımlayan aşağıdaki C# *koduyla değiştirin:*

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

6. Sağ tıklar ve *dosyada Yeniden Adlandır'ı* seçerek dosyayı BankAccount.cs **olarak** **Çözüm Gezgini.**

7. Derleme menüsünde **Çözümü Derleme'ye** **tıklayın (veya** **Ctrl** SHIFT B  +    +  **tuşlarına basın).**

Artık test etmek için yöntemlerle bir projeniz var. Bu makalede testler yöntemine `Debit` odaklanır. Yöntem, `Debit` bir hesaptan para çekildiğiniz zaman çağrılır.

## <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

1. Dosya menüsünde **Yeni** **Ekle'yi seçin**  >  **ve Project.**

   > [!TIP]
   > Ayrıca, Çözüm Gezgini'da çözüme **sağ tık Çözüm Gezgini** **Ekle'yi**  >  **Project.**

::: moniker range="vs-2017"

2. Yeni **Project** iletişim kutusunda Yüklü'leri **genişletin,** **Visual C# öğesini genişletin** ve ardından Test'i **seçin.**

3. Şablon listesinden MSTest Test Project **(.NET Core) öğesini seçin.**

4. Ad **kutusuna yazın** ve `BankTests` Tamam'ı **seçin.**

   **BankTests** projesi Banka **çözümüne** eklenir.

::: moniker-end

::: moniker range=">=vs-2019"

2. Arama **kutusuna test** yazın, dil olarak **C#** öğesini seçin, ardından .NET Core şablonu için C# Birim Testi **Project'yi** seçin ve ardından Sonraki 'ye **tıklayın.**

   > [!NOTE]
   > 2019 Visual Studio 16.9 sürümünden başlayarak, MSTest proje şablonu adı **MSTest Birim Testi Project (.NET Core)** olarak Birim Testi şablonu **olarak Project.**

3. Projeye **BankTests adını ve Ardından'ya** **tıklayın.**

4. Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   **BankTests** projesi Banka **çözümüne** eklenir.

::: moniker-end

5. **BankTests projesine** bir başvuru **ekleyin.**

   Bu **Çözüm Gezgini** **BankTests** **projesinin** altında Bağımlılıklar'ı seçin ve ardından sağ tıklama **menüsünden** Başvuru Ekle'yi seçin.

6. Başvuru Yöneticisi **iletişim kutusunda** Projeler'i **genişletin,** **Çözüm'i seçin** ve ardından Banka **öğesini** işaretleyin.

7. **Tamam'ı seçin.**

## <a name="create-the-test-class"></a>Test sınıfını oluşturma

Sınıfını doğrulamak için bir test sınıfı `BankAccount` oluşturun. Proje şablonu tarafından *oluşturulan UnitTest1.cs* dosyasını kullanabilirsiniz, ancak dosyaya ve sınıfa daha açıklayıcı adlar veebilirsiniz.

### <a name="rename-a-file-and-class"></a>Bir dosyayı ve sınıfı yeniden adlandırma

1. Dosyayı yeniden adlandırmak **için, Çözüm Gezgini** *BankTests projesinde UnitTest1.cs* dosyasını seçin. Sağ tıklama menüsünden Yeniden Adlandır'ı **seçin** (veya **F2** tuşuna basın) ve ardından dosyayı *BankAccountTests.cs olarak yeniden adlandırın.*

::: moniker range="vs-2017"

2. Sınıfı yeniden adlandırmak **için** açılan iletişim kutusunda Evet'i seçin ve kod öğesine yapılan başvuruları yeniden adlandırmak isteyip istemediklerini sorar.

::: moniker-end

::: moniker range=">=vs-2019"

2. Sınıfı yeniden adlandırmak için imleci kod düzenleyicisinde üzerine getirin, sağ tıklayın ve Yeniden `UnitTest1` Adlandır'ı  seçin (veya **F2 tuşuna basın).** **BankAccountTests yazın ve** Enter tuşuna **basın.**

::: moniker-end

*BankAccountTests.cs* dosyası artık aşağıdaki kodu içerir:

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

### <a name="add-a-using-statement"></a>Using deyimi ekleme

Tam [ `using` adları](/dotnet/csharp/language-reference/keywords/using-statement) kullanmadan test altındaki projeye çağrı yapmak için test sınıfına bir deyimi ekleyin. Sınıf dosyasının en üstüne şunları ekleyin:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Test sınıfı gereksinimleri

Bir test sınıfı için en düşük gereksinimler:

- özniteliği, `[TestClass]` Test Gezgini'nde çalıştırmak istediğiniz birim testi yöntemlerini içeren herhangi bir sınıfta gereklidir.

- Test Gezgini'nin tanımasını istediğiniz her test yönteminin özniteliğine sahip olması `[TestMethod]` gerekir.

Bir birim testi projesinde özniteliğine sahip olan başka sınıflar olabilir ve test sınıflarında özniteliğine sahip `[TestClass]` başka yöntemleriniz `[TestMethod]` olabilir. Bu diğer sınıfları ve yöntemleri test yöntemlerinize çağırabilirsiniz.

## <a name="create-the-first-test-method"></a>İlk test yöntemini oluşturma

Bu yordamda, sınıfının yönteminin davranışını doğrulamak için birim testi `Debit` yöntemleri `BankAccount` yazacaksiniz.

Denetlenen en az üç davranış vardır:

- Yöntemi, banka tutarı <xref:System.ArgumentOutOfRangeException> bakiyeden büyükse bir atar.

- Yöntemi, banka tutarı <xref:System.ArgumentOutOfRangeException> sıfırdan küçükse bir atar.

- Banka tutarı geçerli ise yöntemi, banka tutarını hesap bakiyeden çıkarır.

> [!TIP]
> Varsayılan yöntemi `TestMethod1` silebilirsiniz çünkü bu kılavuzda kullanmayabilirsiniz.

### <a name="to-create-a-test-method"></a>Test yöntemi oluşturmak için

İlk test, geçerli bir miktarın (hesap bakiyeden küçük ve sıfırdan büyük bir miktar) hesaptan doğru miktarı geri çekildiğini doğrular. Bu sınıfa aşağıdaki yöntemi `BankAccountTests` ekleyin:

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

Yöntemi basittir: Başlangıç bakiyesi olan yeni `BankAccount` bir nesne ayarlar ve ardından geçerli bir miktarı geri çeker. Bitiş <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> bakiyenin beklendiği gibi olduğunu doğrulamak için yöntemini kullanır. , ve `Assert.AreEqual` diğerleri <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> gibi yöntemler genellikle birim testlerinde kullanılır. Birim testi yazma hakkında daha fazla kavramsal bilgi için [bkz. Testlerinizi yazma.](../test/unit-test-basics.md#write-your-tests)

### <a name="test-method-requirements"></a>Test yöntemi gereksinimleri

Test yöntemi aşağıdaki gereksinimleri karşılamalıdır:

- özniteliğiyle birlikte dekore `[TestMethod]` edilmiştir.

- döndürür. `void`

- Parametreleri olamaz.

## <a name="build-and-run-the-test"></a>Testi derleme ve çalıştırma

1. Derleme menüsünde **Çözümü** Derleme'yi **seçin (veya** **Ctrl** SHIFT B  +    +  **tuşlarına basın).**

2. **Test Gezgini açık** yoksa, üst menü **çubuğundan Test** Gezgini'ni Windows Test Gezgini'ni seçerek açın  >    >   **(veya Ctrl** E , T  +  **tuşlarına** **basın).**

3. Testi **çalıştırmak için Hepsini** Çalıştır'ı seçin (veya **Ctrl**  +  **R**, **V tuşlarına basın).**

   Test çalışırken Test Gezgini penceresinin üst kısmında yer alan durum **çubuğu animasyonlu** olur. Test çalıştırması sonunda tüm test yöntemleri başarılı olursa çubuk yeşile, testlerden herhangi biri başarısız olursa kırmızıya döner.

   Bu durumda test başarısız olur.

4. Pencerenin alt kısmında **ayrıntıları görüntülemek** için Test Gezgini'nde yöntemini seçin.

## <a name="fix-your-code-and-rerun-your-tests"></a>Kodunuzu düzeltme ve testlerinizi yeniden çalıştırma

Test sonucu, başarısızlığı açıklayan bir ileti içerir. yöntemi `AreEqual` için ileti, beklenen ve gerçekte alınan öğeleri görüntüler. Dengenin azalmayı beklemiştiniz, ancak bunun yerine denge miktarı artmıştır.

Birim testi bir hata olduğunu tespit etti:  çıkarılma gereken hesap bakiyesi için geri ödeme *miktarı eklenir.*

### <a name="correct-the-bug"></a>Hatayı düzeltme

Hatayı düzeltmek için *BankAccount.cs* dosyasındaki şu satırı değiştirin:

```csharp
m_balance += amount;
```

Yeni değer:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Testi yeniden çalıştırın

**Test Gezgini**'nde, testi yeniden **çalıştırmak için Tümünü Çalıştır** ' ı seçin (veya **CTRL**  +  **R**, **V** tuşlarına basın). Kırmızı/yeşil çubuk, testin geçtiğini belirtmek için yeşile dönüşür.

![geçilen testi gösteren Visual Studio 2019 ' de Test gezgini](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>Kodunuzu geliştirmek için birim testlerini kullanın

Bu bölümde, yinelenen analiz, birim testi geliştirme ve yeniden düzenleme işlemlerinin üretim kodunuzu daha sağlam ve etkili hale getirmenize nasıl yardımcı olduğu açıklanır.

### <a name="analyze-the-issues"></a>Sorunları analiz etme

Geçerli bir miktarın yöntemde doğru şekilde kesildiğini onaylamak için bir test yöntemi oluşturdunuz `Debit` . Şimdi, <xref:System.ArgumentOutOfRangeException> Borç tutarının aşağıdakilerden biri olması durumunda yöntemin bir olduğunu doğrulayın:

- bakiyesinden büyük veya
- sıfırdan küçük.

### <a name="create-and-run-new-test-methods"></a>Yeni test yöntemleri oluştur ve Çalıştır

Borç miktarı sıfırdan küçükse doğru davranışı doğrulamak için bir test yöntemi oluşturun:

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

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A>Doğru özel durumun atılmışsa emin olmak için yöntemini kullanın. Bu yöntem, bir oluşturulmadığı takdirde testin başarısız olmasına neden olur <xref:System.ArgumentOutOfRangeException> . Test altındaki yöntemi geçici olarak değiştirirseniz, <xref:System.ApplicationException> borç miktarı sıfırdan küçükse, test doğru bir şekilde davranır &mdash; , başarısız olur.

Geri kalan miktar bakiyesinden daha büyükse, büyük/küçük harf durumunu test etmek için aşağıdaki adımları uygulayın:

1. Adlı yeni bir test yöntemi oluşturun `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` .

2. Yöntem gövdesini ' dan `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` yeni yönteme kopyalayın.

3. `debitAmount`Sayısını bakiyesinden daha büyük bir sayı olarak ayarlayın.

İki testi çalıştırın ve bunların başarılı olduğunu doğrulayın.

### <a name="continue-the-analysis"></a>Analize devam edin

Test edilmekte olan yöntem daha fazla geliştirilebilir. Geçerli uygulamayla, test sırasında hangi koşulun ( `amount > m_balance` veya) atılmakta olduğunu belirlemenin bir yolu yoktur `amount < 0` . `ArgumentOutOfRangeException`Yönteminde bir yerde oluşturulduğunu biliyoruz. `BankAccount.Debit`Özel durumun hangi koşulla kaynaklandığını (veya) söylediğimiz durumlarda, `amount > m_balance` `amount < 0` yöntemimizin bağımsız değişkenlerini doğru şekilde kontrol etmemiz konusunda emin olduğumuz için bu daha iyi olacaktır.

Test edilen yönteme ( `BankAccount.Debit` ) yeniden bakın ve her iki koşullu deyimin da `ArgumentOutOfRangeException` bağımsız değişkenin adını parametre olarak alan bir Oluşturucu kullandığına dikkat edin:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Daha zengin bilgilerin bulunduğu raporları kullanabileceğiniz bir Oluşturucu vardır: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> bağımsız değişkenin adını, bağımsız değişken değerini ve Kullanıcı tanımlı bir iletiyi içerir. Bu Oluşturucuyu kullanmak için test edilen yöntemi yeniden düzenleyebilirsiniz. Daha da iyisi, hataları belirtmek için genel kullanıma açık tür üyelerini kullanabilirsiniz.

### <a name="refactor-the-code-under-test"></a>Test altındaki kodu yeniden düzenleme

İlk olarak, sınıf kapsamındaki hata iletileri için iki sabit tanımlayın. Bunları test edilen sınıfına yerleştirin `BankAccount` :

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Ardından, yönteminde iki koşullu deyimi değiştirin `Debit` :

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

Çağrısını kaldırarak test yöntemlerini yeniden düzenleyin <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> . Çağrıyı `Debit()` bir blokta sarın `try/catch` , beklenen özel durumu yakalayın ve ilişkili iletisini doğrulayın. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName>Yöntemi iki dizeyi karşılaştırma yeteneği sağlar.

Şimdi, şöyle `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` görünebilir:

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

### <a name="retest-rewrite-and-reanalyze"></a>Yeniden test etme, yeniden yazma ve yeniden çözümleme

Şu anda test yöntemi, gereken tüm durumları işlemez. Test edilen yöntem, `Debit` bir <xref:System.ArgumentOutOfRangeException> zaman `debitAmount` bakiyesinden (veya sıfırdan küçükse) daha büyük olduğunda yöntemi oluşturamadı, test yöntemi geçer. Hiçbir özel durum atılmadığı takdirde test yönteminin başarısız olmasını istediğiniz için bu iyi değildir.

Bu, test yöntemindeki bir hatadır. Sorunu çözmek için, bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A?displayProperty=nameWithType> özel durumun oluşturulduğu durumu işlemek üzere test yönteminin sonuna bir onay ekleyin.

Testin yeniden çalıştırılması, doğru özel durum yakalanırsa testin artık *başarısız* olduğunu gösterir. `catch`Blok özel durumu yakalar, ancak yöntem yürütülmeye devam eder ve yeni onaylama sırasında başarısız olur <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A?displayProperty=nameWithType> . Bu sorunu çözmek için, `return` bloktaki öğesinden sonra bir ifade ekleyin `StringAssert` `catch` . Testi yeniden çalıştırmak, bu sorunu düzelttik olduğunu onaylar. Öğesinin son sürümü şöyle `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` görünür:

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

Test koduna yönelik iyileştirmeler daha sağlam ve bilgilendirici test yöntemlerine sahiptir. Ancak daha da önemlisi test altındaki kodu geliştirmiştir.

> [!TIP]
> Bu izlenecek yol, yönetilen kod için Microsoft birim testi çerçevesini kullanır. **Test Gezgini** , **Test Gezgini** için bağdaştırıcılara sahip üçüncü taraf birim testi çerçevelerinden testleri de çalıştırabilir. Daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçevelerini yüklemeyi](../test/install-third-party-unit-test-frameworks.md).

## <a name="see-also"></a>Ayrıca bkz.

Bir komut satırından testlerin nasıl çalıştırılacağı hakkında daha fazla bilgi için [VSTest.Console.exe komut satırı seçenekleri](vstest-console-options.md)' ne bakın.
