---
title: -Rebuild (devenv.exe)
description: Yeniden oluşturma Devenv komut satırı anahtarını kullanarak, belirtilen çözüm yapılandırmasını temizleyip oluşturmayı öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8086e5ffb2ebdd154e95eda18e04ed5b64cd3dd2
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040049"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

Belirtilen çözüm yapılandırmasını temizler ve oluşturur.

## <a name="syntax"></a>Söz dizimi

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Gereklidir. Çözüm dosyasının tam yolu ve adı.

- *SolnConfigName*

  İsteğe bağlı. `Debug` `Release` *SolutionName* içinde adlı çözümü yeniden derlemek için kullanılacak Çözüm yapılandırmasının adı (veya gibi). Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu bağımsız değişken belirtilmemişse veya boş bir dize ( `""` ) ise, araç çözümün etkin yapılandırmasını kullanır.

- `/Project` *ProjName*

  İsteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. Projenin görünen adını veya *SolutionName* klasöründen proje dosyasına göreli bir yol girebilirsiniz. Proje dosyasının tam yolunu ve adını da girebilirsiniz.

- `/ProjectConfig`*Projconfigname*

  İsteğe bağlı. Adlandırılmış dosyanın yeniden derlenmesi sırasında kullanılacak projenin derleme yapılandırma adı ( `Debug` veya gibi `Release` ) `/Project` . Birden fazla çözüm platformu varsa, platformu da belirtmeniz gerekir (örneğin, `Debug|Win32` ). Bu anahtar belirtilmişse, *Solnconfigname* bağımsız değişkenini geçersiz kılar.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

- Bu anahtar, IDE içindeki **çözümü yeniden derle** menü komutuyla aynı şeyi yapar.

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Temizleme ve oluşturma için hatalar da dahil olmak üzere Özet bilgiler, **komut** penceresinde veya [/Out](out-devenv-exe.md) anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek

Bu örnek `CSharpWinApp` , `Debug` içindeki proje derleme yapılandırması kullanılarak projeyi temizler ve yeniden oluşturur `MySolution` .

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
