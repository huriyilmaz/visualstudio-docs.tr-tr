---
title: VSPackage Geliştirme için Devenv Komut Hattı Anahtarları | Microsoft Dokümanlar
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
ms.openlocfilehash: ad3a5125a730b9230959bbf9342b4c0a4823c4d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712188"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage geliştirme için Devenv komut satırı anahtarları

Visual Studio, geliştiricilerin Visual Studio IDE'yi başlatan dosyayı çalıştırırken `devenv.exe`komut satırından görevleri otomatikleştirmelerine olanak tanır.

 Görevler şunlardır:

- Uygulamaları IDE dışından önceden tasarlanmış yapılandırmalarda dağıtma.

- Önceden ayarlanmış yapı ayarlarını veya hata ayıklama yapılandırmalarını kullanarak projeleri otomatik olarak oluşturma.

- IDE'nin tüm ide dışından belirli yapılandırmalarda yüklenmesi. Ayrıca, lansmanda IDE'yi özelleştirebilirsiniz.

## <a name="guidelines-for-switches"></a>Anahtarlar için yönergeler

Visual Studio belgeleri, kullanıcı `devenv` düzeyindeki komut satırı anahtarlarını açıklar. Daha fazla bilgi için Bkz. [Devenv komut satırı anahtarları.](../ide/reference/devenv-command-line-switches.md) Araç `devenv` ayrıca VSPackage geliştirme, dağıtım ve hata ayıklama ile yararlı ek komut satırı anahtarları destekler.

| Komut satırı anahtarı | Açıklama |
|---------------------| - |
| `/ResetSkipPkgs` | Sorunlu VSPackages yüklemekten kaçınmak isteyen kullanıcılar tarafından eklenen tüm atlama yükleme seçeneklerini temizler ve Visual Studio'yı başlatır. SkipLoading etiketinin varlığı, bir VSPackage'ın yüklenmesinin devre dışı kalır. Etiketi temizlemek VSPackage'ın yüklenmesine olanak sağlar.<br /><br /> Bu anahtar hiçbir argüman alır. |
| `/RootSuffix` | Alternatif bir konum kullanarak Visual Studio'yı başlatır. Aşağıdaki komut Visual Studio SDK yükleyicitarafından oluşturulan kısayol tarafından çalıştırılır:<br /><br /> `devenv /RootSuffix exp`<br /><br /> Bu durumda, `exp` belirli bir sonek (örneğin, `10.0Exp` yerine) `10.0`ile bir konum tanımlar. Deneysel örnek, kod yazmak için kullandığınız Visual Studio örneğinden ayrı olarak bir VSPackage hata ayıklamanızı sağlar.<br /><br /> Bu anahtar, VSRegEx.exe kullanarak oluşturduğunuz bir konumu tanımlayan herhangi bir dize alabilir. Daha fazla bilgi için [Deneysel Örnek'e](../extensibility/the-experimental-instance.md)bakın. |
| `/SafeMode` | Visual Studio'yu güvenli modda başlatıyor ve yalnızca varsayılan IDE'yi ve hizmetleri yükler. Anahtar, `/SafeMode` Visual Studio başladığında tüm üçüncü taraf VSPackages'ın yüklenmesine engel olarak kararlı bir yürütme sağlar.<br /><br /> Bu anahtar hiçbir argüman alır. |
| `/Setup` | Visual Studio'yı, kullanılabilir tüm VSPackages'lerden menüleri, araç çubuklarını ve komut gruplarını açıklayan kaynak meta verilerini birleştirmeye zorlar. Bu komutu yalnızca yönetici olarak çalıştırabilirsiniz. <br /><br /> Bu anahtar hiçbir argüman alır. Komut `devenv /Setup` genellikle yükleme işleminin son adımı olarak verilir. Anahtarın `/Setup` kullanımı IDE'yi başlatmaz.|
| `/Splash` | Visual Studio sıçrama ekranını her zamanki gibi gösterir ve ana IDE'yi göstermeden önce bir ileti kutusu gösterir. İleti kutusu sıçrama ekranını incelemenize olanak tanır (örneğin, vspackage ürün simgesini kontrol etmek için).<br /><br /> Bu anahtar hiçbir argüman alır. |

## <a name="see-also"></a>Ayrıca bkz.

- [Komut satırı anahtarları ekleme](../extensibility/adding-command-line-switches.md)
- [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)
