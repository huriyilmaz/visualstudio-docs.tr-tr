---
description: Sanal temel tablo işaretçisinin türünü alır.
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6a254663eab843e35e733f1c380f93c2a33ebc74
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635366"
---
# <a name="idiasymbolget_virtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Sanal temel tablo işaretçisinin türünü alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|`pRetVal`|[out] Temel [tablonun türünü belirten bir IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.|

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Sanal temel tablo işaretçisi ( ), sanal temel sınıflardan devralmayı ele alan `vbtptr` [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] bir sanal tablodaki gizli bir işaretçidir. `vbtptr`devralınan sınıflara bağlı olarak farklı boyutlara sahip olabilir.

 Bu yöntem, vbtptr boyutunu belirlemek için kullanılan bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
