---
title: Sembol Yolu Komutu
description: Sembol Yolu komutunu ve hata ayıklayıcının sembol araması için dizin listesini nasıl ayarlayıcısı olduğunu öğrenin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 67e13204ae754375d5844c04cf783e6a7fa4ebb1ae7ce739254f85686e6e08f9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121289081"
---
# <a name="symbol-path-command"></a>Sembol Yolu Komutu
Hata ayıklayıcısının sembol araması için dizin listesini ayarlar.

## <a name="syntax"></a>Söz dizimi

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Bağımsız değişkenler
`pathname`

İsteğe bağlı. Hata ayıklayıcının sembol araması için noktalı virgülle ayrılmış yol listesi.

## <a name="remarks"></a>Açıklamalar
`pathname`belirtilmezse, komut geçerli sembol yollarını listeler.

## <a name="example-1"></a>Örnek 1
Bu örnek, sembol dizinleri listesine iki yol ekler.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example-2"></a>Örnek 2
Bu örnekte geçerli sembol yollarının noktalı virgülle ayrılmış listesi görüntülenir.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Ayrıca bkz.

- [Komut Penceresi](../../ide/reference/command-window.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
