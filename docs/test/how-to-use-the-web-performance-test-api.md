---
title: Web performans testi API 'SI
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d22c1962727d22af965c879de3ae5fea6d4e54af
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653306"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Nasıl yapılır: Web başarım testi API 'sini kullanma

Web performans testleriniz için kod yazabilirsiniz. Web performans testi API 'SI, kodlanmış Web performans testleri, Web performans testi eklentileri, istek eklentileri, istekler, ayıklama kuralları ve doğrulama kuralları oluşturmak için kullanılır. Bu türleri oluşturan sınıflar, bu API 'deki temel sınıflardır. Bu API 'deki diğer türler <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> nesnelerini oluşturmayı desteklemek için kullanılır. Özelleştirilmiş Web performans testleri oluşturmak için <xref:Microsoft.VisualStudio.TestTools.WebTesting> ad alanını kullanırsınız.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Ayrıca, bildirim temelli Web performans testlerini programlı bir şekilde oluşturmak ve kaydetmek için Web performans testi API 'sini de kullanabilirsiniz. Bunu yapmak için <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer> sınıflarını kullanın.

> [!TIP]
> @No__t_0 ad alanını incelemek için nesne tarayıcısını kullanın. Hem görsel C# hem de Visual Basic düzenleyiciler, ad alanındaki sınıflarla kodlama için IntelliSense desteği sunar.

Ayrıca, yük testleri için eklentiler de oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yük TESTI API 'Sini kullanma](../test/how-to-use-the-load-test-api.md) ve [nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>WebTesting ad alanını kullanmak için

1. Web performans testi içeren bir Web performans ve yük testi projesi açın.

2. Test çözümünüze bir C# görsel veya Visual Basic sınıf kitaplığı projesi ekleyin.

3. Web performansı ve yük testi projesinde sınıf kitaplığı projesine bir başvuru ekleyin.

4. Sınıf Kitaplığı projesindeki Microsoft. VisualStudio. QualityTools. WebTestFramework DLL dosyasına bir başvuru ekleyin.

5. Sınıf kitaplığı projesinde bulunan sınıf dosyasında, <xref:Microsoft.VisualStudio.TestTools.WebTesting> ad alanı için `using` bir ifade ekleyin.

6. @No__t_0 arabirimini uygulayan bir sınıf oluşturun.

7. Projeyi oluşturun.

8. Yeni Web performans testi eklentisini Web Performans Testi Düzenleyicisi kullanarak ekleyin:

    1. Araç çubuğunda **Web testi eklentisi Ekle** ' yi seçin.

         **Web testi eklentisi Ekle** iletişim kutusu görüntülenir.

    2. **Eklenti seçin**altında Web başarım testi eklenti sınıfınızı seçin.

    3. **Seçili eklenti bölmesinin Özellikler** bölümünde, çalışma zamanında kullanılacak eklentinin başlangıç değerlerini ayarlayın.

        > [!NOTE]
        > Eklentilerinizi istediğiniz kadar çok özelliği kullanıma sunabilirsiniz. bunları ortak, ayarlanabilir ve tamsayı, Boole veya dize gibi bir temel tür yapmanız yeterlidir. Ayrıca, daha sonra Özellikler penceresi kullanarak Web performans testi eklentisi özelliklerini düzenleyebilirsiniz.

    4. **Tamam ' ı**seçin.

9. Web performans testinizi çalıştırın.

     @No__t_0 örnek bir uygulama için bkz. [nasıl yapılır: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapılır: yük testi API 'sini kullanma](../test/how-to-use-the-load-test-api.md)
- [Nasıl yapılır: Web başarım testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md)