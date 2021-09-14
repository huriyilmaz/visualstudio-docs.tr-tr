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
ms.openlocfilehash: 71ab67e5457d4616d9abbba0570443e6a1b2a817
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628160"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Kodlanmış UI testlerini ve eylem kayıtlarını genişletme

Kodlanmış UI testleri ve eylem kayıtları için test çerçevesi, olası her kullanıcı arabirimini desteklemez. Test etmek istediğiniz belirli kullanıcı arabirimini desteklemeyebilir. Örneğin, bir kullanıcı arabirimi elektronik tablosu için hemen kodlanmış ui testi veya eylem Microsoft Excel oluşturamazsiniz. Ancak, kodlanmış UI test çerçevesinin genişletilebilirlik avantajını kullanarak belirli kullanıcı arabiriminizi destekleyen kodlanmış UI test çerçevesine kendi uzantınızı oluşturabilirsiniz.

![UI Test Mimarisi](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Test etmek için örnek uzantı Microsoft Excel

Bu [blog gönderisi,](/archive/blogs/gautamg/3-introducing-sample-excel-extension) kodlanmış UI [test çerçevesi için](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) örnek bir uzantının bağlantısını içerir. Kodlanmış UI [test genişletilebilirliği için blog gönderisi serisinin tamamını da görüntüebilirsiniz.](/archive/blogs/gautamg/series-on-coded-ui-test-extensibility)

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