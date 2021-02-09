---
title: Yerelleştirilmiş önyükleyici paketi oluştur | Microsoft Docs
description: Her yerel ayar için iki dosya oluşturarak ClickOnce 'ta Önyükleyici paketinin yerelleştirilmiş sürümlerini oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9eb06c54caceb2e9329347fb1dd0114749975e7d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927593"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Nasıl yapılır: yerelleştirilmiş önyükleyici paketi oluşturma
Bir önyükleyici paketi oluşturduktan sonra, her yerel ayar için iki farklı dosya oluşturarak Önyükleyici paketinin yerelleştirilmiş sürümlerini oluşturabilirsiniz: bir yazılım lisans koşulları dosyası (örneğin, *EULA. rtf*) ve bir paket bildirimi (*package.xml*).

 Visual Studio 2010, varsayılan olarak yalnızca .NET Framework 4, .NET Framework 4 Istemci profili, F # çalışma zamanı 2,0 ve F # çalışma zamanı 4,0 için yerelleştirilmiş önyükleyici paketleri içerir. Üç adımı tamamlayarak, diğer bootstrapiçin yerelleştirilmiş paketler oluşturabilirsiniz.

1. *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName>* içindeki yerel ayar adından sonra adlı bir klasör oluşturun.

2. Önyükleyici paketinin yazılım lisans koşullarını içeren bir dosya oluşturun ve yeni klasöre yerleştirin.

3. *package.xml* adlı bir paket bildirimi oluşturun, dizeleri ve kültürü güncelleştirin ve dosyayı yeni klasöre yerleştirin. Hedef dilde Visual Studio 'nun bir önyükleyiciyi zaten oluşturduysanız, Visual Studio *package.xml* dosyasını kopyalayabilir ve bu adımda değiştirebilirsiniz.

> [!NOTE]
> Uygulamaları dağıtmak için bir kurulum projesi kullanıyorsanız, **Yerelleştirme** özelliğini değiştirerek uygulamanızı yerelleştirebilirsiniz.

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Yerelleştirilmiş bir önyükleyici paketi oluşturmak için

1. Yerel ayar adından sonra adlı bir klasör oluşturun.

     32 bit bilgisayarlarda, *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName> \\* klasöründe klasörünü oluşturun.

     64 bit bilgisayarlarda, *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName> \\* klasöründe klasörünü oluşturun.

     Aşağıdaki tabloda, bir yerel ayara eşleştirmek için kullanabileceğiniz klasör adları gösterilmektedir.

    |Yerel Ayar|Klasör adı|
    |------------|-----------------|
    |Basitleştirilmiş Çince|zh-Hans|
    |Geleneksel Çince|zh-Hant|
    |Çekçe|'ye|
    |Almanca|seçimini|
    |İngilizce|en|
    |Spanish|es|
    |Fransızca|kesir|
    |İtalyanca|içerdiği|
    |Korece|dili|
    |Japonca|Sofya|
    |Lehçe|pl|
    |Portekizce (Brezilya)|pt-BR|
    |Rusça|ru|
    |Türkçe|tr|

2. Önyükleyici paketinin yazılım lisans koşullarını içeren bir dosya oluşturun ve yeni klasöre yerleştirin.

3. *package.xml* adlı bir paket bildirimi oluşturun ve yeni klasöre yerleştirin. Daha fazla bilgi için bkz. [nasıl yapılır: paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md).

4. `<Strings>`Dizelerin yerel ayar için doğru dilde olması için paket bildiriminin bölümünü güncelleştirin.

5. `<String Name="Culture">`Değeri klasör adıyla eşleşecek şekilde değiştirin.

6. *package.xml* dosyasını kaydedin.

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Fransızca 'da yerelleştirilmiş .NET Framework 3,5 Service Pack 1 için bir önyükleyici paketi oluşturmak için

1. *Fr* adlı bir klasör oluşturun. Klasör adı, yerel ayar adıyla eşleşmelidir.

     32 bit bilgisayarlarda, *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1 \\* klasöründe klasörünü oluşturun.

     64 bit bilgisayarlarda, *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1 \\* klasöründe klasörünü oluşturun.

2. Yazılım lisans koşullarının yerelleştirilmiş bir sürümünü *fr* klasörüne yerleştirin.

3. *\Program Files (x86) \microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* dosyasını *fr* KLASÖRÜNE kopyalayın ve dosyayı XML tasarımcısında açın.

4. `<Strings>`Hata dizelerinin Fransızca olması için paket bildiriminin bölümünü güncelleştirin.

5. `<String Name="Culture">`Değeri *fr* olarak değiştirin.

6. *package.xml* dosyasını kaydedin.

## <a name="see-also"></a>Ayrıca bkz.
- [Önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md)
- [Uygulama dağıtımının önkoşulları](../deployment/application-deployment-prerequisites.md)
- [Nasıl yapılır: Paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md)