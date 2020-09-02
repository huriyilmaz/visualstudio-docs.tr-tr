---
title: 'IDebugProcess2:: EnumThreads | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e9b6447827baa80da2843c992a8d2233dd1a4b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188027"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

İşlemde çalışan tüm iş parçacıklarının bir listesini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppEnum`  
 dışı İşlemdeki tüm programlardaki tüm iş parçacıklarının listesini içeren bir [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, her bir programda çalışan iş parçacıklarını numaralandırır ve ardından bunları iş parçacıklarının işlem görünümünde birleştirir. Tek bir iş parçacığı birden çok programda çalıştırılabilir; Bu yöntem, iş parçacığını yalnızca bir kez numaralandırır.  
  
 Bu yöntem, işlemin iş parçacıklarının bir listesini yinelemeler olmadan gösterir. Aksi takdirde, belirli bir programda çalışan iş parçacıklarını numaralandırmak için [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) yöntemini kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
