---
title: Iactivescriptauthor arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed0734fa48d58a5eae779c75c838c09215ed60a0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576164"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor Arabirimi
IntelliSense ve bilgi harmanlama dahil olmak üzere yazma hizmetlerini temsil eder.  
  
 @No__t_0 devralınan yöntemlere ek olarak, `IActiveScriptAuthor` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Kök düzeyindeki bir öğenin adını betik yazma altyapısının ad alanına ekler. *Kök düzeyindeki öğe* , Özellikler ve Yöntemler içerebilen ve bir olay kaynağı içerebilen bir nesnedir.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Kök düzeyi `IScriptNode` nesnenin alt öğesi olarak bir kod kod oluşturma yöntemi ekler. Konakta, kod oluşturma yöntemi tam adı yalnızca iki düzeye sahip olabilir.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Betik için ad alanına bir tür kitaplığı ekler.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|İstenen tamamlama bağlamının tamamlanma karakter kümesini döndürür.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Belirtilen özniteliklere sahip olan kod oluşturma yöntemi döndürür.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Kod bloğundaki belirli bir karakter için tür bilgilerini ve yer işareti konumlarını döndürür. Bu, üye IntelliSense, genel listeler ve parametre ipuçları hakkında bilgiler sağlar.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Dil bilgisini döndürür.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Yazarın betik ağacının `IScriptNode` kökünü döndürür.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Bir kod oluşturma yöntemi öğesinin metin özniteliklerini döndürür.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Bir betik bloğunun metin özniteliklerini döndürür.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Verilen bir karakterin uygulama tarafından bir deyimin tamamlanmasını yürütmesi gerekip gerekmediğini belirten bir değer döndürür.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Betik metnini ayrıştırır, metni yazma betiği yazma altyapısına ekler ve betik bloğuna karşılık gelen bir `IScriptEntry` nesnesi oluşturur.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Betik yazma altyapısının ad alanından bir `NamedItem` nesnesini kaldırır.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Betik yazma altyapısı ad alanından bir tür kitaplığını kaldırır.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Yazma Arabirimleri](../../winscript/reference/active-script-authoring-interfaces.md)