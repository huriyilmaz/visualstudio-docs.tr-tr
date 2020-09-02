---
title: 'IDebugProperty2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a94e3767ee05e39e847af27dc5999fa8bbbe2d44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193444"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu özelliğin değerini belirtilen başvurunun değerine ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `rgpArgs`  
 'ndaki Yönetilen kod özellik ayarlayıcısına geçirilecek bağımsız değişken dizisi. Özellik ayarlayıcısı bağımsız değişkenler almaz veya bu [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi bu tür bir özellik ayarlayıcısına başvurmadığından, `rgpArgs` null bir değer olmalıdır. Bu parametre genellikle null bir değerdir.  
  
 `dwArgCount`  
 'ndaki Dizideki bağımsız değişkenlerin sayısı `rgpArgs` .  
  
 `pValue`  
 'ndaki Bu özelliği ayarlamak için kullanılacak değere, bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi biçiminde bir başvuru.  
  
 `dwTimeout`  
 'ndaki Değeri, milisaniye cinsinden ayarlamak için ne kadar sürer. Tipik bir değer `INFINITE` . Bu, olası değerlendirmenin süredeki süreyi etkiler.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, genellikle aşağıdakilerden biri bir hata kodu döndürür:  
  
|Hata|Açıklama|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Değerin bir başvurudan ayarlanması desteklenmez.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Bu özellik bir yönteme başvurduğundan değer ayarlanamaz.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Değer salt okunurdur ve ayarlanamaz.|  
|`E_NOTIMPL`|Yöntem uygulanmadı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
