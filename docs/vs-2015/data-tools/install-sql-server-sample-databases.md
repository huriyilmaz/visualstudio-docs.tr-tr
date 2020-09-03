---
title: Örnek veritabanlarını SQL Server yüklemesi | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3915351bff74f35ceb5fc462cb29dfd2f322fb6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299634"
---
# <a name="install-sql-server-sample-databases"></a>SQL Server örnek veritabanlarını yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnek veritabanları SQL ve LINQ sorguları, veri bağlama, Entity Framework modelleme vb. ile denemeler yapmak için yararlıdır.  Her veritabanı ürününün kendi örnek veritabanları vardır. Northwind ve AdventureWorks, örnek veritabanlarından oluşan iki popüler SQL Server.

 **AdventureWorks** , SQL Server ürünleri için sunulan geçerli örnek veritabanıdır. [CodePlex 'Teki AdventureWorks sayfasından](https://archive.codeplex.com/?p=msftdbprodsamples)bir. mdf dosyası olarak indirebilirsiniz. Burada, veritabanının normal ve hafif (LT) sürümleri mevcuttur. Çoğu senaryoda, LT sürümü daha az karmaşık olduğu için tercih edilir.

 **Northwind** , birçok yıl boyunca kullanılan görece basit bir SQL Server veritabanıdır. [CodePlex 'Teki Northwind veritabanı sayfasından](https://northwinddatabase.codeplex.com/)bir. bak dosyası olarak indirebilirsiniz. İzin sorunlarından kaçınmak için, dosyayı Kullanıcı klasörünüzün altında olmayan yeni bir klasöre ayıklayın.

#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Visual Studio 'da bir. bak dosyasından bir veritabanını geri yüklemek için

1. Microsoft SQL Server bir veritabanını yedeklerken sonuç bir. bak dosyasıdır. . Bak dosyasını bir veritabanı dosyası olarak yeniden kullanılabilir hale getirmek için *geri yüklenmesi*gerekir. Ana menüde SQL Server Nesne Gezgini **görüntüle**' yi seçin  >  **SQL Server Object Explorer**. Bunu görmüyorsanız, yüklemeniz gerekebilir. **Denetim Masası**  >  **Programlar ve Özellikler**' e gidin, Microsoft Visual Studio 2015 ' i bulun ve **Değiştir** düğmesine tıklayın. Yüklü bileşenlerin listesi Yükleyici penceresinde göründüğünde, **SQL Server Nesne Gezgini** onay kutusunu seçin ve yükleme işlemine devam edin.

2. SQL Server Nesne Gezgini, herhangi bir SQL Server veritabanı altyapısına (örneğin, LocalDB) sağ tıklayın ve**Yeni sorgu**' yı seçin.

     ![Yeni sorgu SQL Server Nesne Gezgini](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "radveri SQL Server Nesne Gezgini yeni sorgu")

3. İlk olarak,. bak dosyasının içindeki veritabanının ve günlük dosyalarının mantıksal adlarına ihtiyacınız vardır. Bunu almak için, bu sorguyu SQL sorgu Düzenleyicisi 'ne girin ve ardından pencerenin üst kısmındaki yeşil **çalıştırma** düğmesini seçin. Dosya yolunu,. bak dosyasını işaret etmek için gerekiyorsa değiştirin.

    ```
    RESTORE FILELISTONLY
    FROM DISK = 'C:\nw\northwind.bak'
    GO
    ```

     Sonuçlar penceresinde görünen mantıksal adları yazın.  Northwind veritabanı için, iki mantıksal ad Northwind ve Northwind_log.

4. Şimdi veritabanını oluşturmak için bu sorguyu çalıştırın. Northwind için kendi kaynak ve hedef yollarınızı, mantıksal veritabanı adlarınızı ve fiziksel dosya adlarını uygun şekilde değiştirin. . Mdf ve. ldf dosya uzantılarını koruyun.

    ```
    RESTORE DATABASE Northwind
    FROM DISK = 'c:\nw\northwind.bak'
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'
    ```

5. SQL Server Nesne Gezgini, **veritabanları** düğümüne sağ tıklayın ve Northwind veritabanı düğümünü görmeniz gerekir. Aksi takdirde, veritabanlarına sağ tıklayıp **Yeni veritabanı Ekle**' yi seçin. Yeni oluşturduğunuz. mdf dosyasının adını ve konumunu girin.

6. Veritabanı artık Visual Studio 'da bir veri kaynağı olarak kullanıma hazırdır.

#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>SQL Server Management Studio bir veritabanını bir. bak dosyasından geri yüklemek için

1. İndirme sitesinden SQL Server Management Studio indirin.

2. SSMS **Nesne Gezgini** penceresinde **veritabanları** düğümüne sağ tıklayın,**veritabanını geri yükle**' yi seçin ve. bak dosyasının konumunu belirtin.

     ![SSMS geri yükleme veritabanı](../data-tools/media/raddata-ssms-restore-database.png "radveri SSMS veritabanını geri yükleme")
