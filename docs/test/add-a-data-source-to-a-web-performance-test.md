---
title: Web performans testine veri kaynağı ekleme
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c7f947be01500b0d45b81d404206722ac71084a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565415"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Web performans testine veri kaynağı ekleme

Form sonrası parametrelerinize farklı değerler sağlamak için verileri aynı teste (örneğin) bağlamak için veri bağlama.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Verileri web performans testine bağlama](../test/media/web_test_databinding_conceptual.png)

Örnek bir ASP.NET uygulaması kullanacağız. Üç *.aspx* sayfası vardır – varsayılan sayfa, bir Kırmızı sayfa ve mavi sayfa. Varsayılan sayfada kırmızı veya mavi ve gönder düğmesini seçmek için bir radyo denetimi vardır. Diğer iki *.aspx* sayfaları çok basittir. Birinde Kırmızı adında bir etiket, diğerinde mavi adında bir etiket var. Varsayılan sayfada gönder'i seçtiğinizde, diğer sayfalardan birini görüntüleriz. [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) örneğini indirebilir veya kendi web uygulamanızla birlikte takip edebilirsiniz.

![Test edilecek web uygulamasını çalıştırma](../test/media/web_test_databinding_runwebapp.png)

Çözümünüz, web uygulamasının sayfalarında gezinen bir web performans testi de içermelidir.

