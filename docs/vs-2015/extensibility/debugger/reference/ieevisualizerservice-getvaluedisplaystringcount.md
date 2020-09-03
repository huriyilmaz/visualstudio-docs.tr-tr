---
title: 'IEEVisualizerService:: GetValueDisplayStringCount | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6785be367430443f92a9cc54a2d636582053228e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192104"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Belirtilen özellik veya alan için görüntülenecek değer dizelerinin sayısını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```csharp  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `displayKind`  
 'ndaki [Displaykind](../../../extensibility/debugger/reference/displaykind.md) numaralandırmasındaki değer.  
  
 `propertyOrField`  
 'ndaki Bir özelliği veya alanı temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimi.  
  
 `pcelt`  
 dışı Görüntülenecek değer dizelerinin sayısını döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
