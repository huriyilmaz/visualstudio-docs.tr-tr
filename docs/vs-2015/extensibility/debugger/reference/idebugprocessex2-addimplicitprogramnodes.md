---
title: 'IDebugProcessEx2:: Admplicitprogramnodes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: faca728144bde572d8a1d3424fbfcf908403d679
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202826"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, belirtilen her hata ayıklama altyapısı (DE) için bir program düğümü ekler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `guidLaunchingEngine`  
 'ndaki `GUID` Programları başlatmak için kullanılacak olan BIR de (ve kendi program düğümlerini eklemek için varsayılır).  
  
 `rgguidSpecificEngines`  
 'ndaki `GUID`Program düğümlerinin ekleneceği des dizisi.  
  
 `celtSpecificEngines`  
 'ndaki `GUID`Dizideki s sayısı `rgguidSpecificEngines` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Program [düğümleri](../../../extensibility/debugger/program-nodes.md) `rgguidSpecificEngines` `guidLaunchingEngine` , bir program başlattığında kendi program düğümünü eklemek için belirtilen başlatma altyapısı hariç olmak üzere, ' da listelenen her bir ve ' de listelenirler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Program Düğümleri](../../../extensibility/debugger/program-nodes.md)
