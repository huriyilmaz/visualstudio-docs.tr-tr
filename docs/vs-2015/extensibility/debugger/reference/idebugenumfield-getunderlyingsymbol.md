---
title: 'Ihata ayıklama Genumfield:: GetUnderlyingSymbol | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1841ca2bf9bd5a43ec5a16a515a03769db64ea15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188967"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, numaralandırmanın adını temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetUnderlyingSymbol(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetUnderlyingSymbol(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppField`  
 dışı Bu numaralandırmanın adını açıklayan [IDebugField 'ı](../../../extensibility/debugger/reference/idebugfield.md) döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Numaralandırma adı Ayrıca, [bağlama](../../../extensibility/debugger/reference/idebugbinder-bind.md)kullanarak bir bellek konumuna bağlı olan numaralandırmanın türünü de içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ihata ayıklama Genumalanı](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Bağladığınızda](../../../extensibility/debugger/reference/idebugbinder-bind.md)
