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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd6aca05758185f4df47688044f479b7bbe2829e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658812"
---
# <a name="add-existing-project-command"></a>Varolan Projeyi Ekle Komutu
Geçerli çözüme mevcut bir projeyi ekler.

## <a name="syntax"></a>Sözdizimi

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Arguments
`filename`\
İsteğe bağlı. Çözüme eklenecek projenin Uzantısı ile tam yol ve proje adı.

@No__t_0 bağımsız değişkeni boşluk içeriyorsa, tırnak işaretleri içine alınmalıdır.

Dosya adı belirtilmemişse, komut, kullanıcının bir proje seçmesini sağlamak için dosya iletişim kutusunu açar.

## <a name="remarks"></a>Açıklamalar
Otomatik tamamlama, yazarken doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
Bu örnek, TestProject1 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projesini geçerli çözüme ekler.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)