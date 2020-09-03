---
title: Proje komutunu aç | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99596442f3aef9e4cb2d890438d29b96cdf4f083
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671916"
---
# <a name="open-project-command"></a>Proje Aç Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mevcut bir projeyi açar.

## <a name="syntax"></a>Söz dizimi

```
File.OpenProject filename
```

## <a name="arguments"></a>Bağımsız değişkenler
 `filename` Gerekli. Açılacak projenin tam yolu ve dosya adı.

 Bağımsız değişkeninin sözdizimi, `filename` boşluk içeren yolların tırnak işaretleri kullanmasını gerektirir.

## <a name="remarks"></a>Açıklamalar
 Otomatik tamamlama, yazarken doğru yolu ve dosya adını bulmaya çalışır.

 Hata ayıklanırken bu komut kullanılamaz.

## <a name="example"></a>Örnek
 Bu örnek [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , test1 projesini açar.

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
