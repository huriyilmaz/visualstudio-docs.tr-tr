---
title: Kodlu web performans testleri
description: Web performans testini düzenleyemez ve özelleştirebileceğiniz kod tabanlı bir betike nasıl dönüştürebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 02e86eb41a05d880066be5aa102597b114d727d0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083797"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Kodlanmış web performans testi oluşturma

Web performans testleri, web uygulamanıza göz atarak kaydedilir. Testler, web uygulama performansını birden çok kullanıcının stresi altında ölçmek için yük testlerine dahil edilir. Web performans testi, diğer kaynak kodlarda olduğu gibi düzenleyemez ve özelleştirebileceğiniz kod tabanlı bir betik haline dönüştürmek için kullanılabilir. Örneğin, döngü ve dal oluşturma yapıları ekleme.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Kodlu web performans testi oluşturma

1. Web performans testi oluşturmadısanız bkz. [Web performans testini kaydetme.](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project)

2. Kodlu testi oluşturma.

     ![Kodlu web performans testi oluşturma](../test/media/web_test_coded_generate.png)

3. Testi bir adla girin.

     ![Kodlu web performans testi için bir ad girin](../test/media/web_test_coded_generate_nametest.png)

     Yeni kodlu test kod düzenleyicisinde açılır.

     Çözümünüze hangi web performansı ve yük testi proje şablonunu ekley istediğinize bağlı olarak, kod Visual Basic veya Visual C# içinde oluşturulur.

     ![Kod düzenleyicisinde yeni kodlu test açılır](../test/media/web_test_coded_generate_opencodeeditor.png)

     Kodda, C# içinde GetRequestEnumerator() yönteminin veya Visual Basic'daki Run() yönteminin, yeniden kodlu testte yer alan her doğrulama kuralını ve web isteğini içerdiğini bulabilirsiniz.

4. Bazı basit kod eklemeyi göstermek için yönteminin sonuna ve son web isteğinin koduna kadar aşağı kaydırın ve aşağıdaki kodu ekleyin:

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

5. Özel kodunuzun derlenmiş olduğunu doğrulamak için çözümü derle.

6. Testi çalıştırın.

     ![Kodlu web performans testini çalıştırma](../test/media/web_test_coded_generate_run.png)

     Bu çalıştırmanın olduğu gün Çarşamba olduğundan...

     ![Kodlu web performansı testi sonuçları](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Soru-Cevap

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>S: Aynı anda birden fazla test çalıştırabilirsiniz.
**A:** Evet, öğesinde sağ tıklama (bağlam) **menüsünü Çözüm Gezgini.**

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>S: Kodlu test oluşturmadan önce veya sonra bir veri kaynağı eklemeli miyim?
**A:** Kodlu testi [oluşturmadan önce bir](../test/add-a-data-source-to-a-web-performance-test.md) veri kaynağı eklemek daha kolaydır çünkü kod sizin için otomatik olarak oluşturulur.

Bir veri kaynağıyla kodlu bir test çalıştırarak aşağıdaki hata iletisini alabilirsiniz:

**Aracıda test \<Test Name> \<Computer Name> çalıştıramadı: Nesne başvurusu bir nesnenin örneğine ayarlanmaz.**

Bu durum, ilgili DataBindingAttribute olmadan test sınıfı için tanımlanmış bir DataSourceAttribute'uz olduğundan oluşabilir. Bu hatayı çözmek için uygun bir DataBindingAttribute ekleyin, silin veya koddan açıklama ekleyin.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>S: Kodlu test oluşturmadan önce veya sonra doğrulama ve ayıklama kuralları eklemeli miyim?
**A:** Kodlu testi oluşturmadan önce doğrulama kuralları ve ayıklama kuralları eklemek daha kolaydır; ancak doğrulama amacıyla [kodlanmış UI testlerini](../test/use-ui-automation-to-test-your-code.md) kullanmanizi öneririz.
