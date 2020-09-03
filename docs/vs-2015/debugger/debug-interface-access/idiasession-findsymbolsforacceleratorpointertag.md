---
title: 'IDiaSession:: Findsymbolsforivatorpointertag | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 55e69ae6380faa58d2b63074734cfe3c065759e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196352"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen etiket değerinin üst Hızlandırıcı saplama işlevinde karşılık geldiği değişken için bir sembol numaralandırması döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT findSymbolsForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `parent`  
 'ndaki Aranmak üzere Hızlandırıcı saplama işlevine karşılık gelen bir IDiaSymbol.  
  
 `tagValue`  
 'ndaki İşaretçi etiketi değeri.  
  
 `ppResult`  
 dışı `IDiaEnumSymbols` Sonuçla başlatılan arabirim işaretçisine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
