---
title: Sembol Yolu Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a2e4c789f4bd2637cd4da79d66071cc94d697f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748606"
---
# <a name="symbol-path-command"></a>Sembol Yolu Komutu
Hata ayıklayıcının simge araması için dizinlerin listesini ayarlar.

## <a name="syntax"></a>Sözdizimi

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Arguments
`pathname`

İsteğe bağlı. Hata ayıklayıcının simge araması için bir noktalı virgülle ayrılmış yol listesi.

## <a name="remarks"></a>Açıklamalar
@No__t_0 belirtilmemişse, komut geçerli sembol yollarını listeler.

## <a name="example"></a>Örnek
Bu örnek, sembol dizinleri listesine iki yol ekler.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Örnek
Bu örnek, geçerli sembol yollarının noktalı virgülle ayrılmış bir listesini görüntüler.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Ayrıca bkz.

- [Komut Penceresi](../../ide/reference/command-window.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)