---
title: 'IDiaSession:: Findınlineelinesbyaddr | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b35850367ef4bcc4e49cc3d6e76b41a2e9f4cd7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151700"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir istemcinin, belirtilen ana sembolüyle doğrudan veya dolaylı olarak satır numarası bilgilerini, belirtilen üst simgeye göre veya belirtilen adres aralığında bulundurarak yinelemesinden izin veren bir sabit listesi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `parent`  
 'ndaki `IDiaSymbol` Üst öğeyi temsil eden nesne.  
  
 `isect`  
 'ndaki Adresin bölüm bileşenini belirtir.  
  
 `offset`  
 'ndaki Adresin konum bileşenini belirtir.  
  
 `length`  
 'ndaki Bu sorguyla birlikte kapsamak üzere adres aralığını bayt cinsinden belirtir.  
  
 `ppResult`  
 dışı `IDiaEnumLineNumbers` Alınan satır numaralarının listesini içeren bir nesnesi tutar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum numaralandırması](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
