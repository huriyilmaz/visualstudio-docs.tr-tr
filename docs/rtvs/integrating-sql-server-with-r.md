---
title: SQL Server R ile tümleştirme
description: Visual Studio, R 'den SQL sorguları oluşturmayı ve çalıştırmayı ve R 'nin Saklı yordamlarla çalışma özelliğini destekler.
ms.date: 06/25/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 10b5dfee629b5b6e67ab544ca0bdd905ed2a120a
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888452"
---
# <a name="work-with-sql-server-and-r"></a>SQL Server ve R ile çalışma

Visual Studio 'nun SQL Server için mükemmel bir desteği, veri bilimcilerinin SQL sorguları oluşturup çalıştırma ve saklı yordamlarla çalışma yeteneği aracılığıyla R ve SQL veritabanları ile çalışmasına yardımcı olur.

> [!Note]
> SQL ve R ile birlikte çalışmak için SQL Server Veri Araçları yüklü olmalıdır:
> - Visual Studio 2017: Visual Studio yükleyicisi 'ni çalıştırın ve veri depolama ve işleme iş yükünü (SQL Server veri araçları dahil) seçin.
> - Visual Studio 2015: [indirme SQL Server veri araçları](/sql/ssdt/download-sql-server-data-tools-ssdt)yönergeleri izleyin.

