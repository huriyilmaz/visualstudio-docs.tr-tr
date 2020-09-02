---
title: 'IDebugProgram2:: Terminate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4673259e4a8ca0d4354037efbc35b63bedfcbc96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146341"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Programı sonlandırır.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Mümkünse, program sonlandırılır ve işlemden kaldırılır; Aksi takdirde, hata ayıklama altyapısı (DE) gerekli temizleme işlemlerini gerçekleştirir.  
  
 Bu yöntem veya [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) yöntemi IDE tarafından, genellikle kullanıcıya yanıt olarak tüm hata ayıklamayı durdurma olarak çağrılır. Bu yöntemin uygulanması ideal olarak programı işlem içinde sonlandıracaktır. Bu mümkün değilse, DE programın bu işlemde daha fazla çalışma yapmasını (ve gerekli temizleme işlemlerini yapmasını) önlemesi gerekir. `IDebugProcess2::Terminate`YÖNTEMI IDE tarafından çağrıldıysa, Yöntem çağrıldıktan sonra işlemin tamamının sonlandırılması gerekir `IDebugProgram2::Terminate` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
