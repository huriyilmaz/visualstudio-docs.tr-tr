---
title: Web Performans Testi API
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e869bc46997ffb6ebecae2aa3e49c3cb6b2582fa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594350"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Nasıl kullanılır: Web performans testi API'sini kullanın

Web performans testleriniz için kod yazabilirsiniz. Web performans testi API, kodlanmış web performans testleri, web performans testi eklentileri, istek eklentileri, istekler, çıkarma kuralları ve doğrulama kuralları oluşturmak için kullanılır. Bu türleri oluşturan sınıflar bu API'deki temel sınıflardır. Bu API'deki diğer türler, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest> <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest> <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> , ve nesneleri oluşturmayı desteklemek için kullanılır. <xref:Microsoft.VisualStudio.TestTools.WebTesting> Özelleştirilmiş web performans testleri oluşturmak için ad alanını kullanırsınız.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Ayrıca, bildirimsel web performans testlerini programlı bir şekilde oluşturmak ve kaydetmek için web performans testi API'sini de kullanabilirsiniz. Bunu yapmak için, <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer> ve sınıfları kullanın.

> [!TIP]
> Ad alanını incelemek için <xref:Microsoft.VisualStudio.TestTools.WebTesting> nesne tarayıcısını kullanın. Hem Visual C# hem de Visual Basic editörleri, ad alanındaki sınıflarla kodlama için IntelliSense desteği sunar.

Yük testleri için eklentiler de oluşturabilirsiniz. Daha fazla bilgi için [bkz: Yük testi API'sini ve](../test/how-to-use-the-load-test-api.md) [Nasıl Kullanılır: Yük testi eklentisi oluşturun.](../test/how-to-create-a-load-test-plug-in.md)

## <a name="to-use-the-webtesting-namespace"></a>WebTest ad alanını kullanmak için

1. Web performans testi içeren bir web performansı ve yükleme testi projesi açın.

2. Test çözümünüze Visual C# veya Visual Basic sınıf kitaplığı projesi ekleyin.

3. Sınıf kitaplığı projesine web performansına bir başvuru ekleyin ve yükleme testi projesine ekleyin.

4. Sınıf kitaplığı projesinde Microsoft.VisualStudio.QualityTools.WebTestFramework DLL adresine bir başvuru ekleyin.

5. Sınıf kitaplığı projesinde bulunan sınıf `using` <xref:Microsoft.VisualStudio.TestTools.WebTesting> dosyasında, ad alanı için bir deyim ekleyin.

6. <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> Arabirimi uygulayan bir sınıf oluşturun.

7. Projeyi derleyin.

8. Web Performans Testi Düzenleyicisi'ni kullanarak yeni web performans testi eklentisini ekleyin:

    1. Araç çubuğunda **Web Testi Eklentisi Ekle'yi** seçin.

         **Web Test Eklentisi Eklentisi** iletişim kutusu görüntülenir.

    2. **Eklenti seç'in**altında, web performans testi eklentisi sınıfınızı seçin.

    3. **Seçili eklenti** bölmesinin Özellikleri'nde, eklentinin çalışma zamanında kullanması için ilk değerleri ayarlayın.

        > [!NOTE]
        > Eklentilerinizden istediğiniz kadar özellik ortaya çıkarabilirsiniz; onları herkese açık, ayarlanabilir ve Tamsayı, Boolean veya String gibi bir taban türüne ait hale getirin. Özellikler penceresini kullanarak web performans testi eklentiözelliklerini daha sonra da edinebilirsiniz.

    4. **Tamam'ı**seçin.

9. Web performans testinizi çalıştırın.

     Örnek bir uygulama <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>için , [bkz.](../test/how-to-create-a-web-performance-test-plug-in.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl kullanılır: Yük testi API'sini kullanın](../test/how-to-use-the-load-test-api.md)
- [Nasıl yapilir: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md)
