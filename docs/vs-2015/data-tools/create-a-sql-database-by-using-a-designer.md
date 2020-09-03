---
title: Tasarımcı kullanarak SQL veritabanı oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 33b97050f04fd23a9fa3b6c3c641faa5dfe4802f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651054"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Tasarımcı kullanarak SQL veritabanı oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SQL Server Express LocalDB 'de yerel bir veritabanı dosyası oluşturmak ve güncelleştirmek için Visual Studio kullanarak tablo ekleme ve sütun tanımlama gibi temel görevleri inceleyebilirsiniz. Bu izlenecek yolu tamamladığınızda, gereken diğer izlenecek yollar için bir yerel veritabanınızı bir başlangıç noktası olacak şekilde kullanarak daha fazla gelişmiş özelliği keşfedebilirsiniz.

 Ayrıca, Visual Studio 'daki **SQL Server Nesne Gezgini** araç penceresinde SQL Server Management Studio (ayrı bir indirme) veya Transact-SQL deyimlerini kullanarak da bir veritabanı oluşturabilirsiniz.

 Bu izlenecek yol boyunca, aşağıdaki görevler hakkında bilgi edineceksiniz:

- [Bir proje ve yerel veritabanı dosyası oluşturma](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)

- [Tablolar, sütunlar, birincil anahtarlar ve yabancı anahtarlar oluşturma](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)

