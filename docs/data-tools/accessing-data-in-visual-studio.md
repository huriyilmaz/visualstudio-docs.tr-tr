---
title: Visual Studio’da verilerle çalışma
description: Visual Studio 'da verilerle çalışın. Yerel makineler, lan 'Lar veya genel veya özel bulutlar üzerinde diğer veritabanı ürünlerinde veya hizmetlerinde bulunan verilere bağlanan uygulamalar oluşturun.
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
ms.openlocfilehash: 846898c1cf93d0f90ce04e77ee93bd8802e22ec2
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382097"
---
# <a name="work-with-data-in-visual-studio"></a>Visual Studio’da verilerle çalışma

Visual Studio 'da, her bir biçimde, bir yerel makinede, yerel bir ağda veya bir genel, özel veya karma bulutta bulunan herhangi bir biçimde, neredeyse tüm veritabanı ürün veya hizmetindeki verilere bağlanan uygulamalar oluşturabilirsiniz.

JavaScript, Python, PHP, Ruby veya C++ içindeki uygulamalar için, kitaplıkları alarak ve kod yazarak başka herhangi bir şeyi yaptığınız gibi verilere bağlanırsınız. .NET uygulamalarında, Visual Studio veri kaynaklarını araştırmak, verileri bellekte depolamak ve işlemek için nesne modelleri oluşturmak ve Kullanıcı arabirimine veri bağlamak için kullanabileceğiniz araçlar sağlar. Microsoft Azure, .NET, Java, Node.js, PHP, Python, Ruby ve mobil uygulamalar için SDK 'Ları ve Azure depolama 'ya bağlanmak için Visual Studio 'daki araçları sağlar.

::: moniker range="vs-2017"
Aşağıdaki listeler, Visual Studio 'dan kullanılabilen birçok veritabanı ve depolama sisteminin yalnızca birkaçını gösterir. [Microsoft Azure](https://azure.microsoft.com/) teklifleri, temel alınan veri deposunun tüm sağlamasını ve yönetimini içeren veri hizmetlerdir. [Visual studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ' deki **Azure geliştirme** Iş yükü, doğrudan Visual Studio 'dan Azure veri depoları ile çalışmanıza olanak sağlar.
::: moniker-end
::: moniker range=">=vs-2019"
Aşağıdaki listeler, Visual Studio 'dan kullanılabilen birçok veritabanı ve depolama sisteminin yalnızca birkaçını gösterir. [Microsoft Azure](https://azure.microsoft.com/) teklifleri, temel alınan veri deposunun tüm sağlamasını ve yönetimini içeren veri hizmetlerdir. [Visual studio 2019](https://visualstudio.microsoft.com/downloads) ' deki **Azure geliştirme** Iş yükü, doğrudan Visual Studio 'dan Azure veri depoları ile çalışmanıza olanak sağlar.
::: moniker-end

![Azure geliştirme iş yükü](media/azure-development-workload.png)

Burada listelenen diğer SQL ve NoSQL veritabanı ürünlerinin çoğu bir yerel makinede, yerel bir ağda veya bir sanal makinede Microsoft Azure barındırılabilecek. Veritabanını Microsoft Azure sanal bir makinede barındırdıysanız, veritabanının kendisini yönetmekten siz sorumlusunuz.

**Microsoft Azure**

