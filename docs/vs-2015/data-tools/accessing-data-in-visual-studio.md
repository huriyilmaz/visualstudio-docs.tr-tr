---
title: Verilere erişme
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 158bc4c2fc7734957c7d3e946390ab1339a322ba
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299441"
---
# <a name="accessing-data-in-visual-studio"></a>Visual Studio'da verilere erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da verilere neredeyse tüm veritabanı ürün veya hizmeti, herhangi bir biçimde, her yerden bağlanma uygulamalar oluşturabilirsiniz: yerel bir makinede, yerel alan ağı veya genel, özel veya hibrit bulut.

 JavaScript, Python, PHP, Ruby ve C++ için uygulamalar, başka herhangi bir şey kitaplıkları alma ve kod yazmaya yaptığı gibi verilere bağlanın. .NET uygulamaları için Visual Studio veri kaynakları keşfedin, depolamak ve bellekte verileri işlemek ve veri kullanıcı arabirimine bağlamak için nesne modelleri oluşturmak için kullanabileceğiniz araçlar sağlar.     Microsoft Azure Azure depolamaya bağlanmak için .NET, Java, Node.js, PHP, Python, Ruby ve mobil uygulamalar ve Visual Studio Araçları için SDK'lar sağlar.

 Aşağıdaki listelerde, Visual Studio'dan kullanılabilecek çok sayıda veritabanı ve depolama sistemlerini birkaçı gösterilir. [Microsoft Azure](https://azure.microsoft.com/) teklifleri, temel alınan veri deposunun tüm sağlamasını ve yönetimini içeren veri hizmetlerdir.  [Visual Studio Için Azure Araçları](https://www.visualstudio.com/features/azure-tools-vs.aspx) , doğrudan Visual Studio 'dan Azure veri depoları ile çalışmanıza olanak sağlayan isteğe bağlı bir bileşendir. Burada listelenen SQL ve NoSQL veritabanı ürünlerin çoğunu, yerel bir makinede, Microsoft azure'da veya yerel ağdaki bir sanal makine üzerinde barındırılabilir. Bu senaryoda, veritabanı yönetmekten sorumlu olursunuz.

 **Microsoft Azure**

