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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595702"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Belirtilen dosyayı Visual Studio'nun varolan bir örneğinde açar.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *Dosya1*

  İsteğe bağlı. Dosya Visual Studio'nun varolan bir örneğinde açılacak. Visual Studio'nun hiçbir örneği yoksa, basitleştirilmiş bir pencere düzeniyle yeni bir örnek oluşturulur ve araç yeni örnekte *Dosya1'i* açar.

- *FileN*

  İsteğe bağlı. Visual Studio'nun varolan örneğinde açılacak bir veya daha fazla ek dosya.

## <a name="remarks"></a>Açıklamalar

Bir dosya belirtilmediğinde, varolan bir Visual Studio örneği odak alır. Hiçbir dosya belirtilmemişse ve Visual Studio örneği yoksa, araç basitleştirilmiş bir pencere düzenine sahip bir örnek oluşturur.

Varolan Visual Studio örneği modal durumdaysa, Visual Studio modal durumdan çıktığında dosya varolan örnekte açılır. Örneğin, [Seçenekler iletişim kutusu](../../ide/reference/options-dialog-box-visual-studio.md) açıkolduğunda bu durum oluşabilir.

Visual Studio'nun birden fazla örneği açıksa, dosya en son açılan örnekte açılır.

## <a name="example"></a>Örnek

İlk örnek, dosyayı `MyFile.cs` Visual Studio'nun varolan bir örneğinde açar. Visual Studio örneği yoksa, araç dosyayı yeni bir örnekte açar. İkinci örnek, tek bir dosya yerine üç dosya açması dışında benzerdir.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
