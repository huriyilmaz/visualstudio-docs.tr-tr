---
title: SccBackgroundGet Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 118d8458fd9581a87baea08452d0011d4d66c9a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64797057"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, belirtilen dosyaların her birini Kullanıcı etkileşimi olmadan kaynak denetiminden alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pContext  
 'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.  
  
 Nkarşıya  
 'ndaki Dizide belirtilen dosya sayısı `lpFileNames` .  
  
 lpDosyaAdı  
 [in, out] Alınacak dosyaların adları dizisi.  
  
> [!NOTE]
> Adların tam yerel dosya adları olması gerekir.  
  
 dwFlags  
 'ndaki Komut bayrakları ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).  
  
 dwBackgroundOperationID  
 'ndaki Bu işlemle ilişkili benzersiz bir değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|İşlem başarıyla tamamlandı.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Bir arka plan alımı zaten devam ediyor (kaynak denetimi eklentisi bunu yalnızca eşzamanlı Batch işlemlerini desteklemiyorsa döndürmelidir).|  
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev her zaman, kaynak denetimi eklentisini yükleyen bilgisayardan farklı bir iş parçacığında çağrılır. Bu işlevin, tamamlanana kadar dönmesi beklenmez; Ancak, hepsi aynı anda birden çok dosya listesiyle birden çok kez çağrılabilir.  
  
 `dwFlags`Bağımsız değişkeninin kullanımı [SccGet](../extensibility/sccget-function.md)ile aynıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)
