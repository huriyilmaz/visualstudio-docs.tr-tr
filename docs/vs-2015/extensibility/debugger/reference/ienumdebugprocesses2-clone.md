---
title: 'IEnumDebugProcesses2:: Clone | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Clone
helpviewer_keywords:
- IEnumDebugProcesses2::Clone
ms.assetid: 3d4196d3-5a80-4f76-b8b2-f72e80c8d406
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98271c63cd5dc4198bded7bb52eb169651e2e071
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191880"
---
# <a name="ienumdebugprocesses2clone"></a>IEnumDebugProcesses2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Geçerli numaralandırmanın ayrı bir nesne olarak kopyasını döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugProcesses2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugProcesses2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppEnum`  
 dışı Bu numaralandırmanın bir kopyasını ayrı bir nesne olarak döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Numaralandırmanın kopyası, bu yöntemin çağrılışında orijinal ile aynı duruma sahiptir. Bununla birlikte, kopyanın ve özgün durumlarının durumları ayrıdır ve tek tek değiştirilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
