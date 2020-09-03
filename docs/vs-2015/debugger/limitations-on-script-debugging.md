---
title: Betik hata ayıklaması sınırlamaları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9f4f8f1e2fb014dc812bb5980d333e0a851f9222
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476810"
---
# <a name="limitations-on-script-debugging"></a>Betik Hata Ayıklamasında Sınırlamalar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bu konudaki sınırlamalara tabi olmak üzere istemci tarafı komut dosyası hatalarını ayıklamayı destekler.  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Istemci tarafı betiği ile kesme noktası eşleme sınırlamaları  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çalışma zamanında istemci tarafı dosyasına dönüştürülen bir sunucu tarafı ASPX veya HTML dosyasında bir kesme noktası ayarlamanıza olanak sağlar. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sunucu tarafı dosyasındaki kesme noktasını, istemci tarafı dosyasındaki karşılık gelen bir kesme noktasına, aşağıdaki sınırlamalara bağlı olarak eşler:  
  
- Kesme noktaları bloklar içinde ayarlanmalıdır `<script>` . Satır içi betikte veya `<% %>` bloklardaki kesme noktaları eşlenemez.  
  
- Sayfanın tarayıcı URL 'SI, sayfa adı içermelidir. Örneğin, `http://microsoft.com/default.apsx`. Kesme noktası eşleme, varsayılan sayfaya gibi bir adresten yeniden yönlendirmeyi tanıyamaz `http://microsoft.com` .  
  
- Kesme noktası, bir ASPX denetimi (ascx) dosyası, ana sayfa veya bu sayfanın içerdiği başka bir dosya içinde değil, tarayıcı URL 'sinde belirtilen sayfada ayarlanmalıdır. Dahil edilen sayfalarda ayarlanan kesme noktaları eşlenemez.  
  
- Bloklarda ayarlanan kesme noktaları `<script defer=true>` eşlenemez.  
  
- Bloklarda ayarlanan kesme noktaları için `<script id="">` , kesme noktası eşlemesi `id` özniteliği yoksayar.  
  
## <a name="breakpoint-mapping-and-duplicate-lines"></a>Kesme noktası eşleme ve yinelenen satırlar  
 Sunucu tarafı ve istemci tarafı komut dosyasında karşılık gelen konumu bulmak için, kesme noktası eşleme algoritması her satırdaki kodu inceler. Algoritma, her satırın benzersiz olduğunu varsayar. İki veya daha fazla satır aynı kodu içeriyorsa ve bu yinelenen satırlardan birinde bir kesme noktası ayarlarsanız, kesme noktası eşleme algoritması, istemci tarafı dosyasında yanlış yinelemeyi seçebilir. Bunu engellemek için, kesme noktasını ayarladığınız satıra bir açıklama ekleyin. Örnek:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```
