---
title: Visual Studio 'da verilerle çalışma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7c7aa1544f998a88424c0087fadceab63757d23b
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272082"
---
# <a name="work-with-data-in-visual-studio"></a>Visual Studio 'da verilerle çalışma

Visual Studio'da verilere neredeyse tüm veritabanı ürün veya hizmeti, herhangi bir biçimde, her yerden bağlanma uygulamalar oluşturabilirsiniz: yerel bir makinede, yerel alan ağı veya genel, özel veya hibrit bulut.

JavaScript, Python, PHP, Ruby ve C++ için uygulamalar, başka herhangi bir şey kitaplıkları alma ve kod yazmaya yaptığı gibi verilere bağlanın. .NET uygulamalarında, Visual Studio veri kaynaklarını araştırmak, verileri bellekte depolamak ve işlemek için nesne modelleri oluşturmak ve Kullanıcı arabirimine veri bağlamak için kullanabileceğiniz araçlar sağlar. Microsoft Azure Azure depolamaya bağlanmak için .NET, Java, Node.js, PHP, Python, Ruby ve mobil uygulamalar ve Visual Studio Araçları için SDK'lar sağlar.

::: moniker range="vs-2017"
Aşağıdaki listelerde, Visual Studio'dan kullanılabilecek çok sayıda veritabanı ve depolama sistemlerini birkaçı gösterilir. [Microsoft Azure](https://azure.microsoft.com/) teklifleri, temel alınan veri deposunun tüm sağlamasını ve yönetimini içeren veri hizmetlerdir. [Visual studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ' deki **Azure geliştirme** Iş yükü, doğrudan Visual Studio 'dan Azure veri depoları ile çalışmanıza olanak sağlar.
::: moniker-end
::: moniker range=">=vs-2019"
Aşağıdaki listelerde, Visual Studio'dan kullanılabilecek çok sayıda veritabanı ve depolama sistemlerini birkaçı gösterilir. [Microsoft Azure](https://azure.microsoft.com/) teklifleri, temel alınan veri deposunun tüm sağlamasını ve yönetimini içeren veri hizmetlerdir. [Visual studio 2019](https://visualstudio.microsoft.com/downloads) ' deki **Azure geliştirme** Iş yükü, doğrudan Visual Studio 'dan Azure veri depoları ile çalışmanıza olanak sağlar.
::: moniker-end

![Azure geliştirme iş yükü](media/azure-development-workload.png)

Burada listelenen SQL ve NoSQL veritabanı ürünlerin çoğunu, yerel bir makinede, Microsoft azure'da veya yerel ağdaki bir sanal makine üzerinde barındırılabilir. Veritabanını Microsoft Azure sanal bir makinede barındırdıysanız, veritabanının kendisini yönetmekten siz sorumlusunuz.

**Microsoft Azure**

