---
title: 'Idebugprimitivettypeınfo alanı:: GetPrimitiveType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetPrimitiveType
- IDebugPrimitiveTypeField::GetPrimitiveType
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09be168816140781a87528f981d5d93460cec65f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188125"
---
# <a name="idebugprimitivetypefieldgetprimitivetype"></a>IDebugPrimitiveTypeField::GetPrimitiveType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu alanla ilişkili temel türü alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetPrimitiveType (  
   DWORD* pdwType  
);  
```  
  
```csharp  
int GetPrimitiveType (  
   out uint pdwType  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwType`  
 dışı Temel türü temsil eden [CorElementType numaralandırmasındaki](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde döndürür `S_FALSE` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)
