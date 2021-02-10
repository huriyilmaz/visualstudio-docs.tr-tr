---
title: Sembol Yolu Komutu
description: Sembol yolu komutu ve hata ayıklayıcı için sembolleri aramak üzere dizin listesini nasıl ayarlacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 72e69300e9dc621ea346c05923168c33bc7065c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967169"
---
# <a name="symbol-path-command"></a>Sembol Yolu Komutu
Hata ayıklayıcının simge araması için dizinlerin listesini ayarlar.

## <a name="syntax"></a>Söz dizimi

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Bağımsız değişkenler
`pathname`

İsteğe bağlı. Hata ayıklayıcının simge araması için bir noktalı virgülle ayrılmış yol listesi.

## <a name="remarks"></a>Açıklamalar
Hayır `pathname` belirtilmemişse, komut geçerli sembol yollarını listeler.

## <a name="example-1"></a>Örnek 1
Bu örnek, sembol dizinleri listesine iki yol ekler.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example-2"></a>Örnek 2
Bu örnek, geçerli sembol yollarının noktalı virgülle ayrılmış bir listesini görüntüler.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Ayrıca bkz.

- [Komut penceresi](../../ide/reference/command-window.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
