---
title: 'IDebugProgram2:: WriteDump | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 491515d2778c6ad16287739bfc88d8134903d2bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205801"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir dosyaya döküm yazar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `DumpType`  
 'ndaki Döküm türünü belirten [DumpType](../../../extensibility/debugger/reference/dumptype.md) numaralandırmasındaki bir değer (örneğin, kısa veya uzun).  
  
 `pszDumpUrl`  
 'ndaki Döküm yazılacak URL. Genellikle, bu biçimindedir `file://c:\path\filename.ext` , ancak geçerli BIR URL olabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Program dökümü genellikle geçerli yığın çerçevesini, yığının kendisini, programda çalışan iş parçacıklarının bir listesini ve programın sahip olduğu tüm belleği içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
