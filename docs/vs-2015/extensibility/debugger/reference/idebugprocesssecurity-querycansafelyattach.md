---
title: 'Idebugprocesssecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec541b6dc4ccae57628d4b33e7c188008da6edae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187953"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, kullanıcının güvenli olmayan bir işleme iliştirmadan önce bağlantı noktası sağlayıcısı 'nın bir uyarı görüntülemesine olanak tanır.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Dönüş değerleri aşağıdaki gibidir:  
  
- `S_OK`: İşleme ekleme güvenlidir ve hiçbir uyarı iletişim kutusu gösterilmez.  
  
- `S_FALSE`: Ekleme bir güvenlik sorunu ve uyarı içeren bir iletişim kutusu gösterilir.  
  
- `FAILURE`: İşleme ekleme başarısız oluyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
