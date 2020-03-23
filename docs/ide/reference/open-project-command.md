---
title: Proje Aç komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97c1034fbbafa04af2d62526fdbb48812d64e050
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565818"
---
# <a name="open-project-command"></a>Proje komutunu aç

Varolan bir projeyi veya çözümü açar.

## <a name="syntax"></a>Sözdizimi

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Bağımsız Değişkenler

`filename`

Gereklidir. Projenin veya çözümün tam yol ve dosya adı açılır.

> [!NOTE]
> Bağımsız değişkenin `filename` sözdizimi, boşluk içeren yolların tırnak işaretleri kullanmasını gerektirir.

## <a name="remarks"></a>Açıklamalar

Otomatik tamamlama, siz yazarken doğru yolu ve dosya adını bulmaya çalışır.

Hata ayıklama sırasında bu komut kullanılamaz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, Visual Basic proje **Test1'i**açar:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/Komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
