---
title: 'Ihata ayıklama Garrayfield:: GetRank | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d0396718482c9ce90527155a3612160612f66d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198727"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Dizinin boyutunu veya boyut sayısını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwRank`  
 dışı Dereceyi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dizinin sıralaması, boyut sayısına karşılık gelir. C++ ve C# ' de, çok boyutlu diziler gerçekten dizi dizilerdir ve bu nedenle yalnızca bir boyutlu dizi olarak kabul edilebilir (ve `GetRank` yöntemi her zaman 1 ' i döndürür). ' De, [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] diğer yandan çok boyutlu diziler farklı şekilde işlenir ve böyle bir dizinin sıralaması boyut sayısını yansıtır (ve `GetRank` Yöntem her zaman boyut sayısını döndürür).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
