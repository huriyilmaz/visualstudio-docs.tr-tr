---
title: Bir uzantının anatomisi
description: Bir uzantının yapısını Visual Studio açıklar
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: 57a12f428211f4799fa610bf729110743de34f76
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516804"
---
# <a name="anatomy-of-a-visual-studio-extension"></a>Bir Visual Studio anatomisi

VSIX paketi, uzantıları sınıflandırmak ve yüklemek için bir veya daha Visual Studio uzantıyı ve Visual Studio meta verileri içeren bir .vsix dosyasıdır. VSIX paket biçimi, ZIP dosyalarını açabilirsiniz herhangi bir araç tarafından açılabilir anlamına gelir Open Packaging Conventions (OPC) standardını izler.

Uzantı projesi, birkaç ek ekin benzersiz olduğu bir C# projesidir. Aşağıdaki videoda, uzantı projelerinin nasıl çalışta olduğunu daha iyi anlamak için bir uzantı projesi inceler:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWPhtJ]

## <a name="file-structure"></a>Dosya yapısı
VSIX komut satırı **/Komut (Project)** şablonunu Community yeni uzantılar oluştururken, dosya yapısı aşağıdaki gibi olur:

:::image type="content" source="../media/new-project-files.png" alt-text="VSIX projesinin dosya yapısı.":::

**.vsixmanifest** dosyası ana dosyadır. Bu, uygulama tarafından kullanılan uzantı hakkında bilgi içeren bir XML Visual Studio. Uzantının tüm bileşenleri **.vsixmanifest dosyasına** kaydedilir. VsIX projesinde tek zorunlu dosyadır.

**VSCommandTable.vsct** dosyası, komutların bildir olduğu dosyadır. Bu bir XML dosyasıdır ve düğme komutlarının, menülerin, klavye kısayol bağlamalarının ve daha fazlasının tanımlarını içerir. Dosya, içeriğini, komut tablosu menü yapısının tamamını oluşturmak .dll Visual Studio bir bloba derler. Bu dosya yalnızca komut tablosunda bileşenleri belirtir; herhangi bir komut çağrılarını işlemez.

**\* Package.cs** dosyası, çoğu uzantının giriş noktası olan Package sınıfıdır. Burada genellikle komut işleyicileri, araç pencerelerini, seçenek sayfalarını, hizmetleri ve kayıtlı diğer bileşenleri bulabilirsiniz.

## <a name="compilation"></a>Derleme
Proje, geçerli çözüm derleme yapılandırmanıza bağlı olarak */bin/debug* veya */bin/release* klasöründe bulunan bir .vsix dosyasına derler. Uzantı *Visual Studio iş yükü,* [](get-tools.md) VSIX MSBuild işlemek için ayrılmış hedef ve görevler sağlar.

VSIX projesi derlemesi sırasında otomatik olarak Deneysel Örnek'e dağıtılır. Bu, VSIX proje ayarlarında denetlenebilirsiniz: 

:::image type="content" source="../media/deploy-vsix-experimental-instance.png" alt-text="VSIX proje özellikleri.":::

## <a name="experimental-instance"></a>Deneysel örnek
Geliştirme ortamınızı Visual Studio değiştirmeyecek olan test edilmemiş uygulamalardan korumak için VS SDK, deneme yapmak için kullanabileceğiniz deneysel bir alan sağlar. Yeni uygulamaları her zamanki Visual Studio kullanarak geliştirin, ancak bu Deneysel Örneği kullanarak çalıştırın.

VSIX paketi olan her uygulama, Visual Studio hata ayıklama modunda deneysel örneği başlatıyor.

Belirli bir çözümün dışında Visual Studio örneğini başlatmak için komut penceresinde aşağıdaki komutu çalıştırın:

```shell
devenv.exe /RootSuffix Exp
```

Daha fazla genişletilebilirlik kavramı için bu araç [setlerini](useful-resources.md)takip etmek için kullanışlı kaynaklara göz atabilirsiniz.
