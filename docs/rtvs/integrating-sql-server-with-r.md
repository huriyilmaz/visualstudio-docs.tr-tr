---
title: SQL Server'ı R ile tümleştirme
description: Visual Studio, R'den SQL sorguları oluşturmayı ve çalıştırmayı ve R'nin depolanan yordamlarla çalışabilmesiiçin çalışmayı destekler.
ms.date: 06/25/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 10b5dfee629b5b6e67ab544ca0bdd905ed2a120a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72888452"
---
# <a name="work-with-sql-server-and-r"></a>SQL Server ve R ile çalışma

Visual Studio'nun SQL Server için mükemmel desteği, veri bilimcilerin SQL sorguları oluşturma ve çalıştırma ve depolanan yordamlarla çalışma becerisi sayesinde R ve SQL veritabanları yla çalışmasına yardımcı olur.

> [!Note]
> SQL ve R ile birlikte çalışmak için SQL Server Veri Araçları'nın yüklü olması gerekir:
> - Visual Studio 2017: Visual Studio yükleyicisini çalıştırın ve SQL Server Data araçlarını içeren Veri depolama ve işleme iş yükünü seçin.
> - Visual Studio 2015: [SQL Server Veri Araçlarını İndir](/sql/ssdt/download-sql-server-data-tools-ssdt)meyyatını takip edin.

