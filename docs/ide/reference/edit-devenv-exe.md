---
title: -Edit (devenv.exe)
description: Varolan bir Visual Studio örneğinde belirtilen bir dosyayı açmak için Düzenle Devenv komut satırı anahtarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 20f490d5d8178dbc254a7ad2be4a8f7e83979e22e5ea232df5357ce6bc67db24
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357485"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Belirtilen dosyayı varolan bir Visual Studio örneğinde açar.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *FILE1*

  İsteğe bağlı. Visual Studio var olan bir örneğinde açılacak dosya. Visual Studio bir örneği yoksa, basitleştirilmiş bir pencere düzeniyle yeni bir örnek oluşturulur ve araç yeni örnekte *fıle1* öğesini açar.

- *Dosyan*

  İsteğe bağlı. Mevcut Visual Studio örneğinde açmak için bir veya daha fazla ek dosya.

## <a name="remarks"></a>Açıklamalar

bir dosya belirtilmediğinde, var olan bir Visual Studio örneği odağı alır. hiçbir dosya belirtilmemişse ve bir Visual Studio örneği yoksa, araç basitleştirilmiş pencere düzenine sahip bir örnek oluşturur.

mevcut Visual Studio örneği kalıcı durumdaysa, Visual Studio kalıcı durumdan çıktığında dosya mevcut örnekte açılır. Örneğin, [Seçenekler iletişim kutusu](../../ide/reference/options-dialog-box-visual-studio.md) açık olduğunda bu durum oluşabilir.

Visual Studio birden fazla örneği açıksa, dosya en son açılan örnekte açılır.

## <a name="example"></a>Örnek

İlk örnek dosyayı `MyFile.cs` mevcut bir Visual Studio örneğinde açar. bir Visual Studio örneği yoksa, araç dosyayı yeni bir örnekte açar. İkinci örnek, tek bir dosya yerine üç dosya açılmasının dışında benzerdir.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
