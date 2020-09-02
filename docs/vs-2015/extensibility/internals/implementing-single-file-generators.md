---
title: Tek dosya üreteçleri uygulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2ca842f05692d5d47ed42470f58f2be0bb45007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192695"
---
# <a name="implementing-single-file-generators"></a>Tek Dosya Oluşturucular Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tek bir dosya Oluşturucu olarak da adlandırılan özel bir araç, [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] içindeki ve proje sistemlerini genişletmek için kullanılabilir [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Özel bir araç, arabirimini uygulayan bir COM bileşenidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> . Bu arabirimi kullanarak, özel bir araç tek bir giriş dosyasını tek bir çıktı dosyasına dönüştürür. Dönüştürmenin sonucu, kaynak kodu veya yararlı olan herhangi bir çıkış olabilir. Bir görsel tasarımcıda ve Web Hizmetleri Açıklama Dili (WSDL) kullanılarak oluşturulan dosyalardaki değişikliklere yanıt olarak oluşturulan özel araç tarafından oluşturulan kod dosyaları için iki örnek kod verilebilir.  
  
 Özel bir araç yüklendiğinde veya giriş dosyası kaydedildiğinde, proje sistemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> yöntemini çağırır ve bir geri çağırma arabirimine bir başvuru geçirir ve bu da <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> aracın ilerlemesini kullanıcıya bildirebilirler.  
  
 Özel aracın oluşturduğu çıkış dosyası, giriş dosyasına bir bağımlılık ile projeye eklenir. Proje sistemi, özel aracın uygulamasının tarafından döndürülen dizeye göre çıkış dosyasının adını otomatik olarak belirler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .  
  
 Özel bir aracın arabirimini uygulaması gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> . İsteğe bağlı olarak, Özel Araçlar <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> giriş dosyası dışındaki kaynaklardan bilgi almak için arabirimi destekler. Herhangi bir durumda, özel bir araç kullanabilmeniz için, bunu sisteme veya [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yerel kayıt defterine kaydetmeniz gerekir. Özel araçları kaydetme hakkında daha fazla bilgi için bkz. [tek dosya](../../extensibility/internals/registering-single-file-generators.md)oluşturucularını kaydetme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Projenin varsayılan ad alanını belirleme](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Türleri Görsel Tasarımcıların Kullanımına Sunma](../../extensibility/internals/exposing-types-to-visual-designers.md)
