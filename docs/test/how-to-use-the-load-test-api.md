---
title: Yük testi API 'SI
description: Yük testini denetleyen veya geliştiren test eklentilerini destekleyen yük testi API 'sini kullanmayı öğrenin.
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
ms.openlocfilehash: 4e11e100d6a97ee8c60834e4feefb667926eb599
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092442"
---
# <a name="how-to-use-the-load-test-api"></a>Nasıl yapılır: yük testi API 'sini kullanma

Visual Studio yük testini denetleyebilen veya geliştiren yük testi eklentilerini destekler. Yük testi eklentileri <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> , ad alanında bulunan arabirimi uygulayan kullanıcı tanımlı sınıflardır <xref:Microsoft.VisualStudio.TestTools.LoadTesting> . Yük testi eklentileri, bir sayaç veya hata eşiği karşılandığında yük testinin iptal edilme gibi özel yük testi denetimine izin verir. <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest>Kullanıcı tanımlı koddan yük testi parametrelerini almak veya ayarlamak için sınıfındaki özellikleri kullanın. <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest>Yük testi çalışırken bildirimlere temsilciler eklemek için sınıfındaki olayları kullanın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Ad alanını incelemek için nesne tarayıcısını kullanın <xref:Microsoft.VisualStudio.TestTools.LoadTesting> . hem Visual C# hem de Visual Basic düzenleyicileri, ad alanındaki sınıflarla kodlamak için ıntellisense desteği sunar.

Ayrıca, Web performans testleri için eklentiler de oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md) ve [nasıl yapılır: Istek düzeyi eklenti oluşturma](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>LoadTesting ad alanını kullanmak için

1. Bir yük testi içeren bir Web performansı ve yük testi projesi açın.

2. test çözümünüze bir Visual C# veya Visual Basic sınıf kitaplığı projesi ekleyin.

3. Web performansı ve yük testi projesinde sınıf kitaplığı projesine bir başvuru ekleyin.

4. Sınıf Kitaplığı projesindeki Microsoft. VisualStudio. QualityTools. LoadTestFramework DLL dosyasına bir başvuru ekleyin.

5. Sınıf kitaplığı projesinde bulunan sınıf dosyasında `using` ad alanı için bir ifade ekleyin <xref:Microsoft.VisualStudio.TestTools.LoadTesting> .

6. Arabirimini uygulayan bir ortak sınıf oluşturun <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> .

7. Projeyi derleyin.

8. Yeni Yük testi eklentisini Yük Testi Düzenleyicisi kullanarak ekleyin:

    1. Yük testinin kök düğümüne sağ tıklayın ve ardından **Yük testi eklentisi Ekle**' yi seçin.

    2. **Yük testi eklentisi Ekle** iletişim kutusu görüntülenir.

    3. **Seçili eklenti bölmesinin Özellikler** bölümünde, çalışma zamanında kullanılacak eklentinin başlangıç değerlerini ayarlayın.

        > [!NOTE]
        > Eklentilerinizi istediğiniz kadar çok özelliği kullanıma sunabilirsiniz. Bunları ortak, ayarlanabilir ve tamsayı, Boole veya dize gibi bir temel tür yapmanız yeterlidir. Ayrıca, daha sonra **Özellikler** penceresini kullanarak yük testi eklenti özelliklerini düzenleyebilirsiniz.

9. Yük testinizi çalıştırın.

     Uygulamasının uygulanması için <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> bkz. [nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapılır: Web başarım testi API 'sini kullanma](../test/how-to-use-the-web-performance-test-api.md)
- [Nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