|   |   |
|---|---|
| ![video için film kamerası simgesi](../install/media/video-icon.png "Video izleyin") | SQL Server ve R (3M 03s) genel bakışı için [bir video (YouTube.com) izleyin](https://www.youtube.com/watch?v=n4AYr0QIwdQ) . |

## <a name="create-and-run-sql-queries"></a>SQL sorguları oluşturma ve çalıştırma

RTVS, R projelerine SQL sorguları eklemeyi destekler. böylece, aradığınız sonuçları elde edene kadar SQL sorgularını ayrı bir bağlamda bir şekilde geliştirebilirsiniz.

Bir SQL sorgu dosyası eklemek için Çözüm Gezgini ' de projeye sağ tıklayın, > **Yeni öğe** **Ekle** ' yi seçin ve **SQL sorgu** dosyası türünü seçin:

![Projeye SQL sorgu öğesi ekleme](media/sql-add-item.png)

Bu komut, Visual Studio 'nun Transact-SQL düzenleyicisinde, SQL için tam IntelliSense sağlayan ve sorguları çalıştırabilme olanağı sunan dosyayı açar. Bu özelliklerin çalışması için, düzenleyicinin araç çubuğundaki Bağlan düğmesini kullanarak bir veritabanına bağlanmanız veya bir sorgu çalıştırmayı denemeniz gerekir (aynı zamanda bir seçimde da çalışan) (**Ctrl**+**SHIFT**+**E** Her iki yöntem de bağlantı iletişim kutusunu getirir:

![SQL bağlantısı iletişim kutusu](media/sql-connection-dialog.png)

Bağlantı kurulduktan sonra sorguları çalıştırabilir ve sonuçları görebilirsiniz:

![SQL penceresi sorgu sonuçları](media/sql-query-results.png)

Transact-SQL Düzenleyicisi, sorgu için yürütme planını ve sorgu hata ayıklayıcısını görüntüleme gibi diğer birçok özelliği destekler.
Daha fazla bilgi için bkz. [komut dosyalarını düzenlemek ve yürütmek Için Transact-SQL düzenleyicisini kullanma](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="work-with-sql-server-stored-procedures"></a>SQL Server saklı yordamlarla çalışma

[SQL Server R Services](/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 ve üzeri) bir T-SQL saklı yordamından R kodu eklemenizi ve çalıştırmanızı sağlar. R kodunu bir SQL Server bilgisayarda çalıştırabilir, bir SQL sorgusundan döndürülen veriler üzerinde çalışabilir ve daha fazla SQL tarafından işlenebilecek veya istemciye geri döndürülebilecek bir SQL sonuç kümesi oluşturabilirsiniz.

RTVS, SQL ve R Code 'u aşağıdaki bölümlerde açıklandığı gibi tek bir SQL deyimindeki birleştirmek için, aksi durumda ve hataya açık bir işlemi basitleştirir:

- [Veritabanı bağlantısı ekleme](#add-a-database-connection)
- [Bir SQL saklı yordamını yazma ve test etme](#write-and-test-a-sql-stored-procedure)
- [Bir SQL saklı yordamı yayımlama](#publish-a-sql-stored-procedure)

|   |   |
|---|---|
| ![video için film kamerası simgesi](../install/media/video-icon.png "Video izleyin") | R ve SQL saklı yordamlarına (6m 09s) genel bakış için [bir video (YouTube.com) izleyin](https://www.youtube.com/watch?v=dFKIT2OitWQ) . |

### <a name="add-a-database-connection"></a>Veritabanı bağlantısı ekleme

1. **R araçları** > **veri** > **veritabanı bağlantısı ekle** ' yi seçerek **bağlantı özellikleri** iletişim kutusunu açın. Burada, veri kaynağının adını (Bu durumda SQL Server), sunucunun adını, kimlik doğrulama modunu ve veritabanının adını belirtirsiniz. İletişim kutusunu kapatmadan önce girişinizi doğrulamak için **Bağlantıyı Sına** ' yı seçin.

    ![SQL bağlantısı Iletişim kutusu](media/sql-connection-string-dialog.png)

1. Geçerli bir bağlantıyla **Tamam** ' ı seçtiğinizde, Visual Studio yeni ayarlarda `dbConnection` adlı bir bağlantı dizesi oluşturur *. R* dosyası. RTVS, bu dosyayı otomatik olarak kaynaklar (çalıştırır). böylece, R betiklerinden gelen bağlantıyı hemen kullanabilirsiniz:

![SQL Settings. R dosyası](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Bir SQL saklı yordamını yazma ve test etme

Yeni bir SQL saklı yordamı eklemek için projenize sağ tıklayın, > **Yeni öğe** **Ekle** ' yi seçin, şablon listesinden **R ile SQL saklı yordamı** ' nı seçin, dosyaya bir ad verin ve **Tamam**' ı seçin. Varsayılan dosya adı *Sqlsproc. R*; okumayı kolaylaştırmak için, bu bölümün geri kalanında *StoredProcedure. R* dosya adı kullanılır. Birden çok saklı yordamdıysanız, her dosyanın benzersiz bir dosya adı olması gerekir.

RTVS, saklı yordam için üç dosya oluşturur: a *.* R kodunuz için r dosyası, a *. SQL kodu için Query. SQL* dosyası ve bir *. İkisini birleştiren Template. SQL* dosyası. Bunlar ikinci ikisi, ' ın alt öğesi olarak Çözüm Gezgini görünür *. R* dosyası:

![R ile SQL saklı yordamının genişletilmiş görünümünü Çözüm Gezgini](media/sql-solution-explorer-expanded.png)

*. R dosyası* (*StoredProcedure. r* Bu örnek), r kodunu yazdığınız yerdir. Varsayılan içerikler şunlardır:

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

Tek bir deyişle, kod `InputDataSet` adlı bir R dataframe alır ve `OutputDataSet`sonucunu, şablon kodu yalnızca çıktıyı çıkışa kopyalayarak geri döndürür.

> [!Note]
> Bu veri çerçevelerinin adları, `sp_execute_external_script` sistemi saklı yordamına yapılan çağrıda `@input_data_1_name` ve `@output_data_1_name` parametreleri tarafından denetlenir. Bu çağırma kuralının tasarımıyla ilgili daha ayrıntılı bilgi ve bunların kullanımına ilişkin bazı örnekler için bkz. [sp_execute_external_script (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Oluşturulan diğer kod (açıklamalarda), bir SQL deyimini iletmek için SQL Server, çalıştırmak için [Rodbc paketini](https://cran.r-project.org/web/packages/RODBC/index.html) kullanan küçük bir test betiği sağlar ve sonuç kümesini bir R veri çerçevesi olarak alır. SQL Server aldığınız sonuç kümesine göre R kodunuzu etkileşimli olarak yazmak için bu test kodunun açıklamasını kaldırabilirsiniz.

*. Query. SQL* dosyası (Bu örnekteki*StoredProcedure. Query. sql* ) `InputDataSet`IÇIN veri üreten SQL sorgusunu yazdığınızda ve test edersiniz. Bu *. SQL* dosyası ile düzenleyici, tüm olağan Transact-SQL özelliklerini size sağlar.

SQL kodunuzun kutlu olsun, *. SQL* dosyasını ' a yönelik açık düzenleyiciye sürükleyerek R kodunuzla tümleştirin *. R* dosyası. Aşağıdaki görüntüde, *StoredProcedure. Query. SQL* , `sqlQuery(channel, )`virgülden sonra *StoredProcedure. R* içindeki noktaya sürüklenmiştir:

![SQL dosyası R dize değişkenine okunuyor](media/sql-reference-sql-file-from-r.png)

Gördüğünüz gibi bu basit adım, *. SQL* dosyasını açmak, içeriğini bir dizeye okumak ve SQL Server göndermek için rodbc paketine geçirmek üzere R kodu otomatik olarak oluşturur.

Artık `InputDataSet` veri çerçevesini istediğiniz şekilde işleyen R kodunu etkileşimli olarak yazabilirsiniz. Düzenleyicide yalnızca R kodunu seçip **Ctrl**+**ENTER**tuşlarına basarak [etkileşimli pencereye](interactive-repl-for-r-in-visual-studio.md) gönderebilirsiniz.

*. Şablon. SQL* dosyası (Bu örnekteki*StoredProcedure. Template. SQL* ), son olarak SQL saklı yordamınız oluşturmaya yönelik şablonu içerir:

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

- `_RCODE_` yer tutucusu, ' nin içeriğiyle değiştirilmiştir *. R* dosyası (örneğin, *StoredProcedure. R*).
- `_INPUT_QUERY_` yer tutucusu, ' nin içeriğiyle değiştirilmiştir *. Sorgu. SQL* dosyası (örneğin, *StoredProcedure. Query. SQL*).
- Saklı yordamda döndürülen sonuç kümesinin şemasını tanımlayacak `WITH RESULT SETS` yan tümcesini düzenleyin. Saklı yordamın çağıranına döndürmek istediğiniz `OutputDataSet` veri çerçevesindeki sütunları özel olarak belirler.

Örneğin, aşağıdaki sorgu için:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Dönüş değerlerinin veri türlerini belirtmek için aşağıdaki `WITH RESULT SETS` yan tümcesini kullanacaksınız:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Bir SQL saklı yordamı yayımlama

1. Seçenekler menü komutuyla **yayımla** > **veri** > **R araçları** ' nı seçin.
1. Görüntülenen iletişim kutusunda, **Yayımla olarak değiştir:** **veritabanına**, hedefi belirtin, **Yayımla**' yı seçin ve rtvs derlemeleri ve saklı yordamı yayımlar:

    ![Saklı yordam Yayımla iletişim kutusu](media/sql-publish-with-options.png)

1. Bir projedeki tüm saklı yordamları yayımlamak için, Çözüm Gezgini ' de projeye sağ tıkladığınızda da kullanılabilir olan **R araçları** > **verileri** > **saklı yordamları Yayımla** komutunu kullanabilirsiniz.

> [!Tip]
> Visual Studio 'da SQL Server Nesne Gezgini açıksa, yayımlanmış saklı yordamınız veritabanınızın **programlama** > **saklı yordamları** klasöründe görüntülenir. Ayrıca, yordamı Çalıştır ' ı sağ tıklayıp, **yordamı**Çalıştır ' ı seçerek veya bir *. SQL* sorgu penceresinden etkileşimli olarak çağırarak nesne Gezgini de çalıştırabilirsiniz.
