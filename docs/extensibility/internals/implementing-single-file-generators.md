---
title: Tek Dosyalı Jeneratörlerin Uygulanması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e700d09277edbb04b30676d3965b6c996d0a11f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707650"
---
# <a name="implementing-single-file-generators"></a>Tek Dosya Oluşturucular Ekleme
Özel bir araç - bazen tek bir dosya jeneratörü [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] olarak [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] anılacaktır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]- ve proje sistemlerini genişletmek için kullanılabilir. Özel bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> araç, arabirimi uygulayan bir COM bileşenidir. Bu arabirimi kullanarak, özel bir araç tek bir giriş dosyasını tek bir çıktı dosyasına dönüştürür. Dönüştürmenin sonucu kaynak kodu veya yararlı olan başka bir çıktı olabilir. Özel araç tarafından oluşturulan kod dosyalarının iki örneği, görsel tasarımcıdaki değişikliklere ve Web Hizmetleri Açıklama Dili (WSDL) kullanılarak oluşturulan dosyalara yanıt olarak oluşturulan koddur.

 Özel bir araç yüklendiğinde veya giriş dosyası kaydedildiğinde, proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> sistemi yöntemi çağırır ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> bir başvuruyu geri arama arabirimine geçirir ve bu şekilde araç ilerleme sini kullanıcıya bildirebilir.

 Özel aracın oluşturduğu çıktı dosyası, giriş dosyasına bağımlı olarak projeye eklenir. Proje sistemi, özel aracın uygulanması yla döndürülen dizeye göre çıktı dosyasının adını <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>otomatik olarak belirler.

 Özel bir araç <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> arabirimi uygulamalıdır. İsteğe bağlı olarak, <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> özel araçlar giriş dosyası dışındaki kaynaklardan bilgi almak için arabirimi destekler. Her durumda, özel bir aracı kullanmadan önce, sisteme veya yerel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kayıt defterine kaydetmeniz gerekir. Özel araçları kaydetme hakkında daha fazla bilgi için [bkz.](../../extensibility/internals/registering-single-file-generators.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Türleri Görsel Tasarımcıların Kullanımına Sunma](../../extensibility/internals/exposing-types-to-visual-designers.md)
