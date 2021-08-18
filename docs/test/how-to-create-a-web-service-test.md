---
title: Web Hizmeti Testi Oluşturma
description: Web hizmeti sayfalarını bulmak için web hizmetleri için performans testi kullanmayı ve Web Performans Testi Düzenleyicisi istekleri özelleştirmeyi öğrenin.
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
ms.technology: vs-ide-test
ms.openlocfilehash: b41f17b50c359ff7ff8f14bac99d783520a8bc5a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092507"
---
# <a name="how-to-create-a-web-service-test"></a>Nasıl yapılır: Web hizmeti testi oluşturma

Web hizmetlerini test etmek için bir web performans testi kullanabilirsiniz. İstek Ekle **ve** **Web** Hizmeti İsteği Ekle seçeneklerini kullanarak, web hizmeti sayfalarını bulmak **için Web Performans Testi Düzenleyicisi** istekleri tek tek özelleştirebilirsiniz. Genellikle, bu sayfaları web uygulamasında görüntülemezsiniz. Bu nedenle, bu sayfalara erişim kazanmak için isteği özelleştirmeniz gerekir.

>[!NOTE]
> Web performansı ve yük testi işlevleri 2019'Visual Studio kullanım dışıdır. Uygulama testi Analizler, çok adımlı web testleri webtest Visual Studio bağlıdır. Visual Studio [](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/) 2019'un web testi işlevselliğine sahip son sürüm olduğu duyurulmuştu. Yeni özellik eklenmezken, Visual Studio 2019'daki web testi işlevlerinin şu anda destekte olduğunu ve ürünün destek yaşam döngüsü boyunca destek olmaya devam edeceğini anlamak önemlidir. Ürün Azure İzleyici ekibi, çok adımlı kullanılabilirlik testlerinin geleceğiyle ilgili soruları burada ele [aldı.](https://github.com/MicrosoftDocs/azure-docs/issues/26050#issuecomment-468814101)

**Gereksinimler**

Visual Studio Enterprise

## <a name="to-create-a-simple-web-service"></a>Basit bir web hizmeti oluşturmak için

Test etmek için kendi web hizmetinizi kullanabilir veya web hizmetinize dahil olan temel Web Hizmeti (ASMX) Visual Studio. Bu şablonu kullanarak basit bir web hizmeti oluşturmak için:

1. Bu Visual Studio, ASP.NET Web Uygulaması (.NET Framework) şablonunu kullanarak yeni bir proje oluşturun ve  istendiğinde Boş şablonunu seçin. Bir ad yazın ve projeyi oluşturun.

1. Bu Çözüm Gezgini proje düğümüne sağ tıklayın, Yeni **Öğe** Ekle'yi seçin ve ardından Web Hizmeti  >   **(ASMX) öğesini seçin.** Web hizmetini ekleyin.

1. *WebService1.asmx'i* açın ve varsayılan `HelloWorld` web yöntemini aşağıdaki kodla değiştirin.

   ```csharp
   public string HelloWorld(string str)
   {
      return "Hello, " + str;
   }
   ```

## <a name="install-the-load-testing-component"></a>Yük testi bileşenini yükleme

Web performansı ve yük testi araçları bileşeni henüz yüklü değilse, web uygulaması aracılığıyla yüklemeniz Visual Studio Yükleyicisi.

1. Yeni **Visual Studio Yükleyicisi** başlat **menüsünden** Windows. Yeni proje iletişim kutusundan Visual Studio araç çubuğundan Araçlar Araçları ve Özellikleri Al'ı seçerek de  >   erişebilirsiniz.

1. Bu **Visual Studio Yükleyicisi** Tek bileşenler **sekmesini** seçin ve hata ayıklama ve test bölümüne **inin.** Web **performansı ve yük testi araçları'ı seçin.**

   ![Web performansı ve yük testi araçları bileşeni](media/web-perf-load-testing-tools-component.png)

1. Değiştir **düğmesini** seçin.

   Web performansı ve yük testi araçları bileşeni yüklenir.

## <a name="create-a-web-test-project"></a>Web testi projesi oluşturma

Web testi için Web Performansı ve Yük Testi Project şablonu gerekir. Bu bölümde bir C# yük testi projesi oluşturuz. Tercih ederseniz bir Visual Basic test projesi de oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

   Örnek Web Hizmeti (ASMX) şablonunu kullanıyorsanız, web testi projesini aynı çözüme ebilirsiniz.

