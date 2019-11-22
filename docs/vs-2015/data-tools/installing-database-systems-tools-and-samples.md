---
title: Veritabanı sistemlerini, araçları ve örnekleri yükleme | Microsoft Docs
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
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 091338e411369e40f19e028cd19b6cb2e697718c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299606"
---
# <a name="installing-database-systems-tools-and-samples"></a>Veritabanı sistemlerini, araçları ve örnekleri yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'Nun kendisi, dahili olarak kullandığı bir veritabanı sistemi içermez. Visual Studio'da veri bağlı bir uygulama geliştirmek için genellikle veritabanı sistemi yerel geliştirme makinenize yükleyin ve hazır olduğunuzda uygulama ve veritabanı bir üretim ortamına ardından dağıtın. Veritabanı sisteminin .NET uygulamalarından erişilebilir olması ve Visual Studio veri araçları Windows 'da görünür olması için, bir ADO.NET veri sağlayıcısına sahip olması gerekir. Varlık veri modelleri .NET uygulamanızda kullanmayı planlıyorsanız bir sağlayıcı özellikle Entity Framework desteklemesi gerekir.     Birçok sağlayıcı, NuGet Paket Yöneticisi veya Visual Studio Galerisi aracılığıyla sunulur.

 SQL geliştirme için, Visual Studio 'da SQL Server Veri Araçları yüklü olduğundan emin olun. **Görünüm** menüsüne tıklayın. SQL Server Nesne Gezgini görmüyorsanız, Denetim Masası ' na gidin ve Visual Studio 'Yu değiştirin. Yükleyicide **Microsoft SQL Server veri araçları**' nı seçin.

 Azure depolama API 'Lerini kullanıyorsanız, üretime dağıtmaya hazırlanana kadar ücretlendirmeden kaçınmak için geliştirme sırasında yerel makinenize Azure Storage öykünücülerini yükleyebilirsiniz. Daha fazla bilgi için bkz. [Geliştirme ve Sınama için Azure Storage Öykünücüsünü Kullanma](https://azure.microsoft.com/documentation/articles/storage-use-emulator/).

 Aşağıdaki liste, bazı kullanılabilecek daha popüler veritabanı sistemleri Visual Studio projelerinde içerir. Listede hepsine yer verilmemiştir. Visual Studio Araçları ile derinlemesine tümleştirme sağlayan ADO.NET veri sağlayıcıları üçüncü taraf satıcılarla listesi için bkz. [ADO.NET veri sağlayıcıları](https://msdn.microsoft.com/library/dd363565.aspx).

### <a name="microsoft-sql-server"></a>Microsoft SQL Server
 SQL Server, Microsoft Gemisi veritabanı teklifidir. SQL Server 2016 performansından, Gelişmiş Güvenlik ve zengin, tümleşik raporlama ve analiz sunar. Farklı amaçlarla tasarlanmış çeşitli sürümlerinde sunulur: ile yüksek düzeyde ölçeklenebilir, yüksek performanslı iş analytics, tek bir bilgisayar üzerinde kullanılacak. SQL Server Express'in tam özellikli, bir yeniden dağıtımı ve ekleme için tasarlanmış bir SQL Server sürümüdür.  LocalDB, SQL Server, işlem yapılandırma gerektirmez ve uygulamanızın işlemde çalışan Express, Basitleştirilmiş bir sürümüdür. [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)ya da her iki ürünü de indirebilirsiniz. Bu bölümde yer alan SQL örnekler birçoğu, SQL Server LocalDB kullanın. SQL Server Management Studio (SSMS) Visual Studio SQL Server Nesne Gezgini içinde sağlanan değerinden daha fazla işlevselliği olan bir tek başına veritabanı yönetimi uygulamasıdır. SSMS kullanarak önceki bağlantıdan alabilirsiniz.

### <a name="oracle"></a>Oracle
 Oracle teknolojisinin ücretli veya ücretsiz bir sürümünü [Oracle Technology Network](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) sayfasından indirebilirsiniz. Entity Framework ve TableAdapters için tasarım zamanı desteği için, [Visual Studio Için Oracle geliştirici araçları](https://www.oracle.com/database/technologies/developer-tools/visual-studio/)gerekir. Oracle anlık istemci gibi diğer resmi Oracle ürünleri için NuGet Paket Yöneticisi aracılığıyla kullanılabilir.  Oracle [Online belgelerindeki](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)yönergeleri izleyerek Oracle örnek şemaları indirebilirsiniz.

### <a name="mysql"></a>MySQL
 MySQL, kurumlar ve Web siteleri yaygın olarak kullanılan bir popüler açık kaynak veritabanı sistemidir. Visual Studio ve ilgili ürünler için MySQL yüklemeleri için MySQL ndadır [Windows üzerinde MySQL](https://www.mysql.com/why-mysql/windows/).  Üçüncü taraflara, çeşitli Visual Studio uzantıları ve MySQL için tek başına Yönetim uygulamaları sunar. NuGet Paket Yöneticisi'nde tekliflerini göz atabilirsiniz (**Araçları** > **NuGet Paket Yöneticisi** > **çözüm için NuGet paketlerini Yönet**) .

### <a name="postgresql"></a>PostgreSQL
 PostgreSQL, ücretsiz, açık kaynaklı bir nesne ilişkisel veritabanı sistemidir. Windows üzerinde yüklemek için buradan indirebilirsiniz [PostgreSQL indirme sayfası](http://www.postgresql.org/download/windows/).  Ayrıca, kaynak kodundan PostgreSQL oluşturabilirsiniz.  PostgreSQL çekirdek sistem C dili arabirimi içerir. Çok sayıda üçüncü taraflara, .NET uygulamalarından kullanılarak PostgreSQL için NuGet paketlerini sağlar.  NuGet Paket Yöneticisi'nde tekliflerini göz atabilirsiniz (**Araçları** > **NuGet Paket Yöneticisi** > **çözüm için NuGet paketlerini Yönet**) . Belki de en popüler paket [npgsql.org](http://www.npgsql.org/)tarafından sağlanır.

### <a name="sqlite"></a>SQLite
 SQLite uygulamanın kendi işlemde çalışan katıştırılmış bir SQL veritabanı altyapısıdır. Buradan indirebileceğiniz [SQLite indirme sayfası](http://www.sqlite.org/download.html). SQLite için çok sayıda üçüncü taraf NuGet paketlerini de mevcuttur. NuGet Paket Yöneticisi'nde tekliflerini göz atabilirsiniz (**Araçları** > **NuGet Paket Yöneticisi** > **çözüm için NuGet paketlerini Yönet**) .

### <a name="firebird"></a>Firebird
 Firebird bir açık kaynak SQL veritabanı sistemidir. Buradan indirebileceğiniz [Firebird indirme sayfası](http://firebirdsql.org/en/downloads/). Bir ADO.NET veri sağlayıcı, NuGet Paket Yöneticisi aracılığıyla kullanılabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [SQL Server ve bileşenlerinin sürümünü ve belirleme](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
