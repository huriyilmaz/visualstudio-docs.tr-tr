---
title: -Edit (devenv.exe)
description: Edit devenv komut satırı anahtarını kullanarak var olan bir dosya örneğinde belirtilen dosyayı açmayı Visual Studio.
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
ms.openlocfilehash: edbe1d0893e4f9b411f072aecea986646a4b105e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625875"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Belirtilen dosyayı mevcut bir Visual Studio.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *Dosya1*

  İsteğe bağlı. Mevcut bir dosya örneğinde açılacak dosya Visual Studio. Hiç örnek Visual Studio, basitleştirilmiş bir pencere düzeniyle yeni bir örnek oluşturulur ve araç yeni örnekte *Dosya1'i* açar.

- *DosyaN*

  İsteğe bağlı. Dosyanın mevcut örneğinde açılması için bir veya daha fazla Visual Studio.

## <a name="remarks"></a>Açıklamalar

Bir dosya belirtilmediğında, mevcut bir Visual Studio odağı alır. Hiçbir dosya belirtilmezse ve herhangi bir Visual Studio yoksa, araç basitleştirilmiş pencere düzenine sahip bir örnek oluşturur.

Mevcut Visual Studio kalıcı durumda ise, dosya, kalıcı durumdan Visual Studio mevcut örnekte açılır. Örneğin, Seçenekler iletişim kutusu açık [olduğunda bu durum](../../ide/reference/options-dialog-box-visual-studio.md) oluşabilir.

Birden fazla Visual Studio örneği açıksa, dosya en son açılan örnekte açılır.

## <a name="example"></a>Örnek

İlk örnek, dosyayı `MyFile.cs` dosyanın mevcut bir örneğinde Visual Studio. Bir Visual Studio örneği yoksa, araç dosyayı yeni bir örnekte açar. İkinci örnek benzerdir ancak yalnızca bir dosya yerine üç dosya açar.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
