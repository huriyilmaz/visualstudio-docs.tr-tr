---
title: Veritabanı oluşturma ve tablo ekleme
description: Veritabanına tablo ve yabancı anahtar eklemek için veritabanına tablo ekleme hakkında bilgi Tablo Tasarımcısı öğretici Visual Studio. Ayrıca grafik arabirimi aracılığıyla veri eklemeyi de gösterir.
ms.date: 10/15/2021
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
ms.openlocfilehash: fc0557ae483456d1df4252e57558561b6583bb94
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133978413"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Veritabanı oluşturma ve veritabanına tablo Visual Studio

yerel veritabanı Visual Studio oluşturmak ve güncelleştirmek için YerelDB'de SQL Server Express kullanabilirsiniz. Veritabanı oluşturmak için transact-SQL deyimlerini SQL Server Nesne Gezgini **araç** penceresinde Visual Studio. Bu konu başlığında, bir *.mdf* dosyası oluşturarak tablo ve anahtar eklemek için Tablo Tasarımcısı.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için.NET masaüstü geliştirme  ve Veri depolama ile işleme iş yüklerinin Visual Studio.  Bunları yüklemek için, **Visual Studio Yükleyicisi** ve değiştirmek  **istediğiniz** uygulamanın sürümünün yanındaki Değiştir (veya Daha  >  Fazla Değiştir) Visual Studio 'yi seçin.

> [!NOTE]
> Bu makaledeki yordamlar yalnızca .NET Core .NET Framework Windows Forms projeleri için değil, Windows Forms projeleri için geçerlidir.

## <a name="create-a-project-and-a-local-database-file"></a>Proje ve yerel veritabanı dosyası oluşturma

1. Yeni bir Windows **Forms Uygulaması (.NET Framework) projesi** oluşturun ve **SampleDatabaseWalkthrough olarak ad girin.**

2. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

3. Öğe şablonları listesinde aşağı kaydırın ve Hizmet tabanlı **Veritabanı'ı seçin.**

   :::moniker range=">=vs-2022"
   ![Hizmet tabanlı > yeni öğe ekleme](media/vs-2022/visual-studio-add-service-database.png)
   :::moniker-end
   :::moniker range="<=vs-2019"
   ![Hizmet tabanlı > yeni öğe ekleme](media/raddata-vsitemtemplates.png)
   :::moniker-end

4. Veritabanına **SampleDatabase adını ve** ardından Ekle'ye **tıklayın.**

### <a name="add-a-data-source"></a>Veri kaynağı ekleme

1. Veri **Kaynakları penceresi açık** değilse, Shift Alt D tuşuna basarak veya menü çubuğunda Diğer Veri +  +    >    >  **Windows'ı** seçerek açın.

1. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'yi seçin.**

   :::moniker range=">=vs-2022"
   ![Visual Studio'a yeni veri kaynağı ekleme](media/vs-2022/add-new-data-source.png)
   :::moniker-end
   :::moniker range="<=vs-2019"
   ![Visual Studio'a yeni veri kaynağı ekleme](media/add-new-data-source.png)
   :::moniker-end

   Veri **Kaynağı Yapılandırma Sihirbazı** açılır.

1. Veri Kaynağı **Türü Seçin sayfasında Veritabanı'ı** ve **ardından Sonraki'yi** **seçin.**

1. Veritabanı **Modeli Seçin sayfasında,** varsayılan değeri **(Veri Kümesi)** kabul etmek için Sonraki'yi seçin.

1. Veri **Bağlantınızı Seçin sayfasında,** açılan listeden **SampleDatabase.mdf** dosyasını seçin ve ardından Sonraki'yi **seçin.**

1. Bağlantı **Dizesini Uygulama Yapılandırma Dosyasına Kaydet sayfasında, Sonraki'yi** **seçin.**

1. Veritabanı **Nesnelerinizi Seçin sayfasında,** veritabanında nesne olmadığını söyleyen bir ileti görüntülenir. **Son**’u seçin.

### <a name="view-properties-of-the-data-connection"></a>Veri bağlantısının özelliklerini görüntüleme

*SampleDatabase.mdf* dosyasının bağlantı dizesini, veri bağlantısının Özellikler penceresi açarak görüntüebilirsiniz:

- Görünüm **penceresi**  >  **SQL Server Nesne Gezgini'ı** **seçerek SQL Server Nesne Gezgini** açın. **(localdb)\MSSQLLocalDB** Veritabanları'ı  >  **genişletin** ve *SampleDatabase.mdf'ye* sağ tıklayın ve Özellikler'i **seçin.**

- Alternatif olarak, bu **pencere**  >  **Sunucu Gezgini** görünüm seçeneğini de 2009'a 3000000000000000000000000000000000000000000 Veri Özellikler penceresi düğümünü **genişleterek,** *SampleDatabase.mdf'ye* sağ tıklar ve ardından Özellikler'i seçerek bağlantıyı **açın.**

  > [!TIP]
  > Veri Bağlantıları düğümünü genişlete değilken SampleDatabase.mdf bağlantısı listelenmiyorsa,  Bağlan araç çubuğundaki Veritabanına Sunucu Gezgini seçin. Bağlantı Ekle **iletişim kutusunda,** Veri kaynağı **altında Microsoft SQL Server** Veritabanı Dosyası'nın seçili olduğundan emin olun ve sampleDatabase.mdf dosyasına gidin ve dosyayı seçin. Tamam'ı seçerek bağlantıyı eklemeyi **bitirin.**

## <a name="create-tables-and-keys-by-using-table-designer"></a>Tablo ve anahtar oluşturmak için Tablo Tasarımcısı

Bu bölümde, her tabloda bir birincil anahtar ve birkaç örnek veri satırı olmak için iki tablo oluşturacaksınız. Ayrıca bir tablodaki kayıtların diğer tablodaki kayıtlara nasıl karşılık gelen olduğunu belirtmek için bir yabancı anahtar da oluşturabilirsiniz.

### <a name="create-the-customers-table"></a>Customers tablosu oluşturma

1. Bu **Sunucu Gezgini,** Veri **Bağlantıları düğümünü** ve ardından **SampleDatabase.mdf düğümünü** genişletin.

   Veri Bağlantıları düğümünü genişlete değilken SampleDatabase.mdf bağlantısı listelenmiyorsa,  Bağlan araç çubuğundaki Veritabanına Sunucu Gezgini seçin. Bağlantı Ekle **iletişim kutusunda,** Veri kaynağı **altında Microsoft SQL Server** Veritabanı Dosyası'nın seçili olduğundan emin olun ve sampleDatabase.mdf dosyasına gidin ve dosyayı seçin. Tamam'ı seçerek bağlantıyı eklemeyi **bitirin.**

2. Tablolar'a sağ **tıklayın ve** Yeni Tablo **Ekle'yi seçin.**

   Bu Tablo Tasarımcısı açılır ve oluşturmakta olan tabloda tek bir sütunu temsil eden bir varsayılan satıra sahip bir kılavuz görüntülenir. Kılavuza satırlar ekleyerek, tabloda sütunlar ekleyeceksiniz.

3. Kılavuzda, aşağıdaki girişlerin her biri için bir satır ekleyin:

   |Sütun adı|Veri türü|Null'lere izin ver|
   |-----------------|---------------|-----------------|
   |`CustomerID`|`nchar(5)`|False (işaretsiz)|
   |`CompanyName`|`nvarchar(50)`|False (işaretsiz)|
   |`ContactName`|`nvarchar (50)`|True (seçili)|
   |`Phone`|`nvarchar (24)`|True (seçili)|

4. Satıra sağ tıklayın `CustomerID` ve Ardından Birincil Anahtarı **Ayarla'yı seçin.**

5. Varsayılan satıra ( ) sağ tıklayın ve `Id` Sil'i **seçin.**

6. Betik bölmesindeki ilk satırı aşağıdaki örnekle eşleşecek şekilde değiştirerek Müşteriler tablosunu adlandırın:

   ```sql
   CREATE TABLE [dbo].[Customers]
   ```

7. Customers tablosuna bir dizin kısıtlaması ekleyin. Satırın sonuna virgül ekleyin ve ardından `Phone` kapatma parantezi öncesinde aşağıdaki örneği ekleyin:

   ```sql
   CONSTRAINT [PK_Customers] PRIMARY KEY ([CustomerID])
   ```

   Şuna benzer bir şey görmeniz gerekir:

   :::moniker range=">=vs-2022"
   ![Tablo Tasarımcısı tablosuyla birlikte](media/vs-2022/table-designer.png)
   :::moniker-end
   :::moniker range="<=vs-2019"
   ![Tablo Tasarımcısı tablosuyla birlikte](media/table-designer.png)
   :::moniker-end

8. öğesinin sol üst köşesinde **Güncelleştir'Tablo Tasarımcısı seçin** **veya** Shift Alt U  + **tuşlarına** + **basın.**

9. Veritabanı **Güncelleştirmelerini Önizle** iletişim kutusunda Veritabanını **Güncelleştir'i seçin.**

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

4. Customers tablosuna bir dizin kısıtlaması ekleyin. Satırın sonuna virgül ekleyin ve ardından `OrderQuantity` kapatma parantezi öncesinde aşağıdaki örneği ekleyin:

   ```sql
   CONSTRAINT [PK_Orders] PRIMARY KEY ([OrderId])
   ```

5. Dosyanın sol üst köşesinde Güncelleştir'i **Tablo Tasarımcısı** veya **Shift** Alt U  +  + **tuşlarına basın.**

6. Veritabanı **Güncelleştirmelerini Önizle** iletişim kutusunda Veritabanını **Güncelleştir'i seçin.**

   Orders tablosu yerel veritabanı dosyasında oluşturulur. Tablo kümesinde **Tablolar** düğümünü genişlet Sunucu Gezgini iki tabloyla karşı karşıdan bağlantı noktası oluşturursanız:

   :::moniker range=">=vs-2022"
   ![Tablolarda genişletilmiş tablolar Sunucu Gezgini](media/vs-2022/server-explorer-tables-node.png)
   :::moniker-end
   :::moniker range="<=vs-2019"
   ![Tablolarda genişletilmiş tablolar Sunucu Gezgini](media/server-explorer-tables-node.png)
   :::moniker-end

   Bunu görmüyorsanız Yenile araç çubuğu **düğmesine** basın.

### <a name="create-a-foreign-key"></a>Yabancı anahtar oluşturma

1. Siparişler tablosu için Tablo Tasarımcısı kılavuzun sağ tarafındaki bağlam bölmesinde Yabancı Anahtarlar'a sağ tıklayın ve Yeni Yabancı Anahtar **Ekle'yi seçin.** 

   :::moniker range=">=vs-2022"
   ![Visual Studio'de Tablo Tasarımcısı anahtarı Visual Studio](media/vs-2022/add-foreign-key.png)
   :::moniker-end
   :::moniker range="<=vs-2019"
   ![Visual Studio'de Tablo Tasarımcısı anahtarı Visual Studio](../data-tools/media/add-foreign-key.png)
   :::moniker-end

2. Görüntülenen metin kutusunda **ToTable** metnini Customers ile **değiştirin.**

3. T-SQL bölmesinde, son satırı aşağıdaki örnekle eş olacak şekilde güncelleştirin:

   ```sql
   CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
   ```

4. üst köşesindeki sol üst köşede güncelleştir ( **Shift**  + **Alt** + **U)** seçeneğini Tablo Tasarımcısı seçin.

5. Veritabanı **Güncelleştirmelerini Önizle** iletişim kutusunda Veritabanını **Güncelleştir'i seçin.**

   Yabancı anahtar oluşturulur.

## <a name="populate-the-tables-with-data"></a>Tabloları verilerle doldurmak

1. Uygulama **Sunucu Gezgini** **SQL Server Nesne Gezgini,** örnek veritabanı düğümünü genişletin.

2. Tablolar düğümünün kısayol menüsünü **açın,** Yenile'yi **seçin** ve tablolar **düğümünü** genişletin.

3. Müşteriler tablosu için kısayol menüsünü açın ve Verileri **Görüntüle'yi seçin.**

4. Bazı müşteriler için istediğiniz verileri ekleyin.

    Müşteri kimliklerini beş karakterli olarak istediğiniz gibi belirtebilirsiniz, ancak en azından bu yordamda daha sonra kullanmak üzere hatırlayabileceğiniz bir kimlik olmalıdır.

5. Orders tablosu için kısayol menüsünü açın ve Tablo Verilerini **Göster'i seçin.**

6. Bazı siparişler için veri ekleme. Her satırı girerken veritabanına kaydedilir.

    > [!IMPORTANT]
    > Tüm sipariş kimliklerinin ve sipariş miktarlarının tamsayı olduğundan ve her müşteri kimliğinin Customers tablosunda **CustomerID** sütununda belirttiğiniz değerle eş olduğundan emin olun.

Tebrikler! Artık tablo oluşturma, bunları yabancı anahtarla bağlama ve veri ekleme hakkında bilgi edinebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](accessing-data-in-visual-studio.md)
