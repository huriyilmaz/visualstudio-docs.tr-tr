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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299606"
---
# <a name="installing-database-systems-tools-and-samples"></a>Veritabanı sistemlerini, araçları ve örnekleri yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'Nun kendisi, dahili olarak kullandığı bir veritabanı sistemi içermez. Visual Studio 'da veri bağlantılı bir uygulama geliştirmek için, genellikle veritabanı sistemini yerel geliştirme makinenize yüklersiniz ve sonra uygulamayı ve veritabanını, bir üretim ortamına, varsa bu ortama dağıtırsınız. Veritabanı sisteminin .NET uygulamalarından erişilebilir olması ve Visual Studio veri araçları Windows 'da görünür olması için, bir ADO.NET veri sağlayıcısına sahip olması gerekir. .NET uygulamanızda varlık veri modellerini kullanmayı planlıyorsanız, sağlayıcı Entity Framework özel olarak desteklemelidir.     Birçok sağlayıcı, NuGet Paket Yöneticisi veya Visual Studio Galerisi aracılığıyla sunulur.

 SQL geliştirme için, Visual Studio 'da SQL Server Veri Araçları yüklü olduğundan emin olun. **Görünüm** menüsüne tıklayın. SQL Server Nesne Gezgini görmüyorsanız, Denetim Masası ' na gidin ve Visual Studio 'Yu değiştirin. Yükleyicide **Microsoft SQL Server veri araçları**' nı seçin.

 Azure depolama API 'Lerini kullanıyorsanız, üretime dağıtmaya hazırlanana kadar ücretlendirmeden kaçınmak için geliştirme sırasında yerel makinenize Azure Storage öykünücülerini yükleyebilirsiniz. Daha fazla bilgi için bkz. [geliştirme ve test Için Azure depolama öykünücüsünü kullanma](https://azure.microsoft.com/documentation/articles/storage-use-emulator/).

 Aşağıdaki listede, Visual Studio projelerinde kullanılabilecek daha popüler veritabanı sistemleri yer almaktadır. Liste ayrıntılı değildir. Visual Studio Araçları ile derin tümleştirme sağlayan ADO.NET veri sağlayıcıları sunan üçüncü taraf satıcıların bir listesi için bkz. [ADO.NET veri sağlayıcıları](https://msdn.microsoft.com/library/dd363565.aspx).

### <a name="microsoft-sql-server"></a>Microsoft SQL Server
 SQL Server, Microsoft flaggeme veritabanı sunumudur. SQL Server 2016, performans, gelişmiş güvenlik ve zengin, tümleşik raporlama ve analizler sunar. Bu, farklı kullanımlar için tasarlanan çeşitli sürümlerde dağıtılır: yüksek düzeyde ölçeklenebilir, yüksek performanslı iş analizinden tek bir bilgisayarda kullanılmak üzere. SQL Server Express, yeniden dağıtım ve ekleme için uyarlanmış SQL Server tam özellikli bir sürümdür.  LocalDB, uygulamanızın işleminde yapılandırma ve çalıştırma gerektirmeyen SQL Server Express basitleştirilmiş bir sürümüdür. [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)ya da her iki ürünü de indirebilirsiniz. Bu bölümdeki SQL örneklerinin birçoğu SQL Server LocalDB kullanır. SQL Server Management Studio (SSMS), Visual Studio SQL Server Nesne Gezgini sağlandıklarından daha fazla işlevselliğe sahip tek başına bir veritabanı yönetim uygulamasıdır. SSMS 'yi önceki bağlantıdan edinebilirsiniz.

### <a name="oracle"></a>Oracle
 Oracle teknolojisinin ücretli veya ücretsiz bir sürümünü [Oracle Technology Network](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) sayfasından indirebilirsiniz. Entity Framework ve TableAdapters için tasarım zamanı desteği için, [Visual Studio Için Oracle geliştirici araçları](https://www.oracle.com/database/technologies/developer-tools/visual-studio/)gerekir. Oracle Instant Client dahil diğer resmi Oracle ürünleri, NuGet Paket Yöneticisi aracılığıyla kullanılabilir.  Oracle [Online belgelerindeki](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)yönergeleri izleyerek Oracle örnek şemaları indirebilirsiniz.

### <a name="mysql"></a>MySQL
 MySQL, kurumlar ve web sitelerinde yaygın olarak kullanılan, popüler bir açık kaynaklı veritabanı sistemidir. MySQL için karşıdan yüklemeler, Visual Studio için MySQL ve ilgili ürünler [Windows üzerinde MySQL](https://www.mysql.com/why-mysql/windows/)'de yer alır.  Üçüncü taraflar, MySQL için çeşitli Visual Studio uzantıları ve tek başına yönetim uygulamaları sunar. NuGet Paket Yöneticisi 'ndeki tekliflere gözatabilmeniz (**Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet paketlerini yönetme**).

### <a name="postgresql"></a>PostgreSQL
 PostgreSQL, ücretsiz, açık kaynaklı bir nesne ilişkisel veritabanı sistemidir. Windows 'a yüklemek için [PostgreSQL indirme sayfasından](http://www.postgresql.org/download/windows/)indirebilirsiniz.  Kaynak koddan PostgreSQL de oluşturabilirsiniz.  PostgreSQL çekirdek sistemi bir C dili arabirimi içerir. Birçok üçüncü taraf, .NET uygulamalarından PostgreSQL kullanmaya yönelik NuGet paketleri sağlar.  NuGet Paket Yöneticisi 'ndeki tekliflere gözatabilmeniz (**Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet paketlerini yönetme**). Belki de en popüler paket [npgsql.org](http://www.npgsql.org/)tarafından sağlanır.

### <a name="sqlite"></a>SQLite
 SQLite, uygulamanın kendi sürecinde çalışan gömülü bir SQL veritabanı altyapısıdır. Bunu, [SQLite indirme sayfasından](http://www.sqlite.org/download.html)indirebilirsiniz. SQLite için birçok üçüncü taraf NuGet paketi de mevcuttur. NuGet Paket Yöneticisi 'ndeki tekliflere gözatabilmeniz (**Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet paketlerini yönetme**).

### <a name="firebird"></a>Firebird
 Firebird açık kaynaklı bir SQL veritabanı sistemidir. Bunu, [Firebird indirme sayfasından](http://firebirdsql.org/en/downloads/)indirebilirsiniz. NuGet Paket Yöneticisi aracılığıyla bir ADO.NET veri sağlayıcısı mevcuttur.

## <a name="see-also"></a>Ayrıca Bkz.
 [SQL Server ve bileşenlerinin sürümü ve sürümü nasıl belirlenir](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
