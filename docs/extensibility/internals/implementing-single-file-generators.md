---
title: Tek dosya üreteçleri uygulama | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707650"
---
# <a name="implementing-single-file-generators"></a>Tek Dosya Oluşturucular Ekleme
Tek bir dosya Oluşturucu olarak da adlandırılan özel bir araç, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] içindeki ve proje sistemlerini genişletmek için kullanılabilir [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Özel bir araç, arabirimini uygulayan bir COM bileşenidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> . Bu arabirimi kullanarak, özel bir araç tek bir giriş dosyasını tek bir çıktı dosyasına dönüştürür. Dönüştürmenin sonucu, kaynak kodu veya yararlı olan herhangi bir çıkış olabilir. Bir görsel tasarımcıda ve Web Hizmetleri Açıklama Dili (WSDL) kullanılarak oluşturulan dosyalardaki değişikliklere yanıt olarak oluşturulan özel araç tarafından oluşturulan kod dosyaları için iki örnek kod verilebilir.

 Özel bir araç yüklendiğinde veya giriş dosyası kaydedildiğinde, proje sistemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> yöntemini çağırır ve bir geri çağırma arabirimine bir başvuru geçirir ve bu da <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> aracın ilerlemesini kullanıcıya bildirebilirler.

 Özel aracın oluşturduğu çıkış dosyası, giriş dosyasına bir bağımlılık ile projeye eklenir. Proje sistemi, özel aracın uygulamasının tarafından döndürülen dizeye göre çıkış dosyasının adını otomatik olarak belirler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .

 Özel bir aracın arabirimini uygulaması gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> . İsteğe bağlı olarak, Özel Araçlar <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> giriş dosyası dışındaki kaynaklardan bilgi almak için arabirimi destekler. Herhangi bir durumda, özel bir araç kullanabilmeniz için, bunu sisteme veya [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yerel kayıt defterine kaydetmeniz gerekir. Özel araçları kaydetme hakkında daha fazla bilgi için bkz. [tek dosya](../../extensibility/internals/registering-single-file-generators.md)oluşturucularını kaydetme.

## <a name="see-also"></a>Ayrıca bkz.
- [Türleri Görsel Tasarımcıların Kullanımına Sunma](../../extensibility/internals/exposing-types-to-visual-designers.md)
