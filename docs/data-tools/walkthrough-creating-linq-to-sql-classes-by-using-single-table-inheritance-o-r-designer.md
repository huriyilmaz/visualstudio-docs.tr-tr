---
title: LINQ to SQL tablo devralma ile sınıflarını yeniden seçin
description: Bu kılavuzda, LINQ to SQL (O/R Tasarımcısı) içinde tek tablo devralmayı Visual Studio Nesne İlişkisel Tasarımcısı sınıflarını oluşturun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ff15209b60fb40200388eac2d9b1d90bb153fcfbba5c204f391c5bc7fbd70343
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346510"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Kılavuz: Tek LINQ to SQL (O/R Tasarımcısı) kullanarak yeni sınıf oluşturma
Bu [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) ilişkisel sistemlerde uygulanan tek tablo devralmayı destekler. Bu kılavuz, [O/R Tasarımcısı'nın](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) kullanımıyla devralmayı yapılandırma konu başlığında sağlanan genel adımların kapsamını genişleterek ve içinde devralma kullanımını göstermek için bazı gerçek veriler [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sağlar.

Bu kılavuz sırasında aşağıdaki görevleri gerçekleştirebilirsiniz:

- Bir veritabanı tablosu oluşturun ve buna veri ekleyin.

- Windows Forms uygulaması oluşturun.

- Projeye [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] dosya ekleme.

- Yeni varlık sınıfları oluşturun.

- Varlık sınıflarını devralmayı kullanmak üzere yapılandırma.

- Devralınan sınıfı sorgular.

- Verileri bir Form Windows görüntüleme.

## <a name="create-a-table-to-inherit-from"></a>Devralınacak bir tablo oluşturma
Devralmanın nasıl çalıştığını görmek için küçük bir tablo oluşturur, bunu temel sınıf olarak kullanır ve ardından ondan devralan `Person` `Employee` bir nesne oluşturursanız.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Devralmayı göstermek için bir temel tablo oluşturmak için

1. Yeni **Sunucu Gezgini** veya **Veritabanı Gezgini'da** Tablolar düğümüne sağ **tıklayın** ve Yeni Tablo **Ekle'ye tıklayın.**

    > [!NOTE]
    > Northwind veritabanını veya tablo ekleyebilirsiniz başka bir veritabanını kullanabilirsiniz.

2. aşağıdaki **Tablo Tasarımcısı** tabloya aşağıdaki sütunları ekleyin:

    |Sütun Adı|Veri Türü|Null Değerlere İzin Ver|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Tür**|**int**|**True**|
    |**FirstName**|**nvarchar(200)**|**False**|
    |**LastName**|**nvarchar(200)**|**False**|
    |**Yönetici**|**int**|**True**|

3. ID sütununu birincil anahtar olarak ayarlayın.

4. Tabloyu kaydedin ve Person olarak **ad girin.**

## <a name="add-data-to-the-table"></a>Tabloya veri ekleme
Devralmanın doğru yapılandırıldığından emin olmak için tablonun tek tablo devralmadaki her sınıf için bazı verilere ihtiyacı vardır.

### <a name="to-add-data-to-the-table"></a>Tabloya veri eklemek için

1. Tabloyu veri görünümünde açın. (Tablo verilerini **göster'e** **Sunucu Gezgini** veya **Veritabanı Gezgini** **kişi tablosuna sağ tıklayın.)**

2. Aşağıdaki verileri tabloya kopyalayın. (Sonuçlar Bölmesindeki satırın tamamını seçerek kopyalayıp tabloya **yapıştırabilirsiniz.)**

    |**ID**|**Tür**|**FirstName**|**LastName**|**Yönetici**|
    |-|-|-|-|-|
    |**1**|**1**|**Anne**|**Wallace**|**Null**|
    |**2**|**1**|**Carlos**|**Grilo**|**Null**|
    |**3**|**1**|**Yael**|**Peeded**|**Null**|
    |**4**|**2**|**Gatis**|**Oklar**|**1**|
    |**5**|**2**|**Andreas**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michayır**|**Sonzkiewicz**|**2**|
    |**9**|**2**|**Tai**|**Yee**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Mindy**|**Martin**|**3**|
    |**12**|**2**|**UK**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Yeni proje oluşturma
Artık tabloyu oluşturduğunuza göre, devralmayı yapılandırmayı göstermek için yeni bir proje oluşturun.

### <a name="to-create-the-new-windows-forms-application"></a>yeni Windows Forms uygulamasını oluşturmak için

1. Visual Studio, **dosya** menüsünde **yeni**  >  **Project**' yi seçin.

2. sol bölmedeki **Visual C#** ' ı veya **Visual Basic** genişletin ve sonra **Windows masaüstü**' nü seçin.

3. orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **InheritanceWalkthrough** olarak adlandırın ve ardından **Tamam**' ı seçin.

     **InheritanceWalkthrough** projesi oluşturulur ve **Çözüm Gezgini** eklenir.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>projeye LINQ to SQL sınıfları dosyası ekleyin

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>projeye bir LINQ to SQL dosyası eklemek için

1. **Project** menüsünde, **yeni öğe ekle**' ye tıklayın.

2. **LINQ to SQL sınıfları** şablonuna ve ardından **ekle**' ye tıklayın.

     *. Dbml* dosyası projeye eklenir ve **O/R Tasarımcısı** açılır.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>O/R tasarımcısını kullanarak devralmayı oluşturma
**Devralma nesnesini** **araç kutusundan** tasarım yüzeyine sürükleyerek devralmayı yapılandırın.

### <a name="to-create-the-inheritance"></a>Devralmayı oluşturmak için

1. **Sunucu Gezgini** veya **veritabanı Gezgini** içinde, daha önce oluşturduğunuz **kişi** tablosuna gidin.

2. **Kişi** tablosunu **O/R Tasarımcısı** tasarım yüzeyine sürükleyin.

3. İkinci bir **kişi** tablosunu **O/R tasarımcısına** sürükleyin ve adını **çalışan** olarak değiştirin.

4. **Kişi** nesnesinden **yönetici** özelliğini silin.

5. **Employee** nesnesinden **Type**, **ID**, **FirstName** ve **LastName** özelliklerini silin. (Diğer bir deyişle, **yönetici** hariç tüm özellikleri silin.)

6. **araç kutusunun** **Nesne İlişkisel Tasarımcısı** sekmesinden, **kişi** ve **çalışan** nesneleri arasında bir **devralma** oluşturun. Bunu yapmak için **araç kutusu** 'nda **Devralma** öğesine tıklayın ve fare düğmesini bırakın. Ardından, **çalışan** nesnesine ve sonra **O/R tasarımcısında** **Person** nesnesine tıklayın. Devralma satırındaki ok daha sonra **Person** nesnesine işaret eder.

7. Tasarım yüzeyinde **Devralma** satırına tıklayın.

8. **Ayrıştırıcı özelliği** özelliğini **Type** olarak ayarlayın.

9. **Türetilmiş sınıf ayrıştırıcı değeri** özelliğini **2** olarak ayarlayın.

10. **Temel sınıf ayrıştırıcı değeri** özelliğini **1** olarak ayarlayın.

11. **Devralma varsayılan** özelliğini **Person** olarak ayarlayın.

12. Projeyi derleyin.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Devralınan sınıfı sorgulama ve verileri formda görüntüleme
Artık, nesne modelinde belirli bir sınıf için sorgular oluşturacak biçimde kod eklersiniz.

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Bir LINQ sorgusu oluşturmak ve sonuçları formda göstermek için

1. Bir **liste kutusunu** **Form1** üzerine sürükleyin.

2. Olay işleyicisi oluşturmak için forma çift tıklayın `Form1_Load` .

3. Aşağıdaki kodu `Form1_Load` olay işleyicisine ekleyin:

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

## <a name="test-the-application"></a>Uygulamayı test edin
Uygulamayı çalıştırın ve liste kutusunda görüntülenen kayıtların tüm çalışanlar ( **tür** sütununda 2 değeri olan kayıtlar) olduğunu doğrulayın.

### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. **F5** tuşuna basın.

2. Yalnızca **tür** sütununda 2 değeri olan kayıtların görüntülendiğini doğrulayın.

3. Formu kapatın. ( **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur**' a tıklayın.)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio araçlar LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [izlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [nasıl yapılır: Visual Basic veya C 'de nesne modeli oluşturma #](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)
