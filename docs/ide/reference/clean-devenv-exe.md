---
title: -Clean (devenv.exe)
description: Tüm ara dosyaları ve çıkış dizinlerini temizlemek için Clean devenv komut satırı anahtarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- Clean Devenv switch
- /Clean Devenv switch
- Devenv, /Clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3178d4a78b91d862dd6c222dbec6277a31fe9c75a9c7ebf97cbd4a4d2ec6dbfc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121430856"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Tüm ara dosyaları ve çıkış dizinlerini temizler.

## <a name="syntax"></a>Söz dizimi

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Gereklidir. Çözüm dosyasının tam yolu ve adı.

- *Config*

  İsteğe bağlı. SolutionName içinde adlı çözüm için ara dosyaları temizlemek için yapılandırma `Debug` `Release` (veya *gibi).* Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu bağımsız değişken belirtilmemişse veya boş bir dize () `""` ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki proje dosyasının yolu ve adı. *SolutionName* klasöründen projenin görünen adını veya göreli yolunu proje dosyasına girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig`*ProjConfigName*

  İsteğe bağlı. Projenin derleme yapılandırma adı (veya gibi) adı `Debug` `Release` temizken `/Project` kullanılacak. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu anahtar belirtilirse Config bağımsız değişkenlerini *geçersiz* kılar.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Bu anahtar, IDE içindeki **Çözümü Temizle** menü komutuyla aynı işlevi yapar.

Çift tırnak içinde boşluk içeren dizeleri içine alın.

Hatalar da dahil olmak üzere temizleme ve binaya ilişkin özet bilgiler Komut penceresinde veya /Out anahtarıyla belirtilen herhangi bir [günlük dosyasında görüntülenebilir.](out-devenv-exe.md) 

Anahtar `/Project` belirtilmezse, *FileName* proje dosyası olarak belirtilmiş olsa bile çözümde yer alan tüm projelerde temizleme eylemi yapılır.

## <a name="example"></a>Örnek

İlk örnek, çözüm `MySolution` dosyasında belirtilen varsayılan yapılandırmayı kullanarak çözümü temizler.

İkinci örnek, içindeki proje derleme `CSharpWinApp` yapılandırmasını `Debug` kullanarak projesini `MySolution` temizler.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
