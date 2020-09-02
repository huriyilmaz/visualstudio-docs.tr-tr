---
title: Komutu Başlat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a216e053a08662da5da04206c780fb4455e9ec09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663487"
---
# <a name="start-command"></a>Başlat Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Başlangıç projesinde hata ayıklamaya başlar.

## <a name="syntax"></a>Söz dizimi

```
Debug.Start [address]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `address` Seçim. Kaynak kodundaki bir kesme noktasına benzer şekilde programın yürütmeyi askıya aldığı adres. Bu bağımsız değişken yalnızca hata ayıklama modunda geçerlidir.

## <a name="remarks"></a>Açıklamalar
 Çalıştırıldığında **Başlat** komutu, belirtilen adrese bir RunToCursor işlemi gerçekleştirir.

## <a name="example"></a>Örnek
 Bu örnek, hata ayıklayıcıyı başlatır ve oluşan tüm özel durumları yoksayar.

```
>Debug.Start
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
