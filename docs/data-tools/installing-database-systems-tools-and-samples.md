---
title: Veritabanı uyumluluğu
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cfc3b6c3adc5c51cbbc4bc7d91338fd3595ec372
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586412"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Visual Studio için uyumlu veritabanı sistemleri

Visual Studio 'da veri bağlantılı bir uygulama geliştirmek için, genellikle veritabanı sistemini yerel geliştirme makinenize yüklersiniz ve sonra uygulamayı ve veritabanını, bir üretim ortamına, varsa bu ortama dağıtırsınız. Visual Studio, **veri depolama ve işleme** iş yükünün bir parçası olarak makinenize SQL Server Express LocalDB 'yi yüklüyor. Bu LocalDB örneği, veri bağlantılı uygulamaları hızla ve kolayca geliştirmek için yararlıdır.

Bir veritabanı sisteminin .NET uygulamalarından erişilebilir olması ve Visual Studio veri araçları Windows 'da görünür olması için, bir ADO.NET veri sağlayıcısına sahip olması gerekir. .NET uygulamanızda varlık veri modellerini kullanmayı planlıyorsanız, sağlayıcı Entity Framework özel olarak desteklemelidir. Birçok sağlayıcı, NuGet Paket Yöneticisi veya Visual Studio Market aracılığıyla sunulur.

Azure depolama API 'Lerini kullanıyorsanız, üretime dağıtmaya hazırlanana kadar ücretlendirmeden kaçınmak için geliştirme sırasında yerel makinenize Azure Storage öykünücülerini yükleyebilirsiniz. Daha fazla bilgi için bkz. [geliştirme ve test Için Azure depolama öykünücüsünü kullanma](/azure/storage/common/storage-use-emulator).

Aşağıdaki listede, Visual Studio projelerinde kullanılabilecek daha popüler veritabanı sistemleri yer almaktadır. Liste ayrıntılı değildir. Visual Studio Araçları ile derin tümleştirme sağlayan ADO.NET veri sağlayıcıları sunan üçüncü taraf satıcıların bir listesi için bkz. [ADO.NET veri sağlayıcıları](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server, Microsoft flaggeme veritabanı sunumudur. SQL Server 2016, performans, gelişmiş güvenlik ve zengin, tümleşik raporlama ve analizler sunar. Bu, farklı kullanımlar için tasarlanan çeşitli sürümlerde dağıtılır: yüksek düzeyde ölçeklenebilir, yüksek performanslı iş analizinden tek bir bilgisayarda kullanılmak üzere. SQL Server Express, yeniden dağıtım ve ekleme için uyarlanmış SQL Server tam özellikli bir sürümdür.  LocalDB, uygulamanızın işleminde yapılandırma ve çalıştırma gerektirmeyen SQL Server Express basitleştirilmiş bir sürümüdür. [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)ya da her iki ürünü de indirebilirsiniz. Bu bölümdeki SQL örneklerinin birçoğu SQL Server LocalDB kullanır. SQL Server Management Studio (SSMS), Visual Studio SQL Server Nesne Gezgini sağlandıklarından daha fazla işlevselliğe sahip tek başına bir veritabanı yönetim uygulamasıdır. SSMS 'yi önceki bağlantıdan edinebilirsiniz.

## <a name="oracle"></a>Oracle

Oracle teknolojisinin ücretli veya ücretsiz bir sürümünü [Oracle Technology Network](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html) sayfasından indirebilirsiniz. Entity Framework ve TableAdapters için tasarım zamanı desteği için, [Visual Studio Için Oracle geliştirici araçları](https://www.oracle.com/database/technologies/developer-tools/visual-studio/)gerekir. Oracle Instant Client dahil diğer resmi Oracle ürünleri, NuGet Paket Yöneticisi aracılığıyla kullanılabilir. Oracle [Online belgelerindeki](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)yönergeleri izleyerek Oracle örnek şemaları indirebilirsiniz.

## <a name="mysql"></a>MySQL

MySQL, kurumlar ve web sitelerinde yaygın olarak kullanılan, popüler bir açık kaynaklı veritabanı sistemidir. MySQL için karşıdan yüklemeler, Visual Studio için MySQL ve ilgili ürünler [Windows üzerinde MySQL](https://www.mysql.com/why-mysql/windows/)'de yer alır. Üçüncü taraflar, MySQL için çeşitli Visual Studio uzantıları ve tek başına yönetim uygulamaları sunar. NuGet Paket Yöneticisi 'ndeki tekliflere gözatabilmeniz (**Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet paketlerini yönetme**).

## <a name="postgresql"></a>PostgreSQL

PostgreSQL, ücretsiz, açık kaynaklı bir nesne ilişkisel veritabanı sistemidir. Windows 'a yüklemek için [PostgreSQL indirme sayfasından](https://www.postgresql.org/download/windows/)indirebilirsiniz. Kaynak koddan PostgreSQL de oluşturabilirsiniz. PostgreSQL çekirdek sistemi bir C dili arabirimi içerir. Birçok üçüncü taraf, .NET uygulamalarından PostgreSQL kullanmaya yönelik NuGet paketleri sağlar. NuGet Paket Yöneticisi 'ndeki tekliflere gözatabilmeniz (**Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet paketlerini yönetme**). Belki de en popüler paket, [npgsql.org](http://www.npgsql.org)tarafından sağlanır.

## <a name="sqlite"></a>SQLite

SQLite, uygulamanın kendi sürecinde çalışan gömülü bir SQL veritabanı altyapısıdır. Bunu, [SQLite indirme sayfasından](https://www.sqlite.org/download.html)indirebilirsiniz. SQLite için birçok üçüncü taraf NuGet paketi de mevcuttur. NuGet Paket Yöneticisi 'ndeki tekliflere gözatabilmeniz (**Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet paketlerini yönetme**).

## <a name="firebird"></a>Firebird

Firebird açık kaynaklı bir SQL veritabanı sistemidir. Bunu, [Firebird indirme sayfasından](http://firebirdsql.org/en/downloads/)indirebilirsiniz. NuGet Paket Yöneticisi aracılığıyla bir ADO.NET veri sağlayıcısı mevcuttur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [SQL Server ve bileşenlerinin sürümü ve sürümü nasıl belirlenir](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
