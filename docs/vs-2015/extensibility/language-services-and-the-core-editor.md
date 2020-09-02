---
title: Dil Hizmetleri ve çekirdek Düzenleyicisi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180299"
---
# <a name="language-services-and-the-core-editor"></a>Dil Hizmetleri ve Temel Düzenleyici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'daki düzenleyiciler sıklıkla bir dil hizmeti ile ilişkilendirilir. Bir dil hizmeti, diğer şeyler arasında sözdizimi renklendirme, ekstre tamamlama, IntelliSense ve metin biçimlendirme sağlar.  
  
## <a name="core-editors-and-document-data-objects"></a>Çekirdek düzenleyiciler ve belge verileri nesneleri  
 Çekirdek düzenleyiciye eriştiğinizde belge verileri ve belge görünümü nesneleri oluşturmayın. IDE, bu iki nesneyi oluşturur ve denetler ve düzenleyici fabrikası uygulamanızda uygun çağrıları yaparak bunlara işleyiciler elde edersiniz.  
  
 Daha fazla bilgi için bkz. [bir projede dosya açan düzenleyiciyi belirleme](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Dil Hizmetleri ve Temel Düzenleyici  
 Bir dil hizmeti uygulayarak, belge görünümünde verilerin nasıl görüntüleneceğini denetleyebilirsiniz. Dil hizmeti, Visual C++ gibi belirli bir dile özgü bilgi ve davranış sağlar. Bir metin arabelleği oluşturup açtığınız belge için dosya adı uzantısını belirlediğinizde, metin arabelleği, bu dosya adı uzantısıyla ilişkili dil hizmetini HKEY_LOCAL_MACHINE \Software\microsoft\düzenleyiciler \\ {YourLanguageService GUID} \ extensiondizinidir. Standart VSPackage yükleme yordamı, VSPackage 'ı yükler ve dil hizmetinizin bir örneği oluşturulur.  
  
 Temel dil hizmeti aşağıdaki çizimde gösterilmiştir.  
  
 ![Dil hizmeti modeli grafiği](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Çekirdek Düzenleyici ve dil hizmeti nesneleri  
  
 Çekirdek Düzenleyici için belge veri nesnesine bir metin arabelleği denir ve nesnesi tarafından temsil edilir <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> . Belge görünümü nesnesine metin görünümü denir ve nesne tarafından temsil edilir <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> . Bu iki nesne, temel düzenleyicinin Birleşik bir görünümünü sağlamak için dil hizmeti aracılığıyla birlikte çalışır. Metin arabelleğinden ve metin görünümündeki bilgiler, kod penceresi olarak adlandırılan bir belge penceresinde görüntülenir. Kod penceresi belgesi bir kod penceresi Yöneticisi tarafından yönetilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Eski API 'YI kullanarak bir dil hizmeti bağlamı sağlama](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense barındırma](../extensibility/intellisense-hosting.md)   
 [İçerilen diller](../extensibility/contained-languages.md)   
 [Eski Dil Hizmeti Geliştirme](../extensibility/internals/developing-a-legacy-language-service.md)