|   |   |
|---|---|
| ![video için film kamera simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") | SQL Server ve R'ye (3m 03s) genel bakış için [bir video (youtube.com) izleyin.](https://www.youtube.com/watch?v=n4AYr0QIwdQ) |

## <a name="create-and-run-sql-queries"></a>SQL sorguları oluşturma ve çalıştırma

RTVS, R projelerine SQL sorguları eklemeyi destekler ve aradığınız sonuçları alana kadar SQL sorgularını ayrı bir bağlamda yinelemeli olarak geliştirmenize olanak sağlar.

SQL sorgu dosyası eklemek için Solution Explorer'da projeyi sağ tıklatın,**Yeni Öğe** **Ekle'yi** > seçin ve **SQL Sorgu** dosya türünü seçin:

![Projeye SQL Sorgu öğesi ekleme](media/sql-add-item.png)

Bu komut, Visual Studio'nun SQL için tam IntelliSense ve sorgu çalıştırma olanağı sağlayan Transact-SQL düzenleyicisinde dosyayı açar. Bu özelliklerin çalışması için, düzenleyicinin araç çubuğundaki bağlantı düğmesini kullanarak bir veritabanına bağlanmanız veya bir sorgu çalıştırmayı denemeniz gerekir **(Ctrl**+**Shift**+**E**, seçimde de çalışır). Her iki şekilde de bağlantı iletişim kutusunu getirir:

![SQL bağlantı iletişim kutusu](media/sql-connection-dialog.png)

Bir bağlantı kurulduktan sonra sorguları çalıştırabilir ve sonuçları görebilirsiniz:

![SQL pencere sorgu sonuçları](media/sql-query-results.png)

Transact-SQL düzenleyicisi, sorgunun yürütme planını görüntüleme ve sorgu hata ayıklama gibi çeşitli özellikleri destekler.
Daha fazla bilgi için, [Komut Dosyalarını Yeniden Etkinleştirmek ve Yürütmek için Transact-SQL Düzenleyicisini Kullan'a](https://msdn.microsoft.com/library/hh272706.aspx)bakın.

## <a name="work-with-sql-server-stored-procedures"></a>SQL Server depolanan yordamlarla çalışma

[SQL Server R Services](/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 ve sonrası) T-SQL depolanan yordamından R kodunu gömmenize ve çalıştırmanıza olanak tanır. Bir SQL Server bilgisayarında R kodunu çalıştırabilir, SQL sorgusundan döndürülen veriler üzerinde çalışabilir ve daha fazla SQL tarafından işlenebilen veya istemciye döndürülebilen bir SQL sonuç kümesi oluşturabilirsiniz.

RTVS, aşağıdaki bölümlerde açıklandığı gibi, SQL ve R kodunu tek bir SQL deyimi içinde birleştirme işlemini basitleştirir:

- [Veritabanı bağlantısı ekleme](#add-a-database-connection)
- [SQL depolanmış yordamı yazma ve test edin](#write-and-test-a-sql-stored-procedure)
- [SQL depolanan yordamı yayımlama](#publish-a-sql-stored-procedure)

|   |   |
|---|---|
| ![video için film kamera simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") | R ve SQL depolanan yordamlara (6m 09s) genel bakış için [bir video (youtube.com) izleyin.](https://www.youtube.com/watch?v=dFKIT2OitWQ) |

### <a name="add-a-database-connection"></a>Veritabanı bağlantısı ekleme

1. **Bağlantı Özellikleri** iletişim kutusunu açmak için **R Tools** > **Data** > **Add Database Connection'ı** seçin. Burada veri kaynağının adını (bu durumda SQL Server), sunucunun adını, kimlik doğrulama modunu ve veritabanının adını belirtirsiniz. İletişim kutusunu kapatmadan önce girişinizi doğrulamak için **Test Bağlantısı'nı** seçin.

    ![SQL Bağlantı İletişim Kutusu](media/sql-connection-string-dialog.png)

1. Geçerli bir bağlantıyla **Tamam'ı** seçtikten sonra Visual `dbConnection` Studio, yeni ayarlarda adı verilen bir bağlantı dizesi *oluşturur. R* dosyası. RTVS bu dosyayı otomatik olarak kaynaklara (çalıştırAna) göre, r komut dosyasından gelen bağlantıyı hemen kullanabilirsiniz:

![SQL Settings.R dosyası](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>SQL depolanmış yordamı yazma ve test edin

Yeni bir SQL Saklı Yordam eklemek için, projenize sağ tıklayın,**Yeni Öğe** **Ekle'yi** > seçin, şablonlar listesinden R ile **SQL Stored** Yordamı'nı seçin, dosyaya bir ad verin ve **Tamam'ı**seçin. Varsayılan dosya adı *SqlSProc.R;* okuma kolaylığı için bu bölümün geri kalanında *StoredProcedure.R* dosya adı kullanılır. Birden çok depolanmış yordamınvarsa, her dosyanın benzersiz bir dosya adı olmalıdır.

RTVS depolanan yordam için üç dosya oluşturur: bir *. *R kodunuz için R dosyası, bir *. *SQL kodu için Query.sql dosyası ve bir *. İkisini birleştiren Template.sql* dosyası. Onlar son iki Çözüm Explorer'da çocuklar olarak *görünür. R* dosyası:

![Çözüm Gezgini, SQL Stored Procedure'ın R ile genişletilmiş görünümünü genişletti](media/sql-solution-explorer-expanded.png)

*Şey. R* dosyası (*StoredProcedure.R* bu örnek) R kodu yazdığınız yerdir. Varsayılan içerikler şunlardır:

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

Basitçe söylemek gerekirse, kod denilen `InputDataSet` bir R veri `OutputDataSet`çerçevesi alır ve şablon kodu sadece çıktı giriş kopyalama ile, sonuçlarını döndürür.

> [!Note]
> Bu veri çerçevelerinin `@input_data_1_name` `@output_data_1_name` `sp_execute_external_script` adları, sistem depolanan yordama yapılan çağrıdaki parametreler tarafından denetlenir. Bu çağrı kuralının tasarımı ve bazı kullanım örnekleri hakkında daha fazla bilgi için [sp_execute_external_script (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)bölümüne bakın.

Oluşturulan diğer kod (yorumlarda), BIR SQL deyimini SQL Server'a iletmek, çalıştırmak ve sonuç kümesini R veri çerçevesi olarak almak için [RODBC paketini](https://cran.r-project.org/web/packages/RODBC/index.html) kullanan küçük bir test komut dosyası sağlar. SQL Server'dan aldığınız sonuç kümesine karşı R kodunuzu etkileşimli olarak yazmak için bu test kodunun yorumunu geri leyebilirsiniz.

*Şey. Query.sql* dosyası ( Bu örnekte*StoredProcedure.Query.sql)* için veri üreten SQL sorgusunu yazıp test ettiğiniz `InputDataSet`yerdir. Bu *.sql* dosyası ile editör size tüm olağan Transact-SQL özelliklerini sağlar.

SQL kodunuzdan memnun olduğunuzda *,.sql* dosyasını açık düzenleyiciye sürükleyerek R kodunuzla *tümleştirin. R* dosyası. Aşağıdaki resimde, *StoredProcedure.Query.sql* virgülden sonra *StoredProcedure.R* noktasına `sqlQuery(channel, )`sürüklendi:

![SQL Dosyayı R String Değişkenine Okuma](media/sql-reference-sql-file-from-r.png)

Gördüğünüz gibi, bu basit adım otomatik olarak *.sql* dosyasını açmak, içeriğini bir dize halinde okumak ve SQL Server'a göndermek için RODBC paketine geçirmek için R kodu oluşturur.

Artık veri çerçevesini `InputDataSet` istediğiniz gibi işleyen Etkileşimli R kodu yazabilirsiniz. Editörde R kodunu seçip **Ctrl**+**Enter**tuşuna basarak [etkileşimli pencereye](interactive-repl-for-r-in-visual-studio.md) gönderebileceğinizi unutmayın.

*Şey. Template.sql* dosyası ( Bu örnekte*StoredProcedure.Template.sql),* son olarak, SQL Stored Yordamoluşturmak için şablon içerir:

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

- Yer `_RCODE_` tutucu, yer tutucunun içeriği ile *değiştirilir. R* dosyası (örneğin, *StoredProcedure.R*).
- Yer `_INPUT_QUERY_` tutucu, yer tutucunun içeriği ile *değiştirilir. Query.sql* dosyası (örneğin, *StoredProcedure.Query.sql*).
- Depolanan `WITH RESULT SETS` yordamdan döndürülen sonuç kümesinin şemasını açıklamak için yan tümceyi edin. Depolanan yordamı `OutputDataSet` arayana dönmek istediğiniz veri çerçevesindeki sütunları özellikle tanımlayın.

Örneğin, aşağıdaki sorgu için:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

İade değerlerinin veri `WITH RESULT SETS` türlerini belirtmek için aşağıdaki yan tümceyi kullanırsınız:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>SQL depolanan yordamı yayımlama

1. Seçeneklerle **R Araçları** > **Veri** > **Yayımla** menüsü komutunu seçin.
1. Görünen iletişim kutusunda **Yayımla'yı** şu şekilde değiştirin: **Veritabanına,** hedefi belirtin, **Yayımla'yı**seçin ve RTVS depolanan yordamı oluşturur ve yayımlar:

    ![Depolanan yordam iletişim kutusunu yayımlama](media/sql-publish-with-options.png)

1. Bir projede depolanan tüm yordamları yayımlamak için, Çözüm Gezgini'nde projeyi sağ tıklattığınızda da kullanılabilen **R Tools** > **Data** > **Publish Stored Yordamları** komutunu kullanabilirsiniz.

> [!Tip]
> Visual Studio'da SQL Server Object Explorer açıksa, yayınlanan saklı yordamınız veritabanınızın **Programlanabilirlik** > **Saklı Yordamlar** klasöründe görünür. Ayrıca, Object Explorer'dan **Yürüt Yordamı'nı**sağ tıklayıp seçerek veya *.sql* sorgu penceresinden etkileşimli olarak çağırarak da çalıştırabilirsiniz.
