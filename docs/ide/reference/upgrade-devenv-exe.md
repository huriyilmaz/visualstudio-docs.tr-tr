---
title: -Upgrade (devenv.exe)
description: Çözüm dosyasını ve tüm proje dosyalarını veya belirtilen proje dosyasını bu dosyalar için geçerli dosya biçimine güncelleştirmek için Upgrade devenv komut satırı anahtarını Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3787cccb41738050fae1fe16e03e8a8ca273f5ebb30ac3b71e9d146c1b9e2001
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387154"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Çözüm dosyasını ve tüm proje dosyalarını veya belirtilen proje dosyasını, bu dosyalar için geçerli Visual Studio olarak günceller.

## <a name="syntax"></a>Söz dizimi

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionFile*

  Bir çözümün tamamını ve projelerini yükseltıyorsanız gereklidir. Çözüm dosyasının yolu ve adı. Yalnızca çözüm dosyasının adını veya tam yolu ve çözüm dosyasının adını girebilirsiniz. adlı klasör veya dosya henüz yoksa oluşturulur.

- *ProjectFile*

  Tek bir projeyi yükseltıyorsanız gereklidir. Çözüm içindeki bir proje dosyasının yolu ve adı. Yalnızca proje dosyasının adını veya tam yolu ve proje dosyasının adını girebilirsiniz. adlı klasör veya dosya henüz yoksa oluşturulur.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Yedeklemeler otomatik olarak oluşturulur ve geçerli dizinde oluşturulan Backup adlı bir dizine kopyalanır.

Kaynak denetimli çözümlerin veya projelerin yükseltilmeden önce kullanıma alınmış olması gerekir.

anahtarı, `/Upgrade` anahtar kullanılarak Visual Studio. Yükseltmenin sonuçları, çözümün veya projenin geliştirme dili için Yükseltme Raporu'nda görülebilir. Hata veya kullanım bilgisi döndürülemedi. Visual Studio'de projeleri yükseltme hakkında daha fazla bilgi için bkz. Visual Studio [Projelerini Taşıma, Geçirme ve Yükseltme.](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)

## <a name="example"></a>Örnek

Bu örnek, "MyProject.sln" adlı bir çözüm dosyasını yükselter.

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
