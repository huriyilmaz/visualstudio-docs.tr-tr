---
title: Idebugportpicker::D ıplayportpicker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dd9317a73800a3886a5a807e9e28b0c24b2301c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188372"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kullanıcının bir bağlantı noktası seçmesini sağlayan, belirtilen iletişim kutusunu görüntüler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `hwndParentDialog`  
 'ndaki Üst iletişim kutusu için tanıtıcı.  
  
 `pbstrPortId`  
 dışı Bağlantı noktası tanımlayıcı dizesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Dönüş değeri `S_FALSE` (veya `S_OK` `BSTR` olarak ayarlandığı küme `NULL` ), kullanıcının **iptal 'e**tıkladığını gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
