---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d180d5a5d723d8085537f2993aac022d74df2c08
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595702"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Belirtilen dosyayı Visual Studio 'nun mevcut bir örneğinde açar.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Arguments

- *FILE1*

  İsteğe bağlı. Visual Studio 'nun mevcut bir örneğinde açılacak dosya. Visual Studio 'nun bir örneği yoksa, Basitleştirilmiş bir pencere düzeniyle yeni bir örnek oluşturulur ve araç yeni örnekte *FILE1* öğesini açar.

- *Dosyan*

  İsteğe bağlı. Visual Studio 'nun mevcut örneğinde açmak için bir veya daha fazla ek dosya.

## <a name="remarks"></a>Açıklamalar

Bir dosya belirtilmediğinde, var olan bir Visual Studio örneği odağı alır. Hiçbir dosya belirtilmemişse ve hiçbir Visual Studio örneği yoksa, araç Basitleştirilmiş pencere düzenine sahip bir örnek oluşturur.

Mevcut Visual Studio örneği kalıcı durumdaysa, Visual Studio kalıcı durumdan çıktığında dosya mevcut örnekte açılır. Örneğin, [Seçenekler iletişim kutusu](../../ide/reference/options-dialog-box-visual-studio.md) açık olduğunda bu durum oluşabilir.

Visual Studio 'nun birden fazla örneği açıksa, dosya en son açılan örnekte açılır.

## <a name="example"></a>Örnek

İlk örnek dosya `MyFile.cs` Visual Studio 'nun mevcut bir örneğinde açar. Bir Visual Studio örneği yoksa, araç dosyayı yeni bir örnekte açar. İkinci örnek, tek bir dosya yerine üç dosya açılmasının dışında benzerdir.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
