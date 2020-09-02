---
title: 'IDebugPortSupplier3:: CanPersistPorts | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: edc989771b41cc4a5cc5b4710de4cbb5632873e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188189"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, bağlantı noktası üreticisinin hata ayıklayıcıyı etkinleştirmeleri arasında bağlantı noktalarını (diske yazarak) kalıcı yapıp yapamayacağını belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yok.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` bağlantı noktaları kalıcı hale gelebilir veya `S_FALSE` bağlantı noktalarının kalıcı olarak olmadığını belirtmek için.  
  
## <a name="remarks"></a>Açıklamalar  
 Bağlantı noktası tedarikçisi bağlantı noktalarını kalıcı hale getirebilse, bu, yok edildiğinde bunu yapması gerekir ve bir kez daha sonra yeniden yüklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
