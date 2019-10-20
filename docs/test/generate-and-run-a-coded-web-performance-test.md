---
title: Kodlanmış Web performans testleri
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 082412d6773bbe69306f3cf95d10716f5675f3bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664933"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Kodlanmış web performans testi oluşturma

Web performans testleri, Web uygulamanıza göz atarak kaydedilir. Testler, birden çok kullanıcının stres altındayken Web uygulamanızın performansını ölçmek için yük testlerine dahil edilir. Web performans testi, diğer kaynak kodları gibi düzenleyebileceğiniz ve özelleştirebileceğiniz kod tabanlı bir betiğe dönüştürülebilir. Örneğin, döngü ve dallanma yapıları ekleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Kodlanmış Web performans testi oluşturma

1. Web performans testi oluşturmadıysanız, bkz. [Web performans testini kaydetme](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project).

2. Kodlanmış testi oluşturun.

     ![Kodlanmış Web performans testi oluşturma](../test/media/web_test_coded_generate.png)

3. Testi adlandırın.

     ![Kodlanmış Web performans testi için bir ad girin](../test/media/web_test_coded_generate_nametest.png)

     Yeni kodlanmış test kod düzenleyicisinde açılır.

     Çözümünüze eklediğiniz Web performansına ve yük testi projesi şablonuna bağlı olarak, kod Visual Basic ya da görselde C#oluşturulur.

     ![Yeni kodlanmış test kod düzenleyicisinde açılıyor](../test/media/web_test_coded_generate_opencodeeditor.png)

     İçindeki C#GetRequestEnumerator () yönteminin veya Visual Basic içindeki Run () yönteminin, tüm doğrulama kuralları ve tüm Web isteklerini içeren kodda görebilirsiniz.

4. Basit kod eklemeyi göstermek için, metodun sonuna kadar aşağı kaydırın ve son Web isteğinin kodundan sonra aşağıdaki kodu ekleyin:

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

5. Özel kodunuzun derlendiğini doğrulamak için çözümü oluşturun.

6. Testi çalıştırın.

     ![Kodlanmış Web performans testini çalıştırma](../test/media/web_test_coded_generate_run.png)

     Çünkü bu, çalıştırıldığı gün bir Çarşamba olarak gerçekleşti...

     ![Kodlanmış Web performans testi sonuçları](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Soru-cevap &

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>S: aynı anda birden fazla test çalıştırabilir miyim?
Y **:** Evet, **Çözüm Gezgini**' de sağ tıklama (bağlam) menüsünü kullanın.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>S: kodlanmış bir test oluşturmadan önce veya sonra bir veri kaynağı eklemem gerekir mi?
Y **:** Kod sizin için otomatik olarak oluşturulduğundan, kodlanmış testi oluşturmadan önce bir [veri kaynağı](../test/add-a-data-source-to-a-web-performance-test.md) eklemek daha kolaydır.

Bir veri kaynağıyla kodlanmış bir test çalıştırdığınızda aşağıdaki hata iletisini görebilirsiniz:

**Test \<Test name > aracı \<Computer adı > çalıştırılamadı: nesne başvurusu bir nesnenin örneğine ayarlanmadı.**

Bu, karşılık gelen bir DataBindingAttribute olmadan test sınıfı için tanımlanmış bir DataSourceAttribute olduğu için meydana gelebilir. Bu hatayı çözmek için uygun bir DataBindingAttribute ekleyin, silin veya kodun dışına yorum yapın.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>S: kodlanmış bir test oluşturmadan önce veya sonra doğrulama ve ayıklama kuralları eklemem gerekir mi?
Y **:** Kodlanmış testi oluşturmadan önce doğrulama kuralları ve ayıklama kuralları eklemek daha kolaydır; Ancak, doğrulama amaçları için [KODLANMıŞ UI testlerini](../test/use-ui-automation-to-test-your-code.md) kullanmanızı öneririz.