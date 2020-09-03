---
title: Çözüm komutunu aç | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9c9ab66d2885137e9c470f577996ab861b554d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671904"
---
# <a name="open-solution-command"></a>Çözümü Aç Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mevcut bir çözümü açar ve diğer açık çözümleri kapatıyor.

## <a name="syntax"></a>Söz dizimi

```
File.OpenSolution filename
```

## <a name="arguments"></a>Bağımsız değişkenler
 `Filename` Gerekli. Açılacak çözümün tam yolu ve dosya adı.

 Bağımsız değişkeninin sözdizimi, `filename` boşluk içeren yolların tırnak işaretleri kullanmasını gerektirir.

## <a name="remarks"></a>Açıklamalar
 Otomatik tamamlama, yazarken doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
 Bu örnek, test1. sln çözümünü açar.

```
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
