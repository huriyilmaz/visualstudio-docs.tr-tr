---
title: Kodlanmış UI Testlerini ve Eylem Kayıtlarını Genişletme
description: Kodlanmış UI test çerçevesinin genişletilebilirlik avantajını kullanarak belirli bir kullanıcı arabiriminiz için kodlanmış UI test çerçevesine uzantı oluşturma hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 454e2065068a4f79bff96776a050a43c049af5c3
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431308"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Kodlanmış UI testlerini ve eylem kayıtlarını genişletme

Kodlanmış UI testleri ve eylem kayıtları için test çerçevesi, olası her kullanıcı arabirimini desteklemez. Test etmek istediğiniz belirli kullanıcı arabirimini desteklemeyebilir. Örneğin, bir kullanıcı arabirimi elektronik tablosu için hemen kodlanmış ui testi veya eylem Microsoft Excel oluşturamazsiniz. Ancak, kodlanmış UI test çerçevesinin genişletilebilirlik avantajını kullanarak belirli kullanıcı arabiriminizi destekleyen kodlanmış UI test çerçevesine kendi uzantınızı oluşturabilirsiniz.

![UI Test Mimarisi](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Test etmek için örnek Microsoft Excel

Bu [blog gönderisi,](/archive/blogs/gautamg/3-introducing-sample-excel-extension) kodlanmış UI test çerçevesi için örnek bir uzantının bağlantısını içerir. Kodlanmış UI [test genişletilebilirliği için blog gönderisi serisinin tamamını da görüntüebilirsiniz.](/archive/blogs/gautamg/series-on-coded-ui-test-extensibility)

> [!NOTE]
> Örnek, örnekle birlikte kullanılmak üzere Microsoft Excel 2010. Uygulamanın diğer sürümleriyle çalışabiliyor veya Excel.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [Uıtestactionfilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri için en iyi yöntemler](../test/best-practices-for-coded-ui-tests.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)