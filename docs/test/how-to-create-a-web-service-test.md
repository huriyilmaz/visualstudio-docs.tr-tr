---
title: Web hizmeti testi oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a6e42d6d92a74a0fc8be96c966b9146b7888b9e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589103"
---
# <a name="how-to-create-a-web-service-test"></a>Nasıl yapılır: web hizmeti testi oluşturma

Web performans testi, web hizmetleri test etmek için kullanabilirsiniz. Kullanarak **istek Ekle** ve **Web hizmeti isteği Ekle** seçenekleri, istekleri tek tek özelleştirebilirsiniz **Web Performans Testi Düzenleyicisi** web bulmak için hizmeti sayfaları. Genellikle, web uygulamasında bu sayfa görüntülenmez. Bu nedenle, bu sayfaları için erişim isteği özelleştirmeniz gerekir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Ticaret başlangıç Seti içinde yer alan bir web hizmeti aşağıdaki yordamları kullanın. Buradan indirebileceğiniz [gt;ASP.NET ticaret başlangıç Seti](https://sourceforge.net/projects/ppcsk/).

**Requirements**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Bir web hizmeti test etmek için

1. Yeni bir web performans testi oluşturun. Tarayıcı açıldığı anda, seçin **Durdur**.

2. İçinde **Web Performans Testi Düzenleyicisi**, web performans testi sağ tıklatın ve seçin **Web hizmeti isteği Ekle**.

3. İçinde **Url** türü adı web hizmetinin gibi yeni isteğin özelliğini **http://localhost/storecsvs/InstantOrder.asmx** .

4. Ayrı bir tarayıcı oturumu açın ve URL'sini yazın *.asmx* sayfasını **adresi** araç çubuğu. Test ve SOAP iletisi incelemek istediğiniz yöntemi seçin. İçerdiği bir `SOAPAction`.

5. İçinde **Web Performans Testi Düzenleyicisi**, istek sağ tıklayıp **üst bilgi Ekle** yeni üst bilgi eklemek için. İçinde **adı** özelliği, türü `SOAPAction`. İçinde **değer** özelliği, gördüğünüz değeri yazın `SOAPAction`, gibi `"http://tempuri.org/CheckStatus"`.

6. Düzenleyicide URL düğümünü genişletin, seçin **dize gövdesi** düğüm ve **içerik türü** özellik değerini girin `text/xml`.

7. 4\. adımda tarayıcıya dönün, web hizmeti açıklaması sayfasından SOAP isteği XML bölümünü seçin ve panoya kopyalayın.

8. XML içeriği, aşağıdaki örneğe benzer:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
     <soap:Body>
       <CheckStatus xmlns="http://tempuri.org/">
         <userName>string</userName>
         <password>string</password>
         <orderID>int</orderID>
       </CheckStatus>
     </soap:Body>
     </soap:Envelope>
     ```

9. Geri dönüp **Web Performans Testi Düzenleyicisi** ve ardından üç noktayı seçin **(...)**  içinde **dize gövdesi** özelliği. Pano içeriğini özelliğine yapıştırın.

10. XML içindeki herhangi bir yer tutucu değerlerini geçirmek test için geçerli değerlerle değiştirmeniz gerekir. Önceki örnekte iki örneğinden birini değiştirirler `string` diğeri `int`. Sipariş kayıtlı bir kullanıcı varsa bu web hizmeti işlemi yalnızca tamamlanır.

11. Web servisi isteği sağ tıklayıp **URL QueryString parametresi Ekle**.

12. Sorgu dizesi parametresi ad ve değer atayın. Önceki örnekte addır `op` ve değer `CheckStatus`. Bu web hizmeti işlemi gerçekleştirmek için tanımlar.

    > [!NOTE]
    > Veri bağlama kullanarak veri bağlama değerleriyle herhangi bir yer tutucu değerini değiştirmek için SOAP'daki kullanabileceğiniz `{{DataSourceName.TableName.ColumnName}}` söz dizimi.

13. Testi çalıştırın. Üst bölmesindeki **Web Performans Test Sonuçları Görüntüleyicisi**, web hizmeti isteğini seçin. Alt bölmede Web tarayıcısı sekmesini seçin. Web hizmeti tarafından döndürülen XML ve tüm işlemlerin sonuçları görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel kod ve yük testleri için eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
