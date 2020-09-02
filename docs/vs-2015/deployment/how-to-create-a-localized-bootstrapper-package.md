---
title: 'Nasıl yapılır: yerelleştirilmiş önyükleyici paketi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ec3cd1365826c1a06b2d0f7bd6da377c8dc4d46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64835203"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Nasıl yapılır: Yerelleştirilmiş Önyükleyici Paketi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir önyükleyici paketi oluşturduktan sonra, her yerel ayar için iki farklı dosya oluşturarak Önyükleyici paketinin yerelleştirilmiş sürümlerini oluşturabilirsiniz: bir yazılım lisans koşulları dosyası (örneğin, EULA. rtf) ve bir paket bildirimi (package.xml).  
  
 Visual Studio 2010, varsayılan olarak yalnızca .NET Framework 4, .NET Framework 4 Istemci profili, F # çalışma zamanı 2,0 ve F # çalışma zamanı 4,0 için yerelleştirilmiş önyükleyici paketleri içerir. Üç adımı tamamlayarak, diğer bootstrapiçin yerelleştirilmiş paketler oluşturabilirsiniz.  
  
1. \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ *BootstrapperPackageName*' de yerel ayar adından sonra adlı bir klasör oluşturun.  
  
2. Önyükleyici paketinin yazılım lisans koşullarını içeren bir dosya oluşturun ve yeni klasöre yerleştirin.  
  
3. package.xml adlı bir paket bildirimi oluşturun, dizeleri ve kültürü güncelleştirin ve dosyayı yeni klasöre yerleştirin. Hedef dilde Visual Studio 'nun bir önyükleyiciyi zaten oluşturduysanız, Visual Studio package.xml dosyasını kopyalayabilir ve bu adımda değiştirebilirsiniz.  
  
> [!NOTE]
> Uygulamaları dağıtmak için bir kurulum projesi kullanıyorsanız, **Yerelleştirme** özelliğini değiştirerek uygulamanızı yerelleştirebilirsiniz.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>Yerelleştirilmiş bir önyükleyici paketi oluşturmak için  
  
1. Yerel ayar adından sonra adlı bir klasör oluşturun.  
  
     32 bit bilgisayarlarda, \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ *BootstrapperPackageName*\ klasöründe klasörünü oluşturun.  
  
     64 bit bilgisayarlarda, \Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ *BootstrapperPackageName*\ klasöründe klasörünü oluşturun.  
  
     Aşağıdaki tabloda, bir yerel ayara eşleştirmek için kullanabileceğiniz klasör adları gösterilmektedir.  
  
    |Yerel Ayar|Klasör adı|  
    |------------|-----------------|  
    |Basitleştirilmiş Çince|zh-Hans|  
    |Geleneksel Çince|zh-Hant|  
    |Çekçe|'ye|  
    |Almanca|seçimini|  
    |İngilizce|tr|  
    |İspanyolca|es|  
    |Fransızca|kesir|  
    |İtalyanca|içerdiği|  
    |Korece|dili|  
    |Japonca|Sofya|  
    |Lehçe|pl|  
    |Portekizce (Brezilya)|pt-BR|  
    |Rusça|ru|  
    |Türkçe|tr|  
  
2. Önyükleyici paketinin yazılım lisans koşullarını içeren bir dosya oluşturun ve yeni klasöre yerleştirin.  
  
3. package.xml adlı bir paket bildirimi oluşturun ve yeni klasöre yerleştirin. Daha fazla bilgi için bkz. [nasıl yapılır: paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md).  
  
4. `<Strings>`Dizelerin yerel ayar için doğru dilde olması için paket bildiriminin bölümünü güncelleştirin.  
  
5. `<String Name="Culture">`Değeri klasör adıyla eşleşecek şekilde değiştirin.  
  
6. package.xml dosyasını kaydedin.  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Fransızca 'da yerelleştirilmiş .NET Framework 3,5 Service Pack 1 için bir önyükleyici paketi oluşturmak için  
  
1. Fr adlı bir klasör oluşturun. Klasör adı, yerel ayar adıyla eşleşmelidir.  
  
     32 bit bilgisayarlarda, \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\ klasöründe klasörünü oluşturun.  
  
     64 bit bilgisayarlarda, \Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\ klasöründe klasörünü oluşturun.  
  
2. Yazılım lisans koşullarının yerelleştirilmiş bir sürümünü fr klasörüne yerleştirin.  
  
3. \Program Files (x86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml dosyasını fr klasörüne kopyalayın ve dosyayı XML tasarımcısında açın.  
  
4. `<Strings>`Hata dizelerinin Fransızca olması için paket bildiriminin bölümünü güncelleştirin.  
  
5. `<String Name="Culture">`Değeri fr olarak değiştirin.  
  
6. package.xml dosyasını kaydedin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md)   
 [Uygulama dağıtımı önkoşulları](../deployment/application-deployment-prerequisites.md)   
 [Nasıl yapılır: paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md)
