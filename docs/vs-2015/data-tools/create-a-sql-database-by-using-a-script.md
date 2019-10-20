---
title: Betik kullanarak SQL veritabanı oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bef7c4be2f38d0f50b2a13c7745cb212204769b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670088"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Betik kullanarak SQL veritabanı oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuzda, [ADO.NET kullanarak basit bir veri uygulaması oluşturmak](../data-tools/create-a-simple-data-application-by-using-adonet.md)için örnek kodu içeren küçük bir veritabanı oluşturmak üzere Visual Studio 'yu kullanırsınız.

 **Bu konuda**

- [Veritabanı şeması içeren bir komut dosyası oluşturma](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)

- [Veritabanı projesi oluşturma ve bir şemayı içeri aktarma](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)

- [Veritabanını dağıtma](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)

## <a name="prerequisites"></a>Prerequisites
 Bu yönergeyi tamamlamak için, SQL Server Express LocalDB veya başka bir SQL veritabanınızın yüklü olması gerekir.

## <a name="CreateScript"></a>Veritabanı şeması içeren bir komut dosyası oluşturma

#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Bir şemayı içeri aktarabileceğiniz bir komut dosyası oluşturmak için

1. @No__t_0 menüsünde, menü çubuğunda **dosya**  > **Yeni**  > **dosyası**' nı seçin.

     **Yeni dosya** iletişim kutusu görüntülenir.

2. **Kategoriler** listesinde **genel**' i seçin.

3. **Şablonlar** listesinde, **SQL dosyası**' nı seçin ve ardından **Aç** düğmesini seçin.

     Transact-SQL Düzenleyicisi açılır.

4. Aşağıdaki Transact-SQL kodunu kopyalayın ve ardından Transact-SQL düzenleyicisine yapıştırın.

    ```
    PRINT N'Creating Sales...';
    GO
    CREATE SCHEMA [Sales]
        AUTHORIZATION [dbo];
    GO
    PRINT N'Creating Sales.Customer...';
    GO
    CREATE TABLE [Sales].[Customer] (
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,
        [CustomerName] NVARCHAR (40) NOT NULL,
        [YTDOrders]    INT           NOT NULL,
        [YTDSales]     INT           NOT NULL
    );
    GO
    PRINT N'Creating Sales.Orders...';
    GO
    CREATE TABLE [Sales].[Orders] (
        [CustomerID] INT      NOT NULL,
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,
        [OrderDate]  DATETIME NOT NULL,
        [FilledDate] DATETIME NULL,
        [Status]     CHAR (1) NOT NULL,
        [Amount]     INT      NOT NULL
    );
    GO
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';
    GO
    ALTER TABLE [Sales].[Customer]
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];
    GO
    PRINT N'Creating Sales.Def_Customer_YTDSales...';
    GO
    ALTER TABLE [Sales].[Customer]
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];
    GO
    PRINT N'Creating Sales.Def_Orders_OrderDate...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];
    GO
    PRINT N'Creating Sales.Def_Orders_Status...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];
    GO
    PRINT N'Creating Sales.PK_Customer_CustID...';
    GO
    ALTER TABLE [Sales].[Customer]
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);
    GO
    PRINT N'Creating Sales.PK_Orders_OrderID...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);
    GO
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;
    GO
    PRINT N'Creating Sales.CK_Orders_FilledDate...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));
    GO
    PRINT N'Creating Sales.CK_Orders_OrderDate...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));
    GO
    PRINT N'Creating Sales.uspCancelOrder...';
    GO
    CREATE PROCEDURE [Sales].[uspCancelOrder]
    @OrderID INT
    AS
    BEGIN
    DECLARE @Delta INT, @CustomerID INT
    BEGIN TRANSACTION
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Orders]
       SET [Status] = 'X'
    WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Customer]
       SET
       YTDOrders = YTDOrders - @Delta
        WHERE [CustomerID] = @CustomerID
    COMMIT TRANSACTION
    END
    GO
    PRINT N'Creating Sales.uspFillOrder...';
    GO
    CREATE PROCEDURE [Sales].[uspFillOrder]
    @OrderID INT, @FilledDate DATETIME
    AS
    BEGIN
    DECLARE @Delta INT, @CustomerID INT
    BEGIN TRANSACTION
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Orders]
       SET [Status] = 'F',
           [FilledDate] = @FilledDate
    WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Customer]
       SET
       YTDSales = YTDSales + @Delta
        WHERE [CustomerID] = @CustomerID
    COMMIT TRANSACTION
    END
    GO
    PRINT N'Creating Sales.uspNewCustomer...';
    GO
    CREATE PROCEDURE [Sales].[uspNewCustomer]
    @CustomerName NVARCHAR (40),
    @CustomerID INT OUTPUT
    AS
    BEGIN
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);
    SET @CustomerID = SCOPE_IDENTITY();
    RETURN @@ERROR
    END
    GO
    PRINT N'Creating Sales.uspPlaceNewOrder...';
    GO
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'
    AS
    BEGIN
    DECLARE @RC INT
    BEGIN TRANSACTION
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)
    SELECT @RC = SCOPE_IDENTITY();
    UPDATE [Sales].[Customer]
       SET
       YTDOrders = YTDOrders + @Amount
        WHERE [CustomerID] = @CustomerID
    COMMIT TRANSACTION
    RETURN @RC
    END
    GO
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]
    @CustomerID INT=0
    AS
    BEGIN
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]
      FROM [Sales].[Customer] AS C
      INNER JOIN [Sales].[Orders] AS O
         ON [O].[CustomerID] = [C].[CustomerID]
      WHERE [C].[CustomerID] = @CustomerID
    END
    GO
    ```

