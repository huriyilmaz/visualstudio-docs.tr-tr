---
title: Visual Studio’da verilerle çalışma
description: Verilerle çalışma Visual Studio. Yerel makineler, LAN'ler veya genel ya da özel bulutlar üzerinden diğer veritabanı ürünleri veya hizmetlerinde yer alan verilere bağlanan uygulamalar oluşturun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b6f79c38b599a66a9609bd88399f075f54f59dd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631641"
---
# <a name="work-with-data-in-visual-studio"></a>Visual Studio’da verilerle çalışma

Bu Visual Studio, neredeyse tüm veritabanı ürünlerinde veya hizmetlerinde, herhangi bir biçimde, her yerde, yerel bir makinede, yerel bir ağ üzerinde ya da genel, özel veya hibrit bir buluttaki verilere bağlanan uygulamalar oluşturabilirsiniz.

JavaScript, Python, PHP, Ruby veya C++ uygulamaları için kitaplıkları edinerek ve kod yazarak diğer her şeyi gibi verilere bağlanabilirsiniz. .NET uygulamaları için Visual Studio kaynakları keşfetmek, verileri bellekte depolamak ve işlemek için nesne modelleri oluşturmak ve verileri kullanıcı arabirimine bağlamak için kullanabileceğiniz araçlar sağlar. Microsoft Azure.NET, Java, Node.js, PHP, Python, Ruby ve mobil uygulamalar için SDK'lar ve Azure Visual Studio'a bağlanmak için Depolama.

