---
title: 'IDebugField:: Geiddeınfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3de21bc984a36db87f8ce1567f4ff7d97212c40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547565"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, bir alanla ilgili genişletilmiş bilgileri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `guidExtendedInfo`  
 'ndaki Döndürülecek bilgileri seçer. Geçerli değerler:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`guidConstantValue`|Değer bir bayt dizisi olarak.|  
|`guidConstantType`|Tür imzası olarak yazın.|  
  
 `prgBuffer`  
 dışı Genişletilmiş bilgileri döndürür.  
  
 `pdwLen`  
 [in, out] Genişletilmiş bilgilerin boyutunu bayt cinsinden döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Şu anda, bu yöntem yalnızca bir sabitin türünü veya değerini döndürür. Çağıran, `prgBuffer` com `CoTaskMemFree` Işlevi (C++) veya <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#) çağırarak ' de döndürülen arabelleği boşaltmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
