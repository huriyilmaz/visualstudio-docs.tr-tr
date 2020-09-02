---
title: 'IDebugMessageEvent2:: GetMessage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14eb540962db3a806273d5c76facb7f9bf25dee7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685891"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Görüntülenecek iletiyi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetMessage(   
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrMessage,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetMessage(   
   out enum_MESSAGETYPE pMessageType,  
   out string           pbstrMessage,  
   out uint             pdwType,  
   out string           pbstrHelpFileName,  
   out uint             dwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pMessageType`  
 dışı İleti türünü açıklayan [MessageType](../../../extensibility/debugger/reference/messagetype.md) numaralandırmasından bir değer döndürür.  
  
 `pbstrMessage`  
 dışı İletiyi döndürür.  
  
 `pdwType`  
 dışı Win32 işlevinin kurallarını kullanarak iletinin türünü döndürür `MessageBox` . Ayrıntılar için bkz. [AfxMessageBox](https://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) işlevi.  
  
 `pbstrHelpFileName`  
 [in, out] Yardım dosyası adını döndürür. Yardım dosyası yoksa null (C++) veya boş (C#) değeri olabilir.  
  
 `pdwHelpId`  
 [in, out] Yardım tanımlayıcısını döndürür. Bu iletiyle ilişkili bir yardım yoksa 0 olabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](https://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8)
