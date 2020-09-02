---
title: Funcmı Gentıd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugEnd symbol
- debugging [DIA SDK], end point
ms.assetid: 68f84fff-7cd3-4636-b929-7063a45009f8
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa95b9001fe1d0b38da686cf60f1a291cc6cb5df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704855"
---
# <a name="funcdebugend"></a>FuncDebugEnd
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir işlevde hata ayıklamanın sona erdirmek için tanımlı bir nokta varsa, hata ayıklama başlangıç noktası etiketi ile bir sembol tarafından tanımlanır `SymTagFuncDebugEnd` .  
  
## <a name="properties"></a>Özellikler  
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.  
  
|Özellik|Veri türü|Açıklama|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Konumun konum parçası; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Konumun bölüm bölümü; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` işlev özel bir çağırma kuralı kullanıyorsa (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` Eğer işlevi bir far return gerçekleştirir (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` Eğer işlevi kesmede bir dönüş içeriyorsa (yalnızca DIA SDK V 8.0 veya üzeri).|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` işlev statikse (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan işlevin simgesi.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Bitiş noktalarında statik konum vardır; Ayrıntılar için bkz. [sembol konumları](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` işlev [noinline](https://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) özniteliğiyle belirtilirse (yalnızca DIA SDK v 8.0 veya üzeri).|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` işlev [noreturn](https://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) özniteliğiyle belirtilirse (yalnızca DIA SDK v 8.0 veya üzeri).|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` işlev hiçbir şekilde çağrılmadıysa (yalnızca DIA SDK V 8.0 veya üzeri).|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Simgenin bellekteki boşluğu; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel` .|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` işlevde iyileştirilmiş kod için hata ayıklama bilgileri varsa (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Modülün içindeki bu işlevin sonundaki göreli konum.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagFuncDebugEnd` ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Bu işlevin yürütülebilir görüntü içinde konumu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol türlerinin sözcük hiyerarşisi hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md)   
 [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)
