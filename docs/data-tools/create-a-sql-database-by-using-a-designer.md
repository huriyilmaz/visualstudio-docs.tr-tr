---
title: Veritabanı dosyası oluşturma ve tablo tasarımcısını kullanma
description: Visual Studio Tablo Tasarımcısı kullanarak bir veritabanına nasıl tablo ve yabancı anahtar ekleneceğini açıklayan öğretici. Ayrıca grafik arabiriminden nasıl veri ekleneceğini gösterir.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037154"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Visual Studio bir veritabanı oluşturun ve tablo ekleyin

Visual Studio, SQL Server Express localdb 'de yerel bir veritabanı dosyası oluşturmak ve güncelleştirmek için kullanabilirsiniz. ayrıca, Visual Studio içindeki **SQL Server Nesne Gezgini** araç penceresinde Transact-SQL deyimlerini yürüterek bir veritabanı oluşturabilirsiniz. Bu konu başlığında, Tablo Tasarımcısı kullanarak bir *. mdf* dosyası oluşturacağız ve tablo ve anahtar ekleyeceğiz.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için, **.net masaüstü geliştirme** ve **veri depolama ve işleme** iş yüklerinin Visual Studio ' de yüklü olması gerekir. bunları yüklemek için **Visual Studio Yükleyicisi** açın ve değiştirmek istediğiniz Visual Studio sürümünün yanındaki **değiştir** ' i (veya **daha fazla**  >  **değiştir**) seçin.

> [!NOTE]
> bu makaledeki yordamlar, .net Core Windows Forms projelerine değil, yalnızca .NET Framework Windows Forms projelerine uygulanır.

## <a name="create-a-project-and-a-local-database-file"></a>Bir proje ve yerel veritabanı dosyası oluşturma

1. yeni bir **Windows Forms App (.NET Framework)** projesi oluşturun ve **sampledatabasewalkthrough** olarak adlandırın.

2. menü çubuğunda **Project**  >  **yeni öğe ekle**' yi seçin.

3. Öğe şablonları listesinde, aşağı kaydırın ve **hizmet tabanlı veritabanı**' nı seçin.

   ![Öğe şablonları iletişim kutusu](../data-tools/media/raddata-vsitemtemplates.png)

4. Veritabanı **örnekveritabanını** adlandırın ve ardından **Ekle**' ye tıklayın.

### <a name="add-a-data-source"></a>Veri kaynağı ekleme

1. **veri kaynakları** penceresi açık değilse, **shıft** + **Alt** + **D** tuşlarına basarak veya   >  menü çubuğunda **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçerek açın.

1. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' yi seçin.

   ![Visual Studio yeni veri kaynağı Ekle](media/add-new-data-source.png)

   **Veri kaynağı Yapılandırma Sihirbazı** açılır.

1. **Veri kaynağı türü seç** sayfasında, **veritabanı** ' nı seçin ve ardından **İleri**' yi seçin.

1. **Veritabanı modeli Seç** sayfasında, Varsayılanı kabul etmek için **İleri** ' yi seçin (veri kümesi).

1. **Veri bağlantınızı seçin** sayfasında, açılan listeden **SampleDatabase. mdf** dosyasını seçin ve ardından **İleri**' yi seçin.

1. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri**' yi seçin.

1. **Veritabanı nesnelerinizi seçin** sayfasında, veritabanının herhangi bir nesne içermediğini belirten bir ileti görürsünüz. **Son**’u seçin.

### <a name="view-properties-of-the-data-connection"></a>Veri bağlantısının özelliklerini görüntüle

Veri bağlantısının Özellikler penceresi açarak *SampleDatabase. mdf* dosyası için bağlantı dizesini görüntüleyebilirsiniz:

-   >  **SQL Server Nesne Gezgini** penceresini açmak için **SQL Server Nesne Gezgini** görüntüle ' yi seçin. **(LocalDB) \mssqllocaldb**  >  **veritabanları**' nı genişletin ve *SampleDatabase. mdf* ' ye sağ tıklayıp **Özellikler**' i seçin.

