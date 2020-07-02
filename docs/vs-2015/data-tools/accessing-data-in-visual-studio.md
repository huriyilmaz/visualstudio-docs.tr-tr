---
title: Veri erişimi
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
ms.openlocfilehash: 78d950b777d866835ef516c4910180b21de295e9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545008"
---
# <a name="accessing-data-in-visual-studio"></a>Visual Studio'da verilere erişime
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, her bir biçimde, bir yerel makinede, yerel bir ağda veya bir genel, özel veya karma bulutta bulunan herhangi bir biçimde, neredeyse tüm veritabanı ürün veya hizmetindeki verilere bağlanan uygulamalar oluşturabilirsiniz.

 JavaScript, Python, PHP, Ruby veya C++ içindeki uygulamalar için, kitaplıkları alarak ve kod yazarak başka herhangi bir şeyi yaptığınız gibi verilere bağlanırsınız. .NET uygulamalarında, Visual Studio veri kaynaklarını araştırmak, verileri bellekte depolamak ve işlemek için nesne modelleri oluşturmak ve Kullanıcı arabirimine veri bağlamak için kullanabileceğiniz araçlar sağlar.     Microsoft Azure, .NET, Java, Node.js, PHP, Python, Ruby ve mobil uygulamalar için SDK 'Ları ve Azure depolama 'ya bağlanmak için Visual Studio 'daki araçları sağlar.

 Aşağıdaki listeler, Visual Studio 'dan kullanılabilen birçok veritabanı ve depolama sisteminin yalnızca birkaçını gösterir. [Microsoft Azure](https://azure.microsoft.com/) teklifleri, temel alınan veri deposunun tüm sağlamasını ve yönetimini içeren veri hizmetlerdir.  [Visual Studio Için Azure Araçları](https://www.visualstudio.com/features/azure-tools-vs.aspx) , doğrudan Visual Studio 'dan Azure veri depoları ile çalışmanıza olanak sağlayan isteğe bağlı bir bileşendir. Burada listelenen diğer SQL ve NoSQL veritabanı ürünlerinin çoğu bir yerel makinede, yerel bir ağda veya bir sanal makinede Microsoft Azure barındırılabilecek. Bu senaryoda, veritabanının kendisini yönetmekten siz sorumlusunuz.

 **Microsoft Azure**

- SQL Veritabanı

- DocumentDB

