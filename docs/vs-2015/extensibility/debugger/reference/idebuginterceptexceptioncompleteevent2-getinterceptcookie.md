---
title: 'IDebugInterceptExceptionCompleteEvent2:: Getyakatcookie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e186419a102bdf48a437002ab03120587d6e0822
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180649"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Yakalanamayan bir özel durum işlenirken çağırılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetInterceptCookie(  
   UINT64* pqwCookie  
);  
```  
  
```csharp  
int GetInterceptCookie(  
   out ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pqwCookie`  
 dışı Yakalanamayan özel durumla ilişkili benzersiz değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 [Yakatcurrentexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) yöntemi, ele geçirilebilecek bir özel durumun işlenmesini tamamladıktan sonra, [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) olayını gönderir. İşleyici `GetInterceptCookie` yöntemini özel durumla ilişkili benzersiz değeri almak için kullanabilir (yönteme geçirilen değer aynı değer `InterceptCurrentException` ).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
