---
title: 'IDebugProviderProgramNode2:: Unmarshaldebuggeeınterface | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3007d13ec3eae46511e4775497d0aad5b6325b2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146258"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

İşlem sınırları genelinde belirtilen bir arabirimi edinir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `riid`  
 'ndaki Elde edilecek arabirimin GUID 'ı.  
  
 `ppvObject`  
 dışı İstenen arabirimi uygulayan nesneyi döndürür. [C++] Bu, doğrudan istenen arabirim türüne dönüşebilir. [C#] <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> istenen arabirimi almak için yöntemini kullanın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklama altyapısı işlem alanında çalışırken [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ve hata ayıklamakta olan programın kendi işlem alanında çalıştığı durumlarda kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
