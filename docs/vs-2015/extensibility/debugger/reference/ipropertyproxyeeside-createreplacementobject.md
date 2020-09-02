---
title: 'IPropertyProxyEESide:: CreateReplacementObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3a21e640d6661f8066609bdc344299ccbd63d52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147502"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

İfade değerlendirici (EE) öğesine özel bir veri nesnesinin kopyasını oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dataIn`  
 'ndaki Kopyalanacak verileri tutan bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi.  
  
 `dataOut`  
 dışı Yeni bir `IEEDataStorage` nesne döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yönteme, bir bayt dizisini temsil eden bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi verilir. Bu gelen veri nesnesi genellikle EE tarafından uygulanmaz. Ancak, bu yöntemin döndürdüğü nesne her zaman EE tarafından uygulanır. Bu, her zaman her `IEEDataStorage` türlü sınıfa arayüzün uygulanmasını sağlar.  
  
 Gelen nesne tarafından sağlanan verilerin `IEEDataStorage` giden nesnedeki verilerle aynı olması gerektiğini unutmayın `IEEDataStorage` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
