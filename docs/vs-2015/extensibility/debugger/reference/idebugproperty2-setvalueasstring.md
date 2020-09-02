---
title: 'IDebugProperty2:: SetValueAsString | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d50057570b5b067447321f975d4d33da8aa3de43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193433"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Belirli bir dizeden bir özelliğin değerini ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszValue`  
 'ndaki Ayarlanacak değeri içeren bir dize.  
  
 `nRadix`  
 'ndaki Herhangi bir sayısal bilgiyi yorumlamak için kullanılan bir taban. Bu, taban x 'i otomatik olarak belirlemeyi denemek için 0 olabilir.  
  
 `dwTimeout`  
 'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süreyi milisaniye olarak belirtir. `INFINITE`Sonsuza kadar beklemek için kullanın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür. Aşağıdaki tabloda olası diğer değerler gösterilmektedir.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Dize bir özellik değerine dönüştürülemedi veya özellik değeri ayarlanamadı.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Özellik salt okunurdur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