::: moniker range="vs-2017"
Aşağıdaki listelerde, veritabanı ve depolama sistemlerinden yalnızca birkaçı Visual Studio. En [Microsoft Azure,](https://azure.microsoft.com/) temel alınan veri deposuna tüm sağlama ve yönetim hizmetlerini içeren veri hizmetleridir. Visual Studio  [2017'de](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Azure geliştirme iş yükü, Doğrudan Azure veri depoları ile çalışma Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Aşağıdaki listelerde, veritabanı ve depolama sistemlerinden yalnızca birkaçı Visual Studio. En [Microsoft Azure,](https://azure.microsoft.com/) temel alınan veri deposuna tüm sağlama ve yönetim hizmetlerini içeren veri hizmetleridir. [Visual Studio 2019'daki](https://visualstudio.microsoft.com/downloads) **Azure** geliştirme iş yükü, doğrudan azure veri depoları ile çalışma Visual Studio.
::: moniker-end

![Azure geliştirme iş yükü](media/azure-development-workload.png)

Burada listelenen diğer SQL ve NoSQL veritabanı ürünlerinin çoğu yerel makinede, yerel bir ağ üzerinde veya sanal makinede Microsoft Azure barındırabilirsiniz. Veritabanını bir sanal makinede Microsoft Azure, veritabanının kendisini yönetmek sizin sorumluluğundadır.

**Microsoft Azure**

- SQL Veritabanı
- Azure Cosmos DB
- Depolama (bloblar, tablolar, kuyruklar, dosyalar)
- SQL Veri Ambarı
- SQL Server Stretch Database
- StorSimple
- Ve daha fazlası...

**SQL**

- SQL Server 2005-2016 (Express ve LocalDB içerir)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- Ve daha fazlası...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB|
- Db
- VelocityDB
- Ve daha fazlası...

::: moniker range="vs-2017"

Birçok veritabanı satıcı ve üçüncü taraf, Visual Studio tarafından NuGet destekler. Teklif tekliflerini nuget.org NuGet Paket Yöneticisi Visual Studio ( Araçlar NuGet Paket Yöneticisi Çözüm için NuGet  >    >  **Paketlerini Yönet) aracılığıyla keşfedebilirsiniz.** Diğer veritabanı ürünleri, Visual Studio olarak tümleştirildi. [Visual Studio Market'te](https://marketplace.visualstudio.com/) veya Araçlar Uzantıları ve Güncelleştirmeler'e giderek ve iletişim kutusunun sol bölmesinde Çevrimiçi'ni seçerek bu tekliflere  >   göz atabilirsiniz.  Daha fazla bilgi için bkz. Visual Studio için [uyumlu veritabanı sistemleri.](../data-tools/installing-database-systems-tools-and-samples.md)

::: moniker-end

::: moniker range=">=vs-2019"

Birçok veritabanı satıcı ve üçüncü taraf, Visual Studio tarafından NuGet destekler. Teklif tekliflerini nuget.org NuGet Paket Yöneticisi Visual Studio ( Araçlar NuGet Paket Yöneticisi Çözüm için NuGet  >    >  **Paketlerini Yönet) aracılığıyla keşfedebilirsiniz.** Diğer veritabanı ürünleri, Visual Studio olarak tümleştirildi. Bu tekliflere Visual Studio [Market'te](https://marketplace.visualstudio.com/) veya Uzantı yönetimi Uzantıları'na giderek ve iletişim kutusunun sol bölmesinde Çevrimiçi'ni   >   seçerek göz atabilirsiniz.  Daha fazla bilgi için bkz. Visual Studio için [uyumlu veritabanı sistemleri.](../data-tools/installing-database-systems-tools-and-samples.md)

::: moniker-end

> [!NOTE]
> SQL Server 2005 için genişletilmiş destek 12 Nisan 2016'da sona erdi. Visual Studio 2015 ve sonrasındaki veri araçlarının 2005'te SQL Server garanti edilemez. Daha fazla bilgi için [bkz. 2005'te SQL Server sonu duyurusu.](https://www.microsoft.com/sql-server/sql-server-2005)

## <a name="net-languages"></a>.NET dilleri

.NET Core dahil olmak üzere tüm .NET veri erişimi, ADO.NET, hem ilişkisel hem de ilişkisel olmayan herhangi bir veri kaynağına erişmek için bir arabirim tanımlayan bir sınıf kümesi olan ADO.NET'a dayalıdır. Visual Studio veritabanlarına bağlanmanıza, verileri işlemeye ve verileri kullanıcıya ADO.NET yardımcı olmak için ADO.NET ile birlikte çalışan çeşitli araçlar ve tasarımcılar vardır. Bu bölümdeki belgelerde bu araçların nasıl kullanımı açıklanmıştır. Ayrıca doğrudan komut nesnelerini kullanarak ADO.NET programlandırabilirsiniz. Api'leri doğrudan çağırma hakkında ADO.NET için bkz. [ADO.NET.](/dotnet/framework/data/adonet/index)

Veri erişimi belgeleri için ASP.NET [sitenin Verilerle](https://www.asp.net/web-forms/overview/presenting-and-managing-data) Çalışma ASP.NET bakın. ASP.NET MVC ile Entity Framework öğreticisi için [bkz. MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)kullanarak Entity Framework 6 Code First ile Başlarken.

C# Windows platform (UWP) uygulamaları Visual Basic Azure .NET için Microsoft Azure SDK ve diğer Azure Depolama erişmek için bu Depolama kullanabilir. Windows. Web.HttpClient sınıfı herhangi bir RESTful hizmetiyle iletişimi sağlar. Daha fazla bilgi için, [bkz. How to connect to an HTTP server using Windows. Web.Http](/previous-versions/windows/apps/dn469430(v=win.10)).

Yerel makinede veri depolama için önerilen yaklaşım, uygulamayla aynı işlemde çalışan SQLite kullanmaktır. Nesne ilişkisel eşleme (ORM) katmanı gerekli ise, bu katmanı Entity Framework. Daha fazla bilgi için [bkz. Geliştirici](/windows/uwp/data-access/index) Merkezi'Windows veri erişimi.

Azure hizmetlerine bağlanıyorsanız, en son Azure SDK araçlarını [indirmeyi emin olun.](https://azure.microsoft.com/downloads/)

### <a name="data-providers"></a>Veri sağlayıcılar

Bir veritabanının bir veritabanı tarafından ADO.NET için özel  bir ADO.NET veri sağlayıcısına sahip olması veya başka bir ODBC ya da OLE DB gerekir. Microsoft, ADO.NET [ürünleri için SQL Server](/dotnet/framework/data/adonet/ado-net-overview) veri sağlayıcılarının listesinin yanı sıra ODBC ve OLE DB sağlar.

### <a name="data-modeling"></a>Veri modelleme

.NET'te, verileri bir veri kaynağından alan verileri modellemek ve bellekte manipüle etmeye üç seçenek vardır:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Tercih edilen Microsoft ORM teknolojisi. İlişkisel verilere karşı birinci sınıf .NET nesneleri olarak program yapmak için bunu kullanabilirsiniz. Yeni uygulamalar için model gerektiğinde varsayılan ilk seçenek bu olacaktır. Temel alınan hizmet sağlayıcısından özel ADO.NET gerektirir.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Önceki nesil bir nesne ilişkisel eşleyici. Daha az karmaşık senaryolar için iyi çalışır, ancak artık etkin geliştirme aşamasında değildir.

[Veri kümeleri](../data-tools/dataset-tools-in-visual-studio.md) Üç modelleme teknolojisi arasında en eski olan. Birincil olarak çok miktarda veri işlemeye veya karmaşık sorgular ya da dönüşümler gerçekleştirmeye çalışmayarak "veriler üzerinde formlar" uygulamalarının hızlı bir şekilde geliştirilmesi için tasarlanmıştır. DataSet nesnesi, .NET nesnelerinden çok daha fazla veritabanı nesnesine SQL DataTable ve DataRow nesnelerinden oluşur. Veri kaynaklarını temel alan SQL basit uygulamalar için veri kümeleri yine de iyi bir seçenek olabilir.

Bu teknolojilerden herhangi birini kullanmak gerekli değildir. Özellikle performansın kritik olduğu bazı senaryolarda, veritabanından okumak ve ihtiyacınız olan değerleri List gibi bir koleksiyon nesnesine kopyalamak için bir DataReader nesnesi \<T> kullanabilirsiniz.

## <a name="native-c"></a>Yerel C++

SQL Server'a ® C++ uygulamalarının çoğu durumda SQL Server [için Microsoft® ODBC Sürücüsü 13.1'i](https://www.microsoft.com/download/details.aspx?id=53339) kullanmaları gerekir. Sunucular bağlı ise, OLE DB gereklidir ve bunun için de [SQL Server Native Client.](/sql/relational-databases/native-client/sql-server-native-client) ODBC veya sürücülerini doğrudan kullanarak [diğer](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017&preserve-view=true) veritabanlarına OLE DB erişebilirsiniz. ODBC geçerli standart veritabanı arabirimidir, ancak çoğu veritabanı sistemi ODBC arabirimi aracılığıyla erişilemedi özel işlevler sağlar. OLE DB, hala desteklenen ancak yeni uygulamalar için önerilmez olan eski bir COM veri erişimi teknolojisidir. Daha fazla bilgi için [bkz. Visual C++.](/cpp/data/data-access-in-cpp)

REST hizmetlerini kullanan C++ programları [C++ REST SDK'sı kullanabilir.](https://github.com/Microsoft/cpprestsdk)

Microsoft Azure Depolama ile Microsoft Azure Depolama C++ [programları.](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP)

Veri &mdash; Visual Studio, C++ için bir ORM katmanı sağlamaz. [ODB,](https://www.codesynthesis.com/products/odb/) C++ için popüler bir açık kaynak ORM'dir.

C++ uygulamalarıyla veritabanlarına bağlanma hakkında daha fazla bilgi edinmek için [bkz. C++ Visual Studio araçlarına bağlanma.](../data-tools/visual-studio-data-tools-for-cpp.md) Eski Visual C++ veri erişimi teknolojileri hakkında daha fazla bilgi için bkz. [veri erişimi](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[Visual Studio JavaScript](/scripting/javascript/javascript-language-reference) , platformlar arası uygulamalar, UWP uygulamaları, bulut hizmetleri, web siteleri ve web uygulamaları oluşturmak için birinci sınıf bir dildir. en sevdiğiniz JavaScript kitaplıklarını ve veritabanı ürünlerini yüklemek için Visual Studio içinden bower, grer, Gulp, npm ve NuGet kullanabilirsiniz. azure [web sitesinden](https://azure.microsoft.com/)sdk 'ları indirerek azure depolama ve hizmetlerine Bağlan. Edge.js, ADO.NET veri kaynaklarına sunucu tarafı JavaScript (Node.js) bağlayan bir kitaplıktır.

## <a name="python"></a>Python

python uygulamaları oluşturmak için [Visual Studio python desteği '](../python/overview-of-python-tools-for-visual-studio.md) ni yükler. Azure belgelerinin, aşağıdakiler de dahil olmak üzere verilere bağlanmaya yönelik çeşitli öğreticiler vardır:

- [Azure 'da docgo ve SQL Veritabanı](/azure/app-service/app-service-web-get-started-python)
- [Azure 'da docgo ve MySQL](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- [Bloblar](/azure/storage/blobs/storage-quickstart-blobs-python), [dosyalar](/azure/storage/files/storage-python-how-to-use-file-storage), [Kuyruklar](/azure/storage/queues/storage-python-how-to-use-queue-storage)ve [Tablolar (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python)ile çalışın.

## <a name="related-topics"></a>İlgili konular

[MICROSOFT AI platformu](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash; Cortana Analytics Suite ve Nesnelerin İnterneti desteği dahil olmak üzere Microsoft akıllı bulutuna bir giriş sağlar.

[Microsoft Azure Depolama](/azure/storage/) &mdash; azure Depolama ve azure blob 'ları, tabloları, kuyrukları ve dosyalarını kullanarak uygulama oluşturmayı açıklar.

[Azure SQL Veritabanı](/azure/sql-database/) &mdash; bir hizmet olarak ilişkisel veritabanı olan Azure SQL Veritabanı nasıl bağlanabileceğinizi açıklar.

[SQL Server Veri Araçları](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; Verilere bağlı uygulamaların ve veritabanlarının tasarımını, araştırmasını, test edilmesini ve dağıtılmasını kolaylaştıran araçları açıklar.

[ADO.net](/dotnet/framework/data/adonet/index) &mdash; ADO.NET mimarisini ve uygulama verilerini yönetmek ve veri kaynaklarıyla ve XML ile etkileşime geçmek için ADO.NET sınıflarının nasıl kullanılacağını açıklar.

[ADO.NET Entity Framework](/ef/ef6/) &mdash; Geliştiricilerin doğrudan ilişkisel bir veritabanına karşı kavramsal bir modelde programlama yapmasına izin veren veri uygulamalarının nasıl oluşturulacağını açıklar.

[WCF Veri Hizmetleri 4,5](/dotnet/framework/data/wcf/index) &mdash; [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]Web 'de veya [Açık Veri Protokolü 'Nü (OData)](https://www.odata.org/)uygulayan bir intranette veri hizmetleri dağıtmak için ' nin nasıl kullanılacağını açıklar.

[Office çözümlerinde veri](../vsto/data-in-office-solutions.md) &mdash; Office çözümlerinde verilerin nasıl çalıştığını açıklayan konuların bağlantılarını içerir. Burada şema tabanlı programlama, verileri önbelleğe alma ve sunucu tarafında veri erişimi hakkında bilgiler bulunur.

[LINQ (dil Ile tümleşik sorgu)](/dotnet/csharp/linq/) &mdash; C# ve Visual Basic yerleşik sorgu özelliklerini ve ilişkisel veritabanlarını, XML belgelerini, veri kümelerini ve bellek içi koleksiyonları sorgulamak için ortak modeli açıklar.

[Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) &mdash; XML araçları XML verileriyle çalışmayı, XSLT 'yi, .NET XML özelliklerini ve XML sorgusunun mimarisini açıklar.

[XML belgeleri ve verileri](/dotnet/standard/data/xml/index) &mdash; .NET 'teki XML belgeleriyle ve verilerle çalışan kapsamlı ve tümleşik bir sınıf kümesine genel bakış sunar.