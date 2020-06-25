---
title: Web performans testine veri kaynağı ekleme
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94ad53e4ac3d65bfe6cf08bf03f1f79c2075e03d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289072"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Web performans testine veri kaynağı ekleme

Aynı teste farklı değerler sağlamak için veri bağlama (örneğin, form gönderi parametreleriniz için farklı değerler sağlamak için).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Web performans testine veri bağlama](../test/media/web_test_databinding_conceptual.png)

Örnek bir ASP.NET uygulaması kullanacağız. Üç *. aspx* sayfası vardır: varsayılan sayfa, kırmızı sayfa ve mavi sayfa. Varsayılan sayfada kırmızı veya mavi ve bir Gönder düğmesi seçmek için bir radyo denetimi vardır. Diğer iki *. aspx* sayfası çok basittir. Birinin kırmızı adlı bir etiketi vardır ve diğeri mavi adlı bir etikete sahiptir. Varsayılan sayfada Gönder ' i seçtiğinizde, diğer sayfalardan birini görüntüyoruz. [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) örneğini indirebilir veya yalnızca kendi web uygulamanızla birlikte takip edebilirsiniz.

![Sınanacak Web uygulamasını çalıştırma](../test/media/web_test_databinding_runwebapp.png)

Çözümünüz, Web uygulamasının sayfalarına gözatan bir Web performans testi de içermelidir.

