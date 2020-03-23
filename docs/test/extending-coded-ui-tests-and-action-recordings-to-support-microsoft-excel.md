---
title: Kodlu UI Testlerini ve Eylem Kayıtlarını Genişlet
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 05ccb885c799bf2bfd2e3868b80226eca726cc31
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589558"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Kodlanmış UI testlerini ve eylem kayıtlarını genişletme

Kodlanmış Kullanıcı Arabirimi testleri ve eylem kayıtları için test çerçevesi olası her kullanıcı arabirimini desteklemez. Test etmek istediğiniz belirli u-u bilgi sini desteklemeyebilir. Örneğin, bir Microsoft Excel elektronik tablosu için hemen kodlanmış bir ui testi veya eylem kaydı oluşturamazsınız. Ancak, kodlanmış UI test çerçevesinin genişletilebilirliğinden yararlanarak belirli UI'nizi destekleyen kodlanmış UI test çerçevesine kendi uzantınızı oluşturabilirsiniz.

![UI Test Mimarisi](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Microsoft Excel'i test etmek için örnek uzantı

Bu [blog gönderisi,](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/3-introducing-sample-excel-extension/) kodlanmış UI test çerçevesi için örnek bir [uzantıya](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) bağlantı içerir. Ayrıca [kodlanmış UI test genişletilebilirlik için](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/series-on-coded-ui-test-extensibility/)tüm blog yazısı serisi görüntüleyebilirsiniz.

> [!NOTE]
> Örnek Microsoft Excel 2010 ile kullanılmak üzere tasarlanmıştır. Excel'in diğer sürümlerinde çalışabilir veya çalışmayabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [Uıtestactionfilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış Ara Birimi testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
