---
title: Web Performans Testi API'si
description: Kodlu web performansı testlerini, test eklentilerini, istek eklentilerini, istekleri ve ayıklama/doğrulama kurallarını destekleyen web performans testi API'si hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: ba9eccbfba9bd965969f426714eab51289c7e1fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139965"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Nasıl kullanılır: Web performans testi API'sini kullanma

Web performans testleriniz için kod yazabilirsiniz. Web performans testi API'si kodlu web performansı testleri, web performans testi eklentileri, istek eklentileri, istekler, ayıklama kuralları ve doğrulama kuralları oluşturmak için kullanılır. Bu türlerin sınıflarını bu API'nin temel sınıfları oluşturur. Bu API'nin diğer türleri , <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest> ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest> nesnelerinin <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> oluşturulmasını desteklemek için <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> kullanılır. Özelleştirilmiş web performans <xref:Microsoft.VisualStudio.TestTools.WebTesting> testleri oluşturmak için ad alanını kullanırsınız.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bildirime bağlı web performans testleri oluşturmak ve kaydetmek için web performans testi API'sini de kullanabilirsiniz. Bunu yapmak için ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> sınıflarını <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer> kullanın.

> [!TIP]
> Ad alanını incelemek için nesne tarayıcısını <xref:Microsoft.VisualStudio.TestTools.WebTesting> kullanın. Hem Visual C# hem de Visual Basic düzenleyicileri, ad alanı sınıflarına kodlama için IntelliSense desteği sağlar.

Ayrıca yük testleri için eklentiler de oluşturabilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: Yük testi API'sini](../test/how-to-use-the-load-test-api.md) kullanma ve Nasıl [kullanılır: Yük testi eklentisi oluşturma.](../test/how-to-create-a-load-test-plug-in.md)

## <a name="to-use-the-webtesting-namespace"></a>WebTesting ad alanını kullanmak için

1. Web performans testi içeren bir web performansı ve yük testi projesi açın.

2. Test çözümünüze bir Visual C# Visual Basic sınıf kitaplığı projesi ekleyin.

3. Web performansı ve yük testi projesine sınıf kitaplığı projesine bir başvuru ekleyin.

4. Sınıf kitaplığı projesinde Microsoft.VisualStudio.QualityTools.WebTestFramework DLL'lerine bir başvuru ekleyin.

5. Sınıf kitaplığı projesinde bulunan sınıf dosyasında, ad alanı için `using` bir deyimi <xref:Microsoft.VisualStudio.TestTools.WebTesting> ekleyin.

6. Arabirimi uygulayan bir sınıf <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> oluşturun.

7. Projeyi derleyin.

8. Yeni web performansı testi eklentisini aşağıdaki Web Performans Testi Düzenleyicisi:

    1. Araç **çubuğunda Web Testi Eklentisi Ekle'yi** seçin.

         **Web Testi Eklentisi Ekle** iletişim kutusu görüntülenir.

    2. Eklenti **seçin altında web** performans testi eklenti sınıfınızı seçin.

    3. Seçili **eklentinin Özellikler bölmesinde,** eklentinin çalışma zamanında kullanmak üzere başlangıç değerlerini ayarlayın.

        > [!NOTE]
        > Eklentilerinizin istediğiniz sayıda özelliği ortaya çıkarabilirsiniz; yalnızca bunları public, settable ve Integer, Boole veya String gibi bir temel türe göre ayarlayın. Daha sonra web performans testi eklenti özelliklerini düzenlemek için aşağıdaki Özellikler penceresi.

    4. **Tamam'ı seçin.**

9. Web performans testini çalıştırın.

     uygulamasının örnek bir uygulaması <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> için [bkz. Nasıl? Web performansı testi eklentisi oluşturma.](../test/how-to-create-a-web-performance-test-plug-in.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl kullanılır: Yük testi API'sini kullanma](../test/how-to-use-the-load-test-api.md)
- [Nasıl: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md)
