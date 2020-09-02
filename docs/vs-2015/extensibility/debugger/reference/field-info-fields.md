---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3f947db7606d6f7495cb1d88591aafa9e9933b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423718"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi hakkında hangi bilgilerin alınması gerektiğini belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Üyeler  
 FIF_FULLNAME  
 `bstrFullName` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) yapısındaki alanı başlatın/kullanın.  
  
 FIF_NAME  
 Yapıda alanı başlatın/kullanın `bstrName` `FIELD_INFO` .  
  
 FIF_TYPE  
 Yapıda alanı başlatın/kullanın `bstrType` `FIELD_INFO` .  
  
 FIF_MODIFIERS  
 Yapıda alanı başlatın/kullanın `bstrModifiers` `FIELD_INFO` .  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değerler aynı zamanda [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) yöntemine bir bağımsız değişken olarak geçirilir ve bu da [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) yapısının hangi alanlarının başlatıldığını belirtir.  
  
 Bu değerler, `dwFields` `FIELD_INFO` hangi alanların kullanıldığını ve geçerli olduğunu göstermek için yapının üyesinde de kullanılır.  
  
 Bu bayraklar bit düzeyinde birleştirilebilir `OR` .  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
