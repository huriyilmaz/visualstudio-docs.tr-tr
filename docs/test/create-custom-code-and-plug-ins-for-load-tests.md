---
title: Yük testleri için özel kod ve eklentiler oluşturma
description: Yük testi API'sini ve web performans testi API'sini kullanarak testlerin yerleşik işlevlere genişletecek özel eklentiler oluşturmasını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: b32cf0afed7d9a87babe34b0ebfeb781788f4504
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725627"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Yük testleri için özel kod ve eklentiler oluşturma

Özel bir eklenti, bir yük testi veya web performans testi yazmak ve eklemek için kod kullanır. Yük testi API'sini ve web performans testi API'sini kullanarak testlerin yerleşik işlevselliğine genişletecek özel eklentiler oluşturabilirsiniz. Yük teste birden çok eklenti eklemek için kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-----------------------|
|**Yük testi için özel bir** eklenti oluşturma: Yük testi API'sini kullanarak yük testinize daha fazla test işlevi eklemek için özel bir eklenti oluşturabilirsiniz.|-   [Nasıl kullanılır: Yük testi API'sini kullanma](../test/how-to-use-the-load-test-api.md)<br />-   [Nasıl: Yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)|
|**Web Performansı testi için özel bir eklenti oluşturun:** web performans testi API'sini kullanarak istek düzeyinde de dahil olmak üzere web performans testinize daha fazla test işlevi eklemek için özel bir eklenti oluşturabilirsiniz. Ayrıca bir web hizmeti testi de oluşturabilirsiniz.<br /><br /> Buna ek olarak, kaydedildikten sonra ancak web'de görünene kadar web performans testini değiştiren bir web kaydedici eklentisi Web Performans Testi Sonuç Görüntüleyicisi.|-   [Nasıl kullanılır: Web performans testi API'sini kullanma](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Nasıl: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Nasıl: İstek düzeyi eklenti oluşturma](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Nasıl: Web hizmeti testi oluşturma](../test/how-to-create-a-web-service-test.md)<br />-   [Nasıl kullanılır: Kaydedici eklentisi oluşturma](../test/how-to-create-a-recorder-plug-in.md)|
|**Web Performansı ve Görüntüleyicisi'ne kullanıcı arabirimi Test Sonuçları ekleyin:** Bir kullanıcı arabirimi eklentisini kullanarak Web Performansı Test Sonuçları Görüntüleyicisi'ne Visual Studio kullanıcı arabirimi özellikleri ekleyebilirsiniz.|-   [Nasıl yapılan: Web Visual Studio sonuçları görüntüleyicisi için yeni bir eklenti oluşturma](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Özel bir HTTP gövde düzenleyicisi oluşturun:** Bir web hizmetinin ikili veya dize http XML yanıtlarını düzenlemek için özel bir düzenleyici oluşturabilirsiniz.|-   [Nasıl olur: Web performans testi düzenleyicisi için özel bir HTTP gövde düzenleyicisi oluşturma](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Başvuru

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Kodlanmış web performans testi oluşturma](../test/generate-and-run-a-coded-web-performance-test.md)
