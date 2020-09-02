---
title: 'IDebugPortRequest2:: GetPortName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: afed0bb700f41f7c39551f1a9bc7779f36b0ae57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188359"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bağlantı noktasının adını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstrPortName`  
 dışı Bağlantı noktasının adını döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) arabirimi genellikle bir bağlantı noktasına bağlantı almak için bir hata ayıklama paketinden (istemci) bir bağlantı noktası sağlayıcısına (sunucu) geçirilir. Hem hata ayıklama paketi hem de bağlantı noktası sağlayıcısı, bağlantı noktası için olası seçimleri algılar. Basit bir dize bağlantı noktasını tanımlıyorsa, `IDebugPortRequest2::GetPortName` yöntemi bağlantı kurmak için yeterli bilgiye sahip olabilir. Aksi takdirde, kullanarak sunucu tarafından elde edilebilir istemci tarafından Ek arabirimler temin edilebilir `IDebugPortRequest2::QueryInterface` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
