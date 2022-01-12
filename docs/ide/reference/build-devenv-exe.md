---
title: -Build (devenv.exe)
description: Build Devenv komut satırı anahtarı hakkında bilgi edinin ve belirli bir çözüm yapılandırma dosyası ile bir çözüm veya proje oluşturmak için nasıl kullanılacağını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: aee0d27701e2c170fffe85f871cb792045bed28b
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805877"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Belirtilen çözüm yapılandırma dosyasını kullanarak bir çözüm veya proje oluşturur.

## <a name="syntax"></a>Söz dizimi

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Gereklidir. Çözümün dizinine göre çözüm dosyasının yolu ve adı.

- *SolnConfigName*

  İsteğe bağlı. `Debug` `Release` *SolutionName* içinde adlı çözümü oluşturmak için kullanılacak Çözüm yapılandırmasının adı (veya gibi). Birden çok çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu bağımsız değişken belirtilmemişse veya boş bir dize ( `""` ) ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. *SolutionName* klasöründen proje dosyasına ya da projenin görünen adına veya proje dosyasının tam yolunu ve adına bir göreli yol girebilirsiniz.

- `/ProjectConfig`*Projconfigname*

  İsteğe bağlı. `Debug`Adlandırılmış proje oluşturulurken kullanılacak bir proje derleme yapılandırmasının (veya gibi `Release` ) adı. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu anahtar belirtilmişse, *Solnconfigname* bağımsız değişkenini geçersiz kılar.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

- `/Build`Anahtar, tümleşik geliştirme ortamı (IDE) Içinde **yapı çözümü** menü komutu ile aynı işlevi gerçekleştirir.

- Boşluk içeren dizeleri çift tırnak içine alın.

- Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, komut penceresinde veya anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir `/Out` .

- `/Build`Anahtar yalnızca son derlemeden bu yana değiştirilen projeleri oluşturur. Bir Çözümdeki tüm projeleri oluşturmak için, bunun yerine [/Rebuild](../../ide/reference/rebuild-devenv-exe.md) kullanın.

- **Geçersiz proje yapılandırması** belirten bir hata iletisi alırsanız, bir çözüm platformu veya proje platformu belirttiğinizden emin olun (örneğin, `Debug|Win32` ).

## <a name="example"></a>Örnek

Aşağıdaki komut, `CSharpWinApp` `Debug` içindeki proje yapı yapılandırmasını kullanarak projeyi oluşturur `MySolution` .

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Projeleri ve çözümleri oluşturma ve temizleme](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
