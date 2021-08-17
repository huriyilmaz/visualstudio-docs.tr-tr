---
title: VSPackage geliştirmesi için devenv Command-Line anahtarları | Microsoft Docs
description: geliştiricilerin Visual Studio ıde 'yi başlatan dosyayı devenv.exe yürütürken komut satırından görevleri nasıl otomatikleştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 08d111a4e9ce0081c3fa73b5d9b64d926cbfa8ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095094"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage geliştirmesi için Devenv komut satırı anahtarları

Visual Studio `devenv.exe` , geliştiricilerin Visual Studio ıde 'yi başlatan dosyayı yürütürken görevleri komut satırından otomatikleştirmesine olanak tanır.

 Görevler şunları içerir:

- Uygulamaları, IDE dışından önceden tasarlanmış yapılandırmalara dağıtma.

- Önceden ayarlanmış yapı ayarlarını veya hata ayıklama yapılandırmasını kullanarak projeleri otomatik olarak derleme.

- IDE 'nin dışındaki belirli yapılandırmalarda IDE 'yi yükleme. Ayrıca, başlatma sonrasında IDE 'yi özelleştirebilirsiniz.

## <a name="guidelines-for-switches"></a>Anahtarlar için yönergeler

Visual Studio belge, kullanıcı düzeyi `devenv` komut satırı anahtarlarını açıklar. Daha fazla bilgi için bkz. [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md). `devenv`Araç ayrıca VSPackage geliştirme, dağıtım ve hata ayıklama ile yararlı olan ek komut satırı anahtarlarını da destekler.

| Komut satırı anahtarı | Açıklama |
|---------------------| - |
| `/ResetSkipPkgs` | Sorunlu VSPackages yüklemeden kaçınmak isteyen kullanıcılar tarafından eklenmiş olan tüm atlama yükleme seçeneklerini temizler, sonra Visual Studio başlatır. Bir Skipyükleme etiketinin varlığı, VSPackage yüklemesini devre dışı bırakır. Etiketi temizlemek, VSPackage yüklemesini yeniden etkinleştirilir.<br /><br /> Bu anahtar bağımsız değişken almaz. |
| `/RootSuffix` | Visual Studio başka bir konum kullanarak başlatır. aşağıdaki komut, Visual Studio SDK yükleyicisi tarafından oluşturulan kısayol tarafından çalıştırılır:<br /><br /> `devenv /RootSuffix exp`<br /><br /> Bu durumda, `exp` belirli bir sonekine sahip bir konum tanımlar (örneğin, `10.0Exp` yerine `10.0` ). deneysel örnek, bir vspackage 'ın kod yazmak için kullandığınız Visual Studio örneğinden ayrı olarak hata ayıklamanıza olanak tanır.<br /><br /> Bu anahtar, VSRegEx.exe kullanarak oluşturduğunuz bir konumu tanımlayan herhangi bir dizeyi alabilir. Daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | yalnızca varsayılan ıde ve hizmetleri yükleyerek Visual Studio güvenli modda başlatır. bu `/SafeMode` anahtar, Visual Studio başladığında tüm üçüncü taraf vspackages 'nin yüklenmesini engeller ve kararlı yürütme sağlar.<br /><br /> Bu anahtar bağımsız değişken almaz. |
| `/Setup` | Visual Studio, tüm kullanılabilir vspackages 'tan menüleri, araç çubuklarını ve komut gruplarını açıklayan kaynak meta verilerini birleştirmeye zorlar. Bu komutu yalnızca yönetici olarak çalıştırabilirsiniz. <br /><br /> Bu anahtar bağımsız değişken almaz. `devenv /Setup`Komut genellikle yükleme işleminin son adımı olarak verilir. `/Setup`Anahtarın kullanımı IDE 'yi başlatamıyor.|
| `/Splash` | Visual Studio giriş ekranını her zamanki gibi gösterir ve ardından ana ıde 'yi göstermeden önce bir ileti kutusu görüntüler. İleti kutusu, giriş ekranını (örneğin, VSPackage ürün simgesini denetlemek için) denetlemenize olanak tanır.<br /><br /> Bu anahtar bağımsız değişken almaz. |

## <a name="see-also"></a>Ayrıca bkz.

- [Komut satırı anahtarları Ekle](../extensibility/adding-command-line-switches.md)
- [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)
