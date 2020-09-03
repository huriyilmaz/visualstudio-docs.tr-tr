---
title: UdtKind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9fb22471cea7cd717b8969682a0e1f643f912150
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202376"
---
# <a name="udtkind"></a>UdtKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kullanıcı tanımlı farklı tür (UDT) açıklanmaktadır.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum UdtKind {   
   UdtStruct,  
   UdtClass,  
   UdtUnion,  
   UdtInterface  
};  
```  
  
## <a name="elements"></a>Öğeler  
 UdtStruct yapısı  
 UDT bir yapıdır.  
  
 UdtClass  
 UDT bir sınıftır.  
  
 Udtuniyon  
 UDT bir birleşimdir.  
  
 Udtınterface  
 UDT bir arabirimdir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu Numaralandırmadaki değerler [IDiaSymbol:: get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) yöntemi tarafından döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: cvconst. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar ve yapılar](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
