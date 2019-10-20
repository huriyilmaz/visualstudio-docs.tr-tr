---
title: Mevcut proje komutunu Ekle | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 73d8e54938659920227b3614046b8a8f933023ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670221"
---
# <a name="add-existing-project-command"></a>Varolan Projeyi Ekle Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Geçerli çözüme mevcut bir projeyi ekler.

## <a name="syntax"></a>Sözdizimi

```
File.AddExistingProject filename
```

## <a name="arguments"></a>Arguments
 Isteğe bağlı `filename`. Çözüme eklenecek projenin Uzantısı ile tam yol ve proje adı.

 @No__t_0 bağımsız değişkeni boşluk içeriyorsa, tırnak işaretleri içine alınmalıdır.

 Dosya adı belirtilmemişse, komut, kullanıcının bir proje seçmesini sağlamak için dosya iletişim kutusunu açar.

## <a name="remarks"></a>Açıklamalar
 Otomatik tamamlama, yazarken doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
 Bu örnek, TestProject1 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projesini geçerli çözüme ekler.

```
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