5. Menü çubuğunda **dosya**  > **SqlQuery_1. SQL dosyasını farklı kaydet**' i seçin.

     **Dosyayı farklı kaydet** iletişim kutusu görüntülenir.

6. **Dosya adı** kutusuna `SampleImportScript.sql` girin, dosyayı kaydedeceğiniz konuma göz önünde **saklayın ve Kaydet** düğmesini seçin.

7. Menü çubuğunda **dosya**  > **çözümü kapat**' ı seçin.

     Sonra, bir veritabanı projesi oluşturun ve sonra oluşturduğunuz betikten şemayı içeri aktarın.

## <a name="CreateProject"></a>Veritabanı projesi oluşturma ve bir şemayı içeri aktarma

#### <a name="to-create-a-database-project"></a>Veritabanı projesi oluşturmak için

1. Menü çubuğunda **dosya**  > **Yeni**  > **projesi**' ni seçin.

     **Yeni proje** iletişim kutusu görüntülenir.

2. **Yüklü**altında **Şablonlar** düğümünü genişletin, **diğer diller** düğümünü genişletin, **SQL Server** kategorisini seçin ve **SQL Server veritabanı projesi** şablonunu seçin.

    > [!NOTE]
    > **Diğer diller** düğümü, Visual Studio 'nun tüm yüklemelerinde görünmez.

3. **Ad** kutusuna `Small Database` girin.

4. Henüz seçili değilse, **çözüm için dizin oluştur** onay kutusunu seçin.

5. Henüz temizlenmemişse **kaynak denetimine Ekle** onay kutusunun işaretini kaldırın ve **Tamam** düğmesini seçin.

     Veritabanı projesi oluşturulur ve **Çözüm Gezgini**içinde görüntülenir.

     Sonra, veritabanı şemasını betikten içeri aktarın.

#### <a name="to-import-a-database-schema-from-a-script"></a>Bir komut dosyasından veritabanı şemasını içeri aktarmak için

1. Menü çubuğunda **proje**  >   > **betiği** **içeri aktar** ' ı seçin.

2. **Hoş geldiniz** sayfasında, metni gözden geçirin ve ardından **İleri** düğmesini seçin.

3. **Tek dosya** seçenek düğmesini seçin ve sonra da **tarayıcı** düğmesini seçin.

     **SQL betiği Içeri aktar** iletişim kutusu görünür.

4. Sampleımportscript. SQL dosyasını kaydettiğiniz klasörü açın, dosyayı seçin ve ardından **Aç** düğmesini seçin.

5. **SQL betiği Içeri aktar** iletişim kutusunu kapatmak için **son** düğmesini seçin.

     Betik içeri aktarılır ve komut dosyasının tanımladığı nesneler veritabanı projenize eklenir.

6. Özeti gözden geçirin ve ardından **son** DÜĞMESINE tıklayarak **SQL betik dosyasını içeri aktar** iletişim kutusunu kapatın.

7. **Çözüm Gezgini**' de, projenizin satış, betikleri ve güvenlik klasörlerini genişletin ve. SQL dosyaları içerdiğini doğrulayın.

8. **SQL Server Nesne Gezgini**, veritabanının **Projeler** düğümü altında göründüğünü doğrulayın.

     Bu noktada, veritabanı yalnızca tablolar ve saklı yordamlar gibi sistem nesnelerini içerir. Veritabanını dağıttıktan sonra, komut dosyalarının tanımladıkları Kullanıcı tablolarını ve saklı yordamları içerir.

## <a name="DeployDatabase"></a>Veritabanını dağıtma
 **F5** tuşuna bastığınızda veritabanını varsayılan olarak bir LocalDB veritabanına dağıtır (veya yayımlayabilirsiniz). Projenin Özellikler sayfasını açıp **Hata Ayıkla** sekmesini seçerek ve sonra bağlantı dizesini değiştirerek veritabanını farklı bir konuma dağıtabilirsiniz.
