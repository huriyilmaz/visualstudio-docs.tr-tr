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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9aef4dcdc9069c1bbfe71a90bbaba214ebcd18ed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667875"
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

  İsteğe bağlı. Adlandırılmış proje oluşturulurken kullanılacak bir proje derleme yapılandırması (`Debug` veya `Release` gibi) adı. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32`). Bu anahtar belirtilmişse, *Solnconfigname* bağımsız değişkenini geçersiz kılar.

- `/Out` *outputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

- @No__t_0 anahtarı tümleşik geliştirme ortamı (IDE) içinde **yapı çözümü** menü komutuyla aynı işlevi gerçekleştirir.

- Boşluk içeren dizeleri çift tırnak içine alın.

- Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, komut penceresinde veya `/Out` anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

- @No__t_0 anahtarı yalnızca son derlemeden bu yana değiştirilen projeleri oluşturur. Bir Çözümdeki tüm projeleri oluşturmak için, bunun yerine [/Rebuild](../../ide/reference/rebuild-devenv-exe.md) kullanın.

- **Geçersiz proje yapılandırması**belirten bir hata iletisi alırsanız, bir çözüm platformu veya proje platformu belirttiğinizden emin olun (örneğin, `Debug|Win32`).

## <a name="example"></a>Örnek

Aşağıdaki komut, `MySolution` içinde `Debug` proje derleme yapılandırması kullanarak proje `CSharpWinApp` oluşturur.

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Projeleri ve çözümleri oluşturma ve temizleme](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)