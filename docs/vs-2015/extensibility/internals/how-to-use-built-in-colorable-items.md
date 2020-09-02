---
title: 'Nasıl yapılır: yerleşik Renklenebilir öğeleri kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a86361f28eb4c73a65093fc5c80ef15ddf791a77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787392"
---
# <a name="how-to-use-built-in-colorable-items"></a>Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yerleşik renklenebilir öğeleri kullanmadan önce, kendi özel renksiz öğelerinizi sağlamaktan önce tümleşik geliştirme ortamına (IDE) işaret etmeniz gerekir ve bu durumda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> nesneler olur. Bu, dil hizmeti için bir kayıt defteri girişi ayarlayarak yapabilirsiniz.  
  
### <a name="to-use-built-in-colorable-items"></a>Yerleşik renklenebilir öğeleri kullanmak için  
  
1. HKEY_LOCAL_MACHINE \VisualStudio \\ *X. Y*\ Languages\language Services \\ *dil adı*' nın altında, *X. Y* bir sürümüdür [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve *dil adı* , dilinizin adıdır, adlı bir DWORD kayıt defteri giriş değeri oluşturun `RequestStockColors` .  
  
2. `RequestStockColors`Kayıt defteri girdisinin değerini 1 olarak ayarlayın.  
  
     Kayıt defteri girişini oluşturduktan sonra, Colorizer 'ın yöntemi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> Düzenleyici tarafından kullanılacak renk öznitelikleri dizisini dolduracak şekilde numaralandırmanın üyelerini kullanabilir.  
  
    > [!NOTE]
    > Özel renklenebilir öğeler sağlıyorsanız bu kayıt defteri girişini ayarlamayın. Daha fazla bilgi için bkz. [özel Renklenebilir öğeler](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel düzenleyicilerde söz dizimi renklendirmesi](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Eski dil hizmetinde söz dizimi renklendirmesi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Sözdizimi renklendirme uygulama](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Özel Renklenebilir öğeler](../../extensibility/internals/custom-colorable-items.md)   
 [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service2.md)
