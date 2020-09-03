---
title: 'IDebugBoundBreakpoint2:: SetCondition | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8ac19bfe2109d7885265342ccc5ef4d358727d49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156203"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu ilişkili kesme noktasıyla ilişkili koşulu ayarlar veya değiştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bpCondition`  
 'ndaki Koşulu açıklayan [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Numaralandırmadaki bir değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. , `E_BP_DELETED` Bağlantılı kesme noktası nesnesinin durumunun `BPS_DELETED` ( [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) sabit listesinin parçası) olarak ayarlanmış olup olmadığını döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Daha önce bu kesme noktasıyla ilişkilendirilmiş olan herhangi bir koşul kaybolur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
