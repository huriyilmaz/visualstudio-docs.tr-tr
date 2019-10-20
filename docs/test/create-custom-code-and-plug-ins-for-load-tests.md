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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7cd3dbd5e7aeb00c2de1a656c26db3a377b8ffe8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665103"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Yük testleri için özel kod ve eklentiler oluşturma

Özel eklenti, yazdığınız ve bir yük testine veya bir Web başarım testine eklediğiniz kodu kullanır. Testlerin yerleşik işlevselliğine genişlemesine yönelik özel eklentiler oluşturmak için yük testi API 'SI ve Web performans testi API 'sini kullanabilirsiniz. Yük testinize birden çok eklenti ekleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-----------------------|
|**Yük testiniz için bir özel eklenti oluşturun**: yük testine daha fazla test işlevselliği eklemek için bir özel eklenti oluşturmak üzere yük testi API 'sini kullanabilirsiniz.|-   [nasıl yapılır: yük TESTI API 'Sini kullanma](../test/how-to-use-the-load-test-api.md)<br />-   [nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)|
|**Web performans testiniz için özel eklenti oluşturun:** Web performans test API 'sini, istek düzeyinde dahil olmak üzere Web performans testinize daha fazla test işlevselliği eklemek için kullanabilirsiniz. Ayrıca, bir Web hizmeti testi de oluşturabilirsiniz.<br /><br /> Ayrıca, kaydedildikten sonra, ancak Web Performans Testi Sonuç Görüntüleyicisi görüntülenmeden önce bir Web performans testini değiştirebilecek bir Web Kaydedicisi eklentisi oluşturabilirsiniz.|-   [nasıl yapılır: Web başarım TESTI API 'Sini kullanma](../test/how-to-use-the-web-performance-test-api.md)<br />-   [nasıl yapılır: Web başarım testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [nasıl yapılır: istek düzeyi eklentisi oluşturma](../test/how-to-create-a-request-level-plug-in.md)<br />-   [nasıl yapılır: Web hizmeti testi oluşturma](../test/how-to-create-a-web-service-test.md)<br />-   [nasıl yapılır: Kaydedici eklentisi oluşturma](../test/how-to-create-a-recorder-plug-in.md)|
|**Web performans test sonuçları görüntüleyicisine Kullanıcı arabirimi özellikleri ekleme:** Bir Visual Studio eklentisi kullanarak Web performans Test Sonuçları görüntüleyicisine daha fazla UI özelliği ekleyebilirsiniz.|-   [nasıl yapılır: Web performans testi sonuçları Görüntüleyicisi Için Visual Studio eklentisi oluşturma](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Özel http gövde Düzenleyicisi oluşturun:** Bir Web hizmetinden ikili veya dize http XML yanıtlarını düzenlemek için özel bir düzenleyici oluşturabilirsiniz.|-   [nasıl yapılır: Web Performans Testi Düzenleyicisi için özel http gövde Düzenleyicisi oluşturma](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Başvuru

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Kodlanmış Web performans testi oluşturma ve çalıştırma](../test/generate-and-run-a-coded-web-performance-test.md)