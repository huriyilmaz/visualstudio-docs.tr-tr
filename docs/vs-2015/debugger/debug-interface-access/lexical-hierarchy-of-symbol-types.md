---
title: Sembol türlerinin sözcük hiyerarşisi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e70b83046c41b13cb51324eb63e81b26a118a81f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815734"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Simge Türlerinin Sözcük Hiyerarşisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıdaki tabloda, sözcük temelli hiyerarşide sembol türleri gösterilmektedir.  
  
## <a name="symbol-types"></a>Sembol türleri  
  
|Sembol türü|Description|  
|-----------------|-----------------|  
|[Ek Açıklama](../../debugger/debug-interface-access/annotation.md)|Program kodunda açıklamalı bir konum belirtir.|  
|[Block](../../debugger/debug-interface-access/block.md)|İşlevlerde iç içe kapsamları belirtir.|  
|`Compiland`|`compiland`. Exe dosyasına bağlı bir bağlantı belirtir.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Ek compiland ayrıntılarının yüklenmesi gereken compiland verilerini belirtir ve bu nedenle alınacak çalışma zamanı ek yüküne neden olur.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Compiland derlemesi için önemli olan ek ortam değişkenlerini belirtir.|  
|[Özel (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Kullanıcı tanımlı bir simge belirtir.|  
|[Veriler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Bu tür değişkenleri parametreler, yerel değişkenler, genel değişkenler ve sınıf üyeleri olarak belirtir.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Verilerin genel kapsamını belirtir; bir. exe veya. dll dosyasının tamamına karşılık gelir.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Hata ayıklamanın sona erdirmek için tanımlı bir noktaya sahip bir işlevi belirtir.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Hata ayıklamanın başlayacağı tanımlı bir noktaya sahip bir işlevi belirtir.|  
|[İşlev (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Bir işlevi belirtir.|  
|[Etiket (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Program kodundaki bir konumu belirtir.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Yürütülebilir program oluşturulurken görüntülenen bir dış simgeyi belirtir.|  
|[Dönüştürücü](../../debugger/debug-interface-access/thunk.md)|Bir belirtir `thunk` .|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Bir `namespace` tanımlayıcıyı belirtir.|  
  
> [!NOTE]
> Sembol türüne bağlı olarak ek sembol özellikleri kullanılabilir olabilir. Bu özellikler, tek sembol konularında listelenmiştir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol türlerinin sınıf hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Semboller ve sembol etiketleri](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
