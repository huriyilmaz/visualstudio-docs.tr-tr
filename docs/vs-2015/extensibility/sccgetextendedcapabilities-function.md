---
title: Sccgebir Dedcapabilities Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f02591eac6a3f69ae5513aa9dc0abed381cd1c8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200105"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, kaynak denetimi eklentisi tarafından desteklenen ek özellikleri döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pContext  
 'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.  
  
 lSccExCaps  
 'ndaki Test edilecek genişletilmiş bir özellik belirten bayrak (olası bayraklar için [yetenek bayraklarıyla](../extensibility/capability-flags.md) genişletilmiş yetenek kodu tablosuna bakın).  
  
 PBX destekleniyor  
 dışı `TRUE`Belirtilen yetenek destekleniyorsa sıfır olmayan () döndürür; Aksi takdirde, sıfır ( `FALSE` ) döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Özellik al işlemi başarıyla tamamlandı.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Bilinmeyen veya belirtilmeyen bir hata oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem isteğe bağlı olarak çağrılır; diğer bir deyişle, bir özelliğin test olması gerektiğinde, bu özelliğin desteklenip desteklenmediğini tespit etmek için bu yöntem çağrılır. Tek seferde yalnızca bir bayrak belirtildi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [Hata kodları](../extensibility/error-codes.md)   
 [Özellik Bayrakları](../extensibility/capability-flags.md)
