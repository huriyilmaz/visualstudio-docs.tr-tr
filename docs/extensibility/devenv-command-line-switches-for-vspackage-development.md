---
title: VSPackage geliştirme Command-Line için Devenv | Microsoft Docs
description: Geliştiricilerin, IDE'nin ilk dosyasını başlatan dosya olan devenv.exe komut satırı Visual Studio öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726952"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage geliştirme için Devenv komut satırı anahtarları

Visual Studio, geliştiricilerin IDE'nin ilk dosyasını başlatan dosyasını yürütürken `devenv.exe` komut Visual Studio sağlar.

 Görevler şunlardır:

- Önceden tasarlanmış yapılandırmalarda IDE dışından uygulama dağıtma.

- Önceden ayarlanmış derleme ayarlarını veya hata ayıklama yapılandırmalarını kullanarak projeleri otomatik olarak oluşturma.

- IDE'nin belirli yapılandırmalarda, hepsi IDE dışından yükleniyor. IDE'nin lansmanını da özelleştirebilirsiniz.

## <a name="guidelines-for-switches"></a>Anahtarlar için yönergeler

Visual Studio belgelerde kullanıcı düzeyinde komut `devenv` satırı anahtarları açıklanmıştır. Daha fazla bilgi için bkz. [Devenv komut satırı anahtarları.](../ide/reference/devenv-command-line-switches.md) Araç ayrıca VSPackage geliştirme, dağıtım ve hata ayıklama ile yararlı olan ek `devenv` komut satırı anahtarlarını da destekler.

| Komut satırı anahtarı | Description |
|---------------------| - |
| `/ResetSkipPkgs` | Sorunlu VSPackage'ları yüklememek isteyen kullanıcılar tarafından eklenen tüm yükleme atlama seçeneklerini temizler ve ardından Visual Studio. SkipLoading etiketinin olması VSPackage yüklemesini devre dışı bıraktırır. Etiketinin yeniden temizleniyor, VSPackage'ın yüklenmesine olanak sağlar.<br /><br /> Bu anahtar hiçbir bağımsız değişken alır. |
| `/RootSuffix` | Alternatif Visual Studio kullanarak bir uygulama başlatır. Aşağıdaki komut, Visual Studio SDK yükleyicisi tarafından oluşturulan kısayol tarafından çalıştırılan komuttır:<br /><br /> `devenv /RootSuffix exp`<br /><br /> Bu durumda, `exp` belirli bir son eke sahip bir konum tanımlar (örneğin, `10.0Exp` `10.0` yerine). Deneysel örnek, kod yazmak için kullanmakta olduğunu Visual Studio vsPackage örneğinden ayrı olarak hata ayıklamaya olanak sağlar.<br /><br /> Bu anahtar, VSRegEx.exe kullanarak oluşturduğunuz konumu tanımlayan herhangi bir dizeyi VSRegEx.exe. Daha fazla bilgi için [bkz. Deneysel Örnek](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Güvenli modda Visual Studio, yalnızca varsayılan IDE ve hizmetleri yükler. anahtarı, `/SafeMode` uygulama başlatıldığında tüm üçüncü taraf VSPackage'ların yüklenmesini Visual Studio kararlı yürütmeyi sağlar.<br /><br /> Bu anahtar hiçbir bağımsız değişken alır. |
| `/Setup` | Bu Visual Studio tüm kullanılabilir VSPackage'lardan menüleri, araç çubuklarını ve komut gruplarını açıklayan kaynak meta verilerini birleştirmeye zorlar. Bu komutu yalnızca yönetici olarak çalıştırabilirsiniz. <br /><br /> Bu anahtar hiçbir bağımsız değişken alır. Komutu `devenv /Setup` genellikle yükleme işleminin son adımı olarak verilir. Anahtarın `/Setup` kullanımı IDE'nin başlatılamaz.|
| `/Splash` | Giriş Visual Studio her zamanki gibi gösterir ve ardından ana IDE'leri göstermeden önce bir ileti kutusu gösterir. İleti kutusu, giriş ekranı üzerinde çalışmanızı sağlar (örneğin VSPackage ürün simgesini kontrol etmek için).<br /><br /> Bu anahtar hiçbir bağımsız değişken alır. |

## <a name="see-also"></a>Ayrıca bkz.

- [Komut satırı anahtarları ekleme](../extensibility/adding-command-line-switches.md)
- [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)
