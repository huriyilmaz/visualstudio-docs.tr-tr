---
title: Yük testi API 'SI
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 571abf14b1e17d85e21667c0ef0dbc3894b3ae76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653311"
---
# <a name="how-to-use-the-load-test-api"></a>Nasıl yapılır: yük testi API 'sini kullanma

Visual Studio, bir yük testini denetleyebilen veya geliştiren yük testi eklentilerini destekler. Yük testi eklentileri, <xref:Microsoft.VisualStudio.TestTools.LoadTesting> ad alanında bulunan <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> arabirimini uygulayan kullanıcı tanımlı sınıflardır. Yük testi eklentileri, bir sayaç veya hata eşiği karşılandığında yük testinin iptal edilme gibi özel yük testi denetimine izin verir. Kullanıcı tanımlı koddan yük testi parametrelerini almak veya ayarlamak için <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> sınıfındaki özellikleri kullanın. Yük testi çalışırken bildirimlere temsilciler iliştirmek için <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> sınıfındaki olayları kullanın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> @No__t_0 ad alanını incelemek için nesne tarayıcısını kullanın. Hem görsel C# hem de Visual Basic düzenleyiciler, ad alanındaki sınıflarla kodlama için IntelliSense desteği sunar.

Ayrıca, Web performans testleri için eklentiler de oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md) ve [nasıl yapılır: Istek düzeyi eklenti oluşturma](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>LoadTesting ad alanını kullanmak için

1. Bir yük testi içeren bir Web performansı ve yük testi projesi açın.

2. Test çözümünüze bir C# görsel veya Visual Basic sınıf kitaplığı projesi ekleyin.

3. Web performansı ve yük testi projesinde sınıf kitaplığı projesine bir başvuru ekleyin.

4. Sınıf Kitaplığı projesindeki Microsoft. VisualStudio. QualityTools. LoadTestFramework DLL dosyasına bir başvuru ekleyin.

5. Sınıf kitaplığı projesinde bulunan sınıf dosyasında, <xref:Microsoft.VisualStudio.TestTools.LoadTesting> ad alanı için `using` bir ifade ekleyin.

6. @No__t_0 arabirimini uygulayan bir ortak sınıf oluşturun.

7. Projeyi oluşturun.

8. Yeni Yük testi eklentisini Yük Testi Düzenleyicisi kullanarak ekleyin:

    1. Yük testinin kök düğümüne sağ tıklayın ve ardından **Yük testi eklentisi Ekle**' yi seçin.

    2. **Yük testi eklentisi Ekle** iletişim kutusu görüntülenir.

    3. **Seçili eklenti bölmesinin Özellikler** bölümünde, çalışma zamanında kullanılacak eklentinin başlangıç değerlerini ayarlayın.

        > [!NOTE]
        > Eklentilerinizi istediğiniz kadar çok özelliği kullanıma sunabilirsiniz. Bunları ortak, ayarlanabilir ve tamsayı, Boole veya dize gibi bir temel tür yapmanız yeterlidir. Ayrıca, daha sonra **Özellikler** penceresini kullanarak yük testi eklenti özelliklerini düzenleyebilirsiniz.

9. Yük testinizi çalıştırın.

     @No__t_0 uygulanması için bkz. [nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapılır: Web başarım testi API 'sini kullanma](../test/how-to-use-the-web-performance-test-api.md)
- [Nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)