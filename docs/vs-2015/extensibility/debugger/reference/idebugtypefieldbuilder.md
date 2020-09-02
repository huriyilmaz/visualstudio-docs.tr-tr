---
title: Idebugtypefieldbuilder | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84a4da6bcd306e409582077f66fab1a40b7d7942
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199710"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir türü temsil eden alan oluşturma yeteneğini temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugTypeFieldBuilder : IUnknown  
```  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim, sembol sağlayıcısından alınır.  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim aşağıdaki yöntemleri uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Temel bir türü temsil eden bir nesne oluşturur.|  
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Belirtilen türe bir işaretçi oluşturur.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
