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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed8ec8e7f990a4a2c5d943a15a105faa5ab23572
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589389"
---
# <a name="symbol-path-command"></a>Sembol Yolu Komutu
Hata ayıklayıcının simge araması dizinler listesini ayarlar.

## <a name="syntax"></a>Sözdizimi

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Arguments
`pathname`

İsteğe bağlı. Hata ayıklayıcının simge araması için bir noktalı virgülle ayrılmış yol listesi.

## <a name="remarks"></a>Açıklamalar
`pathname` belirtilmemişse, komut geçerli sembol yollarını listeler.

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
