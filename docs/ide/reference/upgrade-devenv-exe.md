---
title: -Upgrade (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9894056babdd8615e4ae052eb73e91e9b108acc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622414"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Çözüm dosyasını ve tüm proje dosyalarını veya belirtilen proje dosyasını, bu dosyalar için geçerli Visual Studio biçimlerine güncelleştirir.

## <a name="syntax"></a>Sözdizimi

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Arguments

- *SolutionFile*

  Bir çözümün tamamını ve projelerini yükseltiyorsanız gereklidir. Çözüm dosyasının yolu ve adı. Yalnızca çözüm dosyasının adını veya çözüm dosyasının tam yolunu ve adını girebilirsiniz. Adlı klasör veya dosya henüz yoksa, oluşturulur.

- *ProjectFile*

  Tek bir projeyi yükseltiyorsanız gereklidir. Çözüm içindeki bir proje dosyasının yolu ve adı. Yalnızca proje dosyasının adını veya proje dosyasının tam yolunu ve adını girebilirsiniz. Adlı klasör veya dosya henüz yoksa, oluşturulur.

- `/Out` *outputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Yedeklemeler otomatik olarak oluşturulur ve geçerli dizinde oluşturulan yedekleme adlı bir dizine kopyalanır.

Kaynak denetimli çözümlerin veya projelerin yükseltibilmeleri için önce kullanıma alınması gerekir.

@No__t_0 anahtarının kullanılması Visual Studio 'Yu açmaz. Yükseltmenin sonuçları, çözüm veya projenin geliştirme dili için yükseltme raporunda görülebilir. Hata veya kullanım bilgisi döndürülmedi. Visual Studio 'da projeleri yükseltme hakkında daha fazla bilgi için bkz. [bağlantı noktası, geçirme ve Visual Studio projelerini yükseltme](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Örnek

Bu örnek, "MyProject. sln" adlı bir çözüm dosyasını yükseltir.

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)