---
title: R ile SQL Server tümleştirme
description: Visual Studio, R'den SQL sorgular oluşturmayı ve çalıştırmayı ve R'nin saklı yordamlarla çalışma becerisini destekler.
ms.date: 06/25/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: d391f5dc6e02403366a7646bb6bc103d12cc2248
ms.sourcegitcommit: dcecc0ed37b5e976b5dc83c5128ba5ecc8bc04b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2022
ms.locfileid: "135750884"
---
# <a name="work-with-sql-server-and-r"></a>SQL Server ve R ile çalışma

Visual Studio desteği, SQL Server sorguları oluşturma ve çalıştırma ve saklı yordamlarla çalışma olanağı SQL R ve SQL SQL veritabanlarıyla çalışmalarına yardımcı olur.

> [!Note]
> SQL ve R ile birlikte çalışmak için aşağıdaki SQL Server Veri Araçları yüklü olması gerekir:
> - Visual Studio 2017: Visual Studio yükleyicisini çalıştırın ve Veri araçları'nın da dahil olduğu Veri depolama ve işleme SQL Server seçin.
> - Visual Studio 2015: İndirme [yönergelerini](/sql/ssdt/download-sql-server-data-tools-ssdt)SQL Server Veri Araçları.

:::row:::
    :::column:::
        ![video için film kamerası simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için")
    :::column-end:::
    :::column:::
        SQL Server ve R'ye (3m 03s) genel bakış için bir [video (youtube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) izleyin.
    :::column-end:::
:::row-end:::

## <a name="create-and-run-sql-queries"></a>Sorgu oluşturma SQL çalıştırma

RTVS, SQL sonuçları alıncaya kadar ayrı bir bağlamda SQL sorgular geliştirmenize olanak sağlayarak R projelerine farklı sorgular eklemeyi destekler.

Bir sorgu SQL eklemek için, Çözüm Gezgini'de projeye sağ tıklayın, Yeni Öğe Ekle'yi seçin ve  >  SQL **Sorgu dosyası** türünü seçin:

![Projeye SQL Sorgu öğesi ekleme](media/sql-add-item.png)

Bu komut, Visual Studio için tam Intelli SQL Sense SQL ve sorgu çalıştırma olanağı sağlayan Transact-SQL düzenleyicisinde dosyasını açar. Bu özelliklerin çalışması için, düzenleyicinin araç çubuğundaki bağlan düğmesini kullanarak bir veritabanına bağlanmanız veya bir sorgu çalıştırmayı denemeniz gerekir (**Ctrl** Shift E , seçimde de +  + çalışır). Her iki şekilde de bağlantı iletişim kutusu görüntülenir:

![SQL bağlantı iletişim kutusu](media/sql-connection-dialog.png)

Bağlantı kurulduktan sonra sorguları çalıştırarak sonuçları abilirsiniz:

![SQL penceresi sorgu sonuçları](media/sql-query-results.png)

Transact-SQL düzenleyicisi, sorgunun yürütme planını görüntüleme ve sorgu hata ayıklayıcısı gibi çeşitli diğer özellikleri destekler.
Daha fazla bilgi için [bkz. Betikleri Düzenlemek ve yürütmek SQL Transact-SQL Düzenleyicisi'ni kullanma.](/previous-versions/sql/sql-server-data-tools/hh272706(v=vs.103))

## <a name="work-with-sql-server-stored-procedures"></a>Saklı yordamlarla SQL Server çalışma

[SQL Server R Services](/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 ve sonrası), bir T-SQL saklı yordamından R kodu eklemenizi ve çalıştırmayı sağlar. R kodunu bir SQL Server bilgisayarda çalıştırabilir, SQL sorgusundan döndürülen veriler üzerinde çalıştırabilir ve daha fazla SQL tarafından işlenecek veya istemciye döndürülecek bir SQL sonuç kümesi oluşturabilirsiniz.

RTVS, aşağıdaki bölümlerde açıklandığı gibi tek bir SQL ve R kodunu tek bir SQL deyiminde birleştirmeye ilişkin aksi halde kullandırılamaz ve hataya açık işlemi basitleştirmektedir:

- [Veritabanı bağlantısı ekleme](#add-a-database-connection)
- [Saklı yordamda SQL ve test edin](#write-and-test-a-sql-stored-procedure)
- [Saklı yordam SQL yayımlama](#publish-a-sql-stored-procedure)

:::row:::
    :::column:::
        ![video için film kamerası simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için")
    :::column-end:::
    :::column:::
        R ve youtube.com saklı yordamlara (6m 09 SQL genel bakış için bir [video izleyin.)](https://www.youtube.com/watch?v=dFKIT2OitWQ)
    :::column-end:::
:::row-end:::

### <a name="add-a-database-connection"></a>Veritabanı bağlantısı ekleme

1. Bağlantı **Özellikleri iletişim** kutusunu açmak için R Araçları Veri Veritabanı Bağlantısı  >    >   **Ekle'yi** seçin. Burada veri kaynağının adını (SQL Server), sunucunun adını, kimlik doğrulama modunu ve veritabanının adını belirtirsiniz. İletişim **kutusunu kapatmadan** önce girişinizi doğrulamak için Bağlantıyı Sına'ya seçin.

    ![SQL Bağlantı İletişim Kutusu](media/sql-connection-string-dialog.png)

1. Geçerli bir **bağlantıyla** Tamam'ı Visual Studio yeni ayarlarda adlı bir `dbConnection` bağlantı dizesi *oluşturulur. R* dosyası. RTVS bu dosyayı otomatik olarak kullanır (çalıştırır), böylece R betiklerinden bağlantıyı hemen kullanabilirsiniz:

![SQL Ayarlar. R dosyası](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Saklı yordamda SQL ve test edin

Saklı Yordamda yeni SQL eklemek için projenize sağ tıklayın, Yeni Öğe Ekle'yi seçin, şablon listesinden R ile Saklı Yordam'ı SQL Saklı Yordam'ı seçin, dosyaya bir ad girin ve  >  Tamam'ı **seçin.**  Varsayılan dosya adı *SqlSProc.R'dır;* okuma kolaylığı için, bu bölümün geri kalanında *StoredProcedure.R* dosya adı kullanılır. Birden çok saklı yordam varsa, her dosyanın benzersiz bir dosya adı olmalıdır.

RTVS saklı yordam için üç dosya oluşturur: bir *. R* kodunuz için R dosyası, bir *. SQL için Query.sql* dosyası ve *. İki dosyayı birleştiren Template.sql* dosyası. İkinci ikisi, Çözüm Gezgini olarak *görünür. R* dosyası:

![Çözüm Gezgini Saklı Yordamın R SQL genişletilmiş görünümü](media/sql-solution-explorer-expanded.png)

. *R* dosyası (*Bu örnekte StoredProcedure.R)* R kodu yazmak için buraya yazın. Varsayılan içerikler:

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

Basitçe ifade etmek gerekirse, kod adlı bir R veri çerçevesi alır ve şablon kodu yalnızca girişi çıkışa kopyalayıp sonuçlarını `InputDataSet` `OutputDataSet` içinde döndürür.

> [!Note]
> Bu veri çerçevelerinin adları, sistem saklı `@input_data_1_name` `@output_data_1_name` yordamına yapılan çağrıda ve `sp_execute_external_script` parametreleri tarafından denetlenmektedir. Bu çağırma kuralı tasarımı hakkında daha fazla ayrıntı ve kullanımına ilişkin bazı örnekler için bkz. [sp_execute_external_script (Transact-SQL).](/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)

Oluşturulan diğer kod (açıklamalarda), SQL deyimini SQL Server'a iletmek, çalıştırmak ve sonuç kümesi olarak R veri çerçevesi olarak almak için [RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) paketini kullanan küçük bir test betiği sağlar. R kodunuzu bu test kodundan elde edilen sonuç kümesine karşı etkileşimli olarak yazmak için bu test kodunun SQL Server.

. *Query.sql* dosyası (bu örnekte *StoredProcedure.Query.sql),* verilerini oluşturan sorguyu SQL ve test etmek için `InputDataSet` kullanılır. Bu *.sql dosyasıyla,* düzenleyici size tüm normal Transact-SQL özelliklerini sağlar.

Uygulama kodunuzdan memnun *SQL.sql* dosyasını için açık düzenleyiciye sürükleyerek R kodunuzla tümleştirin. *R* dosyası. Aşağıdaki görüntüde *StoredProcedure.Query.sql,* içinde virgülden sonra *StoredProcedure.R'de* bir noktaya sürüklendi: `sqlQuery(channel, )`

![Bir SQL R Dize Değişkenine Okuma](media/sql-reference-sql-file-from-r.png)

Gördüğünüz gibi bu basit adım otomatik olarak R kodu kullanarak *.sql* dosyasını açar, içeriğini bir dizeye okur ve bu kodu rodbc paketine iletir ve bu kodu SQL Server.

Artık veri çerçevesini istediğiniz gibi yönlendiren R kodunu `InputDataSet` etkileşimli olarak yazabilirsiniz. Düzenleyicide R kodunu seçerek Ctrl Enter tuşuna basarak bunu [etkileşimli pencereye](interactive-repl-for-r-in-visual-studio.md) **gönderebilirsiniz.** + 

. *Template.sql* dosyası (bu örnekte *StoredProcedure.Template.sql),* son olarak saklı saklı yordamınızı oluşturmak SQL içerir:

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- yer `_RCODE_` tutucusu, içeriğinin ile *değiştirilir. R* dosyası (örneğin, *StoredProcedure.R*).
- yer `_INPUT_QUERY_` tutucusu, içeriğinin ile *değiştirilir. Query.sql* dosyası (örneğin, *StoredProcedure.Query.sql).*
- Saklı `WITH RESULT SETS` yordamdan döndürülen sonuç kümesi şemasını açıklamak için yan tümcesini düzenleyin. Saklı yordamın `OutputDataSet` çağırana geri dönmek istediğiniz veri çerçevesinden sütunları özellikle tanımlama.

Örneğin, aşağıdaki sorgu için:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Dönüş değerlerinin veri `WITH RESULT SETS` türlerini belirtmek için aşağıdaki yan tümcesini kullanırsınız:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Saklı yordam SQL yayımlama

1. R Araçları **Veri Yayımlama**  >    >  **seçenekleriyle yayımla menü** komutunu seçin.
1. Görüntülenen iletişim kutusunda Yayımla seçeneğini  **Veritabanı** olarak değiştirerek hedefi belirtin, Yayımla'yı seçin ve RTVS saklı yordamı oluşturur ve yayımlar:

    ![Saklı yordamı yayımla iletişim kutusu](media/sql-publish-with-options.png)

1. Bir projede tüm saklı yordamları yayımlamak için, R **Araçları** Verileri Saklı Yordamları Yayımla komutunu kullanabilirsiniz. Bu  >    >   komut, Çözüm Gezgini.

> [!Tip]
> SQL Server Nesne Gezgini açık Visual Studio saklı yordamınız, veritabanınıza **ilişkin Programlanabilir** Saklı Yordamlar  >   klasöründe görünür. Ayrıca sağ tıklar ve Yordamı Yürüt'Nesne Gezgini seçerek veya *bir .sql* sorgu penceresinden etkileşimli olarak çağırarak da bu sorguyu doğrudan çalıştırabilirsiniz.