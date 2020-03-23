---
title: Kodlanmış web performans testleri
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, creating
- code, Web performance tests
- Web performance tests, coded
ms.assetid: 169e48f9-52fd-4d0b-83d9-54913bde506b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4297f60c74e32b904d7c36912a8377d33f23ebdf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589584"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Kodlanmış web performans testi oluşturma

Web performans testleri, web uygulamanızda göz atarak kaydedilir. Testler, web uygulamanızın performansını birden çok kullanıcının stresi altında ölçmek için yük testlerine dahil edilir. Web performans testi, diğer kaynak kodlar gibi değiştirebileceğiniz ve özelleştirebileceğiniz kod tabanlı bir komut dosyasına dönüştürülebilir. Örneğin, döngü ve dallanma yapıları ekleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Kodlanmış bir web performans testi oluşturma

1. Bir web performans testi oluşturmadıysanız, [bkz.](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project)

2. Kodlanmış testi oluşturun.

     ![Kodlanmış bir web performans testi oluşturma](../test/media/web_test_coded_generate.png)

3. Testi adlandırın.

     ![Kodlanmış web performans testi için bir ad girin](../test/media/web_test_coded_generate_nametest.png)

     Kod düzenleyicisinde yeni kodlu test açılır.

     Çözümünüze eklediğiniz web performansı ve yük testi proje şablonuna bağlı olarak, kod Visual Basic veya Visual C#'da oluşturulur.

     ![Kod düzenleyicisinde yeni kodlu test açılır](../test/media/web_test_coded_generate_opencodeeditor.png)

     Kodda, C#'daki GetRequestEnumerator() yönteminin veya Visual Basic'teki Çalıştır() yönteminin yeniden kodlanmış testte bulunan her doğrulama kuralını ve web isteğini içerdiğini görebilirsiniz.

4. Bazı basit kod eklemeyi göstermek için, yöntemin sonuna ve son web isteği için koddan sonra aşağı kaydırın ve aşağıdaki kodu ekleyin:

    ```c#
    if (DateTime.Today.DayOfWeek == DayOfWeek.Wednesday)
    {
        WebTestRequest customRequest = new WebTestRequest("http://weather.msn.com/");
        yield return customRequest;
    }
    else
    {
        WebTestRequest customRequest = new WebTestRequest("https://msdn.microsoft.com/");
        yield return customRequest;
    }
    ```

    ```vb
    If DateTime.Today.DayOfWeek = DayOfWeek.Wednesday Then
        Dim customRequest As WebTestRequest = New WebTestRequest("http://weather.msn.com/")
        MyBase.Send(customRequest)
    Else
        Dim customRequest As WebTestRequest = New WebTestRequest("https://msdn.microsoft.com/")
        MyBase.Send(customRequest)
    End If
    ```

5. Özel kodunuzu derlediğini doğrulamak için çözüm oluşturun.

6. Testi çalıştırın.

     ![Kodlanmış web performans testini çalıştırma](../test/media/web_test_coded_generate_run.png)

     Ve bu gün bu bir Çarşamba oldu çalıştırmak çünkü ...

     ![Kodlanmış web performans testi sonuçları](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Soru-Cevap

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>S: Aynı anda birden fazla test çalıştırabilir miyim?
**A:** Evet, **Solution Explorer'da**sağ tıklatma (bağlam) menüsünü kullanın.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>S: Kodlanmış bir test oluşturmadan önce veya sonra bir veri kaynağı eklemeli miyim?
**A:** Kod sizin için otomatik olarak oluşturulacağı için, kodlanmış testi oluşturmadan önce bir [veri kaynağı](../test/add-a-data-source-to-a-web-performance-test.md) eklemek daha kolaydır.

Bir veri kaynağı ile kodlanmış bir test çalıştırdığınızda, aşağıdaki hata iletisi görebilirsiniz:

**Aracı \<Bilgisayar \<Adı>> test adı> çalıştırılamadım: Nesne başvurusu bir nesnenin bir örneğine ayarlanmaz.**

Bu, test sınıfı için tanımlanan bir DataSourceAttribute'unuzun karşılık gelen databindingattribute olmadan olması nedeniyle oluşabilir. Bu hatayı gidermek için uygun bir DataBindingAttribute ekleyin, silin veya kod dışında yorum.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>S: Kodlanmış bir test oluşturmadan önce veya sonra doğrulama ve çıkarma kuralları eklemeli miyim?
**A:** Kodlanmış testi oluşturmadan önce doğrulama kuralları ve çıkarma kuralları eklemek daha kolaydır; ancak, doğrulama amacıyla [kodlanmış UI testlerini](../test/use-ui-automation-to-test-your-code.md) kullanmanızı öneririz.