- SQL Veritabanı
- Azure Cosmos DB
- Depolama (blob 'lar, tablolar, kuyruklar, dosyalar)
- SQL Veri Ambarı
- SQL Server Stretch Database
- StorSimple
- Ve daha fazlası...

**SQL**

- SQL Server 2005-2016 (Express ve LocalDB 'yi içerir)
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
- NVeritabanı
- Cumentdb |
- Çvendb
- VelocityDB
- Ve daha fazlası...

::: moniker range="vs-2017"

Birçok veritabanı satıcısı ve üçüncü taraf, NuGet paketleri tarafından Visual Studio tümleştirmesini destekler. Teklifleri NuGet.org üzerinde veya Visual Studio 'daki NuGet Paket Yöneticisi aracılığıyla inceleyebilirsiniz ( **Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet Paketlerini Yönet** ). Diğer veritabanı ürünleri, Visual Studio ile bir uzantı olarak tümleştirilir. Bu tekliflere [Visual Studio Market](https://marketplace.visualstudio.com/) gözatabilir veya **Araçlar**  >  **uzantıları ve güncelleştirmeleri** ' ne giderek ve ardından iletişim kutusunun sol bölmesinde **çevrimiçi** ' i seçerek bu teklife gidebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio Için uyumlu veritabanı sistemleri](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Birçok veritabanı satıcısı ve üçüncü taraf, NuGet paketleri tarafından Visual Studio tümleştirmesini destekler. Teklifleri NuGet.org üzerinde veya Visual Studio 'daki NuGet Paket Yöneticisi aracılığıyla inceleyebilirsiniz ( **Araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet Paketlerini Yönet** ). Diğer veritabanı ürünleri, Visual Studio ile bir uzantı olarak tümleştirilir. Bu tekliflerde [Visual Studio Market](https://marketplace.visualstudio.com/) veya **Uzantılar**  >  **Yönet** ' e gidip iletişim kutusunun sol bölmesinde **çevrimiçi** ' i seçerek bu tekliflere gidebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio Için uyumlu veritabanı sistemleri](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> SQL Server 2005 için genişletilmiş destek 12 Nisan 2016 tarihinde sona erdi. Visual Studio 2015 ve üzeri veri araçlarının SQL Server 2005 ile çalışmaya devam edeceğini garanti yoktur. Daha fazla bilgi için [SQL Server 2005 için destek sonu duyurusuna](https://www.microsoft.com/sql-server/sql-server-2005)bakın.

## <a name="net-languages"></a>.NET dilleri

.NET Core dahil olmak üzere tüm .NET veri erişimleri, hem ilişkisel hem de ilişkisel olmayan her türlü veri kaynağına erişim için bir arabirim tanımlayan bir sınıf kümesi olan ADO.NET tabanlıdır. Visual Studio, veritabanlarına bağlanmanıza, verileri işlemenizi ve verileri kullanıcıya sunmanıza yardımcı olmak üzere ADO.NET ile çalışan çeşitli araçlara ve tasarımcılara sahiptir. Bu bölümdeki belgelerde, bu araçların nasıl kullanılacağı açıklanmaktadır. Ayrıca doğrudan ADO.NET komut nesnelerine karşı programlayabilirsiniz. ADO.NET API 'Lerini doğrudan çağırma hakkında daha fazla bilgi için bkz. [ADO.net](/dotnet/framework/data/adonet/index).

ASP.NET ile ilgili veri erişimi belgeleri için bkz. ASP.NET sitesindeki [verilerle çalışma](https://www.asp.net/web-forms/overview/presenting-and-managing-data) . ASP.NET MVC ile Entity Framework kullanmaya yönelik bir öğretici için bkz. [MVC 5 kullanarak Entity Framework 6 Code First](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)kullanmaya başlama.

C# veya Visual Basic Evrensel Windows Platformu (UWP) uygulamaları, Azure depolama ve diğer Azure hizmetlerine erişmek için .NET için Microsoft Azure SDK kullanabilir. Windows. Web. HttpClient sınıfı, herhangi bir yeniden iletişim hizmeti ile iletişime izin verebilir. Daha fazla bilgi için bkz. [Windows. Web. http kullanarak http sunucusuna bağlanma](/previous-versions/windows/apps/dn469430(v=win.10)).

Yerel makinedeki veri depolama için önerilen yaklaşım, uygulamayla aynı işlemde çalışan SQLite ' ı kullanmaktır. Nesne ilişkisel eşleme (ORM) katmanı gerekliyse Entity Framework kullanabilirsiniz. Daha fazla bilgi için bkz. Windows Geliştirici Merkezi 'nde [veri erişimi](/windows/uwp/data-access/index) .

Azure hizmetlerine bağlanıyorsanız en son [Azure SDK araçlarını](https://azure.microsoft.com/downloads/)indirdiğinizden emin olun.

### <a name="data-providers"></a>Veri sağlayıcılar

Bir veritabanının ADO.NET 'de tüketilebilir olması için, özel bir *ADO.NET veri sağlayıcısına* sahip olması veya bir ODBC veya OLE DB arabirimini kullanıma sunması gerekir. Microsoft, SQL Server ürünlerin yanı sıra ODBC ve OLE DB sağlayıcıları için [ADO.NET veri sağlayıcılarının bir listesini](/dotnet/framework/data/adonet/ado-net-overview) sağlar.

### <a name="data-modeling"></a>Veri modelleme

.NET ' te, verileri bir veri kaynağından aldıktan sonra modelleme ve bellekteki verileri düzenleme için üç seçeneğiniz vardır:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Tercih edilen Microsoft ORM teknolojisi. Bunu, birinci sınıf .NET nesneleri olarak ilişkisel verilerle programlama için kullanabilirsiniz. Yeni uygulamalar için, bir model gerektiğinde varsayılan olarak ilk seçenek olmalıdır. Temel ADO.NET sağlayıcısından özel destek gerektirir.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Önceki nesil bir nesne ilişkisel Eşleyici. Daha az karmaşık senaryolar için uygundur, ancak artık etkin bir geliştirme aşamasındadır.

[Veri kümeleri](../data-tools/dataset-tools-in-visual-studio.md) Üç modelleme teknolojisinin en eski sürümü. Bu, öncelikli olarak büyük miktarlarda veri işlemenin veya karmaşık sorgular ya da dönüşümler yerine getirilmesi gereken "veri üzerinden Forms" uygulamalarının hızlı geliştirmesi için tasarlanmıştır. Veri kümesi nesnesi, SQL veritabanı nesnelerine .NET nesnelerinden çok daha fazla benzeyen DataTable ve DataRow nesnelerinden oluşur. SQL veri kaynaklarını temel alan görece basit uygulamalar için, veri kümeleri yine de iyi bir seçenek olabilir.

Bu teknolojilerden herhangi birini kullanma gereksinimi yoktur. Bazı senaryolarda, özellikle performans önemli olduğu durumlarda, veritabanından okumak ve ihtiyacınız olan değerleri liste gibi bir koleksiyon nesnesine kopyalamak için yalnızca bir DataReader nesnesi kullanabilirsiniz \<T> .

## <a name="native-c"></a>Yerel C++

SQL Server bağlanan C++ uygulamaları çoğu durumda [SQL Server Için Microsoft® ODBC sürücü 13,1](https://www.microsoft.com/download/details.aspx?id=53339) ' i kullanmalıdır. Sunucular bağlantısa, OLE DB gereklidir ve [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client)kullanmanız gerekir. Diğer veritabanlarına, [ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017&preserve-view=true) veya OLE DB sürücülerini doğrudan kullanarak erişebilirsiniz. ODBC, geçerli standart veritabanı arabirimidir, ancak çoğu veritabanı sistemi ODBC arabiriminden erişilemeyen özel işlevlere sahiptir. OLE DB, hala desteklenen ancak yeni uygulamalar için önerilmeyen eski bir COM veri erişim teknolojisidir. Daha fazla bilgi için bkz. [Visual C++ veri erişimi](/cpp/data/data-access-in-cpp).

REST hizmetlerini kullanan c++ programları [C++ Rest SDK 'sını](https://github.com/Microsoft/cpprestsdk)kullanabilir.

Microsoft Azure Depolama ile çalışan C++ programları [Microsoft Azure depolama istemcisini](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP)kullanabilir.

Veri modelleme &mdash; Visual Studio, C++ için BIR ORM katmanı sağlamıyor. [ODB](https://www.codesynthesis.com/products/odb/) , C++ için popüler bir açık kaynaklı ORM 'dir.

C++ uygulamalarından veritabanlarına bağlanma hakkında daha fazla bilgi için bkz. [c++ Için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-cpp.md). Eski Visual C++ veri erişimi teknolojileri hakkında daha fazla bilgi için bkz. [veri erişimi](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[Visual Studio 'Da JavaScript](/scripting/javascript/javascript-language-reference) , platformlar arası uygulamalar, UWP uygulamaları, bulut Hizmetleri, Web siteleri ve Web uygulamaları oluşturmak için birinci sınıf bir dildir. En sevdiğiniz JavaScript kitaplıklarını ve veritabanı ürünlerini yüklemek için Visual Studio içinden Bower, Grsıt, Gulp, NPM ve NuGet kullanabilirsiniz. [Azure Web sitesinden](https://azure.microsoft.com/)SDK 'Ları indirerek Azure depolama ve hizmetlere bağlanın. Edge.js, sunucu tarafı JavaScript 'ı (Node.js) ADO.NET veri kaynaklarına bağlayan bir kitaplıktır.

## <a name="python"></a>Python

Python uygulamaları oluşturmak için [Visual Studio 'Da Python desteği '](../python/overview-of-python-tools-for-visual-studio.md) ni yükler. Azure belgelerinin, aşağıdakiler de dahil olmak üzere verilere bağlanmaya yönelik çeşitli öğreticiler vardır:

- [Azure 'da docgo ve SQL veritabanı](/azure/app-service/app-service-web-get-started-python)
- [Azure 'da docgo ve MySQL](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- [Bloblar](/azure/storage/blobs/storage-quickstart-blobs-python), [dosyalar](/azure/storage/files/storage-python-how-to-use-file-storage), [Kuyruklar](/azure/storage/queues/storage-python-how-to-use-queue-storage)ve [Tablolar (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python)ile çalışın.

## <a name="related-topics"></a>İlgili konular

[MICROSOFT AI platformu](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash; Cortana Analytics Suite ve Nesnelerin İnterneti için destek dahil olmak üzere Microsoft Akıllı bulutuna bir giriş sağlar.

[Microsoft Azure depolama](/azure/storage/) &mdash; Azure depolama 'yı ve Azure Blob 'ları, tabloları, kuyrukları ve dosyalarını kullanarak uygulama oluşturmayı açıklar.

[Azure SQL veritabanı](/azure/sql-database/) &mdash; Hizmet olarak ilişkisel bir veritabanı olan Azure SQL veritabanı 'na nasıl bağlanabileceğinizi açıklar.

[SQL Server veri araçları](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; Verilere bağlı uygulamaların ve veritabanlarının tasarımını, araştırmasını, test edilmesini ve dağıtılmasını kolaylaştıran araçları açıklar.

[ADO.net](/dotnet/framework/data/adonet/index) &mdash; ADO.NET mimarisini ve uygulama verilerini yönetmek ve veri kaynaklarıyla ve XML ile etkileşime geçmek için ADO.NET sınıflarının nasıl kullanılacağını açıklar.

[ADO.NET Entity Framework](/ef/ef6/) &mdash; Geliştiricilerin doğrudan ilişkisel bir veritabanına karşı kavramsal bir modelde programlama yapmasına izin veren veri uygulamalarının nasıl oluşturulacağını açıklar.

[WCF Veri Hizmetleri 4,5](/dotnet/framework/data/wcf/index) &mdash; [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]Web 'de veya [Açık Veri Protokolü 'Nü (OData)](https://www.odata.org/)uygulayan bir intranette veri hizmetleri dağıtmak için ' nin nasıl kullanılacağını açıklar.

[Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md) &mdash; Office çözümlerinde verilerin nasıl çalıştığını açıklayan konulara bağlantılar içerir. Burada şema tabanlı programlama, verileri önbelleğe alma ve sunucu tarafında veri erişimi hakkında bilgiler bulunur.

[LINQ (dil Ile tümleşik sorgu)](/dotnet/csharp/linq/) &mdash; C# ve Visual Basic yerleşik sorgu özelliklerini ve ilişkisel veritabanlarını, XML belgelerini, veri kümelerini ve bellek içi koleksiyonları sorgulamak için ortak modeli açıklar.

[Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) &mdash; 'da XML araçları XML verileriyle çalışmayı, XSLT 'yi, .NET XML özelliklerini ve XML sorgusunun mimarisini açıklar.

[XML belgeleri ve verileri](/dotnet/standard/data/xml/index) &mdash; .NET 'teki XML belgeleriyle ve verilerle çalışan kapsamlı ve tümleşik bir sınıf kümesine genel bakış sunar.