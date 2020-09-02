---
title: Hata ayıklayıcıyı genişletmek için yol haritası | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695954"
---
# <a name="roadmap-for-extending-the-debugger"></a>Hata Ayıklayıcıyı Genişletmek için Yol Haritası
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu belge [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] , hata ayıklayıcıyı ile genişletmek için kılavuz ve başvuru bilgileri sağlar [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklama belgelerinin örnekleri, kapsamlı bir başvuru ve hata ayıklayıcıyı özelleştirmenin tipik yollarını gösteren çeşitli temsili senaryolar bulunur.  
  
 Derleyicinizi ve çıktısı, ürününüzün hata ayıklamayı uygulamak için ne yapmanız gerektiğini tespit ediyor. Derleyicinizi:  
  
- Windows yerel işletim sistemini hedefler ve a yazar. PDB dosyası, ile tümleştirilmiş yerel kod hata ayıklama altyapısı (DE) ile programlarda hata ayıklaması yapabilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Bir DE veya ifade değerlendirici uygulamanız gerekmez. İfade değerlendiricisi, C++ programlama dilinin sözdizimi için yazılmıştır.  
  
- Microsoft ara dili (MSIL) çıkışı üretir, yönetilen kod hata ayıklama altyapısı ile, ayrıca ile tümleştirilmiş programlarda hata ayıklaması yapabilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Bu nedenle, yalnızca bir ifade değerlendirici uygulamanız gerekir. Sizin için örnek bir ifade değerlendirici sunulmaktadır. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
     [İfade Değerlendirme](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [İfadeleri Değerlendirme](../../extensibility/debugger/evaluating-expressions.md)  
  
     [İfade Değerlendirme Bağlamı](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Kesme Modunda İfade Değerlendirme](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Ortak Dil Çalışma Zamanı İfade Değerlendiricisi Yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Özel bir işletim sistemini veya diğer bir çalışma zamanı ortamını hedefler, kendi DE yazmanız gerekir. ATL COM kullanarak basit bir DE oluşturan bir öğretici sunulmaktadır. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
     [Özel Hata Ayıklama Altyapısı Oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Öğretici: ATL COM kullanarak hata ayıklama altyapısı oluşturma](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Bağlantı Noktası Sağlayıcısı Uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
