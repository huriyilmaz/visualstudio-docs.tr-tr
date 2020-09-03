---
title: 'IDebugSettingsCallback2:: Trmees | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cca998c4cdae8cc5e543a24a5cdfe18369e51b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155219"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Dil ve satıcı tanımlayıcıları verilen kullanılabilir ifade değerlendiricileri numaralandırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT EnumEEs(  
   DWORD  celtBuffer,  
   GUID*  rgguidLang,  
   GUID*  rgguidVendor,  
   DWORD* pceltEEs  
);  
```  
  
```csharp  
public int EnumEEs(  
   uint       celtBuffer,  
   ref Guid   rgguidLang,  
   ref Guid   rgguidVendor,  
   ref uint[] pceltEEs  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celtBuffer`  
 'ndaki Arabellekteki öğe sayısı `pceltEEs` .  
  
 `rgguidLang`  
 [in, out] Programlama dili için benzersiz tanımlayıcı.  
  
 `rgguidVendor`  
 [in, out] Satıcı için benzersiz tanımlayıcı.  
  
 `pceltEEs`  
 [in, out] Değerlendiricileri ifadesinin dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
