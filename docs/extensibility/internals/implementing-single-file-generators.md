---
title: Single-File Oluşturucuları | Microsoft Docs
description: IVsSingleFileGenerator arabirimini uygulayan özel bir araç kullanarak Visual Basic ve Visual C# proje sistemlerini Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11ce8a69841d18d383e9d8e12c14d7af652d9cb8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900050"
---
# <a name="implementing-single-file-generators"></a>Tek Dosya Oluşturucular Ekleme
bazen tek dosya oluşturucu olarak da adlandırılan özel bir araç, 'de ve proje sistemlerini [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] genişletmek için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanılabilir. Özel araç, arabirimi uygulayan bir COM <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> bileşenidir. Özel bir araç, bu arabirimi kullanarak tek bir giriş dosyasını tek bir çıkış dosyasına dönüştürer. Dönüştürmenin sonucu kaynak kod veya yararlı olan başka bir çıkış olabilir. Özel araç tarafından oluşturulan kod dosyalarının iki örneği, bir görsel tasarımcıda yapılan değişikliklere yanıt olarak oluşturulan kod ve Web Hizmetleri Açıklama Dili (WSDL) kullanılarak oluşturulan dosyalardır.

 Özel bir araç yüklendiğinde veya giriş dosyası kaydedildikçe, proje sistemi yöntemini çağırarak bir geri çağırma arabirimine başvuru iletir ve aracın ilerlemesini kullanıcıya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> bildirebilinir.

 Özel aracın oluşturulan çıktı dosyası, giriş dosyasına bağımlılığı olan projeye eklenir. Proje sistemi, özel aracın uygulaması tarafından döndürülen dizeye göre çıkış dosyasının adını otomatik olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> belirler.

 Özel bir aracın arabirimini uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> gerekir. İsteğe bağlı olarak, özel araçlar <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> giriş dosyası dışında kaynaklardan bilgi almak için arabirimini destekler. Her durumda, özel bir araç kullanamadan önce bunu sisteme veya yerel kayıt defterine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaydetmeniz gerekir. Özel araçları kaydetme hakkında daha fazla bilgi için [bkz. Tek Dosya Oluşturucuları Kaydetme.](../../extensibility/internals/registering-single-file-generators.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Türleri Görsel Tasarımcıların Kullanımına Sunma](../../extensibility/internals/exposing-types-to-visual-designers.md)
