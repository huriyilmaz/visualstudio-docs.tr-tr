---
title: VSPackage geliştirmesi için devenv Command-Line anahtarları | Microsoft Docs
description: Geliştiricilerin, Visual Studio IDE 'yi Başlatan dosyayı devenv.exe yürütürken komut satırından görevleri nasıl otomatikleştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: conceptual
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6e2784066c98f8fac696306e455e7cf26b65907
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996155"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage geliştirmesi için Devenv komut satırı anahtarları

Visual Studio `devenv.exe` , Visual STUDIO IDE 'yi Başlatan dosyayı yürütürken geliştiricilerin komut satırından görevleri otomatikleştirmesini sağlar.

 Görevler şunları içerir:

- Uygulamaları, IDE dışından önceden tasarlanmış yapılandırmalara dağıtma.

- Önceden ayarlanmış yapı ayarlarını veya hata ayıklama yapılandırmasını kullanarak projeleri otomatik olarak derleme.

- IDE 'nin dışındaki belirli yapılandırmalarda IDE 'yi yükleme. Ayrıca, başlatma sonrasında IDE 'yi özelleştirebilirsiniz.

## <a name="guidelines-for-switches"></a>Anahtarlar için yönergeler

Visual Studio belgeleri, Kullanıcı düzeyi `devenv` komut satırı anahtarlarını açıklar. Daha fazla bilgi için bkz. [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md). `devenv`Araç ayrıca VSPackage geliştirme, dağıtım ve hata ayıklama ile yararlı olan ek komut satırı anahtarlarını da destekler.

| Komut satırı anahtarı | Açıklama |
|---------------------| - |
| `/ResetSkipPkgs` | Sorunlu VSPackages yüklemeden kaçınmak isteyen kullanıcılar tarafından eklenmiş tüm atlama yükleme seçeneklerini temizler ve sonra Visual Studio 'Yu başlatır. Bir Skipyükleme etiketinin varlığı, VSPackage yüklemesini devre dışı bırakır. Etiketi temizlemek, VSPackage yüklemesini yeniden etkinleştirilir.<br /><br /> Bu anahtar bağımsız değişken almaz. |
| `/RootSuffix` | Visual Studio 'Yu alternatif bir konum kullanarak başlatır. Aşağıdaki komut, Visual Studio SDK yükleyicisi tarafından oluşturulan kısayol tarafından çalıştırılır:<br /><br /> `devenv /RootSuffix exp`<br /><br /> Bu durumda, `exp` belirli bir sonekine sahip bir konum tanımlar (örneğin, `10.0Exp` yerine `10.0` ). Deneysel örnek, bir VSPackage 'ın kod yazmak için kullandığınız Visual Studio örneğinden ayrı olarak hata ayıklamanıza olanak tanır.<br /><br /> Bu anahtar, VSRegEx.exe kullanarak oluşturduğunuz bir konumu tanımlayan herhangi bir dizeyi alabilir. Daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Yalnızca varsayılan IDE ve Hizmetleri yükleyerek Visual Studio 'Yu güvenli modda başlatır. Bu `/SafeMode` anahtar, Visual Studio başlatıldığında tüm üçüncü taraf VSPackages 'nin yüklenmesini engeller ve kararlı bir yürütme sağlar.<br /><br /> Bu anahtar bağımsız değişken almaz. |
| `/Setup` | Visual Studio 'Yu, kullanılabilir tüm VSPackages 'tan menüleri, araç çubuklarını ve komut gruplarını açıklayan kaynak meta verilerini birleştirmeye zorlar. Bu komutu yalnızca yönetici olarak çalıştırabilirsiniz. <br /><br /> Bu anahtar bağımsız değişken almaz. `devenv /Setup`Komut genellikle yükleme işleminin son adımı olarak verilir. `/Setup`Anahtarın kullanımı IDE 'yi başlatamıyor.|
| `/Splash` | Her zamanki gibi Visual Studio giriş ekranını gösterir ve ana IDE 'yi göstermeden önce bir ileti kutusu görüntüler. İleti kutusu, giriş ekranını (örneğin, VSPackage ürün simgesini denetlemek için) denetlemenize olanak tanır.<br /><br /> Bu anahtar bağımsız değişken almaz. |

## <a name="see-also"></a>Ayrıca bkz.

- [Komut satırı anahtarları Ekle](../extensibility/adding-command-line-switches.md)
- [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)
