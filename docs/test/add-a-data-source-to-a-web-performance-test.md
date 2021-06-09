---
title: Web performans testine veri kaynağı ekleme
description: Form gönderi parametrelerinize farklı değerler sağlamak gibi, aynı teste farklı değerler sağlamak için verileri bağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 71aa3dbf4657896093dae59451140f48f83f1622
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761010"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Web performans testine veri kaynağı ekleme

Form gönderi parametrelerinize farklı değerler sağlamak gibi, aynı teste farklı değerler sağlamak için verileri bağlayın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Verileri web performans testlerine bağlama](../test/media/web_test_databinding_conceptual.png)

Örnek bir uygulama ASP.NET. Üç *.aspx sayfası* vardır: varsayılan sayfa, Kırmızı sayfa ve Mavi sayfa. Varsayılan sayfada kırmızı veya maviyi ve gönder düğmesini seçen bir radyo denetimi vardır. Diğer iki *.aspx* sayfası çok basittir. Biri Red, diğeri de Blue adlı bir etikete sahip. Varsayılan sayfada gönder'i seçerseniz diğer sayfalardan birini görüntüleriz. [ColorWebApp örneğini indirebilir](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) veya kendi web uygulamanıza kadar takip edin.

![Test edilecek web uygulamasını çalıştırma](../test/media/web_test_databinding_runwebapp.png)

Çözümünüz, web uygulamasının sayfalarına göz atan bir web performans testi de içermesi gerekir.

