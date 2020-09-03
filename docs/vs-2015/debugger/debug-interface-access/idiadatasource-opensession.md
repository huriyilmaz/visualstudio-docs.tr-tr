---
title: 'IDiaDataSource:: openSession | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bec5507d15374e6e88afd4567d4b0fec9ca6cb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198595"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sembolleri sorgulamak için bir oturum açar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 ppSession  
 dışı Açık oturumu temsil eden bir [IDiaSession](../../debugger/debug-interface-access/idiasession.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda bu yöntem için olası dönüş değerleri gösterilmektedir.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) nesnesi daha önce bir sembol kaynağı ile başlatılmamış.|  
|E_INVALIDARG|Geçersiz `ppSession` parametre.|  
|E_OUTOFMEMORY|Oturumu açmak için yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem bir veri kaynağı için bir [IDiaSession](../../debugger/debug-interface-access/idiasession.md) nesnesi açar.  
  
 `IDiaSession` nesneler veri kaynağına sorguları uygular. Bir oturum, her hata ayıklama sembolleri kümesi için bir adres alanını yönetir. Veri kaynağı sembolleri tarafından tanımlanan. exe veya. dll dosyası birden çok adres aralığında etkin ise (örneğin, birden çok işlem yüklendiği için), her bir adres aralığı için bir oturum kullanılmalıdır.  
  
## <a name="example"></a>Örnek  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Bakýþ](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [.Pdb Dosyasını Sorgulama](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
