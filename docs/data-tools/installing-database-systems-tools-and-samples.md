---
title: Veritabanı uyumluluğu
description: Microsoft SQL Server, Oracle, MySQL, postgresql, SQLite ve firebird gibi Visual Studio için uyumlu veritabanı sistemlerini gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6ccbf0866022e6e602938d2a5f86f8374eb73c89
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091207"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Visual Studio için uyumlu veritabanı sistemleri

Visual Studio ' de veriye bağlı bir uygulama geliştirmek için, genellikle veritabanı sistemini yerel geliştirme makinenize yüklersiniz ve ardından uygulamayı ve veritabanını, bir üretim ortamına, hazırlık sırasında dağıtırsınız. Visual Studio, **veri depolama ve işleme** iş yükünün bir parçası olarak makinenizde SQL Server Express localdb 'yi yüklüyor. Bu LocalDB örneği, veri bağlantılı uygulamaları hızla ve kolayca geliştirmek için yararlıdır.

bir veritabanı sisteminin .net uygulamalarından erişilebilir olması ve Visual Studio veri araçları penceresinde görünür olması için, bir ADO.NET veri sağlayıcısına sahip olması gerekir. .NET uygulamanızda varlık veri modellerini kullanmayı planlıyorsanız, sağlayıcı Entity Framework özel olarak desteklemelidir. birçok sağlayıcı, NuGet Paket Yöneticisi veya Visual Studio market aracılığıyla sunulur.

Azure depolama API 'Lerini kullanıyorsanız, üretime dağıtmaya hazırlanana kadar ücretlendirmeden kaçınmak için geliştirme sırasında yerel makinenize Azure Storage öykünücülerini yükleyebilirsiniz. daha fazla bilgi için bkz. [geliştirme ve test için Azure Depolama Emulator kullanma](/azure/storage/common/storage-use-emulator).

aşağıdaki liste, Visual Studio projelerinde kullanılabilecek daha popüler veritabanı sistemlerinden bazılarını içerir. Liste ayrıntılı değildir. Visual Studio araçları ile derin tümleştirme sağlayan ADO.NET veri sağlayıcıları sunan üçüncü taraf satıcıların bir listesi için bkz. [ADO.NET veri sağlayıcıları](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server, Microsoft flaggeme veritabanı sunumudur. SQL Server 2016, performans, gelişmiş güvenlik ve zengin, tümleşik raporlama ve analizler sunar. Bu, farklı kullanımlar için tasarlanan çeşitli sürümlerde dağıtılır: yüksek düzeyde ölçeklenebilir, yüksek performanslı iş analizinden tek bir bilgisayarda kullanılmak üzere. SQL Server Express, yeniden dağıtım ve ekleme için uyarlanmış SQL Server tam özellikli bir sürümdür.  localdb, uygulamanızın işleminde yapılandırma ve çalıştırma gerektirmeyen SQL Server Express basitleştirilmiş bir sürümüdür. [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)ya da her iki ürünü de indirebilirsiniz. bu bölümdeki SQL örneklerin çoğu SQL Server localdb kullanır. SQL Server Management Studio (ssms), Visual Studio SQL Server Nesne Gezgini tarafından sağlandıklarından daha fazla işlevselliğe sahip tek başına bir veritabanı yönetim uygulamasıdır. SSMS 'yi önceki bağlantıdan edinebilirsiniz.

## <a name="oracle"></a>Oracle

Oracle teknolojisinin ücretli veya ücretsiz bir sürümünü [Oracle Technology Network](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html) sayfasından indirebilirsiniz. Entity Framework ve TableAdapters için tasarım zamanı desteği için, [Visual Studio Için Oracle geliştirici araçlarına](https://www.oracle.com/database/technologies/developer-tools/visual-studio/)ihtiyacınız olacaktır. oracle ınstant Client dahil diğer resmi oracle ürünleri, NuGet Paket Yöneticisi üzerinden kullanılabilir. Oracle [Online belgelerindeki](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)yönergeleri izleyerek Oracle örnek şemaları indirebilirsiniz.

## <a name="mysql"></a>MySQL

MySQL, kurumlar ve web sitelerinde yaygın olarak kullanılan, popüler bir açık kaynaklı veritabanı sistemidir. mysql için karşıdan yüklemeler, Visual Studio için mysql ve ilgili ürünler [Windows üzerinde mysql](https://www.mysql.com/why-mysql/windows/)' dir. üçüncü taraflar, MySQL için çeşitli Visual Studio uzantıları ve tek başına yönetim uygulamaları sunar. NuGet Paket Yöneticisi tekliflere (**araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet paketleri yönetme**) gidebilirsiniz.

## <a name="postgresql"></a>PostgreSQL

PostgreSQL, ücretsiz, açık kaynaklı bir nesne ilişkisel veritabanı sistemidir. Windows yüklemek için [postgresql indirme sayfasından](https://www.postgresql.org/download/windows/)indirebilirsiniz. Kaynak koddan PostgreSQL de oluşturabilirsiniz. PostgreSQL çekirdek sistemi bir C dili arabirimi içerir. birçok üçüncü taraf, .net uygulamalarından postgresql kullanmaya yönelik NuGet paketler sağlar. NuGet Paket Yöneticisi tekliflere (**araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet paketleri yönetme**) gidebilirsiniz. Belki de en popüler paket, [npgsql.org](http://www.npgsql.org)tarafından sağlanır.

## <a name="sqlite"></a>SQLite

SQLite, uygulamanın kendi sürecinde çalışan gömülü bir SQL veritabanı altyapısıdır. Bunu, [SQLite indirme sayfasından](https://www.sqlite.org/download.html)indirebilirsiniz. SQLite için birçok üçüncü taraf NuGet paketi de mevcuttur. NuGet Paket Yöneticisi tekliflere (**araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet paketleri yönetme**) gidebilirsiniz.

## <a name="firebird"></a>Firebird

firebird açık kaynaklı bir SQL veritabanı sistemidir. Bunu, [Firebird indirme sayfasından](http://firebirdsql.org/en/downloads/)indirebilirsiniz. ADO.NET veri sağlayıcısı NuGet Paket Yöneticisi ile kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [SQL Server ve bileşenlerinin sürümü ve sürümü nasıl belirlenir](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
