---
title: Veritabanı dosyası oluşturma ve tablo tasarımcısını kullanma
description: Veritabanına tablo ve yabancı anahtar eklemek için veritabanına tablo ekleme hakkında bilgi Tablo Tasarımcısı öğretici Visual Studio. Ayrıca grafik arabirimi aracılığıyla veri eklemeyi de gösterir.
ms.date: 09/19/2019
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: cecf47d023b98ce8ad3cf67799e4bdfff66f45fa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631509"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Veritabanı oluşturma ve veritabanına tablo Visual Studio

LocalDB'Visual Studio yerel veritabanı dosyası oluşturmak ve güncelleştirmek için SQL Server Express kullanabilirsiniz. Veritabanı oluşturmak için transact-SQL deyimlerini SQL Server Nesne Gezgini **araç** penceresinde Visual Studio. Bu konu başlığında, bir *.mdf* dosyası oluşturarak tablo ve anahtar eklemek için Tablo Tasarımcısı.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için.NET masaüstü geliştirme  ve Veri depolama ile işleme iş yüklerinin Visual Studio.  Bunları yüklemek için, **Visual Studio Yükleyicisi** **ve** değiştirmek istediğiniz uygulamanın sürümünün yanındaki Değiştir (veya Daha  >  Fazla Değiştir) Visual Studio 'yi seçin.

> [!NOTE]
> Bu makaledeki yordamlar yalnızca .NET Framework Windows Forms projeleri için geçerlidir; .NET Core Windows Forms projeleri için geçerli değildir.

## <a name="create-a-project-and-a-local-database-file"></a>Proje ve yerel veritabanı dosyası oluşturma

1. Yeni bir **Windows Forms Uygulaması (.NET Framework) projesi** oluşturun ve **SampleDatabaseWalkthrough olarak ad girin.**

2. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

3. Öğe şablonları listesinde aşağı kaydırın ve Hizmet tabanlı **Veritabanı'ı seçin.**

   ![Öğe Şablonları iletişim kutusu](../data-tools/media/raddata-vsitemtemplates.png)

4. Veritabanına **SampleDatabase adını ve** ardından Ekle'ye **tıklayın.**

### <a name="add-a-data-source"></a>Veri kaynağı ekleme

1. Veri **Kaynakları penceresi açık** değilse, **Shift** Alt D tuşuna basarak veya menü çubuğunda Diğer Veri +  +    >    >  **Windows'yi** seçerek açın.

1. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'yi seçin.**

   ![Visual Studio'a yeni veri kaynağı ekleme](media/add-new-data-source.png)

   Veri **Kaynağı Yapılandırma Sihirbazı** açılır.

1. Veri Kaynağı **Türü Seçin sayfasında Veritabanı'ı** ve **ardından Sonraki'yi** **seçin.**

1. Veritabanı **Modeli Seçin sayfasında,** varsayılan değeri **(Veri Kümesi)** kabul etmek için Sonraki'yi seçin.

1. Veri **Bağlantınızı Seçin sayfasında,** açılan listeden **SampleDatabase.mdf** dosyasını seçin ve ardından Sonraki'yi **seçin.**

1. Bağlantı **Dizesini Uygulama Yapılandırma Dosyasına Kaydet sayfasında, Sonraki'yi** **seçin.**

1. Veritabanı **Nesnelerinizi Seçin sayfasında,** veritabanında nesne olmadığını söyleyen bir ileti görüntülenir. **Son**’u seçin.

### <a name="view-properties-of-the-data-connection"></a>Veri bağlantısının özelliklerini görüntüleme

*SampleDatabase.mdf* dosyasının bağlantı dizesini, veri bağlantısının Özellikler penceresi açarak görüntüebilirsiniz:

- Görünüm **penceresini**  >  **SQL Server Nesne Gezgini'ı** **SQL Server Nesne Gezgini** seçin. **(localdb)\MSSQLLocalDB** Veritabanları'ı  >  **genişletin** ve *SampleDatabase.mdf'ye* sağ tıklayın ve Özellikler'i **seçin.**

- Alternatif olarak, pencere **henüz**  >  **Sunucu Gezgini** görünümü'ne de bakabilirsiniz. Veri Özellikler penceresi genişleterek, *SampleDatabase.mdf'ye* sağ tıklar ve ardından Özellikler'i seçerek veri sayfasını **açın.** 

  > [!TIP]
  > Veri Bağlantıları düğümünü genişletemediyebilirsiniz veya SampleDatabase.mdf bağlantısı listelenmiyorsa, Bağlan araç çubuğundan Veritabanına Sunucu Gezgini seçin.  Bağlantı Ekle **iletişim kutusunda,** Veri kaynağı **altında Microsoft SQL Server** Veritabanı Dosyası'nın seçili olduğundan emin olun ve sampleDatabase.mdf dosyasına gidin ve dosyayı seçin. Tamam'ı seçerek bağlantıyı eklemeyi **bitirin.**

## <a name="create-tables-and-keys-by-using-table-designer"></a>Tablo ve anahtar oluşturmak için Tablo Tasarımcısı

Bu bölümde, her tabloda bir birincil anahtar ve birkaç örnek veri satırı olmak için iki tablo oluşturacaksınız. Ayrıca bir tablodaki kayıtların diğer tablodaki kayıtlara nasıl karşılık gelen olduğunu belirtmek için bir yabancı anahtar da oluşturabilirsiniz.

### <a name="create-the-customers-table"></a>Customers tablosu oluşturma

1. Bu **Sunucu Gezgini,** Veri **Bağlantıları düğümünü** ve ardından **SampleDatabase.mdf düğümünü** genişletin.

   Veri Bağlantıları düğümünü genişletemediyebilirsiniz veya SampleDatabase.mdf bağlantısı listelenmiyorsa, Bağlan araç çubuğundan Veritabanına Sunucu Gezgini seçin.  Bağlantı Ekle **iletişim kutusunda,** Veri kaynağı **altında Microsoft SQL Server** Veritabanı Dosyası'nın seçili olduğundan emin olun ve sampleDatabase.mdf dosyasına gidin ve dosyayı seçin. Tamam'ı seçerek bağlantıyı eklemeyi **bitirin.**

2. Tablolar'a sağ **tıklayın ve** Yeni Tablo **Ekle'yi seçin.**

   Bu Tablo Tasarımcısı açılır ve oluşturmakta olduğu tablodaki tek bir sütunu temsil eden bir varsayılan satıra sahip bir kılavuz gösterir. Kılavuza satırlar ekleyerek, tabloda sütunlar ekleyeceksiniz.

3. Kılavuzda, aşağıdaki girişlerin her biri için bir satır ekleyin:

   |Sütun adı|Veri türü|Null'lere izin ver|
   |-----------------|---------------|-----------------|
   |`CustomerID`|`nchar(5)`|False (işaretsiz)|
   |`CompanyName`|`nvarchar(50)`|False (işaretsiz)|
   |`ContactName`|`nvarchar (50)`|True (seçili)|
   |`Phone`|`nvarchar (24)`|True (seçili)|

4. satıra sağ tıklayın `CustomerID` ve Ardından Birincil Anahtarı **Ayarla'yı seçin.**

5. Varsayılan satıra ( ) sağ tıklayın ve `Id` Sil'i **seçin.**

6. Betik bölmesindeki ilk satırı aşağıdaki örnekle eşleşecek şekilde değiştirerek Müşteriler tablosunu adlandırın:

   ```sql
   CREATE TABLE [dbo].[Customers]
   ```

   Şuna benzer bir şey görmeniz gerekir:

   ![Tablo Tasarımcısı](../data-tools/media/table-designer.png)

7. Öğesinin sol üst köşesinde **güncelleştir'Tablo Tasarımcısı** **seçin.**

8. Veritabanı **Güncelleştirmelerini Önizle** iletişim kutusunda Veritabanını **Güncelleştir'i seçin.**

   Customers tablosu yerel veritabanı dosyasında oluşturulur.

### <a name="create-the-orders-table"></a>Orders tablosu oluşturma

1. Başka bir tablo ekleyin ve sonra aşağıdaki tabloda her giriş için bir satır ekleyin:

   |Sütun adı|Veri türü|Null'lere izin ver|
   |-----------------|---------------|-----------------|
   |`OrderID`|`int`|False (işaretsiz)|
   |`CustomerID`|`nchar(5)`|False (işaretsiz)|
   |`OrderDate`|`datetime`|True (seçili)|
   |`OrderQuantity`|`int`|True (seçili)|

2. Birincil **anahtar olarak OrderID'i** ayarlayın ve ardından varsayılan satırı silin.

3. Betik bölmesindeki ilk satırı aşağıdaki örnekle eşleşecek şekilde değiştirerek Siparişler tablosunu adlandırın:

   ```sql
   CREATE TABLE [dbo].[Orders]
   ```

4. Dosyanın sol üst köşesinde **güncelleştir'Tablo Tasarımcısı** **seçin.**

5. Veritabanı **Güncelleştirmelerini Önizle** iletişim kutusunda Veritabanını **Güncelleştir'i seçin.**

   Orders tablosu yerel veritabanı dosyasında oluşturulur. Tablolarda Tablolar **düğümünü** genişlet Sunucu Gezgini iki tablo olduğunu görüyorsunuz:

   ![Tablolarda genişletilmiş tablolar Sunucu Gezgini](media/server-explorer-tables-node.png)

### <a name="create-a-foreign-key"></a>Yabancı anahtar oluşturma

1. Orders tablosu için Tablo Tasarımcısı kılavuzun sağ tarafındaki bağlam bölmesinde Yabancı Anahtarlar'a  sağ tıklayın ve Yeni Yabancı Anahtar **Ekle'yi seçin.**

   ![Tablo Tasarımcısı'de Tablo Tasarımcısı anahtarı Visual Studio](../data-tools/media/add-foreign-key.png)

2. Görüntülenen metin kutusunda **ToTable** metnini Customers ile **değiştirin.**

3. T-SQL bölmesinde, son satırı aşağıdaki örnekle eş olacak şekilde güncelleştirin:

   ```sql
   CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
   ```

4. Dosyanın sol üst köşesinde **güncelleştir'Tablo Tasarımcısı** **seçin.**

5. Veritabanı **Güncelleştirmelerini Önizle** iletişim kutusunda Veritabanını **Güncelleştir'i seçin.**

   Yabancı anahtar oluşturulur.

## <a name="populate-the-tables-with-data"></a>Tabloları verilerle doldurmak

1. Sunucu Gezgini  veya **SQL Server Nesne Gezgini** içinde, örnek veritabanı düğümünü genişletin.

2. Tablolar düğümü kısayol menüsünü açın, **Yenile'yi seçin** ve tablolar **düğümünü** genişletin. 

3. Customers tablosu için kısayol menüsünü açın ve Tablo Verilerini **Göster'i seçin.**

4. Bazı müşteriler için istediğiniz verileri ekleyin.

    Müşteri kimliklerini beş karakterli olarak istediğiniz gibi belirtebilirsiniz, ancak en azından bu yordamda daha sonra kullanmak üzere hatırlayabileceğiniz bir kimlik olmalıdır.

5. Orders tablosu kısayol menüsünü açın ve Tablo Verilerini **Göster'i seçin.**

6. Bazı siparişler için veri ekleme.

    > [!IMPORTANT]
    > Tüm sipariş kimliklerinin ve sipariş miktarlarının tamsayı olduğundan ve her müşteri kimliğinin Customers tablosunda **CustomerID** sütununda belirttiğiniz bir değerle eş olduğundan emin olun.

7. Menü çubuğunda Dosya Hepsini **Kaydet'i**  >  **seçin.**

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](accessing-data-in-visual-studio.md)
