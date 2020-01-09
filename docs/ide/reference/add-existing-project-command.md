---
title: Varolan Projeyi Ekle Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 008802546d87bd44137c6d13ee2aef802877e308
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595884"
---
# <a name="add-existing-project-command"></a>Varolan Projeyi Ekle Komutu
Mevcut bir projeyi çözüme ekler.

## <a name="syntax"></a>Sözdizimi

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Arguments
`filename`\
İsteğe bağlı. Çözüme eklenecek projenin Uzantısı ile tam yol ve proje adı.

`filename` bağımsız değişkeni boşluk içeriyorsa, tırnak işaretleri içine alınmalıdır.

Dosya adı belirtilmemişse, komut, kullanıcının bir proje seçmesini sağlamak için dosya iletişim kutusunu açar.

## <a name="remarks"></a>Açıklamalar
Otomatik tamamlama, yazarken doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
Bu örnek, TestProject1 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projesini geçerli çözüme ekler.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
