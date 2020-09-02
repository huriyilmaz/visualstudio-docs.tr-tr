---
title: Sembol yolu komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d02d4cfede6ed3499d09ff58e4454c1ef9cbe0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651011"
---
# <a name="symbol-path-command"></a>Sembol Yolu Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklayıcının simge araması için dizinlerin listesini ayarlar.

## <a name="syntax"></a>Söz dizimi

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Bağımsız değişkenler
 `pathname` Seçim. Hata ayıklayıcının simge araması için bir noktalı virgülle ayrılmış yol listesi.

## <a name="remarks"></a>Açıklamalar
 Hayır `pathname` belirtilmemişse, komut geçerli sembol yollarını listeler.

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

## <a name="see-also"></a>Ayrıca Bkz.
 [Komut penceresi](../../ide/reference/command-window.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
