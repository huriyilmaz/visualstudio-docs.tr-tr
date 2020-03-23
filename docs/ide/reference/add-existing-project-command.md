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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595884"
---
# <a name="add-existing-project-command"></a>Varolan Projeyi Ekle Komutu
Geçerli çözüme varolan bir proje ekler.

## <a name="syntax"></a>Sözdizimi

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Bağımsız Değişkenler
`filename`\
İsteğe bağlı. Tam yol ve proje adı, uzantısı ile, projenin çözümeklemek için.

`filename` Bağımsız değişken boşluklar içeriyorsa, tırnak işaretleriyle eklenmelidir.

Dosya adı belirtilmemişse, kullanıcının bir proje seçebilmeleri için komut dosya iletişim kutusunu açar.

## <a name="remarks"></a>Açıklamalar
Otomatik tamamlama, siz yazarken doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
Bu örnek, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projeyi, TestProject1'i geçerli çözüme ekler.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
