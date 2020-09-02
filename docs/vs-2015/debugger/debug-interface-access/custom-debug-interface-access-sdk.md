---
title: Özel (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Custom symbol
ms.assetid: a219fc83-d2a8-4bc5-b7e1-bfafeb247f16
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e1a1819178961ae0a4ccd02286d6a166fd18b8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164405"
---
# <a name="custom-debug-interface-access-sdk"></a>Özel (Arabirim Erişimi SDK'sında Hata Ayıklama)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bazı derleyiciler, standart sözlü sembol türlerinden herhangi biri tarafından tanımlanmayan semboller sunar. Bu semboller bir `SymTagCustom` etiketle tanımlanır.  
  
## <a name="properties"></a>Özellikler  
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.  
  
|Özellik|Veri türü|Açıklama|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|`BYTE`|Sembolle ilişkili veri dizisi.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagCustom` ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
