---
title: -Out (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cda81d37be0246c1181b4d82cbd17c3119b94437
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568017"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Bir dosyayı çalıştırdığınızda, [çalıştırDığınızda](run-devenv-exe.md) [ve çıktığınızda,](runexit-devenv-exe.md) [yükselttidiğinizde,](upgrade-devenv-exe.md)oluşturduğunuzda, [yeniden](build-devenv-exe.md) [inşa](rebuild-devenv-exe.md)ettiğinizde, [temizlediğinizde](clean-devenv-exe.md)veya bir çözüm [dağıttığınızda](deploy-devenv-exe.md) depolamak ve görüntülemek için bir dosya belirtir.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *Dosyaadı*

  Gereklidir. Yürütülebilir bir yapı oluştururken çıktı almak için dosyanın yolu ve adı.

## <a name="remarks"></a>Açıklamalar

Varolmayan bir dosya adı belirtilirse, dosya otomatik olarak oluşturulur. Aksi takdirde, dosya zaten var ve sonuçlar dosyanın varolan içeriğine eklenir.

Komut satırı yapı hataları **Komut** penceresinde ve **Çıktı** penceresinin Çözüm Oluşturucu görünümünde görüntülenir. Bu anahtar, gözetimsiz yapılar sonuçlarını görüntülemek için yararlıdır.

## <a name="example"></a>Örnek

Bu örnek, dosyaya `MySolution` `MyErrorLog.txt`hataları çalıştırıp yazar.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Çalıştır (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Temiz (devenv.exe)](clean-devenv-exe.md)
- [/Yapı (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
