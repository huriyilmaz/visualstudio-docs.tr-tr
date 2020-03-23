---
title: -Upgrade (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bb2b296d8728587c9aa3c22b7a670d89612eff1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596430"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Çözüm dosyasını ve tüm proje dosyalarını veya belirtilen proje dosyasını bu dosyalar için geçerli Visual Studio biçimleriyle güncelleştirir.

## <a name="syntax"></a>Sözdizimi

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *SolutionFile*

  Tüm çözümü ve projelerini yükseltiyorsanız gereklidir. Çözüm dosyasının yolu ve adı. Çözüm dosyasının adını veya tam bir yolu ve çözüm dosyasının adını girebilirsiniz. Adlandırılmış klasör veya dosya henüz yoksa oluşturulur.

- *Proje Dosyası*

  Tek bir projeyi yükseltiyorsanız gereklidir. Çözüm içindeki proje dosyasının yolu ve adı. Proje dosyasının adını veya tam bir yolu ve proje dosyasının adını girebilirsiniz. Adlandırılmış klasör veya dosya henüz yoksa oluşturulur.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıktısını göndermek istediğiniz bir dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Yedeklemeler otomatik olarak oluşturulur ve geçerli dizinde oluşturulan Yedekleme adlı bir dizine kopyalanır.

Kaynak kontrollü çözümler veya projeler yükseltilmeden önce kullanıma alınmalıdır.

`/Upgrade` Anahtarı kullanmak Visual Studio'yu açmaz. Yükseltmenin sonuçları, çözümün veya projenin geliştirme dili için Yükseltme Raporu'nda görülebilir. Hiçbir hata veya kullanım bilgisi döndürülür. Visual Studio'daki projeleri yükseltme hakkında daha fazla bilgi için [Bkz.](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)

## <a name="example"></a>Örnek

Bu örnek, "MyProject.sln" adlı bir çözüm dosyanı yükseltir.

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
