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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595767"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Belirtilen çözüm yapılandırma dosyasını kullanarak bir çözüm veya proje oluşturur.

## <a name="syntax"></a>Sözdizimi

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Gerekli. Çözüm dosyasının tam yolu ve adı.

- *SolnConfigName*

  İsteğe bağlı. *SolutionName*içinde adlı çözümü oluşturmak için kullanılacak Çözüm yapılandırmasının adı (örneğin, `Debug` veya `Release`). Birden çok çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`). Bu bağımsız değişken belirtilmemişse veya boş bir dize (`""`) ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. *SolutionName* klasöründen proje dosyasına ya da projenin görünen adına veya proje dosyasının tam yolunu ve adına bir göreli yol girebilirsiniz.

- `/ProjectConfig` *Projconfigname*

  İsteğe bağlı. Adlandırılmış proje oluşturulurken kullanılacak bir proje derleme yapılandırması (`Debug` veya `Release`gibi) adı. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`). Bu anahtar belirtilmişse, *Solnconfigname* bağımsız değişkenini geçersiz kılar.

- `/Out` *outputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

- `/Build` anahtarı tümleşik geliştirme ortamı (IDE) içinde **yapı çözümü** menü komutuyla aynı işlevi gerçekleştirir.

- Boşluk içeren dizeleri çift tırnak içine alın.

- Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, komut penceresinde veya `/Out` anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

- `/Build` anahtarı yalnızca son derlemeden bu yana değiştirilen projeleri oluşturur. Bir Çözümdeki tüm projeleri oluşturmak için, bunun yerine [/Rebuild](../../ide/reference/rebuild-devenv-exe.md) kullanın.

- **Geçersiz proje yapılandırması**belirten bir hata iletisi alırsanız, bir çözüm platformu veya proje platformu belirttiğinizden emin olun (örneğin, `Debug|Win32`).

## <a name="example"></a>Örnek

Aşağıdaki komut, `MySolution`içinde `Debug` proje derleme yapılandırması kullanarak proje `CSharpWinApp`oluşturur.

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Projeleri ve çözümleri oluşturma ve temizleme](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