- Alternatif olarak,   >  Bu pencere zaten açık değilse **Sunucu Gezgini** görüntüle ' yi seçebilirsiniz. **Veri bağlantıları** düğümünü genişleterek, *SampleDatabase. mdf*' ye sağ tıklayıp **Özellikler**' i seçerek Özellikler penceresi açın.

  > [!TIP]
  > veri bağlantıları düğümünü genişletemiyorum veya sampledatabase. mdf bağlantısı listelenmiyorsa, Sunucu Gezgini araç çubuğunda **veritabanına Bağlan** düğmesini seçin. **bağlantı ekle** iletişim kutusunda, **veri kaynağı** altında **Microsoft SQL Server veritabanı dosyası** ' nın seçildiğinden emin olun ve sampledatabase. mdf dosyasına gidip seçin. **Tamam ' ı** seçerek bağlantıyı eklemeyi tamamlayın.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Tablo Tasarımcısı kullanarak tablo ve anahtarlar oluşturma

Bu bölümde, iki tablo, her tabloda bir birincil anahtar ve birkaç örnek veri satırı oluşturacaksınız. Ayrıca, bir tablodaki kayıtların diğer tablodaki kayıtlara nasıl karşılık geldiğini belirtmek için bir yabancı anahtar da oluşturacaksınız.

### <a name="create-the-customers-table"></a>Müşteriler tablosunu oluşturma

1. **Sunucu Gezgini**' de, **veri bağlantıları** düğümünü genişletin ve **SampleDatabase. mdf** düğümünü genişletin.

   veri bağlantıları düğümünü genişletemiyorum veya sampledatabase. mdf bağlantısı listelenmiyorsa, Sunucu Gezgini araç çubuğunda **veritabanına Bağlan** düğmesini seçin. **bağlantı ekle** iletişim kutusunda, **veri kaynağı** altında **Microsoft SQL Server veritabanı dosyası** ' nın seçildiğinden emin olun ve sampledatabase. mdf dosyasına gidip seçin. **Tamam ' ı** seçerek bağlantıyı eklemeyi tamamlayın.

2. **Tablolar** ' a sağ tıklayıp **Yeni Tablo Ekle**' yi seçin.

   Tablo Tasarımcısı açılır ve oluşturmakta olduğunuz tablodaki tek bir sütunu temsil eden bir varsayılan satır içeren bir kılavuz gösterir. Kılavuza satırlar ekleyerek, tabloda sütunlar ekleyeceksiniz.

3. Kılavuzda, aşağıdaki girişlerin her biri için bir satır ekleyin:

   |Sütun adı|Veri türü|Null'lere izin ver|
   |-----------------|---------------|-----------------|
   |`CustomerID`|`nchar(5)`|False (işaretsiz)|
   |`CompanyName`|`nvarchar(50)`|False (işaretsiz)|
   |`ContactName`|`nvarchar (50)`|True (seçili)|
   |`Phone`|`nvarchar (24)`|True (seçili)|

4. Satıra sağ tıklayın `CustomerID` ve ardından **birincil anahtarı ayarla**' yı seçin.

5. Varsayılan satıra () sağ tıklayın `Id` ve ardından **Sil**' i seçin.

6. Betik bölmesindeki ilk satırı aşağıdaki örnekle eşleşecek şekilde değiştirerek Müşteriler tablosunu adlandırın:

   ```sql
   CREATE TABLE [dbo].[Customers]
   ```

   Şuna benzer bir şey görmeniz gerekir:

   ![Tablo Tasarımcısı](../data-tools/media/table-designer.png)

7. **Tablo Tasarımcısı** sol üst köşesinde **Güncelleştir**' i seçin.

8. **Veritabanı güncelleştirmelerini Önizle** Iletişim kutusunda **veritabanını güncelleştir**' i seçin.

   Müşteriler tablosu, yerel veritabanı dosyasında oluşturulur.

