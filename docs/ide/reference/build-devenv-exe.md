---
title: -Build (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1766fe22573554b41ebfaa38fbd9e8d6c90c5790
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595767"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Belirli bir çözüm yapılandırma dosyası kullanarak bir çözüm veya proje oluşturur.

## <a name="syntax"></a>Sözdizimi

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *SolutionName*

  Gereklidir. Çözüm dosyasının tam yolu ve adı.

- *SolnConfigName*

  İsteğe bağlı. *SolutionName'de*adı geçen `Debug` çözümü `Release`oluşturmak için kullanılacak çözüm yapılandırmasının adı (veya) Birden çok çözüm platformu varsa, platformu da belirtmeniz `Debug|Win32`gerekir (örneğin,). Bu bağımsız değişken belirtilmemişse`""`veya boş bir dize ise ( ), araç çözümün etkin yapılandırmasını kullanır.

- `/Project`*ProjName*

  İsteğe bağlı. Çözüm içindeki proje dosyasının yolu ve adı. *SolutionName* klasöründen proje dosyasına veya projenin görüntü adıveya proje dosyasının tam yolunu ve adını göreli bir yol girebilirsiniz.

- `/ProjectConfig`*ProjConfigName*

  İsteğe bağlı. Adlandırılmış proje yi oluştururken `Debug` kullanılacak `Release`proje yapı yapılandırmasının adı (örneğin veya) kullanılacaktır. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir `Debug|Win32`(örneğin, ). Bu anahtar belirtilirse, *SolnConfigName* bağımsız değişkenini geçersiz kılar.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıktısını göndermek istediğiniz bir dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

- Anahtar, `/Build` tümleşik geliştirme ortamında (IDE) **Çözüm Oluştur** menüsü komutuyla aynı işlevi gerçekleştirir.

- Çift tırnak içinde boşluklar içeren dizeleri içine.

- Hatalar da dahil olmak üzere yapılariçin özet bilgiler komut penceresinde veya `/Out` anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

- Anahtar `/Build` yalnızca son yapıdan bu yana değişen projeler oluşturur. Tüm projeleri bir çözümde oluşturmak için bunun yerine [/yeniden oluşturma'yı](../../ide/reference/rebuild-devenv-exe.md) kullanın.

- **Geçersiz proje yapılandırması**yazan bir hata iletisi alırsanız, bir çözüm platformu veya proje `Debug|Win32`platformu (örneğin, ) belirttiğinden emin olun.

## <a name="example"></a>Örnek

Aşağıdaki komut, proje `CSharpWinApp`yapı yapılandırmasını `Debug` kullanarak `MySolution`projeyi oluşturur.

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümler oluşturma ve temizleme](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Temiz (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
