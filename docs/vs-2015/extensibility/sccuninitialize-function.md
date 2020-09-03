---
title: Sccunınitialize Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcb0b3a6718cc90db6f7176c823ccccbbfc05f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190843"
---
# <a name="sccuninitialize-function"></a>SccUninitialize İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, kaynak denetimi eklentisinin kapanmasından dolayı bir önceki [SccInitialize](../extensibility/sccinitialize-function.md) çağrısıyla oluşturulan tüm ayırmaları veya açık bağlantıları temizler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 'ndaki [SccInitialize](../extensibility/sccinitialize-function.md)içinde oluşturulan kaynak denetimi eklentisi bağlam yapısına yönelik işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Temizleme işlemi başarıyla tamamlandı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak denetimi eklentisi kapanmaya hazırlanmaktan ve eklentinin bağlam yapısına ayrılan bellek boşaltmasından sorumludur. Bu işlev, bir eklentinin verilen her örneği için bir kez çağrılır. [SccInitialize](../extensibility/sccinitialize-function.md) çağrısı bu çağrıdan önce gelir. Çağrısı sırasında hiç proje hala açık olamaz `SccUninitialize` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