- SQL Database
- Azure Cosmos DB
- Depolama (BLOB'lar, tablolar, kuyruklar, dosyalar)
- SQL Veri Ambarı
- SQL Server Stretch Database
- StorSimple
- ve daha fazlası...

**SQL**

- SQL Server 2005-2016 (Express ve LocalDB 'yi içerir)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- ve daha fazlası...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NVeritabanı
- Cumentdb |
- RavenDB
- VelocityDB
- ve daha fazlası...

::: moniker range="vs-2017"

Birçok veritabanı satıcılar ve üçüncü taraflar tarafından NuGet paketlerini Visual Studio tümleştirmesini desteklemiyor. Teklifleri nuget.org üzerinde veya Visual Studio 'daki NuGet Paket Yöneticisi aracılığıyla inceleyebilirsiniz (**araçlar** > **nuget Paket Yöneticisi** > **çözüm için NuGet Paketlerini Yönet**). Diğer veritabanı ürünleri bir uzantısı olarak Visual Studio ile tümleştirin. Bu tekliflere [Visual Studio Market](https://marketplace.visualstudio.com/) gözatabilir veya **Araçlar** > **Uzantılar ve güncelleştirmeler** ' e giderek iletişim kutusunun sol bölmesinde **çevrimiçi** ' i seçerek bu teklife gidebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio Için uyumlu veritabanı sistemleri](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Birçok veritabanı satıcılar ve üçüncü taraflar tarafından NuGet paketlerini Visual Studio tümleştirmesini desteklemiyor. Teklifleri nuget.org üzerinde veya Visual Studio 'daki NuGet Paket Yöneticisi aracılığıyla inceleyebilirsiniz (**araçlar** > **nuget Paket Yöneticisi** > **çözüm için NuGet Paketlerini Yönet**). Diğer veritabanı ürünleri bir uzantısı olarak Visual Studio ile tümleştirin. [Visual Studio Market](https://marketplace.visualstudio.com/) bu tekliflere gözatabilir veya uzantıları **yönetebilir** ** > ve** ardından iletişim kutusunun sol bölmesinde **çevrimiçi** ' yi seçerek bu teklife gidebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio Için uyumlu veritabanı sistemleri](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> SQL Server 2005'e yönelik genişletilmiş destek 12 Nisan 2016 tarihinde sona erdi. Visual Studio 2015 ve üzeri veri araçlarının SQL Server 2005 ile çalışmaya devam edeceğini garanti yoktur. Daha fazla bilgi için [SQL Server 2005 için destek sonu duyurusuna](https://www.microsoft.com/sql-server/sql-server-2005)bakın.

## <a name="net-languages"></a>.NET dilleri

.NET Core dahil olmak üzere tüm .NET veri erişimleri, hem ilişkisel hem de ilişkisel olmayan her türlü veri kaynağına erişim için bir arabirim tanımlayan bir sınıf kümesi olan ADO.NET tabanlıdır. Visual Studio çeşitli araçları vardır ve veritabanlarına bağlanmanıza yardımcı olması için ADO.NET çalışmak tasarımcıları verileri işlemek ve kullanıcıya verileri sunar. Bu bölümdeki belgeler bu araçlarının nasıl kullanılacağını açıklar. Ayrıca, doğrudan ADO.NET komut nesneleri karşı programlama yapabilirsiniz. ADO.NET API 'Lerini doğrudan çağırma hakkında daha fazla bilgi için bkz. [ADO.net](/dotnet/framework/data/adonet/index).

ASP.NET ile ilgili veri erişimi belgeleri için bkz. ASP.NET sitesindeki [verilerle çalışma](https://www.asp.net/web-forms/overview/presenting-and-managing-data) . ASP.NET MVC ile Entity Framework kullanmaya yönelik bir öğretici için bkz. [MVC 5 kullanarak Entity Framework 6 Code First](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)kullanmaya başlama.

C# Veya Visual Basic evrensel WINDOWS platformu (UWP) uygulamaları, Azure depolama ve diğer Azure hizmetlerine erişmek için .NET için Microsoft Azure SDK kullanabilir. Herhangi bir RESTful hizmeti ile iletişimi Windows.Web.HttpClient sınıfı sağlar. Daha fazla bilgi için bkz. [Windows. Web. http kullanarak http sunucusuna bağlanma](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Yerel makinede veri depolama için önerilen yaklaşım uygulama ile aynı işlemde çalışan SQLite kullanmaktır. Bir nesne ilişkisel eşleme (ORM) katman gerekiyorsa, Entity Framework kullanabilirsiniz. Daha fazla bilgi için bkz. Windows Geliştirici Merkezi 'nde [veri erişimi](/windows/uwp/data-access/index) .

Azure hizmetlerine bağlanıyorsanız en son [Azure SDK araçlarını](https://azure.microsoft.com/downloads/)indirdiğinizden emin olun.

### <a name="data-providers"></a>Veri sağlayıcıları

Bir veritabanının ADO.NET 'de tüketilebilir olması için, özel bir *ADO.NET veri sağlayıcısına* sahip olması veya bir ODBC veya OLE DB arabirimini kullanıma sunması gerekir. Microsoft, SQL Server ürünlerin yanı sıra ODBC ve OLE DB sağlayıcıları için [ADO.NET veri sağlayıcılarının bir listesini](/dotnet/framework/data/adonet/ado-net-overview) sağlar.

### <a name="data-modeling"></a>Veri modelleme

. NET'te, modelleme ve veri kaynağından aldıktan sonra bellekteki verileri işlemek için üç seçeneğiniz vardır:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Tercih edilen Microsoft ORM teknolojisi. Bunu ilişkisel verilere karşı programlama birinci sınıf .NET nesneleri kullanabilirsiniz. Yeni uygulamalar için bir model gerekli olduğunda varsayılan ilk seçenek olmalıdır. Bu, temel alınan ADO.NET sağlayıcısı özel desteğini gerektirir.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Önceki nesil bir nesne ilişkisel Eşleyici. Daha az karmaşık senaryolar için iyi çalışır, ancak artık etkin geliştirme değildir.

[Veri kümeleri](../data-tools/dataset-tools-in-visual-studio.md) Üç modelleme teknolojisinin en eski sürümü. Bu, öncelikli olarak hangi, katılmamaları büyük miktarlarda veri işleme veya karmaşık sorgular veya dönüşüm gerçekleştiren "veriler üzerinden formlar" uygulamaların hızlı geliştirme için tasarlandı. Veri kümesi nesnesi, SQL veritabanı nesnelerine .NET nesnelerinden çok daha fazla benzeyen DataTable ve DataRow nesnelerinden oluşur. SQL veri kaynaklarını temel alan görece basit uygulamalar için, veri kümeleri yine de iyi bir seçenek olabilir.

Bu teknolojiler birini kullanmak için bir gereksinim değildir. Bazı senaryolarda, özellikle de performans önemli olduğu durumlarda, veritabanından okumak ve ihtiyacınız olan değerleri liste\<T > gibi bir koleksiyon nesnesine kopyalamak için yalnızca bir DataReader nesnesi kullanabilirsiniz.

## <a name="native-c"></a>Yerel C++

C++SQL Server bağlanan uygulamalar çoğu durumda [SQL Server Için Microsoft® ODBC sürücüsü 13,1](https://www.microsoft.com/download/details.aspx?id=53339) ' i kullanmalıdır. Sunucular bağlantısa, OLE DB gereklidir ve [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client)kullanmanız gerekir. Diğer veritabanlarına, [ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) veya OLE DB sürücülerini doğrudan kullanarak erişebilirsiniz. ODBC için geçerli standart veritabanı arabirimi olsa da, çoğu veritabanı sistemi ODBC arabirimi üzerinden erişilemeyen özel işlevsellik sağlar. OLE DB, yine de desteklenir, ancak yeni uygulamalar için önerilen eski bir COM veri erişimi teknolojisidir. Daha fazla bilgi için bkz. [Visual C++'te veri erişimi ](/cpp/data/data-access-in-cpp).

C++Rest hizmetlerini kullanan programlar [ C++ Rest SDK 'yı](https://github.com/Microsoft/cpprestsdk)kullanabilir.

C++Microsoft Azure Depolama ile çalışan programlar [Microsoft Azure depolama istemcisini](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP)kullanabilir.

Visual Studio&mdash;veri modellemesi, için C++bir ORM katmanı sağlamıyor. [ODB](https://www.codesynthesis.com/products/odb/) , için C++popüler bir açık kaynaklı ORM 'dir.

Uygulamalardan veritabanlarına bağlanma hakkında daha fazla bilgi edinmek için bkz. [Visual Studio veri araçları C++. ](../data-tools/visual-studio-data-tools-for-cpp.md) C++ Eski görsel C++ veri erişimi teknolojileri hakkında daha fazla bilgi için bkz. [veri erişimi](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[Visual Studio 'Da JavaScript](/scripting/javascript/javascript-language-reference) , platformlar arası uygulamalar, UWP uygulamaları, bulut Hizmetleri, Web siteleri ve Web uygulamaları oluşturmak için birinci sınıf bir dildir. En sevdiğiniz JavaScript kitaplıklarını ve veritabanı ürünlerini yüklemek için Visual Studio içinden Bower, Grsıt, Gulp, NPM ve NuGet kullanabilirsiniz. [Azure Web sitesinden](https://azure.microsoft.com/)SDK 'Ları indirerek Azure depolama ve hizmetlere bağlanın. Edge.js sunucu tarafı JavaScript (Node.js) için ADO.NET veri kaynaklarına bağlanan bir kitaplıktır.

## <a name="python"></a>Python

Python uygulamaları oluşturmak için [Visual Studio 'Da Python desteği '](../python/overview-of-python-tools-for-visual-studio.md) ni yükler. Azure belgelerinin, aşağıdakiler de dahil olmak üzere verilere bağlanmaya yönelik çeşitli öğreticiler vardır:

- [Azure 'da docgo ve SQL veritabanı](/azure/app-service/app-service-web-get-started-python)
- [Azure 'da docgo ve MySQL](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- [Bloblar](/azure/storage/blobs/storage-quickstart-blobs-python), [dosyalar](/azure/storage/files/storage-python-how-to-use-file-storage), [Kuyruklar](/azure/storage/queues/storage-python-how-to-use-queue-storage)ve [Tablolar (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python)ile çalışın.

## <a name="related-topics"></a>İlgili konular

[MICROSOFT AI platformu](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;, Cortana Analytics Suite ve nesnelerin interneti desteği dahil olmak üzere Microsoft Akıllı bulutuna bir giriş sağlar.

[Microsoft Azure Depolama](/azure/storage/)&mdash;Azure depolama 'Yı ve Azure Blob 'ları, tabloları, kuyrukları ve dosyalarını kullanarak uygulama oluşturmayı açıklar.

[Azure SQL veritabanı](/azure/sql-database/)&mdash;bir hizmet olarak ilişkisel veritabanı olan Azure SQL veritabanı 'na nasıl bağlanabileceğinizi açıklar.

[SQL Server Veri Araçları](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;, verilere bağlı uygulamaların ve veritabanlarının tasarımını, araştırmasını, test edilmesini ve dağıtılmasını kolaylaştıran araçları açıklar.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;, ADO.NET mimarisini ve uygulama verilerini yönetmek ve veri kaynakları ile XML ile etkileşim kurmak için ADO.net sınıflarının nasıl kullanılacağını açıklar.

[ADO.NET Entity Framework](/ef/ef6/)&mdash;, geliştiricilerin doğrudan ilişkisel bir veritabanına karşı kavramsal bir modelde programlama yapmasına izin veren veri uygulamalarının nasıl oluşturulacağını açıklar.

[WCF Veri Hizmetleri 4,5](/dotnet/framework/data/wcf/index)&mdash;Web 'de veya [Açık Veri Protokolü 'nü (OData)](https://www.odata.org/)uygulayan bir intranette veri hizmetleri dağıtmak Için [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] nasıl kullanılacağını açıklar.

[Office çözümlerinde&mdash;veriler](../vsto/data-in-office-solutions.md) , Office çözümlerinde verilerin nasıl çalıştığını açıklayan konuların bağlantılarını içerir. Burada şema tabanlı programlama, verileri önbelleğe alma ve sunucu tarafında veri erişimi hakkında bilgiler bulunur.

[LINQ (dil Ile tümleşik sorgu)](/dotnet/csharp/linq/)&mdash;, C# ve Visual Basic yerleşik sorgu özelliklerini ve ilişkisel veritabanlarını, XML belgelerini, veri kümelerini ve bellek içi koleksiyonları sorgulamak Için kullanılan ortak modeli açıklar.

[Visual Studio 'Daki XML araçları](../xml-tools/xml-tools-in-visual-studio.md)&mdash;XML verileriyle ÇALıŞMAYı, XSLT, .NET XML özellıklerını ve XML sorgusunun mimarisini açıklar.

[XML belgeleri ve veri](/dotnet/standard/data/xml/index)&mdash;, .NET içindeki XML belgeleriyle ve verilerle çalışan kapsamlı ve tümleşik sınıflar kümesine genel bir bakış sağlar.
