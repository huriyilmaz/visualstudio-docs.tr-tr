---
title: SccCloseProject Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d2364215f528f16d05ecf0c53b152f7334f4b4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156143"
---
# <a name="scccloseproject-function"></a>SccCloseProject İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, belirli bir oturumun sonuna işaret eden bir projeyi kapatır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 Kaynak denetimi eklentisi bağlam yapısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Proje başarıyla kapatıldı.|  
|SCC_E_PROJNOTOPEN|Şu anda açık proje yok.|  
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|  
|SCC_E_NONSPECIFICERROR|Özel olmayan hata.|  
  
## <a name="remarks"></a>Açıklamalar  
 [SccOpenProject](../extensibility/sccopenproject-function.md) her zaman bu işlevden önce çağırılır. Daha sonra bu işleve yapılan bir çağrı, sonra, `SccOpenProject` kaynak denetim sistemine olan bağlantıyı tamamen sonlandıran işlev veya [Sccunınitialize](../extensibility/sccuninitialize-function.md)çağrısı tarafından izlenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
