---
title: Web hizmeti testi oluşturma
description: Web Hizmetleri için bir performans testi kullanmayı ve Web Performans Testi Düzenleyicisi Web hizmeti sayfalarını bulmak için istekleri özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/30/2020
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 2d368ca7cbe64f2c0e8c8dc5e18e5f3c7145274c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949850"
---
# <a name="how-to-create-a-web-service-test"></a>Nasıl yapılır: Web hizmeti testi oluşturma

Web hizmetlerini test etmek için bir Web performans testi kullanabilirsiniz. **Ekleme isteği** ve **Web hizmeti isteği ekleme** seçeneklerini kullanarak, Web hizmeti sayfalarını bulmak için **Web Performans Testi Düzenleyicisi** bireysel istekleri özelleştirebilirsiniz. Genellikle, bu sayfaları Web uygulamasında göstermeyin. Bu nedenle, bu sayfalara erişim kazanmak için isteği özelleştirmeniz gerekir.

>[!NOTE]
> Web performansı ve yük testi işlevselliği, Visual Studio 2019 ' de kullanım dışıdır. Application Insights için, çok adımlı Web testleri Visual Studio WebTest dosyalarına bağımlıdır. Visual Studio 2019 ' nin, WebTest işlevselliğiyle ilgili son sürüm olacağı [duyurulmuştur](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/) . Yeni özellik eklenmadığında, Visual Studio 2019 ' deki WebTest işlevinin hala desteklenmekte olduğunu ve ürünün destek yaşam döngüsü sırasında desteklenmeye devam edecek olduğunu anlamak önemlidir. Azure Izleyici ürün ekibi, [buradaki](https://github.com/MicrosoftDocs/azure-docs/issues/26050#issuecomment-468814101)çok adımlı kullanılabilirlik testlerinin geleceği hakkında sorular buldu.

**Gereksinimler**

Visual Studio Enterprise

## <a name="to-create-a-simple-web-service"></a>Basit bir Web hizmeti oluşturmak için

Test etmek için kendi Web hizmetinizi kullanabilir veya Visual Studio 'ya dahil olan temel Web hizmeti (ASMX) şablonunu kullanabilirsiniz. Bu şablonu kullanarak basit bir Web hizmeti oluşturmak için:

1. Visual Studio 'da, ASP.NET Web uygulaması (.NET Framework) şablonunu kullanarak yeni bir proje oluşturun ve istendiğinde **boş** şablonu seçin. Bir ad yazın ve projeyi oluşturun.

1. Çözüm Gezgini, proje düğümüne sağ tıklayın, yeni öğe **Ekle**' yi seçin  >  ve ardından **Web hizmeti (asmx)** öğesini seçin. Web hizmetini ekleyin.

1. *WebService1. asmx* ' i açın ve varsayılan `HelloWorld` Web yöntemini aşağıdaki kodla değiştirin.

   ```csharp
   public string HelloWorld(string str)
   {
      return "Hello, " + str;
   }
   ```

## <a name="install-the-load-testing-component"></a>Yük testi bileşenini yükleme

Web performans ve yük testi Araçları bileşeni yüklü değilse, Visual Studio Yükleyicisi aracılığıyla yüklemeniz gerekir.

1. Windows 'un **Başlat** menüsünden **Visual Studio yükleyicisi** açın. Ayrıca, Visual Studio 'da yeni proje iletişim kutusundan veya **Araçlar**  >  **' ın araç ve Özellikler Al ' i** seçerek menü çubuğundan erişebilirsiniz.

1. **Visual Studio yükleyicisi**, **tek tek bileşenler** sekmesini seçin ve aşağı kaydırarak **hata ayıklama ve test** bölümüne gidin. **Web performansı ve yük testi Araçları '** nı seçin.

   ![Web performansı ve yük testi Araçları bileşeni](media/web-perf-load-testing-tools-component.png)

1. **Değiştir** düğmesini seçin.

   Web performans ve yük testi Araçları bileşeni yüklendi.

## <a name="create-a-web-test-project"></a>Web testi projesi oluşturma

Web testi, Web performansı ve yük testi projesi şablonu gerektirir. Bu bölümde, bir C# yük testi projesi oluşturacağız. Dilerseniz, bir Visual Basic yük testi projesi de oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

   Örnek Web hizmeti (ASMX) şablonunu kullanıyorsanız, Web test projesini aynı çözüme ekleyebilirsiniz.

2. Menü çubuğundan **Dosya** > **Yeni** > **Proje** ' yi seçin.

   **Yeni proje** iletişim kutusu açılır.

