---
title: Web Hizmeti Testi Oluşturma
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589103"
---
# <a name="how-to-create-a-web-service-test"></a>Nasıl yapılır: Web hizmeti testi oluşturma

Web hizmetlerini test etmek için bir web performans testi kullanabilirsiniz. Web Hizmeti **İsteği Ekle** ve **Ekle Web Hizmeti İsteği** seçeneklerini kullanarak, Web Hizmeti Test Düzenleyicisi'ndeki tek tek istekleri web hizmeti sayfalarını bulmak için özelleştirebilirsiniz. **Web Performance Test Editor** Genellikle, bu sayfaları web uygulamasında görüntülemezsiniz. Bu nedenle, bu sayfalara erişmek için isteği özelleştirmeniz gerekir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki yordamlar, Commerce Starter Kit'inde bulunan bir web hizmetini kullanır. [ASP.NET ticaret başlangıç kiti](https://sourceforge.net/projects/ppcsk/)indirebilirsiniz.

**Gereksinimler**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Bir web hizmetini test etmek için

1. Yeni bir web performans testi oluşturun. Tarayıcı açılır açılmaz **Durdur'u**seçin.

2. Web **Performans Testi Düzenleyicisi'nde,** web performans testine sağ tıklayın ve **Web Hizmeti İsteği Ekle'yi**seçin.

3. Yeni isteğin **Url** özelliğine, web hizmetinin adını yazın, örneğin. **http://localhost/storecsvs/InstantOrder.asmx**

4. Tarayıcının ayrı bir oturumunu açın ve **Adres** araç çubuğuna *.asmx* sayfasının URL'sini yazın. SOAP iletisini test etmek ve incelemek istediğiniz yöntemi seçin. Bir `SOAPAction`.

5. Web **Performans Testi**Düzenleyicisi'nde, isteğe sağ tıklayın ve yeni bir üstbilgi eklemek için **Üstbilgi Ekle'yi** seçin. **Ad** özelliğine, `SOAPAction`yazın. **Değer** özelliğinde, `SOAPAction`gördüğünüz değeri , `"http://tempuri.org/CheckStatus"`

6. Düzenleyicideki URL düğümünün genişletilmesi, **String Body** düğümünün seçimi ve **İçerik** Türü `text/xml`özelliğine bir değer girin.

7. Adım 4'teki tarayıcıya dönün, WEB hizmeti açıklama sayfasından SOAP isteğinin XML bölümünü seçin ve panoya kopyalayın.

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

9. **Web Performans Testi Düzenleyicisine** dönün ve string **gövdesi** özelliğindeki elipsleri **(...)** seçin. Pano içeriğini tesise yapıştırın.

10. Testin geçmesi için XML'deki herhangi bir yer tutucu değerlerini geçerli değerlerle değiştirmeniz gerekir. Önceki örnekte iki örnek `string` ve bir `int`değiştirirsiniz. Bu web hizmeti işlemi yalnızca sipariş vermiş kayıtlı bir kullanıcı varsa tamamlanır.

11. Web hizmeti isteğine sağ tıklayın ve **URL QueryString Parametre ekle'yi**seçin.

12. Sorgu dize parametresini bir ad ve değer atayın. Önceki örnekte, ad `op` ve değeri `CheckStatus`. Bu, gerçekleştirecek web hizmeti işlemini tanımlar.

    > [!NOTE]
    > Sözdizimini kullanarak herhangi bir yer tutucu değerini veri bağlama değerleriyle `{{DataSourceName.TableName.ColumnName}}` değiştirmek için SOAP gövdesindeki veri bağlamayı kullanabilirsiniz.

13. Testi çalıştırın. **Web Performans Testi Sonuçları Görüntüleyici'nin**üst bölmesinde, web hizmeti isteğini seçin. Alt bölmede web Tarayıcısekmesini seçin. Web hizmeti tarafından döndürülen XML ve tüm işlemlerin sonuçları görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
