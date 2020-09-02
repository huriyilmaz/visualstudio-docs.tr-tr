---
title: Kapsanan diller | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184284"
---
# <a name="contained-languages"></a>Kapsanan Dillerin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

*İçerilen diller* , diğer dillerin içerdiği dillerdir. Örneğin, sayfalardaki HTML, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] komut dosyaları içerebilir. . Aspx dosya Düzenleyicisi 'nin hem HTML hem de komut dosyası dili için IntelliSense, renklendirme ve diğer düzenleme özellikleri sağlaması için çift dil mimarisi gereklidir.  
  
## <a name="implementation"></a>Uygulama  
 Kapsanan diller için uygulamanız gereken en önemli arabirim <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> arabirimidir. Bu arabirim, birincil bir dil içinde barındırılabilecek herhangi bir dil tarafından uygulanır. Dil hizmetinin Colorizer, metin görünümü filtresi ve birincil dil hizmeti KIMLIĞINE erişim sağlar. , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> Bir arabirim oluşturmanıza olanak sağlar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> . Aşağıdaki adımlarda, içerilen bir dilin nasıl uygulanacağı gösterilmektedir:  
  
1. `QueryService()`Dil HIZMETI kimliğini ve ARABIRIM kimliğini almak için kullanın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> .  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A>Bir arabirim oluşturmak için yöntemini çağırın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> . Bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirim, bir veya daha fazla [öğe kimliği](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> arabirim geçirin.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>Metin arabelleği Düzenleyicisi nesnesi olan arabirim, birincil bir dosyadaki konumları ikincil dilin arabelleğine eşlemek için gereken temel hizmetleri sağlar.  
  
     Örneğin, tek bir. aspx dosyasında, birincil dosya ASP, HTML ve içerdiği tüm kodu içerir. Ancak, İkincil arabellek, ikincil arabelleği geçerli bir kod dosyası haline getirmek için, tüm sınıf tanımlarına sahip yalnızca içerilen kodu içerir. Arabellek Düzenleyicisi, bir arabellekten diğerine düzenleme yapma işini işler.  
  
4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>Birincil dil olan yöntemi, arabellek düzenleyicisine arabelleğin içindeki metnin ikincil arabellekte karşılık gelen metinle eşlendiğini söyler.  
  
     Dil, <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> Şu anda yalnızca birincil ve ikincil bir yayılma içeren bir yapının dizisini geçirir.  
  
5. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>Yöntemi ve yöntemi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> birincil ve ikincil arabelleğe eşlemeyi sağlar ve tam tersi de geçerlidir.
