---
title: Web hizmeti testi oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4bbc7423c3f08665109c17d25d43ae6d9d652100
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653604"
---
# <a name="how-to-create-a-web-service-test"></a>Nasıl yapılır: Web hizmeti testi oluşturma

Web hizmetlerini test etmek için bir Web performans testi kullanabilirsiniz. **Ekleme isteği** ve **Web hizmeti isteği ekleme** seçeneklerini kullanarak, Web hizmeti sayfalarını bulmak için **Web Performans Testi Düzenleyicisi** bireysel istekleri özelleştirebilirsiniz. Genellikle, bu sayfaları Web uygulamasında göstermeyin. Bu nedenle, bu sayfalara erişim kazanmak için isteği özelleştirmeniz gerekir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki yordamlar, Commerce Starter Kit içinde bulunan bir Web hizmetini kullanır. [ASP.NET Commerce Starter Kit](http://go.microsoft.com/fwlink/?LinkId=181469)'ten indirebilirsiniz.

**Requirements**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Bir Web hizmetini test etmek için

1. Yeni bir Web performans testi oluşturun. Tarayıcı açıldığı anda **Durdur**' u seçin.

2. **Web Performans Testi Düzenleyicisi**Web performans testini sağ tıklatın ve **Web hizmeti isteği Ekle**' yi seçin.

3. Yeni isteğin **URL** özelliğinde, **http://localhost/storecsvs/InstantOrder.asmx** gibi Web hizmetinin adını yazın.

4. Tarayıcının ayrı bir oturumunu açın ve **Adres** araç çubuğunda *. asmx* sayfasının URL 'sini yazın. Sınamak istediğiniz yöntemi seçin ve SOAP iletisini inceleyin. Bir `SOAPAction` içerir.

5. **Web Performans Testi Düzenleyicisi**, isteğe sağ tıklayın ve yeni bir üst bilgi eklemek Için **üst bilgi Ekle** ' yi seçin. **Ad** özelliğinde `SOAPAction` yazın. **Değer** özelliğinde, `"http://tempuri.org/CheckStatus"` gibi `SOAPAction` gördüğünüz değeri yazın.

6. Düzenleyicide URL düğümünü genişletin, **dize gövdesi** düğümünü seçin ve **içerik türü** özelliği `text/xml` bir değer girin.

7. 4\. adımdaki tarayıcıya geri dönün, Web hizmeti Açıklama sayfasından SOAP isteğinin XML bölümünü seçin ve panoya kopyalayın.

8. XML içeriği aşağıdaki örneğe benzer:

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

9. **Web Performans Testi Düzenleyicisi** dönüp **dize gövdesi** özelliğindeki üç nokta **(...)** simgesini seçin. Panonun içeriğini özelliğine yapıştırın.

10. XML 'deki herhangi bir yer tutucu değerini, testin geçirilecek geçerli değerlerle değiştirmeniz gerekir. Önceki örnekte, iki `string` örneğini ve bir `int` değiştirirsiniz. Bu Web hizmeti işlemi, yalnızca sipariş veren kayıtlı bir kullanıcı varsa tamamlanır.

11. Web hizmeti isteğine sağ tıklayıp **URL QueryString parametresi Ekle**' yi seçin.

12. Sorgu dizesi parametresine bir ad ve değer atayın. Önceki örnekte, ad `op` ve değer `CheckStatus`. Bu, gerçekleştirilecek Web hizmeti işlemini belirler.

    > [!NOTE]
    > @No__t_0 sözdizimini kullanarak herhangi bir yer tutucu değerini veri bağlama değerleriyle değiştirerek, SOAP gövdesinde veri bağlamayı kullanabilirsiniz.

13. Testi çalıştırın. **Web performans test sonuçları görüntüleyicisinin**üst bölmesinde Web hizmeti isteğini seçin. Alt bölmede Web tarayıcısı sekmesini seçin. Web hizmeti tarafından döndürülen XML ve tüm işlemlerin sonuçları görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)