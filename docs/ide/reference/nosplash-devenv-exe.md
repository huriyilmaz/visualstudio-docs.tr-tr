---
title: -NoSplash (devenv.exe)
description: Giriş ekranının görüntülenmesini engellemek için NoSplash Devenv komut satırı anahtarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c88d75c0658c861c4631daeeb736ed7cfdb0a487
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967234"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Giriş ekranının gösterilmesini engeller.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *FILE1*

  İsteğe bağlı. Visual Studio 'nun mevcut bir örneğinde açılacak dosya. Visual Studio 'nun bir örneği yoksa, Basitleştirilmiş bir pencere düzeniyle yeni bir örnek oluşturulur ve araç yeni örnekte *FILE1* öğesini açar.

- *Dosyan*

  İsteğe bağlı. Visual Studio 'nun mevcut örneğinde açmak için bir veya daha fazla ek dosya.

## <a name="remarks"></a>Açıklamalar

Bu anahtar giriş ekranını gizler. Bu anahtardan ayrıldığınızda giriş ekranının görüntülenmesine neden olur. Giriş ekranını daha fazla incelemek istiyorsanız (örneğin, VSPackage ürün simgesini denetlemek için), [/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md) anahtarını kullanın.

`/NoSplash`Anahtar, [/Run](run-devenv-exe.md) veya [/debugexe](debugexe-devenv-exe.md)gibi diğer anahtarlarla birleştirilebilir.

## <a name="example"></a>Örnek

Örneklerin üçü de giriş ekranını görüntülemeden IDE 'yi açar. İkinci örnek ayrıca, belirtilen çözümü derler ve oluşturulmuş çalıştırılabiliri çalıştırır. Üçüncü örnek, IDE 'de hata ayıklama için belirtilen yürütülebiliri açar.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [VSPackage geliştirmesi için Devenv komut satırı anahtarları](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
