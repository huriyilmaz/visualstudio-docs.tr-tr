---
title: VSPackage sorunlarını | Microsoft Docs
description: VSPackage ile ilgili sık karşılaşılan sorunlar ve sorunları çözmek için sorun giderme ipuçları hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ac1ff1aff18aca87f94ad1b771766401254994c0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110026"
---
# <a name="troubleshooting-vspackages"></a>VSPackage Sorunlarını Giderme
VSPackage' la ilgili sık karşılaşılan sorunlar ve sorunları çözmeye ilişkin ipuçları aşağıda ve ardından ve ardından ve ve ardından ve ve ardından yer alan bilgiler ve öneriler yer atır.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Uygulamanın başlamaya devam Visual Studio VSPackage sorunlarını gidermek için

- Güvenli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modda başlatın.

   Güvenli modda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] başlamak için komut isteminde **/safemodedevenv.exe yazın.**

   Bu işlem sırasında, içinde yer alan VSPackage'lar dışında HIÇBIR VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklenmez.

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Yüklenmez bir VSPackage sorunlarını gidermek için

1. VSPackage'ın çalıştırmak için kayıtlı olduğu kayıt defteri kökünü (genellikle deneysel kayıt defteri kökü) kullanırkenn emin olun.

    Daha fazla bilgi için [bkz. Deneysel Örnek](../extensibility/the-experimental-instance.md).

2. VSPackage'ın deneysel kayıt defteri kökünde çalışması hedefli ise, deneysel sürümünün çalıştırılmış olduğundan emin [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olun.

    Deneysel sürümü çalıştırmak için bir komut penceresine şunları yazın: **devenv /rootsuffix exp**.

3. VSPackage kayıt defteri girdilerinizi kontrol edin.

    Daha fazla bilgi için [bkz. VSPackage'ları](registering-and-unregistering-vspackages.md) Kaydetme [ve VSPackage'ları Yönetme.](../extensibility/managing-vspackages.md)

4.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage'ın yüklenemedi olduğu örneğinin Çıkış penceresini açın. VSPackage'ın neden yüklenemedikleri hakkında bilgiler bu pencerede görüntülenebilir.

   > [!NOTE]
   > deneysel sürümünü tümleşik geliştirme [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ortamından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (IDE) başlatacaksanız, her iki **sürümün Çıkış** penceresini inceler.

5. Etkinlik günlüğünü inceleme.

    Daha fazla bilgi için, [bkz. How to: Use the Activity Log](../extensibility/how-to-use-the-activity-log.md).

6. IDE tarafından özel durumlar hakkında daha fazla bilgi için, özel **durumları** etkinleştirmek için **Hata** Ayıklama menüsünde Özel Durumlar'a tıklayın. Özel **Durumlar iletişim** kutusunda, hakkında daha fazla bilgi istediğiniz özel durum türlerini seçin.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Kaydolmaz bir VSPackage sorunlarını gidermek için

1. VSPackage derlemenin güvenilir bir konumda yer olduğundan emin olun. RegPkg, derlemeleri varsayılan .net güvenlik yapılandırmasında bir ağ paylaşımı gibi güvenilmeyen veya kısmen güvenilen bir konuma kaydedilemez. Kullanıcı güvenilmeyen bir konumda proje oluşturduğunda bir uyarı gösterse de, "Bu iletiyi bir daha gösterme" onay kutusu bu uyarının tekrarlanmasını önlenebilir.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Görünür durumda olan veya bir komuta tıklarken hata oluşturan bir komutun sorunlarını gidermek için

1. Yeni veya değiştirilmiş menü komutlarını ve zaten IDE'de bulunanları Komut İstemi'ne yazarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] birleştirin: **devenv /rootsuffix Exp /setup**.

2. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage'nıza UI.dll emin olun.

   1. VSPackage'ın CLSID'sini kayıt defterinin Paketler bölümünde bulun:

        HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \Packages

   2. SatelliteDll alt anahtarı tarafından verilen yolun doğru olduğunu doğrulayın.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Beklenmedik şekilde davranan bir VSPackage sorunlarını gidermek için

1. Kodunda kesme noktaları ayarlayın.

     Hata ayıklama için iyi başlangıç noktaları oluşturucu ve başlatma yöntemidir. Ayrıca, değerlendirmek istediğiniz alanda menü komutu gibi kesme noktaları da ayarlayın. Kesme noktaları etkinleştirmek için hata ayıklayıcısı altında çalışmalı.

    1. Yeni **Project** Özellikler'e **tıklayın.**

    2. Özellik **Sayfaları iletişim** kutusunda Hata Ayıkla **sekmesini** seçin.

    3. Komut **satırı bağımsız değişkenleri** kutusuna VSPackage'nizin hedeflemesi geliştirme ortamının kök soneki yazın. Örneğin deneysel derlemeyi seçmek için **/RootSuffix Exp yazın.**

    4. Hata **Ayıkla menüsünde Hata** Ayıklamayı **Başlat'a tıklayın veya** F5'e basın.

        > [!NOTE]
        > Bir projede hata ayıklarsanız, projenizin mevcut bir örneğini şimdi oluşturun veya yüklenin.

2. Etkinlik günlüğünü kullanın.

     Önemli noktalarda etkinlik günlüğüne bilgi yazarak VSPackage davranışını izleme. Bu teknik özellikle bir perakende ortamında VSPackage çalıştırmada yararlıdır. Daha fazla bilgi için, [bkz. How to: Use the Activity Log](../extensibility/how-to-use-the-activity-log.md).

3. Ortak sembolleri kullanma.

     Hata ayıklama sırasında okunabilirliği artırmak için hata ayıklayıcıya semboller iliştirin.

    1. **Araçlar/Seçenekler menüsünden** Hata **Ayıklama/Semboller iletişim kutusuna** gidin.

    2. Bu Sembol **dosyası (.pdb) konumunu ekleyin:**

         `https://msdl.microsoft.com/download/symbols`

    3. Performansı artırmak için bir sembol önbellek klasörü belirtin, örneğin:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Eksik VSPackage veya bağımlılıklarından birinin sorunlarını gidermek için

1. Yönetilen kod için başvuru yollarının doğru olduğundan emin olun.

   1. Yeni **Project** Özellikler'e **tıklayın.**

   2. Özellik **Sayfaları iletişim** kutusunda **Başvurular sekmesini** seçin ve tüm yolların doğru olduğundan emin olun. Alternatif olarak, başvurulan **nesnelere göz atmak** için Object Browser'ı kullanabilirsiniz.

        Yönetilen kod için, başarısız derlemeFuslogvw.exe ayrıntılarını görüntülemek içinFuslogvw.exe (Derleme BağlamaSı Günlük [ Görüntüleyicisi)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) kullanabilirsiniz.

2. Unmanaged code için CLSID kayıt defteri düğümünde VSPackage'ın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID'sini bulun:

    HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \CLSID

   InprocServer32 girişinin VSPackage dll dosyasının doğru yoluna sahip olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
- [Visual Studio giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
