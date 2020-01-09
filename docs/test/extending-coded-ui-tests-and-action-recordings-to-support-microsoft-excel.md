---
title: Kodlanmış UI testlerini ve eylem kayıtlarını genişletme
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 05ccb885c799bf2bfd2e3868b80226eca726cc31
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589558"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Kodlanmış UI testlerini ve eylem kayıtlarını genişletme

Kodlanmış UI testleri ve eylem kayıtları için test çerçevesi, olası her kullanıcı arabirimini desteklemez. Test etmek istediğiniz belirli kullanıcı arabirimini desteklemiyor olabilir. Örneğin, bir Microsoft Excel elektronik tablosu için hemen kodlanmış UI testi veya eylem kaydı oluşturamazsınız. Ancak, kodlanmış UI test çerçevesinin genişletilebilirliğine katılarak, kendi uzantınızı, belirli kullanıcı arabirimini destekleyen kodlanmış UI test çerçevesi için oluşturabilirsiniz.

![UI test mimarisi](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Microsoft Excel 'i test etmek için örnek uzantı

Bu [blog gönderisi](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/3-introducing-sample-excel-extension/) , kodlanmış UI test çerçevesi için bir [örnek uzantının](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) bağlantısını içerir. Ayrıca, [KODLANMıŞ UI testi genişletilebilirliği için blog gönderisi serisinin](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/series-on-coded-ui-test-extensibility/)tamamını görüntüleyebilirsiniz.

> [!NOTE]
> Örnek, Microsoft Excel 2010 ile kullanılmak üzere tasarlanmıştır. Excel 'in diğer sürümleriyle çalışmayabilir ya da çalışmayabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
