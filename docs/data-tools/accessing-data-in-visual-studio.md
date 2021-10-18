---
title: Visual Studio’da verilerle çalışma
description: Visual Studio verilerle çalışın. Yerel makineler, lan 'Lar veya genel veya özel bulutlar üzerinde diğer veritabanı ürünlerinde veya hizmetlerinde bulunan verilere bağlanan uygulamalar oluşturun.
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
ms.openlocfilehash: 24051678c5d17344684c806abde7940bc619b10e
ms.sourcegitcommit: 3cfe24a74b611440b831d9591e067874c51a3bfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2021
ms.locfileid: "130087481"
---
# <a name="work-with-data-in-visual-studio"></a>Visual Studio’da verilerle çalışma

Visual Studio ' de, her bir biçimde, bir yerel makinede, yerel bir ağda veya ortak, özel veya karma bulutta bulunan her türlü veritabanı ürününde veya hizmetinde bulunan verilere bağlanan uygulamalar oluşturabilirsiniz.

JavaScript, Python, PHP, Ruby veya C++ içindeki uygulamalar için, kitaplıkları alarak ve kod yazarak başka herhangi bir şeyi yaptığınız gibi verilere bağlanırsınız. .net uygulamaları için Visual Studio, veri kaynaklarını araştırmak, verileri bellekte depolamak ve işlemek için nesne modelleri oluşturmak ve kullanıcı arabirimine veri bağlamak için kullanabileceğiniz araçlar sağlar. Microsoft Azure, .net, Java, Node.js, PHP, Python, Ruby ve mobil uygulamalar için sdk 'lar ve Azure Depolama 'ye bağlanmak için Visual Studio araçlar sağlar.

