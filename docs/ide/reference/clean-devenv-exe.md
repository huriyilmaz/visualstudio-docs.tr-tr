---
title: -Clean (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- Clean Devenv switch
- /Clean Devenv switch
- Devenv, /Clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f46a17371f0c83d3bdb3873c0138eca87c6b3d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663816"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Tüm ara dosyaları ve çıkış dizinlerini temizler.

## <a name="syntax"></a>Sözdizimi

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Gerekli. Çözüm dosyasının tam yolu ve adı.

- *Kurulumunun*

  İsteğe bağlı. *SolutionName*içinde adlı çözüme ait aracı dosyalarını temizlemek için yapılandırma (`Debug` veya `Release` gibi). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`). Bu bağımsız değişken belirtilmemişse veya boş bir dize (`""`) ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. Projenin görünen adını veya *SolutionName* klasöründen proje dosyasına göreli bir yol girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig` *Projconfigname*

  İsteğe bağlı. Adlı `/Project` temizlenirken kullanılacak projenin derleme yapılandırma adı (`Debug` veya `Release` gibi). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`). Bu anahtar belirtilmişse, *yapılandırma* bağımsız değişkenini geçersiz kılar.

- `/Out` *outputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Bu anahtar, IDE içindeki **Çözümü Temizle** menü komutuyla aynı işlevi yapar.

Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

Temizleme ve oluşturma sırasında hatalar dahil, **komut** penceresinde veya [/Out](out-devenv-exe.md) anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilecek Özet bilgiler.

@No__t_0 anahtarı belirtilmezse, *dosya adı* bir proje dosyası olarak belirtilmiş olsa bile, çözüm içindeki tüm projelerde Temizleme eylemi yapılır.

## <a name="example"></a>Örnek

İlk örnek, çözüm dosyasında belirtilen varsayılan yapılandırmayı kullanarak `MySolution` çözümünü temizler.

İkinci örnek, `MySolution` içindeki `Debug` proje derleme yapılandırması kullanılarak proje `CSharpWinApp` temizler.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)