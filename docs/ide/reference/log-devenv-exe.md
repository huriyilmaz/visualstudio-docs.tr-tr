---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 008e7ca15595db249c05485f0d9e8f8b1277993e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595468"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Tüm etkinliği, sorun giderme amacıyla günlük dosyasına kaydeder. Bu dosya, en az `devenv /log` bir kez aradıktan sonra görüntülenir. Varsayılan olarak, günlük dosyası burada bulunur:

**%APPDATA%\\\\Microsoft\\VisualStudio**\<Sürüm\>**\\ActivityLog.xml**

Nerede \<\> Sürüm Visual Studio sürümüdür. Ancak, farklı bir yol ve dosya adı belirtebilirsiniz.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *NameoflogFile*

  Gereklidir. Kaydolmak için günlük dosyasının tam yolu ve adı.

## <a name="remarks"></a>Açıklamalar

Bu anahtar, diğer tüm anahtarlardan sonra komut satırının en sonunda görünmelidir.

Günlük, yalnızca `/Log` anahtarla açtığınız Visual Studio'nun tüm örnekleri için yazılır.

## <a name="example"></a>Örnek

Bu örnek, kullanıcının `MyVSLog.xml` ev dizinindeki dosyaya günlüğe kaydetmeyi yönlendirir.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
