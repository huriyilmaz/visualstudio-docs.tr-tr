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
ms.openlocfilehash: afa6bd926490a34f0878a50f4d9108e5a3fceb0e
ms.sourcegitcommit: aff49629012f4d5fa07c75ea0ca5bf53d28aa173
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2021
ms.locfileid: "131662522"
---
# <a name="work-with-data-in-visual-studio"></a>Visual Studio’da verilerle çalışma

Bu Visual Studio, neredeyse tüm veritabanı ürünlerinde veya hizmetlerinde, herhangi bir biçimde, her yerde, yerel makinede, yerel bir ağ üzerinde ya da genel, özel veya hibrit bir buluttaki verilere bağlanan uygulamalar oluşturabilirsiniz.

JavaScript, Python, PHP, Ruby veya C++ uygulamaları için kitaplıkları edinerek ve kod yazarak diğer her şeyi gibi verilere bağlanabilirsiniz. .NET uygulamaları için Visual Studio kaynakları keşfetmek, verileri bellekte depolamak ve işlemek için nesne modelleri oluşturmak ve verileri kullanıcı arabirimine bağlamak için kullanabileceğiniz araçlar sağlar. Microsoft Azure.NET, Java, Node.js, PHP, Python, Ruby ve mobil uygulamalar için SDK'lar ve Azure Visual Studio'a bağlanmak için Depolama.

