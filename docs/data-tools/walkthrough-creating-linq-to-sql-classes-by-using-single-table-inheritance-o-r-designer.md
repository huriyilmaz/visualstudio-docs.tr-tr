---
title: LINQ to SQL tablo devralma ile sınıflarını yeniden seçin
description: Bu kılavuzda, LINQ to SQL (O/R Tasarımcısı) içinde tek tablo devralmayı kullanarak Visual Studio Nesne İlişkisel Tasarımcısı sınıflarını oluşturun.
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

- Verileri Bir Windows Görüntüleme.

## <a name="create-a-table-to-inherit-from"></a>Devralınacak bir tablo oluşturma
Devralmanın nasıl çalıştığını görmek için küçük bir tablo oluşturur, bunu temel sınıf olarak kullanır ve ardından ondan devralan `Person` `Employee` bir nesne oluşturursanız.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Devralmayı göstermek için bir temel tablo oluşturmak için

1. Yeni **Sunucu Gezgini** veya **Veritabanı Gezgini,** Tablolar düğümüne sağ **tıklayın** ve Yeni Tablo **Ekle'ye tıklayın.**

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

1. Tabloyu veri görünümünde açın. (Tablo veya Tablo Verilerini **Göster'Sunucu Gezgini** **Veritabanı Gezgini** **Kişi tablosuna sağ tıklayın.)** 

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
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Yeni proje oluşturma
Tabloyu oluşturduğunuza göre, devralmayı yapılandırmayı göstermek için yeni bir proje oluşturun.

### <a name="to-create-the-new-windows-forms-application"></a>Yeni Windows Forms uygulaması oluşturmak için

1. Bu Visual Studio, Dosya **menüsünde Yeni** **dosya'Project.**  >  

2. Sol **bölmede Visual C#** **Visual Basic** görseli genişletin ve ardından Masaüstü'Windows **seçin.**

3. Orta bölmede Windows **Forms Uygulaması proje** türünü seçin.

4. Projeye **InheritanceWalkthrough adını ve** ardından Tamam'ı **seçin.**

     **InheritanceWalkthrough** projesi oluşturulur ve **Çözüm Gezgini.**

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Projeye LINQ to SQL sınıf dosyası ekleme

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Projeye bir LINQ to SQL dosyası eklemek için

1. Yeni **Project** Ekle'ye **tıklayın.**

2. LINQ to SQL **Sınıfları şablonuna** ve ardından **Ekle'ye tıklayın.**

     *.dbml* dosyası projeye eklenir ve **O/R Tasarımcısı** açılır.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>O/R Tasarımcısını kullanarak devralmayı oluşturma
Devralma nesnesini Araç **Kutusundan** tasarım **yüzeyine sürükleyerek** devralmayı yapılandırma.

### <a name="to-create-the-inheritance"></a>Devralmayı oluşturmak için

1. Uygulama **Sunucu Gezgini** **Veritabanı Gezgini** daha önce oluşturduğunuz **Kişi** tablosuna gidin.

2. Kişi **tablosu'na** **O/R Tasarımcısı tasarım yüzeyine** sürükleyin.

3. İkinci bir **Kişi tabloyu** **O/R Tasarımcısı'na sürükleyin** ve adını Employee olarak **değiştirme.**

4. Person **nesnesinden Manager** **özelliğini** silin.

5. Employee **nesnesinden** **Tür, Kimlik,** **FirstName** ve **LastName** **özelliklerini** silin. (Başka bir deyişle, Yönetici dışındaki tüm özellikleri **silin.)**

6. Araç **Nesne İlişkisel Tasarımcısı** **sekmesinden Kişi** ve Çalışan nesneleri **arasında** bir **Devralma** **oluşturun.** Bunu yapmak için Araç Kutusunda **Devralma** öğesini **tıklatın ve** fare düğmesini bırakın. Ardından Employee **nesnesine ve** ardından O/R **Tasarımcısı'nda** **Person nesnesine tıklayın.** Devralma çizgisinin okunu Person nesnesine **gösterir.**

7. Tasarım yüzeyinde **Devralma** satırına tıklayın.

8. **Discriminator Özelliği özelliğini Tür** olarak **ayarlayın.**

9. Derived **Class Discriminator Value özelliğini** **2 olarak ayarlayın.**

10. Temel Sınıf **Ayırıcı Değeri özelliğini** **1 olarak ayarlayın.**

11. Devralma Varsayılan **özelliğini Kişi** olarak **ayarlayın.**

12. Projeyi derleyin.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Devralınan sınıfı sorgulama ve formda verileri görüntüleme
Şimdi forma, nesne modelinde belirli bir sınıf için sorgulanan bazı kodlar eklersiniz.

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>LinQ sorgusu oluşturmak ve sonuçları formda görüntülemek için

1. **ListBox'ı** **Form1'e sürükleyin.**

2. Bir olay işleyicisi oluşturmak için `Form1_Load` forma çift tıklayın.

3. Olay işleyiciye aşağıdaki `Form1_Load` kodu ekleyin:

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
Uygulamayı çalıştırın ve liste kutusunda görüntülenen kayıtların tüm çalışanların **(Tür** sütununda 2 değeri olan kayıtlar) olduğunu doğrulayın.

### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. **F5 tuşuna basın.**

2. Tür sütununda yalnızca 2 değerine sahip olan **kayıtların görüntülendiğinden** emin olur.

3. Formu kapatın. (Hata Ayıklama **menüsünde Hata Ayıklamayı** **Durdur'a tıklayın.)**

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [adım adım kılavuz: LINQ to SQL sınıfları oluşturma (O-R Tasarımcısı)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Nasıl kullanılır: Visual Basic veya C'de nesne modeli oluşturma #](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)