3. **Yeni proje** iletişim kutusunda, **yüklü** ve **Visual C#**' yi genişletin ve ardından **Test** kategorisini seçin. **Web performansı ve yük testi proje** şablonunu seçin.

   ![Web performansı ve yük testi proje şablonu](media/web-perf-load-test-project-template.png)

4. Varsayılan adı kullanmak istemiyorsanız, proje için bir ad girin ve ardından **Tamam**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

   Örnek Web hizmeti (ASMX) şablonunu kullanıyorsanız, Web test projesini aynı çözüme ekleyebilirsiniz.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **Web testi** yazın ve ardından C# için **Web performansı ve yük testi projesi \[ kullanım dışı bırakıldı]** şablonunu seçin. **İleri**’yi seçin.

4. Varsayılan adı kullanmak istemiyorsanız proje için bir ad girin ve ardından **Oluştur**' u seçin.

::: moniker-end

   Visual Studio projeyi oluşturur ve **Çözüm Gezgini** dosyaları görüntüler. Proje başlangıçta *WebTest1. webtest* adlı bir Web testi dosyası içerir.

## <a name="to-test-a-web-service"></a>Bir Web hizmetini test etmek için

1. Web hizmetinizi başlatın ve gerekirse hizmeti duraklatmak için **Durdur** ' u seçin.

1. Web testi projesinde, Web Performans Testi Düzenleyicisi açan *WebTest1. webtest*' i açın. Test düzenleyicisinde, Web performans testini sağ tıklatın ve **Web hizmeti Isteği Ekle**' yi seçin.

1. Yeni isteğin **URL** özelliğinde, gibi Web hizmetinin adını yazın **https://localhost:44318/WebService1.asmx** .

1. Web hizmeti için, tarayıcının ayrı bir oturumunu açın ve **Adres** araç çubuğunda *. asmx* sayfasının URL 'sini yazın. Web sayfasının en üstünde, test etmek istediğiniz yöntemi seçin ve SOAP iletisini inceleyin. (Örnek Web hizmetinde, yöntemi HelloWorld ' dir.) Yöntemini açtığınızda, içerdiğini görürsünüz `SOAPAction` .

1. **Web Performans Testi Düzenleyicisi**, isteğe sağ tıklayın ve yeni bir üst bilgi eklemek Için **üst bilgi Ekle** ' yi seçin. **Ad** özelliğinde, yazın `SOAPAction` . **Değer** özelliğinde, içinde gördüğünüz değeri yazın ( `SOAPAction` Örneğin,) *http://tempuri.org/HelloWorld* .

1. Test düzenleyicisinde URL düğümünü genişletin, **dize gövdesi** düğümünü seçin ve **içerik türü** özelliği için bir değer girin `text/xml` .

1. 4. adımdaki tarayıcıya geri dönün, Web hizmeti Açıklama sayfasından SOAP isteğinin XML bölümünü seçin ve panoya kopyalayın.

   XML içeriği aşağıdaki örneğe benzer:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
       <soap:Body>
         <HelloWorld xmlns="http://tempuri.org/">
           <str>string</str>
         </HelloWorld>
       </soap:Body>
     </soap:Envelope>
     ```

1. Web Performans Testi Düzenleyicisi dönün ve sonra **dize gövdesi** özelliğindeki üç nokta **(...)** simgesini seçin. Panonun içeriğini özelliğine yapıştırın.

1. Testin geçebilmesi için XML 'teki tüm yer tutucu değerlerini geçerli değerlerle değiştirin. Önceki örnekte, öğesinin örneğini `string` bir adla değiştirirsiniz.

1. Web hizmeti isteğine sağ tıklayıp **URL QueryString parametresi Ekle**' yi seçin.

1. Sorgu dizesi parametresine bir ad ve değer atayın. Önceki örnekte, adı `op` ve değeridir `HelloWorld` . Bu, gerçekleştirilecek Web hizmeti işlemini belirler.

    > [!NOTE]
    > Sözdizimini kullanarak herhangi bir yer tutucu değerini veri bağlama değerleriyle değiştirmek için SOAP gövdesinde veri bağlamayı kullanabilirsiniz `{{DataSourceName.TableName.ColumnName}}` .

1. Testi çalıştırın. **Web performans test sonuçları görüntüleyicisinin** üst bölmesinde Web hizmeti isteğini seçin. Alt bölmede **Web tarayıcısı** sekmesini seçin. Web hizmeti tarafından döndürülen XML ve tüm işlemlerin sonuçları görüntülenir.

   Web hizmeti isteğinizin sonuçlarını arayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