![Web performans testi ile çözüm](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>SQL veritabanı oluşturma

::: moniker range="vs-2017"

1. Visual Studio Enterprise'ınyoksa, [Visual Studio İndirmeler](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasından indirebilirsiniz.

2. Bir SQL veritabanı oluşturun.

     ![Yeni bir SQL veritabanı ekleme](../test/media/web_test_databinding_sql_addnewdb.png)

3. Bir veritabanı projesi oluşturun.

     ![Veritabanından yeni proje oluşturma](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Veritabanı projesine bir tablo ekleyin.

     ![Veritabanı projesine yeni bir tablo ekleme](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Tabloya alanlar ekleyin.

     ![Tabloya alan ekleme](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Veritabanı projesini yayımlayın.

     ![Solution Explorer'dan veritabanı projesini yayımlama](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Alanlara veri ekleyin.

     ![Alanlara veri ekleme](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio Enterprise'ınyoksa, [Visual Studio İndirmeler](https://visualstudio.microsoft.com/downloads) sayfasından indirebilirsiniz.

2. Bir SQL veritabanı oluşturun.

     ![Yeni bir SQL veritabanı ekleme](../test/media/web_test_databinding_sql_addnewdb.png)

3. Bir veritabanı projesi oluşturun.

     ![Veritabanından yeni proje oluşturma](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Veritabanı projesine bir tablo ekleyin.

     ![Veritabanı projesine yeni bir tablo ekleme](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Tabloya alanlar ekleyin.

     ![Tabloya alan ekleme](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Veritabanı projesini yayımlayın.

     ![Solution Explorer'dan veritabanı projesini yayımlama](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Alanlara veri ekleyin.

     ![Alanlara veri ekleme](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Veri kaynağını ekleme

1. Bir veri kaynağı ekleyin.

     ![Web performans testine veri kaynağı ekleme](../test/media/web_test_databinding_sql_adddatasource.png)

2. Veri kaynağının türünü seçin ve adlandırın.

     ![Veritabanı kaynağını adlandırın](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Bir bağlantı oluşturun.

     ![Yeni bağlantı seçin](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Bağlantı ayrıntılarını girin.

     ![SQL veritabanı bağlantı özelliklerini girin](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Testiniz için kullanmak istediğiniz tabloyu seçin.

     ![Veri kaynağı olarak Renk tablosunu ekleme](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tablo teste bağlıdır.

     ![Veri Kaynakları düğümü web performans testine ekle](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Testi kaydet.

## <a name="bind-the-data"></a>Verileri bağlama

1. **ColorName** alanını bağla.

     ![ColorName alanını RadioButtonList1 değerine bağlama](../test/media/web_test_databinding_sql_binddatasource.png)

2. **Solution Explorer'da** *Local.testsettings* dosyasını açın ve **veri kaynağı satırı başına Bir çalıştır** seçeneğini belirleyin.

     ![Test ayarları dosyasını değiştirme](../test/media/web_test_databinding_sql_testsettings.png)

3. Web performans testini kaydedin.

## <a name="run-the-test-with-the-data"></a>Testi verilerle çalıştırma

1. Testi çalıştırın.

     ![Bağlamayı doğrulamak için web performans testini çalıştırın](../test/media/web_test_databinding_sql_runtest.png)

     İki çalıştırma her veri satırı için görüntülenir. Run 1, *Red.aspx*sayfası için bir istek gönderir ve Run 2 *blue.aspx*sayfası için bir istek gönderir.

     ![Test çalıştırma sonuçları](../test/media/web_test_databinding_sql_runresults.png)

     Bir veri kaynağına bağlandığınızda, varsayılan yanıt URL kuralını ihlal edebilirsiniz. Bu durumda, Run 2'deki hata, *red.aspx* sayfasını özgün test kaydından bekleyen kuraldan kaynaklanır, ancak veri bağlama şimdi onu *Blue.aspx* sayfasına yönlendirir.

2. **Yanıt URL** doğrulama kuralını silerek ve testi yeniden çalıştırarak doğrulama hatasını düzeltin.

     ![Yanıt URL doğrulama kuralını silme](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Web performans testi artık veri bağlama kullanarak geçer.

     ![Veri bağlama yı kullanarak test geçişleri](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Soru-Cevap

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>S: Veri kaynağı olarak hangi veritabanlarını kullanabilirim?

**A:** Aşağıdakileri kullanabilirsiniz:

- Microsoft SQL Azure.

- Microsoft SQL Server 2005 veya sonraki sürümlerden herhangi biri.

- Microsoft SQL Server veritabanı dosyası (SQL Express dahil).

- Microsoft ODBC.

- Microsoft Access dosyası, OLE DB için .NET Framework sağlayıcısını kullanarak dosyayı kullanır.

- Oracle 7.3, 8i, 9i veya 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>S: Virgülle ayrılmış değer (CSV) metin dosyalarını veri kaynağı olarak nasıl kullanırım?

**A:** Bunun nasıl bir şekilde açıklanmıştır:

1. Proje veritabanı yapılarınızı düzenlemek ve bir öğe eklemek için bir klasör oluşturun.

     ![Veri klasörüne yeni öğe ekleme](../test/media/web_test_databinding_foldernewitem.png)

2. Bir metin dosyası oluşturun.

     ![Yeni metin dosyası ColorData.csv adı](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Metin dosyasını edin ve aşağıdakileri ekleyin:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Veri kaynağını [ekle](#add-the-data-source)adımlarını kullanın, ancak veri kaynağınız olarak CSV dosyasını seçin.

     ![Bir ad girin ve CSV dosyanızı seçin](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>S: Varolan CSV dosyam sütun başlıkları içermiyorsa ne olur?

**A:** Sütun üstbilgileri ekleyemiyorumsa, CSV dosyasını veritabanı olarak ele almak için şema açıklama dosyasını kullanabilirsiniz.

1. *schema.ini*adlı yeni bir metin dosyası ekleyin.

     ![Şema.ini dosyası ekle](../test/media/web_test_databinding_schemafile.png)

2. Verilerinizin yapısını açıklayan bilgileri eklemek için *şema.ini* dosyasını edin. Örneğin, CSV dosyasını açıklayan bir şema dosyası aşağıdaki gibi görünebilir:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Teste bir veri kaynağı ekleyin.

     ![Web performans testine veri kaynağı ekleme](../test/media/web_test_databinding_sql_adddatasource.png)

4. *Şema.ini* dosyası kullanıyorsanız, veri kaynağı olarak **Veritabanı'nı** (CSV dosyası değil) seçin ve adını verin.

     ![Veritabanı veri kaynağı ekleme](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Yeni bağlantı oluşturun.

     ![Yeni bağlantı seçin](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. OLE DB için .NET Framework Data Provider'ı seçin.

     ![.NET framework OLE DB veri sağlayıcısını seçin](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. **Gelişmiş'i**seçin.

     ![Gelişmiş'i Seçin](../test/media/web_test_databinding_advanced.png)

8. Sağlayıcı özelliği için Microsoft.Jet.OLEDB.4.0'ı seçin ve **ardından Genişletilmiş Özellikleri** Met'e ayarlayın; HDR=HAYR.

     ![Gelişmiş özellikleri uygulama](../test/media/web_test_databinding_advancedproperties.png)

9. Şema dosyasını içeren klasörün adını yazın ve bağlantınızı test edin.

     ![Veri klasörüne giden yolu girin](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Kullanmak istediğiniz CSV dosyasını seçin.

     ![Metin dosyasını seçin](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Bitirdikten sonra, CSV dosyası tablo olarak görünür.

     ![Teste eklenen veri kaynağı](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>S: Bir XML dosyayı veri kaynağı olarak nasıl kullanırım?

**Y:** Evet.

1. Proje veritabanı yapılarınızı düzenlemek ve bir öğe eklemek için bir klasör oluşturun.

     ![Veri klasörüne yeni öğe ekleme](../test/media/web_test_databinding_foldernewitem.png)

2. Bir XML dosyası oluşturun.

     ![ColorData.xml dosyası ekle](../test/media/web_test_databinding_additemxmlfile.png)

3. XML dosyasını edin ve verilerinizi ekleyin:

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

4. Veri kaynağını [ekle'deki](#add-the-data-source)adımları kullanın, ancak veri kaynağınız olarak XML dosyasını seçin.

     ![Bir ad girin ve XML dosyayı seçin](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>S: SOAP kullanan bir web hizmeti isteğine veri bağlama ekleyebilir miyim?

**A:** Evet, SOAP XML'i el ile değiştirmeniz gerekir.

1. İstek ağacındaki web hizmeti isteğini seçin ve Özellikler penceresinde String Body özelliğindeki elipsleri (...) seçin.

     ![Web hizmeti dize gövdesini edin](../test/media/web_test_databinding_webservicerequest.png)

2. SOAP gövdesindeki değerleri aşağıdaki sözdizimi kullanarak veriye bağlı değerlerle değiştirin:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Örneğin, aşağıdaki kod varsa:

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

    Şu na göre değiştirebilirsiniz:

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

3. Testi kaydet.
