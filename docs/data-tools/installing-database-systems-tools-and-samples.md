---
title: Veritabanı uyumluluğu
description: Microsoft SQL Server, Oracle, MySQL, PostgreSQL, SQLite ve Firebird gibi Visual Studio için uyumlu veritabanı sistemlerini gözden geçirme.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631286"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Visual Studio için uyumlu veritabanı sistemleri

Visual Studio'de veri bağlantılı bir uygulama geliştirmek için veritabanı sistemini yerel geliştirme makinenize yüklemeniz ve ardından uygulamayı ve veritabanını hazır olduğunda bir üretim ortamına dağıtmanız gerekir. Visual Studio, SQL Server Express depolama ve işleme iş yükünün bir parçası olarak **makinenize localDB'yi** yüklür. Bu LocalDB örneği, verilere bağlı uygulamaları hızlı ve kolay bir şekilde geliştirmek için kullanışlıdır.

Bir veritabanı sisteminin .NET uygulamalarından erişilebilir olması ve veri araçları Visual Studio görünür olması için bir veri ADO.NET olmalıdır. Varlık veri modellerini .NET Entity Framework kullanmayı planlıyorsanız sağlayıcının özel olarak bu verileri desteklemesi gerekir. Birçok sağlayıcı, NuGet Paket Yöneticisi Market üzerinden Visual Studio sunulur.

Azure depolama API'lerini kullanıyorsanız üretim ortamına dağıtım yapmaya hazır olana kadar ücret ödememek için geliştirme sırasında yerel makinenize Azure depolama öykünücülerini yükleyin. Daha fazla bilgi için [bkz. Azure Depolama Emulator geliştirme ve test için kullanma.](/azure/storage/common/storage-use-emulator)

Aşağıdaki listede, Visual Studio projelerinde kullanılmaktadır. Liste kapsamlı değildir. Veri Sağlayıcıları ile derin tümleştirme sağlayan ADO.NET veri sağlayıcıları sunan üçüncü taraf satıcıların Visual Studio listesi için [bkz. ADO.NET Sağlayıcıları.](/dotnet/framework/data/adonet/data-providers)

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server, Microsoft'un en önemli veritabanı teklifidir. SQL Server 2016' da çığır açan performans, gelişmiş güvenlik ve zengin, tümleşik raporlama ve analiz özellikleri sunar. Yüksek oranda ölçeklenebilir, yüksek performanslı iş analizinden tek bir bilgisayarda kullanmak üzere farklı kullanımlar için tasarlanmış çeşitli sürümler sunar. SQL Server Express, yeniden dağıtım ve SQL Server uyarlanmış tam özellikli bir yayındır.  LocalDB, yapılandırma gerektir SQL Server Express ve uygulamanın sürecinde çalışan bir uygulamanın basitleştirilmiş bir sürümüdir. ürünlerinden birini veya her ikisini de indirme [SQL Server Express indirebilirsiniz.](https://www.microsoft.com/sql-server/sql-server-editions-express) Bu bölümdeki SQL örneklerin çoğu localDB SQL Server kullanır. SQL Server Management Studio (SSMS), tek başına veritabanı yönetim uygulamasıdır ve bu uygulamanın içinde sağlanandan daha fazla işlevselliğe Visual Studio SQL Server Nesne Gezgini. Önceki bağlantıdan SSMS'ye ulaşabilirsiniz.

## <a name="oracle"></a>Oracle

Oracle veritabanının ücretli veya ücretsiz bir sürümünü Oracle teknoloji ağı [sayfasından indirebilirsiniz.](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html) Entity Framework ve TableAdapter'lar için tasarım zamanı desteği için, Geliştirici araçları [Oracle Visual Studio.](https://www.oracle.com/database/technologies/developer-tools/visual-studio/) Oracle Instant Client da dahil olmak üzere diğer resmi Oracle ürünleri, oracle NuGet Paket Yöneticisi. Oracle çevrimiçi belgelerinde yer alan yönergeleri izleyerek Oracle örnek [şemalarını indirebilirsiniz.](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)

## <a name="mysql"></a>MySQL

MySQL, kuruluşlarda ve web sitelerinde yaygın olarak kullanılan popüler bir açık kaynak veritabanı sistemidir. MySQL, Visual Studio için MySQL ve ilgili ürünler için [indirmeler, Windows.](https://www.mysql.com/why-mysql/windows/) Üçüncü taraflar, MySQL Visual Studio yönetim uygulamaları ve farklı uzantılar sunan çeşitli uzantılar sunar. Tekliflere NuGet Paket Yöneticisi **(** Araçlar NuGet Paket Yöneticisi Çözüm  >  **için NuGet**  >  **Paketleri) göz atabilirsiniz.**

## <a name="postgresql"></a>PostgreSQL

PostgreSQL, ücretsiz ve açık kaynaklı bir nesne ilişkisel veritabanı sistemidir. Bunu bir Windows yüklemek için [PostgreSQL indirme sayfasından indirebilirsiniz.](https://www.postgresql.org/download/windows/) PostgreSQL'i kaynak koddan da derlemek için de kullanılabilirsiniz. PostgreSQL çekirdek sistemi bir C dil arabirimi içerir. Birçok üçüncü taraf, .NET NuGet PostgreSQL kullanmaya uygun paketler sağlar. Tekliflere NuGet Paket Yöneticisi **(** Araçlar NuGet Paket Yöneticisi Çözüm  >  **için NuGet**  >  **Paketleri) göz atabilirsiniz.** Belki de en popüler paket, [npgsql.org.](http://www.npgsql.org)

## <a name="sqlite"></a>SQLite

SQLite, uygulamanın SQL çalışan tümleşik bir veritabanı altyapısıdır. SQLite indirme [sayfasından indirebilirsiniz.](https://www.sqlite.org/download.html) SQLite için NuGet üçüncü taraf yazılım paketi de mevcuttur. Tekliflere NuGet Paket Yöneticisi **(** Araçlar NuGet Paket Yöneticisi Çözüm  >  **için NuGet**  >  **Paketleri) göz atabilirsiniz.**

## <a name="firebird"></a>Firebird

Firebird, açık kaynak bir SQL sistemidir. Firebird indirme [sayfasından indirebilirsiniz.](http://firebirdsql.org/en/downloads/) Veri ADO.NET sağlayıcısı, veri sağlayıcısı NuGet Paket Yöneticisi.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [SQL Server ve bileşenlerinin sürümünü belirleme](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