![Web performans testine sahip çözüm](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>SQL veritabanı oluşturma

::: moniker range="vs-2017"

1. Visual Studio Enterprise yoksa, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasından indirebilirsiniz.

2. Bir SQL veritabanı oluşturun.

     ![Yeni bir SQL veritabanı Ekle](../test/media/web_test_databinding_sql_addnewdb.png)

3. Veritabanı projesi oluşturun.

     ![Veritabanından yeni proje oluştur](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Veritabanı projesine tablo ekleyin.

     ![Veritabanı projesine yeni bir tablo ekleyin](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Tabloya alanlar ekleyin.

     ![Tabloya alanlar ekleyin](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Veritabanı projesini yayımlayın.

     ![Çözüm Gezgini veritabanı projesini yayımlama](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Alanlara veri ekleyin.

     ![Alanlara veri ekleme](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio Enterprise yoksa, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasından indirebilirsiniz.

2. Bir SQL veritabanı oluşturun.

     ![Yeni bir SQL veritabanı Ekle](../test/media/web_test_databinding_sql_addnewdb.png)

3. Veritabanı projesi oluşturun.

     ![Veritabanından yeni proje oluştur](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Veritabanı projesine tablo ekleyin.

     ![Veritabanı projesine yeni bir tablo ekleyin](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Tabloya alanlar ekleyin.

     ![Tabloya alanlar ekleyin](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Veritabanı projesini yayımlayın.

     ![Çözüm Gezgini veritabanı projesini yayımlama](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Alanlara veri ekleyin.

     ![Alanlara veri ekleme](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Veri kaynağını ekleyin

1. Bir veri kaynağı ekleyin.

     ![Web performans testine veri kaynağı ekleme](../test/media/web_test_databinding_sql_adddatasource.png)

2. Veri kaynağı türünü seçin ve adlandırın.

     ![Veritabanı kaynağını Adlandır](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Bir bağlantı oluşturun.

     ![Yeni bağlantı seçin](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Bağlantı ayrıntılarını girin.

     ![SQL veritabanı bağlantı özelliklerini girin](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Testiniz için kullanmak istediğiniz tabloyu seçin.

     ![Veri kaynağı olarak renk tablosu ekleme](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tablo teste bağlanır.

     ![Web performans testine veri kaynakları düğümü ekleme](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Testi kaydedin.

## <a name="bind-the-data"></a>Verileri bağlama

1. **ColorName** alanını bağlayın.

     ![ColorName alanını RadioButtonList1 değerine bağlayın](../test/media/web_test_databinding_sql_binddatasource.png)

2. **Çözüm Gezgini** *yerel. testsettings* dosyasını açın ve **veri kaynağı başına bir çalıştırma satırı** seçeneğini belirleyin.

     ![Test ayarları dosyasını düzenleme](../test/media/web_test_databinding_sql_testsettings.png)

3. Web performans testini kaydedin.

## <a name="run-the-test-with-the-data"></a>Testi verilerle çalıştırın

1. Testi çalıştırın.

     ![Bağlamayı doğrulamak için Web performans testini çalıştırın](../test/media/web_test_databinding_sql_runtest.png)

     Her veri satırı için iki çalışma görüntülenir. Run 1, *Red. aspx*sayfası için bir istek gönderir ve 2. çalıştırma, *Blue. aspx*sayfasına bir istek gönderir.

     ![Test çalıştırması sonuçları](../test/media/web_test_databinding_sql_runresults.png)

     Bir veri kaynağına bağladığınızda, varsayılan yanıt URL kuralını ihlal edebilirsiniz. Bu durumda, çalışma 2 ' deki hata, özgün test kaydından *Red. aspx* sayfasını bekleyen kural nedeniyle oluşur, ancak veri bağlama şimdi onu *Blue. aspx* sayfasına yönlendirir.

2. **Yanıt URL** doğrulama kuralını silip testi yeniden çalıştırarak doğrulama hatasını düzeltin.

     ![Yanıt URL 'SI doğrulama kuralını Sil](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Web performans testi artık veri bağlamayı kullanarak geçirilir.

     ![Veri bağlamayı kullanarak test geçişleri](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Soru-Cevap

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>S: veri kaynağı olarak hangi veritabanlarını kullanabilirim?

Y **:** Aşağıdakileri kullanabilirsiniz:

- Microsoft SQL Azure.

- Microsoft SQL Server 2005 veya sonraki bir sürümü.

- Microsoft SQL Server veritabanı dosyası (SQL Express dahil).

- Microsoft ODBC.

- OLE DB için .NET Framework sağlayıcıyı kullanan Microsoft Access dosyası.

- Oracle 7,3, 8i, 9i veya 10G.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>S: Nasıl yaparım? bir virgülle ayrılmış değer (CSV) metin dosyasını veri kaynağı olarak kullanmak mı istiyorsunuz?

Y **:** Şöyle:

1. Proje veritabanı yapıtlarınızı düzenlemek ve bir öğe eklemek için bir klasör oluşturun.

     ![Veri klasörüne yeni öğe Ekle](../test/media/web_test_databinding_foldernewitem.png)

2. Bir metin dosyası oluşturun.

     ![Yeni metin dosyasını adlandırın ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Metin dosyasını düzenleyin ve aşağıdakileri ekleyin:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. [Veri kaynağı ekleme](#add-the-data-source)bölümündeki adımları kullanın, ancak veri KAYNAĞıNıZ olarak CSV dosyası ' nı seçin.

     ![Bir ad girin ve CSV dosyası seçin](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>S: var olan CSV dosyamın sütun başlıkları yoksa ne olacak?

Y **:** Sütun üst bilgileri ekleyemez, CSV dosyasını veritabanı olarak değerlendirmek için bir şema açıklaması dosyası kullanabilirsiniz.

1. *schema.ini*adlı yeni bir metin dosyası ekleyin.

     ![schema.ini dosyası Ekle](../test/media/web_test_databinding_schemafile.png)

2. Verilerinizin yapısını açıklayan bilgileri eklemek için *schema.ini* dosyasını düzenleyin. Örneğin, CSV dosyasını tanımlayan bir şema dosyası şöyle görünebilir:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Teste bir veri kaynağı ekleyin.

     ![Web performans testine veri kaynağı ekleme](../test/media/web_test_databinding_sql_adddatasource.png)

4. Bir *schema.ini* dosyası kullanıyorsanız, veri kaynağı olarak **veritabanı** (CSV dosyası değil) öğesini seçin ve adlandırın.

     ![Veritabanı veri kaynağı Ekle](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Yeni bağlantı oluşturun.

     ![Yeni bağlantı seçin](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. OLE DB için .NET Framework Veri Sağlayıcısı seçin.

     ![.NET Framework OLE DB veri sağlayıcısını seçin](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. **Gelişmiş**' i seçin.

     ![Gelişmiş seçin](../test/media/web_test_databinding_advanced.png)

8. Sağlayıcı özelliği için, Microsoft. Jet. OLEDB. 4.0 ' ı seçin ve **genişletilmiş özellikleri** metin olarak ayarlayın; HDR = NO.

     ![Gelişmiş özellikleri Uygula](../test/media/web_test_databinding_advancedproperties.png)

9. Şema dosyasını içeren klasörün adını yazın ve bağlantınızı test edin.

     ![Veri klasörünün yolunu girin](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Kullanmak istediğiniz CSV dosyasını seçin.

     ![Metin dosyasını seçin](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Bitirdikten sonra CSV dosyası bir tablo olarak görünür.

     ![Test 'e eklenen veri kaynağı](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>S: bir XML dosyasını veri kaynağı olarak kullanmak Nasıl yaparım? mı?

**Y:** Evet.

1. Proje veritabanı yapıtlarınızı düzenlemek ve bir öğe eklemek için bir klasör oluşturun.

     ![Veri klasörüne yeni öğe Ekle](../test/media/web_test_databinding_foldernewitem.png)

2. Bir XML dosyası oluşturun.

     ![ColorData.xml dosyası Ekle](../test/media/web_test_databinding_additemxmlfile.png)

3. XML dosyasını düzenleyin ve verilerinizi ekleyin:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. [Veri kaynağı ekleme](#add-the-data-source)bölümündeki adımları kullanın, ancak veri KAYNAĞıNıZ olarak XML dosyası ' nı seçin.

     ![Bir ad girin ve XML dosyası seçin](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>S: SOAP kullanan bir Web hizmeti isteğine veri bağlama ekleyebilir miyim?

Y **:** Evet, SOAP XML 'i el ile değiştirmeniz gerekir.

1. İstek ağacındaki Web hizmeti isteğini seçin ve Özellikler penceresi dize gövdesi özelliğindeki üç nokta (...) simgesini seçin.

     ![Web hizmeti dize gövdesini düzenleme](../test/media/web_test_databinding_webservicerequest.png)

2. SOAP gövdesindeki değerleri, aşağıdaki sözdizimini kullanarak veriye dayalı değerlerle değiştirin:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Örneğin, aşağıdaki koda sahipseniz:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    Bunu şu şekilde değiştirebilirsiniz:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. Testi kaydedin.
