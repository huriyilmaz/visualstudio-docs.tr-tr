---
title: Yerelleştirilmiş Önyükleyici Paketi | Microsoft Docs
description: Her yerel seçim için iki dosya daha oluşturarak önyükleyici paketinin ClickOnce sürümlerini oluşturmayı öğrenin.
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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 95b1d4e68f6508751d79fab2970d79cb74577e55
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090011"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Nasıl yapılır: Yerelleştirilmiş önyükleyici paketi oluşturma
Bir önyükleyici paketi oluşturduktan sonra, her yerel seçim için iki dosya daha oluşturarak önyükleyici paketinin yerelleştirilmiş sürümlerini oluşturabilirsiniz: bir yazılım lisans koşulları dosyası *(eula.rtf* gibi) ve bir paket bildirimi (*package.xml*).

 varsayılan olarak, Visual Studio 2010 yalnızca .NET Framework 4, .NET Framework 4 İstemci Profili, F# Çalışma Zamanı 2.0 ve F# Çalışma Zamanı 4.0 için yerelleştirilmiş önyükleyici paketlerini içerir. Üç adımı tamamlayarak diğer önyükleyiciler için yerelleştirilmiş paketler oluşturabilirsiniz.

1. *\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages \\ \<BootstrapperPackageName>* konumunda yerel olarak yerel olarak adlandırılmış bir klasör oluşturun.

2. Önyükleyici paketi için yazılım lisans koşullarını içeren bir dosya oluşturun ve yeni klasöre yazın.

3. package.xmladlı bir *paket* bildirimi oluşturun, dizeleri ve kültürü güncelleştirin ve dosyayı yeni klasöre yazın. Hedef dilde önceden Visual Studio önyükleyicisi oluşturduysanız, Visual Studio *package.xml* dosyasını kopyalayıp bu adımda değiştirebilirsiniz.

> [!NOTE]
> Uygulamaları dağıtmak için bir Kurulum projesi kullanıyorsanız, Yerelleştirme özelliğini değiştirerek uygulamanızı **yerelleştirebilirsiniz.**

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Yerelleştirilmiş önyükleyici paketi oluşturmak için

1. Yerel seçim adından sonra adlı bir klasör oluşturun.

     32 bit *bilgisayarlarda, \Program Files\Microsoft SDKs\ClickOnce Bootstrapper\Packages klasöründe \\ \<BootstrapperPackageName> \\ klasörü* oluşturun.

     64 bit *bilgisayarlarda, \Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages klasöründe \\ \<BootstrapperPackageName> \\ klasörü* oluşturun.

     Aşağıdaki tabloda yerel bir bölgeyle eşleşmek için kullanabileceğiniz klasör adları yer alır.

    |Yerel Ayar|Klasör adı|
    |------------|-----------------|
    |Basitleştirilmiş Çince|zh-Hans|
    |Geleneksel Çince|zh-Hant|
    |Çekçe|Cs|
    |Almanca|de|
    |İngilizce|en|
    |Spanish|es|
    |Fransızca|Fr|
    |İtalyanca|bu|
    |Korece|ko (ko)|
    |Japonca|Ja|
    |Lehçe|Pl|
    |Portekizce (Brezilya)|pt-BR|
    |Rusça|Ru|
    |Türkçe|tr|

2. Önyükleyici paketi için yazılım lisans koşullarını içeren bir dosya oluşturun ve yeni klasöre yazın.

3. *package.xmladlı bir* paket bildirimi oluşturun ve yeni klasöre yazın. Daha fazla bilgi için, [bkz. How to: Create a package manifest](../deployment/how-to-create-a-package-manifest.md).

4. Dizelerin yerel dil için doğru dilde olacak şekilde paket `<Strings>` bildirimi bölümünü güncelleştirin.

5. Değeri `<String Name="Culture">` klasör adıyla eş değiştirecek şekilde değiştirme.

6. package.xml *kaydedin.*

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>.NET Framework 3.5 Service Pack 1 için Fransızca yerelleştirilmiş bir önyükleyici paketi oluşturmak için

1. fr adlı bir klasör *oluşturun.* Klasör adı, yerel adla eşleşmeli.

     32 bit *bilgisayarlarda\Program \\ Files\Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1* klasöründe klasörü oluşturun.

     64 bit *bilgisayarlarda\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1 \\* klasöründe klasörü oluşturun.

2. Yazılım lisansı koşullarının yerelleştirilmiş bir sürümünü *fr klasörüne* yazın.

3. *\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* dosyasını *fr* klasörüne kopyalayın ve dosyayı XML Tasarımcısı'nda açın.

4. Hata `<Strings>` dizelerinin Fransızca olacak şekilde paket bildirimi bölümünü güncelleştirin.

5. değerini `<String Name="Culture">` fr olarak *değiştirme.*

6. package.xml *kaydedin.*

>[!NOTE]
> Visual Studio 2019 Güncelleştirme 7 yayın önyükleyici paketleri *<VS Install Path> de \MSBuild\Microsoft\VisualStudio\BootstrapperPackages yolunda keşfedildi.*

## <a name="see-also"></a>Ayrıca bkz.
- [Önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md)
- [Uygulama dağıtımının önkoşulları](../deployment/application-deployment-prerequisites.md)
- [Nasıl yapılır: Paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md)