---
title: Yük testi API'si
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3d949b8c73bb155b2e6fe4900c54c6d5314d26c4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588817"
---
# <a name="how-to-use-the-load-test-api"></a>Nasıl yapılır: yük testi API'si kullanma

Visual Studio Yük testi denetlemek veya geliştiren bir yük testi eklentileri destekler. Yük testi eklentileri olan kullanıcı tanımlı uygulayan sınıflar <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> arabirimi bulunan <xref:Microsoft.VisualStudio.TestTools.LoadTesting> ad alanı. Yük testi eklentileri, özel bir yük testi denetimi için gibi bir sayaç veya hata eşiğine ulaşıldığında bir yük testi iptal ediliyor izin verin. Özellikleri kullanın <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> almak veya yük testi parametrelerine kullanıcıdan ayarlamak için sınıf tanımlanan kod. Olayları kullanın <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> yük testi çalışırken, bildirimler için temsilciler eklemek için sınıfı.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> İncelemek için Nesne Tarayıcısı kullanmanız <xref:Microsoft.VisualStudio.TestTools.LoadTesting> ad alanı. Visual C# ve Visual Basic düzenleyicileri ad alanındaki sınıflarla kodlamak için IntelliSense desteği sunar.

Web performans testleri için eklentileri de oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md) ve [nasıl yapılır: istek düzeyi eklentisi oluşturma](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>LoadTesting ad alanını kullanmak için

1. Bir web performansı ve yük testi içeren bir yük testi projesi açın.

2. Visual C# veya Visual Basic kitaplık projesi sınama çözümünüze ekleyin.

3. Bir başvuru, sınıf kitaplığı projesi için web performansı ve yük testi projesi ekleyin.

4. Sınıf kitaplığı projesinde gt;Microsoft.VisualStudio.QualityTools.LoadTestFramework & DLL'ye bir başvuru ekleyin.

5. Sınıf kitaplığı projesinde yer alan sınıf dosyasında, ekleme bir `using` bildirimi <xref:Microsoft.VisualStudio.TestTools.LoadTesting> ad alanı.

6. Uygulayan bir ortak sınıf oluşturun <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> arabirimi.

7. Projeyi oluşturun.

8. Yeni Yük testi kullanarak Yük Testi Düzenleyicisi eklentisini ekleyin:

    1. Yük testi kök düğümüne sağ tıklayın ve ardından **Yük Testi Eklentisi Ekle**.

    2. **Yük Testi Eklentisi Ekle** iletişim kutusu görüntülenir.

    3. İçinde **özelliklerini çili eklenti** bölmesinde, çalışma zamanında kullanmak eklenti için başlangıç değerlerini ayarlayın.

        > [!NOTE]
        > Eklentilerinizi istediğiniz kadar çok özelliği kullanıma sunabilirsiniz. Bunları ortak, ayarlanabilir ve tamsayı, Boole veya dize gibi bir temel tür yapmanız yeterlidir. Yük Testi Eklentisi özelliklerini de düzenleyebilirsiniz daha sonra kullanarak **özellikleri** penceresi.

9. Yük testinizi çalıştırın.

     Bir uygulama için <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>, bkz: [nasıl yapılır: bir yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Özel kod ve yük testleri için eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapılır: web başarım testi API'si kullanma](../test/how-to-use-the-web-performance-test-api.md)
- [Nasıl yapılır: bir yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
