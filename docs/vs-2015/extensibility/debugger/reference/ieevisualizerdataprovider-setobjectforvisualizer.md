---
title: 'IEEVisualizerDataProvider:: SetObjectForVisualizer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d20164e31f8c42b7099f99ff34ac120319a2def1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62540285"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, Görselleştirici temsil ettiği nesneyi değiştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pNewObject`  
 'ndaki Ayarlanacak nesne.  
  
 `error`  
 dışı Nesne ayarlanırken bir hata oluşursa, bu dize hata iletisini tutar.  
  
 `pException`  
 dışı Bir hata oluşursa, bu nesne özel durum bilgilerini tutar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu, hata bilgilerinin nasıl döndürüldüğünü belirleme uygulayıcısı 'na sahiptir. Ancak bazı çağıranlar yalnızca bir hata olduğunu anlamak için bir özel durum nesnesinin döndürülüp döndürülmeyeceğini görebilir, bu nedenle bir hata oluşursa bu yöntem her zaman bir özel durum nesnesi döndürmelidir. Çağıran tarafından kullanılması istediği durumlarda hata dizesi de sağlanmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