### <a name="create-the-orders-table"></a>Siparişler tablosu oluşturma

1. Başka bir tablo ekleyin ve sonra aşağıdaki tabloda her giriş için bir satır ekleyin:

   |Sütun adı|Veri türü|Null'lere izin ver|
   |-----------------|---------------|-----------------|
   |`OrderID`|`int`|False (işaretsiz)|
   |`CustomerID`|`nchar(5)`|False (işaretsiz)|
   |`OrderDate`|`datetime`|True (seçili)|
   |`OrderQuantity`|`int`|True (seçili)|

2. **OrderID** öğesini birincil anahtar olarak ayarlayın ve ardından varsayılan satırı silin.

3. Betik bölmesindeki ilk satırı aşağıdaki örnekle eşleşecek şekilde değiştirerek Siparişler tablosunu adlandırın:

   ```sql
   CREATE TABLE [dbo].[Orders]
   ```

4. **Tablo Tasarımcısı** sol üst köşesinde **Güncelleştir**' i seçin.

5. **Veritabanı güncelleştirmelerini Önizle** Iletişim kutusunda **veritabanını güncelleştir**' i seçin.

   Siparişler tablosu, yerel veritabanı dosyasında oluşturulur. Sunucu Gezgini içindeki **Tables** düğümünü genişletirseniz, iki tablo görürsünüz:

   ![Sunucu Gezgini Genişletilmiş Tablolar düğümü](media/server-explorer-tables-node.png)

### <a name="create-a-foreign-key"></a>Yabancı anahtar oluştur

1. Siparişler tablosu için Tablo Tasarımcısı kılavuzunun sağ tarafındaki bağlam bölmesinde **yabancı anahtarlar** ' a sağ tıklayın ve **yeni yabancı anahtar Ekle**' yi seçin.

   ![Visual Studio Tablo Tasarımcısı yabancı anahtar ekleme](../data-tools/media/add-foreign-key.png)

2. Görüntülenen metin kutusunda, Text **ToTable** değerini **Customers** ile değiştirin.

3. T-SQL bölmesinde son satırı aşağıdaki örnekle eşleşecek şekilde güncelleştirin:

   ```sql
   CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
   ```

4. **Tablo Tasarımcısı** sol üst köşesinde **Güncelleştir**' i seçin.

5. **Veritabanı güncelleştirmelerini Önizle** Iletişim kutusunda **veritabanını güncelleştir**' i seçin.

   Yabancı anahtar oluşturulur.

## <a name="populate-the-tables-with-data"></a>Tabloları verilerle doldurma

1. **Sunucu Gezgini** veya **SQL Server Nesne Gezgini**, örnek veritabanının düğümünü genişletin.

2. **Tablolar** düğümü için kısayol menüsünü açın, **Yenile**' yi seçin ve **Tablolar** düğümünü genişletin.

3. Müşteriler tablosu için kısayol menüsünü açın ve ardından **tablo verilerini göster**' i seçin.

4. Bazı müşteriler için istediğiniz verileri ekleyin.

    Müşteri kimliklerini beş karakterli olarak istediğiniz gibi belirtebilirsiniz, ancak en azından bu yordamda daha sonra kullanmak üzere hatırlayabileceğiniz bir kimlik olmalıdır.

5. Siparişler tablosu için kısayol menüsünü açın ve ardından **tablo verilerini göster**' i seçin.

6. Bazı siparişler için veri ekleyin.

    > [!IMPORTANT]
    > Tüm sipariş kimlikleri ve sipariş miktarları ' nın tamsayılar olduğundan ve her müşteri KIMLIĞININ Customers tablosunun **CustomerID** sütununda belirtilen bir değerle eşleştiğinden emin olun.

7. Menü çubuğunda **Dosya**  >  **Tümünü Kaydet**' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](accessing-data-in-visual-studio.md)
