---
title: SccGetUserOption Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd00a2b669b806b09a6ae221b2ba2e03f8d45ceb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200078"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, kullanıcıya özgü çeşitli seçenekleri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pContext  
 'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.  
  
 nOption  
 'ndaki Alma seçeneği (olası seçeneklere yönelik açıklamalar bölümüne bakın).  
  
 lpVal  
 dışı Seçenekle ilişkili değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Seçenek başarıyla alındı.|  
|SCC_E_OPNOTSUPPORTED|Seçenek desteklenmiyor.|  
|SCC_E_NONSPECIFICERROR|Belirtilmeyen bir hata oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki seçenekler bu komut tarafından desteklenir:  
  
|Kullanıcı seçeneği|Açıklama|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Kullanıcının dosyaların yerel sürümünü kullanıma almak isteyip istemediğini belirler. `lpVal` atandı `SCC_USEROPT_COLV_YES` (Kullanıcı yerel dosyaları kullanıma almak istiyor) veya `SCC_USEROPT_COLV_NO` .|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [Hata Kodları](../extensibility/error-codes.md)
