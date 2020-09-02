---
title: 'IDebugEngine3:: LoadSymbols | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29f8af5e258da923ec814e0a224dcf87cbbfae9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195939"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu hata ayıklama altyapısı tarafından hata ayıklamakta olan tüm modüller için (gerektiğinde) semboller yükler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yok.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu hata ayıklama altyapısı tarafından başvurulan tüm modüller için hata ayıklama sembolleri yükler. Semboller yalnızca henüz yüklenmediyse yüklenir. Simgeler [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)çağrısıyla ayarlanan yollarda aranır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
