---
title: Yük Testi API'si
description: Yük testini kontrol etmek veya geliştirmek için test eklentilerini destekleyen yük testi API'sini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 3764f0d6edd08bd4eddad842a703ed6d34c2b78f8d28f7d1236f78d2c67acb7a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395214"
---
# <a name="how-to-use-the-load-test-api"></a>Nasıl kullanılır: Yük testi API'sini kullanma

Visual Studio, yük testini kontrol altına alan veya geliştiren yük testi eklentilerini destekler. Yük testi eklentileri, ad alanı içinde bulunan arabirimi uygulayan <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> kullanıcı tanımlı <xref:Microsoft.VisualStudio.TestTools.LoadTesting> sınıflardır. Yük testi eklentileri, sayaç veya hata eşiğine karşı geldiğinde yük testini iptal etmek gibi özel yük testi denetimine olanak sağlar. Kullanıcı tanımlı koddan <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> yük testi parametrelerini almak veya ayarlamak için sınıfındaki özellikleri kullanın. Yük testi çalıştır <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> olduğunda bildirimler için temsilciler eklemek üzere sınıfındaki olayları kullanın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Ad alanını incelemek için nesne tarayıcısını <xref:Microsoft.VisualStudio.TestTools.LoadTesting> kullanın. Hem Visual C# hem de Visual Basic düzenleyicileri, ad alanı sınıflarına kodlama için IntelliSense desteği sağlar.

Web performans testleri için eklentiler de oluşturabilirsiniz. Daha fazla bilgi [için, bkz. How to: Create a web performance test plug-in](../test/how-to-create-a-web-performance-test-plug-in.md) ve [How to: Create a request-level plug-in](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>LoadTesting ad alanını kullanmak için

1. Yük testi içeren bir web performansı ve yük testi projesi açın.

2. Test çözümünüze bir Visual C# Visual Basic sınıf kitaplığı projesi ekleyin.

3. Web performansı ve yük testi projesine sınıf kitaplığı projesine bir başvuru ekleyin.

4. Sınıf Kitaplığı projesinde Microsoft.VisualStudio.QualityTools.LoadTestFramework DLL'lerine bir başvuru ekleyin.

5. Sınıf kitaplığı projesinde bulunan sınıf dosyasında, ad alanı için `using` bir deyimi <xref:Microsoft.VisualStudio.TestTools.LoadTesting> ekleyin.

6. Arabirimi uygulayan bir genel sınıf <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> oluşturun.

7. Projeyi derleyin.

8. Aşağıdakini kullanarak yeni yük testi eklenti Yük Testi Düzenleyicisi:

    1. Yük testinin kök düğümüne sağ tıklayın ve ardından Yük Testi **Eklentisi Ekle'yi seçin.**

    2. Yük **Testi Eklentisi Ekle iletişim** kutusu görüntülenir.

    3. Seçili **eklentinin Özellikler bölmesinde,** eklentinin çalışma zamanında kullanmak üzere başlangıç değerlerini ayarlayın.

        > [!NOTE]
        > Eklentilerinizi istediğiniz kadar çok özelliği ortaya çıkarabilirsiniz. Yalnızca bunları public, settable ve Integer, Boole veya String gibi bir temel türe göre ayarlayın. Daha sonra Özellikler penceresini kullanarak yük testi eklentisi özelliklerini de **düzenleyebilirsiniz.**

9. Yük testini çalıştırın.

     uygulamasının bir uygulaması için <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> bkz. Nasıl 2012: Yük [testi eklentisi oluşturma.](../test/how-to-create-a-load-test-plug-in.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl kullanılır: Web performansı test API'sini kullanma](../test/how-to-use-the-web-performance-test-api.md)
- [Nasıl: Yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
