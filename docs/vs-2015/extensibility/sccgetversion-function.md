---
title: SccGetVersion Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4e548f1f2b82a97206cdf41174a8c1c7d61e885
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200053"
---
# <a name="sccgetversion-function"></a>SccGetVersion İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, kaynak denetimi eklentisi tarafından desteklenen kaynak denetimi eklentisi API 'sinin sürüm numarasını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yok.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `LONG`Desteklenen kaynak denetimi EKLENTISI API 'sinin sürüm numarasını içeren bir veri türü:  
  
|WORD|Açıklama|  
|----------|-----------------|  
|HıWORD|Ana sürüm|  
|LOWORD|İkincil sürüm|  
  
## <a name="remarks"></a>Açıklamalar  
 Örneğin, kaynak denetimi eklentisi kaynak denetimi eklentisi API 'sinin 1,3 sürümünü destekliyorsa, bu işlev 0x0103 ' ü döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
