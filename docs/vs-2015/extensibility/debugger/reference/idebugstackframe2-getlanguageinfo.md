---
title: 'IDebugStackFrame2:: GetLanguageInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d370670ed86ee3484243fe5dc7cfdd8ea64be084
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153135"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yığın çerçevesiyle ilişkili dili alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetLanguageInfo (   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo (   
   ref string pbstrLanguage,  
   ref Guid   pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstrLanguage`  
 dışı Bu yığın çerçevesiyle ilişkili yöntemi uygulayan dilin adını döndürür.  
  
 `pguidLanguage`  
 dışı `GUID` Dilin konumunu döndürür. Diller için, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Örneğin, aşağıdakiler döndürülebilir:  
  
- `guidVBScriptLang`  
  
- `guidJScriptLang`  
  
- `guidCPPLang`  
  
- `guidVBLang`  
  
- `guidSQLLang`  
  
- `guidScriptLang`  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
