---
title: Yük testleri için özel kod ve eklentiler oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3519a593182c199cc9f7a92cfb77e9c79bd1a9ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590104"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Yük testleri için özel kod ve eklentiler oluşturma

Özel eklenti, yazdığınız ve bir yük testine veya web performans testine eklediğiniz kodu kullanır. Yerleşik işlevsellik genişletmek için testler için özel eklentiler oluşturmak için yük testi API'sını ve web performans testi API'sini kullanabilirsiniz. Yükleme testinize birden çok eklenti ekleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-----------------------|
|**Yük testiniz için özel bir eklenti oluşturun**: Yük testinize daha fazla test işlevi eklemek için özel bir eklenti oluşturmak için yükleme testi API'sini kullanabilirsiniz.|-   [Nasıl kullanılır: Yük testi API'sini kullanın](../test/how-to-use-the-load-test-api.md)<br />-   [Nasıl yapılsın: Yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)|
|**Web Performans testiniz için özel bir eklenti oluşturun:** İstek düzeyinde de dahil olmak üzere web performans testinize daha fazla test işlevi eklemek için özel bir eklenti oluşturmak için web performans testi API'sını kullanabilirsiniz. Ayrıca bir web hizmeti testi oluşturabilirsiniz.<br /><br /> Ayrıca, bir web performans testini kaydedildikten sonra, ancak Web Performans Testi Sonuç Görüntüleyici'de görünmeden önce değiştirebilen bir web kaydedici eklentisi oluşturabilirsiniz.|-   [Nasıl kullanılır: Web performans testi API'sini kullanın](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Nasıl yapilir: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Nasıl yapilir: İstek düzeyi eklentisi oluşturma](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Nasıl?](../test/how-to-create-a-web-service-test.md)<br />-   [Nasıl yapilir: Kaydedici eklentisi oluşturma](../test/how-to-create-a-recorder-plug-in.md)|
|**Web Performans Test Sonuçları Görüntüleyici'ye UI özelliklerini ekleyin:** Visual Studio eklentisini kullanarak Web Performans Test Sonuçları Görüntüleyicisi'ne daha fazla Web Sürümü özelliği ekleyebilirsiniz.|-   [Nasıl yapIlir: Web performans testi sonuçları görüntüleyicisi için Visual Studio eklentisi oluşturma](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Özel bir HTTP gövde düzenleyicisi oluşturun:** Bir web hizmetinden ikili veya dize http XML yanıtlarını yeniden oluşturmak için özel bir düzenleyici oluşturabilirsiniz.|-   [Nasıl: Web performans testi düzenleyicisi için özel bir HTTP vücut düzenleyicisi oluşturun](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Başvuru

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Kodlanmış web performans testi oluşturma](../test/generate-and-run-a-coded-web-performance-test.md)