-Depolama (blob 'lar, tablolar, kuyruklar, dosyalar)

- SQL Veri Ambarı

- SQL Server Stretch Database

- StorSimple

 Ve daha fazlası...

 **SQL**

- Express ve LocalDB dahil SQL Server 2005 – 2016
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite

 Ve daha fazlası...

 **NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NVeritabanı
- Cumentdb
- Çvendb
- VelocityDB

 Ve daha fazlası...

 Birçok veritabanı satıcısı ve üçüncü taraf, NuGet paketleri tarafından Visual Studio tümleştirmesini destekler. Teklifleri NuGet.org üzerinde veya Visual Studio 'daki NuGet Paket Yöneticisi aracılığıyla inceleyebilirsiniz (**Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet Paketlerini Yönet**). Diğer veritabanı ürünleri, Visual Studio ile bir uzantı olarak tümleştirilir.   **Araçlar**  >  **Uzantılar ve güncelleştirmeler** ' e giderek ve ardından iletişim kutusunun sol bölmesinde **çevrimiçi** ' i seçerek Visual Studio Galerisinde bu tekliflere gidebilirsiniz.  Daha fazla bilgi için bkz. [veritabanı sistemlerini, araçları ve örnekleri yükleme](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> SQL Server 2005 için genişletilmiş destek 12 Nisan 2016 tarihinde sona erdi.   Visual Studio 2015 ve sonraki sürümlerde veri araçlarının bu tarihten sonra SQL Server 2005 ile çalışmaya devam edeceğini garanti yoktur. Daha fazla bilgi için [SQL Server 2005 için destek sonu duyurusuna](https://www.microsoft.com/sql-server/sql-server-2005)bakın.

### <a name="net-languages"></a>.NET dilleri
 .NET Core dahil olmak üzere tüm .NET veri erişimleri, hem ilişkisel hem de ilişkisel olmayan her türlü veri kaynağına erişim için bir arabirim tanımlayan bir sınıf kümesi olan ADO.NET tabanlıdır. Visual Studio, veritabanlarına bağlanmanıza, verileri işlemenizi ve verileri kullanıcıya sunmanıza yardımcı olmak üzere ADO.NET ile çalışan çeşitli araçlara ve tasarımcılara sahiptir. Bu bölümdeki belgelerde, bu araçların nasıl kullanılacağı açıklanmaktadır. Ayrıca doğrudan ADO.NET komut nesnelerine karşı programlayabilirsiniz. ADO.NET API 'Lerini doğrudan çağırma hakkında daha fazla bilgi için MSDN Kitaplığı 'nda [ADO.net](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) bölümüne bakın.

 Özellikle ASP.NET ile ilgili veri erişimi belgeleri için bkz. ASP.NET sitesindeki [verilerle çalışma](/aspnet/web-forms/overview/presenting-and-managing-data/) . ASP.NET MVC ile Entity Framework kullanmaya yönelik bir öğretici için bkz. [MVC 5 kullanarak Entity Framework 6 Code First](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)kullanmaya başlama.

 C# veya Visual Basic Evrensel Windows Platformu (UWP) uygulamaları, Azure depolama ve diğer Azure hizmetlerine erişmek için .NET için Microsoft Azure SDK kullanabilir. Windows. Web. HttpClient sınıfı, herhangi bir yeniden iletişim hizmeti ile iletişime izin verebilir. Daha fazla bilgi için bkz. [Windows. Web. http kullanarak http sunucusuna bağlanma](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Yerel makinedeki veri depolama için önerilen yaklaşım, uygulamayla aynı işlemde çalışan SQLite ' ı kullanmaktır. Nesne ilişkisel eşleme (ORM) katmanı gerekliyse Entity Framework kullanabilirsiniz. Daha fazla bilgi için bkz. Windows Geliştirici Merkezi 'nde [veri erişimi](https://msdn.microsoft.com/windows/uwp/data-access/index) .

 Azure hizmetlerine bağlanıyorsanız en son [Azure SDK araçlarını](https://azure.microsoft.com/downloads/)indirdiğinizden emin olun.

#### <a name="data-providers"></a>Veri sağlayıcılar
 Bir veritabanının ADO.NET 'de tüketilebilir olması için, özel bir *ADO.NET veri sağlayıcısına* sahip olması veya bir ODBC veya OLE DB arabirimini kullanıma sunması gerekir. Microsoft, SQL Server ürünlerin yanı sıra ODBC ve OLE DB sağlayıcıları için [ADO.NET veri sağlayıcılarının bir listesini](https://msdn.microsoft.com/data/dd363565) sağlar.

#### <a name="data-modeling"></a>Veri modelleme
 .NET ' te, verileri bir veri kaynağından aldıktan sonra modelleme ve bellekteki verileri düzenleme için üç seçeneğiniz vardır:

 Tercih edilen Microsoft ORM teknolojisini Entity Framework. Bunu, birinci sınıf .NET nesneleri olarak ilişkisel verilerle programlama için kullanabilirsiniz. Yeni uygulamalar için, bir model gerektiğinde varsayılan olarak ilk seçenek olmalıdır. Temel ADO.NET sağlayıcısından özel destek gerektirir.

 Daha önceki nesil bir nesne ilişkisel Eşleyici LINQ to SQL. Daha az karmaşık senaryolar için uygundur, ancak artık etkin bir geliştirme aşamasındadır.

 Üç modelleme teknolojisinin en eski kısmını veri kümeleri. Bu, öncelikli olarak büyük miktarlarda veri işlemenin veya karmaşık sorgular ya da dönüşümler yerine getirilmesi gereken "veri üzerinden Forms" uygulamalarının hızlı geliştirmesi için tasarlanmıştır. Veri kümesi nesnesi, SQL veritabanı nesnelerine .NET nesnelerinden çok daha fazla benzeyen DataTable ve DataRow nesnelerinden oluşur. SQL veri kaynaklarını temel alan görece basit uygulamalar için, veri kümeleri yine de iyi bir seçenek olabilir.

 Bu teknolojilerden herhangi birini kullanma gereksinimi yoktur. Bazı senaryolarda, özellikle performans önemli olduğu durumlarda, veritabanından okumak ve ihtiyacınız olan değerleri liste gibi bir koleksiyon nesnesine kopyalamak için yalnızca bir DataReader nesnesi kullanabilirsiniz \<T> .

### <a name="native-c"></a>Yerel C++
 SQL Server bağlanan C++ uygulamaları [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx)kullanmalıdır. Diğer veritabanlarına, [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) veya OLE DB sürücülerini doğrudan kullanarak erişebilirsiniz. ODBC, geçerli standart veritabanı arabirimidir, ancak çoğu veritabanı sistemi ODBC arabiriminden erişilemeyen özel işlevlere sahiptir.  OLE DB, hala desteklenen ancak yeni uygulamalar için önerilmeyen eski bir COM veri erişim teknolojisidir.  Daha fazla bilgi için bkz. [veri erişimi](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 REST hizmetlerini kullanan c++ programları [C++ Rest SDK 'sını](https://github.com/Microsoft/cpprestsdk)kullanabilir.

 Microsoft Azure Depolama ile çalışan C++ programları [Microsoft Azure depolama istemcisini](https://www.nuget.org/packages/wastorage)kullanabilir.

#### <a name="data-modeling"></a>Veri modelleme
 Visual Studio, C++ için bir ORM katmanı sağlamıyor.  [ODB](https://www.codesynthesis.com/products/odb/) , C++ için popüler bir açık kaynaklı ORM 'dir.

 Eski Visual C++ veri erişimi teknolojileri hakkında daha fazla bilgi için bkz. [veri erişimi](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [Visual Studio 'Da JavaScript](https://msdn.microsoft.com/library/hh334522.aspx) , platformlar arası uygulamalar, UWP uygulamaları, bulut Hizmetleri, Web siteleri ve Web uygulamaları oluşturmak için birinci sınıf bir dildir. En sevdiğiniz JavaScript kitaplıklarını ve veritabanı ürünlerini yüklemek için Visual Studio içinden Bower, Grsıt, Gulp, NPM ve NuGet kullanabilirsiniz. [Azure Web sitesinden](https://azure.microsoft.com/)SDK 'Ları indirerek Azure depolama ve hizmetlere bağlanın.  Edge.js, sunucu tarafı JavaScript 'ı (Node.js) ADO.NET veri kaynaklarına bağlayan bir kitaplıktır.

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

 [WCF Veri Hizmetleri 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]Web 'de veya [Açık Veri Protokolü 'Nü (OData)](https://www.odata.org/)uygulayan bir intranette veri hizmetleri dağıtmak için ' nin nasıl kullanılacağını açıklar.

 [Office çözümlerindeki veriler](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Office çözümlerinde verilerin nasıl çalıştığını açıklayan konulara bağlantılar içerir. Burada şema tabanlı programlama, verileri önbelleğe alma ve sunucu tarafında veri erişimi hakkında bilgiler bulunur.

 [LINQ (dil Ile tümleşik sorgu)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) C# ve Visual Basic yerleşik sorgu özelliklerini ve ilişkisel veritabanlarını, XML belgelerini, veri kümelerini ve bellek içi koleksiyonları sorgulamak için ortak modeli açıklar.

 [Visual Studio 'Da XML araçları](../xml-tools/xml-tools-in-visual-studio.md) XML verileri, XSLT hata ayıklama, .NET Framework XML özellikleri ve XML sorgusunun mimarisi ile çalışmayı açıklar.

 [XML belgeleri ve verileri](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) .NET Framework XML belgeleriyle ve verilerle çalışan kapsamlı ve tümleşik bir sınıf kümesine genel bakış sağlar.