- [Tabloları verilerle doldurma](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenecek yolu tamamlamak için SQL Server Veri Araçları yüklü olduğundan emin olun. **Görünüm** menüsünde **SQL Server Nesne Gezgini**görmeniz gerekir. Bu yoksa, **Program Ekle veya Kaldır**'a gidin, **Visual Studio 2015**' e tıklayın, **değiştir**' i seçin ve **SQL Server veri araçları**yanındaki kutuyu seçin.

## <a name="create-a-project-and-a-local-database-file"></a><a name="BKMK_CreateNewSQLDB"></a> Bir proje ve yerel veritabanı dosyası oluşturma

#### <a name="to-create-a-project-and-a-database-file"></a>Bir proje ve yerel veritabanı dosyası oluşturmak için

1. Adında bir Windows Forms projesi oluşturun `SampleDatabaseWalkthrough` .

2. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

3. Öğe şablonları listesinde, aşağı kaydırın ve **hizmet tabanlı veritabanı**' nı seçin.

    ![Öğe şablonları iletişim kutusu](../data-tools/media/raddata-vsitemtemplates.png "radveri VSItemTemplates")

4. Veritabanını **SampleDatabase**olarak adlandırın ve ardından **Ekle** düğmesini seçin.

5. **Veri kaynakları** penceresi açık değilse, SHIFT + alt + D tuşlarını seçerek veya menü çubuğunda **View**  >  **diğer Windows**  >  **veri kaynaklarını**görüntüle ' yi seçerek açın.

6. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle** bağlantısını seçin.

7. **Veri kaynağı Yapılandırma sihirbazında**, varsayılan ayarları kabul etmek için **İleri** düğmesini dört kez seçin ve ardından **son** düğmesini seçin.

   Veritabanı için özellikler penceresini açarak bağlantı dizesini ve birincil .mdf dosyasının konumunu görüntüleyebilirsiniz. Veritabanı dosyasının proje klasöründe olduğunu görürsünüz.

- **View**  >  Bu pencere zaten açık değilse, Visual Studio 'da görüntüle**SQL Server Nesne Gezgini** ' yi seçin. **Veri bağlantıları** düğümünü genişleterek, SampleDatabase. mdf kısayol menüsünü açarak ve ardından **Özellikler**' i seçerek Özellikler penceresini açın.

- Alternatif olarak, **View**  >  Bu pencere zaten açık değilse**Sunucu Gezgini**görüntüle ' yi seçebilirsiniz. **Veri bağlantıları** düğümünü genişleterek Özellikler penceresini açın. SampleDatabase. mdf için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

## <a name="create-tables-columns-primary-keys-and-foreign-keys"></a><a name="BKMK_CreateNewTbls"></a> Tablolar, sütunlar, birincil anahtarlar ve yabancı anahtarlar oluşturma
 Bu bölümde birkaç tablo, her tabloda bir birincil anahtar ve birkaç örnek veri satırı oluşturacaksınız. Sonraki izlenecek yolda, bu bilgilerin uygulamada nasıl görüneceği hakkında bir fikir elde edeceksiniz. Ayrıca, bir tablodaki kayıtların diğer tablodaki kayıtlara nasıl karşılık gelebileceğini belirtmek için yabancı anahtar da oluşturacaksınız.

#### <a name="to-create-the-customers-table"></a>Müşteriler tablosu oluşturmak için

1. **Sunucu Gezgini** veya **SQL Server Nesne Gezgini**' de, **veri bağlantıları** düğümünü genişletin ve **SampleDatabase. mdf** düğümünü genişletin.

2. **Tablolar**için kısayol menüsünü açın ve **Yeni Tablo Ekle**' yi seçin.

     **Tablo Tasarımcısı** açılır ve oluşturmakta olduğunuz tablodaki tek bir sütunu temsil eden bir varsayılan satır içeren bir kılavuz gösterir. Kılavuza satırlar ekleyerek, tabloda sütunlar ekleyeceksiniz.

3. Kılavuzda, aşağıdaki girişlerin her biri için bir satır ekleyin:

    |Sütun adı|Veri türü|Null'lere izin ver|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (işaretsiz)|
    |`CompanyName`|`nvarchar(50)`|False (işaretsiz)|
    |`ContactName`|`nvarchar (50)`|True (seçili)|
    |`Phone`|`nvarchar (24)`|True (seçili)|

4. Satır için kısayol menüsünü açın `CustomerID` ve ardından **birincil anahtarı ayarla**' yı seçin.

5. Varsayılan satır için kısayol menüsünü açın ve **Sil**' i seçin.

6. Betik bölmesindeki ilk satırı aşağıdaki örnekle eşleşecek şekilde değiştirerek Müşteriler tablosunu adlandırın:

    ```
    CREATE TABLE [dbo].[Customers]
    ```

     Şuna benzer bir şey görmeniz gerekir:

     ![Tablo Tasarımcısı](../data-tools/media/raddata-table-designer.png "radveri Tablo Tasarımcısı")

7. **Tablo Tasarımcısı**sol üst köşesinde **Güncelleştir** düğmesini seçin.

8. **Veritabanı güncelleştirmelerini Önizle** Iletişim kutusunda **veritabanını güncelleştir** düğmesini seçin.

     Değişiklikleriniz yerel veritabanı dosyasına kaydedildi.

#### <a name="to-create-the-orders-table"></a>Siparişler tablosu oluşturmak için

1. Başka bir tablo ekleyin ve sonra aşağıdaki tabloda her giriş için bir satır ekleyin:

    |Sütun adı|Veri türü|Null'lere izin ver|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (işaretsiz)|
    |`CustomerID`|`nchar(5)`|False (işaretsiz)|
    |`OrderDate`|`datetime`|True (seçili)|
    |`OrderQuantity`|`int`|True (seçili)|

2. **OrderID** öğesini birincil anahtar olarak ayarlayın ve ardından varsayılan satırı silin.

3. Betik bölmesindeki ilk satırı aşağıdaki örnekle eşleşecek şekilde değiştirerek Siparişler tablosunu adlandırın:

    ```
    CREATE TABLE [dbo].[Orders]
    ```

4. **Tablo Tasarımcısı**sol üst köşesinde **Güncelleştir** düğmesini seçin.

5. **Veritabanı güncelleştirmelerini Önizle** Iletişim kutusunda **veritabanını güncelleştir** düğmesini seçin.

     Değişiklikleriniz yerel veritabanı dosyasına kaydedildi.

#### <a name="to-create-a-foreign-key"></a>Yabancı anahtar oluşturmak için

1. Kılavuzun sağ tarafındaki bağlam bölmesinde **yabancı anahtarlar**için kısayol menüsünü açın ve aşağıdaki çizimde gösterildiği gibi **yeni yabancı anahtar Ekle**öğesini seçin.

     ![Tablo Tasarımcısı yabancı anahtar ekleme](../data-tools/media/foreignkey.png "Yabancıanahtar")

2. Görüntülenen metin kutusunda **ToTable** öğesini ile değiştirin `Customers` .

3. T-SQL bölmesinde, son satırı aşağıdaki örnekle eşleşecek şekilde güncelleştirin:

    ```
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. **Tablo Tasarımcısı**sol üst köşesinde **Güncelleştir** düğmesini seçin.

5. **Veritabanı güncelleştirmelerini Önizle** Iletişim kutusunda **veritabanını güncelleştir** düğmesini seçin.

     Değişiklikleriniz yerel veritabanı dosyasına kaydedildi.

## <a name="populate-the-tables-with-data"></a><a name="BKMK_Populating"></a> Tabloları verilerle doldurma

#### <a name="to-populate-the-tables-with-data"></a>Tabloları veriyle doldurmak için

1. **Sunucu Gezgini** veya **SQL Server Nesne Gezgini**' de, örnek veritabanının düğümünü genişletin.

2. **Tablolar** düğümü için kısayol menüsünü açın, **Yenile**' yi seçin ve **Tablolar** düğümünü genişletin.

3. Müşteriler tablosu için kısayol menüsünü açın ve ardından **tablo verilerini göster**' i seçin.

4. En az üç müşteriye istediğiniz verileri ekleyin.

     Müşteri kimliklerini beş karakterli olarak istediğiniz gibi belirtebilirsiniz, ancak en azından bu yordamda daha sonra kullanmak üzere hatırlayabileceğiniz bir kimlik olmalıdır.

5. Siparişler tablosu için kısayol menüsünü açın ve ardından **tablo verilerini göster**' i seçin.

6. En az üç sipariş için veri ekleyin.

    > [!IMPORTANT]
    > Tüm sipariş kimlikleri ve sipariş miktarlarının tam sayılar olduğundan ve her müşteri kimliğinin Müşteriler tablosunun CustomerID sütununda belirttiğiniz bir değerle eşleştiğinden emin olun.

7. Menü çubuğunda **Dosya**  >  **Tümünü Kaydet**' i seçin.

8. Menü çubuğunda **Dosya**  >  **Kapat çözüm**' ü seçin.

    > [!NOTE]
    > En iyi uygulama yöntemi olarak, az önce oluşturduğunuz veritabanı dosyasını kopyalayarak ve daha sonra kopyayı diğer bir konuma yapıştırarak ya da kopyaya başka bir ad vererek yedekleyebilirsiniz.

## <a name="next-steps"></a>Sonraki Adımlar
 Artık bazı örnek veriler içeren bir yerel veritabanı dosyasına sahip olduğunuza göre, veritabanı görevlerini gösteren yönergelerden herhangi birini tamamlayabilirsiniz.
