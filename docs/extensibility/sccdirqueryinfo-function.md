---
description: Bu işlev, geçerli durumları için tam dizinlerin listesini inceler.
title: SccDirQueryInfo Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 81087d4f4da3435fb7bc80ec4a965394c7d6c7f3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060334"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo işlevi
Bu işlev, geçerli durumları için tam dizinlerin listesini inceler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Parametreler
 pContext

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 nDirs

'ndaki Sorgulanmasını seçtiğiniz dizinlerin sayısı.

 lpDirNames

'ndaki Sorgulanacak dizinlerin tam nitelikli yolları dizisi.

 lpStatus

[in, out] Kaynak denetimi eklentisinin durum bayraklarını döndürmesi için bir dizi yapısı (Ayrıntılar için [Dizin durum koduna](../extensibility/directory-status-code-enumerator.md) bakın).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Sorgu başarılı oldu.|
|SCC_E_OPNOTSUPPORTED|Kaynak kodu denetim sistemi bu işlemi desteklemiyor.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 İşlevi, döndürülen diziyi aileden bit bit maskesi `SCC_DIRSTATUS` (bkz. [Dizin durum kodu](../extensibility/directory-status-code-enumerator.md)), verilen her dizin için bir giriş ile doldurur. Durum dizisi, çağıran tarafından ayrılır.

 Bu işlev, bir dizin yeniden adlandırılmadan önce, kaynağın karşılık gelen bir proje olup olmadığını sorgulayarak kaynak denetimi altında olup olmadığını denetlemek için kullanılır. Dizin, kaynak denetimi altında değilse, IDE kullanıcıya uygun bir uyarı verebilir.

> [!NOTE]
> Bir kaynak denetimi eklentisi bir veya daha fazla durum değeri uygulamamı seçerse, uygulanmayan bitler sıfır olarak ayarlanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Dizin durum kodu](../extensibility/directory-status-code-enumerator.md)
