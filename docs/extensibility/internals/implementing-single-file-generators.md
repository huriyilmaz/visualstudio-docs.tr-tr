---
title: Tek dosya üreteçleri uygulama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69bde665e62d063b6bab8784634777eeea02e941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727173"
---
# <a name="implementing-single-file-generators"></a>Tek Dosya Oluşturucular Ekleme
Tek bir dosya Oluşturucu olarak da adlandırılan özel bir araç, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] içindeki [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ve [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proje sistemlerini genişletmek için kullanılabilir. Özel araç, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> arabirimini uygulayan bir COM bileşenidir. Bu arabirimi kullanarak, özel bir araç tek bir giriş dosyasını tek bir çıktı dosyasına dönüştürür. Dönüştürmenin sonucu, kaynak kodu veya yararlı olan herhangi bir çıkış olabilir. Bir görsel tasarımcıda ve Web Hizmetleri Açıklama Dili (WSDL) kullanılarak oluşturulan dosyalardaki değişikliklere yanıt olarak oluşturulan özel araç tarafından oluşturulan kod dosyaları için iki örnek kod verilebilir.

 Özel bir araç yüklendiğinde veya giriş dosyası kaydedildiğinde, proje sistemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> yöntemini çağırır ve bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> geri çağırma arabirimine bir başvuru geçirir ve bu da aracın ilerlemesini kullanıcıya bildirebilirler.

 Özel aracın oluşturduğu çıkış dosyası, giriş dosyasına bir bağımlılık ile projeye eklenir. Proje sistemi, özel aracın <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> uygulamasının döndürdüğü dizeye göre çıkış dosyasının adını otomatik olarak belirler.

 Özel bir aracın <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> arabirimini uygulaması gerekir. İsteğe bağlı olarak, özel araçlar giriş dosyası dışındaki kaynaklardan bilgi almak için <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> arabirimini destekler. Herhangi bir durumda, özel bir araç kullanabilmeniz için, uygulamayı sisteme veya [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yerel kayıt defterine kaydetmelisiniz. Özel araçları kaydetme hakkında daha fazla bilgi için bkz. [tek dosya](../../extensibility/internals/registering-single-file-generators.md)oluşturucularını kaydetme.

## <a name="see-also"></a>Ayrıca bkz.
- [Türleri Görsel Tasarımcıların Kullanımına Sunma](../../extensibility/internals/exposing-types-to-visual-designers.md)