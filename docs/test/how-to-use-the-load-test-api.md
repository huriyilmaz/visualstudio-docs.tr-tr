---
title: Yük Testi API
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588817"
---
# <a name="how-to-use-the-load-test-api"></a>Nasıl kullanılır: Yük testi API'sini kullanın

Visual Studio, yük testini kontrol eden veya geliştirebilen yük testi eklentilerini destekler. Yük testi eklentileri, <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> <xref:Microsoft.VisualStudio.TestTools.LoadTesting> ad alanında bulunan arabirimi uygulayan kullanıcı tanımlı sınıflardır. Yük testi eklentileri, sayaç veya hata eşiği karşılandığında yük testinin iptali gibi özel yük testi denetimine olanak sağlar. Kullanıcı tanımlı <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> koddan yük testi parametrelerini almak veya ayarlamak için sınıftaki özellikleri kullanın. Yük testi çalışırken <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> bildirimler için temsilci eklemek için sınıftaki olayları kullanın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Ad alanını incelemek için <xref:Microsoft.VisualStudio.TestTools.LoadTesting> nesne tarayıcısını kullanın. Hem Visual C# hem de Visual Basic editörleri, ad alanındaki sınıflarla kodlama için IntelliSense desteği sunar.

Ayrıca web performans testleri için eklentiler oluşturabilirsiniz. Daha fazla bilgi için [bkz: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md) ve [nasıl yapIlec: İstek düzeyi eklentisi oluşturun.](../test/how-to-create-a-request-level-plug-in.md)

## <a name="to-use-the-loadtesting-namespace"></a>LoadTesting ad alanını kullanmak için

1. Bir yük testi içeren bir web performansı ve yük testi projesi açın.

2. Test çözümünüze Visual C# veya Visual Basic sınıf kitaplığı projesi ekleyin.

3. Sınıf kitaplığı projesine web performansına bir başvuru ekleyin ve yükleme testi projesine ekleyin.

4. Sınıf Kitaplığı projesinde Microsoft.VisualStudio.QualityTools.LoadTestFramework DLL adresine bir başvuru ekleyin.

5. Sınıf kitaplığı projesinde bulunan sınıf dosyasında, `using` <xref:Microsoft.VisualStudio.TestTools.LoadTesting> ad alanı için bir deyim ekleyin.

6. <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> Arabirimi uygulayan ortak bir sınıf oluşturun.

7. Projeyi derleyin.

8. Load Test Editor'u kullanarak yeni yük testi eklentisini ekleyin:

    1. Yük testinin kök düğümüne sağ tıklayın ve ardından **Yükle Testi Eklentisi Ekle'yi**seçin.

    2. **Yükle Testi Eklentisi** iletişim kutusu görüntülenir.

    3. **Seçili eklenti** bölmesinin Özellikleri'nde, eklentinin çalışma zamanında kullanması için ilk değerleri ayarlayın.

        > [!NOTE]
        > Eklentilerinizden istediğiniz kadar özellik ortaya çıkarabilirsiniz. Bunları herkese açık, ayarlanabilir ve Tamsayı, Boolean veya String gibi bir taban türüne ait hale getirin. Ayrıca, **Özellikler** penceresini kullanarak yük testi eklentiözelliklerini daha sonra da edinebilirsiniz.

9. Load testinizi çalıştırın.

     Bir uygulama <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>için , [bkz.](../test/how-to-create-a-load-test-plug-in.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl kullanılır: Web performans testi API'sini kullanın](../test/how-to-use-the-web-performance-test-api.md)
- [Nasıl yapılsın: Yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
