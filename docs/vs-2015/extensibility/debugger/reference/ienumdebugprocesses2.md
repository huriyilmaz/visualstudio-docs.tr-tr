---
title: IEnumDebugProcesses2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d56d284d08a1c6b55318300ef7e1db1e385d584e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178418"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, hata ayıklama bağlantı noktası üzerinde çalışan işlemi numaralandırır.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Özel bir bağlantı noktası sağlayıcısı, bir bağlantı noktasında çalışan işlemlerin listesini sağlamak için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Visual Studio bu arabirimi edinmek için [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) çağırır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugProcesses2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Bir numaralandırma dizisindeki belirtilen sayıda işlemi alır.|  
|[Atla](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Sabit Listesi dizisinde belirtilen sayıda işlemi atlar.|  
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|  
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Bir Numaralandırıcı içindeki işlem sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio, **işlem** penceresini doldurmak için bu arabirimi kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