![Web performans testi ile çözüm](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>SQL veritabanı oluşturma

::: moniker range="vs-2017"

1. Başka bir dosyanız Visual Studio Enterprise İndirmeler sayfasından Visual Studio [indirebilirsiniz.](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

2. SQL veritabanı oluşturun.

     ![Yeni bir SQL veritabanı ekleme](../test/media/web_test_databinding_sql_addnewdb.png)

3. Veritabanı projesi oluşturun.

     ![Veritabanından yeni proje oluşturma](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Veritabanı projesine bir tablo ekleyin.

     ![Veritabanı projesine yeni bir tablo ekleme](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Tabloya alanlar ekleyin.

     ![Tabloya alan ekleme](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Veritabanı projesini yayımlama.

     ![Veritabanı projesini Çözüm Gezgini](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Alanlara veri ekleyin.

     ![Alanlara veri ekleme](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Başka bir dosyanız Visual Studio Enterprise İndirmeler sayfasından Visual Studio [indirebilirsiniz.](https://visualstudio.microsoft.com/downloads)

2. SQL veritabanı oluşturun.

     ![Yeni bir SQL veritabanı ekleme](../test/media/web_test_databinding_sql_addnewdb.png)

3. Veritabanı projesi oluşturun.

     ![Veritabanından yeni proje oluşturma](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Veritabanı projesine bir tablo ekleyin.

     ![Veritabanı projesine yeni bir tablo ekleme](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Tabloya alanlar ekleyin.

     ![Tabloya alan ekleme](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Veritabanı projesini yayımlama.

     ![Veritabanı projesini Çözüm Gezgini](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Alanlara veri ekleyin.

     ![Alanlara veri ekleme](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Veri kaynağını ekleme

1. Bir veri kaynağı ekleyin.

     ![Web performans testinde veri kaynağı ekleme](../test/media/web_test_databinding_sql_adddatasource.png)

2. Veri kaynağı türünü seçin ve bu türe bir ad girin.

     ![Veritabanı kaynağını adla](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Bağlantı oluşturun.

     ![Yeni bağlantı seçme](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Bağlantı ayrıntılarını girin.

     ![SQL veritabanı bağlantı özelliklerini girin](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Test için kullanmak istediğiniz tabloyu seçin.

     ![Veri kaynağı olarak Color tablosu ekleme](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tablo teste bağlı.

     ![Veri Kaynakları düğümü web performans testini ekler](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Testi kaydedin.

## <a name="bind-the-data"></a>Verileri bağlama

1. **ColorName alanını** bağlayın.

     ![ColorName alanını RadioButtonList1 değerine bağlama](../test/media/web_test_databinding_sql_binddatasource.png)

2. Yerel *ayarda Local.testsettings* **dosyasını Çözüm Gezgini** veri kaynağı satırı başına **bir çalıştırma seçeneğini** belirleyin.

     ![Test ayarları dosyasını düzenleme](../test/media/web_test_databinding_sql_testsettings.png)

3. Web performans testini kaydedin.

## <a name="run-the-test-with-the-data"></a>Testi verilerle çalıştırma

1. Testi çalıştırın.

     ![Bağlamayı doğrulamak için web performans testini çalıştırma](../test/media/web_test_databinding_sql_runtest.png)

     Her veri satırı için iki çalıştırma görüntülenir. Çalıştırma 1, *Red.aspx* sayfası için bir istek gönderir ve Çalıştırma 2, *Blue.aspx* sayfası için bir istek gönderir.

     ![Test çalıştırması sonuçları](../test/media/web_test_databinding_sql_runresults.png)

     Bir veri kaynağına bağlanarak varsayılan yanıt URL'si kuralını ihlal etmiş oluruz. Bu durumda, Çalıştırma 2'de hata, özgün test kaydından *Red.aspx* sayfasını bekler ancak veri bağlama artık bunu *Blue.aspx* sayfasına yönlendiriyor.

2. Yanıt URL'si doğrulama kuralını **silerek ve** testi yeniden çalıştırarak doğrulama hatasını düzeltin.

     ![Yanıt URL'si doğrulama kuralını silme](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Web performans testi artık veri bağlama kullanılarak başarılı olur.

     ![Veri bağlama kullanarak test geçişleri](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Soru-Cevap

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>S: Veri kaynağı olarak hangi veritabanlarını kullanabilirim?

**A:** Şunları kullanabilirsiniz:

- Microsoft SQL Azure.

- Microsoft SQL Server 2005 veya sonraki bir sürümü.

- Microsoft SQL Server veritabanı dosyası (SQL Express dahil).

- Microsoft ODBC.

- OLE DB için .NET Framework sağlayıcısını kullanan Microsoft Access OLE DB.

- Oracle 7.3, 8i, 9i veya 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>S: Nasıl yaparım? veri kaynağı olarak virgülle ayrılmış değer (CSV) metin dosyası mı kullanabilirsiniz?

**A:** Şöyle bir şey:

1. Proje veritabanı yapıtlarınızı düzenlemek ve bir öğe eklemek için bir klasör oluşturun.

     ![Veri klasörüne yeni öğe ekleme](../test/media/web_test_databinding_foldernewitem.png)

2. Bir metin dosyası oluşturun.

     ![Yeni metin dosyasını dosya adı ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Metin dosyasını düzenleyin ve şunları ekleyin:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Veri kaynağını [ekleme'de yer alan adımları kullanın,](#add-the-data-source)ancak veri kaynağınız olarak CSV dosyası'ı seçin.

     ![Bir ad girin ve CSV dosyası'ı seçin](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>S: Mevcut CSV dosyam sütun üst bilgileri içeriyorsa ne olur?

**A:** Sütun üst bilgileri ekleyamıyorsanız, CSV dosyasını veritabanı olarak kullanmak için şema açıklaması dosyası kullanabilirsiniz.

1. schema.iniadlı yeni *bir metin dosyası ekleyin.*

     ![Bir schema.ini ekleme](../test/media/web_test_databinding_schemafile.png)

2. Verilerinizin *schema.ini* bilgilerini eklemek içinschema.inidosyasını düzenleyin. Örneğin, CSV dosyasını açıklayan bir şema dosyası şöyle olabilir:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Teste bir veri kaynağı ekleyin.

     ![Web performans testinde veri kaynağı ekleme](../test/media/web_test_databinding_sql_adddatasource.png)

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