::: moniker range="vs-2017"
Aşağıdaki listelerde, veritabanı ve depolama sistemlerinden yalnızca birkaçı aşağıda Visual Studio. Bu [Microsoft Azure,](https://azure.microsoft.com/) temel alınan veri deposu için tüm sağlama ve yönetim hizmetlerini içeren veri hizmetleridir. Visual Studio  [2017'de](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Azure geliştirme iş yükü, Doğrudan Azure veri depoları ile çalışma Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Aşağıdaki listelerde, veritabanı ve depolama sistemlerinden yalnızca birkaçı aşağıda Visual Studio. Bu [Microsoft Azure,](https://azure.microsoft.com/) temel alınan veri deposu için tüm sağlama ve yönetim hizmetlerini içeren veri hizmetleridir. [Visual Studio 2019'daki](https://visualstudio.microsoft.com/downloads) **Azure** geliştirme iş yükü, Doğrudan Azure veri depoları ile çalışma Visual Studio.
::: moniker-end

![Azure geliştirme iş yükü](media/azure-development-workload.png)

Burada listelenen diğer SQL noSQL veritabanı ürünlerinin çoğu yerel bir makinede, yerel ağ üzerinde veya sanal makinede Microsoft Azure barındırabilirsiniz. Veritabanını bir sanal makinede Microsoft Azure, veritabanının kendisini yönetmek sizin sorumluluğundadır.

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

Birçok veritabanı satıcı ve üçüncü taraf, Visual Studio paketlerle NuGet destekler. Teklif tekliflerini nuget.org NuGet Paket Yöneticisi Visual Studio ( Araçlar NuGet Paket Yöneticisi Çözüm için NuGet  >    >  **Paketlerini Yönet) aracılığıyla keşfedebilirsiniz.** Diğer veritabanı ürünleri, Visual Studio olarak tümleştirildi. [Visual Studio Market'te](https://marketplace.visualstudio.com/) veya Araçlar Uzantıları ve Güncelleştirmeler'e giderek ve iletişim kutusunun sol bölmesinde Çevrimiçi'ni seçerek bu tekliflere  >   göz atabilirsiniz.  Daha fazla bilgi için bkz. Visual Studio için [uyumlu veritabanı sistemleri.](../data-tools/installing-database-systems-tools-and-samples.md)

::: moniker-end

::: moniker range=">=vs-2019"

Birçok veritabanı satıcı ve üçüncü taraf, Visual Studio paketlerle NuGet destekler. Teklif tekliflerini nuget.org NuGet Paket Yöneticisi Visual Studio ( Araçlar NuGet Paket Yöneticisi Çözüm için NuGet  >    >  **Paketlerini Yönet) aracılığıyla keşfedebilirsiniz.** Diğer veritabanı ürünleri, Visual Studio olarak tümleştirildi. [Visual Studio Market'te](https://marketplace.visualstudio.com/) veya Uzantı yönetimi uzantıları'na giderek ve iletişim kutusunun sol bölmesinde Çevrimiçi'ni seçerek bu tekliflere  >   göz atabilirsiniz.  Daha fazla bilgi için bkz. Visual Studio için [uyumlu veritabanı sistemleri.](../data-tools/installing-database-systems-tools-and-samples.md)

::: moniker-end

> [!NOTE]
> SQL Server 2005 için genişletilmiş destek 12 Nisan 2016'da sona erdi. Visual Studio 2015 ve sonrasındaki veri araçlarının 2005'te SQL Server garanti edilemez. Daha fazla bilgi için [bkz. 2005 için SQL Server sonu duyurusu.](https://www.microsoft.com/sql-server/sql-server-2005)

## <a name="net-languages"></a>.NET dilleri

.NET Core dahil olmak üzere tüm .NET veri erişimi, ADO.NET, hem ilişkisel hem de ilişkisel olmayan herhangi bir veri kaynağına erişmek için bir arabirim tanımlayan bir sınıf kümesi olan ADO.NET'a dayalıdır. Visual Studio veritabanlarına bağlanmanıza, verileri işlemeye ve verileri kullanıcıya ADO.NET yardımcı olmak için ADO.NET ile birlikte çalışan çeşitli araçlar ve tasarımcılar vardır. Bu bölümdeki belgelerde bu araçların nasıl kullanımı açıklanmıştır. Ayrıca doğrudan komut nesnelerini kullanarak ADO.NET programlandırabilirsiniz. Api'leri doğrudan çağırma hakkında ADO.NET için bkz. [ADO.NET.](/dotnet/framework/data/adonet/index)

Veri erişimi belgeleri için ASP.NET [sitenin Verilerle](https://www.asp.net/web-forms/overview/presenting-and-managing-data) Çalışma ASP.NET bakın. ASP.NET MVC ile Entity Framework öğreticisi için [bkz. MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)Entity Framework 6 Başlarken ile Code First.

C# Windows platform (UWP) uygulamaları Visual Basic Azure .NET için Microsoft Azure SDK ve diğer Azure Depolama erişmek için bu Depolama kullanabilir. Aşağıdaki Windows. Web.HttpClient sınıfı herhangi bir RESTful hizmetiyle iletişimi sağlar. Daha fazla bilgi için, [bkz. How to connect to an HTTP server using Windows. Web.Http](/previous-versions/windows/apps/dn469430(v=win.10)).

Yerel makinede veri depolama için önerilen yaklaşım, uygulamayla aynı işlemde çalışan SQLite kullanmaktır. Nesne ilişkisel eşleme (ORM) katmanı gerekli ise, bu katmanı Entity Framework. Daha fazla bilgi için [bkz. Geliştirici](/windows/uwp/data-access/index) Merkezi'Windows veri erişimi.

Azure hizmetlerine bağlanıyorsanız, en son Azure SDK araçlarını [indirmeyi emin olun.](https://azure.microsoft.com/downloads/)

### <a name="data-providers"></a>Veri sağlayıcılar

Veritabanının bir veritabanı tarafından ADO.NET için özel bir ADO.NET  veri sağlayıcısına sahip olması veya başka bir ODBC ya da OLE DB gerekir. Microsoft, SQL Server [için](/dotnet/framework/data/adonet/ado-net-overview) ADO.NET sağlayıcılarının listesinin yanı sıra ODBC ve OLE DB sağlar.

::: moniker range=">=vs-2019"
> [!NOTE]
>OLEDB veya ODBC veri sağlayıcılarını kullanarak veritabanlarına bağlanmak için Visual Studio kullanıyorsanız, Visual Studio 2022'den önceki Visual Studio sürümlerinin 32 bit işlemler olduğunu fark etmek gerekir. Başka bir ifadeyle, Visual Studio bazı veri araçları yalnızca 32 bit veri sağlayıcılarını kullanarak OLEDB veya ODBC veritabanlarına bağlanabilecektir. Buna Microsoft Access 32 bit OLEDB veri sağlayıcısının yanı sıra diğer üçüncü taraf 32 bit sağlayıcılar dahildir.
>
>Veritabanlarına bağlanmak için Visual Studio 2022 kullanıyorsanız, Visual Studio 2022'nin 64 bitlik bir işlem olduğunu fark etmek gerekir. Bu, Visual Studio veri araçlarından bazılarının 32 bit veri sağlayıcılarını kullanarak OLEDB veya ODBC veritabanlarına bağlanamayacakları anlamına gelir.
>
>OLEDB veya ODBC veritabanlarına bağlı 32 bit uygulamaları sürdürmeye devam ediyorsanız, uygulamayı yine de 2022'de Visual Studio çalıştırabilirsiniz. Ancak, Sunucu Gezgini, Veri Kaynağı Sihirbazı veya Veri Kümesi Tasarımcısı gibi Visual Studio Veri Araçları'nın herhangi birini kullanıyorsanız, Visual Studio'nin hala 32 bit işlem olan önceki bir sürümünü kullansanız gerekir. 32 bitlik Visual Studio olan son sürüm, 2019'Visual Studio sürümüdür.
>
>Projeyi 64 bitlik bir işlem olacak şekilde dönüştürmeyi planlıyorsanız, Access Connectivity Engine (ACE) olarak da adlandırılan 64 bit Microsoft Access Veritabanı Altyapısı'nın kullanılması önerilir. Daha fazla OLE DB için lütfen Jet ve ODBC için [sağlayıcının 32 bit sürümlerine sahip](/office/troubleshoot/access/jet-odbc-driver-available-32-bit-version) olduğunu lütfen unutmayın.

::: moniker-end

### <a name="data-modeling"></a>Veri modelleme

.NET'te, verileri bir veri kaynağından alan verileri modellemek ve bellekte manipüle etmeye üç seçenek vardır:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Tercih edilen Microsoft ORM teknolojisi. İlişkisel verilere karşı birinci sınıf .NET nesneleri olarak program yapmak için bunu kullanabilirsiniz. Yeni uygulamalar için model gerektiğinde varsayılan ilk seçenek bu olacaktır. Temel alınan hizmet sağlayıcısından özel ADO.NET gerektirir.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Önceki nesil nesne ilişkisel eşlemci. Daha az karmaşık senaryolar için iyi çalışır, ancak artık etkin geliştirme aşamasında değildir.

[Veri kümeleri](../data-tools/dataset-tools-in-visual-studio.md) Üç modelleme teknolojisi arasında en eski olan. Öncelikle çok büyük miktarlarda veri işlemeyen veya karmaşık sorgular ya da dönüşümler gerçekleştirmeyen "veriler üzerinde formlar" uygulamalarının hızlı bir şekilde geliştirilmesi için tasarlanmıştır. DataSet nesnesi, .NET nesnelerinden çok daha fazla veritabanı nesnesine mantıksal olarak SQL DataTable ve DataRow nesnelerinden oluşur. Veri kaynaklarını temel alan SQL basit uygulamalar için veri kümeleri yine de iyi bir seçenek olabilir.

Bu teknolojilerden herhangi birini kullanmak gerekli değildir. Özellikle performansın kritik olduğu bazı senaryolarda, veritabanından okumak ve ihtiyacınız olan değerleri List gibi bir koleksiyon nesnesine kopyalamak için bir DataReader nesnesi \<T> kullanabilirsiniz.

## <a name="native-c"></a>Yerel C++

SQL Server'a ® C++ uygulamaları çoğu durumda ® [için Microsoft SQL SERVER ODBC Sürücüsü 13.1'i](https://www.microsoft.com/download/details.aspx?id=53339) kullan SQL Server gerekir. Sunucular bağlı ise, OLE DB gerekli olur ve bunun için [SQL Server Native Client.](/sql/relational-databases/native-client/sql-server-native-client) ODBC veya sürücülerini doğrudan kullanarak [diğer](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017&preserve-view=true) OLE DB erişebilirsiniz. ODBC geçerli standart veritabanı arabirimidir, ancak çoğu veritabanı sistemi ODBC arabirimi üzerinden erişilemedi özel işlevler sağlar. OLE DB, hala desteklenen ancak yeni uygulamalar için önerilmez olan eski bir COM veri erişim teknolojisidir. Daha fazla bilgi için [bkz. Visual C++.](/cpp/data/data-access-in-cpp)

REST hizmetlerini kullanan C++ programları [C++ REST SDK'sı kullanabilir.](https://github.com/Microsoft/cpprestsdk)

Microsoft Azure Depolama ile Microsoft Azure Depolama [C++ programları.](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP)

Veri &mdash; Visual Studio, C++ için bir ORM katmanı sağlamaz. [ODB,](https://www.codesynthesis.com/products/odb/) C++ için popüler bir açık kaynak ORM'dir.

C++ uygulamalarıyla veritabanlarına bağlanma hakkında daha fazla bilgi edinmek için [bkz. C++ Visual Studio araçlarına bağlanma.](../data-tools/visual-studio-data-tools-for-cpp.md) Eski veri erişim teknolojileri Visual C++ daha fazla bilgi için bkz. [Veri Erişimi.](/cpp/data/data-access-in-cpp)

## <a name="javascript"></a>JavaScript

[Visual Studio JavaScript;](/scripting/javascript/javascript-language-reference) platformlar arası uygulamalar, UWP uygulamaları, bulut hizmetleri, web siteleri ve web uygulamaları oluşturmanın birinci sınıf bir dilidir. Bower, Grunt, Gulp, npm ve NuGet kullanarak Visual Studio JavaScript kitaplıklarınızı ve veritabanı ürünlerinizi yükleyebilirsiniz. Bağlan azure web sitesinden SDK'ları indirerek Azure depolama ve [hizmetlere gidin.](https://azure.microsoft.com/) Edge.js, sunucu tarafı JavaScript'i (Node.js) ADO.NET kitaplıktır.

## <a name="python"></a>Python

Python [uygulamaları oluşturmak Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) Python desteğini yükleyin. Azure belgelerinde verilere bağlanmaya ilişkin aşağıdakiler de dahil olmak üzere çeşitli öğreticiler vardır:

- [Azure'da Django SQL Veritabanı ve sanal ağ](/azure/app-service/app-service-web-get-started-python)
- [Azure'da Django ve MySQL](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- [Bloblar, dosyalar,](/azure/storage/blobs/storage-quickstart-blobs-python) [kuyruklar ve tablolar](/azure/storage/queues/storage-python-how-to-use-queue-storage) [(Cosmo DB) ile çalışma.](/azure/cosmos-db/table-storage-how-to-use-python) [](/azure/storage/files/storage-python-how-to-use-file-storage)

## <a name="related-topics"></a>İlgili konular

[Microsoft AI platformu](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash; Cortana Analytics Suite dahil olmak üzere Microsoft akıllı buluta giriş ve Nesnelerin İnterneti.

[Microsoft Azure Depolama](/azure/storage/) &mdash; Azure Depolama ve Azure bloblarını, tablolarını, kuyruklarını ve dosyalarını kullanarak uygulama oluşturma hakkında bilgi sağlar.

[Azure SQL Veritabanı](/azure/sql-database/) &mdash; İlişkisel veritabanı olan Azure SQL Veritabanı veritabanına nasıl bağlanabilirsiniz?

[SQL Server Veri Araçları](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; Verilere bağlı uygulamalar ve veritabanlarının tasarımını, araştırmalarını, testlerini ve dağıtmalarını kolaylaştıran araçları açıklar.

[ADO.NET](/dotnet/framework/data/adonet/index) &mdash; Uygulama mimarisini ADO.NET uygulama verilerini yönetmek ve veri kaynakları ADO.NET XML ile etkileşim kurmak için ADO.NET sınıflarını kullanmayı açıklar.

[ADO.NET Entity Framework](/ef/ef6/) &mdash; Geliştiricilerin doğrudan bir ilişkisel veritabanı yerine kavramsal modele göre program oluşturmasına olanak sağlayan veri uygulamalarının nasıl oluşturul açıklanacak?

[WCF Veri Hizmetleri 4.5](/dotnet/framework/data/wcf/index) &mdash; Web'de veya Açık [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] Veri [Protokolü'nü (OData)](https://www.odata.org/)uygulayan bir intranette veri hizmetlerini dağıtmak için kullanmayı açıklar.

[Office Çözümlerde Veriler](../vsto/data-in-office-solutions.md) &mdash; Verilerin çözümlerde nasıl çalıştığını açıklayan konuların bağlantılarını Office içerir. Burada şema tabanlı programlama, verileri önbelleğe alma ve sunucu tarafında veri erişimi hakkında bilgiler bulunur.

[LINQ (Dille Tümleşik Sorgu)](/dotnet/csharp/linq/) &mdash; C# ve Visual Basic'de yerleşik sorgu özelliklerini ve ilişkisel veritabanlarını, XML belgelerini, veri kümelerini ve bellek içinde koleksiyonları sorgulamaya ilişkin ortak modeli açıklar.

[Visual Studio'de XML Araçları](../xml-tools/xml-tools-in-visual-studio.md) &mdash; XML verileriyle çalışmayı, XSLT'de hata ayıklamayı, .NET XML özelliklerini ve XML Sorgusu mimarisini ele almaktadır.

[XML Belgeleri ve Verileri](/dotnet/standard/data/xml/index) &mdash; .NET'te XML belgeleri ve verileriyle birlikte çalışmak için kapsamlı ve tümleşik bir sınıf kümesine genel bakış sağlar.
