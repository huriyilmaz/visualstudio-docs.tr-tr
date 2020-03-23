---
title: -NoSplash (devenv.exe)
ms.date: 12/10/2018
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a1e8118faa743398271fb282a2603aab5fcd76b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62950654"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Sıçrama ekranının gösterilmesini önler.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *Dosya1*

  İsteğe bağlı. Dosya Visual Studio'nun varolan bir örneğinde açılacak. Visual Studio'nun hiçbir örneği yoksa, basitleştirilmiş bir pencere düzeniyle yeni bir örnek oluşturulur ve araç yeni örnekte *Dosya1'i* açar.

- *FileN*

  İsteğe bağlı. Visual Studio'nun varolan örneğinde açılacak bir veya daha fazla ek dosya.

## <a name="remarks"></a>Açıklamalar

Bu anahtar sıçrama ekranını gizler. Bu anahtarın dışarıda bırakması sıçrama ekranının gösterilmesine neden olur. Sıçrama ekranını daha fazla incelemek istiyorsanız (örneğin, VSPackage ürün simgesini kontrol etmek [için), /Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md) anahtarını kullanın.

Anahtar, `/NoSplash` [/Run](run-devenv-exe.md) veya [/DebugExe](debugexe-devenv-exe.md)gibi diğer anahtarlarla birleştirilebilir.

## <a name="example"></a>Örnek

Örneklerin üçü de sıçrama ekranını görüntülemeden IDE'yi açar. İkinci örnek de belirtilen çözümü derler ve yapılı yürütülebilir çalışır. Üçüncü örnek, IDE'de hata ayıklama için belirtilen yürütücünün açılışını açar.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [VSPackage geliştirme için Devenv komut satırı anahtarları](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
