---
title: 'İzlenecek yol: tek Tablo Devralma kullanarak LINQ to SQL sınıfları oluşturma (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 695378404e27b64f269fe4e9820b6b9e520c9d0f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660149"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>İzlenecek yol: tek tablo devralma (O/R Designer) kullanarak LINQ to SQL sınıfları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) , genellikle ilişkisel sistemlerde uygulanan tek tablo devralmayı destekler. Bu izlenecek yol, [nasıl yapılır: u/R tasarımcısını kullanarak devralmayı yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) konusuna sağlanan genel adımlara ve [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] devralma kullanımını göstermek için bazı gerçek veriler sağlar.

 Bu izlenecek yol sırasında, aşağıdaki görevleri yerine getirmeniz gerekir:

- Bir veritabanı tablosu oluşturun ve bu tabloya veri ekleyin.

- Windows Forms uygulaması oluşturun.

- Bir projeye [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] dosyası ekleyin.

- Yeni varlık sınıfları oluşturun.

- Devralma kullanmak için varlık sınıflarını yapılandırın.

- Devralınan sınıfı sorgulayın.

- Verileri bir Windows formunda görüntüleyin.

## <a name="create-a-table-to-inherit-from"></a>Devralması için bir tablo oluşturun
 Kalıtımın nasıl çalıştığını görmek için küçük bir kişi tablosu oluşturup bunu temel sınıf olarak kullanacaksınız ve bundan devralan bir çalışan nesnesi oluşturacaksınız.

#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Devralmayı göstermek üzere bir temel tablo oluşturmak için