2. Menü  > **çubuğundan** > **Project** Yeni Dosya'ya tıklayın.

   Yeni **Project** iletişim kutusu açılır.

3. Yeni **Project** iletişim kutusunda Yüklü ve  Visual **C#** öğesini genişletin ve ardından **Test kategorisini** seçin. Web Performansı **ve Yük Testi Project** seçin.

   ![Web performansı ve yük testi proje şablonu](media/web-perf-load-test-project-template.png)

4. Varsayılan adı kullanmak istemiyorsanız proje için bir ad girin ve tamam'ı **seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

   Örnek Web Hizmeti (ASMX) şablonunu kullanıyorsanız, web testi projesini aynı çözüme ebilirsiniz.

2. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

3. Yeni **proje oluştur sayfasında,** arama kutusuna **web testi** yazın ve ardından C# için Web Performansı ve Yük Testi Project **Kullanım \[ dışı]** şablonunu seçin. **İleri**’yi seçin.

4. Varsayılan adı kullanmak istemiyorsanız proje için bir ad girin ve oluştur'a **basın.**

::: moniker-end

   Visual Studio projeyi oluşturur ve dosyaları **Çözüm Gezgini.** Proje başlangıçta *WebTest1.webtest* adlı bir web test dosyası içerir.

## <a name="to-test-a-web-service"></a>Web hizmetini test etmek için

1. Web hizmetinizi başlatın ve gerekirse hizmeti duraklatmak **için Durdur'a** seçin.

1. Web testi projesinde, web *testini açan WebTest1.webtest* Web Performans Testi Düzenleyicisi. Test düzenleyicisinde web performans testini sağ tıklatın ve Web Hizmeti İsteği **Ekle'yi seçin.**

1. Yeni **isteğin Url** özelliğinde, web hizmetinin adını yazın, **https://localhost:44318/WebService1.asmx** örneğin: .

1. Web hizmeti için tarayıcının ayrı bir oturumunu açın ve Adres araç çubuğuna *.asmx* sayfasının **URL'sini** yazın. Web sayfasının üst kısmında, TEST etmek ve SOAP iletiyi incelemek istediğiniz yöntemi seçin. (Örnek web hizmette helloworld yöntemidir.) yöntemini açıp bir içerdiğini `SOAPAction` görüyorsunuz.

1. yeni **Web Performans Testi Düzenleyicisi** eklemek için isteke sağ tıklayın ve Üst **Bilgi Ekle'yi** seçin. Ad **özelliğine** `SOAPAction` yazın. Value **özelliğinde** içinde gördüğünüz değeri `SOAPAction` yazın, *http://tempuri.org/HelloWorld* örneğin.

1. Test düzenleyicisinde URL düğümünü genişletin, Dize Gövdesi **düğümünü** seçin ve İçerik Türü **özelliğinde** değerini `text/xml` girin.

1. 4. adımda tarayıcıya geri dönüp web hizmeti açıklama sayfasından SOAP isteğinin XML bölümünü seçin ve panoya kopyalayın.

   XML içeriği aşağıdaki örnekteki gibi olur:

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

1. Dize gövdesine Web Performans Testi Düzenleyicisi ve ardından Dize Gövdesi özelliğinde üç **noktayı** **(...)** seçin. Pano içeriğini özelliğine yapıştırın.

1. Testin başarılı olması için XML'de yer tutucu değerlerini geçerli değerlerle değiştirin. Önceki örnekte örneğini bir adla `string` değiştirirsiniz.

1. Web hizmeti isteğine sağ tıklayın ve URL Ekle **QueryString Parametresi'yi seçin.**

1. Sorgu dizesi parametresine bir ad ve değer attayabilirsiniz. Önceki örnekte, adı ve `op` değeri `HelloWorld` olur. Bu işlem, gerçekleştirecek web hizmeti işlemini tanımlar.

    > [!NOTE]
    > Söz dizimi kullanarak herhangi bir yer tutucu değerini veriye bağlı değerlerle değiştirmek için SOAP gövdesinde veri bağlamayı `{{DataSourceName.TableName.ColumnName}}` kullanabilirsiniz.

1. Testi çalıştırın. Web Performansı Görüntüleyicisi'nin **Test Sonuçları bölmesinde** web hizmeti isteğini seçin. Alt bölmede Web Tarayıcısı **sekmesini** seçin. Web hizmeti tarafından döndürülen XML ve tüm işlemlerin sonuçları görüntülenir.

   Web hizmeti isteğinizin sonuçlarını arama.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