||||
|-|-|-|
|SQL veritabanı|DocumentDB|Depolama (BLOB'lar, tablolar, kuyruklar, dosyalar)|
|SQL veri ambarı|SQL Server Stretch Database|StorSimple|

 ve daha fazlası...

 **SQL**

||||
|-|-|-|
|SQL Server 2005 – 2016 Express ve LocalDB dahil,|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

 ve daha fazlası...

 **NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NVeritabanı|OrientDB|RavenDB|
|VelocityDB|||

 ve daha fazlası...

 Birçok veritabanı satıcılar ve üçüncü taraflar tarafından NuGet paketlerini Visual Studio tümleştirmesini desteklemiyor. Teklifleri nuget.org üzerinde veya Visual Studio 'daki NuGet Paket Yöneticisi aracılığıyla inceleyebilirsiniz (**araçlar** > **nuget Paket Yöneticisi** > **çözüm için NuGet Paketlerini Yönet**). Diğer veritabanı ürünleri bir uzantısı olarak Visual Studio ile tümleştirin.   **Araçlar** > **Uzantılar ve güncelleştirmeler** ' e giderek ve ardından Iletişim kutusunun sol bölmesinde **çevrimiçi** ' i seçerek Visual Studio Galerisinde bu tekliflere gidebilirsiniz.  Daha fazla bilgi için bkz. [veritabanı sistemlerini, araçları ve örnekleri yükleme](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> SQL Server 2005'e yönelik genişletilmiş destek 12 Nisan 2016 tarihinde sona erdi.   Veri araçları Visual Studio 2015 ve sonraki sürümlerinde bu tarihten sonra SQL Server 2005 ile çalışmaya devam edeceği kesin değildir. Daha fazla bilgi için [SQL Server 2005 için destek sonu duyurusuna](https://www.microsoft.com/sql-server/sql-server-2005)bakın.

### <a name="net-languages"></a>.NET dilleri
 .NET Core dahil olmak üzere tüm .NET veri erişimi, ADO.NET, veri kaynağı, ilişkisel ve ilişkisel olmayan herhangi bir türden erişmek için bir arabirim tanımlayan bir sınıf kümesi dayanır. Visual Studio çeşitli araçları vardır ve veritabanlarına bağlanmanıza yardımcı olması için ADO.NET çalışmak tasarımcıları verileri işlemek ve kullanıcıya verileri sunar. Bu bölümdeki belgeler bu araçlarının nasıl kullanılacağını açıklar. Ayrıca, doğrudan ADO.NET komut nesneleri karşı programlama yapabilirsiniz. ADO.NET API 'Lerini doğrudan çağırma hakkında daha fazla bilgi için MSDN Kitaplığı 'nda [ADO.net](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) bölümüne bakın.

 Özellikle ASP.NET ile ilgili veri erişimi belgeleri için bkz. ASP.NET sitesindeki [verilerle çalışma](https://docs.microsoft.com/aspnet/web-forms/overview/presenting-and-managing-data/) . ASP.NET MVC ile Entity Framework kullanmaya yönelik bir öğretici için bkz. [MVC 5 kullanarak Entity Framework 6 Code First](https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)kullanmaya başlama.

 C# veya Visual Basic'te Evrensel Windows Platformu (UWP) uygulamaları, .NET için Microsoft Azure SDK'sı, Azure depolama ve diğer Azure hizmetlerine erişmek için kullanabilirsiniz. Herhangi bir RESTful hizmeti ile iletişimi Windows.Web.HttpClient sınıfı sağlar. Daha fazla bilgi için bkz. [Windows. Web. http kullanarak http sunucusuna bağlanma](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Yerel makinede veri depolama için önerilen yaklaşım uygulama ile aynı işlemde çalışan SQLite kullanmaktır. Bir nesne ilişkisel eşleme (ORM) katman gerekiyorsa, Entity Framework kullanabilirsiniz. Daha fazla bilgi için bkz. Windows Geliştirici Merkezi 'nde [veri erişimi](https://msdn.microsoft.com/windows/uwp/data-access/index) .

 Azure hizmetlerine bağlanıyorsanız en son [Azure SDK araçlarını](https://azure.microsoft.com/downloads/)indirdiğinizden emin olun.

#### <a name="data-providers"></a>Veri sağlayıcıları
 Bir veritabanının ADO.NET 'de tüketilebilir olması için, özel bir *ADO.NET veri sağlayıcısına* sahip olması veya bir ODBC veya OLE DB arabirimini kullanıma sunması gerekir. Microsoft, SQL Server ürünlerin yanı sıra ODBC ve OLE DB sağlayıcıları için [ADO.NET veri sağlayıcılarının bir listesini](https://msdn.microsoft.com/data/dd363565) sağlar.

#### <a name="data-modeling"></a>Veri modelleme
 . NET'te, modelleme ve veri kaynağından aldıktan sonra bellekteki verileri işlemek için üç seçeneğiniz vardır:

 Entity Framework tercih edilen Microsoft ORM teknoloji. Bunu ilişkisel verilere karşı programlama birinci sınıf .NET nesneleri kullanabilirsiniz. Yeni uygulamalar için bir model gerekli olduğunda varsayılan ilk seçenek olmalıdır. Bu, temel alınan ADO.NET sağlayıcısı özel desteğini gerektirir.

 LINQ to SQL eski kuşak nesne ilişkisel eşleyicidir. Daha az karmaşık senaryolar için iyi çalışır, ancak artık etkin geliştirme değildir.

 Veri kümeleri üç modelleme teknolojilerinin en eski. Bu, öncelikli olarak hangi, katılmamaları büyük miktarlarda veri işleme veya karmaşık sorgular veya dönüşüm gerçekleştiren "veriler üzerinden formlar" uygulamaların hızlı geliştirme için tasarlandı. DataTable ve DataRow nesnelerin mantıksal olarak SQL veritabanı nesnelerini .NET nesneleri birden çok fazla benzer bir veri kümesi nesnesi oluşur. SQL veri kaynağını temel alan görece basit uygulamalar için veri kümeleri yine de iyi bir seçim olabilir.

 Bu teknolojiler birini kullanmak için bir gereksinim değildir. Bazı senaryolarda, özellikle de performans önemli olduğu durumlarda, veritabanından okumak ve ihtiyacınız olan değerleri liste\<T > gibi bir koleksiyon nesnesine kopyalamak için yalnızca bir DataReader nesnesi kullanabilirsiniz.

### <a name="native-c"></a>Yerel C++
 C++SQL Server bağlanan uygulamalar [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx)kullanmalıdır. Diğer veritabanlarına, [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) veya OLE DB sürücülerini doğrudan kullanarak erişebilirsiniz. ODBC için geçerli standart veritabanı arabirimi olsa da, çoğu veritabanı sistemi ODBC arabirimi üzerinden erişilemeyen özel işlevsellik sağlar.  OLE DB, yine de desteklenir, ancak yeni uygulamalar için önerilen eski bir COM veri erişimi teknolojisidir.  Daha fazla bilgi için bkz. [veri erişimi](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 C++Rest hizmetlerini kullanan programlar [ C++ Rest SDK 'yı](https://github.com/Microsoft/cpprestsdk)kullanabilir.

 C++Microsoft Azure Depolama ile çalışan programlar [Microsoft Azure depolama istemcisini](https://www.nuget.org/packages/wastorage)kullanabilir.

#### <a name="data-modeling"></a>Veri modelleme
 Visual Studio C++ için ORM katman sağlamaz.  [ODB](https://www.codesynthesis.com/products/odb/) , için C++popüler bir açık kaynaklı ORM 'dir.

 Eski görsel C++ veri erişimi teknolojileri hakkında daha fazla bilgi için bkz. [veri erişimi](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [Visual Studio 'Da JavaScript](https://msdn.microsoft.com/library/hh334522.aspx) , platformlar arası uygulamalar, UWP uygulamaları, bulut Hizmetleri, Web siteleri ve Web uygulamaları oluşturmak için birinci sınıf bir dildir. Sık kullandığınız JavaScript kitaplıklarını ve veritabanı ürünleri yüklemek için Bower, Grunt, Gulp, npm ve Visual Studio içinden Nuget'ten kullanabilirsiniz. [Azure Web sitesinden](https://azure.microsoft.com/)SDK 'Ları indirerek Azure depolama ve hizmetlere bağlanın.  Edge.js sunucu tarafı JavaScript (Node.js) için ADO.NET veri kaynaklarına bağlanan bir kitaplıktır.

### <a name="python"></a>Python
 Cponthon veya IronPython (.NET) uygulamaları oluşturmak için en sevdiğiniz Python çerçevesiyle birlikte [Visual Studio için Python araçları](http://microsoft.github.io/PTVS/) ' i de yüklersiniz.  Visual Studio için Python Araçları Web sitesinde Azure 'da [Dmongo ve SQL veritabanı](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), Azure 'da [Dmongo ve MySQL](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) ve Azure 'Daki [şişe ve MongoDB](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure)gibi veri bağlama konusunda çeşitli öğreticiler vardır.

## <a name="in-this-section"></a>Bu bölümde
 [Veritabanı sistemlerini, araçları ve örnekleri yükleme](../data-tools/installing-database-systems-tools-and-samples.md) Veritabanı ürünlerinin ve bunları destekleyen Visual Studio uzantılarının veya sürücülerin nasıl alınacağını ve deneme ve öğrenme amaçlarıyla örnek veritabanlarının nerede bulunacağını açıklar.

 [.Net Için Visual Studio veri araçları](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Veri kaynaklarına bağlanmak, veri kümeleri veya Entity Framework modeller oluşturmak ve verileri Kullanıcı arabirimi denetimlerine bağlamak için Visual Studio araç pencerelerinin nasıl kullanılacağını açıklar.

## <a name="related-topics"></a>İlgili konular
 [Veri, cihaz ve analiz](https://msdn.microsoft.com/data-and-devices) Cortana Analytics Suite ve Nesnelerin İnterneti için destek dahil olmak üzere Microsoft Akıllı bulutuna bir giriş sağlar.

 [Microsoft Azure depolama](/azure/storage/) Azure depolama 'yı ve Azure Blob 'ları, tabloları, kuyrukları ve dosyalarını kullanarak uygulama oluşturmayı açıklar.

 [Azure SQL veritabanı](https://azure.microsoft.com/documentation/services/sql-database/) Hizmet olarak ilişkisel bir veritabanı olan Azure SQL veritabanı 'na nasıl bağlanabileceğinizi açıklar.

 [SQL Server veri araçları](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) Verilere bağlı uygulamaların ve veritabanlarının tasarımını, araştırmasını, test edilmesini ve dağıtılmasını kolaylaştıran araçları açıklar.

 [ADO.net](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) ADO.NET mimarisini ve uygulama verilerini yönetmek ve veri kaynaklarıyla ve XML ile etkileşime geçmek için ADO.NET sınıflarının nasıl kullanılacağını açıklar.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) Geliştiricilerin doğrudan ilişkisel bir veritabanına karşı kavramsal bir modelde programlama yapmasına izin veren veri uygulamalarının nasıl oluşturulacağını açıklar.

 [WCF Veri Hizmetleri 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Web 'de veya [Açık Veri Protokolü 'nü (OData)](https://go.microsoft.com/fwlink/?LinkID=182204)uygulayan bir intranette veri hizmetlerini dağıtmak için [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] kullanmayı açıklar.

 [Office çözümlerindeki veriler](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Office çözümlerinde verilerin nasıl çalıştığını açıklayan konulara bağlantılar içerir. Burada şema tabanlı programlama, verileri önbelleğe alma ve sunucu tarafında veri erişimi hakkında bilgiler bulunur.

 [LINQ (dil Ile tümleşik sorgu)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) C# Ve Visual Basic yerleşik sorgu özelliklerini ve ilişkisel VERITABANLARıNı, XML belgelerini, veri kümelerini ve bellek içi koleksiyonları sorgulamak için ortak modeli açıklar.

 [Visual Studio 'Da XML araçları](../xml-tools/xml-tools-in-visual-studio.md) XML verileri, XSLT hata ayıklama, .NET Framework XML özellikleri ve XML sorgusunun mimarisi ile çalışmayı açıklar.

 [XML belgeleri ve verileri](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) .NET Framework XML belgeleriyle ve verilerle çalışan kapsamlı ve tümleşik bir sınıf kümesine genel bakış sağlar.