1. **Sunucu Gezgini** /**veritabanı Gezgini**, **Tablolar** düğümüne sağ tıklayıp **Yeni Tablo Ekle**' ye tıklayın.

    > [!NOTE]
    > Northwind veritabanını veya tablo ekleyebileceğiniz herhangi bir veritabanını kullanabilirsiniz.

2. Tablo Tasarımcısı, tabloya aşağıdaki sütunları ekleyin:

    |Sütun adı|Veri Türü|Null değerlere izin ver|
    |-----------------|---------------|-----------------|
    |**NUMARASıNı**|**int**|**Yanlýþ**|
    |**Türüyle**|**int**|**Değeri**|
    |**FirstName**|**nvarchar (200)**|**Yanlýþ**|
    |**Soyadı**|**nvarchar (200)**|**Yanlýþ**|
    |**Manager**|**int**|**Değeri**|

3. KIMLIK sütununu birincil anahtar olarak ayarlayın.

4. Tabloyu kaydedin ve **kişiyi**adlandırın.

## <a name="add-data-to-the-table"></a>Tabloya veri ekleme
 Kalıtımın doğru yapılandırıldığını doğrulayabilmeniz için tablonun tek tablo Devralmada her bir sınıf için bazı veriler olması gerekir.

#### <a name="to-add-data-to-the-table"></a>Tabloya veri eklemek için

1. Tabloyu veri görünümünde açın. ( **Sunucu Gezgini** /**veritabanı Gezgini** **kişi** tablosuna sağ tıklayın ve **tablo verilerini göster**' e tıklayın.)

2. Aşağıdaki verileri tabloya kopyalayın. (Bunu kopyalayabilir ve ardından sonuçlar bölmesinde tüm satırı seçerek tabloya yapıştırabilirsiniz.)

    ||||||
    |-|-|-|-|-|
    |**NUMARASıNı**|**Türüyle**|**FirstName**|**Soyadı**|**Manager**|
    |**1**|**1**|**Gamze**|**Wallace**|**DEĞER**|
    |**iki**|**1**|**Carlos**|**Grilo dili**|**DEĞER**|
    |**03**|**1**|**Yael**|**Peled**|**DEĞER**|
    |**4**|**iki**|**Gaz**|**Ozolins**|**1**|
    |**e**|**iki**|**Andreas**|**Hauser**|**1**|
    |**inç**|**iki**|**Tiffany**|**Phuvasate**|**1**|
    |**7@@**|**iki**|**Alexey**|**Orekhov**|**iki**|
    |**240**|**iki**|**Michał**|**Poliszkiewicz**|**iki**|
    |**tuşlarına**|**iki**|**Tay**|**Yee**|**iki**|
    |**(**|**iki**|**Fabricıo**|**Noriega dili**|**03**|
    |**üst**|**iki**|**Mindy**|**Martin**|**03**|
    |**+**|**iki**|**UK**|**Kwok**|**03**|

## <a name="create-a-new-project"></a>Yeni bir proje oluştur
 Artık tabloyu oluşturduğunuza göre, devralmayı yapılandırmayı göstermek için yeni bir proje oluşturun.

#### <a name="to-create-the-new-windows-application"></a>Yeni Windows uygulaması oluşturmak için

1. **Dosya** menüsünden Yeni bir proje oluşturun.

2. Projeyi **InheritanceWalkthrough**olarak adlandırın.

    > [!NOTE]
    > @No__t_0 Visual Basic ve C# projelerinde desteklenir. Yeni projeyi bu dillerden birinde oluşturun.

3. **Windows Forms uygulama** şablonuna ve ardından **Tamam**' a tıklayın. Daha fazla bilgi için bkz. [Istemci uygulamaları](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

4. InheritanceWalkthrough projesi oluşturulup **Çözüm Gezgini**eklenir.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Projeye LINQ to SQL sınıfları dosyası ekleyin

#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Projeye bir LINQ to SQL dosyası eklemek için

1. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

2. **LINQ to SQL sınıfları** şablonuna ve ardından **Ekle**' ye tıklayın.

     . Dbml dosyası projeye eklenir ve [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] açılır.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>O/R tasarımcısını kullanarak devralmayı oluşturma
 **Devralma nesnesini** **araç kutusundan** tasarım yüzeyine sürükleyerek devralmayı yapılandırın.

#### <a name="to-create-the-inheritance"></a>Devralmayı oluşturmak için

1. **Sunucu Gezgini** /**veritabanı Gezgini**, daha önce oluşturduğunuz **kişi** tablosuna gidin.

2. **Kişi** tablosunu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tasarım yüzeyine sürükleyin.

3. İkinci bir **kişi** tablosunu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] sürükleyin ve adını **çalışan**olarak değiştirin.

4. **Kişi** nesnesinden **yönetici** özelliğini silin.

5. **Employee** nesnesinden **Type**, **ID**, **FirstName**ve **LastName** özelliklerini silin. (Diğer bir deyişle, **yönetici**hariç tüm özellikleri silin.)

6. **Araç kutusunun** **nesne ilişkisel Tasarımcısı** sekmesinden, **kişi** ve **çalışan** nesneleri arasında bir **Devralma** oluşturun. Bunu yapmak için **araç kutusu** 'nda **Devralma** öğesine tıklayın ve fare düğmesini bırakın. Ardından, **çalışan** nesnesine ve sonra [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] **kişi** nesnesine tıklayın. Devralma satırındaki ok, **Person** nesnesine işaret eder.

7. Tasarım yüzeyinde **Devralma** satırına tıklayın.

8. **Ayrıştırıcı özelliği** özelliğini **Type**olarak ayarlayın.

9. **Türetilmiş sınıf ayrıştırıcı değeri** özelliğini **2**olarak ayarlayın.

10. **Temel sınıf ayrıştırıcı değeri** özelliğini **1**olarak ayarlayın.

11. **Devralma varsayılan** özelliğini **Person**olarak ayarlayın.

12. Projeyi oluşturun.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Devralınan sınıfı sorgulama ve verileri formda görüntüleme
 Şimdi nesne modelinde belirli bir sınıf için sorgular oluşturacak biçimde bazı kodlar ekleyeceksiniz.

#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Bir LINQ sorgusu oluşturmak ve sonuçları formda göstermek için

1. Bir **liste kutusunu** Form1 üzerine sürükleyin.

2. @No__t_0 olay işleyicisi oluşturmak için forma çift tıklayın.

3. @No__t_0 olay işleyicisine aşağıdaki kodu ekleyin:

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>Uygulamayı test etme
 Uygulamayı çalıştırın ve liste kutusunda görüntülenen kayıtların tüm çalışanlar (tür sütununda 2 değeri olan kayıtlar) olduğunu doğrulayın.

#### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. F5 tuşuna basın.

2. Yalnızca tür sütununda 2 değeri olan kayıtların görüntülendiğini doğrulayın.

3. Formu kapatın. ( **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur**' a tıklayın.)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [nasıl yapılır: bir projeye LINQ to SQL sınıfları ekleme (o-r Designer)](https://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6) [Izlenecek yol: LINQ to SQL sınıfları oluşturma (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri Için saklı yordamlar atama (o/r Tasarımcı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [nasıl yapılır: Visual Basic veya C# nesne modelini oluşturma](https://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)