::: moniker range="vs-2017"
Aşağıdaki listeler, Visual Studio kullanılabilecek birçok veritabanı ve depolama sisteminin yalnızca birkaçını gösterir. [Microsoft Azure](https://azure.microsoft.com/) teklifleri, temel alınan veri deposunun tüm sağlamasını ve yönetimini içeren veri hizmetlerdir. [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ' deki **azure geliştirme** iş yükü, doğrudan Visual Studio azure veri depolarıyla çalışmanıza olanak sağlar.
::: moniker-end
::: moniker range=">=vs-2019"
Aşağıdaki listeler, Visual Studio kullanılabilecek birçok veritabanı ve depolama sisteminin yalnızca birkaçını gösterir. [Microsoft Azure](https://azure.microsoft.com/) teklifleri, temel alınan veri deposunun tüm sağlamasını ve yönetimini içeren veri hizmetlerdir. [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) ' deki **azure geliştirme** iş yükü, doğrudan Visual Studio azure veri depolarıyla çalışmanıza olanak sağlar.
::: moniker-end

![Azure geliştirme iş yükü](media/azure-development-workload.png)

burada listelenen diğer SQL ve nosql veritabanı ürünlerinin çoğu bir yerel makinede, yerel bir ağda veya bir sanal makinede Microsoft Azure barındırılabilir. veritabanını Microsoft Azure sanal bir makinede barındırdıysanız, veritabanının kendisini yönetmekten siz sorumlusunuz.

**Microsoft Azure**

- SQL Veritabanı
- Azure Cosmos DB
- Depolama (bloblar, tablolar, kuyruklar, dosyalar)
- SQL Veri Ambarı
- SQL Server Stretch Database
- StorSimple
- Ve daha fazlası...

**SQL**

- SQL Server 2005-2016 (Express ve localdb 'yi içerir)
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

birçok veritabanı satıcısı ve üçüncü taraf, NuGet paketlere göre tümleştirmeyi Visual Studio destekler. teklifleri nuget.org üzerinde veya NuGet Visual Studio Paket Yöneticisi aracılığıyla inceleyebilirsiniz (**araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet paketleri yönetme**). diğer veritabanı ürünleri, bir uzantı olarak Visual Studio ile tümleşir. [Visual Studio markette](https://marketplace.visualstudio.com/) bu tekliflere gözatabilir veya **araçlar**  >  **uzantıları ve güncelleştirmeleri** ' ne giderek iletişim kutusunun sol bölmesinde **çevrimiçi** ' i seçerek bu teklife gidebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio Için uyumlu veritabanı sistemleri](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

birçok veritabanı satıcısı ve üçüncü taraf, NuGet paketlere göre tümleştirmeyi Visual Studio destekler. teklifleri nuget.org üzerinde veya NuGet Visual Studio Paket Yöneticisi aracılığıyla inceleyebilirsiniz (**araçlar**  >  **NuGet Paket Yöneticisi**  >  **çözüm için NuGet paketleri yönetme**). diğer veritabanı ürünleri, bir uzantı olarak Visual Studio ile tümleşir. [Visual Studio markette](https://marketplace.visualstudio.com/) bu tekliflere gözatıp **, uzantıları yönet ' e giderek**  >   iletişim kutusunun sol bölmesinde **çevrimiçi** ' i seçerek bu teklife gidebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio Için uyumlu veritabanı sistemleri](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> SQL Server 2005 için genişletilmiş destek 12 nisan 2016 tarihinde sona erdi. Visual Studio 2015 ve sonraki sürümlerde bulunan veri araçlarının 2005 SQL Server çalışmaya devam edeceğini garanti yoktur. daha fazla bilgi için [SQL Server 2005 için destek sonu duyurusuna](https://www.microsoft.com/sql-server/sql-server-2005)bakın.

## <a name="net-languages"></a>.NET dilleri

.net Core dahil olmak üzere tüm .net veri erişimleri, hem ilişkisel hem de ilişkisel olmayan her türlü veri kaynağına erişmek için bir arabirim tanımlayan bir sınıf kümesi olan ADO.NET tabanlıdır. Visual Studio, veritabanlarına bağlanmanıza, verileri işlemenizi ve verileri kullanıcıya sunmanıza yardımcı olmak üzere ADO.NET birlikte çalışan çeşitli araçlara ve tasarımcılara sahiptir. Bu bölümdeki belgelerde, bu araçların nasıl kullanılacağı açıklanmaktadır. ayrıca, doğrudan ADO.NET komut nesnelerine karşı programlayabilirsiniz. ADO.NET apı 'lerini doğrudan çağırma hakkında daha fazla bilgi için bkz. [ADO.NET](/dotnet/framework/data/adonet/index).

ASP.NET ilgili veri erişimi belgeleri için, bkz. ASP.NET sitesindeki [verilerle çalışma](https://www.asp.net/web-forms/overview/presenting-and-managing-data) . ASP.NET mvc ile Entity Framework kullanmaya yönelik bir öğretici için bkz. [mvc 5 kullanarak Entity Framework 6 Code First](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)kullanmaya başlama.

C# veya Visual Basic Evrensel Windows Platformu (UWP) uygulamaları, .NET için Microsoft Azure SDK Azure Depolama ve diğer azure hizmetlerine erişmek için kullanabilir. Windows. Web. HttpClient sınıfı, herhangi bir yeniden iletişim hizmeti ile iletişime izin verebilir. Daha fazla bilgi için bkz [. Windows kullanarak http sunucusuna bağlanma. Web. http](/previous-versions/windows/apps/dn469430(v=win.10)).

Yerel makinedeki veri depolama için önerilen yaklaşım, uygulamayla aynı işlemde çalışan SQLite ' ı kullanmaktır. Nesne ilişkisel eşleme (ORM) katmanı gerekliyse Entity Framework kullanabilirsiniz. daha fazla bilgi için bkz. Windows geliştirici merkezi 'nde [veri erişimi](/windows/uwp/data-access/index) .

Azure hizmetlerine bağlanıyorsanız en son [Azure SDK araçlarını](https://azure.microsoft.com/downloads/)indirdiğinizden emin olun.

### <a name="data-providers"></a>Veri sağlayıcılar

bir veritabanının ADO.NET tüketilebilir olması için, özel bir *ADO.NET veri sağlayıcısına* sahip olması veya bir ODBC veya OLE DB arabirimini kullanıma sunması gerekir. Microsoft, SQL Server ürünlerin yanı sıra ODBC ve OLE DB sağlayıcıları için [ADO.NET veri sağlayıcılarının bir listesini](/dotnet/framework/data/adonet/ado-net-overview) sağlar.

::: moniker range=">=vs-2022"
> [!NOTE]
> OLEDB veya ODBC veri sağlayıcılarına bağlanmak için Visual Studio 2022 kullanıyorsanız, Visual Studio 2022 ' nin artık 64-bit işlemi olduğunu bilmeniz gerekir.
>
> bu, Visual Studio 'deki bazı veri araçlarının 32 bit veri sağlayıcıları kullanarak OLEDB veya ODBC veritabanlarına bağlanamadığını gösterir. Bu, Microsoft Access 32-bit OLEDB veri sağlayıcısı 'nın yanı sıra diğer üçüncü taraf 32 bit sağlayıcıları da içerir.
>
>OLEDB veya ODBC 'ye bağlanan 32 bitlik uygulamaları korumanız gerekiyorsa, uygulamayı yine de Visual Studio 2022 ile derleyip çalıştırabilirsiniz. ancak, Sunucu Gezgini, veri kaynağı sihirbazı veya veri kümesi tasarımcısı gibi Visual Studio veri araçlarından birini kullanmanız gerekiyorsa, hala 32 bitlik bir işlem olan Visual Studio önceki bir sürümünü kullanmanız gerekir. 32 bitlik bir işlem olan Visual Studio son sürümü 2019 Visual Studio.
>
>Projeyi 64 bitlik bir işlem olarak dönüştürmeyi planlıyorsanız,, 64 bit veri sağlayıcılarını kullanmak için OLEDB ve ODBC veri bağlantılarını güncelleştirmeniz gerekir.
>
>Uygulamanız Microsoft Access veritabanları kullanıyorsa ve projeyi 64 bit 'e dönüştürebiliyorsanız, erişim bağlantı altyapısı (ACE) olarak da adlandırılan 64 bit Microsoft Access veritabanı altyapısını kullanmanız önerilir. Lütfen bkz. [Jet için OLE DB sağlayıcısı ve ODBC sürücüsü yalnızca](/office/troubleshoot/access/jet-odbc-driver-available-32-bit-version) daha fazla bilgi için 32 bitlik sürümleridir.
>
>Üçüncü taraf veri sağlayıcısı kullanıyorsanız, projeyi 64 bit 'e dönüştürmeden önce 64 bitlik bir sağlayıcı sunduklarında, satıcınızla bağlantı kurmanızı öneririz.

::: moniker-end

### <a name="data-modeling"></a>Veri modelleme

.NET ' te, verileri bir veri kaynağından aldıktan sonra modelleme ve bellekteki verileri düzenleme için üç seçeneğiniz vardır:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Tercih edilen Microsoft ORM teknolojisi. Bunu, birinci sınıf .NET nesneleri olarak ilişkisel verilerle programlama için kullanabilirsiniz. Yeni uygulamalar için, bir model gerektiğinde varsayılan olarak ilk seçenek olmalıdır. temel alınan ADO.NET sağlayıcısından özel destek gerektirir.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Önceki nesil bir nesne ilişkisel Eşleyici. Daha az karmaşık senaryolar için uygundur, ancak artık etkin bir geliştirme aşamasındadır.

[Veri kümeleri](../data-tools/dataset-tools-in-visual-studio.md) Üç modelleme teknolojisinin en eski sürümü. Bu, öncelikli olarak büyük miktarlarda veri işlemenin veya karmaşık sorgular ya da dönüşümler yerine getirilmesi gereken "veri üzerinden Forms" uygulamalarının hızlı geliştirmesi için tasarlanmıştır. veri kümesi nesnesi, veritabanı nesneleri SQL .net nesnelerinden çok daha fazla mantıksal olarak benzeyen DataTable ve DataRow nesnelerinden oluşur. SQL veri kaynaklarına dayalı görece basit uygulamalar için, veri kümeleri yine de iyi bir seçim olabilir.

Bu teknolojilerden herhangi birini kullanma gereksinimi yoktur. Bazı senaryolarda, özellikle performans önemli olduğu durumlarda, veritabanından okumak ve ihtiyacınız olan değerleri liste gibi bir koleksiyon nesnesine kopyalamak için yalnızca bir DataReader nesnesi kullanabilirsiniz \<T> .

## <a name="native-c"></a>Yerel C++

SQL Server bağlanan C++ uygulamaları çoğu durumda [SQL Server için Microsoft® ODBC sürücü 13,1](https://www.microsoft.com/download/details.aspx?id=53339) ' i kullanmalıdır. Sunucular bağlı ise, OLE DB gerekli olur ve bunun için [SQL Server Native Client.](/sql/relational-databases/native-client/sql-server-native-client) ODBC veya sürücülerini doğrudan kullanarak [diğer](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017&preserve-view=true) OLE DB erişebilirsiniz. ODBC geçerli standart veritabanı arabirimidir, ancak çoğu veritabanı sistemi ODBC arabirimi aracılığıyla erişilemedi özel işlevler sağlar. OLE DB, hala desteklenen ancak yeni uygulamalar için önerilmez olan eski bir COM veri erişimi teknolojisidir. Daha fazla bilgi için [bkz. Visual C++.](/cpp/data/data-access-in-cpp)

REST hizmetlerini kullanan C++ programları [C++ REST SDK'sı kullanabilir.](https://github.com/Microsoft/cpprestsdk)

Microsoft Azure Depolama ile Microsoft Azure Depolama [C++ programları.](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP)

Veri &mdash; Visual Studio, C++ için bir ORM katmanı sağlamaz. [ODB,](https://www.codesynthesis.com/products/odb/) C++ için popüler bir açık kaynak ORM'dir.

C++ uygulamalarıyla veritabanlarına bağlanma hakkında daha fazla bilgi edinmek için [bkz. C++ Visual Studio araçlarına bağlanma.](../data-tools/visual-studio-data-tools-for-cpp.md) Eski veri erişimi teknolojileri Visual C++ daha fazla bilgi için bkz. [Veri Erişimi.](/cpp/data/data-access-in-cpp)

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

[SQL Server Veri Araçları](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; Veri bağlantılı uygulamalar ve veritabanlarının tasarımını, araştırmalarını, testlerini ve dağıtmalarını kolaylaştıran araçları açıklar.

[ADO.NET](/dotnet/framework/data/adonet/index) &mdash; Uygulama mimarisini ADO.NET uygulama verilerini yönetmek ve veri kaynakları ADO.NET XML ile etkileşim kurmak için ADO.NET sınıflarını kullanmayı açıklar.

[ADO.NET Entity Framework](/ef/ef6/) &mdash; Geliştiricilerin doğrudan ilişkisel veritabanı yerine kavramsal bir modele göre program oluşturmasına olanak sağlayan veri uygulamalarının nasıl oluşturul açıklanacak?

[WCF Veri Hizmetleri 4.5](/dotnet/framework/data/wcf/index) &mdash; Web'de veya Açık [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] Veri [Protokolü'nü (OData)](https://www.odata.org/)uygulayan bir intranette veri hizmetlerini dağıtmak için kullanmayı açıklar.

[Office Çözümlerde Veriler](../vsto/data-in-office-solutions.md) &mdash; Verilerin çözümlerde nasıl çalıştığını açıklayan konuların bağlantılarını Office içerir. Burada şema tabanlı programlama, verileri önbelleğe alma ve sunucu tarafında veri erişimi hakkında bilgiler bulunur.

[LINQ (Dille Tümleşik Sorgu)](/dotnet/csharp/linq/) &mdash; C# ve Visual Basic yerleşik sorgu özelliklerini ve ilişkisel veritabanlarını, XML belgelerini, veri kümelerini ve bellek içinde koleksiyonları sorgulamaya ilişkin ortak modeli açıklar.

[Visual Studio'de XML Araçları](../xml-tools/xml-tools-in-visual-studio.md) &mdash; XML verileriyle çalışmayı, XSLT'de hata ayıklamayı, .NET XML özelliklerini ve XML Sorgusu mimarisini ele almaktadır.

[XML Belgeleri ve Verileri](/dotnet/standard/data/xml/index) &mdash; .NET'te XML belgeleri ve verileriyle birlikte çalışmak için kapsamlı ve tümleşik bir sınıf kümesine genel bakış sağlar.
