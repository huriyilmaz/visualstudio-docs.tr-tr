---
title: -Deploy (devenv.exe)
description: Derleme veya yeniden derleme sonrasında çözüm dağıtmak için Deploy devenv komut satırı anahtarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Deploy switch
- Deploy Devenv switch
- deploying applications [Visual Studio], after build
- /Deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 34ad9f8da134241ce818cf37022a28fd8509b7f5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117377"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

Derleme veya yeniden derleme sonrasında bir çözüm dağıtır. Yalnızca yönetilen kod projeleri için geçerlidir.

## <a name="syntax"></a>Söz dizimi

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Gereklidir. Çözüm dosyasının tam yolu ve adı.

- *SolnConfigName*

  İsteğe bağlı. SolutionName içinde adlı çözümü oluşturmak için kullanılacak çözüm yapılandırmasının adı `Debug` `Release` (veya *gibi).* Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu bağımsız değişken belirtilmemişse veya boş bir dize () `""` ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki proje dosyasının yolu ve adı. *SolutionName* klasöründen projenin görünen adını veya göreli yolunu proje dosyasına girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig`*ProjConfigName*

  İsteğe bağlı. Bir proje derleme yapılandırmasının (veya gibi) adı `Debug` `Release` oluşturmada kullanılacak `/Project` adları. Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu anahtar belirtilirse *SolnConfigName bağımsız değişkenlerini geçersiz* kılar.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Belirtilen proje bir dağıtım projesi olması gerekir. Belirtilen proje bir dağıtım projesi değilse, proje dağıtım için geçiriliyorsa bir hatayla başarısız olur.

Çift tırnak içinde boşluk içeren dizeleri içine alın.

Hatalar da dahil olmak üzere derlemelerin özet  bilgileri Komut penceresinde veya /Out anahtarıyla belirtilen herhangi bir günlük [dosyasında görüntülenebilir.](out-devenv-exe.md)

## <a name="example"></a>Örnek

Bu örnek, içindeki proje `CSharpWinApp` derleme yapılandırmasını `Release` kullanarak projesini `MySolution` dağıtır.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
