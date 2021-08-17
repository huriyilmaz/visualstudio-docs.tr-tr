---
title: -Rebuild (devenv.exe)
description: Rebuild devenv komut satırı anahtarını kullanarak temizlemeyi ve ardından belirtilen çözüm yapılandırmasını derlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- Rebuild Devenv switch (/Rebuild)
- projects [Visual Studio], rebuilding
- /Rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6a3ef4a0394f62e214865e89f08d6d65771954e8724686db27a76ded978d7b46
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400120"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

Temizlenir ve ardından belirtilen çözüm yapılandırmasını derlemek.

## <a name="syntax"></a>Söz dizimi

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Gereklidir. Çözüm dosyasının tam yolu ve adı.

- *SolnConfigName*

  İsteğe bağlı. SolutionName içinde adlı çözümü yeniden inşa etmek için kullanılacak çözüm yapılandırmasının adı `Debug` `Release` (veya *gibi).* Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu bağımsız değişken belirtilmemişse veya boş bir dize () `""` ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. *SolutionName* klasöründen projenin görünen adını veya göreli yolunu proje dosyasına girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig`*ProjConfigName*

  İsteğe bağlı. Projenin derleme yapılandırması adı (veya gibi) yeniden `Debug` `Release` derlemek için `/Project` kullanılacak. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu anahtar belirtilirse *SolnConfigName bağımsız değişkenlerini geçersiz* kılar.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

- Bu anahtar, IDE içindeki Çözümü **Yeniden Oluştur** menü komutuyla aynı şeyi yapar.

- Çift tırnak içinde boşluk içeren dizeleri içine alın.

- Hatalar da dahil olmak üzere temizleme ve binaya ilişkin özet bilgiler Komut penceresinde veya /Out anahtarıyla belirtilen herhangi bir [günlük dosyasında görüntülenebilir.](out-devenv-exe.md) 

## <a name="example"></a>Örnek

Bu örnek içindeki proje derleme yapılandırmasını kullanarak `CSharpWinApp` projesini temizler `Debug` ve yeniden derlemesi `MySolution` sağlar.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
